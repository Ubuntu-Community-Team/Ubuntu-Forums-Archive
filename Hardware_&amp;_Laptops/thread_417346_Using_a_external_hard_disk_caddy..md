---
title: "Using a external hard disk caddy."
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by Nevermore Burning on 2007-04-21
OK, i have a external ha5d disk caddy which contains my old hard drive (I have just got a new one and installed feisty on it). when it is plugged in, it mounts the windown partiiton, the linux partition and teh recovery partiton. But it will nnot eject. I will unmount them but hey will nto eject, and the devices stay up even when tehdrive is pulled out.

Any idea why this is happeing. On windoze and os x the drive just appears as the first partition (the windows one)

---

### Post by F-3582 on 2007-04-26
I have a similar problem. I use Feisty, too and since the upgrade I can't eject my Maxtor HDD I put into a USB 2.0 case, anymore. I have two partitions on it, one ext3 and a smaller FAT32 one.

When I right-click and eject one of the drive symbols, I get an error message ("Device not mounted") and the drive appears again. The only way to eject it is selecting both drive symbols at once and eject the simultaniously. This gives me two error messages, but at least the drive is ejected, now. Unfortunately HAL won't recognize it anymore until next reboot.

---

### Post by skaboss on 2007-04-27
Same problem here since the upgrade to Feisty...
(The only problem i encountered, i must say !), but it is quite annoying. I wonder if someone did post a bug report.

---

### Post by allwin on 2007-04-27
Yes, it's annoying a ton of people who upgraded.  I was out on launchpad earlier this week and there's a ratsnest of bug reports and more finger pointing and handwaving than you can shake a stick at.  Bottom line is, go to a terminal and use a "sudo umount" command to take the device offline.  There is  tweak one can make to one of the rules files which governs whether USB devices need EJECT or UNMOUNT commands but the way I read it there's some controversy that changing the file yourself is the right thing to do.  As they say with Myspace bugs, SIT IT OUT, well, that's what I plan on doing.  Meanwhile the command line always does the right thing so far that is...

---

