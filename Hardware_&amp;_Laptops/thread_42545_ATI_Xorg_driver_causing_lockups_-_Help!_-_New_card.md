---
title: "ATI Xorg driver causing lockups - Help! - New card recommendation??"
date: 2005-06-18
forum: Hardware &amp; Laptops
---

### Post by speedsix on 2005-06-18
Just spent ages trying to diagnose random lockups in Ubuntu, the machine would hard lock always when resizing windows, I could replicate it every time.

I have got round this by changingmy Xorg.conf to use the 'vesa' driver instead of the 'ati' one. Obviously this isn't ideal, mplayer video playback doesn't function properly. Card is ATI Radeon 7000

I'm not sure I understand Linux video drivers, would I be correct in saying the 'ati' driver used by Xorg is actually an open source reverse engineered driver supplied by Xorg themselves?

If so what is the 'radeon' driver for? This has the same problems.

I tried downloading the 'fglrx' driver from the Ubuntu repository but X won't even start with these, the docs don't actually list the 7000 as a supported card.

What are my options, do I need an updated 'ati' driver from Xorg?


If not I will replace the card, I don't need a gaming card, compatibility is most important, only used ofr 2d so cheap and need dual monitor support.

Stick with Ati or nVidia?


Obviously I would like to get the current card working.

Thanks

Dom

---

### Post by diebels on 2005-06-18
Don't know about ATI. But "Matrox G400 max" rocks in linux for 2d, video-playback, hi res console, old games and dual analog monitor. Try to get a cheap used one.

---

### Post by sapo on 2005-06-18
You should try the new ati installed.. but make sure to remove the xorg-fglrx and the linux-restricted-modules before installing it..

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

---

### Post by speedsix on 2005-06-20
Hi, this driver refuses to work, it doesn't list the 7000 as a compatible card.

What is considered the most compatible with linux, nvidia or ati?

---

### Post by drummer on 2005-07-31
[QUOTE=speedsix]Hi, this driver refuses to work, it doesn't list the 7000 as a compatible card.

What is considered the most compatible with linux, nvidia or ati?[/QUOTE]
 Nvidia is aparrently much easier to install 3d drivers for, ati is a real headache sometimes. I have an ati radeon 9250, tried the drivers once and couldn't get them to work. Nvidia as a company seem to support their linux drivers/development more than ati do.

My card works fine using the xorg ati drivers i think, as long as i don't need 3d hardware accelleration. I have experienced a few lockups or xorg, requiring a hard restart.. but not too often. The next graphics card I get will most likely be nvidia. And perhaps I'll try the ati drivers once more, now months down the track, as there have been new releases of the ati drivers that might fare better for me.

---

### Post by nemnivus on 2005-07-31
Just get the cheapest Nvidia card you can find with dual head support.  I'm assuming you could find something for under 30 dollars if you checked pricewatch.  Twinview using the Nvidia binary drivers is currently the best solution for running two monitors on one card under Linux.  Matrox works, but the HAL layer required by their drivers is difficult to get working with 2.6.

---

### Post by drummer on 2005-08-01
Just an update on my ATI situation, I tried the newest ati drivers from the ati website and they worked fairly easily after following this how to: [http://ubuntuforums.org/showthread.php?t=32495](http://ubuntuforums.org/showthread.php?t=32495)

Note that I had to do "sudo modprobe -r fglrx" before installing (it didn't work the first time I tried), also I added the video overlay option in the driver section of xorg.conf to get mplayer and tvtime working.

I know the drivers don't work with 7000 series cards, but I thought I'd say that the ati drivers are MUCH easier than they used to be, from what I remember.

---

