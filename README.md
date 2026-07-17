import React, { useState, useRef, useEffect } from "react";
import { Link } from "react-router-dom";
import { motion } from "framer-motion";
import { Feather, FlaskConical, Palette, ArrowRight, Sparkles, BookOpen, Microscope, Brush } from "lucide-react";
import SocialDock from "@/components/SocialDock";

const features = [
  {
    to: "/about-family",
    title: "Location of My Home",
    desc: "Where we call home — our village, district, and roots in western Uganda.",
    icon: Feather,
    accent: "from-amber-400 to-orange-500",
    glow: "shadow-amber-500/20",
  },
  {
    to: "/members",
    title: "My Family Members",
    desc: "Meet the people who make the Natamba family — our parents and siblings.",
    icon: FlaskConical,
    accent: "from-sky-400 to-indigo-500",
    glow: "shadow-indigo-500/20",
  },
];

const inspirations = [
  { icon: BookOpen, label: "Fantasy worlds", color: "text-amber-500" },
  { icon: Microscope, label: "Hidden science", color: "text-sky-500" },
  { icon: Brush, label: "Art movements", color: "text-rose-500" },
  { icon: Sparkles, label: "Mystery plots", color: "text-violet-500" },
];

export default function Home() {
  return (
    <div className="min-h-screen bg-stone-900 text-stone-100 relative overflow-hidden">
      {/* Wallpaper */}
      <div
        className="absolute inset-0 bg-cover bg-center"
        style={{ backgroundImage: "url('https://media.base44.com/images/public/6a58f15848c259231956193c/9715a5794_generated_image.png')" }}
      />
      {/* Readability overlay */}
      <div className="absolute inset-0 bg-gradient-to-b from-stone-900/70 via-stone-900/55 to-stone-900/80" />

      {/* Hero */}
      <header className="relative max-w-6xl mx-auto px-6 pt-20 pb-12 text-center">
        <motion.div
          initial={{ opacity: 0, y: 20 }}
          animate={{ opacity: 1, y: 0 }}
          transition={{ duration: 0.7 }}
        >
          <div className="inline-flex items-center gap-2 px-4 py-1.5 rounded-full bg-white/10 backdrop-blur border border-amber-300/30 text-xs font-medium tracking-wide text-amber-200 mb-8 shadow-sm">
            <Sparkles className="w-3.5 h-3.5" />
            AI storytelling &amp; research companion · by Natamba's Family
          </div>
          <h1 className="font-display text-6xl md:text-8xl font-bold tracking-tight text-white leading-[0.95]">
            Natamba's <span className="bg-gradient-to-r from-amber-500 via-orange-500 to-rose-500 bg-clip-text text-transparent">Family</span>
          </h1>
          <p className="mt-6 text-lg md:text-xl text-stone-200 max-w-2xl mx-auto leading-relaxed font-body">
            A place where stories come to life and curiosity meets discovery.
            Write tales together, or explore the frontiers of science and art.
          </p>
        </motion.div>

        {/* Inspiration pills */}
        <motion.div
          className="flex flex-wrap items-center justify-center gap-3 mt-10"
          initial={{ opacity: 0 }}
          animate={{ opacity: 1 }}
          transition={{ delay: 0.4, duration: 0.6 }}
        >
          {inspirations.map((insp) => (
            <div key={insp.label} className="inline-flex items-center gap-2 px-3.5 py-2 rounded-full bg-white/10 backdrop-blur-sm border border-white/20 text-sm text-stone-200 shadow-sm">
              <insp.icon className={`w-4 h-4 ${insp.color}`} />
              {insp.label}
            </div>
          ))}
        </motion.div>
      </header>

      {/* Feature cards */}
      <section className="relative max-w-6xl mx-auto px-6 pb-20">
        <div className="grid md:grid-cols-2 gap-6 md:gap-8">
          {features.map((f, i) => (
            <motion.div
              key={f.title}
              initial={{ opacity: 0, y: 30 }}
              animate={{ opacity: 1, y: 0 }}
              transition={{ delay: 0.6 + i * 0.15, duration: 0.6 }}
            >
              <Link
                to={f.to}
                className={`group block rounded-3xl bg-white p-8 md:p-10 shadow-xl ${f.glow} border border-stone-100 hover:shadow-2xl transition-all duration-300 hover:-translate-y-1`}
              >
                <div className={`w-14 h-14 rounded-2xl bg-gradient-to-br ${f.accent} flex items-center justify-center shadow-lg mb-6`}>
                  <f.icon className="w-7 h-7 text-white" />
                </div>
                <h2 className="font-heading text-2xl font-bold text-stone-900 mb-2">{f.title}</h2>
                <p className="text-stone-600 leading-relaxed mb-6">{f.desc}</p>
                <span className="inline-flex items-center gap-2 text-sm font-semibold text-stone-900 group-hover:gap-3 transition-all">
                  Begin <ArrowRight className="w-4 h-4" />
                </span>
              </Link>
            </motion.div>
          ))}
        </div>

        {/* Subject strip */}
        <motion.div
          initial={{ opacity: 0 }}
          animate={{ opacity: 1 }}
          transition={{ delay: 1, duration: 0.6 }}
          className="mt-12 grid grid-cols-2 md:grid-cols-4 gap-4"
        >
          {[
            { icon: Palette, label: "Art &amp; Culture", color: "bg-rose-50 text-rose-600" },
            { icon: FlaskConical, label: "Natural Sciences", color: "bg-sky-50 text-sky-600" },
            { icon: BookOpen, label: "Literature", color: "bg-amber-50 text-amber-600" },
            { icon: Microscope, label: "Frontier Research", color: "bg-violet-50 text-violet-600" },
          ].map((s) => (
            <div key={s.label} className={`rounded-2xl p-5 ${s.color} border border-current/10 flex items-center gap-3`}>
              <s.icon className="w-5 h-5 shrink-0" />
              <span className="text-sm font-medium" dangerouslySetInnerHTML={{ __html: s.label }} />
            </div>
          ))}
        </motion.div>
      </section>

      <footer className="relative max-w-6xl mx-auto px-6 pb-12 text-center">
        <p className="text-sm text-stone-300">Natamba's Family — where imagination and inquiry meet.</p>
        <p className="mt-2 text-xs text-stone-400">
          Created by <span className="font-semibold text-stone-200">NATAMBA ZHOUGGUO</span>
          <br className="sm:hidden" /> <span className="hidden sm:inline">·</span> Kisanja, Masindi, Uganda
        </p>
      </footer>

      <SocialDock />
    </div>
  );
}
