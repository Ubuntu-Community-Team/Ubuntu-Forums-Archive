---
title: "when will a fix for MSI WIND Ubuntu 9.10 brightness issue be available?"
date: 2010-01-09
forum: Hardware
---

### Post by manuleka on 2010-01-09
it's been around for a while now (Karmic Koala) and it seems like there's still no fix for the MSI WIND brightness issue... 

i'm just wondering if anyone knows any updated fix for this?

i've got a U100 netbook and i find the Karmic brightness issue a real pain in the but

current fix for me is terminate gnome-power-manager but i won't get any warning on low battery :( and brightness can't be adjusted

---

### Post by kstella on 2010-01-13
I'd like to know this, too. I tried wading through the bug report over on Launchpad to see what they'd figured out so far, but I drowned instead. :(

The USB issue is a pain, too; I've blacklisted uvcvideo, but then I miss my webcam.

---

### Post by SPazzo on 2010-01-17
I'm having the same problem too.  Does anyone know of a solution yet?  (Sorry for bumping this up).

---

### Post by Munk3y on 2010-01-21
I own two MSI Wind U100 Netbooks and I solved all the brightness/lighting issues on both by updating to the latest BIOS, v1.0G. One was running 9.10 with all updates and the other was running 9.10 with no updates. After the BIOS update, both work properly.

Here's where I got my BIOS update:

Link: [MSI Wind U100]("http://www.msi.com/index.php?func=downloaddetail&type=bios&maincat_no=135&prod_no=1474")

Hope that helps!

---

### Post by jgcamp99 on 2010-01-21
The bios update worked for me too. I found a website that allows the bios update to be performed while using Windows XP. Funny, just about the only thing I use Windows XP on the netbook these days.

---

### Post by erqiyang on 2010-01-22
does anyone knows if the same bios update will solve the problem for U123H ??

---

### Post by SPazzo on 2010-01-22
> **erqiyang said:**
> does anyone knows if the same bios update will solve the problem for U123H ??

Don't use that one.  Use [this one]("http://www.msi.com/index.php?func=downloaddetail&type=bios&maincat_no=135&prod_no=1764").

---

### Post by erqiyang on 2010-01-23
> **SPazzo said:**
> Don't use that one.  Use [this one]("http://www.msi.com/index.php?func=downloaddetail&type=bios&maincat_no=135&prod_no=1764").

Hi,

Thanks. That's what I meant. Does upgrading the BIOS on U123H helps solve the problem.

Anyway, just for the record, I tested it last night. It works perfectly. The 3G modem works out of the box as well.

Though I figured that the difficult part for anyone would be how to upgrade the BIOS itself.

:-)

---

### Post by Ubunthree on 2010-02-12
I attempted to do the BIOS update last night - booted into XP, downloaded MSI's Live Update software, ran it (the online update option didn't seem to be working). It pulled in updates for some LAN thing and an audio driver, but was unable to even identify which BIOS version I have, and would neither update it nor tell me whether I needed to. Back in Ubuntu, suddenly my U100 is no longer able to mount USB devices *again,* after I thought I finally had that fixed. Meaning, when I plug in a flash drive, nothing happens, even if I restart with it plugged in, and lsusb won't show that it is there. A USB mouse will work if I start up with it attached, but if I unplug it and then put it in again, it won't be recognized. Flash drives, however, don't work at all as far as I can tell. I don't know whether this has anything to do with the BIOS issue or not. If anyone who has successfully updated the U100 BIOS can actually tell me HOW they did this, I will be grateful, and I will at least be able to eliminate that as the cause of this problem.

Thanks!

---

### Post by erqiyang on 2010-02-27
> **Ubunthree said:**
> I attempted to do the BIOS update last night - booted into XP, downloaded MSI's Live Update software, ran it (the online update option didn't seem to be working). It pulled in updates for some LAN thing and an audio driver, but was unable to even identify which BIOS version I have, and would neither update it nor tell me whether I needed to. Back in Ubuntu, suddenly my U100 is no longer able to mount USB devices *again,* after I thought I finally had that fixed. Meaning, when I plug in a flash drive, nothing happens, even if I restart with it plugged in, and lsusb won't show that it is there. A USB mouse will work if I start up with it attached, but if I unplug it and then put it in again, it won't be recognized. Flash drives, however, don't work at all as far as I can tell. I don't know whether this has anything to do with the BIOS issue or not. If anyone who has successfully updated the U100 BIOS can actually tell me HOW they did this, I will be grateful, and I will at least be able to eliminate that as the cause of this problem.

Thanks!

Hi,Ubunthree, not sure if you still need help, or if the below info is helpful.

When I did my bios update, I had to prep plenty of stuff, mainly because I don't have any copy of MS.

Hence, I got a blank drive and partitioned about 3MB of it. (For some reason which I never got to understand, larger storage doesn't seem to boot properly). Then, I went online to download a copy of MS boot disk with the MS-DOS in it.

The basic idea was to make a bootable flash drive with MS-DOS in it, which is required to execute the update.

(side note: i previously mentioned that the 3g modem for U123H works out of the box for UNR9.10 ... that's not the case as I found out. In fact, it's rather intermittent. On some boot, it works perfectly fine, but other times, it just doesn't work, despite multiple reboot. I can't get it to work, so if anyone's got any idea, drop me a note too to let me know. :-) )

---

