---
title: "webcam eMPIA EM2700 any ubuntu support for it"
date: 2007-02-25
forum: Hardware &amp; Laptops
---

### Post by justinol on 2007-02-25
hi

i am a sorta new ubuntu user. really enjoy it big time. the only letdown for me is webcam.

the new laptop i bought has a eMPIA EM2700 USB2 webcam. 

i searched this forum and performed a google search. no help. easycam2 no help.

anyone who would be able to show me how to install webcam driver for ubuntu? is it possible even?

i am frustrated about this and would appreciate a knowledagble person helping if possible (especially cause nothing seems to be out there.)

thanks

lsusb

Bus 005 Device 004: ID 0aec:3260 Neodio Technologies Corp. 7-in-1 Card Reader
Bus 005 Device 003: ID eb1a:2750 eMPIA Technology, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 046d:c042 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

---

### Post by Stemp on 2007-02-25
From [Em2880 V4LWiki]("http://www.linuxtv.org/v4lwiki/index.php/Em2880") 

> Devices
in progress:
    * eb1a:2750 based webcams 

2007-02-11:

    * back on the track again, committed pre eb1a:2750 webcam support, 2.6.20 isn't supported yet 

---

### Post by justinol on 2007-02-26
great news. thanks for sharing the info. i await sort of patiently.

:)

---

### Post by spera on 2007-11-15
Hi everyone,

same problem for me, desperate to find my eb1a:2750 webcam working under 7.10 - I'm completely new to Ubuntu, eager to learn, though !

Any relevant help or info would be appreciated.

---

### Post by Stemp on 2007-11-15
From : [http://mcentral.de/wiki/index.php/Em2880](http://mcentral.de/wiki/index.php/Em2880)

> eb1a:2750 based webcams (partly supported)

You may try it now ;)

---

### Post by adamboy007 on 2007-11-15
My problem would be with the webcam.   it  I would like to configure my A4 Tech PK-35N camera to Ubunto 10.7. Neither the camorama neither the gspca  packet did not help. The error message at camorama: could not connect to video device (/dev/video0). 
At lsusb:
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 03f0:171d Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 046d:c019 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 08ff:2580 AuthenTec, Inc. 
Bus 003 Device 001: ID 0000:0000  
(sorry for my english) Thanks for any help.

---

### Post by Mildertduck on 2007-11-21
I have a similar problem, lsusb gives:

...
eb1a:5052 eMPIA Technology, Inc.
...

no luck with EasyCam.  Can anyone help?

Thanks, Richard

---

### Post by Stemp on 2007-11-21
@ adamboy007 : your problem has nothing to do with eMPIA webcam. Your webcam is or should be recognized by gspca driver. Create a new thread with your specific problem ;)

@ Mildertduck : Check the link I've gave a few posts ago. You'll have to compile this beta driver yourself, and pray :D

---

### Post by Mildertduck on 2007-12-09
Stemp: Thanks for your reply - I'm not a very advanced user, so compiling a driver is slightly beyond me :/

Are there any other solutions?

---

### Post by Stemp on 2007-12-12
@ Mildertduck : it's not as difficult as it seems ;)

First you have to prepare Ubuntu for compilations :
```
user@ubuntu:~$ sudo apt-get update  
user@ubuntu:~$ sudo apt-get install build-essential
```

Then install the kernel headers :
```
user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r`  
user@ubuntu:~$ sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build
```

Now you're ready for compiling software and drivers.

For this particular driver you also need mercurial (to get the sources) :
```
user@ubuntu:~$ sudo apt-get install mercurial
```

Now grab the sources :
```
user@ubuntu:~$ hg clone http://mcentral.de/hg/~mrec/v4l-dvb-experimental
```

Compile the driver :
```
user@ubuntu:~$ cd v4l-dvb-experimental
user@ubuntu:~$ make && sudo make install
```

At this point you probably need to reboot.

Load the module :
```
user@ubuntu:~$ sudo modprobe em28xx 
```

And test ;)

---

### Post by randyrick on 2008-02-12
Thanks for the detailed instructions, Stemp.  However, no luck for me.  Whenever I try to start the cam up, I get the same error message on GyachE Improved 1.1.0.

An error occurred at 'ioctl VIDIOCSPICT'. Could not set camera properties.

I have a pretty cheapo generic cam bought from eBay from China.  The cam worked fine on both Windows XP & Mac OS X without having to install any drivers.

---

randy@randy:~$ lsusb
Bus 003 Device 003: ID eb1a:2761 eMPIA Technology, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  


randy@randy:~$ sudo tail /var/log/syslog
Feb 09 XX:39:27 randy kernel: [  168.347709] uvcvideo: disagrees about version of symbol video_unregister_device
Feb 09 XX:39:27 randy kernel: [  168.347720] uvcvideo: Unknown symbol video_unregister_device
Feb 09 XX:39:27 randy kernel: [  168.347928] uvcvideo: disagrees about version of symbol video_device_alloc
Feb 09 XX:39:27 randy kernel: [  168.347936] uvcvideo: Unknown symbol video_device_alloc
Feb 09 XX:39:27 randy kernel: [  168.348098] uvcvideo: disagrees about version of symbol video_register_device
Feb 09 XX:39:27 randy kernel: [  168.348105] uvcvideo: Unknown symbol video_register_device
Feb 09 XX:39:27 randy kernel: [  168.348494] uvcvideo: disagrees about version of symbol video_device_release
Feb 09 XX:39:27 randy kernel: [  168.348503] uvcvideo: Unknown symbol video_device_release
Feb 09 XX:39:27 randy NetworkManager: <debug> [1202794767.770799] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_eb1a_2761_noserial_if0'). 
Feb 09 XX:39:27 randy NetworkManager: <debug> [1202794767.818361] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_eb1a_2761_noserial_usbraw'). 


Any ideas where I should go from here?  

Also, Is there anyway I can undo or remove the installation of the experimental drivers?

---

