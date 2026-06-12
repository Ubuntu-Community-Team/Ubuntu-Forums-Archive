---
title: "Ricoh webcam on hp pavilion dv6000 series"
date: 2007-03-01
forum: Hardware &amp; Laptops
---

### Post by pescez on 2007-03-01
Hello guys, i have a hp pavilion dv61646eu laptop and i had some trouble to make it all working with ubuntu 6.10 edgy.. but after some workaround almost everything is working now.
There is still something to do about the webcam though.
The one on my system is an integrated Ricoh model that lsusb recognizes like this:

```
$ lsusb
Bus 002 Device 002: ID 05ca:1870 Ricoh Co., Ltd 
...
``` 

I found [_this blog_]("http://lsb.blogdns.net/software") where this guy is working on a driver for our webcam, but still needs some information that i cannot give him.. 
The first dev-release i tried works almost completely but it still lacks something.

Guys out there, if you have this same webcam and you want to make it work under linux and (most important) you understand something more than me about USB tracing... well take a look!
I'll try to learn something more meanwhile..

---
pescez

---

### Post by codemills on 2007-03-04
> **pescez said:**
> Hello guys, i have a hp pavilion dv61646eu laptop and i had some trouble to make it all working with ubuntu 6.10 edgy.. but after some workaround almost everything is working now.
There is still something to do about the webcam though.
The one on my system is an integrated Ricoh model that lsusb recognizes like this:

```
$ lsusb
Bus 002 Device 002: ID 05ca:1870 Ricoh Co., Ltd 
...
``` 

I found [_this blog_]("http://lsb.blogdns.net/software") where this guy is working on a driver for our webcam, but still needs some information that i cannot give him.. 
The first dev-release i tried works almost completely but it still lacks something.

Guys out there, if you have this same webcam and you want to make it work under linux and (most important) you understand something more than me about USB tracing... well take a look!
I'll try to learn something more meanwhile..

---
pescez


I am using other distro but have same webcam, maybe we all should gather and do something so our webcam works, I got complete laptop working (even easy Bluetooth transfers to by pda/phone etc) now this webcam is all that remains.
```

===============================================
lsusb 
Bus 005 Device 003: ID 05ca:1870 Ricoh Co., Ltd 


 lspci | grep Ricoh
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Generic system peripheral [Class 0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

===============================================
```


I even downloaded the file he provides and compiled with my kernel.
```

=================================================================

 uname  -a
Linux susebox 2.6.18.2-34-default #1 SMP Mon Nov 27 11:46:27 UTC 2006 i686 i686 i386 GNU/Linux


lsmod | grep ry5u

ry5u870                58308  0 
video_buf              28676  1 ry5u870
compat_ioctl32          5504  1 ry5u870
videodev               26880  1 ry5u870
v4l1_compat            16388  2 ry5u870,videodev
v4l2_common            26240  2 ry5u870,videodev
usbcore               114896  5 ry5u870,hci_usb,usbhid,ehci_hcd,uhci_hcd


=================================================================
```


there is no /dev/video0 , So cant get anything.

 I am now going to reboot into windows and give him the webcam trace. lets see what happens.

---

### Post by codemills on 2007-03-05
Just to keep you updated.

right now I am in windows and  I have now sent the LOG file as directed by SAM at his blog ( [http://lsb.blogdns.net/software](http://lsb.blogdns.net/software) ) and given him reference of this thread too.

Hope to hear  from him soon. lets hope the log file  i sent him was useful.

---

### Post by codemills on 2007-03-05
Update,

Sam  @ [http://lsb.blogdns.net/software](http://lsb.blogdns.net/software) replied to my Email and gave me latest version of his driver, he included configurations of HP Webcam given by me in the logs and ITS WORKINGGGGGGGG :guitar: 

Below are screenshots of ekiga and caminfo showing it working.

[IMG]http://img208.imageshack.us/img208/1514/screenshotsn2.jpg[/IMG]

[IMG]http://img208.imageshack.us/img208/5131/hpcaminfovn2.jpg[/IMG]

---

### Post by serag on 2007-03-05
^^^would it be possible to share the updated driver?

---

### Post by dfreer on 2007-03-05
BTW, I have the dv6000t laptop, and the Webcam is made by Sonix NOT Ricoh, they make the Card Reader... 
lsusb
```
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 045e:00e1 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 0c45:62c0 Microdia 
Bus 005 Device 001: ID 0000:0000
```

sudo lshw
```
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-11-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
              *-usb UNCLAIMED
                   description: Video
                   product: USB 2.0 Camera
                   vendor: Sonix Technology Co., Ltd.
                   physical id: 4
                   bus info: usb@5:4
                   version: 1.00
                   serial: SN0001
                   capabilities: usb-2.00
                   configuration: maxpower=500mA speed=480.0MB/s

```

I followed the instructions on [this page]("http://www.suseforums.net/index.php?showtopic=28111"), it compiled and installed the driver fine (created the /dev/video0 and /dev/video directory, and dmesg shows it loading fine), but I can't use camorama, gqcam, aMSN to grab the video (error from camorama = cannot connect to /dev/video0).

EDIT: The link for [uvcvideo-52.tar.gz]("http://mxhaard.free.fr/spca50x/Investigation/uvc/uvcvideo-52.tar.gz")

---

### Post by serag on 2007-03-05
^^^ not all HP laptops have the same components.  Some do come with the Ricoh webcam and this is what this thread is discussing.

---

### Post by dfreer on 2007-03-05
Ok... Here's what I've done so far:

downloaded the latest uvcvideo driver from the svn and installed it:
```
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
cd trunk
make
sudo make install
sudo modprobe uvcvideo
```

Then I started Ekiga.
Going through its configuration wizard it asked me if I wanted to configure the webcam. Video4Linux didn't work, but Video4Linux2 did. After clicking on the webcam button the blue light came on and voila! the Webcam is working.

I can't seem to get it to work anywhere else, namely aMSN. Is there any IM clients for MSN that support webcams that I can try?

EDIT: > ^^^ not all HP laptops have the same components. Some do come with the Ricoh webcam and this is what this thread is discussing.
Sorry to ruin your thread with useless info, I didn't see your post. It seems weird that the same laptop dv6xxx series doesn't use the same hardware. ;) Shows my lack of m4d google skillz

---

### Post by codemills on 2007-03-06
Ok ,  I was just informed by Sam that a NEW DRIVER has been released, he included new device support for the CAM  i have, [http://lsb.blogdns.net/ry5u870](http://lsb.blogdns.net/ry5u870) << Check it out.

I would strongly suggest all you guys who want your Cams to be supported, To follow the [webcam tracing ]("http://lsb.blogdns.net/webcam-tracing")guide and give this very generous driver developer the details (log files), He will surely reply you with modified drivers.


Anshu.

---

### Post by pescez on 2007-03-06
> **codemills said:**
> Ok ,  I was just informed by Sam that a NEW DRIVER has been released, he included new device support for the CAM  i have, [http://lsb.blogdns.net/ry5u870](http://lsb.blogdns.net/ry5u870) << Check it out.

I would strongly suggest all you guys who want your Cams to be supported, To follow the [webcam tracing ]("http://lsb.blogdns.net/webcam-tracing")guide and give this very generous driver developer the details (log files), He will surely reply you with modified drivers.


Anshu.

i came just to say the same.. Sam released a new version where our webcam is supported and working!! thank you all for cooperating and thanks to Sam! :) 

---
pescez

---

### Post by serag on 2007-03-06
thank you codemills and Sam for the driver, can't wait to get home and try it.

---

### Post by serag on 2007-03-06
just installed the new driver and it works great on my HP DV9010CA with Ricoh webcam.   thanks again.

---

### Post by icdkp on 2007-11-25
Hi!

Hopefully I can find some help here. When using my webcam locally, I can see images without any problem, but when it comes to a transmission over internet, there's no image sent. I have no idea of network stuff, but I guess that's where the problem is. Could someone please guide me in oder to solve this problem?
Thanks in advance

---

### Post by anpu1 on 2008-05-30
hi everyone!

I have now ubuntu 8.04 and can't install webcam! I have HP Pavilion dv6000 and Ricoh webcam and i can't install it!! 

any help? plz

---

### Post by mr.pirate on 2008-06-30
I have a HP Pavilion dv6338se and I just downloaded the driver from [http://www.qbik.ch/usb/devices/showdr.php?id=247](http://www.qbik.ch/usb/devices/showdr.php?id=247) because the server for the previous link seems to be down. I unpacked it and then went into the directory and did make but it seemed as though the directory "build" was missing, so i went looking for it and found it in the "generic" directory instead of the "rt" directory. When i tried to make it with those files it didnt work

```

slick@localhost:~/Desktop/Source/r5u870-0.10.0$ make -C /lib/modules/2.6.24-19-generic/build M=/home/slick/Desktop/Source/r5u870-0.10.0 V=0 modules
make: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/slick/Desktop/Source/r5u870-0.10.0/r5u870_md.o
In file included from /home/slick/Desktop/Source/r5u870-0.10.0/r5u870_md.c:55:
/home/slick/Desktop/Source/r5u870-0.10.0/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
make[1]: *** [/home/slick/Desktop/Source/r5u870-0.10.0/r5u870_md.o] Error 1
make: *** [_module_/home/slick/Desktop/Source/r5u870-0.10.0] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'

```

---

