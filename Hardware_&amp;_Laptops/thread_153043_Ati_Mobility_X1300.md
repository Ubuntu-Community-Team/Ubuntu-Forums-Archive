---
title: "Ati Mobility X1300"
date: 2006-03-31
forum: Hardware &amp; Laptops
---

### Post by Synasius on 2006-03-31
Hello evryone

I have an ati x1300 on my notebook and Ubuntu Breezy 

The problem is that the latest official ati drivers don't support x1300;
so i'm looking for ati opensource drivers. do they exist?? 

Can anyone help me?

Thanks

Syn

---

### Post by sublime on 2006-03-31
change the driver in xorg from ati to vesa.  that should run your card in 2d mode.  you'll have to wait till the next ati drivers to come out that will support the card.  im in teh same boat but with an nvidia 7600gt.

---

### Post by tormod on 2006-04-24
You may have seen this elsewhere, but the new 8.24 driver (closed-source, official from ATI) is now included in the official Ubuntu repositories: sudo apt-get install xorg-driver-fglrx

It should support the X1300, but myself and many others have problems getting it to work:
[http://ubuntuforums.org/showthread.php?t=163398](http://ubuntuforums.org/showthread.php?t=163398)

Let's just hope an opensource driver for this card will arrive soon, and that it will work better...

---

### Post by tmunro55 on 2006-11-10
Well, I'm using an ATI Mobility Radeon X1300. I've downloaded the 8.30.3-1 package from ATI, and it won't install. I've created the .deb packages, I've gone through many if not all of the threads on removing, re-installing, tweaking etc. So far it looks like I'm stuck with "vesa" and 1024x768.

---

### Post by tormod on 2006-11-11
The problems we had in April were fixed before Dapper was released.

In Edgy (since you don't give any details, I suppose you're using the same) the ubuntu "fglrx" driver (from the "restricted" repository) works fine on X1300 once you have enabled fglrx in /etc/default/linux-restricted-modules-common

---

### Post by tmunro55 on 2006-11-11
Sorry for the missing details. I'm using Dapper on a Dell Inspiron 6400. It has the Radeon Mobility X1300 video card. All the linux kernel stuff, restricted drivers etc are all up to date. Wireless (8495ABG) is all working great. I can't seem to get my screen beyond 1024x768.

---

### Post by tmunro55 on 2006-11-11
After following the thread titled "Howto: Fglrx 8.26.18 Driver Install (works With Xpress Series Cards Now!)" I am now up and running. Although I used version 8.27.10 of the ATI driver, the instructions work properly.

Turns out what was blocking me was the installtion of the fglrx complained about trying to overwrite an ati file that belonged to fglrx-6-8-0. So I uninstalled that package and the 8.27.10 package installed as outined in the above document.

---

### Post by xtlosx on 2006-11-14
> **tmunro55 said:**
> After following the thread titled "Howto: Fglrx 8.26.18 Driver Install (works With Xpress Series Cards Now!)" I am now up and running. Although I used version 8.27.10 of the ATI driver, the instructions work properly.

Turns out what was blocking me was the installtion of the fglrx complained about trying to overwrite an ati file that belonged to fglrx-6-8-0. So I uninstalled that package and the 8.27.10 package installed as outined in the above document.


what documents did you follow i have the same problems...

---

### Post by ironslave on 2006-11-25
i got my x1300 running with this howto the only issue is that i crashes on logout... sometimes.. (white windowswith a greyish frame) and than freezes

[http://www.ubuntuforums.org/showthread.php?t=291464](http://www.ubuntuforums.org/showthread.php?t=291464)

so as long as you dont logout it's all good... but i havent tried the secondary monitor though

it uses the 2.28 drivers

---

