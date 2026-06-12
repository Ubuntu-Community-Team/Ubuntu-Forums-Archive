---
title: "Gateway MX3560 - Lucid Lynx, both upgrade and fresh install unsuccessful"
date: 2010-05-05
forum: Hardware
---

### Post by nlippincott on 2010-05-05
After three days, I have been completely unsuccessful in attempting to upgrade from Karmic to Lucid, and also in attempting to install Lucid from scratch. I will note my attempts here, in the event someone has some suggestions, but will drop back to Karmic (which runs flawlessly, by the way).

I was completely unsuccessful in booting the Desktop CD. I can get as far as the opening menu, and both "Try Ubuntu" and "Install Ubuntu" simply hang at a blank screen. I have tried numerous combinations of the F6 boot options to no avail.

Naturally, I tried the Alternate CD image, which does boot successfully and proceeds with an installation. However, near the end of the installation, while installing software packages, the installation fails. Thinking I might have a bad CD, I tried several times with different CD's of different manufacturers, all with the same results.

I thought perhaps that since this laptop was about 5 years old, the CD drive was beginning to have trouble. My next idea was to use the Minimal CD, then use "tasksel" to install an Ubuntu Desktop. The Minimal CD installed, and the desktop install via tasksel proceeded, installing over the Internet without errors. However, once the desktop system was installed, it resulted in the same blank screen I encountered with the Live CD.

I have tried using the command line to inspect the X Server log, naturally suspecting an X Server problem, but this log file was completely blank. No information in syslog either. Interestingly, there was no xorg.conf in /etc/X11. I tried to build one, and tinker with it, using "Xorg -configure" without success.

My last attempt... Install Karmic, then use the Internet to upgrade to Lucid. Of course, if my CD drive had problems as I suspected, I may be dead in the water anyway. I tried nonetheless.

Karmic installed perfectly. No errors, booted just fine, and I was up and running in about twenty minutes. This is the experience I have always come to expect from Ubuntu. And absolutely no problems with the CD drive.

Next, I tried to upgrade to Lucid. This was about a three-hour process, which seemed to run without problems, and finally finished and was ready to reboot. Upon rebooting, I get the purple Ubuntu splash screen, then a blank screen, then nothing. No response, and even unable to reach a console prompt. I am at the same point I reached with the Minimal CD install.

I am running Lucid on two desktop machines with no problems. I would like to run it on this laptop, but I do need a laptop that works. So it will remain with Karmic, at least for the short term.

If anyone has had success with the Gateway MX3560, I would like to know about it. Or, for that matter, I would like to know about experiences similar to mine as well. Any input would be greatly appreciated.

---

### Post by nlippincott on 2010-05-05
I thought I'd give one more thing a try... Netbook Remix. No luck. It did go a little further... stayed on the purple splash screen for 3 or 4 minutes before the blank screen.

Dropped back to 9.10, and it looks like that's where I'll have to stay. And for anyone with the same hardware, that is my recommendation.

](*,)

---

### Post by nlippincott on 2010-05-05
I found my problem... A known bug with i8xx video drivers...
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

The Gateway MX3560 has the video hardware in question. I got the installation going by adding "xforcevesa" to the boot options on the Ubuntu Desktop CD. I was then able to install the system, but it installed with the VESA video driver - not perfect, but workable for now.

Problem at least identified, if not solved. But a workaround is place. Thanks to all who took a look.

---

