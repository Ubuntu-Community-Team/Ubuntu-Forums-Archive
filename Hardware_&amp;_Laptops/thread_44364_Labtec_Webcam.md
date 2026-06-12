---
title: "Labtec Webcam"
date: 2005-06-25
forum: Hardware &amp; Laptops
---

### Post by enphlict on 2005-06-25
Hello! While I was doing the usual, I normally do every day, I fell over a guide on how to build support for a Labtec Webcam in Ubuntu. I forgot to bookmark it, and now I hopelessly search for it. If you can help me, then I would appreciate it.

Thanks to the Ubuntu community for making such a project. The GNU/Linux community really needs this project!

---

### Post by az on 2005-06-25
What does the inf file in the windows driver say it is?

---

### Post by OwlManAtt on 2005-06-25
[QUOTE=enphlict]Hello! While I was doing the usual, I normally do every day, I fell over a guide on how to build support for a Labtec Webcam in Ubuntu. I forgot to bookmark it, and now I hopelessly search for it. If you can help me, then I would appreciate it.

Thanks to the Ubuntu community for making such a project. The GNU/Linux community really needs this project![/QUOTE]
 This page has a driver and two projects which (I believe) both support this camera.

[http://home.tiscali.dk/tomasgc/labtec/](http://home.tiscali.dk/tomasgc/labtec/)

---

### Post by az on 2005-06-25
If your camera is SPCA5XX based, you need this driver:
[http://mxhaard.free.fr/spca50x/Download/spca5xx-20050601.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20050601.tar.gz)

Install build-essential and linux-headers-(kernelversion - stock kernel is linux-headers-2.6.10-5-386)

tar xvzv spca*
cd spca*
make
sudo make install
(I do not remember if you need to do :

sudo depmod -a

It may do it for you....)

You need to stop your x server and make sure that the v4l module gets loaded.  You need to reconfigure your xserver

CTRL-ALT-F1
login
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start

(Or just edit the file by hand (/etc/X11/xorg.conf)


Plug in your camera and you are almost good to go.  When I launch gqcam, it complains that ther is no /dev/video.  I need to make a symlink from /dev/video0 to /dev/video.

That's it.  As soon as I can find the debian package for the source (it is in preparation), I will try to package some modules and make them available...


If your labtech webcam uses another chipset, I dunno how to help you.

---

### Post by enphlict on 2005-06-26
I could just swear, that it was a Ubuntu wiki page, that showed how to make Ubuntu support your webcam (Labtec Webcam was one of the supported webcams). I remember, it was saying, that I should get the kernel sources and compile them and thereafter install another program in order to support certain webcams for Ubuntu.

---

### Post by enphlict on 2005-06-26
I found the page, and it was a Ubuntu wiki page: [https://wiki.ubuntu.com/Spca5xx?highlight=%28webcam%29](https://wiki.ubuntu.com/Spca5xx?highlight=%28webcam%29)

This guide supports the webcams listed on the page. Thank science (or god?) I found it. Now.. Back to Python and Blender! :)

---

### Post by az on 2005-06-26
You do not need to compile the kernel.  You can just use the linux-headers to compile the driver...

I did know about the libpt-plugins-v4l...

---

### Post by oofnik on 2005-06-28
Hey azz, thanks a lot. I have an Intel Pro webcam that's a few years old and it is supported by the spca5xx driver. I found this thread in search of answers, because I can't get it to load properly. I compiled it and everything went fine, did sudo modprobe spca5xx. but when I try to load a program like gqcam or similar, it tells me: /dev/video0: Cannot allocate memory.
Weird! I have 1GB system RAM and 128mb video RAM...
So I checked dmesg after each command. Maybe this can help somebody figure out what's going on:
```
$ sudo modprobe spca5xx
$ dmesg
/home/oofnik/Desktop/spca5xx-20050601/drivers/usb/spca5xx.c: USB SPCA5XX camera found. Type Intel PC Camera Pro (SPCA505+SAA7113)
/home/oofnik/Desktop/spca5xx-20050601/drivers/usb/spca5xx.c: [spca5xx_probe:8495] Camera type YYUV
usbcore: registered new driver spca5xx
/home/oofnik/Desktop/spca5xx-20050601/drivers/usb/spca5xx.c: spca5xx driver 00.56.03 registered
$ spcaview
 Spcaview version:1.0.6 date: 01:06:2005 (C) mxhaard@magic.fr
Initializing SDL.
SDL initialized.
bpp 3 format 15
Using video device /dev/video0.
Initializing v4l.
ERROR opening V4L interface
: Cannot allocate memory
oofnik@oofnik:~/Desktop/spca5xx-20050601$ cat /dev/video0
cat: /dev/video0: Cannot allocate memory
oofnik@oofnik:~/Desktop/spca5xx-20050601$ dmesg
/home/oofnik/Desktop/spca5xx-20050601/drivers/usb/spca5xx.c: USB SPCA5XX camera found. Type Intel PC Camera Pro (SPCA505+SAA7113)
/home/oofnik/Desktop/spca5xx-20050601/drivers/usb/spca5xx.c: [spca5xx_probe:8495] Camera type YYUV
usbcore: registered new driver spca5xx
/home/oofnik/Desktop/spca5xx-20050601/drivers/usb/spca5xx.c: spca5xx driver 00.56.03 registered
/home/oofnik/Desktop/spca5xx-20050601/drivers/usb/spca5xx.c: init isoc: usb_submit_urb(0) ret -12
/home/oofnik/Desktop/spca5xx-20050601/drivers/usb/spca5xx.c: [spca5xx_open:4501]  DEALLOC error on init_Isoc

$
```

Yeah.. some kind of error that I don't understand. I'm pretty new to linux but I have been an ultra fast learner so far, so I hope I can figure this out with the help of this fine community!

---

### Post by arunsub on 2005-07-07
I have an Intel webcam that's few years old. Since I'm new to Linux, I'm not sure how to make it work. Could you please give me step by step instruction on how to make it work?

Thanks.

---

### Post by Kimm on 2005-08-01
I'm trying to use the same Driver for a Creative Webcam NX (that should be supported). The compiles works nicely but it wount load when I do 'sudo insmod spca5xx.ko', the error message I get is:

```

insmod: error inserting 'spca5xx.ko': -1 unknown symbol in module

```

Any ideas?

---

### Post by arunsub on 2005-08-01
I too got errors, a little different. See this thread:
[http://ubuntuforums.org/showthread.php?t=46092&page=5&pp=10&highlight=software+webcam](http://ubuntuforums.org/showthread.php?t=46092&page=5&pp=10&highlight=software+webcam)

---

### Post by Kimm on 2005-08-01
Thank you.. thats looks like a good thread :)

---

### Post by trollzor on 2005-08-02
Just a quick note to people out there needing help who have webcams which register with a Vendor Id 0x46d of and a Product Id of 0x840, 0x850, or 0x870 to a "lsusb", I have written a HOWTO for logitech and labtec webcams that match those ids, and a little bit on getting gnomemeeting working for them.

HOWTO is [here](http://ubuntuforums.org/showthread.php?t=53755)

cheers, 

Trollzor

---

### Post by az on 2005-08-02
I am short on time.  Who wants to put these two webcam howtos on the wiki?

wiki.ubuntu.com/UserDocumentation

or

wiki.ubuntu.com/forum

---

### Post by mrdunk on 2006-05-06
the error in dmesg oofnik refers to:
```
/home/oofnik/Desktop/spca5xx-20050601/drivers/usb/spca5xx.c: [spca5xx_open:4501]  DEALLOC error on init_Isoc
```
is caused (i think) by bandwidth issues on the USB bus.

i get the same error if i use my quickcam from a USB hub but it works fine if i plug it into a native port.

note that some PC cases contain USB hubs. the USB ports on the front of your case *may* actually be a USB hub. try it from a USB port on your motherboard.

dunk.

---

