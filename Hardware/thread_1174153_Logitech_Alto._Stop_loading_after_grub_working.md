---
title: "Logitech Alto. Stop loading after grub working"
date: 2009-05-30
forum: Hardware
---

### Post by devmstr on 2009-05-30
I have connected my Logitech Alto wireless keyboard to my laptop through USB. It is working perfect but if keyboard is connected during loading the problem appears. After choosing OS in grub 1.5 the Linux stops loading if keyboard is connected. The message Starting Up is showing but nothing happens. If keyboard is not connected than everything ok. If I am connecting keyboard after loading screen appears, than loading continue without problems. How can I solve this problem and where I can get some additional information(may be I should analyse some logs).

---

### Post by UrbenLegend on 2009-05-30
Hmm, weird issue. Kernel hang maybe?

Try looking in /var/log/kern.log or one of the older versions of the file.

---

### Post by devmstr on 2009-05-30
There is a screenshort of my screen in safe booting mode with connected keyboard.

kern.log has only 2 lines:
May 31 00:01:16 devLaptop kernel: [  776.191963] [drm] Num pipes: 1
May 31 00:01:16 devLaptop kernel: [  776.270000] mtrr: no MTRR for d0000000,4000000 found

Other lines is about my successful booting without keyboard.

---

### Post by UrbenLegend on 2009-06-01
Hmm, I am clueless at this point. My best guess is that your IRQ settings are conflicting.

---

