---
title: "Major hardware upgrade -- reinstall required?"
date: 2010-10-18
forum: Hardware
---

### Post by Der Ritter on 2010-10-18
Hello folks.

So this weekend I'm essentially going to build myself a new computer. This is a complete and radical change -- Intel 32-bit to AMD 64-bit CPU, Intel to nVidia graphics, etc., etc. The only component that will be left from the old box is the hard drive (with Ubuntu installed), which I will be inserting into the new computer. 
Now I know that Windows throws up and requires re-installation and activation when it's placed under new hardware. Surely Ubuntu is better than that? Am I going to have to re-install Ubuntu the minute I plug in the new computer, or will it be able to adjust to the new hardware on the fly? I read something about having to reconfigure X for the new video card, but the post was from 2007 or something, so I would like to know if that is still the case as well.

---

### Post by cj.surrusco on 2010-10-18
You shouldn't have any problems. 64-bit systems will run a 32-bit OS fine, and you should be able to install the graphics driver on the first boot with the new system.

---

### Post by JC Cheloven on 2010-10-18
+1
I did an Ubuntu install in an external usb hard disk (please note: an install, not a liveCD-like boot), and I boot several different computers using it without noticeable issues. 
This should be pretty similar to what you're triyng to do with your internal hard disk.

---

### Post by AoSteve on 2010-10-18
I have a 9.10 USB stick that I run on three different systems..  Two of them running intel X4500HD's and one running a nVidia 8800 chip.   Also; they are different chipsets, processors, hard disks, ...   None of the machines are identical in any respect and they don't really have much of a change in performance at all.  The only problem I ran into was the intel driver didn't like loading after I installed the nVidia driver.   So it reverted to "failsafe" mode and this ended up in myself creating two different xorg.confs... 

In your case; you should be able to just install the nVidia drivers and go on without a hitch.

I even ended up running the USB on an AMD/nVidia system without a hitch and the nVidia drivers for the 8800 worked for the onboard 6400GS (or whatnot onboard nVidia chip).    :)   Ubuntu is grand for these reasons!  That disk replaced my XP version that crashed more times then I can count!

---

### Post by JC Cheloven on 2010-10-19
@AoSteve: Is it a full installation? If so, you may consider that a full install will perform a lot of R/W operations in the pendrive. It's not designed for that, and it will shorten its life. If you're fine with that (or if it's a live-cd type of "install"), no worries though.

---

### Post by AoSteve on 2010-10-19
It's a live CD that I've modified the packages on O.o.    I tell you what; you take out a lot of the useless crap (Not that it's useless to everyone but to me) an SD card will boot quick.  It's actually just an el-cheapo SD card in a reader USB dongle.  I have two copies.  If it dies; oh well!  :)   But I can take my OS anywhere I need it!

---

### Post by JC Cheloven on 2010-10-21
> **AoSteve said:**
>   If it dies; oh well!  :) 
In fact I like the spirit.
After all, we all have some 128, 256, or 512 Mb usb sticks sleeping in a drawer. They work, but will be never used again. Hey, take the best of it, burn it before it outdates! :)

---

### Post by AoSteve on 2010-10-21
exactly..  They can handle what?  About a half a million writes?  LOL   I don't care much for them anyways..  My important ones are all 8gb+   Not these 2gb pos's...

---

