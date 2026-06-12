---
title: "Digital Video over USB"
date: 2006-03-26
forum: Hardware &amp; Laptops
---

### Post by Lary Grant on 2006-03-26
I have a Samsung SC-D103 digial video camera which has both USB and firewire interfaces. I plugged the USB cable into my Breezy box and did [FONT=Fixedsys]lsusb[/FONT] getting:[INDENT][FONT=Fixedsys]Bus 004 Device 010: ID 04e8:120f Samsung Electronics Co., Ltd[/FONT] [/INDENT]However, [FONT=Fixedsys]v4l-conf[/FONT] gives me:[INDENT][FONT=Fixedsys]can't open /dev/video0: No such device[/FONT] [/INDENT]I googled the USB ID [FONT=Fixedsys]04e8:120f[/FONT] and got the following info:[INDENT]**Status:** [SIZE=3][COLOR=Red]**X**[/COLOR][/SIZE]
**Driver:** no driver available
**Comment:** This is an excellent little digital camcorder from Samsung. It has both a IEEE1394 and USB interface. It records to both digital tape or a memory stick. lsusb shows it as Bus 002 Device 004: ID 04e8:1207 Samsung Electronics Co., Ltd.
[/INDENT]( [http://qbik.ch/usb/devices/showdev.php?id=3023]("http://qbik.ch/usb/devices/showdev.php?id=3023") )

Forgive me if this is a stupid question, but... does the a big red X and "no driver available" mean I am just out of luck getting Linux to talk to this camera?

---

### Post by arnieboy on 2006-03-26
[QUOTE=Lary Grant]I have a Samsung SC-D103 digial video camera which has both USB and firewire interfaces. I plugged the USB cable into my Breezy box and did [FONT=Fixedsys]lsusb[/FONT] getting:[INDENT][FONT=Fixedsys]Bus 004 Device 010: ID 04e8:120f Samsung Electronics Co., Ltd[/FONT] [/INDENT]However, [FONT=Fixedsys]v4l-conf[/FONT] gives me:[INDENT][FONT=Fixedsys]can't open /dev/video0: No such device[/FONT] [/INDENT]I googled the USB ID [FONT=Fixedsys]04e8:120f[/FONT] and got the following info:[INDENT]**Status:** [SIZE=3][COLOR=Red]**X**[/COLOR][/SIZE]
**Driver:** no driver available
**Comment:** This is an excellent little digital camcorder from Samsung. It has both a IEEE1394 and USB interface. It records to both digital tape or a memory stick. lsusb shows it as Bus 002 Device 004: ID 04e8:1207 Samsung Electronics Co., Ltd.
[/INDENT]( [http://qbik.ch/usb/devices/showdev.php?id=3023]("http://qbik.ch/usb/devices/showdev.php?id=3023") )

Forgive me if this is a stupid question, but... does the a big red X and "no driver available" mean I am just out of luck getting Linux to talk to this camera?[/QUOTE]
have u tried doing:
```
sudo ln -fs /dev/video /dev/video0
```

---

### Post by Lary Grant on 2006-03-26
It was already linked:
[INDENT][FONT=Courier New]lrwxrwxrwx  1 root root 6 2006-03-26 12:11 /dev/video -> video0[/FONT]
[/INDENT]

---

### Post by majikstreet on 2006-03-27
Lary,
As far as I know, USB video camera support is very limited, if present at all..

I am going to buy a firewire card for my camera soon, so that I can use it. I have a similar Samsung camera. Here's the one that I am considering: [http://www.newegg.com/Product/Product.asp?Item=N82E16815104218](http://www.newegg.com/Product/Product.asp?Item=N82E16815104218)

There are many threads that tell you about using firewire and a camera. Try searching video camera firewire... That's how I found your post!

HTH,
majikstreet

edit: one site that they said is: [http://www.bxlug.be/en/articles/220](http://www.bxlug.be/en/articles/220)

---

### Post by Lary Grant on 2006-03-28
[quote=majikstreet]Lary,
As far as I know, USB video camera support is very limited, if present at all..
[/quote]

Yes, thanks!  I also figured out that I need a Firewire card!  If I had known that they were so cheap and easy to install / use, I would have saved many hours of frustration trying to get it to work with USB!  ](*,)

---

### Post by stoothman on 2006-04-11
I have updated my entry on the camera.  I have gotten it to work using the firewire port.  That was a couple months ago and I ran out of time to play.  I am going to get back to it soon and when I do I will post my instructions.  Mind you I do not use Ubuntu, but came across your post while trying to recreate what I had done before.  But in general the instructions will work I think.

Wish me luck.

---

