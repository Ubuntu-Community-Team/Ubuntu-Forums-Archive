---
title: "lm-sensors and vt1211: A small nightmare."
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by keithjr on 2006-06-05
Ok guys, I've been working on this for several hours and have had absolutely zero success.  I'm calling out for help now.

I tried to [install and configure lm-sensors]("http://www.ubuntuforums.org/showthread.php?t=2780&highlight=lmsensors") so that I could get info on my cpu temperatute, fan speed, etc.  When it ran it found that I needed a module called vt1211 to get that information.  

Since then I've been fighting an uphill struggle trying to acquire it.  I only found two other threads here that even mention it, and have found [this site]("http://hem.bredband.net/ekmlar/vt1211.html") that details the 2.6 port for the software in question.  Nobody, however, is willing to give a detailed explanation of how to get the module built. :confused: 

  I have a .c file (the older version) which will not make because of apparently missing header files, which was supposed to be a problem solved by getting the older version of the driver's code... I guess not...  and I have a slew of choices of kernel patches, NONE of which includes the 2.6.12 kernel upon which I am currently running in Breezy.  I got the kernel source and compiled the source tree already but I have no idea what to do with it.

Please, somebody, point me in the right direction.  I'll happily provide any necessary info.

---

### Post by keithjr on 2006-06-06
I think I've figured out exactly what I need to do if I can just get the source code for the driver to compile into a module.  Can anybody grab one of the sources from the link above and just make it into a Breezy-friendly (2.6.12-10) kenrel module?

edit:  Okay, I'm getting a little frustrated here.  Does the fact that the creator of the vt1211 2.6 port failed to make a 2.6.12 version of the kernel patches he provides mean that I have to upgrade my kernel to one that he did support?  SOMEBODY out there must know...

---

