---
title: "CD wont even boot"
date: 2007-04-11
forum: Hardware &amp; Laptops
---

### Post by Stolidusx on 2007-04-11
Im running on a Toshiba Satellite A45 series with 512mb ram, 60gig hd, Mobile Intel Pentium 4 processor  2.80 ghz running microsoft xp and I want to completely install Ubuntu and get rid of xp since this isnt my main computer im willing to lose everything and not care.

When I put the cd with the Ubuntu files on it in my computer and restart it nothing happens it restarts the same way it always does.  This same thing happens on my other computer which has the following specs

Gateway MX6453, AMD Turion X2 Mobile processor, 1.6 ghz, 2 gb of ram, windows xp media center edition.

This one I want to install linux on after I know how it works and everything, neither will load the disk though, Im wondering if im doing something wrong because I feel really stupid.

Any help would be appreciated thanks.

---

### Post by floke on 2007-04-11
Some things to try...

(1) Does the CD even try to run? If not you need to set the bios to boot up from the CD. When you boot up you'll see quickly a message saying something like press F12 to enter setup. Press this as soon as the PC comes on. You'll either be presented with a 'highlighter' that you can move to an icon of CD, Hard Drive etc. (in which case select CD and press enter), or a technical-looking screen - here you need to find the boot order (eg HDD-CDROM-USB) and make sure that CD comes first.

(2) If it tries to run but doesn't work - check the integrity of the disc by selecting option 2 (i think) from the menu; or try a reburn at the slowest possible speed. If this fails try downloading again since you could have errors on it (it happens and its happened to me a few times).

(3) If this fails then you need to get hold of the alternative installer rather than the LiveCD and use that.

---

### Post by Mack Mirillo on 2007-04-11
I don't know if this applies to you or not, but my father made this mistake, so maybe I'll say....  You can't just copy the files from a disk, I think.  I'm pretty sure you have to write directly from a .iso file, to end up with a bootable disk - the disk will be missing what's called a boot sector if you just copy the files to it. You can download the .iso from [www.ubuntu.org](www.ubuntu.org) .

---

### Post by Stolidusx on 2007-04-11
yeah i just wrote them to a disk, I will look into this...btw that website is some african civil service site :)

---

### Post by heimo on 2007-04-11
> **Stolidusx said:**
> yeah i just wrote them to a disk, I will look into this

This guide may be helpful:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Stolidusx on 2007-04-11
its reburning now and i found a nice tut here

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

this helped me a lot and it has more tuts for installation and whatnot thanks for the help everyone

---

### Post by heimo on 2007-04-11
Yeah, those pages are maintained by [aysiu]("http://ubuntuforums.org/member.php?u=21941"), member and moderator of this forum.

---

### Post by Stolidusx on 2007-04-11
lol wow Im having good luck today Im getting to installation screen now!! Which is a success for how far ive been getting all day but now

ERROR!!!

BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)



Im guessing this is a problem with the downloaded ubuntu file being corrupted, can someone confirm so I can download for the 4th time :)

---

### Post by Truefire on 2008-03-15
For the Gateway, you need the alternate installer.

---

### Post by Truefire on 2008-03-15
Use the alternate installer. Works on my Gateway, same model.
Been using it on this baby for a year.

---

