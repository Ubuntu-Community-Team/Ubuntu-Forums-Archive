---
title: "GRUB error 13"
date: 2009-06-10
forum: Installation &amp; Upgrades
---

### Post by Istvan D on 2009-06-10
Hi,

I have the following problem:
I use dualboot Win XP + Ubuntu 9.04, 1 HDD, 4 partitions (NTFS, NTFS, swap, ext4, in this order). I upgraded from 8.10 via update manager, converted last partition from ext3 to ext4. XP is a fresh install, GRUB was restored from LiveCD.
/boot/grub/menu.lst:

[I]## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		afacf316-5745-4a23-ade9-1bc2ad952489
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=afacf316-5745-4a23-ade9-1bc2ad952489 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		afacf316-5745-4a23-ade9-1bc2ad952489
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=afacf316-5745-4a23-ade9-1bc2ad952489 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		afacf316-5745-4a23-ade9-1bc2ad952489
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=afacf316-5745-4a23-ade9-1bc2ad952489 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		afacf316-5745-4a23-ade9-1bc2ad952489
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=afacf316-5745-4a23-ade9-1bc2ad952489 ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		afacf316-5745-4a23-ade9-1bc2ad952489
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=afacf316-5745-4a23-ade9-1bc2ad952489 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		afacf316-5745-4a23-ade9-1bc2ad952489
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=afacf316-5745-4a23-ade9-1bc2ad952489 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		afacf316-5745-4a23-ade9-1bc2ad952489
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional - magyar
root		(hd0,0)
savedefault
makeactive
chainloader	+1
[/I]

XP boots fine, but I cannot get the latest two kernels working: each time I try to use them, I get "Error 13 Unsupported or invalid executable format" I downloaded both kernels via the update manager. Kernel 2.6.28-11 works fine.
What to do????? :confused: PLEASE help!

---

### Post by zvacet on 2009-06-10
I hope [this]("http://members.iinet.net.au/~herman546/p15.html#13") will be helpful.

---

### Post by Istvan D on 2009-06-11
okay, I read the link above; via Synaptic, I uninstalled the 2.6.28-12 kernel (all components), and reinstalled the 2.6.28-13. After reboot, kernel 2.6.28-12 is not in the list any more, but with 2.6.28-13 still getting the same error, kernel 2.6.28-11 and Win still working fine. :confused:

---

### Post by fenixk19 on 2009-06-11
I have the same problem on Ubuntu 9.04, ext4 partition, amd64 architecture. Seems that the bug is in the kernel package.

---

### Post by Istvan D on 2009-06-11
what to do then? download kernel source and compile it?
besides, why doesn't then everybody scream, that the new kernel isn't working? And why isn't it fixed, if so?

---

### Post by fenixk19 on 2009-06-12
No, compiling from the source is not a solution.
The bug can be too specific, to be found so fast. I'll take a look on new kernel more deeply, when i have time.

---

### Post by PessimistByNature on 2009-06-15
I will add that my grub seems to break immediately and drop to the grub minimal bash-like line editor.  It does not give me the chance to even select from the different kernels.  If I attempt to launch the kernel via:
```
root (hd0,0)
kernel (hd0,0)/boot/vmlinuz-2.6.28-13-generic
```
it returns:
> Error 13: Invalid or unsupported executable format

If I try
```
cat /boot/grub/menu.lst
```
from the command line shown when I all I see is lots of gibberish (???8?a?*?????/ and so on)

However, if I try the same command after inserting a live usb key, it prints out properly.

At this point, I am lost as to how to proceed, and will gladly run any tests or commands needed to help shed light on this error.

---

### Post by fenixk19 on 2009-06-17
What if you try to run update-grub? But before you need to rename your menu.lst in back up purpose.

---

### Post by rohitfeb14 on 2009-06-17
i think the problem is not with the kernel pacage but your grub...
compare grub menu.lst with someone like u

---

### Post by PessimistByNature on 2009-06-17
Ok, by manually entering the lines that grub normally uses to boot the computer, I got it into recovery mode, but update-grub did not fix the problem.

Comparing the menu.lst of two different ubuntu computers I have, I see no real difference between the two, aside from the obvious (they have different kernels installed, and one dual boots with windows xp)

As some other data, on the problem computer, only 2.6.28-11 works, the other two I have installed (-12 and -13) give me the aforementioned grub error 13: invalid or unsupported executable format.  I am not sure whether this is significant.

---

### Post by fenixk19 on 2009-06-17
PessimistByNature, are you using ext4 filesystem?
I guess, that kernels, that is installed after conversion from ext3 to ext4 are getting broken. At least for me, it is so.

---

### Post by PessimistByNature on 2009-06-17
Yes, I am.

Is it only 2.6.28-11 that works for you as well?

---

### Post by fenixk19 on 2009-06-18
No, for me -12 also works, but i have installed it before conversion. And -13 after, and it doesn't load.

---

### Post by Istvan D on 2009-06-18
well, this is my problem: I thought I could install the whole again, ext4 being the default filesystem, but I didn't want to lose all my drivers, apps and settings :(

---

### Post by fenixk19 on 2009-06-18
My OS have been evolving since 6.06 and i will never reinstall it, until it is possible. I want some way to fix it without reinstalling too.
P.S. It is possible, that installing grub2 will fix the problem.  Does any one wants to try? :)

---

### Post by cat5 on 2009-06-18
Too funny - I had a power outage today, and come home to an error 13.. and yes, I converted from ext3 -> ext4 manually.

my fstab didn't change, and I'm using linux-server kernels (server install disk, not desktop)

I'm not dual-booting myself - just 2 HDD's on a SiI raid-controller (no raid) - a 40G boot/OS, and 500G data drive.

I'm not chainloading, but my 500gig was an old Slackware install - from slack8 up to 12.1, then moved everything to this new disk, upgraded it to 12.2.. and slackware-current before I had some other problems, and decided to throw on ubuntu 8.10 on a spare 40Gig, and did a dist-upgrade on the server to 9.04 a few afer it was released... so this is probably only the 2nd or 3rd reboot since I upgraded. My MythTV computer is stable after 4+ dist-upgrades, though haven't moved to ext4 on account of 700+ Gigs of movies/recorded TV/MP3... etc.


I wonder if grub is borked, or something missing from the kernels.. I'll try -11 and -12 myself. and report back.

Cat5

---

### Post by fenixk19 on 2009-06-19
I'm sure that it is grub problem. It's ext4 related code is broken so, that it can't work with converted filesystems.
I've tried to use GRUB2. It doesn't chainloading. As i think, for the same reason, that kernel don't want to load - GRUB Legacy just can't read GRUB2 image. Then i've tried to use pure GRUB2 and it finally broke my system, because all that GRUB2 was able to do is to print "GRUB" message :(
With some magic i've restored my bootloader, but now i don't have any ideas. Exept using separate /boot partion. But i dislike this way.

---

### Post by fenixk19 on 2009-06-19
Yeah! Guys, i've solved it!
I was looking on web and found, few resources, including:
  [http://ubuntuforums.org/showthread.php?t=1104822](http://ubuntuforums.org/showthread.php?t=1104822)
Then i've realized, that when i was fixing my system, i run grub-install. I've tried to boot and it works! I run just grub-install, without --recheck option, in spite of written in the link above.
This effect can be explained so: GRUB lives in MBR, but when GRUB has been updated, it didn't update the MBR. So there was old code not supporting ext4 partitions.

---

