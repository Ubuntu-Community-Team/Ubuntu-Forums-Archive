---
title: "Question about RealTek ethernet adapter driver not loading on Ubuntu 20.04.3"
date: 2021-11-20
forum: Hardware
---

### Post by tomdkat on 2021-11-20
Hi!  On my mom's HP Pavilion P7-1380T PC ([https://support.hp.com/us-en/document/c03368473](https://support.hp.com/us-en/document/c03368473)), I have Ubuntu 20.04.3 installed.  She's been running Ubuntu, on this system, since 18.04.  Anyway, today, I booted a Manjaro 20.2 GNOME live USB drive just to see how Manjaro would run, on her system.  Everything worked perfectly well and I was able to access the Internet without any issues.  After rebooting the system to run Ubuntu again, the "realtek.ko" kernel module refused to load and the ethernet adapter wasn't recognized.  After several reboots and eventually unplugging some USB cables and plugging them back in, I was able to "coax" the system into recognizing the ethernet adapter again.

Could booting Manjaro have done something to make the ethernet adapter not recognized?  I didn't install Manjaro or anything.

Thanks in advance!

Peace...

---

### Post by TheFu on 2021-11-21
Some drivers don't properly initialize all the hardware "ports", so if you were rebooting between, without a full shutdown, it is possible that the realtek driver didn't follow the best coding practices of initializing the memory to "known values".  Lots of programmers get lazy because some compilers automatically initialize the entire address space to zeros before loading the CS/DS areas.
This issue used to happen when people were dual booting Windows and Linux with some Realtek cards/drivers too.  Haven't seen that in a number of years and I don't recall which order caused the issue. I haven't dual booted in a very long time - perhaps a decade.

---

### Post by tomdkat on 2021-11-21
Thanks for the reply! Your suspicion was spot on!  I was able to recreate the issue and simply shutting down the system, waiting a few minutes (something I chose to do), and turning it back on solved the ethernet adapter issue.  I don't do this kind of thing very often, so I'm satisfied.

Thanks!

---

