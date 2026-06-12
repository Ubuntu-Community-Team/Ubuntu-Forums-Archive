---
title: "[SOLVED] Help! Almost works... GSPCA webcam driver - DMES says found BUT..."
date: 2008-05-12
forum: Hardware
---

### Post by arman.haghi on 2008-05-12
[SOLVED]
**********************************************************

Summary

D-Link DSC-350

Working in Ubuntu (Kubuntu) 7.10 (64)

**********************************************************

HOW:

**1)** I removed the gscpa,

> sudo modprobe -r gspca

**2)** I disconnected my webcam

then ran module assistant, i.e.

> sudo m-a

and while in m-a

a) update

b) prepare

c) select ... then select the gspca module and hit ok...

it'll say:

                               &#9474; You have selected the following packages:                     &#9474;
                               &#9474;                                                               &#9474;
                               &#9474;  gspca                                                        &#9474;
                               &#9474;                                                               &#9474;
                               &#9474;  Choose one of the following commands to proceed or Cancel    &#9474;
                               &#9474;                                                               &#9474;
                               &#9474;    LIST    List installed (binary) packages                   &#9474;
                               &#9474;    SEARCH  List and search with apt-cache                     &#9474;
                               &#9474;    GET     Get or update the source package                   &#9474;
                               &#9474;    BUILD   Compiles module packages for the current kernel    &#9474;
                               &#9474;    INSTALL Installs the packages for the current kernel       &#9474;
                               &#9474;    BACK    Returns to the module selection                    &#9474;
                               &#9474;                                                               &#9474;
                               &#9474;                                                               &#9474;
                               &#9474;                <Ok>                    <Cancel>               &#9474;
                               &#9474;                                                               &#9474;
                               &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;


so do:

a) get

b) build

and then it'll probably ask you if you want to install, so say yes and it'll install, otherwise:

c) install.

then (I'm not sure if this was neccesary) but I did a modprobe on the new module...

> sudo modprobe gspca

then replugged the usb cable and it started to work with skype, cheese, camorama, and camstream.

NOTE: it gives in and dies every now and then, so I just run all the steps again.

Hope this is of some help to someone.


******************
original post
******************

Hi people,

I've seriously read through heaps of pages, on and off these forums, tried a stack of stuff ~ and I'm totally perplexed; help is really appreciated.

Long story short, I have a

D-Link DSC-350 (which is supported by spca5xx driver)

camera (webcam), and I'm trying to run it on

Kubuntu 7.10 (64bit)

This is the latest: I plug in my webcam and [SIZE="5"]dmesg[/SIZE] gives me:

[ 6437.892797] /home/arman/Desktop/webcamdriver/gspcav1-20071224/gspca_core.c: USB GSPCA camera found.(SPCA500+unknown CCD)
[ 6437.892803] /home/arman/Desktop/webcamdriver/gspcav1-20071224/gspca_core.c: [spca5xx_probe:4275] Camera type JPEG
[ 6437.895821] /home/arman/Desktop/webcamdriver/gspcav1-20071224/gspca_core.c: [spca5xx_getcapability:1249] maxw 640 maxh 480 minw 176 minh 144

So it seems to be detecting the camera but when I go to Camorama I get

"could not connect to video device (/dev/video0) Please check connection."

Which is fair, as /dev/video0 doesn't exist (no such file or directory)

Also, Skype, Kopete etc don't pick it up...

Where to from here? how to make it create that video0 node? lost...


---

P.S

deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

seems to be down...? (for easycam)

P.S.

I can't remember all the pages I went through, but seen these to name a few:
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)
[https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)
[https://help.ubuntu.com/community/Spca5xx](https://help.ubuntu.com/community/Spca5xx)
[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)
[http://ubuntuforums.org/showthread.php?t=787055&highlight=%2Fdev%2Fvideo0](http://ubuntuforums.org/showthread.php?t=787055&highlight=%2Fdev%2Fvideo0)
[http://ubuntuforums.org/showthread.php?t=723492&highlight=%2Fvideo0](http://ubuntuforums.org/showthread.php?t=723492&highlight=%2Fvideo0)
[http://ubuntuforums.org/showthread.php?t=355648&highlight=spca50x](http://ubuntuforums.org/showthread.php?t=355648&highlight=spca50x)
[http://ubuntuforums.org/showthread.php?t=375005&highlight=spca50x](http://ubuntuforums.org/showthread.php?t=375005&highlight=spca50x)
[http://ubuntuforums.org/showthread.php?t=256307&highlight=%2Fvideo0](http://ubuntuforums.org/showthread.php?t=256307&highlight=%2Fvideo0)
[http://www.mythtv.org/pipermail/mythtv-users/2006-December/162136.html](http://www.mythtv.org/pipermail/mythtv-users/2006-December/162136.html)
[http://www.crazysquirrel.com/computing/debian/webcam.jspx](http://www.crazysquirrel.com/computing/debian/webcam.jspx)

---

### Post by Tomatz on 2008-05-12
Do you connect the webcam through a hub as that can cause problems.

If you do connect it directly into the port on the back of your box then reboot.

---

### Post by hermes0710 on 2008-05-12
Try the cheese application. Could you post the contents of /dev folder?

---

### Post by arman.haghi on 2008-05-12
> **Tomatz said:**
> Do you connect the webcam through a hub as that can cause problems.

If you do connect it directly into the port on the back of your box then reboot.

Thanks for the super quick reply (it's 1am in OZ, I'm just about to go to bed but the fact that you both replied made my day)

-> it's running straight onto my mobo onboard USB, and note that dmesg picks it up and its working as a USB drive (i.e. when I plug it in it can be openned and the content viewed)

-> also, there are two text files stored in the camera itself (when opened as USB) and they read:

spca50x library v0.1 02/09/03 - 23:14:11
Till Adam <till@adam-lilienthal.de>
Support for digital cameras with a sunplus spca50x chip based on several other gphoto2 camlib modules and the information kindly provided by Mustek.

---

### Post by arman.haghi on 2008-05-12
> **hermes0710 said:**
> Try the cheese application. Could you post the contents of /dev folder?

Hey mate, thanks for the pointers; I've installed cheese and running it plays the same tune: 'unable to find a webcam, sorry'

also, running it from terminal gives this message while cheese is running:

** Message: test pipeline for v4lsrc failed:
[v4lsrc ! video/x-raw-rgb,width=160,height=120 ! fakesink]: Device "/dev/video0" does not exist.

<- long list was here ->

---

