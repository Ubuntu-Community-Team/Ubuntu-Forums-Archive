---
title: "Triple boot Win 7, Vista, UE 2.3"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by cappaj1 on 2009-08-01
Have windows 7 64 bit and vista 64 bit dual system each on own hard drive and want to install ubuntu ultimate 64 bit on esata external hard drive and get triple boot menu from grub or windows boot manager. 

Has anyone done this?

System is i7 with 12gb ram. Thanks.

---

### Post by quixote on 2009-08-03
What you're trying to do is non-trivial, but I'm pretty sure I've read about others successfully doing it.  I think maybe your main problem is going to be getting the computer to recognize the USB drive in time, before grub times out.  Not sure how you do that (another one of those things I saw somewhere), but there's a lot of information on the wiki [GrubHowTo]("https://help.ubuntu.com/community/GrubHowto").  Especially relevant for you may be the section about halfway down about changing the disk grub is installed to.

Not sure whether [this]("http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/") is directly relevant, but thought I'd leave that link in case it's useful.

There's also something called [SuperGrub]("http://www.supergrubdisk.org/w/index.php5?title=Boot_Problems") which might be useful in your case.

I wish I had some solid answers, but all I have are pointers.

---

### Post by Mark Phelps on 2009-08-03
Haven't done this as I have an ASUS Motherboard and have never been able to figure out how to get the E-SATA port to work ...

But, the main concern is whether or not your BIOS supports booting from an E-SATA drive.  If you know that it DOES, installing Ubuntu there should be no different than installing it on an external USB-connected drive.

---

### Post by cappaj1 on 2009-08-10
I decided to put Ubuntu on it's own drive. Any suggestions would be appreciated on steps to installation. Thanks in advance.

---

