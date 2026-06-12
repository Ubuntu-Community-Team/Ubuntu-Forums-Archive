---
title: "New Kernel 2.6.29.1: Black Boot Screen with vga=795 mode"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by TheExplorer on 2009-04-11
Just upgraded Ubuntu 8.10 default kernel to 2.6.29.1 taken from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
Reinstalled the latest stable NVidia driver and I'm getting black screen when booting in verbose mode with **vga=795** option. It is working with the old kernel but not with the new one actually. Seems that this was a problem in a previous Ubuntu concerning **vesafb** or something. Do I have to update some config or what?

P.S. When reinstalling NVidia driver on a new kernel I get a warning about different 'gcc' versions used and an option to continue. The driver compiled without errors btw.

---

### Post by TheExplorer on 2009-04-11
bump, please...

---

### Post by TheExplorer on 2009-04-12
:-k

---

### Post by renkinjutsu on 2009-06-13
same problem here.. it works in verbose if i take out the vga addition, but i'll get crappy huge fonts in the terminal screens

WITH the vga=795 added, it's blank on boot and also blank when i go to screens alt+ctrl+F* but F7 works fine of course.

---

