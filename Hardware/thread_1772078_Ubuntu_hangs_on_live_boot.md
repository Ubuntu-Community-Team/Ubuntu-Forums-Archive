---
title: "Ubuntu hangs on live boot"
date: 2011-05-31
forum: Hardware
---

### Post by ranmat on 2011-05-31
I have an Acer Aspire one ZG5 netbook. When I put in a usb drive with 11.04 live on it, it begins to boot, but it hangs on the beginning of syslinux (where it says "SYSLINUX 4.03 2010-10-22 EDD Copyright (C) 1994-2010 H. Peter Anvin et al"). Then it just stays like that for as long as I leave it. I has a blinking cursor, but I can't type anything. Can anyone help me boot it? :(

EDIT: It ran 10.04 fine

---

### Post by Rubi1200 on 2011-05-31
Hi and welcome to the forums :-)

How did you put the image on the USB?

I recommend UNetbootin:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by ranmat on 2011-06-01
> **Rubi1200 said:**
> 
How did you put the image on the USB?

I recommend UNetbootin:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I tried it first with the method recommended on the main ubuntu websit and then I tried unetbootin. It had exactly the same problem. I used a 4GB Kingston USB stick which has done live boots successfully before and a windows vista ultimate computer to write the image with which has also done similar things successfully. I am trying to run 11.04 on a Acer Aspire One ZG5 netbook.  Does anyone know the name of the old tool Ubuntu used to provide for installing ubuntu netbook remix? Maybe that will work.

---

### Post by jopedder on 2011-07-15
Hi - did you manage to resolve this, I have the same problem - can't get past SYSLINK.... tried multiple USB sticks, multiple Live USB creators, multiple USB slots, and they all seem to work on my other laptop (and used to work on my AAO too).

---

### Post by WestCoastSunset on 2011-07-15
Yeah, me to.  I have a Toshiba Satelite A75-s1253 and I am experiencing the exact same issue.  Not even going to bother with the other methods if no one else has done it successfully.  I will just try a different distribution.  I have had too many problems with Ubuntu.  On a previous distribution that I tried installing on a desktop I had to take out half my ram just to get the install process going.

---

### Post by shouds on 2011-07-15
i'm stuck on this problem as well XD ive been tryin for days on my own to fix it but im extremely newby at this...i think somethins wrong wid the grub stuff? idk any updates on yalls situations would be nice

---

### Post by WestCoastSunset on 2011-07-16
Unetbootin worked for me on both my desktop and my laptop.  I have a sandisk 8 gig usb drive without the launchpad software.  My only issue with the livecd itself is I have to set nomodeset for my desktop, but unetbootin provides an easy way to edit the command line.

---

