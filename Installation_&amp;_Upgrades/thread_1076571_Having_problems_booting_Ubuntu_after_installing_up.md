---
title: "Having problems booting Ubuntu after installing upgrades"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by jennaeppink on 2009-02-21
I'm fairly new to Linux, I've only been using it for about a few months with no problems until now.  I am doing dual-boot on my dell precision m2300 with ubuntu hardy heron and windows.  After installing some updates last night, I tried to shut it off and it froze and wouldn't shut down.  So I did a hard reset, only to have my computer start beeping at me incessantly.  I tried resetting again, this time I was able to get past Grub, the Ubuntu load screen came up and finished loading, but then the screen went completely blank.  After that I tried booting ubuntu in "repair mode", and it worked ok for a few minutes, but eventually froze and I had to do another hard shut down.  I did that several times trying to poke around and see if I could figure out what was wrong, but it kept freezing.  Now my computer won't even boot at all.  I turn it on, and get a blank screen, usually the first thing to come up is the dell logo, and it loads, and then grub comes up, but the dell logo screen doesn't even come up now.

On a side note, if I can get to Grub, I can load Windows with no problems, so I'm pretty sure this is an Ubuntu issue. 

Any help would be much appreciated!

Thanks!
Jenna

---

### Post by dstew on 2009-02-21
I am a bit confused. Do you get the Dell logo screen? If not, there is serious trouble, because that screen is produced by the BIOS, and should come up even if there were no disks in your computer! So, that can't be a problem with Ubuntu.

If you get the grub menu, but only Windows works, then perhaps Ubuntu is mis-configured. Boot Ubuntu in recovery mode, and see if you get a command line. If you do, try```
sudo apt-get update
sudo apt-get upgrade
```and tell us what happens.

---

### Post by ezacon on 2009-02-21
If you d'ont get Dell Logo, It is probably a hardware problem.
Intermitent bios start problem are often produced by faulty capacitors (you can visualy check for damaged one). You can check the 4 diagnostics leds on the back. Resulting fault code can be found on the dell web.

---

