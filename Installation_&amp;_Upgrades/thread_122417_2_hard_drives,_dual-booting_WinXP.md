---
title: "2 hard drives, dual-booting WinXP"
date: 2006-01-27
forum: Installation &amp; Upgrades
---

### Post by Footix on 2006-01-27
I'd like to install 5.04 (or 5.10, if I can find a blank in my house) onto my laptop. Since I've not got enough space on c:\ to dual-boot there, I want to install Ubuntu onto d:\. Can someone tell me how to do this without nuking Windows? If possible, I'd like a response with as little jargon as possible - I'm not really a hardware guy :)

---

### Post by Ocxic on 2006-01-27
if you already have your Hardrive partitoned, wich it sounds like you do scince you have a C: and D: drive, all you'll have to do is make sure you select you second partion (D:) and format and install to that.
this will leave you C: drive intact and you will have ubuntu on your D drive.
CAUTION: putting ubuntu on your D: drive or second partion will earse everyhtin on that partion so if you have anything there you wan to keep then move it to C: befor you do anything. doing this will alos give you a menu when you computer starts to chose iether to boot windows or ubuntu.

---

### Post by aysiu on 2006-01-27
See the fifth link of my signature and just ignore all the stuff about resizing partitions. Just make sure you pick the correct partition to install Ubuntu on. My guess is that C: is /dev/hda1 and D: is /dev/hdb1

---

### Post by Horndog on 2006-01-27
I tried to dual-boot two had drives, one with ubuntu and the other Windows XP.
My problem was that the Grub could not read NTFS. I have head success using Windows boot.ini and adding ubuntu and using the Windows boot menu. I just change the boot order in the BIOS to what ever drive I want to boot.

---

### Post by Footix on 2006-01-27
So I tried installing. First thing I found was that the installer program was too "tall" for my screen. When I got to the partitioning stage, I couldn't see anything resembling hdb. I went into manual partitioning mode, and the partition table showed something like 
[FONT="Fixedsys"]primary     500-ish KB
primary     18-ish GB (lightning bolt symbol)
logical     18-ish GB[/FONT]

I had no clue what to make of this, so I just hit the panic button and aborted the install. Where do I go from here? Forgive my n00bishness...

---

### Post by Footix on 2006-03-06
I hate to bump this, but on a sudden inspiration I asked someone at school about it this morning. As a better means of explanation, Windows can "see" the D:\ drive, but shows no files on it. However, it says that 1.78 megs of space is taken up; the guy I talked to says that it's a chunk of data Windows uses to "describe" the drive, and it's safe to nuke it. Not that I mean to second-guess him, but is he right?

---

