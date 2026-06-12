---
title: "Pentium II 366MHz - 1fps video playback"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by jarthurs on 2007-12-30
I've recently resurrected an old Dell Inspiron 7000 (Pentium II 366MHz, 320Mb RAM, ATI Rage LT Pro video) and installed Xubuntu on it as a basic web browsing machine. Everything works fine with the exception of watching website video for example YouTube where I get about 1fps. 

Is this just a limitation of such a slow machine? I changed the video driver to ATI Mach64 (Utah) as it had defaulted to Vesa but the video playback is still a non-runner. I've tried installing the Rage LT Pro driver but cannot get it to work at a resolution above 800x600 despite manually tweaking xorg.conf.

01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)

I believe this laptop has some form of hardware acceleration for DVD playback which meant it could decode DVD Video under Windows 98 but I can't find any evidence of it under Xubuntu.

Am I asking too much of this elderly beast or do I have the wrong drivers installed?

Regards,
Jason.

---

### Post by foolsh on 2007-12-31
driver direct rendering for the mach64 version of ati cards is not included in the recent release of xorg.
there is a thread about compiling ati mach 64 drivers here some where
[http://ubuntuforums.org/showthread.php?t=7200](http://ubuntuforums.org/showthread.php?t=7200)
best of luck

---

### Post by kinston on 2008-02-08
Have you had any luck?  I have the same machine, well almost.  Dell Inspiron 7000, 333mhz cpu, 192mb ram, 10GB HDD, and the exact same video card.  The video is very choppy in youtube and even in local playback.  I was looking into Xfree86 but the installation instructions didn't make sense.  So I'm here now.  If I could get the video to stop being choppy this machine would be the Ultimate Dinosaur.  Well, if you found a fix please post the instructions.


Thanks

---

