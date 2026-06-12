---
title: "Ubuntu on Compaq R4000"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by rekahsoft on 2006-06-06
Hello everyone...lately i have been working on getting my laptop (compaq R4000) fully fuctional in linux. I could not get my ATI Radeon 200M working with the ATI propriatary drivers and i also could not get my broadcom BCM4318 wireless card working. I have used many tutorials and how-to's but they did not work. (i used ndiswrapper and bcm43xx-fwcutter). I got the wireless temporarily working but when after that time it has not worked. I did modprobe bcm43xx. Anyway i was wondering if anybody has got the ATI propriatary drivers for the Radeon 200M working (and how) and the broadcom BCM4318 wireless card working (and how). Thanks

---

### Post by H.E. Pennypacker on 2006-06-06
Did you check out ndiswrapper's driver wiki list?  It may be there.

---

### Post by Zodiakos on 2006-06-07
The compaq R4000 has a broadcom 4306 I believe, not a 4318.  That's a good thing... all you have to do is download the firmware for it (search these forums for fwcutter), reboot... and it might just work automagically, assuming you haven't disabled the ubuntu default broadcom drivers.

As for the Xpress200M, there's already a few threads about it here.  I recently got mine working, it's very particular on this machine.  Be sure that you have UMA only selected in your bios (and yes, that means taking 128MB out of your system ram... sigh...), because for some reason, one of the systems on the R4000 is misrepresenting the amount of video memory available at 256MB.  If you don't, all you'll get is a blank screen and tears.

---

### Post by rekahsoft on 2006-06-08
I thaught i had to set video mode to UMA + Sideport and share 128mb ram...i am going to hopefully get it working tonight...thanks :)
btw i have a compaq R4200 and something...and it does have the Broadcom 4318 :( i can't use the firmware for it because it dosn't work properly..

---

### Post by snowpalmer on 2006-06-08
[QUOTE=rekahsoft]I thaught i had to set video mode to UMA + Sideport and share 128mb ram...i am going to hopefully get it working tonight...thanks :)
btw i have a compaq R4200 and something...and it does have the Broadcom 4318 :( i can't use the firmware for it because it dosn't work properly..[/QUOTE]

I have a Compaq R400.  I had actually no trouble at all setting up the fglrx video drivers. In fact I'm running Xgl/Compiz on here and it's working like a champ (considering I only have 256 megs of ram)

I couldn't help you on the wifi.  I have the Broadcom 4306 and it works quite well.  But for the video try this.  Make sure you have ONLY UMA enabled. It has *sometimes* worked for me to share 128 and use the 128 sideport but that's not very often. Only UMA works all the time for me.

```

sudo apt-get update 
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

```

Then reboot (thanks to OneSeventeen for this)

---

### Post by rekahsoft on 2006-06-11
Wierd, i am going to try it again tonight but i did the exact thing:
```
sudo apt-get update 
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
``` and it did not work...

---

### Post by linuxfanatic1024 on 2006-06-15
:confused: Sorry if I look like an idiot here, but I was wondering why you want the proprietary ones working. My ATI Mobilitiy Radeon 7000 works fine with the Xorg-supplied ati driver (with OpenGL and everything)... Just wondering if anyone tried this.

---

### Post by rekahsoft on 2006-06-15
No i am trying to get the propriatary drivers working...the ones that come with xorg work fine (but with no 3d acceleration).

---

