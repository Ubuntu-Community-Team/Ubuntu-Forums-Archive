---
title: "intel_agp and kernel wierdless causing shutdown problems"
date: 2005-05-02
forum: Hardware &amp; Laptops
---

### Post by SalsaDoom on 2005-05-02
Hi fellas,

I'm mostly a new Ubuntu user. Been using it on my desktop for a bit, put it on my laptop replacing Gentoo. Getting lazy in my old age ;)

Anyway, I'm having a wierd little problem here. My laptop has an ATI card in it, and it works fine with it. Except that when I shutdown my laptop, as in, shut it off, it doesn't actually do the "power down" bit. It just freezes there. I've seen this before and agpgart is almost always the culprit. I looked and I'm using the intel_agp driver, but I've been unable to confirm its the problem exactly (although I'm *sure* it is.) since I cannot unload the module -- it says its in use, but not by what. Well, regardless, I wanted to custom compile my kernel anyway, but keep it mostly in line with what the base Ubuntu developers expect. So I've patched up the source code from the ubuntu repositories to what the latest 2.6.10 kernel should be. Here is my problem(s) now:  

1. When compiled, the kernel refuses to load up. It just locks right after grub. Screen goes black, stays black, nothing ever happens. Very strange. This is when I've just taken the /boot/config file and slapped it in what should be the offical ubuntu kernel sources. It does this with our without the initrd file loading. (Whats that do btw?)

2. I can't remove the stinking intel_agp module! It just won't let me, I press 'n' on it and it just redraws the screen. I want the whole agpgart driver set gone, but it just redraws the screen. Its infuriating. There is some wierd dependency thing here, but I have no clue as to the source of it. Anyone?

Thanks!
--SD

---

