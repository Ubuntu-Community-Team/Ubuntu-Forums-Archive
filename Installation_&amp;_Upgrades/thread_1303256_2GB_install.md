---
title: "2GB install"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by josefnpat on 2009-10-28
From [http://xubuntu.com/get](http://xubuntu.com/get)
> You need 192 MB RAM to run the Live CD or 128 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM at install time. To install Xubuntu, you need 1.5 GB of free space on your hard disk. Once installed, Xubuntu can run with starting from 192 (or even just 128) MB RAM, but it is strongly recommended to have at least 256 MB RAM. 

I am trying to install xubuntu 9.10 on my eeepc (2GB surf), and I'm getting errno28: No Space Left.

It clearly says above that I need 1.5GB of free space. How can I achieve this?

---

### Post by gareththegeek on 2009-10-28
x

---

### Post by kerry_s on 2009-10-28
:lolflag: 2gb, thats wishfull thinking.

---

### Post by cwsnyder on 2009-10-28
To **install** in 2G or less, you must be using an alternate installation disk, not a Live disk and it must be from either Xubuntu, Lubuntu, or UNR.  You probably are going to have to tweak what gets loaded to get the minimum necessary to get you going, foregoing OpenOffice.org in lieu of Abiword and Gnumeric, maybe using Midori or one of the lighter browsers in place of Firefox.  I think the absolute minimum install doesn't even include X for a graphical system.

---

### Post by josefnpat on 2009-10-28
> **gareththegeek said:**
> x
yyz?

> **kerry_s said:**
> :lolflag: 2gb, thats wishfull thinking.
That's off topic. It says what it says.


> **cwsnyder said:**
> To **install** in 2G or less, you must be using an alternate installation disk, not a Live disk and it must be from either Xubuntu, Lubuntu, or UNR.  You probably are going to have to tweak what gets loaded to get the minimum necessary to get you going, foregoing OpenOffice.org in lieu of Abiword and Gnumeric, maybe using Midori or one of the lighter browsers in place of Firefox.  I think the absolute minimum install doesn't even include X for a graphical system.

I will try using an alternate install. I find it very... annoying that they advertise that it takes 1.5GB, when in fact, it does not. This misinformation has made my netbook useless for the next few days.

---

### Post by earthpigg on 2009-10-28
> **josefnpat said:**
> 
I will try using an alternate install. I find it very... annoying that they advertise that it takes 1.5GB, when in fact, it does not. This misinformation has made my netbook useless for the next few days.

it isn't misinformation. i have installed Ubuntu using 600mb. granted, it didn't have any sort of graphical user interface... but it was still ubuntu!



anywho, the ubuntu remix i put together uses about 1gb of hard drive space on install. and thats an honest quote, graphical desktop included :D

---

### Post by josefnpat on 2009-10-28
> **earthpigg said:**
> it isn't misinformation. i have installed Ubuntu using 600mb. granted, it didn't have any sort of graphical user interface... but it was still ubuntu!



anywho, the ubuntu remix i put together uses about 1gb of hard drive space on install. and thats an honest quote, graphical desktop included :D

The problem is that it is misinformation, because it came from the **xubuntu** website. Not the remix, ubuntu, etc but xubuntu.

The website gives no extra information about an install, so one can safely assume that by the wording, the install is 1.5GB. What I would like to see is the number changed to a real value.

---

### Post by kerry_s on 2009-10-28
the only way your going to work in 2gb's is using a custom install with the alternate, server or mini.iso, then you can select your stuff to fit the space.

you really need to look at smaller distros.

---

### Post by earthpigg on 2009-10-28
he does certainly have a point, though, at the non-complete information provided.

---

### Post by josefnpat on 2009-10-28
Who would be the appropriate person to ask to change the detail?

---

### Post by kerry_s on 2009-10-28
i think its just never been updated from the first xubuntu. i'm running lenny xfce4 and i'm under 1.5gb installed.

so, how did you setup the drive?
cause you should skip swap, forget separate partions, just use 1 root partion on ext2.

also don't forget 2gb's is not exactly 2gb's it's smaller.

---

