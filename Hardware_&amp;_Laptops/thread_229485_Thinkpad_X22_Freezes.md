---
title: "Thinkpad X22 Freezes"
date: 2006-08-04
forum: Hardware &amp; Laptops
---

### Post by tzadokan on 2006-08-04
I have been using Ubuntu/Kubuntu/Xubuntu for a while now on my notebook (Thinkpad X22), but for some reason the Thinkpad freezes randomly, it does it no matter which desktop environment I am using. I can't find a pattern to the freezes, does anyone have some advice? I just can't seem to find a solution for this problem. Thanks.

---

### Post by sprucegum on 2006-08-05
same problem here, im running an updated version of dapper from may 23.  Just got back from travelling without my laptop.  It was freezing before I left,  I updated it today when I got back and thought the problem was fixed but I have had one freeze since,  it seems to be better,  I hope one of us can find a solution.

---

### Post by raf-it on 2006-08-05
i've de same problem

---

### Post by sprucegum on 2006-08-06
Maybe the best solution is to move back to breezy until the bugs are worked out.  Do you guys have visual artifacts on buttons?

---

### Post by IrishGangsta on 2006-08-06
I have a similiar problem.  My laptop (Dell Inspiron 6000) is very laggy.  I am using Dapper Drake and i have 4 desktop environments. I have Gnome, Kde, XFCE and XGL/COMPIZ.  Most of the time i am on gnome but programs open very slow and don't respond right away.  I have 508 MB RAM and only 5MB free.  I was wondering if the same reason your guys laptops freezes is the same problem i am having...

The CPU usage is unusally high and alot of RAM memory is being using causing it to lagg and also freeze.

---

### Post by sprucegum on 2006-08-06
searching through the forums I found this post [http://www.ubuntuforums.org/showthread.php?t=193283&page=5&highlight=freeze+dapper]("http://www.ubuntuforums.org/showthread.php?t=193283&page=5&highlight=freeze+dapper")

ddumanis posted

>  I had this problem with a Dell 640C with a Mobility Radeon 7500. I solved it (I think) by doing:

sudo dpkg-reconfigure xserver-xorg

and manually picking the VESA driver instead of the ATI driver (which is what the live CD installed).

So far I've been able to watch DVDs, use mail and openoffice, etc. without a crash.

I'll post updates here. Meanwhile, try it--it couldn't hurt and actually improved my screen video quality. (No more funky stripes in dialog boxes.)

Daveh

I did this and have not experienced a crash yet, hopefully this is the solution.  Im gonna send a thanks over Daves way right now.  :D

Edit:  2 days no crash, mission accomplished.

---

### Post by Zhengtonic on 2006-08-18
I had the same problems until i fixed the xorg.conf like that ...

Section "Device"
	Identifier  "Card0"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "Radeon Mobility M6 LY"
	BusID       "PCI:1:0:0"
	Option      "DDCMode"      "on"
      Option      "BIOSHotkeys"  "on"
	Option      "pci retry" 
	Option      "AGPMode"      "4"
	Option      "AGPFastWrite" "on"
	Option      "BIOSHotKeys"  "on"
EndSection

3D still sucks, but the average X22 owner hardly uses 3D ... i think

---

### Post by sprucegum on 2006-08-28
I changed my configuration over to yours Zhengtonic,  played around with it a little in hopes of getting 3d working.  DRI isnt loading,  I think 3d would work if that was loading.

---

### Post by sprucegum on 2006-08-30
I just had an epiphany!  3d works!  all I had to do was change the color depth from 24 to 16!!!

---

### Post by ssalman on 2006-09-28
Just to post some of my experiances... I have an x22 thinkpad and so far I could get ubunutu 6.06, kubuntu 6.06 running on it. on the other hand xubuntu 6.06 will always freeze during install.

update -- 

I used Zhengtonic's configuration and set the color depth to 16 as sprucegum said, and it works great... Thanks!

---

