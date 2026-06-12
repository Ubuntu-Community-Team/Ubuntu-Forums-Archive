---
title: "Aspire E11 - dead mousepad"
date: 2014-09-06
forum: Hardware
---

### Post by haplorrhine on 2014-09-06
I'm about to report the bug.

After going through the [DebuggingTouchpadDetection guide]("https://wiki.ubuntu.com/DebuggingTouchpadDetection"), it seems that it's a [Synaptics]("http://www.synaptics.com/en/press-releases/acer-selects-synaptics-precision-touchpad-solutions.php") touchpad being incorrectly detected as a [PS/2]("https://en.wikipedia.org/wiki/PS/2_connector") plug-in mouse, gleaned from Xorg.0.log and further supported by the lack of response from the command-line:[INDENT]cat /proc/bus/input/devices > ~/devices

[/INDENT]

I didn't have touchpad options in *Mouse* settings at first.  They might have returned after I updated *gpointing-device-settings* through [Synaptic]("https://help.ubuntu.com/community/SynapticHowto").

---

### Post by bomtempo2 on 2014-11-03
Hey I also have problems with my touchpad sometimes it frezzes especially after suspend. And sometimes it just goes crazy moving around. After the freezing part i get problems with rebooting as it often gets stuck on the boot and i have to push the power button. Has this happend to you too? do you have any solution?

I tried some diffrent solutions but it seemed they all backfired...

---

### Post by bomtempo2 on 2014-11-03
I'm sorry to hear that :/

 I started up a new thread mentioning the boot and crazy pointer problems. Please write about your problems there!

[http://ubuntuforums.org/showthread.php?t=2251345&highlight=aspire+e11](http://ubuntuforums.org/showthread.php?t=2251345&highlight=aspire+e11)

---

