---
title: "Won't boot live CD or install"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by jokre on 2009-10-27
I'm trying to install Xubuntu 9.04 i386 on a Toshiba Satellite 4030CDT laptop, but it just stops all the time with the following on the screen (text mode)


[COLOR=Red]¤¤¤¤¤ Screen dump start ¤¤¤¤¤[/COLOR]


* Preparing restricted drivers...                                  [ OK ]
* Starting kernel event manager...                             [ OK ]
* Loading hardware drivers...
udevd-event[2350]: 'path_id /devices/platform/pcspkr/input/input2/event2' abnormal exit
udevd-event[1933]: '/sbin/modprobe -b pci:v0000125Dd00001978sv00001179sd00000001bc04sc01i00' abnormal exit

                                                                               [ OK ]
_


[COLOR=Red]¤¤¤¤¤ Screen dump end ¤¤¤¤¤[/COLOR]


I've had Xubuntu installed on the PC before, but with another release and that worked perfectly fine (was some years ago though).

Anyone got a clue on what to try to look for?
Thanks!
/ J

---

### Post by fancypiper on 2009-10-27
Try the disk test.  You may have a bad burn.

---

### Post by phillw on 2009-10-27
> **fancypiper said:**
> Try the disk test.  You may have a bad burn.


For the OP ...

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

has the how to. Always burn at 4X maximum speed, people have reported all sorts of 'funnies' when burning at high speeds.

Regards,

Phill.

---

### Post by jokre on 2009-10-27
OK! Thanks! I will try to burn at lower speed. I usually always do checksum calculation on downloads, but not sure if I did it this time, I will download it again and do the whole process from scratch.

---

### Post by fancypiper on 2009-10-27
You should do the md5sum on the cd as well.

---

### Post by jokre on 2009-10-27
Yepp, I'm planning to do that as well

---

### Post by jokre on 2009-10-27
No progress made. Downloaded the ISO image once again, checked the burnt CD integrity and booted it on another PC - worked perfectly ok. Tried it on the Toshiba laptop and... same error... :mad:

---

### Post by fancypiper on 2009-10-27
Run the memtest and see if you might have bad memory.

---

### Post by jokre on 2009-10-27
Memtest passed with 100%. Downloaded 8.0.4.1 and booted and went all to the desktop without any problems. Something in 9.0.4 and my Toshiba don't seem to get along.

---

### Post by fancypiper on 2009-10-27
Why didn't you choose Xbuntu 8.10? Maybe Xbuntu 9.10 will be better for you.  Just 2 days to go!

---

### Post by jokre on 2009-10-27
I just grabbed what was first at hand since I just wanted to rule out if it was the PC or the OS.

---

### Post by fancypiper on 2009-10-27
Aha! Good luck.

[Mark Your Thread as [SOLVED] After Getting Your Answer](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6)

---

