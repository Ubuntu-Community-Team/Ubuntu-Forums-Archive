---
title: "Issues with Xorg 7.3 Autodetection"
date: 2008-05-16
forum: Hardware
---

### Post by divideoverflow on 2008-05-16
I am currently working on my first bit of GNU and Ubuntu evangelism-- installing Hardy Heron on a friend's old Compaq Presario 700, with a Duron Mobile (1 GHz), 256MB SDRAM, and unfortunately, an S3 display adapter. 

lspci reveals (specifically):  *S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK) (rev 01)*

At least on this laptop Xorg 7.3 does not automatically use the appropriate driver (savage). Running displayconfig-gtk and checking the "Graphics Card" tab shows that no driver is selected in the "Driver" drop box. Attempting to use displayconfig-gtk to select the driver causes the tool to crash. Once I specify the driver in xorg.conf and restart X however, the driver loads. Running displayconfig-gtk now shows "savage" as the driver currently in use on the "Graphics Card" tab, and this poor laptop's CPU can finally focus on doing things *other* than drawing the screen. :)

I figured I'd post this for anyone having slow performance or graphics issues in Hardy.

---

