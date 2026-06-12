---
title: "Hardy Hardly Holds on to Hard Drives"
date: 2008-05-16
forum: Hardware
---

### Post by DuplexEmotions on 2008-05-16
I have been having this problem with Hardy on both of my computers, a Toshiba Satellite M20 and my Athlon 64 3700+ (socket 939) on a MSI K8N-SLI motherboard using SATA hard drives; after being in use for an indiscriminate amount of time, Hardy seems to lose the hard drive (the primary that the OS is installed on). It loses read/write support and shortly after everything locks up as it tries to read from the drive. First sign is often Pidgin telling me that my new conversation can't be logged or an inability to open programs that aren't already loaded into the ram. This problem was not present at all on 7.04, and both of the computers have a fresh Heron install. 

I've spent the last couple hours (through a few reboots) looking on the forums and couldn't find any problem like mine. Has anybody else had this problem, and if so are there any solutions you know of? I really would like to have Hardy working properly, as everything else seems to be working just fine here on the desktop aside from that.

Thanks a lot

---

### Post by DuplexEmotions on 2008-05-17
As a quick update to the problem, now both of my PCs are down. Seems hardy was trying to write to the wrong parts of the hard drive before failure; I had to repair the tables extensively to get it to boot again and the problem is becoming more and more regular. I have decided to cease using those computers to protect my hard drives until I can find a solution or I install  Sabayon, which ever comes first.

---

### Post by 00arthuryu on 2008-05-17
Heya
this sounds sort of like my problem which is also in the same category
[http://ubuntuforums.org/showthread.php?t=795787](http://ubuntuforums.org/showthread.php?t=795787)

My first sign would be that amarok would stop playing music
could it be the same problem??

---

### Post by DuplexEmotions on 2008-05-17
looks like it very well is the same problem. I have the laptop limping along right now, the desktop is getting a dose of Fedora for the time being. Here's hoping somebody has seen this before and knows what is up with it.

---

### Post by 00arthuryu on 2008-05-18
I've done the updates (kernel update included) and still no luck, I can't really live without me beloved ubuntu. Someone please help :(

After it can't read the Hard disk, It tries to remount the root partition as read only but still fails. I do not think any logs are taken as the HDD is completely unreadable/unwriteable

this happened twice just trying to post this :(

---

