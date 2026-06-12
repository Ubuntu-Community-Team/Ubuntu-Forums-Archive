---
title: "Dell Inspiron 9400 - Installation hangs on Splash Screen - 6.10"
date: 2007-01-15
forum: Hardware &amp; Laptops
---

### Post by Rhawi Dantas on 2007-01-15
Hey folks...

I've been struggling with the 6.10 version since a month, I think, trying to get this thing to work on my laptop and nothing.
The little progress bar gets stuck after some time sliding from one side to the other on the screen... It just stops moving and then nothing. I've also waited for several minutes to see what was going to happen.

Already, changed the parameters to the kernel removing the splash and adding the break=bottom... Already downloaded from many sources, Brazil, Germany, USA and nothing...

I've also tried the alternative cd and 64 bits one... The alternative worked but I want the Desktop normal one... This thing gotta work for god sakes...

I'm already downloading, sadly, OpenSuSE 10.2 to give it a try that is impossible to be happening...

Saw also in the ubuntu laptop testing team that works perfectly with the same brand/model of my laptop...

I'm out of ideas... Can someone, please, help me ?
Otherwise go back to suse ? Noooo :P

---

### Post by PurplePenguin on 2007-01-15
Doesn't the alternative disc install the same things as the normal installation disc?  I was always under the impression that it did, although I've never used it.

---

### Post by Rhawi Dantas on 2007-01-16
Yeah, in a way it does...
But when I'm turning off the computer it also has a problem to get the screen stuck. And I WANT the desktop cd to work :P hehe

That is not normal that one cd works and the other one not...

---

### Post by PurplePenguin on 2007-01-16
Did you try booting with your disc and checking the cd for errors?

---

### Post by Rhawi Dantas on 2007-01-16
yeah, i already did that...
burned also different cds from different architectures from different sources with multiple speed...
Nothing works with this crap... gosh...
The old ubuntu 6.04 used to work... but i want the new one :P
something gotta work with this

---

### Post by Rhawi Dantas on 2007-01-22
hey people try to help me out...
can't get stuck with opensuse on my notebook, although it's been a long time since i last used kde and it's great :P

---

### Post by Rhawi Dantas on 2007-01-23
It happens that i was getting the following message:

soft lockup detected on CPU#0!

I found out disabling the splash, or deleting the parameter, on the installation screen when you press F6.

I just disabled the wireless on the BIOS and everything went smoothly...

Also this guy did the same, thanks to him
[http://ubuntuforums.org/showthread.php?t=322180](http://ubuntuforums.org/showthread.php?t=322180)

---

### Post by dom on 2007-02-25
Also have an inspiron 9400.

I have been using the laptop fine for the most part. have noticed a slow boot.

It does recover after a while for me, including the cd boot, without bios tweaks :)

I have also noticed a boot hang (If i have hibernated another os on this multiboot system) with a message saying "soft lockup detected on CPU#0".

Wireless is working in WEP, but not WPA yet. (intel 3945abg).

Graphics is ATI Mobility Radeon x1400

---

### Post by dom on 2007-02-25
the hangs i am experiencing are happening after the boot message about 'configuration network connections'. So, though it boots, it's a slow boot and i probably still have a wireless related issue of some sort

---

### Post by Lord Crow on 2007-03-20
I got a 9400 with an Intel 945 gm graphics on board. I'm trying to use the live CD but it gets so far then get an error. X-Server or some swap error. This is so frustrating as I'm dying to know what this os is like and want to ditch windows but obviously i'm some way off tht.

---

### Post by Lord Crow on 2007-03-20
I also now get a Swap error now, please can you point me in the right direction?

---

