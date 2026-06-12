---
title: "S3 Virge Freeze"
date: 2005-07-20
forum: Hardware &amp; Laptops
---

### Post by southy on 2005-07-20
Hi all.

Im just having a little trouble getting ubuntu up here. 
This is an IBM netfinity with an S3 Trio card. I got that working only with 640x480 on warthy (live-CD) and hoary (installed) "XFree and Xorg".

So I got me a S3 Virge. 
But - its still not working: 
Hoary freezes after the login-screen of xorg (when the "ubuntu - linux for human beings" - Banner is displayed). Sometimes reboots, sometimes just hangs.

warthy (XFree) works fine and even on 1024x768, but if possible I would like to get hoary up. 

According to the log, hoary starts up with 1024x768.
How can it be the login screen works well and it freeyes after that?
Shouldnt all critical modules be loaded before the login screen?

I tried with and without ramdac, same problem.

The Xorg.0.log says nothing spevial in my eyes, I have the second half of the log and the xorg.conf attached here.

Please, can anyone help me with this, I really getting mad here, just got this new graphics card, because I was told, S3 Virge would work well with hoary and now it still doesn"t work, this really sucks.

Thanks so much, 
Southy.

---

### Post by Teroedni on 2005-07-20
edit found this
[http://www.linux-sxs.org/multimedia/s3virge.html](http://www.linux-sxs.org/multimedia/s3virge.html)

i dont know if its any use for you.

I will se if i can find some more information tommorow

---

### Post by southy on 2005-07-20
[QUOTE=Teroedni]
[http://www.linux-sxs.org/multimedia/s3virge.html](http://www.linux-sxs.org/multimedia/s3virge.html)
i dont know if its any use for you.
[/QUOTE]

Hi Teroedni,

Thanks for your help. 
Unfortunately its not quite working:
The link you pointed out suggests to use the "svga" driver instead of the "s3virge".
"svga" works here, but - surprise, surprise - only with 4 bit color depth.
with 15 bit and more, I get an error saying that higher color depth is not aviable.
Also, it just does only work 640x480. (Why do they call it "SVGA" anyway?)

To be honest I cant image what  more to try. I got me an S3 Virge, because I knew it is one of the graphic chipsets sold most often ever. 
It just cant be not supportet, I cant believe this. 

As I pointed out, XFree86 works just fine. 
I guess perhaps I should just forget about hoary and install warthy. 

Thanks for your help and if you find out some more hints Ill be most grateful.

Best wishes from europe, 
Southy

---

### Post by Teroedni on 2005-07-21
have you innstaled the latest xfree version 4.3.0
in 4.3.0 Virge should be happy;)


Heres whats stands about s3virge
1. Supported hardware

The s3virge driver in XFree86 4.3.0 supports the S3 ViRGE, ViRGE DX, GX, GX2, MX, MX+, and VX chipsets. It also supports Trio3D and Trio3D/2x chips. A majority of testing is done on ViRGE DX chips, making them the most stable to date. This release has added support for doublescan modes on DX.


Features:

    * Fully accelerated support for S3 ViRGE family video adapters
    * uses linear frame buffer
    * supports resolutions up to 2048x2048
    * supports color depths of 8, 15, 16 and 24
    * full use of video card memory for acceleration caching when visible framebuffer leaves extra memory
    * XVideo on DX, GX, GX2, MX, MX+ and Trio3D/2X at depth 16 and 24
    * Doublescan modes on DX, possibly others (untested)


with other words you should get more than vga:)

heres the link
[http://www.xfree86.org/4.3.0/s3virge.html](http://www.xfree86.org/4.3.0/s3virge.html)

---

### Post by Teroedni on 2005-07-21
is it also possible to get it to work in xorg but it is perhaps a little to difficult?
Well you can check it if you want to
heres the link
[http://linux.com.hk/PenguinWeb/manpage.jsp?section=4&name=s3virge](http://linux.com.hk/PenguinWeb/manpage.jsp?section=4&name=s3virge)

---

### Post by Teroedni on 2005-07-21
and here we have a driver thats only work for your first trio64 card
[http://packages.ubuntu.com/breezy/x11/xserver-xorg-driver-s3](http://packages.ubuntu.com/breezy/x11/xserver-xorg-driver-s3)

and for virge
[http://packages.ubuntu.com/breezy/x11/xserver-xorg-driver-s3virge](http://packages.ubuntu.com/breezy/x11/xserver-xorg-driver-s3virge)

Well its sime the like you can get it to work on both freex86 and xorg

Good luck;)

---

### Post by Teroedni on 2005-07-21
Heres something more for x.org
[http://wiki.x.org/wiki/VideoDriverFAQ](http://wiki.x.org/wiki/VideoDriverFAQ)

---

### Post by Teroedni on 2005-07-21
okey last post
Your s3 driver should realy work if you download the latest x.org X11R6.8
link
[http://www.x.org/Downloads.html](http://www.x.org/Downloads.html)

list over supported video card included your s3virge:)
[http://www.x.org/X11R6.8/doc/RELNOTES3.html#9](http://www.x.org/X11R6.8/doc/RELNOTES3.html#9)


and the configuration options for the virge in xorg r6.8
[http://www.x.org/X11R6.8/doc/s3virge.4.html](http://www.x.org/X11R6.8/doc/s3virge.4.html)


Well it shuldnt be a problem to get your card to work now ;)
If your need help to configure it just ask ,and i or someone else will help you
Good Luck :grin:

---

