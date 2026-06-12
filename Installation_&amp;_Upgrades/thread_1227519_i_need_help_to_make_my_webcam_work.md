---
title: "i need help to make my webcam work"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by Maios on 2009-07-30
plz help me letting my web cam work ... am new here and don't know how to do anything
i just bought a cam ' live! cam chat '' and when i inserted  the installation CD into the CD-ROm drive .. it did not worked as the manual said !! i tried to figure out why but i coudln't 
i really need help here cause it seemd that i know nothing about this thing!! 
plz help me

---

### Post by running_rabbit07 on 2009-07-30
Have you already tried just plugging the camera in?

Chances are your install cd is for Microsoft not Linux.

---

### Post by Maios on 2009-07-30
yes i pluged it in ... and there is nothing :(

---

### Post by running_rabbit07 on 2009-07-30
I don't have a webcam hooked up but I just did a search in Synaptic Package Manager under System>Administration menu and there are a few different webcam programs there. Search through and find one that you think will work for you and give it a try.

---

### Post by bcschmerker on 2009-07-31
> **Maios said:**
> plz help me letting my web cam work ... am new here and don't know how to do anything
i just bought a cam ' live! cam chat '' and when i inserted  the installation CD into the CD-ROm drive .. it did not worked as the manual said !! i tried to figure out why but i coudln't 
i really need help here cause it seemd that i know nothing about this thing!! 
plz help meBad choice of a camera; to my knowledge, the "Live! Cam Chat" is NOT supported in any of the packages available in any Ubuntu version.  Check out the [LinUX USB Video Class](http://linux-uvc.berlios.de/) page at BerliOS.de (hosted by Fraunhofer GmbH) for Webcams supported under most LinUX distros.

I recently installed a [Dynex DX-USB1C webcam](http://www.dynexproducts.com/) and, notwithstanding CamServ's crashing upon unexpected error conditions such as a streaming-link break, it operates pretty consistently.  The UVCVideo source package from BerliOS includes improved versions of several drivers already available as Debian-Source packages (typically BZip2 tape-archives) in the Ubuntu repositories.

---

### Post by no2498 on 2009-09-08
dont give up yet
try it in the termial
type 
gstreamer-properties
play with the video v4l and v4l2

---

