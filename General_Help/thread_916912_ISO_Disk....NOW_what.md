---
title: "ISO Disk....NOW what?"
date: 2008-09-11
forum: General Help
---

### Post by dv1396r on 2008-09-11
Hello All!
I've recently downloaded 8.4.1  and have burned an ISO Image onto a DVD. That is all great, but what do I DO with the disk now? I can only get Roxio DVD burner software to even recognize the disk at all, let alone doing ANYTHING with the disk itself.
Context drop menu under Vista doesn't have "EXPLORE" or ANYTHING when right-clicking it. I am completely lost here, and am DESPERATE to get Bill Gate's junk off of this laptop. Thanks in advance!
Dave

---

### Post by Titan8990 on 2008-09-11
It sounds like you burn did not take properly. What you will do with it is boot to it. Put it in your CD drive and restart your computer. On the POST screen there is typically buttons to press for BIOS menu and boot menu. Boot menu keys are often F12 or Esc.

Hit your boot menu key and select your cd ROM drive. If the burn was successful then you will be presented with the Ubuntu menu.

---

### Post by cdtech on 2008-09-11
using a DVD is a bit of a waste for the ISO. You could just use a standard CD-R to burn to but the DVD will work. You should select the option burn image to disk and it will be ready to boot with. Place it in your drive and be sure you can boot from CD then restart your system.

---

### Post by jerome1232 on 2008-09-11
> **cdtech said:**
> using a DVD is a bit of a waste for the ISO. You could just use a standard CD-R to burn to but the DVD will work. You should select the option burn image to disk and it will be ready to boot with. Place it in your drive and be sure you can boot from CD then restart your system.

offtopic, it's a HUGE waste of space but I actually burn them to dvd's because of the faster read speeds from a dvd, the live 'dvd' environment is much, much more responsive than when running from a cd /offtopic

---

### Post by dv1396r on 2008-09-11
Thank you All who replied to this thread so quickly! I've been able to make "Boot 1st from CD/DVD Drive" the default choice and everything, but after a pause of 20 seconds or so, this Compaq Laptop fires up Vista. Is this a sure sign of a bad burn then? The only response to the disk in the drive is the roxio program that burned the ISO Image in the 1st place. After the original burn, I had Roxio verify the ISO and got a A-OK from it.
Thanks AGAIN! You guys ROCK!
Dave

---

### Post by jerome1232 on 2008-09-11
> **dv1396r said:**
> Thank you All who replied to this thread so quickly! I've been able to make "Boot 1st from CD/DVD Drive" the default choice and everything, but after a pause of 20 seconds or so, this Compaq Laptop fires up Vista. Is this a sure sign of a bad burn then? The only response to the disk in the drive is the roxio program that burned the ISO Image in the 1st place. After the original burn, I had Roxio verify the ISO and got a A-OK from it.
Thanks AGAIN! You guys ROCK!
Dave

At the very least that means it spins up the DVD determines it's not bootable then continues to fire up Vista.

A couple things to do, lets verify that your iso you downloaded is good.
md5sum it make sure the number it spits out matches what ubuntu says it should be on their site, if not redownload
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

secondly, once we are sure of a good iso, lets burn it at a good slow speed to a cd-r this time, another good small tut on burning an image (I figure better to give to much info than not enough info right?)
[https://help.ubuntu.com/community/BurningIsoHowto#MD5%20Sums](https://help.ubuntu.com/community/BurningIsoHowto#MD5%20Sums)

Then let's try and boot off it again, if you do get to the cd boot screen verify the integrity of the cd by running the integrity check.

---

### Post by mb_webguy on 2008-09-11
Also, make sure you're using the "burn disc image" option (or whatever it happens to be in Nero), and not simply burning the ISO file to a data disc.  If after you've burned the disc you open it up and see an ISO file sitting there, you're not doing it correctly.

---

### Post by cdtech on 2008-09-12
I used infrarecorder to burn my images from Vista:
[http://infrarecorder.sourceforge.net/](http://infrarecorder.sourceforge.net/)

---

