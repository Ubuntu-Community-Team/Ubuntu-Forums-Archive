---
title: "VERY simple questions"
date: 2006-02-08
forum: Installation &amp; Upgrades
---

### Post by lifespurpose on 2006-02-08
Hi, am considering Ubuntu but my experience with other distros has me spooked. So here are 3 easy questions. I have poked around on the forum for an hour or so and cannot find the answers.
1. Most distros (including live CD's) get so far into the boot process and then choose a screen resolution my monitor won't support, leaving me seeing either black or a kaleidoscope. Will Ubuntu do the same? Why does everything look fine up till it goes wacko? I now have an LCD with 1024 x 768, 60 Hz. VERY generic, so why do they all do this? What is the EASY fix?

2. I now have Mandrake 10.0 in a 30G set of partitions. (Win98 in another 30G.) It worked OK last year but I tried to update it using dialup and apparently corrupted something, it hangs unpredictably (at least I haven't noticed a consistent pattern; my Win98 is troublefree). I've switched to DSL in Windows but I can't get that far in Mandrake, so fixing it online is out. That is why I'm thinking of Ubuntu. The question is, on install, I assume Ubuntu will see the Mandrake partitions. Will it try to move in and take over there (which is what I want) or what? If not, how do I prepare the HD without buying anything? (I have Partition Magic 4, which I think is limited to 8 Gig.)

3. Unrelated: Although my DSL out here in the country is only about 10x faster than dialup, this forum loads pages slower than dialup. Anybody know why?

---

### Post by aysiu on 2006-02-08
[QUOTE=lifespurpose]
1. Most distros (including live CD's) get so far into the boot process and then choose a screen resolution my monitor won't support, leaving me seeing either black or a kaleidoscope. Will Ubuntu do the same? Why does everything look fine up till it goes wacko? I now have an LCD with 1024 x 768, 60 Hz. VERY generic, so why do they all do this? What is the EASY fix?[/quote] The easy fix for this: when you first load up the CD, instead of just hitting **Enter**, type ```
boot vga=791
```

If you still end up at a black screen, press Control-Alt-F1 and then type ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by dcast on 2006-02-08
ubuntu will detect your partitions when you start the install. try using the livecd to see if your monitor will work,

---

