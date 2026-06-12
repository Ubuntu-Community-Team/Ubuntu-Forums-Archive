---
title: "creative webcam pd1001 driver ?"
date: 2006-01-17
forum: Installation &amp; Upgrades
---

### Post by Asad2k5 on 2006-01-17
I have a problem installing my creative webcam model pd1001 on breezy.

I have downloaded this driver "epcam-src-0.7.1.tar.gz" and installed it but dmesg shows this error "epcam: Unknown symbol remap_page_range"

lsusb shows:
Bus 002 Device 005: ID 041e:400d Creative Technology, Ltd WebCam PD1001

Any suggestion, I want to use amsn with this camera.

---

### Post by Loco_gr on 2006-04-18
I have the same WebCam and obviously the same problem.
Is there any suggestion or any solution???

---

### Post by BigMoby on 2006-05-03
Hi! I've modified the epcam's source code (epcam.c) and I've compiled the modules successfully and whitout error.
After #include <asm/semaphore.h> and #include "epcam.h" I've added this:

/*FABIO MAURO*/
static inline int remap_page_range(struct vm_area_struct *vma,
unsigned long uvaddr,
unsigned long paddr,
unsigned long size, pgprot_t prot)
{
return remap_pfn_range(vma, uvaddr, paddr >> PAGE_SHIFT, size, prot);
}
/*FABIO MAURO*/

I hope it's work also for you! 
Bye!

---

### Post by KoMpLoT on 2006-05-09
Hi BigMoby! I've managed to build and load the module with the changes you propose. But now when I'm using some software like camorama the image is mainly black. I say mainly because it shows "movement" on the top of the image.
I would like to know if you have it running and what did you use to make it work...
Thanks!

---

### Post by BigMoby on 2006-05-11
Hi KoMpLoT and all,
well, in my pc's configuration (Slackware and 2.6.16.12 kernel) the webcam working! But I used the same webcam in another pc and, so you have noticed, the PD1001 not properly work! ...NOT WORK!!! :) 
So I changed again some line of source code and I've recompiled the modules again. I plug-in the webcam, I #modprobe epcam... After I removed the /dev/v4l/video0 device with #rm /dev/v4l/video0 of course... and I made again a video device #mknod /dev/v4l/video0 c 81 0
The file of differences is:

######################################################
```


--- epcam.c	2006-05-10 19:26:00.000000000 +0200
+++ ./epcam-src-0.7.1/drivers/usb/epcam.c	2006-05-11 11:25:27.000000000 +0200
@@ -45,6 +45,15 @@
 
 static int video_nr=-1;
 
+static inline int remap_page_range(struct vm_area_struct *vma,
+unsigned long uvaddr,
+unsigned long paddr,
+unsigned long size, pgprot_t prot)
+{
+return remap_pfn_range(vma, uvaddr, paddr >> PAGE_SHIFT, size, prot);
+}
+
+
 static struct usb_device_id device_table [] = {
 	{ USB_DEVICE(0x03e8, 0x1005), driver_info: (unsigned long)"Endpoints EP800"	},/* Reference model */
 	{ USB_DEVICE(0x03e8, 0x1003), driver_info: (unsigned long)"Endpoints SE402"	},/* Reference model */
@@ -62,7 +71,7 @@
 
 MODULE_DEVICE_TABLE(usb, device_table);
 
-MODULE_AUTHOR("Jeroen Vreeken <pe1rxq@amsat.org>");
+MODULE_AUTHOR("Jeroen Vreeken <pe1rxq@amsat.org> and Modified by Fabio Mauro");
 MODULE_DESCRIPTION("EPcam USB Camera Driver");
 MODULE_LICENSE("GPL");
 MODULE_PARM(video_nr, "i");
@@ -221,23 +230,20 @@
 	if (epcam->brightness<4096)
 		epcam->brightness=4096;
 	
-//	epcam_set_feature(epcam, HV7131_REG_TITU, epcam->brightness>>8);
-//	epcam_set_feature(epcam, HV7131_REG_TITM, epcam->brightness&0xff);
-//	epcam_set_feature(epcam, HV7131_REG_TITL, 0);
-
-	/* the SE402 does this itself, don't bother it... */
-	if (epcam->camid!=0x402) {
-		epcam_sndctrl(0, epcam, VENDOR_REQ_IMAGE_INFO, 0, cp, sizeof(cp));
-		INT2QT(epcam->brightness>>5, cp+2);
-		size=QT2INT(cp);
-		if (size>40)
-			size=40;
-		epcam_sndctrl(1, epcam, VENDOR_REQ_IMAGE_INFO, 0, cp, size);
-	}
-
-//	info("TIT: %d", 256*256*epcam_get_feature(epcam, HV7131_REG_TITU)+
-//	    256*epcam_get_feature(epcam, HV7131_REG_TITM)+
-//	    epcam_get_feature(epcam, HV7131_REG_TITL));
+	epcam_set_feature(epcam, HV7131_REG_TITU, epcam->brightness>>8);
+	epcam_set_feature(epcam, HV7131_REG_TITM, epcam->brightness&0xff);
+	epcam_set_feature(epcam, HV7131_REG_TITL, 0);
+
+	epcam_sndctrl(0, epcam, VENDOR_REQ_IMAGE_INFO, 0, cp, sizeof(cp));
+	INT2QT(epcam->brightness>>5, cp+2);
+	size=QT2INT(cp);
+	if (size>40)
+		size=40;
+	epcam_sndctrl(1, epcam, VENDOR_REQ_IMAGE_INFO, 0, cp, size);
+
+	info("TIT: %d", 256*256*epcam_get_feature(epcam, HV7131_REG_TITU)+
+	    256*epcam_get_feature(epcam, HV7131_REG_TITM)+
+	    epcam_get_feature(epcam, HV7131_REG_TITL));
 
 	return 0;
 }
@@ -246,15 +252,13 @@
 {
 	unsigned char cp[40];
 	    	
-	if (epcam->camid!=0x402) {
-		epcam_sndctrl(0, epcam, VENDOR_REQ_IMAGE_INFO, 0, cp, sizeof(cp));
-		epcam->brightness=QT2INT(cp+2)<<5;
-	}
+//	epcam_sndctrl(0, epcam, VENDOR_REQ_IMAGE_INFO, 0, cp, sizeof(cp));
+//	epcam->brightness=QT2INT(cp+2)<<5;
 
-//	epcam->brightness=
-//	    epcam_get_feature(epcam, HV7131_REG_TITU)*256+
-//	    epcam_get_feature(epcam, HV7131_REG_TITM);
-//	epcam_get_feature(epcam, HV7131_REG_TITL);
+	epcam->brightness=
+	    epcam_get_feature(epcam, HV7131_REG_TITU)*256+
+	    epcam_get_feature(epcam, HV7131_REG_TITM);
+	epcam_get_feature(epcam, HV7131_REG_TITL);
 
 	return 0;
 }
@@ -1419,7 +1423,7 @@
 
 
 static struct usb_driver epcam_driver = {
-	.owner		= THIS_MODULE,
+	/*.owner		= THIS_MODULE,*/
 	.name		= "epcam",
 	.id_table	= device_table,
 	.probe		= epcam_probe,


```

#####################################################

Of course, this is an hack-version driver!
I hope it's work also for you! ;)
Fabio "Bigmoby" Mauro

---

### Post by BigMoby on 2006-05-13
I hope that my last post has been useful for someone...
But I suggest to add this line in your /etc/udev/rules.d/udev.rules
```

BUS=="usb", KERNEL="video[0-9]*", SYSFS{product}="Creative WebCam", SYSFS{manufacturer}=="CTL", NAME="v4l/video%n", SYMLINK="video%n"

```
and in your /etc/udev/scripts/make_extra_nodes.sh
```

if [ ! -r /dev/v4l/video0 ]; then
  mknod -m 660 /dev/v4l/video0 c 81 0
fi

```
...instead of #rm /dev/v4l/video0 and #mknod /dev/v4l/video0 c 81 0 .
Of course you must modify SYSFS{manufacturer} or SYSFS{product} for your system...for exemple when I plug my webcam in my usb port and I do #udevinfo -a -p /sys/devices/pci0000:00/0000:00:09.1/usb3/3-2/ (...becouse the port is the usb 3-2)
I've this output:
```

looking at class device '/sys/devices/pci0000:00/0000:00:09.1/usb3/3-2':
    SYSFS{bConfigurationValue}="1"
    SYSFS{bDeviceClass}="00"
    SYSFS{bDeviceProtocol}="00"
    SYSFS{bDeviceSubClass}="00"
    SYSFS{bMaxPacketSize0}="8"
    SYSFS{bMaxPower}="500mA"
    SYSFS{bNumConfigurations}="1"
    SYSFS{bNumInterfaces}=" 1"
    SYSFS{bcdDevice}="9717"
    SYSFS{bmAttributes}="80"
    SYSFS{devnum}="2"
    SYSFS{idProduct}="400d"
    SYSFS{idVendor}="041e"
    SYSFS{manufacturer}="CTL"
    SYSFS{maxchild}="0"
    SYSFS{product}="Creative WebCam"
    SYSFS{speed}="12"
    SYSFS{version}=" 1.00"

```
But I've noticed that if I turn-on my pc without the webcam and after the boot I plug-in it, the webcam work well...instead if the webcam I already plugged in I've to restart udev system with #udevstart ...so, I must work again to solve this problem... ;) 
BigMoby

---

### Post by InFoMaLuCo on 2006-06-27
I tried but I don't get to do it work. :cry: :cry: 

Please! Help me...[-o< [-o< 

May you write a "step-by-step"?

Thanks.

InFoMaLuCo

---

### Post by Loco_gr on 2006-07-02
[QUOTE=BigMoby]
But I've noticed that if I turn-on my pc without the webcam and after the boot I plug-in it, the webcam work well...instead if the webcam I already plugged in I've to restart udev system with #udevstart ...so, I must work again to solve this problem... ;) 
BigMoby[/QUOTE]

I hope to see you here soon with a complete solution for all us who are nothing more than simple users.

I have an extra problem. I have in my PC a PCTV Pro and that makes a conflict with the WebCam. Although I will try to make it work using your suggestions.

---

### Post by Loco_gr on 2006-07-03
I have tried to compile the drivers with the changes and i finally get those messages. 

```
thanasis@linux:~/test$ sudo make
   Building EPCAM driver for 2.5/2.6 kernel.
   PLEASE IGNORE THE "Overriding SUBDIRS" WARNING
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/thanasis/test modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-25-686'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-25-686'
```

Is that okay? What am I suppose to do after that?

** Okay I found it. 
```

thanasis@linux:~/test$ sudo make install
thanasis@linux:~/test$ sudo make clean

```
and then restart the pc.

Now I am in the same level with KoMpLoT. I am getting a black screen.
Can you please help me by telling me how can I use the file with the differences of source code ??

** I found it again :D

I made the changes in epcam.c and my Camera Worked !! But i didn't do the next steps cause there are no directories such as
```

/etc/udev/rules.d/udev.rules
/etc/udev/scripts/make_extra_nodes.sh

```

Shall I create new ones, empty and then fill them with your code ??? I have to mention here that I am using now Dapper Drake.
Is that neccesary cause my camera already works. What is a little bit annoying is that when I move the frames are changing really slow.
I tested my camera with Camorama.

Thanks

---

### Post by BigMoby on 2006-07-04
Ok Loco_gr, I'm happy you have a working webcam!...if you haven't /etc/udev/rules.d/udev.rules....mmm...maybe you haven't udev system in your pc...but it's strange! However I don't know Ubuntu (I've Slackware...)
The refresh is slow...yes it's true...but they're hack codes and very unstable!...it's better than nothing! no?!
p.s.: InFoMaLuCo, I've wrote a private message in your profile.
Bye...and I'm sorry for this delayed answer...butI've a new work and I'm very busy... ;) 
Fabio "BigMoby" Mauro

---

### Post by Loco_gr on 2006-07-04
[QUOTE=BigMoby]Ok Loco_gr, I'm happy you have a working webcam!...if you haven't /etc/udev/rules.d/udev.rules....mmm...maybe you haven't udev system in your pc...but it's strange! However I don't know Ubuntu (I've Slackware...)[/QUOTE]

Here is what I get when i do the ls command to the directory /etc/udev/rules.d :

```

thanasis@linux:~$ ll /etc/udev/rules.d/
total 140
-rw-r--r-- 1 root root   262 2006-04-28 19:21 00-init.rules
-rw-r--r-- 1 root root  2264 2006-04-28 19:21 20-names.rules
-rw-r--r-- 1 root root   190 2006-05-16 20:49 25-iftab.rules
-rw-r--r-- 1 root root  3048 2006-04-28 19:21 40-permissions.rules
-rw-r--r-- 1 root root 47992 2006-05-10 22:16 45-libgphoto2.rules
-rw-r--r-- 1 root root 28262 2006-04-06 10:12 45-libsane.rules
-rw-r--r-- 1 root root  1306 2006-05-12 14:45 60-symlinks.rules
-rw-r--r-- 1 root root  2585 2006-04-28 19:21 65-persistent-disk.rules
-rw-r--r-- 1 root root   385 2006-04-28 19:21 80-programs.rules
-rw-r--r-- 1 root root   171 2006-04-03 19:33 85-alsa.rules
-rw-r--r-- 1 root root   208 2006-04-21 12:12 85-hal.rules
-rw-r--r-- 1 root root    81 2006-01-04 13:13 85-hdparm.rules
-rw-r--r-- 1 root root   126 2006-05-16 04:43 85-hwclock.rules
-rw-r--r-- 1 root root   657 2006-01-30 15:40 85-ifupdown.rules
-rw-r--r-- 1 root root   937 2006-03-23 22:40 85-pcmcia.rules
-rw-r--r-- 1 root root    82 2006-04-21 12:12 90-hal.rules
-rw-r--r-- 1 root root  2534 2006-04-28 19:21 90-modprobe.rules
-rw-r--r-- 1 root root    75 2006-04-28 19:21 99-udevmonitor.rules
thanasis@linux:~$

```

Any suggestions ???

[QUOTE=BigMoby]
The refresh is slow...yes it's true...but they're hack codes and very unstable!...it's better than nothing! no?!
[/QUOTE]

You are kidding right? It's perfect even that way and thanks in andvance for you huge help. I hope that you will find some free time and develop a little bit more those drivers !!!

Thanks again for your help.

Loco_gr

---

### Post by Loco_gr on 2006-07-08
I decided to write a short HOW-TO for all those who need help with the PD1001 Creative Camera. 

Many thanks to BigMoby for his hack to the drivers.

[LIST=1]
[*]Download the source files that are included in epcam-src-ubuntu-0.7.1.tar.gz
[*]Open a terminal
[*]Go the directory where you download epcam-src-ubuntu-0.7.1.tar.gz
[*]Copy-Paste in your terminal each of the following lines exactly as it is :
[/LIST]

```

tar xfvz epcam-src-ubuntu-0.7.1.tar.gz
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r`
sudo make
sudo make install
sudo make clean

```

_Warning the drivers are still having some bugs!_

---

### Post by BigMoby on 2006-07-10
Yeah!!! It's a good work, Loco_gr!!! Great! ;) 
Also you should add the udev's fix...but it's work fine too! Anyway...asking to your question about udev in ubuntu's distro, sorry but (at this time) I've no solution to solve your problem becouse my distro is a bit different...however, I'll see for you when I'll have two free minutes! :rolleyes: 
Fabio "BigMoby" Mauro

---

### Post by kingmonkey on 2006-07-29
Wow, I have picture with this webcam on linux for the first time ever! (yeah sure the colour is wrong and the refresh rate is 0.25 or somehting but...hey) Amazing! Have been trying to get it to work for 4 years!!!


ls -a /etc/udev/rules.d/
.                     45-libsane.rules          85-hdparm.rules
..                    45-logitechmouse.rules    85-hwclock.rules
00-init.rules         60-symlinks.rules         85-ifupdown.rules
20-names.rules        65-persistent-disk.rules  85-pcmcia.rules
25-iftab.rules        80-programs.rules         90-hal.rules
40-permissions.rules  85-alsa.rules             90-modprobe.rules
45-libgphoto2.rules   85-hal.rules              99-udevmonitor.rules

---

### Post by KoMpLoT on 2006-09-25
Hi! I'm still trying to get this working.
I've managed to compile the driver but since I have kernel 2.6.17-8, there's a line that won't work. After searching for a while I found that this would do the trick:
You have to change the line:

```
MODULE_PARM(video_nr, "i");
```

for this:

```
#if LINUX_VERSION_CODE > KERNEL_VERSION(2,5,0)
module_param(video_nr, int, 000);
#else
MODULE_PARM(video_nr, "i");
#endif
```

then it compiles.

Now my problem is that the webcam keeps black. I've added all the udev stuff mentioned before; Ubuntu detects the webcam but when I launch some application to use it; it all turns slow and there's still no image displayed.

Any clue?
Thanks!

---

### Post by proxess on 2006-11-02
i get the following when I make:

```
proxess@PC-PrXss:~/Desktop/epcam$ make
   Building EPCAM driver for 2.5/2.6 kernel.
   PLEASE IGNORE THE "Overriding SUBDIRS" WARNING
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/proxess/Desktop/epcam modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/proxess/Desktop/epcam/drivers/usb/epcam.o
/home/proxess/Desktop/epcam/drivers/usb/epcam.c:81: error: expected ')' before string constant
/home/proxess/Desktop/epcam/drivers/usb/epcam.c: In function 'epcam_recv_pict':
/home/proxess/Desktop/epcam/drivers/usb/epcam.c:257: warning: unused variable 'cp'
/home/proxess/Desktop/epcam/drivers/usb/epcam.c: In function 'epcam_start_stream':
/home/proxess/Desktop/epcam/drivers/usb/epcam.c:465: warning: unused variable 'endpoint'
/home/proxess/Desktop/epcam/drivers/usb/epcam.c:464: warning: unused variable 'interface'
/home/proxess/Desktop/epcam/drivers/usb/epcam.c: In function 'epcam_read':
/home/proxess/Desktop/epcam/drivers/usb/epcam.c:1209: warning: ignoring return value of 'copy_to_user', declared with attribute warn_unused_result
make[2]: *** [/home/proxess/Desktop/epcam/drivers/usb/epcam.o] Error 1
make[1]: *** [_module_/home/proxess/Desktop/epcam] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [default] Error 2
proxess@PC-PrXss:~/Desktop/epcam$ 

```

any solution to this?!

i use edgy.

---

### Post by Bugaj on 2006-11-22
Same configuration and the same problem ](*,) 
Regards

---

### Post by Patskumaster on 2006-11-26
Today I succesfully compiled and loading epcam drivers, but I don't still get photo. What next?

---

### Post by ekx27 on 2006-12-26
I have fixed the driver to compile under Ubuntu Edgy Eft.

I have a image with Camorama ([http://camorama.fixedgear.org/]("http://camorama.fixedgear.org/")), but I'm not enough qualified to modify it to get a better image (wrong colors and about 0.5 FPS...)

If someone has got time to improve it... :-D 

To install it follow this :

   1. Download the source files that are included in epcam-src-ubuntu-0.7.2.tar.gz
   2. Open a terminal
   3. Go the directory where you download epcam-src-ubuntu-0.7.2.tar.gz
   4. Copy-Paste in your terminal each of the following lines exactly as it is :

> tar xfvz epcam-src-ubuntu-0.7.2.tar.gz
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r`
sudo make
sudo make install
sudo make clean

Here is the file (thanks to everyone who imrove it !) :

---

### Post by InFoMaLuCo on 2007-01-13
I don't get to do it works. Black Screen, yet. :( :(

---

### Post by ogjelland on 2007-01-13
The epcam-src-ubuntu-0.7.2 does the trick! For the 2.6.18 kernel onwards, check out:

[INDENT][http://article.gmane.org/gmane.linux.drivers.quickcam.devel/1136]("http://article.gmane.org/gmane.linux.drivers.quickcam.devel/1136")[/INDENT]

where a little patch is posted by Jose Antonio S. A. It goes something like this:
```
diff -Naur drivers.orig/usb/epcam.h drivers/usb/epcam.h
--- drivers.orig/usb/epcam.h    2004-12-04 04:05:16.000000000 +0000
+++ drivers/usb/epcam.h 2007-01-14 00:37:23.694871104 +0000
@@ -3,6 +3,9 @@
 
 #include <asm/uaccess.h>
 #include <linux/videodev.h>
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,18)
+#include <media/v4l2-common.h>
+#endif
 #include <linux/smp_lock.h>
 
 #ifdef epcam_DEBUG
```
**Nice** colors, by the way. With good, old xawtv on Debian Testing (etch) running a stock kernel 2.6.18-3-486.

---

### Post by ekx27 on 2007-01-21
See the last message for the lastest version...

---

### Post by proxess on 2007-03-10
anyone working on this for kernels 2.6.20? (feisty)

---

### Post by ekx27 on 2007-03-11
Did you try the driver 0.7.3 ?

If yes, is there any errors ? Post them.

Remember that this driver is still in alpha release... don't expect much from it...

---

### Post by proxess on 2007-03-11
well i got them to work, what i had to do was:

go into /usr/src/`uname -r`/includes/linux/
and make a link of autoconf.h and name it config.h ... so im guessing that in the next src for epcam, you use autoconf.h or check for one or the other.

---

### Post by dvm1982 on 2007-05-09
I managed to connect my webcam with your instructions. It recognizes it but when I open camorama or amsn, it crashes after a while without seeing any image. Using feisty fawn with the 2.6.20 kernel. May that be the problem? Making this camera work is IMPOSSIBLE after months and months of trying. It should work with a patch on the stv680 driver i've seen in many pages, but I can't do that too.

---

### Post by ekx27 on 2007-05-09
Well, there are 2 version of the Creative Webcam PD1001 (open the webcam to be sure about which one it is) :

The one with the OV518 chipset :
You are lucky, your webcam will work, just install the ov511 driver from synaptic (may be already installed)

The other one with the EP800 chipset
Use the driver above, but he not working very well. For me, I can only see a picture at about 0.5 fps with wrong colors...
We have to wait until someone continue to develop this driver...

The patch of the stv680 driver is for the Creative Webcam Go Mini PD00070, we are talking here about the PD1001.
I think it is not going to work.

---

### Post by dvm1982 on 2007-05-09
Lol I opened it! never thought how it was inside. Ok, mine is EP800, but not working as I said. Let's wait for an improve of the driver... It would be easier buying another model, I think :(

---

### Post by ekx27 on 2007-05-10
I found documentation on the endpoints Website ! (the website is down, but I used the [WayBack Machine]("http://web.archive.org/web/20021227043220/mirror23.net/EndPoints.com/Products/EP_800/ep_800.html"))

The driver work for me with Ubuntu 7.04 on a 2.6.20 kernel, but the FPS is about 0.5 and the image has wrong colors...

To install it follow this :

   1. Download the source files that are included in epcam-src-0.7.3.tar.gz
   2. Open a terminal
   3. Go the directory where you download epcam-src-ubuntu-0.7.3.tar.gz
   4. Copy-Paste in your terminal each of the following lines exactly as it is :

> sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r`
tar xfvz epcam-src-0.7.3.tar.gz
cd epcam-src-0.7.3
sudo make
sudo make install
sudo modprobe epcam

If someone has got time to improve it... do not hesitate :D 

This is the camera :
[IMG]http://www.aiyamicro.com/pc-parts-peripherals/pics-computer-parts/CRE-PD1001.jpg[/IMG]

Remember, there are 2 version of the Creative Webcam PD1001 (open the webcam to be sure about which one it is) :

* Creative Webcam PD1001 with OV518 chipset :
You are lucky, your webcam will work, just install the ov511 driver from synaptic (may be already installed)

* Creative Webcam PD1001 with EP800 chipset
Use the epcam driver, but he not working very well. We have to wait until someone continue to develop this driver...
EP800 documentation is available at : [http://www.endpoints.com](http://www.endpoints.com) (seems to be down... but use the [WayBack Machine !]("http://web.archive.org/web/20021227043220/mirror23.net/EndPoints.com/Products/EP_800/ep_800.html"))

Here is the epcam driver (as a module) with the documentation included \\:D/  :

---

### Post by Zowie on 2007-06-05
Hi guys.
Im new to ubuntu. 
Just installed version 7.04 (Feisty Fawn) and tried to install my creative webcam (pd1001). my kernel version is 2.6.20-16-generic.

Regarding this last message, and having tried to install the drivers first, I came across a problem compiling the module. I solved it changing the drivers/usb/epcam.c file. 
Where it says "#include <linux/config.h>" I had to change it to "#include <linux/configfs.h>"

Now it compiles in Feisty and the camera is working. Thanks for the "how-to", by the way.
tried it in camorama but doesn't look very good (slow, etc. etc.) but hey, i got video at least ;)
Ill try some other apps also.

Hope this note helps someone using Feisty

---

### Post by reisyboy on 2007-06-06
Will just say you also need to make sure you have the linux headers in right

sudo apt-get install linux-headers-2.6.20-16-generic

---

### Post by proxess on 2007-07-14
> **Zowie said:**
> Regarding this last message, and having tried to install the drivers first, I came across a problem compiling the module. I solved it changing the drivers/usb/epcam.c file. 
Where it says "#include <linux/config.h>" I had to change it to "#include <linux/configfs.h>"

thats funny, i changed "#include <linux/config.h>" to "#include <linux/autoconf.h>" and it worked. I done the same thing to get my xpad360 drivers working. Is configfs the same as autoconf? i dont think it is tho i've never checked.

Hmmm can someone tell me the device of the webcam, i cant find anything like v4l/video0 or /dev/video or anything of the kind

---

### Post by ekx27 on 2007-07-14
For me it is /dev/video0 :popcorn:

---

### Post by proxess on 2007-07-30
anyone still developing these drivers? they are just too damn slow...

---

### Post by ekx27 on 2007-07-31
I think you should ask this guy [http://mxhaard.free.fr/index.html]("http://mxhaard.free.fr/index.html") if he could continue the development of theses drivers... and include it to the 244 drivers he developed.

---

### Post by proxess on 2007-11-10
Has anyone contacted whoever this guy is?

---

### Post by ekx27 on 2007-11-11
> **proxess said:**
> Has anyone contacted whoever this guy is?

Me not, but if nobody has done it, I will

He is french, like me :)

---

### Post by superid on 2007-11-15
Any news on getting the PD1001 to work under Gutsy?
Or just follow the same procedure, using epcam 0.7.3?

Thanks in advance!

---

### Post by ekx27 on 2007-11-15
> **superid said:**
> Any news on getting the PD1001 to work under Gutsy?
Or just follow the same procedure, using epcam 0.7.3?

Thanks in advance!

Well, just try :) :

[Here is how to install the epcam driver for the PD1001 webcam]("http://ubuntuforums.org/showpost.php?p=2626919&postcount=29")

If there is any errors, show them on the forum.

---

### Post by superid on 2007-11-20
Thanks for the reply, I'd lost track of this thread.

I tried the procedure you provided and encountered an error in the 'make' process.
There is no linux/config.h header file on my system.

This is the exact procedure I tried before, and last time I modified the source to include configfs.h instead, no luck.
What should I change the source to (or what header file should I link to)?

Thanks in advance,
 Leo

PS: Here's a list of files in my /usr/src/linux-headers-2.6.22-14-generic/include/linux directory:
[http://pastebin.com/m73d68181](http://pastebin.com/m73d68181)

---

### Post by ekx27 on 2007-11-20
> **superid said:**
> 
I tried the procedure you provided and encountered an error in the 'make' process.
There is no linux/config.h header file on my system.


Just comment the line #include <linux/config.h> in epcam-src-0.7.3/drivers/usb/epcam.c and it compile !

```
/*#include <linux/config.h>*/
```

---

### Post by superid on 2007-11-20
Thanks, I've now compiled/installed the epcam driver.

A video device has been created (/dev/video0/), but it seems to be inaccessible.
Camorama says "Could not connect to video device (/dev/video0). Please check connection."

'lsusb' detects the device on the USB hub:
Bus 002 Device 003: ID 041e:400d Creative Technology, Ltd WebCam PD1001

Any ideas? Thanks for the help so far.

---

### Post by ekx27 on 2007-11-20
Try this in root : ```
modprobe epcam
```
This load the module

Then test if the module is properly loaded : ```
lsmod | grep "epcam"
```

You should see : ```
epcam                  20512  0 
videodev               26656  1 epcam
usbcore               125096  8 epcam,pl2303,usbserial,usbhid,usb_storage,ehci_hcd,uhci_hcd
```

---

### Post by superid on 2007-11-20
Output of lsmod:
```

epcam                  25984  0 
videodev               31360  1 epcam
usbcore               161584  5 epcam,usbhid,ehci_hcd,ohci_hcd

```

I'll try another system restart.

---

### Post by ekx27 on 2007-11-20
The fact is that I'm not under Ubuntu anymore, I've got a Debian Lenny (Testing)...

```
Linux adb 2.6.22-2-686 #1 SMP Fri Aug 31 00:24:01 UTC 2007 i686 GNU/Linux
```

---

### Post by superid on 2007-11-20
Thanks for the help anyways, I'll post if I get it working.

Meanwhile, if anyone else has any ideas, please share them. :)

---

### Post by superid on 2007-11-20
Problem solved by adding user to 'video' group, logging out, logging in again.

For anyone having similar problems, drop to a terminal and type:
```
sudo adduser <user> video
```
Where <user> is the username to be added.

Camorama is fine, but Skype still doesn't seem to recognize the camera.

---

### Post by ekx27 on 2007-11-21
> **superid said:**
> Camorama is fine

Really ? Is the quality good ? Can you show us a picture ?

I've got wrong colors and 0.5 fps...

---

### Post by superid on 2007-11-21
Sorry, I meant it's working, which is a big step in my case.
Colors are indeed wrong, with a blue-wash tint that is unresponsive to Hue/Color adjustments.
I do however have it running at 3.50fps. Check out the attached screenshot.

Still nothing in Skype though. :(

---

### Post by slepax on 2008-02-13
This thread helped me quite a lot so I might as well add some of my experience.

I have Ubuntu 7.10 with 2.6.22-14-generic. I managed to get epcam 7.3 installed.

With Camorama, I have the same blue-wash everyone were talking about, but with webcam_server (v0.50) I get the right colours and everything is working fine.

---

### Post by ekx27 on 2008-02-13
> **slepax said:**
> This thread helped me quite a lot so I might as well add some of my experience.

I have Ubuntu 7.10 with 2.6.22-14-generic. I managed to get epcam 7.3 installed.

With Camorama, I have the same blue-wash everyone were talking about, but with webcam_server (v0.50) I get the right colours and everything is working fine.

WOW ! What a surprize !! It works !

Thank you very much ! My webcam will not be useless anymore :)

---

### Post by slepax on 2008-02-14
Just one more thing I might be able to add to this thread. 

I believe camorama has a problem with RGB conversion, webcam-server has an option for converting RGB to BGR (-x), and when used, you get the same blue-wash as with camorama.

---

### Post by markaur on 2008-03-14
I run Fedore Core 8 and have been able to compile epcam driver from epcam-src-0.7.3 with minor tweeks(replaced CFLAGS with EXTRA_CFLAGS  in Makefile as suggested by make utility, and outcommented /*#include <config.h>*/  inside epcam.h.I also had to put comments around  .hardware variable initialization for video_device data structure inside epcam.c, since compiler gave me error complaining about this variable....).
Driver loads fine with insmod epcam.ko and dumps a lot of debugging information to syslog (can see them with dmesg | grep epcam from command line).
I haven't tried to use any appliaction thus far, but I've heard that webcam_server works solid.
I've noticed error when trying to remove driver with command rmmod epcam.
Anyone had anything similar on Ubuntu?
Thanks.

---

### Post by markaur on 2008-03-21
I've finally found chip specifications for Hyundai hv7121 chip used by this camera.
So far I've made some progress with the driver regarding picture quality and will post my code once I'm done.
This source 0.7.3 I've found on this forum is just alpha quality code but is good starting point and needs some improvements so people can use it with applications such as ekiga, amsn etc....
Please stay tuned, new version should be there, hopefully soon.
Thanks.

---

### Post by markaur on 2008-03-24
I've made some significant progress with this driver and will post my results very soon.It now supports some applications using V4L2 API such as amsn (which in fact supports both V4L and V4L2).
I've found out that skype 2.0 only supports V4L2 and I'm currently working on making this driver work with skype too.

---

### Post by markaur on 2008-04-01
I've attached capture from my webcam.
You'll notice that colours seem to be nice.There is more to be done, so I can control hue,saturation,brightness.

---

### Post by markaur on 2008-04-07
I've attached driver source code for Creative PD1001 with the changes that I've made.
It should work much better now with frame rates going to full 30 fps with small resolution and reduced brightness.I've tested it with ekiga,camorama,mplayer,vlc,amsn and it should work with all open source applications supporting v4l standard.It doesn't work with skype.
I'm using Fedora 8, kernel 2.6.24.3 , but it should work on other distributions too.
In order to build the driver you'll need development packages installed.

tar zxvf epcam-src-0.8.1.tar.gz
cd epcam-src-0.8.1
make
sudo make install
sudo modprobe epcam

---

### Post by gusman21 on 2008-04-08
any ideas?

ubuntu gutsy
2.6.22-14-generic
I am running beta drivers for hauppauge HVR-1600
current v4l

make:
```
gus@ubuntu-desktop:~/Desktop/epcam-src-0.8.1$ make
   Building EPCAM driver for 2.5/2.6 kernel.
   PLEASE IGNORE THE "Overriding SUBDIRS" WARNING
   Remember: you must have read/write access to your kernel source tree.
#make -C /lib/modules/`uname -r`/build SUBDIRS=/home/gus/Desktop/epcam-src-0.8.1 modules
make -C /lib/modules/`uname -r`/build  M=/home/gus/Desktop/epcam-src-0.8.1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.o
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c: In function &#8216;show_model&#8217;:
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:253: warning: initialization from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c: In function &#8216;show_in_use&#8217;:
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:254: warning: initialization from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c: In function &#8216;show_streaming&#8217;:
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:255: warning: initialization from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c: In function &#8216;show_palette&#8217;:
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:256: warning: initialization from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c: In function &#8216;show_frames_total&#8217;:
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:257: warning: initialization from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c: In function &#8216;show_frames_read&#8217;:
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:258: warning: initialization from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c: In function &#8216;show_packets_dropped&#8217;:
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:259: warning: initialization from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c: In function &#8216;epcam_create_sysfs_files&#8217;:
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:265: warning: passing argument 2 of &#8216;video_device_create_file&#8217; from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:267: warning: passing argument 2 of &#8216;video_device_create_file&#8217; from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:269: warning: passing argument 2 of &#8216;video_device_create_file&#8217; from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:271: warning: passing argument 2 of &#8216;video_device_create_file&#8217; from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:273: warning: passing argument 2 of &#8216;video_device_create_file&#8217; from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:275: warning: passing argument 2 of &#8216;video_device_create_file&#8217; from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:277: warning: passing argument 2 of &#8216;video_device_create_file&#8217; from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:282: warning: passing argument 2 of &#8216;video_device_remove_file&#8217; from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:284: warning: passing argument 2 of &#8216;video_device_remove_file&#8217; from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:286: warning: passing argument 2 of &#8216;video_device_remove_file&#8217; from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:288: warning: passing argument 2 of &#8216;video_device_remove_file&#8217; from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:290: warning: passing argument 2 of &#8216;video_device_remove_file&#8217; from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:292: warning: passing argument 2 of &#8216;video_device_remove_file&#8217; from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:294: warning: passing argument 2 of &#8216;video_device_remove_file&#8217; from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c: In function &#8216;epcam_remove_sysfs_files&#8217;:
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:301: warning: passing argument 2 of &#8216;video_device_remove_file&#8217; from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:302: warning: passing argument 2 of &#8216;video_device_remove_file&#8217; from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:303: warning: passing argument 2 of &#8216;video_device_remove_file&#8217; from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:304: warning: passing argument 2 of &#8216;video_device_remove_file&#8217; from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:305: warning: passing argument 2 of &#8216;video_device_remove_file&#8217; from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:306: warning: passing argument 2 of &#8216;video_device_remove_file&#8217; from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:307: warning: passing argument 2 of &#8216;video_device_remove_file&#8217; from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c: In function &#8216;epcam_start_stream&#8217;:
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:822: warning: assignment from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c: In function &#8216;decode_eplite&#8217;:
/home/gus/Desktop/epcam-src-0.8.1/drivers/usb/epcam.c:1096: warning: unused variable &#8216;i&#8217;
  LD [M]  /home/gus/Desktop/epcam-src-0.8.1/epcam.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/gus/Desktop/epcam-src-0.8.1/epcam.mod.o
  LD [M]  /home/gus/Desktop/epcam-src-0.8.1/epcam.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'

```

dmesg:
```

[40981.473441] epcam: disagrees about version of symbol video_devdata
[40981.473447] epcam: Unknown symbol video_devdata
[40981.473620] epcam: disagrees about version of symbol video_unregister_device
[40981.473624] epcam: Unknown symbol video_unregister_device
[40981.473689] epcam: disagrees about version of symbol video_register_device
[40981.473691] epcam: Unknown symbol video_register_device
[40981.473797] epcam: disagrees about version of symbol video_device_release
[40981.473799] epcam: Unknown symbol video_device_release

```

---

### Post by markaur on 2008-04-08
They've made changes to sysfs support for v4l and v4l2 devices after first kernel release 2.6.23.
I've made modifications in driver version 0.8.2, so driver should work with older kernels.
I've been able to compile/install and test it on gutsy live CD.
Driver works fine with amsn,ekiga,camorama (little glitch when changing frame size in camorama, but I'm still not convinced if it is actually driver's problem).You'll have to use color correction effect because camorama doesn't initially support RGB24 format(but BGR...).

---

### Post by gusman21 on 2008-04-09
tried epcam-src-0.8.2.

make and make install:
```

gus@ubuntu-desktop:~/Desktop/epcam-src-0.8.2$ make
   Building EPCAM driver for 2.5/2.6 kernel.
   PLEASE IGNORE THE "Overriding SUBDIRS" WARNING
   Remember: you must have read/write access to your kernel source tree.
#make -C /lib/modules/`uname -r`/build SUBDIRS=/home/gus/Desktop/epcam-src-0.8.2 modules
make -C /lib/modules/`uname -r`/build  M=/home/gus/Desktop/epcam-src-0.8.2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/gus/Desktop/epcam-src-0.8.2/drivers/usb/epcam.o
/home/gus/Desktop/epcam-src-0.8.2/drivers/usb/epcam.c: In function ‘epcam_start_stream’:
/home/gus/Desktop/epcam-src-0.8.2/drivers/usb/epcam.c:885: warning: assignment from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.2/drivers/usb/epcam.c: In function ‘decode_eplite’:
/home/gus/Desktop/epcam-src-0.8.2/drivers/usb/epcam.c:1159: warning: unused variable ‘i’
  LD [M]  /home/gus/Desktop/epcam-src-0.8.2/epcam.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/gus/Desktop/epcam-src-0.8.2/epcam.mod.o
  LD [M]  /home/gus/Desktop/epcam-src-0.8.2/epcam.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
gus@ubuntu-desktop:~/Desktop/epcam-src-0.8.2$ sudo make install
install -c -m 0644 epcam.ko /lib/modules/`uname -r`/kernel/drivers/media/video
/sbin/depmod -ae
gus@ubuntu-desktop:~/Desktop/epcam-src-0.8.2$ sudo modprobe epcam
FATAL: Error inserting epcam (/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/epcam.ko): Unknown symbol in module, or unknown parameter (see dmesg)
gus@ubuntu-desktop:~/Desktop/epcam-src-0.8.2$ 

```

dmesg:
```

[ 1604.058248] epcam: disagrees about version of symbol video_devdata
[ 1604.058254] epcam: Unknown symbol video_devdata
[ 1604.058426] epcam: disagrees about version of symbol video_unregister_device
[ 1604.058429] epcam: Unknown symbol video_unregister_device
[ 1604.058494] epcam: disagrees about version of symbol video_register_device
[ 1604.058499] epcam: Unknown symbol video_register_device
[ 1604.058607] epcam: disagrees about version of symbol video_device_release
[ 1604.058611] epcam: Unknown symbol video_device_release

```

Thoughts?

---

### Post by markaur on 2008-04-09
> **gusman21 said:**
> tried epcam-src-0.8.2.

make and make install:
```

gus@ubuntu-desktop:~/Desktop/epcam-src-0.8.2$ make
   Building EPCAM driver for 2.5/2.6 kernel.
   PLEASE IGNORE THE "Overriding SUBDIRS" WARNING
   Remember: you must have read/write access to your kernel source tree.
#make -C /lib/modules/`uname -r`/build SUBDIRS=/home/gus/Desktop/epcam-src-0.8.2 modules
make -C /lib/modules/`uname -r`/build  M=/home/gus/Desktop/epcam-src-0.8.2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/gus/Desktop/epcam-src-0.8.2/drivers/usb/epcam.o
/home/gus/Desktop/epcam-src-0.8.2/drivers/usb/epcam.c: In function ‘epcam_start_stream’:
/home/gus/Desktop/epcam-src-0.8.2/drivers/usb/epcam.c:885: warning: assignment from incompatible pointer type
/home/gus/Desktop/epcam-src-0.8.2/drivers/usb/epcam.c: In function ‘decode_eplite’:
/home/gus/Desktop/epcam-src-0.8.2/drivers/usb/epcam.c:1159: warning: unused variable ‘i’
  LD [M]  /home/gus/Desktop/epcam-src-0.8.2/epcam.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/gus/Desktop/epcam-src-0.8.2/epcam.mod.o
  LD [M]  /home/gus/Desktop/epcam-src-0.8.2/epcam.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
gus@ubuntu-desktop:~/Desktop/epcam-src-0.8.2$ sudo make install
install -c -m 0644 epcam.ko /lib/modules/`uname -r`/kernel/drivers/media/video
/sbin/depmod -ae
gus@ubuntu-desktop:~/Desktop/epcam-src-0.8.2$ sudo modprobe epcam
FATAL: Error inserting epcam (/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/epcam.ko): Unknown symbol in module, or unknown parameter (see dmesg)
gus@ubuntu-desktop:~/Desktop/epcam-src-0.8.2$ 

```

dmesg:
```

[ 1604.058248] epcam: disagrees about version of symbol video_devdata
[ 1604.058254] epcam: Unknown symbol video_devdata
[ 1604.058426] epcam: disagrees about version of symbol video_unregister_device
[ 1604.058429] epcam: Unknown symbol video_unregister_device
[ 1604.058494] epcam: disagrees about version of symbol video_register_device
[ 1604.058499] epcam: Unknown symbol video_register_device
[ 1604.058607] epcam: disagrees about version of symbol video_device_release
[ 1604.058611] epcam: Unknown symbol video_device_release

```

Thoughts?

If you execute following command: modinfo epcam.ko you'll see among other information following line :

depends:               videodev,v4l2-common,compat_ioctl32

All those unresolved symbols that you're getting when loading epcam driver are supposed to be resolved within videodev.ko module.
So, I suspect that the version of videodev.ko you have has been changed by your DVB driver installation.
There are few people experiencing exactly the same problem with other webcam drivers.
One of them (louis l'ancien) has found solution.Look for the information on the following page:

[https://answers.launchpad.net/ubuntu/+question/21889](https://answers.launchpad.net/ubuntu/+question/21889)

I hope it works out for you.
I didn't have this problem on gutsy live CD.I suspect that your DVB driver installation has modified original videodev.ko module.

---

### Post by markaur on 2008-04-22
> **markaur said:**
> I've attached driver source code for Creative PD1001 with the changes that I've made.
It should work much better now with frame rates going to full 30 fps with small resolution and reduced brightness.I've tested it with ekiga,camorama,mplayer,vlc,amsn and it should work with all open source applications supporting v4l standard.It doesn't work with skype.
I'm using Fedora 8, kernel 2.6.24.3 , but it should work on other distributions too.
In order to build the driver you'll need development packages installed.

tar zxvf epcam-src-0.8.1.tar.gz
cd epcam-src-0.8.1
make
sudo make install
sudo modprobe epcam

Just to clarify why it's not working with skype.
Skype is supporting both V4L and V4L2 standards but it is supporting only YUV420P,YUYV and UYVY formats while driver is supporting RGB24.
I think it's the application that should be doing format conversions not the  driver.

---

### Post by bit0 on 2008-04-25
Just works! 
(Debian-Sid AMD64)
Thanks!

---

### Post by gusman21 on 2008-04-26
> **markaur said:**
> I
All those unresolved symbols that you're getting when loading epcam driver are supposed to be resolved within videodev.ko module.
So, I suspect that the version of videodev.ko you have has been changed by your DVB driver installation.


output of modinfo videodev.ko:
```

modinfo: could not find module videodev.ko

```

thanks though.

---

### Post by panora200 on 2008-05-07
Greetings to all. I'm very pleased to find someone still caring about the EP800 chipset. 

I've recently found this thread, and wanted to group all efforts into epcam linux driver. I've registered a new sourceforge.net project to host everything related to this, but I can't afford to give any kind of support, at least for a few next weeks. 

I invite you all to share your knowledge to the SF.net forums and bug trackers, and specially to the new developers to be bound to it.

The project is hosted at:
[http://sourceforge.net/projects/epcam](http://sourceforge.net/projects/epcam)

I still didn't have a carefull look at it, but it has already an SVN with all releases I found in this thread.

I'll be myself testing the driver and tweaking it as I can.
Best wishes to you all.
-NT

---

### Post by seuaniu on 2008-05-12
This compiled fine for me on Hardy this afternoon.  Camorama, for whatever reason, shows a very blue-tinted picture and ekiga shows very red.  Go figure.  Thanks much for improving on the driver.  This webcam has been sitting in a box for about 3 years.

---

### Post by markaur on 2008-06-10
> **seuaniu said:**
> This compiled fine for me on Hardy this afternoon.  Camorama, for whatever reason, shows a very blue-tinted picture and ekiga shows very red.  Go figure.  Thanks much for improving on the driver.  This webcam has been sitting in a box for about 3 years.

You are welcome.
You'll have to use color correction effect in Camorama because it doesn't handle RGB24 palette properly (it applies BGR32 which swaps blue and red of RGB24)
As far as Ekiga is concerned you should be able to adjust color settings ....
Thanks.

---

### Post by pittle on 2008-07-04
I'm trying to compile this on Ubuntu Dapper.

```
$ uname -sr
Linux 2.6.15-52-server
```

Downloaded [epcam-src-0.8.3.tar.gz from sourceforge.net]("http://kent.dl.sourceforge.net/sourceforge/epcam/epcam-src-0.8.3.tar.gz").

Also note ```
$ lsusb | grep PD1001
Bus 002 Device 002: ID 041e:400d Creative Technology, Ltd WebCam PD1001
```

Successfully extracted contents of the tarball:

```
~$ mkdir epcam
~$ mv epcam-src-0.8.3.tar.gz epcam
~$ cd epcam/
~/epcam$ tar xfz epcam-src-0.8.3.tar.gz 
~/epcam$ ls -AR
.:
CHANGELOG  drivers  epcam-src-0.8.3.tar.gz  Makefile

./drivers:
usb

./drivers/usb:
epcam.c  epcam.h
```

and tried to "make it":

```
~/epcam$ make
   Building EPCAM driver for 2.5/2.6 kernel.
   PLEASE IGNORE THE "Overriding SUBDIRS" WARNING
   Remember: you must have read/write access to your kernel source tree.
#make -C /lib/modules/`uname -r`/build SUBDIRS=/home/exalted/epcam modules
make -C /lib/modules/`uname -r`/build  M=/home/exalted/epcam modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-52-server'
  CC [M]  /home/exalted/epcam/drivers/usb/epcam.o
In file included from /home/exalted/epcam/drivers/usb/epcam.c:54:
/home/exalted/epcam/drivers/usb/epcam.h:315: error: field ‘lock’ has incomplete type
/home/exalted/epcam/drivers/usb/epcam.h:316: error: field ‘res_lock’ has incomplete type
/home/exalted/epcam/drivers/usb/epcam.c: In function ‘epcam_create_sysfs_files’:
/home/exalted/epcam/drivers/usb/epcam.c:329: error: void value not ignored as it ought to be
/home/exalted/epcam/drivers/usb/epcam.c:331: error: void value not ignored as it ought to be
/home/exalted/epcam/drivers/usb/epcam.c:333: error: void value not ignored as it ought to be
/home/exalted/epcam/drivers/usb/epcam.c:335: error: void value not ignored as it ought to be
/home/exalted/epcam/drivers/usb/epcam.c:337: error: void value not ignored as it ought to be
/home/exalted/epcam/drivers/usb/epcam.c:339: error: void value not ignored as it ought to be
/home/exalted/epcam/drivers/usb/epcam.c:341: error: void value not ignored as it ought to be
/home/exalted/epcam/drivers/usb/epcam.c: In function ‘decode_eplite’:
/home/exalted/epcam/drivers/usb/epcam.c:1161: warning: unused variable ‘i’
/home/exalted/epcam/drivers/usb/epcam.c: In function ‘epcam_do_ioctl’:
/home/exalted/epcam/drivers/usb/epcam.c:1424: warning: implicit declaration of function ‘v4l_print_ioctl’
/home/exalted/epcam/drivers/usb/epcam.c: In function ‘epcam_read’:
/home/exalted/epcam/drivers/usb/epcam.c:1644: warning: ignoring return value of ‘copy_to_user’, declared with attribute warn_unused_result
/home/exalted/epcam/drivers/usb/epcam.c: In function ‘epcam_mmap’:
/home/exalted/epcam/drivers/usb/epcam.c:1661: warning: implicit declaration of function ‘mutex_lock’
/home/exalted/epcam/drivers/usb/epcam.c:1664: warning: implicit declaration of function ‘mutex_unlock’
/home/exalted/epcam/drivers/usb/epcam.c: At top level:
/home/exalted/epcam/drivers/usb/epcam.c:1703: error: ‘v4l_compat_ioctl32’ undeclared here (not in a function)
/home/exalted/epcam/drivers/usb/epcam.c: In function ‘epcam_init’:
/home/exalted/epcam/drivers/usb/epcam.c:1823: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
/home/exalted/epcam/drivers/usb/epcam.c: In function ‘epcam_probe’:
/home/exalted/epcam/drivers/usb/epcam.c:1887: warning: implicit declaration of function ‘mutex_init’
make[2]: *** [/home/exalted/epcam/drivers/usb/epcam.o] Error 1
make[1]: *** [_module_/home/exalted/epcam] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-52-server'
make: *** [default] Error 2
```

I was hoping someone could help me here, what's wrong? I believe ```
0.8.3
``` is the latest version available by [markaur]("http://ubuntuforums.org/member.php?u=528474") [as mentioned]("http://ubuntuforums.org/showpost.php?p=4681403&postcount=59").

Appreciate your attention.

Best regards,
[Ali Servet Dönmez]("http://www.pittle.org/")

---

### Post by jaboto on 2008-07-06
Fantastic! It works after lots of years waiting in a box!

Mine is an Spypen Actor.

Thanks!!!!

---

### Post by pittle on 2008-07-07
Gush! Am I the only one who couldn't compile this thing? =(

---

