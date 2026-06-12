---
title: "Vaio r5u870 webcam driver, DKMS package"
date: 2008-09-23
forum: Hardware
---

### Post by IntuitiveNipple on 2008-09-23
I've updated my DKMS (Dynamic Kernel Module Support) package containing the r5u870 driver for Gutsy, Hardy and Intrepid.

It includes support for most Ricoh chip-set Sony Vaio Motion Eye cameras (VGP-VCC2, VGP-VCC3, VGP-VCC4, VGP-VCC5, VGP-VCC6, VGP-VCC7, VGP-VCC8, VGP-VCC9), HP Pavilion Webcam (UVC, Pavilion DV6502AU, Webcam 1000), Fujitsu F01 UVC.

This is the complete list of supported USB device IDs:
```

05CA:1810 05CA:1812 05CA:1830 05CA:1832 05CA:1833
05CA:1834 05CA:1835 05CA:1836 05CA:1837 05CA:1839 
05CA:183a 05CA:183b 05CA:183e 05CA:1841 05CA:1870

```
It is available from my Ubuntu PPA (Personal Package Archive). To install it add my PPA to apt's source list:
```

sudo sh -c "echo 'deb http://ppa.launchpad.net/intuitivenipple/ubuntu $(lsb_release -sc) main' >/etc/apt/sources.list.d/intuitivenipple.list"
sudo apt-get update

```
and then install the package:
```

sudo apt-get install r5u870-dkms

```
Remove my PPA from the apt sources to prevent unexpected upgrades of packages I maintain:
```

sudo rm /etc/apt/sources.list.d/intuitivenipple.list
sudo apt-get update

```

---

### Post by matthias13 on 2008-10-14
When installing the package there is the following error message:

Error! Bad return status for module build on kernel: 2.6.27-7-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/r5u870/0.11.1/build/ for more information.
0
0
dpkg: Fehler beim Bearbeiten von r5u870-dkms (--configure):
 Unterprozess post-installation script gab den Fehlerwert 10 zurück
Fehler traten auf beim Bearbeiten von:
 r5u870-dkms

---

### Post by matthias13 on 2008-10-14
I forgot to attach make.log

---

### Post by chaumurky on 2008-10-15
Ouch!

```
DKMS make.log for r5u870-0.11.1 for kernel 2.6.27-7-generic (i686)
Thu Oct 16 08:44:31 EST 2008
make: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  LD      /var/lib/dkms/r5u870/0.11.1/build/built-in.o
  CC [M]  /var/lib/dkms/r5u870/0.11.1/build/r5u870.o
/var/lib/dkms/r5u870/0.11.1/build/r5u870.c:867:1: warning: "V4L2_CID_SHARPNESS" redefined
In file included from include/linux/videodev.h:16,
                 from /var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam.h:38,
                 from /var/lib/dkms/r5u870/0.11.1/build/r5u870.c:59:
include/linux/videodev2.h:868:1: warning: this is the location of the previous definition
  LD      /var/lib/dkms/r5u870/0.11.1/build/usbcam/built-in.o
  CC [M]  /var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_dev.o
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_dev.c: In function ‘usbcam_work_ref’:
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_dev.c:779: warning: format not a string literal and no format arguments
  CC [M]  /var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.o
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c: In function ‘usbcam_v4l_ioctl’:
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1167: error: implicit declaration of function ‘video_usercopy’
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1171: error: implicit declaration of function ‘video_ioctl2’
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1159: warning: unused variable ‘udp’
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c: At top level:
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1213: error: unknown field ‘type’ specified in initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1214: error: unknown field ‘type2’ specified in initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1217: error: unknown field ‘vidioc_querycap’ specified in initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1217: warning: initialization makes integer from pointer without a cast
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1218: error: unknown field ‘vidioc_enum_fmt_cap’ specified in initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1218: warning: initialization makes integer from pointer without a cast
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1219: error: unknown field ‘vidioc_g_fmt_cap’ specified in initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1219: warning: initialization makes integer from pointer without a cast
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1219: error: initializer element is not computable at load time
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1219: error: (near initialization for ‘usbcam_videodev_template.tvnorms’)
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1220: error: unknown field ‘vidioc_s_fmt_cap’ specified in initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1220: warning: initialization makes integer from pointer without a cast
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1220: error: initializer element is not computable at load time
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1220: error: (near initialization for ‘usbcam_videodev_template.current_norm’)
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1221: error: unknown field ‘vidioc_try_fmt_cap’ specified in initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1221: warning: initialization from incompatible pointer type
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1222: error: unknown field ‘vidioc_reqbufs’ specified in initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1222: warning: initialization from incompatible pointer type
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1223: error: unknown field ‘vidioc_querybuf’ specified in initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1224: error: unknown field ‘vidioc_qbuf’ specified in initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1224: warning: initialization makes integer from pointer without a cast
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1225: error: unknown field ‘vidioc_dqbuf’ specified in initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1225: warning: missing braces around initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1225: warning: (near initialization for ‘usbcam_videodev_template.lock’)
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1225: warning: initialization makes integer from pointer without a cast
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1226: error: unknown field ‘vidiocgmbuf’ specified in initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1226: warning: excess elements in struct initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1226: warning: (near initialization for ‘usbcam_videodev_template’)
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1227: error: unknown field ‘vidioc_enum_input’ specified in initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1227: warning: excess elements in struct initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1227: warning: (near initialization for ‘usbcam_videodev_template’)
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1228: error: unknown field ‘vidioc_streamon’ specified in initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1228: warning: excess elements in struct initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1228: warning: (near initialization for ‘usbcam_videodev_template’)
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1229: error: unknown field ‘vidioc_streamoff’ specified in initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1229: warning: excess elements in struct initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1229: warning: (near initialization for ‘usbcam_videodev_template’)
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1230: error: unknown field ‘vidioc_g_input’ specified in initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1230: warning: excess elements in struct initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1230: warning: (near initialization for ‘usbcam_videodev_template’)
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1231: error: unknown field ‘vidioc_s_input’ specified in initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1231: warning: excess elements in struct initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1231: warning: (near initialization for ‘usbcam_videodev_template’)
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1232: error: unknown field ‘vidioc_queryctrl’ specified in initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1232: warning: excess elements in struct initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1232: warning: (near initialization for ‘usbcam_videodev_template’)
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1233: error: unknown field ‘vidioc_g_ctrl’ specified in initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1233: warning: excess elements in struct initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1233: warning: (near initialization for ‘usbcam_videodev_template’)
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1234: error: unknown field ‘vidioc_s_ctrl’ specified in initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1234: warning: excess elements in struct initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1234: warning: (near initialization for ‘usbcam_videodev_template’)
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1235: error: unknown field ‘vidioc_querymenu’ specified in initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1235: warning: excess elements in struct initializer
/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.c:1235: warning: (near initialization for ‘usbcam_videodev_template’)
make[2]: *** [/var/lib/dkms/r5u870/0.11.1/build/usbcam/usbcam_fops.o] Error 1
make[1]: *** [/var/lib/dkms/r5u870/0.11.1/build/usbcam] Error 2
make: *** [_module_/var/lib/dkms/r5u870/0.11.1/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
```

---

### Post by Pedhead on 2008-10-18
when trying to remove your PPA, I get this:

 ~ $ sudo rm /ect/apt/sources.list.d/intuitivenipple.list
rm: cannot remove `/ect/apt/sources.list.d/intuitivenipple.list': No such file or directory

???

---

### Post by Yako on 2008-10-19
Doesn't work for me either. I attached my make.log.

---

### Post by queno on 2008-11-04
Not Working +1

I've got the same errors in make.log as the others already reported above.

(Not) running a 05ca:183a Sony Visual Communication Camera VGP-VCC7 on a Sony Vaio TZ21MN/N with up-to-date Ubuntu Intrepid 32Bit.

TJ, please look into this!

---

### Post by dviejo on 2008-11-04
The same reported problem for me. I'm trying to install the driver on a 32bits Intrepid Ibex.

Cheers

---

### Post by derick on 2008-11-05
Hate to say a me too, but also getting the same issue on Intrepid 64-bit.

Log is attached

FWIW building from the source I had been using for Hardy also generated the same error messages.  Could it be a compiler issue?

Thanks

Derick

---

### Post by samcompton on 2008-11-05
Didn't work with Intrepid.  I went back to Hardy and installed the Arakhne driver.  Would like to use Intrepid but, waiting for a good webcam driver.  

Thanks for the effort.

---

### Post by derick on 2008-11-06
I followed the instructions in [this]("http://ubuntuforums.org/showthread.php?t=968381&highlight=r5u870") thread and its working for me.  Added a start-up script and all is good.

YMMV

Derick

---

### Post by quini on 2008-11-06
Thanks, Derik!

It is now also working for me (Vaio TZ11MN)  :popcorn::KS:KS

---

### Post by dviejo on 2008-11-06
Derik, Quini, what ubuntu version and kernel are you using? I think this driver is working for Hardy but not for Intrepid yet.

Cheers

---

### Post by ericblr on 2008-11-10
Exact same problem for me.  I am trying to get my built in webcam working on my pavilion dv9335nr laptop.

Can anyone help?

---

### Post by dviejo on 2008-11-11
Finally, the solution proposed by derick works for me. Nevertheless, I hope the package developed by IntuitiveNipple will be fixed soon in order to take advantage from DKMS when a new kernel arrive.

---

### Post by SuperSlickNick2000 on 2008-11-20
This worked for me as well (Intrepid on VAIO VGN-TZ27GN). Just like that if I want a script to be run (as root if possible) at startup where should I put it?

---

### Post by cswert on 2009-05-05
> **IntuitiveNipple said:**
> 

It is available from my Ubuntu PPA (Personal Package Archive). To install it add my PPA to apt's source list:



Thank's very much, mate! Works perfect for me on a Vaio VGN TZ2AWN - no problems, just had to add a "sudo modprobe r5u870" to get the webcam up. And I have been searching a solutions for quite a few hours now.....
Great stuff!

---

### Post by Numer0bis on 2009-05-29
thanks worked perfectly for my sony vaio tz92ns on jaunty

---

### Post by xavivars on 2009-11-07
I've just upgraded to Karmic, and my webcam (VCC4, I've got a Vaio FE) stopped working.

I've tried several things, but I get an error when I try to install ricoh packages from arakhne.org

```
Adding modules to DKMS build system
Doing initial module builds

Error! Bad return status for module build on kernel: 2.6.31-14-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/r5u870/0.11.3/build/ for more information.
Installing initial modules

Error! Could not locate r5u870.ko for module r5u870 in the DKMS tree.
You must run a dkms build for kernel 2.6.31-14-generic (i686) first.
Done.

```

Has anyone solved this issue?

---

### Post by Dr.Dran on 2009-11-07
Hi!
I have the same problem with the amd64 Kernel in Kubuntu Karmic :S

Best regards

Franco Tampieri

---

### Post by galland on 2009-11-19
Hi guys,

I'm the maintainer of the Ricoh webcam package from Arakhne.org.

The version 0.11.3 you have tried to install could not be compiled on newer kernels due to changes in the Video4Linux API.

The version 0.11.4 is patched to be compilable, so installable, on Karmic.

Regards,
Stéphane.

---

### Post by IntuitiveNipple on 2009-11-25
For Karmic and after (and possibly Jaunty) it would be better to use the kernel's **uvcvideo** module (instead of the now deprecated r5u870 module) together with [Alex Hixon's userspace firmware loader tools]("http://bitbucket.org/ahixon/r5u87x/wiki/Home") for those [devices it supports]("http://bitbucket.org/ahixon/r5u87x/src/tip/docs/model_matrix.txt").

```

VID     PID     Chipset Type    Name                                        Notes

0x05CA  0x1803  R5U870  UVC     Flybook V5                                  
0x05CA  0x1810  R5U870  UVC     HP Pavilion Webcam                          
0x05CA  0x1812  Unknown UVC     HP Pavilion Webcam                          Used on HP Pavilion DV6502AU laptops. Apparently does not require ucode.
0x05CA  0x1830  R5U870  WDM     Sony Visual Communication Camera VGP-VCC2   Used on Sony VAIO SZ laptops.
0x05CA  0x1832  R5U870  WDM     Sony Visual Communication Camera VGP-VCC3   Used on Sony VAIO UX laptops.
0x05CA  0x1833  R5U870  WDM     Sony Visual Communication Camera VGP-VCC2   Used on Sony VAIO AR1 laptops.
0x05CA  0x1834  R5U870  WDM     Sony Visual Communication Camera VGP-VCC2   Used on Sony VAIO AR2 laptops.
0x05CA  0x1835  R5U870  UVC     Sony Visual Communication Camera VGP-VCC5   Used on Sony VAIO SZ laptops.
0x05CA  0x1836  R5U870  UVC     Sony Visual Communication Camera VGP-VCC4   Used on Sony VAIO FE laptops.
0x05CA  0x1837  R5U870  UVC     Sony Visual Communication Camera VGP-VCC4   Used on Sony VAIO FZ laptops. The camera is installed upside down.
0x05CA  0x1839  R5U870  UVC     Sony Visual Communication Camera VGP-VCC6   Used on Sony VAIO CR laptops.
0x05CA  0x183a  R5U870  UVC     Sony Visual Communication Camera VGP-VCC7   Used on Sony VAIO SZ and TZ11 laptops.
0x05CA  0x183b  R5U870  UVC     Sony Visual Communication Camera VGP-VCC8   Used on Sony VAIO FZ laptops.
0x05CA  0x183e  R5U870  UVC     Sony Visual Communication Camera VGP-VCC9   Used on Sony VAIO FZ laptops.
0x05CA  0x1841  R5U870  UVC     Fujitsu F01 / Fujitsu Lifebook U810         The camera is installed upside down.                     
0x05CA  0x1870  R5U870  WDM     HP Pavilion Webcam / HP Webcam 1000         VID/PID combination used by two distinct devices. dv1xxx appears to be
                                                                            the less common of the two. The only way to check the difference is to
                                                                            read the model number out via DMI. Not currently supported by loader.


```
Willem Van Engel did try to get the tools added to the Ubuntu repositories ([bug #120434]("https://bugs.launchpad.net/ubuntu/+bug/120434")) but they were rejected and removed from his PPA because the firmware images contained in the package don't have a suitable license to allow redistribution.

As a result it is necessary to install the userspace tools and firmware images from Alex's code repository. The [instructions on installing are in the source repository]("http://bitbucket.org/ahixon/r5u87x/src/tip/README#cl-29").
```

sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
hg clone http://bitbucket.org/ahixon/r5u87x/
cd r5u87x
make
sudo make install

```
This installs a udev rule (/etc/udev/rules.d/90-r5u87x-loader.rules) which ensures that the firmware is loaded when the kernel discovers the camera (on reboots, resumes, etc.).

To reload the camera driver manually and upload the firmware:
```

sudo r5u87x-loader --reload

r5u87x firmware loader v0.2

Searching for device...
Found camera: 05ca:1836
Camera reports negative microcode state.
Sending microcode to camera...
Enabled microcode.
Camera reports microcode version 0x0115.

Successfully uploaded firmware to device 05ca:1836!
Reloading uvcvideo module...
Finished.


```
The log (/var/log/kern.log) should show something like:
```

[10358.844446] Linux video capture interface: v2.00
[10358.849638] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:1836)
[10358.850902] input: UVC Camera (05ca:1836) as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input12
[10358.851002] usbcore: registered new interface driver uvcvideo
[10358.851008] USB Video Class driver (v0.1.0)

```

---

### Post by Francus on 2009-11-27
I tried to install it on Jaunty, but Skype does not see the webcam. On the terminal got some curious messages:

Successfully uploaded firmware to device 05ca:1830!
Reloading uvcvideo module...
WARNING: All config files need .conf: /etc/modprobe.d/snd-hda-intel, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/hsf, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/hsf.conflicts, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/snd-hda-intel, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/hsf, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/hsf.conflicts, it will be ignored in a future release.
Finished.

The The log (/var/log/kern.log) gives:

Nov 27 14:59:26 VAIO kernel: [ 2020.615210] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
Nov 27 15:16:14 VAIO kernel: [ 3028.751232] Linux video capture interface: v2.00
Nov 27 15:16:14 VAIO kernel: [ 3028.781627] usbcore: registered new interface driver uvcvideo
Nov 27 15:16:14 VAIO kernel: [ 3028.781635] USB Video Class driver (v0.1.0)

So it seems it is working, but skype does not see it because it is using some other obsolete stuff.

Any idea?

Best

---

### Post by galland on 2009-11-27
Hi Francus,

Are you sure you are a member of the video group?

One of the common simple errors encountered with this driver in Skype (and other software) is that the driver create /dev/video* with write right set for the members of the "video" group. So you may be inside this group to allow your software to use the webcam.

Stéphane.

---

### Post by devrandom1 on 2009-11-27
I'm seeing the same thing.  The /dev/video0 device node is not created. Based on the dmesg output, it doesn't look like the uvcvideo module recognized the USB device.

Manually creating the /dev/video0 device doesn't help - getting "no device address" or similar message.

Firmware was successfully uploaded using the r5u870_k2.6.30_i386.tar.bz2 tools.  Another USB cam with a different driver works fine when plugged in.

---

### Post by Francus on 2009-11-27
> **galland said:**
> Hi Francus,

Are you sure you are a member of the video group?

One of the common simple errors encountered with this driver in Skype (and other software) is that the driver create /dev/video* with write right set for the members of the "video" group. So you may be inside this group to allow your software to use the webcam.

Stéphane.

Well, don't know. I checked into grops and a video group does not exist. I tried to create it myself and get myself part of this group, but no improvement.

I also checked dmesg and got the following:

[  239.329037] Linux video capture interface: v2.00
[  239.352521] usbcore: registered new interface driver uvcvideo
[  239.352528] USB Video Class driver (v0.1.0)
[  241.600074] usbcore: deregistering interface driver uvcvideo
[  241.621510] Linux video capture interface: v2.00
[  241.627393] usbcore: registered new interface driver uvcvideo
[  241.627399] USB Video Class driver (v0.1.0)

So it seems that the driver is working

Any idea?

Best

---

### Post by avilella on 2009-11-29
It seems that the latest version is available here:

[http://www.palmix.org/r5u870-en.html](http://www.palmix.org/r5u870-en.html)

But now it doesn't work for the newest 2.6.31:

avilella@magneto:~/sonyvaio/camera/latest/r5u870$ sudo make install
make -C /lib/modules/2.6.31-15-generic/build M=/home/avilella/sonyvaio/camera/latest/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
  CC [M] /home/avilella/sonyvaio/camera/latest/r5u870/r5u870_md.o
In file included from /home/avilella/sonyvaio/camera/latest/r5u870/r5u870_md.c:55:
/home/avilella/sonyvaio/camera/latest/r5u870/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
make[2]: *** [/home/avilella/sonyvaio/camera/latest/r5u870/r5u870_md.o] Error 1
make[1]: *** [_module_/home/avilella/sonyvaio/camera/latest/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'
make: *** [all] Error 2


> **Dr.Dran said:**
> Hi!
I have the same problem with the amd64 Kernel in Kubuntu Karmic :S

Best regards

Franco Tampieri

---

### Post by galland on 2009-11-29
Hi guys,

I will ltry to sumarize the process to install a Ricoh webcam here to help you.

Two drivers are currently available on Internet: r5u870 and r5u87x.

First of all you need to determine if your webcam has a WDM chipset (see [here]("http://www.bitbucket.org/ahixon/r5u87x/src/881dbd07a263/docs/model_matrix.txt")).

Driver r5u870 requires a kernel module and supports WDM chipsets. Driver r5u87x does not requires a kernel module but does not support WDM chipsets.

To install r5u870, you need to use one of the driver's versions according to your kernel version. [Arakhne.org]("http://www.arakhne.org/ricoh/") gives several of them. On lastest kernels, DKMS is using. I'm currently using 2.6.31.15.28-i386 kernel and r5u870 works fine.

To install r5u87x, you need to [download]("http://bitbucket.org/ahixon/r5u87x/") and compile by hand. Never tried because my webcam is a WDM.

All my explorations on r5u870 are related to [http://www.arakhne.org/ricoh/](http://www.arakhne.org/ricoh/)

When loaded, the driver must create a /dev/videoXX file (where XX is a number). If no /dev/videoXX file is created, your kernel or your webcam driver does not recognize your webcam device.
Creating by hand the /dev/videoXX does not help because no driver in the kernel is using it. If not present you must try another way.

Finally to use your webcam you need to put your user inside the "video" group. (This video may not be manually created because it is a default standard group on Ubuntu. You may only put your user inside).

Stéphane.

---

### Post by superlex on 2009-12-07
Hi!
I have a Sony VAIO fz31m. My webcam is
```
05ca: 183B Ricoh Co., Ltd Visual Communication Camera VGP-VCC8 [r5u870]
```
I followed the instructions
> sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
hg clone [http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)
cd r5u87x
make
sudo make install
and now my webcam is set for the module uvcvideo and it work very well woth high resolutions (there are still problems with low ones).

> r5u87x firmware loader v0.2

Searching for device...
Found camera: 05ca:183b
Camera reports positive microcode state.
Camera reports microcode version 0x0131.
Not doing anything - camera already setup.

Successfully uploaded firmware to device 05ca:183b!
Reloading uvcvideo module...
Finished.

Even before my webcam works with the uvcvideo module, but sometimes it was not loaded. Now everything seems affixed instead.

There are possibilities that the package r5u87x be included in the Ubuntu repositories and automatically installed?

---

### Post by beezwings on 2009-12-07
> **galland said:**
> Hi Francus,

Are you sure you are a member of the video group?

One of the common simple errors encountered with this driver in Skype (and other software) is that the driver create /dev/video* with write right set for the members of the "video" group. So you may be inside this group to allow your software to use the webcam.

Stéphane.

I don't really understand how to put myself in the "video" group. I checked the /dev/video0 properties, and it does say the group "video" has read and write access, but when I go to "Manage Groups" no such group exists. 

My camera is recognized in gstreamer-properties, but not in Cheese or in Skype. Please, any ideas?  I have the Ricoh Co., Ltd Visual Communication Camera VGP-VCC2 running in Jaunty, with the r5u870 driver installed from the repos.

Please help!!

---

### Post by beezwings on 2009-12-07
> **beezwings said:**
> I don't really understand how to put myself in the "video" group. I checked the /dev/video0 properties, and it does say the group "video" has read and write access, but when I go to "Manage Groups" no such group exists. 

My camera is recognized in gstreamer-properties, but not in Cheese or in Skype. Please, any ideas?  I have the Ricoh Co., Ltd Visual Communication Camera VGP-VCC2 running in Jaunty, with the r5u870 driver installed from the repos.

Please help!!


I found a solution!

(Copied from [http://forum.skype.com/index.php?showtopic=137911#entry618201](http://forum.skype.com/index.php?showtopic=137911#entry618201))

Edit the file /home/YOURUSERNAME/.Skype/YOURSKYPEID/config.xml

and change the value

<Video>
<Disable>1</Disable>
</Video>

to

<Video>
<Disable>0</Disable>
</Video> 

Hope this helps.  Still can't get it to work in Cheese though...

---

### Post by superlex on 2009-12-08
> **beezwings said:**
> I found a solution!

(Copied from [http://forum.skype.com/index.php?showtopic=137911#entry618201](http://forum.skype.com/index.php?showtopic=137911#entry618201))

Edit the file /home/YOURUSERNAME/.Skype/YOURSKYPEID/config.xml

and change the value

<Video>
<Disable>1</Disable>
</Video>

to

<Video>
<Disable>0</Disable>
</Video> 

Hope this helps.  Still can't get it to work in Cheese though...

If you use r5u870 driver, to work in cheese you should do this:

```
cd /usr/share/hal/fdi/information/20thirdparty
sudo wget http://students.ceid.upatras.gr/~asimakis/10-r5u870-webcam.fdi
sudo /etc/init.d/hal restart
```

---

### Post by seventh-star on 2009-12-13
I keep receiving an abort when I select to continue or not continue with the following line:

username@user-laptop:~$ sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
gcc is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  autoconf autotools-dev m4 mercurial-common
Suggested packages:
  autoconf2.13 autobook autoconf-archive gnu-standards autoconf-doc libtool
  gettext libglib2.0-doc qct vim emacs kdiff3 tkdiff meld xxdiff
  python-mysqldb python-pygments
The following NEW packages will be installed:
  autoconf automake autotools-dev libglib2.0-dev libusb-dev m4 mercurial
  mercurial-common
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,628kB of archives.
After this operation, 14.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
username@user-laptop:~$ 

I don't know what's going on.
Thanks for anyone who can help.

---

### Post by superlex on 2009-12-21
> **seventh-star said:**
> I keep receiving an abort when I select to continue or not continue with the following line:

username@user-laptop:~$ sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
gcc is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  autoconf autotools-dev m4 mercurial-common
Suggested packages:
  autoconf2.13 autobook autoconf-archive gnu-standards autoconf-doc libtool
  gettext libglib2.0-doc qct vim emacs kdiff3 tkdiff meld xxdiff
  python-mysqldb python-pygments
The following NEW packages will be installed:
  autoconf automake autotools-dev libglib2.0-dev libusb-dev m4 mercurial
  mercurial-common
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,628kB of archives.
After this operation, 14.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
username@user-laptop:~$ 

I don't know what's going on.
Thanks for anyone who can help.

Y, no y

---

### Post by seventh-star on 2009-12-21
Re: 
 	Quote:
 	 	 		 			 				 					Originally Posted by **seventh-star** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8491918#post8491918") 				
 				[I]I keep receiving an abort when I select to continue or not continue with the following line:

username@user-laptop:~$ sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
gcc is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  autoconf autotools-dev m4 mercurial-common
Suggested packages:
  autoconf2.13 autobook autoconf-archive gnu-standards autoconf-doc libtool
  gettext libglib2.0-doc qct vim emacs kdiff3 tkdiff meld xxdiff
  python-mysqldb python-pygments
The following NEW packages will be installed:
  autoconf automake autotools-dev libglib2.0-dev libusb-dev m4 mercurial
  mercurial-common
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,628kB of archives.
After this operation, 14.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
username@user-laptop:~$ 

I don't know what's going on.
Thanks for anyone who can help.[/I]
 			 		 	 	 
Y, no y

I've tried both Y and y and N and n and received the exact same message.

---

### Post by SteveMcQwark on 2010-01-10
Anyone know why r5u87x doesn't work at resolutions lower than 640x480?

---

### Post by superlex on 2010-02-18
> **SteveMcQwark said:**
> Anyone know why r5u87x doesn't work at resolutions lower than 640x480?


This is a uvcvideo bug, I think.

---

### Post by superlex on 2010-02-26
I have really good info: with kernel 2.6.33 the bug of uvcvideo has been resolved and all resolutions work fine :popcorn:

---

### Post by oooh on 2010-03-02
Hi

I would like to know if this driver from [http://arakhne.org/ricoh/index.html](http://arakhne.org/ricoh/index.html)  allows Brightness and Contrast control of the camera.

The ru5870 does not allow that due to firmaware limitations, that is why I am asking.

Cheers

---

### Post by superlex on 2010-03-02
> **oooh said:**
> Hi

I would like to know if this driver from [http://arakhne.org/ricoh/index.html](http://arakhne.org/ricoh/index.html)  allows Brightness and Contrast control of the camera.

The ru5870 does not allow that due to firmaware limitations, that is why I am asking.

Cheers

I'm using [http://sourceforge.net/projects/v4l2ucp/](http://sourceforge.net/projects/v4l2ucp/) for brightness control

---

### Post by oooh on 2010-03-02
I will give that I try

However, after speaking with the r5u870 driver developers ([http://palmix.org/r5u870-en.html](http://palmix.org/r5u870-en.html)) and they told me that it is a firmware limitation of the firmware dump that this driver uses.

Are you using this driver or the one from [http://arakhne.org/ricoh/index.html](http://arakhne.org/ricoh/index.html) ?

---

### Post by superlex on 2010-03-02
No, I'm using uvcvideo. 

I followed this procedure:

```
sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
hg clone http://bitbucket.org/ahixon/r5u87x/
cd r5u87x
make
sudo make install
```

---

### Post by oooh on 2010-03-02
As it seems the r5u870 is just being replaced by r5u87x , I tried, and it works PERFECT

My problem now is that the video in SKYPE is transparent, double and zoomed in

Any hints for this ?

"You set a circus, and you get dwarfs" (Spanish saying meaning that you solve a matter, and more problems appear...) :)

---

### Post by superlex on 2010-03-03
Try with kernel 2.6.33 [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/) :)

---

### Post by oooh on 2010-03-04
Sure I will give that a try, but before that I want to try out the Skype video configurations:

[http://ubuntuforums.org/showthread.php?p=8916383#post8916383](http://ubuntuforums.org/showthread.php?p=8916383#post8916383)

Still not working fully, but I got some improvements!

---

### Post by oooh on 2010-03-07
I updated to Skype 2.1.0.81 and it solved the matter. I also needed to do this:

    <Video>
      <AutoSend>1</AutoSend>
      <CaptureHeight>480</CaptureHeight>
      <CaptureWidth>640</CaptureWidth>
      <Fps>32</Fps>
      <RecvPolicy>callpolicy</RecvPolicy>
    </Video>

In the configuration file of skype, /USERHOME/.Skype/USER/config.xml

Issue solved, r5u87x driver rocks

---

### Post by superlex on 2010-03-27
> **oooh said:**
> As it seems the r5u870 is just being replaced by r5u87x , I tried, and it works PERFECT

My problem now is that the video in SKYPE is transparent, double and zoomed in

Any hints for this ?

"You set a circus, and you get dwarfs" (Spanish saying meaning that you solve a matter, and more problems appear...) :)

Please, try doing this:

```
sudo apt-get install mercurial
hg clone http://linuxtv.org/hg/~pinchartl/uvcvideo/
cd uvcvideo
make 
sudo make install
```

---

### Post by oooh on 2010-03-27
Sure I did that already, and it made the camera work fine

However, it was giving me the double image in skype, which was not a uvc problem but a skype problem

Finally, your suggestion plus skype updating solved the matter completelly

So now I have it working fully with brightness control, contrast, everything !!!

Gracias  for the info !

---

### Post by Shannon_VanWagner on 2010-03-30
Hi All.

I used comment [#16 at this bug]("https://bugs.launchpad.net/ubuntu/+bug/120434/comments/16") to fix this.

Basically, it's just installing 2 *.deb files (firmware and driver) from:
[http://www.arakhne.org/ricoh/index.html](http://www.arakhne.org/ricoh/index.html)

Works on Sony Vaio SZ670N
$ lsusb |grep Ricoh
Bus 001 Device 003: ID 05ca:183a Ricoh Co., Ltd Visual Communication Camera VGP-VCC7 [R5U870]

Be sure to install build-essential, linux-headers-generic, and possibly others for dependency req.

Hope this helps someone!

---

### Post by dre12b on 2010-04-01
Thanks for all of the help on this issue put into the thread.  I'm getting the webcam on a Sony VGN-FZ140E to use Skype and Ekiga.  Two questions:

1) I installed the r5u870 driver before realizing I can use r5u87x and uvcvideo.  Do I need to uninstall?  
2) Ran the commands listed above to make and make install uvcvideo.  Got some errors.  I've included the last errors below, but here are more (don't want to post too much text).  Am I doing something wrong?  I did this after installing r5u870 and then r5u87x.

make[3]: *** [/home/ddutra/Downloads/uvcvideo/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/ddutra/Downloads/uvcvideo/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/ddutra/Downloads/uvcvideo/v4l'
make: *** [all] Error 2

I'm very inexperienced with Linux but follow directions well.  Any help or suggestions are appreciated!

---

### Post by superlex on 2010-04-01
> **dre12b said:**
> Thanks for all of the help on this issue put into the thread.  I'm getting the webcam on a Sony VGN-FZ140E to use Skype and Ekiga.  Two questions:

1) I installed the r5u870 driver before realizing I can use r5u87x and uvcvideo.  Do I need to uninstall?  
2) Ran the commands listed above to make and make install uvcvideo.  Got some errors.  I've included the last errors below, but here are more (don't want to post too much text).  Am I doing something wrong?  I did this after installing r5u870 and then r5u87x.

make[3]: *** [/home/ddutra/Downloads/uvcvideo/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/ddutra/Downloads/uvcvideo/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/ddutra/Downloads/uvcvideo/v4l'
make: *** [all] Error 2

I'm very inexperienced with Linux but follow directions well.  Any help or suggestions are appreciated!

Go to /uvcvideo/v4l/ directory and edit file colled .config replacing  
CONFIG_DVB_FIREDTV=m
with
CONFIG_DVB_FIREDTV=n
You can use gedit.


@Shannon_VanWagner
did not understand what is your problem exactly ..

---

### Post by Shannon_VanWagner on 2010-04-01
@superlex
I was just saying that I made my Sony Vaio VGN-SZ670N webcam work simply by installing these two *.deb files (my system is 32-bit intel-based):

1.)
[http://download.tuxfamily.org/arakhne/pool/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870-firmware_0.11.4-0arakhne1_i386.deb](http://download.tuxfamily.org/arakhne/pool/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870-firmware_0.11.4-0arakhne1_i386.deb)

2.)
[http://download.tuxfamily.org/arakhne/pool/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870_0.11.4-0arakhne1_i386.deb](http://download.tuxfamily.org/arakhne/pool/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870_0.11.4-0arakhne1_i386.deb)

@dre12b - maybe you could try installing the two packages above and perhaps it will make your webcam work too!

These pages provide more details:
[http://www.arakhne.org/ricoh/index.html](http://www.arakhne.org/ricoh/index.html)
(see comment #16 here) [https://bugs.launchpad.net/ubuntu/+bug/120434](https://bugs.launchpad.net/ubuntu/+bug/120434)

Cheers!

---

### Post by dre12b on 2010-04-01
@ShannonVanWagner
Thanks for the suggestion.  I installed those .deb on a previous setup on this machine.  It did make the webcam work, but evidently the webcam is installed upside down on this laptop.  In skype, the result was always an inverted image.  Problem is listed [here]("http://bitbucket.org/ahixon/r5u87x/src/tip/docs/model_matrix.txt").  I'm hoping the r5u87x will provide a fix for this.

---

### Post by dre12b on 2010-04-01
@superlex
Thanks for the patient help!
Make and make install for r5u87x did not give the error messages after making the change you suggested.  I did a manual reload of the firmware as per an earlier post in this thread and the firmware was confirmed as correctly loaded, but I was informed that modprobe.conf was deprecated - must be in modprobe.d.  So I moved /etc/modprobe.conf to /etc/modprobe.d and then rebooted. (these are really stabs in the dark on my part, in case that's not obvious!)

Skype and ekiga are showing the device UVC camera, but it does not work.  I opened /dev/video0 as root to confirm video group membership, but the file is empty.  Found the command elsewhere on the forum and it successfully added user to video group.  Still no dice with Skype or Ekiga, although the green light one the webcam comes on.  No image.
sudo gpasswd -a myusername video

---

### Post by superlex on 2010-04-01
> **Shannon_VanWagner said:**
> @superlex
I was just saying that I made my Sony Vaio VGN-SZ670N webcam work simply by installing these two *.deb files (my system is 32-bit intel-based):

1.)
[http://download.tuxfamily.org/arakhne/pool/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870-firmware_0.11.4-0arakhne1_i386.deb](http://download.tuxfamily.org/arakhne/pool/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870-firmware_0.11.4-0arakhne1_i386.deb)

2.)
[http://download.tuxfamily.org/arakhne/pool/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870_0.11.4-0arakhne1_i386.deb](http://download.tuxfamily.org/arakhne/pool/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870_0.11.4-0arakhne1_i386.deb)

@dre12b - maybe you could try installing the two packages above and perhaps it will make your webcam work too!

These pages provide more details:
[http://www.arakhne.org/ricoh/index.html](http://www.arakhne.org/ricoh/index.html)
(see comment #16 here) [https://bugs.launchpad.net/ubuntu/+bug/120434](https://bugs.launchpad.net/ubuntu/+bug/120434)

Cheers!

Ah, ok :) According to deegan, we can use in fact both r5u870 driver then r587x ones.

> Hi guys,

I will ltry to sumarize the process to install a Ricoh webcam here to help you.

Two drivers are currently available on Internet: r5u870 and r5u87x.

First of all you need to determine if your webcam has a WDM chipset (see here).

Driver r5u870 requires a kernel module and supports WDM chipsets. Driver r5u87x does not requires a kernel module but does not support WDM chipsets.

To install r5u870, you need to use one of the driver's versions according to your kernel version. Arakhne.org gives several of them. On lastest kernels, DKMS is using. I'm currently using 2.6.31.15.28-i386 kernel and r5u870 works fine.

To install r5u87x, you need to download and compile by hand. Never tried because my webcam is a WDM.

All my explorations on r5u870 are related to [http://www.arakhne.org/ricoh/](http://www.arakhne.org/ricoh/)

...


Thanks to report the link for the packages.

---

### Post by superlex on 2010-04-01
> **dre12b said:**
> @superlex
Thanks for the patient help!
Make and make install for r5u87x did not give the error messages after making the change you suggested.  I did a manual reload of the firmware as per an earlier post in this thread and the firmware was confirmed as correctly loaded, but I was informed that modprobe.conf was deprecated - must be in modprobe.d.  So I moved /etc/modprobe.conf to /etc/modprobe.d and then rebooted. (these are really stabs in the dark on my part, in case that's not obvious!)

Skype and ekiga are showing the device UVC camera, but it does not work.  I opened /dev/video0 as root to confirm video group membership, but the file is empty.  Found the command elsewhere on the forum and it successfully added user to video group.  Still no dice with Skype or Ekiga, although the green light one the webcam comes on.  No image.
sudo gpasswd -a myusername video

My suggestions refers to uvcvideo compilation, not to r5u87x. However, pheraps you must increase image's resolution. Try with cheese.
For the inverted image, search here
[http://ubuntuforums.org/archive/index.php/t-561433.html](http://ubuntuforums.org/archive/index.php/t-561433.html)
the solution.

Ps:
As regards ```
So I moved /etc/modprobe.conf to /etc/modprobe.d and then rebooted.
```
not seems to be correct solution.

---

### Post by dre12b on 2010-04-02
Any insight regarding correct way to solve the problem, or a nudge in the right direction would be greatly appreciated!

---

### Post by dre12b on 2010-04-04
OK, I did a new install (not for issue discussed in this thread) using 9.10 server 32-bit and then added a minimal kde desktop to build on.  I'm using 2.6.31-20-generic-pae kernel.  

Checked and uvcvideo was running.  Cloned mercurial of r5u87x, ran make and make install.  Rebooted.  Lsusb shows the device.  The webcam lights up when I open cheese or skype and both programs show uvc webcam, but no image.  Same with Ekiga.  Cloned mercurial of uvcvideo, ran make and make install (adjusted value for firedtv as per post #51).  Rebooted.  Same situation.  

Ran make uninstall for r5u87x and then installed the two deb packages for r5u870.  Rebooted.  Ran modprobe r5u870.  Same situation, but I noticed that the programs still listed the device as uvc.

Do I need to update to 2.6.33 as per comment #44?  I'm not sure what else to try.  I'm learning, but still getting no webcam love!  

Thanks for all the help.  I'll follow up with the upside down image fix once I can get an image.

---

### Post by dre12b on 2010-04-19
So, tried all the directions, even updated to the latest kernel.  No webcam with Skype, Ekiga, or Cheese.  Then I installed Kopete and I get an image from the webcam, but it's upside down.  Tried the latest patch to fix this problem, but no luck.

I'm frustrated. I just don't have enough know-how to troubleshoot this stuff on my own.  And the amount of time I have to make ubuntu work with my hardware has already been eaten up.  So I've got a crippled Ubuntu box.  Love the way OS runs, but I can't use all the hardware and every time I want to video conference I have to use another OS.  

I'll continue to follow this thread in the event someone can offer guidance.

---

### Post by superlex on 2010-04-21
@galland and IntuitiveNipple

Hi, after hibernation uvcvideo failed to load, but with comand
```
/usr/sbin/r5u87x-loader --reload
```
it works yet.
Is there a way to run the rule automatically after hibernation?

---

### Post by fire.for.effect on 2010-05-28
> **Shannon_VanWagner said:**
> 

...1.)
[http://download.tuxfamily.org/arakhne/pool/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870-firmware_0.11.4-0arakhne1_i386.deb](http://download.tuxfamily.org/arakhne/pool/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870-firmware_0.11.4-0arakhne1_i386.deb)

2.)
[http://download.tuxfamily.org/arakhne/pool/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870_0.11.4-0arakhne1_i386.deb](http://download.tuxfamily.org/arakhne/pool/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870_0.11.4-0arakhne1_i386.deb)

  ...maybe you could try installing the two packages above and perhaps it will make your webcam work too!...

[CENTER][SIZE=5][FONT=Courier New][B][SIZE=4]SONY VAIO VGN-FZ240E
Ricoh VGP-VCC8 05ca:183b[/SIZE][/B]

[SIZE=4]MY GOD! IT WORKS! AND NOW I CAN DO VIDEO WITH THE WIFEY FROM IRAQ AFTER 6 MONTHS OF MISERY!
:guitar:
[/SIZE] [/FONT][/SIZE] [/CENTER]

---

### Post by dre12b on 2010-11-16
that's good news, friend!  congratulations!

---

### Post by elect on 2010-11-22
10.10

Bus 001 Device 002: ID 05ca:1837 Ricoh Co., Ltd Visual Communication Camera VGP-VCC4 [R5U870]

camorama works
cheese and skype dont

r5u87x 

ideas?

Ps: I noticed that also if i followed r5u870 and r5u87x guides, when I try to run "sudo modprobe r5u870/x" i get nothing, it cannot find them..

why?

---

### Post by mmoalem on 2010-12-13
hi there sorry to post this again but my separate thread doesn't have any replys
lost webcam on upgrade to maverick it's a wdm version 05ca:1830
full details here:
[http://ubuntuforums.org/showthread.php?p=10233062#post10233062](http://ubuntuforums.org/showthread.php?p=10233062#post10233062)

---

### Post by authenticroger on 2012-12-28
> **fire.for.effect said:**
> SONY VAIO VGN-FZ240E
Ricoh VGP-VCC8 05ca:183b

MY GOD! IT WORKS! AND NOW I CAN DO VIDEO WITH THE WIFEY FROM IRAQ AFTER 6 MONTHS OF MISERY!
:guitar:

So now here I sit in Afghanistan and it doesn't work anymore. The old links for the drivers are dead and I'm thinking about painting a target on thislaptop and taking it to the range with me on Saturday. Any ideas on how to get the camera up and going again?

---

### Post by howefield on 2012-12-28
Old thread closed. Feel free to start a fresh one.

---

