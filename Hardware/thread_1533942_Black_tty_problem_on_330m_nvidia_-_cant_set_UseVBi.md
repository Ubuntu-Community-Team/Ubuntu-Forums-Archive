---
title: "Black tty problem on 330m nvidia - cant set UseVBios"
date: 2010-07-18
forum: Hardware
---

### Post by jcllings on 2010-07-18
As the tittle says, I can't seem to force UseVBios = 0 in /proc/driver/nvidia/registry. Have tried creating a *.conf file in /etc/modprobe.d containing this line:

 options nvidia NVreg_UseVBios=0

Have also tried this line in /etc/default/grub:

GRUB_CMDLINE_LINUX_DEFAULT="quite splash nomodeset nvidia.NVreg_UseVBios=0,video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"

I guess the above is probably wrong.

Clue please?
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by jcllings on 2010-07-18
> **jcllings said:**
> As the tittle says, I can't seem to force UseVBios = 0 in /proc/driver/nvidia
GRUB_CMDLINE_LINUX_DEFAULT="quite splash nomodeset nvidia.NVreg_UseVBios=0,video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"


Goign to try the above without a comma between ...=0,video=...

Here goes nuthin... 

Nope. No good.

To explain what exactly it is that I am trying to solve, I have a tty screen that loads fine from grub but flickers, wavers and looks like it has lots of shifting lines in it. I surmised that this is a screen resolution problem.

---

### Post by jcllings on 2012-04-03
This whole problem turned out to be due to a virtually useless nVidia driver. One wonders why they even bothered. Have since relegated that machine to "Windows Only". If I had a dog, I would let him chew on it.

---

