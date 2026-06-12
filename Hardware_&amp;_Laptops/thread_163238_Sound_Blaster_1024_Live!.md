---
title: "Sound Blaster 1024 Live!"
date: 2006-04-20
forum: Hardware &amp; Laptops
---

### Post by RHF on 2006-04-20
I'm having a problem getting my sound card to work for me under Ubuntu "Hoary".

I followed the instructions at: [http://www.ubuntuforums.org/showthread.php?t=19307](http://www.ubuntuforums.org/showthread.php?t=19307)

This fixed it, until I rebooted, then it would lose it, then I would have to follow the last steps and re-install the deb file I had created.

I wrote a shell script to fix this, here is it's contents:

```
#/bin/sh
cd /usr/src/modules
sudo dpkg -i alsa-modules-2.6.10-6-686-smp_1.0.8-4ubuntu4_i386.deb
exit
```

I decided to use a Kernel better suited to my processor...

```
rhf@leela:~$ uname -a
Linux leela 2.6.10-6-686-smp #1 SMP Fri Mar 10 18:16:10 UTC 2006 i686 GNU/Linux

```


I recompiled the deb file for the new kernel, I followed the steps in the link I provided above, still no joy.

Can anyone shed any light on how to get my soundcard working please?

---

