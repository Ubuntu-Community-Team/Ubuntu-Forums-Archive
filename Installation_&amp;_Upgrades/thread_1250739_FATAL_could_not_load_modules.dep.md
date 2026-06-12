---
title: "FATAL: could not load modules.dep"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by m_ghv_geo on 2009-08-26
i have new HP notebook pc dv2-1110us 
right know am trying to install ubutnu no matter what i do i can't boot from cd. i know my cd is ok because last month i installed ubuntu on my desktop pc.  also tried from the sd card but same error.
first errors  
first line says 
[     0.540002] ..MP-BIOS bug: 8254 timer connected to IO-APIC
second line says
[     2.000028] ata1: softreset failed (device not ready)

second fetal errors say
modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory 

modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory 

i browsed by built in shell /lib/modules/2.6.28-11-generic/
and i found modules.dep looks ok i tried cat modules.dep and it gived me tones of directores i thnik it is ok 

does someone knows what to do in this case please reply  :confused::(

---

### Post by confused57 on 2009-08-26
See post #2:
[http://ubuntuforums.org/showthread.php?t=892449](http://ubuntuforums.org/showthread.php?t=892449)

A Google search of your error "MP-BIOS bug: 8254 timer connected to IO-APIC" showed several links, if you might want to follow up on some of them if the above doesn't work.

---

### Post by mr_raider on 2009-08-27
amke a bootable USB from the ISO and use that to install OS. When it boots from USB, during the splash screen (ubuntu logo) pull the USB stick out, count to three and put it back in.

---

### Post by abePdIta on 2009-09-04
Hey Mr Raider!! Your "one, two, three" trick works like a charm! =) Are you an archimage??
Thank you very much!

---

### Post by biggz81 on 2009-09-16
Holy cow, he is an archimage...I have a usb DVD drive, and the "count to three" trick worked with that as well.

Thanks!

---

### Post by mr_raider on 2009-09-18
Just don't ask me why it works. But Ubuntu should seriously address this issue. I never had it in 8.04 or 8.10. Plus it seems to be restricted to the AMD 770/780/790 chipsets.

---

### Post by gringoise on 2009-09-27
i can't belive it. It works. :P

---

### Post by SUparJErk on 2009-09-27
Solved my problem with 9.04 Jaunty installing from a USB DVD drive, too. That's so silly.

---

### Post by the_guv on 2009-10-08
> **mr_raider said:**
> amke a bootable USB from the ISO and use that to install OS. When it boots from USB, during the splash screen (ubuntu logo) pull the USB stick out, count to three and put it back in.

God's teeth!  How bizarre.

mr_raider, you have become a noted guest at my blog, where I couldn't resist this ridiculous little story .. [COLOR=MediumTurquoise][Jaunty Install Problem with AMD Laptops]("http://guvnr.com/pc/modprobe_fatal_jaunty_install/")[/COLOR]

Thank you, kindly.

BTW, I still get the error messages, but not the crash, with the Karmic install .. so the chaps have been doing something with the kernel, 'spose.

---

### Post by jimjavad on 2009-10-19
It was great solution how did you find that?

I was using USB memory and it works fine with that too
Really thanks

---

### Post by mr_raider on 2009-10-20
I recommend picking up KArmic ASAP once it's released for dv2/dv2z owners. I've been using the beta for 1 week.

Not only does it solve the aforementioned install issue, everything else works. Wifi, webcam, sound right out of the box. HDMI audio is recognized in the new sound prefs utility. ATI drivers (fglrx) that install by default seem to work too.

What's really cool is now suspend and hibernate work, as well as close the lid to suspend.

---

### Post by sideaway on 2009-11-17
Thanks mr_raider,worked a treat! :D

---

