---
title: "64bit Webcam Drivers HELP!!!"
date: 2008-04-23
forum: Hardware
---

### Post by TheKeyMaker on 2008-04-23
I have been having some trouble finding drivers for my web cam so I was hoping that the forms could help or at least direct me in the right direction.

**Problem:** I'm currently running Ubuntu 8.04 x64, and want to use my Microsoft VX-6000 with aMSN.  I found forms that talk about 32bit drivers, but as you can see I need a 64bit one.  Any ideas?

Any help would be appreciated!

Thank!

Oh if this helps too, my computer does recognize it.

**lsusb:**
**Bus 002 Device 004: ID 045e:00f4 Microsoft Corp. **
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 046d:c222 Logitech, Inc. 
Bus 001 Device 004: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 001 Device 003: ID 046d:c221 Logitech, Inc. 
Bus 001 Device 002: ID 046d:c223 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000

---

### Post by Vadi on 2008-04-24
Just to make sure, install Cheese ([click]("apt:cheese")) and then launch it from applications - graphics - cheese. Does it show no preview?

---

### Post by TheKeyMaker on 2008-04-24
Well I wouldn't say it shows nothing, but at the same time all it does show is the colored lines ans static that Ubuntu uses for there monitor test.

Picture below:

---

### Post by bouchmil on 2008-04-25
I got the same problem here with cheese under 8.04x64. But i got a logitech quickcam messenger.

---

### Post by Vadi on 2008-04-25
Cheese in 8.04 completely broke for me. I know that the 0.23 version in 7.10 repositories was working fine... I'll try and see if I can get a .deb of that.

---

### Post by TheKeyMaker on 2008-04-25
Yeah if it will help. If I can just get this camera working, it would really be helpful!

Thanks for your help thus far!

---

### Post by craigsn on 2008-06-04
Did you have any luck with this?

Thanks
Craig

> **TheKeyMaker said:**
> Yeah if it will help. If I can just get this camera working, it would really be helpful!

Thanks for your help thus far!

---

### Post by TheKeyMaker on 2008-06-10
Nope... Sorry. If I get it working I will let you know. Let me know if you find out anything too. Thanks for the post!

---

### Post by steveneddy on 2008-06-10
Did you look [here]("http://ubuntuforums.org/showthread.php?t=232751")?

Usually a search of the UF or Google will deliver the desired results.

---

### Post by danielmaiarn on 2008-06-21
I'm using Ubuntu 8.04 HH and i got the same problem here.
I have a Z-Star ZC 0303 Webcam and i did everything possible to get it to work, but i failed. Installed V4l and v4l2 libraries, gspca-sources, v4l-conf. and nothing worked. BUT, when i use Ekiga i do use the webcam, when i try to open Cheese or Camorama, it didn't. I almost format the system one more time, but i give up...
What should I do to make my webcam work fine at all programs?

---

### Post by Rebootkid on 2011-01-22
This is an old thread, but for some reason, keeps showing up high in the Google ranking for me. Head on over to [http://ubuntuforums.org/showthread.php?p=10385487#post10385487](http://ubuntuforums.org/showthread.php?p=10385487#post10385487) for how I solved this

---

