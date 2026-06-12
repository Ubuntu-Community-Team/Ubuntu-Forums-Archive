---
title: "Can Only Access a Hard Drive through Linux"
date: 2012-12-08
forum: Hardware
---

### Post by Spirrwell on 2012-12-08
Okay the first response I'm sure I'm going to get is that I have my hard drive formatted to ext4 or the like which is not the case.

I have a 1 TB hard drive that I can access just fine through Ubuntu 12.10 and Linux Mint 13. I'm actually currently quadruple booting among three hard drives with Ubuntu, Linux Mint, Windows 7, and Windows 8. Windows 8 is on my TB hard drive and it was working just fine and I had no problems with it. I went over to Ubuntu to do some programming in Code::Blocks because the program I was trying to compile wasn't working properly under Windows 8. I went to reboot into Windows 7 today and I find that I can't access drive E:\ (My TB drive in Windows 7)

I also can no longer boot into Windows 8, it will restart and if I try it again it will attempt repairs, but it says my hard drive is locked. But again, I can use it just fine in Linux and I can transfer files and everything. I'm dumbfounded. Anybody have an idea? I searched Google and I saw somebody go through a similar problem and they went on a wild goose chase with using the install DVD, using third party programs, people saying it's a hardware problem, etc. But I have Linux here proving that my hard drive is just fine.

---

### Post by oldfred on 2012-12-08
Are you trapped by the new Windows feature that makes it boot really fast? 

Which just is that it always uses hibernation, just two levels of hibernation either full or partial?
And issue could apply just dual booting Windows 7 & Windows 8.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by Spirrwell on 2012-12-08
Well that certainly explains a lot of things even a problem I had a few weeks ago when I had somehow lost a few GB of things that I had installed under Windows 7. 

Anyway I managed to get it going again by actually doing an automatic repair as opposed to the Refresh and Reset options that came up by default. I disabled the hybrid boot. Hopefully it'll be fine now.

---

