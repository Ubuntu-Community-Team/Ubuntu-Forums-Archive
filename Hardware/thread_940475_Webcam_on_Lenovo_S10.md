---
title: "Webcam on Lenovo S10"
date: 2008-10-07
forum: Hardware
---

### Post by puredeviation on 2008-10-07
Hi, I received the Lenovo Ideapad S10 in the mail this morning and I decided to wipe the drive clean and install Ubuntu on it. The problem that I ran into after installation was the webcam. I was wondering if there was any way I can get it to work, I've tried EasyCam2 and it detected nothing. Help would very much be appreciated.

---

### Post by sergiom99 on 2008-10-07
please post the output of ```
lsusb
``` to see how your cam is detected and we can search for specific data about it. type it in a console shell.

---

### Post by puredeviation on 2008-10-07
> **sergiom99 said:**
> please post the output of ```
lsusb
``` to see how your cam is detected and we can search for specific data about it. type it in a console shell.

```
Bus 005 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 005 Device 002: ID 5986:0241 Bison 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by sergiom99 on 2008-10-07
maybe this could help:
[http://ubuntuforums.org/showthread.php?t=913832&highlight=5986%3A0241+Bison](http://ubuntuforums.org/showthread.php?t=913832&highlight=5986%3A0241+Bison)

How I found it> [http://ubuntuforums.org/search.php?searchid=49224626](http://ubuntuforums.org/search.php?searchid=49224626)

your webcam> 5986:0241 Bison 

Good luck!

---

### Post by puredeviation on 2008-10-08
> **sergiom99 said:**
> maybe this could help:
[http://ubuntuforums.org/showthread.php?t=913832&highlight=5986%3A0241+Bison](http://ubuntuforums.org/showthread.php?t=913832&highlight=5986%3A0241+Bison)

How I found it> [http://ubuntuforums.org/search.php?searchid=49224626](http://ubuntuforums.org/search.php?searchid=49224626)

your webcam> 5986:0241 Bison 

Good luck!

Thanks for the reply. I've followed everything on that site, but still can't get the webcam to work in other applications. I tried Cheese and somehow it works. But when I try to use Camorama, it give me an error that says "Could not connect to video device (/dev/video0)." I have everything else working but the webcam. If there is anything else you can provide me with that would be great.

I came across this method as well, [http://blog.myfenris.net/?p=377]("http://blog.myfenris.net/?p=377") but still the camera doesn't work.

---

### Post by patrickballeux on 2008-10-08
> **puredeviation said:**
> Thanks for the reply. I've followed everything on that site, but still can't get the webcam to work in other applications. I tried Cheese and somehow it works. But when I try to use Camorama, it give me an error that says "Could not connect to video device (/dev/video0)." I have everything else working but the webcam. If there is anything else you can provide me with that would be great.

I came across this method as well, [http://blog.myfenris.net/?p=377]("http://blog.myfenris.net/?p=377") but still the camera doesn't work.

This is probably a V4L2 webcam, so it would explain why it worked in Cheese and not with Camorama which support only V4l (old API).

The problem is that V4L2 is not completely supported by now even if new webcams are V4L2 compatible.

But you're in luck!  A month ago, I started a new project on Sourceforge.net called WebcamStudio for GNU/Linux that can capture from any webcam supported by Gstreamer (Cheese) and broadcast to a virtual V4L device.

This makes your webcams compatible with a lot of softwares and Flash (v10).

Read the wiki : [http://webcamstudio.wiki.sourceforge.net/]("http://webcamstudio.wiki.sourceforge.net/")

A debian package is available. (Read the installation page for complete details, there is a module to compile "vloopback"...)

It should take you 5 minutes to make things work.

Here is a video sample: [http://ca.youtube.com/watch?v=R9U8zdjeTa8]("http://ca.youtube.com/watch?v=R9U8zdjeTa8") (Part 1)

Hope you like it!

---

### Post by jetpeach on 2008-11-10
how is your lenovo running? i'm thinking of getting one, but would rather run ubuntu on it than windows... did everything else work alright?

---

### Post by ransomw on 2009-10-10
lsusb doesn't list the camera on my s10.  I've just upgraded from 8.4 to 8.10, still with no success.

$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by ransomw on 2009-10-11
... also no success with 8.04 netbook edition...

---

### Post by chiel-s on 2009-10-13
I have exactly the same webcam in my notebook (msi x340). Try installing installing the linux uvc driver, follow this guide: [https://help.ubuntu.com/community/UVC](https://help.ubuntu.com/community/UVC)

Works like a charm.

Cheers,

Chiel

---

### Post by Nikolopulus on 2009-10-22
Hi, I'm about to buy a netbook, I¡m between this one and Acer AOD250. Is yous runing out of the box? id you have any other problem?
Thanks a lot

---

