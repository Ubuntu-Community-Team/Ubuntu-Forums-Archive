---
title: "Sony VAIO built-in MOtion Eye camera setup"
date: 2010-08-02
forum: Hardware
---

### Post by Lavix on 2010-08-02
I installed Ubuntu 10.04 on my laptop Sony VAIO VGN-FJ3SR the full descrition of which is put at:
[http://support.vaio.sony.eu/computing/vaio/specifications/index.aspx?l=en_gb&m=VGN-FJ3SR_B](http://support.vaio.sony.eu/computing/vaio/specifications/index.aspx?l=en_gb&m=VGN-FJ3SR_B)

Is it possible to make work the built-in camera ?

Thank in advance.

---

### Post by P4man on 2010-08-02
Are you sure its not working? What apps did you test it with? The vast majority of webcams doesnt need any drivers, they just work. Try installing "cheese" and see if it works or not.

---

### Post by Lavix on 2010-08-03
I think I'm sure because it's nowhere, neither in Skype, nor in Ekiga nor in Audio/Video devices, so I don't event know how to check it in any other way.
By the way what's that - 'cheese' ?

---

### Post by P4man on 2010-08-03
cheese is just a cheesy webcam app (its in the repo's). 

Can you post the output of

```
lsusb
```

and 

```
lspci
```

---

### Post by Lavix on 2010-08-03
I'll post the results this evening because I'm not at home and haven't the laptop.

---

### Post by Alfons81 on 2010-08-03
Check this thread, I solved the issue the way they explain:

[http://ubuntuforums.org/showthread.php?t=821343](http://ubuntuforums.org/showthread.php?t=821343)

I think you'll need to install build-essential, to compile the driver. "OryonFire" is explaining the way to compile this driver step by step.

As "P4man" told you, if you want to know the model of your webcam, run in your terminal:

$ lsusb

f you want to know all the hardware you have, just run:

$ lshw

Hope you slve it soon.

---

### Post by Lavix on 2010-08-03
So, here are the outputs:
```

serge@serge-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0ac8:c002 Z-Star Microelectronics Corp. Visual Communication Camera VGP-VCC1
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
serge@serge-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:09.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:09.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:09.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:0a.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
serge@serge-laptop:~$ 

```

I've already tried to execute the 'lsusb' command, so it seems that the camera was recognized. What to do now? thanks

---

### Post by AlanR8 on 2010-08-03
You need to read this thread.....

[http://ubuntuforums.org/showthread.php?t=968381](http://ubuntuforums.org/showthread.php?t=968381)

---

### Post by Lavix on 2010-08-05
Hi everybody, so here is what I get when trying to install it as described in one of yuor links [http://ubuntuforums.org/showthread.php?t=821343](http://ubuntuforums.org/showthread.php?t=821343)
```

serge@serge-laptop:~$ svn co http://svn.mediati.org/svn/r5u870/trunk ~/r5u870
A    /home/serge/r5u870/r5u870_183a.fw
A    /home/serge/r5u870/r5u870_183b.fw
A    /home/serge/r5u870/r5u870_1870_1.fw
A    /home/serge/r5u870/r5u870_183e.fw
A    /home/serge/r5u870/AUTHORS
A    /home/serge/r5u870/ChangeLog
A    /home/serge/r5u870/r5u870.c
A    /home/serge/r5u870/recode-fw.scm
A    /home/serge/r5u870/debug.mk
A    /home/serge/r5u870/README
A    /home/serge/r5u870/r5u870_1810.fw
A    /home/serge/r5u870/r5u870_1812.fw
A    /home/serge/r5u870/r5u870_1830.fw
A    /home/serge/r5u870/r5u870_1841.fw
A    /home/serge/r5u870/r5u870_1832.fw
A    /home/serge/r5u870/r5u870_1833.fw
A    /home/serge/r5u870/r5u870_1834.fw
A    /home/serge/r5u870/r5u870_1870.fw
A    /home/serge/r5u870/r5u870_1835.fw
A    /home/serge/r5u870/r5u870_1836.fw
A    /home/serge/r5u870/COPYING
A    /home/serge/r5u870/r5u870_1839.fw
A    /home/serge/r5u870/MAINTAINERS
A    /home/serge/r5u870/Kbuild
A    /home/serge/r5u870/usbcam
A    /home/serge/r5u870/usbcam/usbcam.h
A    /home/serge/r5u870/usbcam/usbcam_priv.h
A    /home/serge/r5u870/usbcam/usbcam_fops.c
A    /home/serge/r5u870/usbcam/usbcam_buf.c
A    /home/serge/r5u870/usbcam/usbcam_util.c
A    /home/serge/r5u870/usbcam/usbcam_dev.c
A    /home/serge/r5u870/usbcam/usbcam_skel.c
A    /home/serge/r5u870/usbcam/Makefile
A    /home/serge/r5u870/NEWS
A    /home/serge/r5u870/Makefile
Checked out revision 109.
serge@serge-laptop:~$ cd ~/r5u870
serge@serge-laptop:~/r5u870$ sudo make
[sudo] password for serge: 
make -C /lib/modules/2.6.32-24-generic/build M=/home/serge/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/serge/r5u870/r5u870.o
/home/serge/r5u870/r5u870.c:872:1: warning: "V4L2_CID_PRIVACY" redefined
In file included from include/linux/videodev.h:17,
                 from /home/serge/r5u870/usbcam/usbcam.h:38,
                 from /home/serge/r5u870/r5u870.c:59:
include/linux/videodev2.h:1160:1: warning: this is the location of the previous definition
  CC [M]  /home/serge/r5u870/usbcam/usbcam_dev.o
/home/serge/r5u870/usbcam/usbcam_dev.c: In function ‘usbcam_register_mod’:
/home/serge/r5u870/usbcam/usbcam_dev.c:535: warning: assignment from incompatible pointer type
  CC [M]  /home/serge/r5u870/usbcam/usbcam_fops.o
/home/serge/r5u870/usbcam/usbcam_fops.c: In function ‘usbcam_v4l_vidioc_querycap’:
/home/serge/r5u870/usbcam/usbcam_fops.c:522: error: ‘struct device’ has no member named ‘bus_id’
/home/serge/r5u870/usbcam/usbcam_fops.c: In function ‘usbcam_v4l_ioctl’:
/home/serge/r5u870/usbcam/usbcam_fops.c:1170: warning: passing argument 1 of ‘video_usercopy’ from incompatible pointer type
include/media/v4l2-ioctl.h:298: note: expected ‘struct file *’ but argument is of type ‘struct inode *’
/home/serge/r5u870/usbcam/usbcam_fops.c:1170: warning: passing argument 2 of ‘video_usercopy’ makes integer from pointer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘unsigned int’ but argument is of type ‘struct file *’
/home/serge/r5u870/usbcam/usbcam_fops.c:1170: warning: passing argument 4 of ‘video_usercopy’ makes pointer from integer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘v4l2_kioctl’ but argument is of type ‘long unsigned int’
/home/serge/r5u870/usbcam/usbcam_fops.c:1170: error: too many arguments to function ‘video_usercopy’
/home/serge/r5u870/usbcam/usbcam_fops.c:1174: warning: passing argument 1 of ‘video_ioctl2’ from incompatible pointer type
include/media/v4l2-ioctl.h:302: note: expected ‘struct file *’ but argument is of type ‘struct inode *’
/home/serge/r5u870/usbcam/usbcam_fops.c:1174: warning: passing argument 2 of ‘video_ioctl2’ makes integer from pointer without a cast
include/media/v4l2-ioctl.h:302: note: expected ‘unsigned int’ but argument is of type ‘struct file *’
/home/serge/r5u870/usbcam/usbcam_fops.c:1174: error: too many arguments to function ‘video_ioctl2’
/home/serge/r5u870/usbcam/usbcam_fops.c:1162: warning: unused variable ‘udp’
make[3]: *** [/home/serge/r5u870/usbcam/usbcam_fops.o] Error 1
make[2]: *** [/home/serge/r5u870/usbcam] Error 2
make[1]: *** [_module_/home/serge/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [all] Error 2
serge@serge-laptop:~/r5u870$ 

```
Any suggestions ?

---

### Post by Lavix on 2010-08-05
@AlanR8.
Here is what I got when trying your link:
```

serge@serge-laptop:~/Software/r5u87x$ make
cc -g -Wall -DHAVE_CONFIG_H -DUCODE_PATH=\"/usr/lib/r5u87x/ucode/r5u87x-%vid%-%pid%.fw\"  `pkg-config --cflags glib-2.0 libusb` -c loader.c loader.h
Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found
Package libusb was not found in the pkg-config search path.
Perhaps you should add the directory containing `libusb.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libusb' found
loader.c:28:18: error: glib.h: No such file or directory
loader.c:29:25: error: glib/gstdio.h: No such file or directory
loader.c:30:17: error: usb.h: No such file or directory
loader.c:41: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c:45: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘force_clear’
loader.c:46: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘no_load’
loader.c:48: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c:49: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘dump_ucode’
loader.c:50: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘reload’
loader.c:52: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘entries’
loader.c:77: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c: In function ‘find_device’:
loader.c:98: error: ‘gint’ undeclared (first use in this function)
loader.c:98: error: (Each undeclared identifier is reported only once
loader.c:98: error: for each function it appears in.)
loader.c:98: error: expected ‘;’ before ‘i’
loader.c:102: warning: implicit declaration of function ‘usb_get_busses’
loader.c:102: warning: assignment makes pointer from integer without a cast
loader.c:103: error: dereferencing pointer to incomplete type
loader.c:106: error: dereferencing pointer to incomplete type
loader.c:106: error: dereferencing pointer to incomplete type
loader.c:108: error: ‘i’ undeclared (first use in this function)
loader.c:109: error: dereferencing pointer to incomplete type
loader.c:110: error: dereferencing pointer to incomplete type
loader.c:111: error: dereferencing pointer to incomplete type
loader.c: At top level:
loader.c:128: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_image_flip’
loader.c:150: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_upload’
loader.c:232: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_status’
loader.c:249: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_version’
loader.c:268: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_enable’
loader.c:285: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_clear’
loader.c:306: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c:320: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘load_firmware’
loader.c:436: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘main’
loader.h:21:18: error: glib.h: No such file or directory
make: *** [loader.o] Error 1
serge@serge-laptop:~/Software/r5u87x$ 

```
It seems that I should have glib2 installed but I cannot find in Synaptic package manager.;(

---

### Post by AlanR8 on 2010-08-05
OK
Have had this Vaio VGN FZ21S for about three years now and it's had Ubuntu on for almost as long. The one thing that pissed me off was the web cam not working. The thread I pointed you to was about a third of the size back in the day....but I survived and the camera has worked over the last two/three releases.

You need the file I've attached. Decompress it. Navigate to the decompressed folder USING A TERMINAL WINDOW.

Then in terminal issue the following command:

> sudo make

You will be asked for your admin password. Allow the process to complete. Then:

> sudo make install and allow the process to finish. Reboot your machine, Load Skype and your camera should work!

---

### Post by Lavix on 2010-08-05
Thanks Alan for your reply, but the archive you sent is corrupted:
```


bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Child returned status 2
tar: Exiting with failure status due to previous errors

```

---

### Post by AlanR8 on 2010-08-05
Give this a go....


Go to:

[http://www.palmix.org/r5u870-en.html](http://www.palmix.org/r5u870-en.html)

to pick up the latest driver. At the time of writing it was r5u870_k2.6.30_i386.tar.bz2

Extract the to your home directory.

Then open a terminal and enter:

sudo make

sudo make install

---

### Post by Lavix on 2010-08-06
OK, I downloaded the driver r5u870-0.10.0.tgz and unpacked it to my home directory. Here is the result of make command;
```

serge@serge-laptop:~$ cd Software/r5u870-0.10.0
serge@serge-laptop:~/Software/r5u870-0.10.0$ sudo make
[sudo] password for serge: 
make -C /lib/modules/2.6.32-24-generic/build M=/home/serge/Software/r5u870-0.10.0 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/serge/Software/r5u870-0.10.0/r5u870_md.o
In file included from /home/serge/Software/r5u870-0.10.0/r5u870_md.c:55:
/home/serge/Software/r5u870-0.10.0/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
make[2]: *** [/home/serge/Software/r5u870-0.10.0/r5u870_md.o] Error 1
make[1]: *** [_module_/home/serge/Software/r5u870-0.10.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [all] Error 2
serge@serge-laptop:~/Software/r5u870-0.10.0$ 

```
I have an i;pression that it is not compatible with my actual configuration. Do you have any other ideas ?

---

### Post by AlanR8 on 2010-08-06
Which version of Ubuntu are you using?

---

### Post by Lavix on 2010-08-07
10.04 LTS - the Lucid Lynx, released in Aprin 2010.

---

### Post by P4man on 2010-08-07
Did you download the correct version (32 or 64 bit whichever you have installed?). If so, it may just not work with newest kernels. The project is dead and the last supported kernel is listed as 2.6.30.

---

### Post by Lavix on 2010-08-08
Here is what is offered for download:


[Wallpaper World Open source]("http://www.palmix.org/swos.html")
[Wallpaper Bed Vista]("http://www.palmix.org/sfondo-bvista.html")
[Wallpaper Debian Navel]("http://www.palmix.org/ombelico_deb.html")
[Logo Bad Vista]("http://www.palmix.org/download/bad-vista.png")
[Logo Debian]("http://www.palmix.org/download/openlogo-nd-100.png")
[File sources.list APT for amd64(64bit)]("http://www.palmix.org/download/sources.list")
[File sources.list APT (32bit)]("http://www.palmix.org/sources.list")
[File xorg.conf (Compiz-fusion ready) for FZ21]("http://www.palmix.org/download/xorg.conf")
[Monitors for Superkaramba]("http://www.palmix.org/widget-en.html")
[Guide "Linux on Sony Vaio" only italian (pdf)]("http://www.palmix.org/download/giuda-linux-vaio.pdf")
[Driver ALSA 1.0.15 in .deb format (kernel 2.6.23.1)]("http://www.palmix.org/alsa-en.html")
[URL="http://www.palmix.org/splashy-en.html"]Theme for Splashy 
[/URL][Truetype for Linux]("http://www.palmix.org/download/truetype.tar.bz2")
[Parted Magic 4.8]("http://www.palmix.org/pmdown-en.html")
[Auto-load Compiz-fusion script for KDE]("http://www.palmix.org/download/compiz.desktop")
[Webcam driver r5u870 for Vaio FE, AR, SZ, UX, FZ (some models)]("http://www.palmix.org/download/r5u870-0.10.0.tgz")
[Debian package of r5u870 webcam for i386 (Debian, Ubuntu, Sidux)]("http://www.palmix.org/download/r5u870_0.10.1_i386.deb")
[CISCO VPN Client for Linux + patch]("http://www.palmix.org/ciscovpn-en.html")
[Linux DVB firmware]("http://www.palmix.org/download/linux_dvb_firmware.zip")

So as you see there is the only one driver for the webcam. Most probably that the project is dead and there is no solution for the moment, unfortunately.

---

### Post by leandromartinez98 on 2010-09-25
I'm using lucid as well. My web cam Motion Eye was working until
recently, then after some upgrade the webacm is not recognized
anymore.

---

### Post by AlanR8 on 2010-09-28
When there's an upgrade to the kernel you have to reinstall the driver.

I am trying MAVERICK on the Sony at present and again have the problem that the camera's not recognised and the usual driver won't install.

---

### Post by AlanR8 on 2010-09-29
I just came across this in another thread. Since putting Maverick on the Sony Vaio VGN-FZ21S, the motion eye web cam was not working, again. I followed my own instructions, as above and the driver would not install.

I found this: 

> sudo add-apt-repository ppa:r5u87x-loader/ppa
sudo apt-get update
sudo apt-get install r5u87x
sudo /usr/share/r5u87x/r5u87x-download-firmware.sh

It just worked!

Run one command line at a time in terminal.

---

### Post by RDT1 on 2010-09-30
^ Cheers for the fix kernel 2.6.32-25 Generic on 10.04.1 LTS broke the previous fix and made it in compatible.

---

### Post by cajuuh on 2011-06-21
Seems to get worked here gota restart to see whats going on

---

