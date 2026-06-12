---
title: "Toshiba R100 runs really hot (need ACPI?)"
date: 2010-06-17
forum: Hardware
---

### Post by AI52487963 on 2010-06-17
Hey all. I was wondering if I needed to manually configure some ACPI stuff for my R100. I'm running Lucid. Basically, the laptop runs really hot in comparison to when I was running windows on it. The windows drivers had a toshiba power management driver that I'm not sure exists for ubuntu.

I know there are things I have to configure for the [R100 under a Fedora core installation]("http://www.freewebs.com/duckzland/r100.html#acpi"), but do I have to do the same stuff for Lucid?

---

### Post by shel-hall on 2010-06-17
I haven't used the Lucid version of Ubuntu on my R100, but I noticed that older versions did kick on the fan from time to time, and had short battery life, too.  I didn't chase it down too much, I switched distros.

However, there are (or were) Tosh-specific modules in the various repositories, some of which may let you run the processor slower (600 MHz), unload unused modules (if the e100 Ethernet module is loaded but unused, it sucks power.  Even ofter shutdown), etc.

-Shel

---

