---
title: "some problems"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by tompouce on 2007-05-31
Hi!

Ive just installed ubuntu 7.04 on my dell inspiron 9300.

I ran into these problems:
- the sound from mp3s is HORRIBLE. they're full of bass and ARRRGHHH MY EARSSS!!!

- my front buttons works (volumes) but I can't ajust the sound with the little scrolling thing in the tray... and i cant with the buttons too... only the window appears...

And why sometimes when you put something on an usb key, and you remove it and after you plug it back like on a windows machine, the files arent there anymore? and in the linux machine too... always doing this to me:S Argh.

everything else is okay i guess! :P

Thanks!

---

### Post by tehBoris on 2007-05-31
> **tompouce said:**
> Hi!

Ive just installed ubuntu 7.04 on my dell inspiron 9300.

I ran into these problems:
- the sound from mp3s is HORRIBLE. they're full of bass and ARRRGHHH MY EARSSS!!!


Probably a hardware support issue... what sound card does dmesg say you have?
> **tompouce said:**
> 
- my front buttons works (volumes) but I can't ajust the sound with the little scrolling thing in the tray... and i cant with the buttons too... only the window appears...


You have to tell the sound mixer which device is the correct one. Forget how to do it in Gnome, but in KDE you right click the sound mixer systemtray icon and click "Select Master Channel".

> **tompouce said:**
> 

And why sometimes when you put something on an usb key, and you remove it and after you plug it back like on a windows machine, the files arent there anymore? and in the linux machine too... always doing this to me:S Argh.

You must use the "Eject" option on the right click menu. Other wise the files might not have been writen to the drive. The mounter deamon caches files on the local hard disk to improve performance at the cost of "it's finished copy" not been equal to it's finished copying.

> **tompouce said:**
> 
everything else is okay i guess! :P

Thanks!

---

### Post by tompouce on 2007-05-31
its like if i have 2 sound device 

intel ich6 (alsa)
sigmatel (oss)

and they both works, but on one the recording volume control the main volume WTF :P thanks

---

