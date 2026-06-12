---
title: "HOWTO logitech quickcam chat for skype with ubuntu gutsy and skype"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by thewOndErEr57 on 2007-12-27
OK, this is a howto on installing a logitech quickcam chat for skype webcam.

On ubuntu gutsy 7.10 .

	uname -a
2.6.22-14-generic

Firstly, you'll be pleased to know that this is easy and pain free,

Step 1
-----

Install gspca-source

	sudo apt-get install gspca-source

Step 2
-----

Plug in your webcam.

Step 3
-----

Edit /etc/rc.local to make the camera device permissions available to all users on system startup.

	sudo gedit /etc/rc.local
	
The line just before "exit 0", put in:
	
	chmod 777 /dev/video0


The last two lines of /etc/rc.local should look like this:
	
	chmod 777 /dev/video0
	exit 0



Step 4 (optional)
-----

Currently to date (30/12/2007) with skype 2.0.0.27 beta, there's an issue (known to skype developers) about how webcams using the gspca driver have a very dark display. A fix for this (thanks to MrFSL !!!) is this:

sudo gedit /etc/modprobe.d/options

add at the end:

options gspca gamma=6

*note*, if this makes the display look distorted, try the value 5.

save this file.

simplest thing to do at this point is to reboot your PC.



Step 5
-----

Reboot your PC. et voila, your camera should now be working.

Check with the camorama:
	sudo apt-get install camorama
	camorama



If this works, so should Skype (version >= 2 !!)


Cheers.

---

### Post by MrFSL on 2007-12-27
For me, this model camera has drastically bad colors. Also, it is so terribly dark, that even in a bright room it is unusable.

---

### Post by thewOndErEr57 on 2007-12-27
MrFSL, I agree - the colours are very dark.

If you use it with "camorama" then you can change the brightness settings, so I think that this is an issue for the skype development team, possibly offering a "brightness setting", or a more intelligent brightness control system in place.

Bear in mind that skype 2.0.0.27 is a BETA, and video for skype linux is not officially released.
MrFSL, I recommend you hang in there until they make version 2 final, and then test you webcam with skype. The brightness issue may be resolved.

---

### Post by gorby on 2007-12-28
Hello, thanks for the post, I have a usb quick cam and all of the same software u describe, the only differance i knowtices is that i had to manually install camorama with apt. However at the end of the process I still dont have anything in /dev/video0 , any ideas on what i might be missing?

I have a quickcam notebook : ID 046d:08dd Logitech, Inc

done a bit more reading about this particular cam, support is avail (but limited) with this driver [http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz)

Info regarding this particular camera is here [http://forums.quickcamteam.net/archive/index.php/thread-22.html](http://forums.quickcamteam.net/archive/index.php/thread-22.html)

Dont want to thread hijack as this is nice concise info for the cams that do work, will start a new thread in a moment.

---

### Post by thewOndErEr57 on 2007-12-28
gorby,
 if you're using spca driver than I suppose we're looking at a slightly different solution for you.

All I can suggest is this:

remove anything you have so far downloaded/installed with the spca driver. then...

sudo apt-get install spca5xx-source

unplug your webcam.

sudo modprobe spca5xx

Plug in your webcam.

ls /dev/vide*

sudo chmod 777 /dev/vide*

camorama -d /dev/video0

if that fails...

camorama -d /dev/video


if that fails, post output from:

dmesg



It's the best I can think of just now....

---

### Post by dometz on 2007-12-28
Thanks for this tutorial. I followed everything, running Ubuntu 7.10 with Quickcam Messenger. The video works in camorama (looks black and white), but not in Skype. When going to Skype menu 'Options/Video Devices', I get no video signal when clicking the 'test' button. Thanks for your help.

---

### Post by thewOndErEr57 on 2007-12-29
dometz, I think you're past the hard part of getting your webcam working. well done.

it works with Camorama, so that's good. Have you tried the "brightness" and "Contrast" options in camorama to see if a better image is possible?

The skype thing...
Firstly, have you tried with a strong light source on your face? You may have a very dark image, as opposed to a black screen.

Otherwise, unplug your webcam then:
-------------------------
sudo modprobe gspca

plug back in.

sudo chmod 777 /dev/video0

test skype.
-----------------------------

If this doesn't work then tell skype to use an external microhpone, as opposed to the internal one in the camera.

Restart skype and try again.

However, if this does not work, then I suppose like a lot of other people I've heard from, you may have to sit and wait for skype to make this version 2 (for video), a final release. They have a lot of bugs they are working on still, and yours may be one of them.

Have hope with the fact that you at least have some use of your camera.

---

### Post by MrFSL on 2007-12-29
These cheaper logitech cameras are VERY VERY dark. The colors are off and the overall image quality is low. I STRONGLY suggest that you don't buy one. 

However, if you already own one here are some tweaks that might help you get a slightly better picture in skype.

Look at the contents of the 'parameters' directory by opening a terminal and typing the following:
```
ls /sys/module/gspca/parameters/
```

This are "module" (or driver if you will) parameters. We can check the current the values of these parameters by reading the contents of these files. For instance, if you have a parameter file called "gamma," typing the following will show its current settings:
```
cat /sys/module/gspca/parameters/gamma
```

This command says that gamma is set to "3" on my computer.

To set this parameter edit the file "/etc/modprobe.d/options"
In my case, on a new line I added:
```
options gspca gamma=5
```

The difference isn't huge, but at least it isn't too dark to use at all now.

Finally you will have to reload the module:
```
sudo rmmod gspca
sudo modprobe gspca
```

Good luck.

---

### Post by thewOndErEr57 on 2007-12-29
MrFSL, excellent advise.

I tested and although documentation of the gspca driver states that this "gamma" option value is 0 to 7, I tried 7 and the display was very distorted.

So the value of 6 worked for me.

Priceless advise, thanks !!

I will put this into the HOWTO above.

---

### Post by MrFSL on 2007-12-30
> Currently to date (30/12/2007) with skype 2.0.0.27 beta, there's an issue (known to skype developers) about how webcams using the gspca driver have a very dark display. A fix for this (thanks to MrFSL !!!) is this:

sudo gedit /sys/module/gspca/parameters/gamma

add at the end:

options gspca gamma=6

*note*, if this makes the display look distorted, try the value 5.

save this file.

simplest thing to do at this point is to reboot your PC

Check your howto. You do not edit /sys/module/gspca/parameters/gamma - you would edit **/etc/modprobe.d/options**

Cheers.

**EDIT** - the /sys/gspca/parameters/gamma file will show you your current settings. 

Note too that a value of 7 on the cams I have tested inverts and distorts (the same issue I suspect that you reported)

---

### Post by thewOndErEr57 on 2007-12-30
Foolish error.

edited the howto.

Cheers.

---

### Post by Opticon on 2007-12-30
Hi;

I've tried modifying the gamma as mentions above, but I'm still getting a fuzzy image or almost grid like pattern showing up when I test the webcam in skype (I can't make out anything in the test screen). I don't have this problem when I run the webcam with camorama or xawtv. Any ideas?

I'm using ubuntu 7.10 and a quickcam Messenger webcam

---

### Post by blackest_knight on 2008-01-01
> **Opticon said:**
> Hi;

I've tried modifying the gamma as mentions above, but I'm still getting a fuzzy image or almost grid like pattern showing up when I test the webcam in skype (I can't make out anything in the test screen). I don't have this problem when I run the webcam with camorama or xawtv. Any ideas?

I'm using ubuntu 7.10 and a quickcam Messenger webcam

Interesting- that you get anything at all. 
Everything i have seen so far till this thread suggests the quickcam messenger doesn't work with skype in Linux.  camerama gives me a similar grid like output, Xawtv is perfect. 

you couldnt post the output of lsusb could you 

Bus 001 Device 004: ID 046d:08f0 Logitech, Inc. QuickCam Messenger (my cam for comparison)

hopefully your version is the same.

---

### Post by MrFSL on 2008-01-01
If you check out this link:
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

You will see how the author has tried to display cameras that have been tested with this driver; their success, and relative quality.

Now - I do believe the original post was concerning the **"Quickcam Chat For Skype** model. (One not listed on this page.) The closest model is the **"Quickcam Chat"** - which seems to still be in testing. I have owned this quickcam chat and all my references are to it. All other models will probably have DRASTICALLY different qualities - although you should still be able to adjust some of the parameters as I have outlined.

> you couldnt post the output of lsusb could you

Bus 001 Device 004: ID 046d:08f0 Logitech, Inc. QuickCam Messenger (my cam for comparison)
Another camera not listed on this page. I see that 046d:08da is listed and given 4 stars. Curious if you would give your mode 4 stars.

> Everything i have seen so far till this thread suggests the quickcam messenger doesn't work with skype in Linux.
"Work" is a vague term. If the camera works it might have a bug in skype. For instance several cameras (especially from the quickcam series) suffer when the user has bad or low connection speeds. - This is a known bug - skype tries to drop the resolution down and these cameras (or this driver) does not handle this well. The results can be anything from the picture going black to skype crashing. 

What I am saying is that you will read mixed reviews. Some people have (so far) had the same quality every time they have used their camera. (This is where I was! I had purchased the QuickCam Chat and everything seemed low quality but acceptable and reliable. So then I bought 5 more for family members - this is when I realized that my faster internet connection was the key in many cases.) Other people will say the camera has never worked in Skype but it does in Camorama. This could very possibly be because of the resolution bug. On a faster network connection it might work better.

Hope this helps and clarifies.
Cheers
:)

---

### Post by dometz on 2008-01-01
thewOndErEr57, thank you very much for your time and your advice! I followed every step, but unfortunately had not much succes. As you rightly suggested, if nothing works I will have to wait fro Skype to improve v.2. Thanks again. Dom.

---

### Post by Opticon on 2008-01-02
the output for lsusb is 

Bus 002 Device 003: ID 046d:08f6 logitech, Inc.

MrSFL 

Thanks, for the link. The camera does have fairly good image quality, for a webcam, when I use it in other programs like camorama and xawtv, however, for some reason its terrible in Skype. 

I think your explanation of connection speed and quality is probably true. However, does an internet connection affect Skype's camera test option? I've tried the test option and a regular call, both with the same results. 

I've also tried the camera in Ekiga, which doesn't seem to have any trouble with it.

---

### Post by James Newling on 2008-01-14
I am using Logitech QuickCam Chat(Bus 002 Device 003: ID 046d:08da Logitech, Inc.), and after following the clear instructions given at the start of the thread i have got my camera working. However, the image on Camorama has strange colours - my blue eyes appear yellow and my red jacket appears blue. Any parameter suggestions?

---

### Post by citybird on 2008-01-19
hi all.

I have checked everything and installed both the spca and gspca modules.
modprobing them does not work and I do not have a /dev/video or /dev/vdeo0 

First I dont understand how installing the source gives you the driver shouldn't you compile the source first?

Second I tried compiling the source found in /usr/src/
first I unpacked the tar.bz2 files
then cd to the folder /usr/src/modules/spca5xx
then make and I get the following message...

```
# sudo make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/modules/spca5xx CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /usr/src/modules/spca5xx/drivers/usb/spca5xx.o
/usr/src/modules/spca5xx/drivers/usb/spca5xx.c:39:26: error: linux/config.h: No such file or directory
/usr/src/modules/spca5xx/drivers/usb/spca5xx.c: In function ‘spca50x_init_isoc’:
/usr/src/modules/spca5xx/drivers/usb/spca5xx.c:1681: warning: assignment from incompatible pointer type
make[2]: *** [/usr/src/modules/spca5xx/drivers/usb/spca5xx.o] Error 1
make[1]: *** [_module_/usr/src/modules/spca5xx] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2

```

I have no more ideas how to make this work...

---

### Post by Rigrig on 2008-02-17
> **James Newling said:**
> I am using Logitech QuickCam Chat(Bus 002 Device 003: ID 046d:08da Logitech, Inc.), and after following the clear instructions given at the start of the thread i have got my camera working. However, the image on Camorama has strange colours - my blue eyes appear yellow and my red jacket appears blue. Any parameter suggestions?

I've got the same camera with the funny colors in Camorama:
In Camorama, enable 'Show effects' in the 'view' menu, then in the effects list right-click and choose 'Add filter'>'Color correction'.
In Skype I didn't have these color problems at all.

---

### Post by tettayes on 2008-04-02
the #1 how-to post worked for me although I am using Hardy Heron.
however, one problem remains...that is, whenever I am using webcam in skype (in a video chat with someone), it zooms in automatically to very close up of my face.
I need to finish a call and call back again to fix it.  But it happens all the time after in a call for about 2 to 3 minutes...
Does anyone know how to fix this automatically zooming in stuff?
I am pretty sure it is a bug though.

Thanks a lot for your help in advance!

---

### Post by janclodvandam on 2008-04-13
Hello people
I want to thank everyone who has posted advises here. I followed everything but, although amorama works, skype (v 2.0.0.68) doesn't find any cameras. Now, all i can do is watch myself with camorama. Yay! Well, i suppose i could do that in a mirror.
Anyways is there anything new regarding this problem? Can i at least use kopete to video chat with someone who has msn?
Thanks

---

### Post by reemM on 2008-04-13
Hello,:confused:

I've installed gspca. Added the line in rc.local to give permissions to all users, etc.:confused:

1) /dev/video0 does not exist
2) result of lsusb:

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 049f:0086 Compaq Computer Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:08dd Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

3) result of sudo modprobe gspca:
[ 2897.668000] usbcore: registered new interface driver gspca
[ 2897.672000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered

4) /dev/video0 still does not exist

so, I've tried using spca5xx instead, and followed your post.

still, nothing. I've rebooted some 5+ times, just in case. No result. Please help!


Thanks a lot,
Reem

---

### Post by thewOndErEr57 on 2008-05-04
Glad to have helped so many people.

ReemM, version 1.00.12 of gspca is outdated. The first thing I would suggest is to remove this version of gspca you have installed via your package manager.

Then get version 1.00.20 from [HERE]("http://mxhaard.free.fr/download.html") , then execute the gspca_build file as root ("su" or "sudo").

Reboot, then let me know how you get on.

If it fails, post on this forum: 
dmesg | grep gspca

It you succeed then congrats, and let us know.

---

### Post by reemM on 2008-05-04
thewOndErEr57, 

thank you but the post it is now useless for me. My graphics card blew out and I've purchased a Dell Inspiron 1420 w/ a built in camera and Ubuntu preinstalled. Hopefully it will be useful for somebody else to try, though.


Thanks again,
Reem

---

### Post by Lothas on 2008-05-05
Hey, I have the Lego Mindstorms Vision Command camera:
Bus 001 Device 004: ID 046d:0850 Logitech, Inc. QuickCam Web

and it doesn't work properly, not even in Hardy. Since 7.10 the built-in mic works ok (little down on gain) but the camera is still not working. This is one of the only things keeping me from moving completely to Ubuntu.

I've tried compiling the qc-usb driver without much luck. This is the output:

make all
```
make -C "/lib/modules/2.6.24-16-generic/build" SUBDIRS="/home/lothas/Desktop/qc-usb-0.6.6" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /home/lothas/Desktop/qc-usb-0.6.6/.tmp_versions ; rm -f /home/lothas/Desktop/qc-usb-0.6.6/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/lothas/Desktop/qc-usb-0.6.6
  gcc -m32 -Wp,-MD,/home/lothas/Desktop/qc-usb-0.6.6/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -DNOKERNEL -DHAVE_UTSRELEASE_H=1  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/lothas/Desktop/qc-usb-0.6.6/.tmp_qc-driver.o /home/lothas/Desktop/qc-usb-0.6.6/qc-driver.c
In file included from /home/lothas/Desktop/qc-usb-0.6.6/qc-driver.c:47:
/home/lothas/Desktop/qc-usb-0.6.6/quickcam.h:129:1: warning: "BIT" redefined
In file included from include/linux/kernel.h:15,
                 from include/linux/cache.h:4,
                 from include/linux/time.h:7,
                 from include/linux/videodev2.h:59,
                 from include/linux/videodev.h:15,
                 from /home/lothas/Desktop/qc-usb-0.6.6/quickcam.h:95,
                 from /home/lothas/Desktop/qc-usb-0.6.6/qc-driver.c:47:
include/linux/bitops.h:6:1: warning: this is the location of the previous definition
/home/lothas/Desktop/qc-usb-0.6.6/qc-driver.c: In function ‘qc_i2c_init’:
/home/lothas/Desktop/qc-usb-0.6.6/qc-driver.c:824: error: ‘struct urb’ has no member named ‘lock’
/home/lothas/Desktop/qc-usb-0.6.6/qc-driver.c:825: warning: assignment from incompatible pointer type
/home/lothas/Desktop/qc-usb-0.6.6/qc-driver.c: In function ‘qc_isoc_start’:
/home/lothas/Desktop/qc-usb-0.6.6/qc-driver.c:1867: warning: assignment from incompatible pointer type
/home/lothas/Desktop/qc-usb-0.6.6/qc-driver.c: At top level:
/home/lothas/Desktop/qc-usb-0.6.6/qc-driver.c:3009: error: unknown field ‘hardware’ specified in initializer
make[2]: *** [/home/lothas/Desktop/qc-usb-0.6.6/qc-driver.o] Error 1
make[1]: *** [_module_/home/lothas/Desktop/qc-usb-0.6.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [quickcam.ko] Error 2

```

---

### Post by BandD on 2008-05-09
> Currently to date (30/12/2007) with skype 2.0.0.27 beta, there's an issue (known to skype developers) about how webcams using the gspca driver have a very dark display. A fix for this (thanks to MrFSL !!!) is this:

sudo gedit /etc/modprobe.d/options

add at the end:

options gspca gamma=6

*note*, if this makes the display look distorted, try the value 5.

save this file.

simplest thing to do at this point is to reboot your PC.

Changing this value to 5 worked perfectly for me in Gutsy, but doing so in Hardy resulted in a completely frozen system if Skype tried to access the camera--I had to do a forced shutdown by holding the power button (though it was fine for camoramma).  But I found that a value of 4 worked flawlessly with Skype.  So I'm not really sure what the deal was there, just wanted to post in case others had a similar problem.

Thanks again for this great howto!

---

### Post by manosx on 2008-05-26
My webcam is [lsusb output]:
Bus 001 Device 006: ID 046d:08dd Logitech, Inc.

With gspca module my camera works out of the box. Kopete for example manages it correctly and i can change stuff like brightness.
But since it is very dark (with skype, with kopete i haven't test it that time), I load the module with options:

cat /etc/modprobe.d/options
> 
...
options gspca autoexpo=0 gamma=6
...


On Skype, the camera utilized the remaining free cpu. For example when I do Options -> Video devices -> Test (a small window were you see the input from camera, cpu rises to 99%)

To solve this, I am using gstfakevideo. To run skype I
gstfakevideo v4lsrc device=/dev/video0 ! ffmpegcolorspace

Now, the problem is that i have too much brightness, Playing with gamma didn't solve the problem.
Anyway, the brightness is not too much, is more than it should. How can I control that?
Until now, this is the most workable configuration i have tried.

---

### Post by Plasma_NZ on 2008-06-02
> **manosx said:**
> My webcam is [lsusb output]:
Bus 001 Device 006: ID 046d:08dd Logitech, Inc.

With gspca module my camera works out of the box. Kopete for example manages it correctly and i can change stuff like brightness.
But since it is very dark (with skype, with kopete i haven't test it that time), I load the module with options:

cat /etc/modprobe.d/options


On Skype, the camera utilized the remaining free cpu. For example when I do Options -> Video devices -> Test (a small window were you see the input from camera, cpu rises to 99%)

To solve this, I am using gstfakevideo. To run skype I
gstfakevideo v4lsrc device=/dev/video0 ! ffmpegcolorspace

Now, the problem is that i have too much brightness, Playing with gamma didn't solve the problem.
Anyway, the brightness is not too much, is more than it should. How can I control that?
Until now, this is the most workable configuration i have tried.


I've tried using gstfakevideo and get te following result whic crash's skype

```
Skype V4L: Failed to query capabilities: Invalid argument
Starting the process...
Skype Xv: Xv ports available: 32
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 280
Skype Xv: No suitable overlay format found
Aborted

```

---

### Post by taikonaut on 2008-06-15
> **manosx said:**
> 
cat /etc/modprobe.d/options



```
options gspca autoexpo=0 gamma=6
``` doesn't work... doesn't recognoze "options"


> Now, the problem is that i have too much brightness, Playing with gamma didn't solve the problem.
Anyway, the brightness is not too much, is more than it should. How can I control that?Until now, this is the most workable configuration i have tried.

I have wrong colors (same in camorama, in aMSN it works). How can I control these?

---

### Post by sirtah on 2008-06-15
Hello Everyone, 

Thanks for all the help with the logitech quickcam but I'm still having a problem. When I open camorama the video displayed is from my tv tuner. I'm not sure how to fix this and I've created a thread at 

[http://ubuntuforums.org/showthread.php?t=821579](http://ubuntuforums.org/showthread.php?t=821579)

Thanks in advance for any suggestions.

---

### Post by manosx on 2008-06-15
**Taikonaut**, Doesn't recognized options? Is that what you get from the module? When you change options file you need to reload the module.
That is ```

$sudo modprobe -r gspca
$sudo modprobe gspca
```
I'm not sure what is happening, but this is the way to pass options to modules.. :(

**Sirtah**, that is because you are selecting the wrong video device. Your tvtuner may be /dev/video0 and the webcam /dev/video1. Check and see which device is which and select the appropriate device by running gstfakevideo with device=[TheCorrectDevice]

---

### Post by sirtah on 2008-06-15
manosx, 

Thanks for the reply. Sorry but I'm a beginner here. I only have a /dev/video0, how can I create a /dev/video1 and get the webcam to point to it?

Thanks, 

sirtah

---

### Post by manosx on 2008-06-15
You should not create a device.
In my computer:
```
$ ls /dev/video*
ls: cannot access /dev/video*: No such file or directory
**Then I plug in the webcam and**
$ ls /dev/video*
/dev/video0
```

When you plug in the webcam, can you see it when **$ dmesg** ?

Is the module loading? Try 
**$ lsmod | grep gspca** 
after you have plugged in the webcam to see if the module is loading. 

You can manualy load the module with 
**$ sudo modprobe gspca**

---

### Post by sirtah on 2008-06-16
manosx, 

Thanks for your help. I tried your suggestions and here is what happened :

----

 sudo modprobe gspca

FATAL: Error inserting gspca (/lib/modules/2.6.24-18-generic/ubuntu/media/gspcav1/gspca.ko): Unknown symbol in module, or unknown parameter (see dmesg)
 
 dmesg | grep gspca

[   54.836982] gspca: disagrees about version of symbol video_devdata
[   54.836985] gspca: Unknown symbol video_devdata
[   54.837140] gspca: disagrees about version of symbol video_unregister_device
[   54.837141] gspca: Unknown symbol video_unregister_device
[   54.837199] gspca: disagrees about version of symbol video_device_alloc
[   54.837200] gspca: Unknown symbol video_device_alloc
[   54.837221] gspca: disagrees about version of symbol video_register_device
[   54.837223] gspca: Unknown symbol video_register_device
[   54.837347] gspca: disagrees about version of symbol video_device_release
[   54.837348] gspca: Unknown symbol video_device_release
[   54.842955] gspca: disagrees about version of symbol video_devdata
[   54.842958] gspca: Unknown symbol video_devdata
[   54.843112] gspca: disagrees about version of symbol video_unregister_device
[   54.843114] gspca: Unknown symbol video_unregister_device
[   54.843170] gspca: disagrees about version of symbol video_device_alloc
[   54.843172] gspca: Unknown symbol video_device_alloc
[   54.843193] gspca: disagrees about version of symbol video_register_device
[   54.843195] gspca: Unknown symbol video_register_device
[   54.843319] gspca: disagrees about version of symbol video_device_release
[   54.843320] gspca: Unknown symbol video_device_release
[   55.014811] gspca: disagrees about version of symbol video_devdata
[   55.014814] gspca: Unknown symbol video_devdata
[   55.014972] gspca: disagrees about version of symbol video_unregister_device
[   55.014973] gspca: Unknown symbol video_unregister_device
[   55.015031] gspca: disagrees about version of symbol video_device_alloc
[   55.015033] gspca: Unknown symbol video_device_alloc
[   55.015055] gspca: disagrees about version of symbol video_register_device
[   55.015056] gspca: Unknown symbol video_register_device
[   55.015183] gspca: disagrees about version of symbol video_device_release
[   55.015184] gspca: Unknown symbol video_device_release
[ 1594.665922] gspca: disagrees about version of symbol video_devdata
[ 1594.665927] gspca: Unknown symbol video_devdata
[ 1594.666100] gspca: disagrees about version of symbol video_unregister_device
[ 1594.666103] gspca: Unknown symbol video_unregister_device
[ 1594.666169] gspca: disagrees about version of symbol video_device_alloc
[ 1594.666170] gspca: Unknown symbol video_device_alloc
[ 1594.666197] gspca: disagrees about version of symbol video_register_device
[ 1594.666199] gspca: Unknown symbol video_register_device
[ 1594.666341] gspca: disagrees about version of symbol video_device_release
[ 1594.666343] gspca: Unknown symbol video_device_release
[ 1594.728901] gspca: disagrees about version of symbol video_devdata
[ 1594.728906] gspca: Unknown symbol video_devdata
[ 1594.729079] gspca: disagrees about version of symbol video_unregister_device
[ 1594.729080] gspca: Unknown symbol video_unregister_device
[ 1594.729146] gspca: disagrees about version of symbol video_device_alloc
[ 1594.729147] gspca: Unknown symbol video_device_alloc
[ 1594.729173] gspca: disagrees about version of symbol video_register_device
[ 1594.729174] gspca: Unknown symbol video_register_device
[ 1594.729316] gspca: disagrees about version of symbol video_device_release
[ 1594.729317] gspca: Unknown symbol video_device_release
[ 1594.731952] gspca: disagrees about version of symbol video_devdata
[ 1594.731955] gspca: Unknown symbol video_devdata
[ 1594.732128] gspca: disagrees about version of symbol video_unregister_device
[ 1594.732130] gspca: Unknown symbol video_unregister_device
[ 1594.732195] gspca: disagrees about version of symbol video_device_alloc
[ 1594.732197] gspca: Unknown symbol video_device_alloc
[ 1594.732223] gspca: disagrees about version of symbol video_register_device
[ 1594.732224] gspca: Unknown symbol video_register_device
[ 1594.732366] gspca: disagrees about version of symbol video_device_release
[ 1594.732367] gspca: Unknown symbol video_device_release
[ 1720.411770] gspca: disagrees about version of symbol video_devdata
[ 1720.411777] gspca: Unknown symbol video_devdata
[ 1720.412064] gspca: disagrees about version of symbol video_unregister_device
[ 1720.412068] gspca: Unknown symbol video_unregister_device
[ 1720.412179] gspca: disagrees about version of symbol video_device_alloc
[ 1720.412181] gspca: Unknown symbol video_device_alloc
[ 1720.412225] gspca: disagrees about version of symbol video_register_device
[ 1720.412228] gspca: Unknown symbol video_register_device
[ 1720.412465] gspca: disagrees about version of symbol video_device_release
[ 1720.412467] gspca: Unknown symbol video_device_release
[ 2137.310284] gspca: disagrees about version of symbol video_devdata
[ 2137.310292] gspca: Unknown symbol video_devdata
[ 2137.310580] gspca: disagrees about version of symbol video_unregister_device
[ 2137.310584] gspca: Unknown symbol video_unregister_device
[ 2137.310694] gspca: disagrees about version of symbol video_device_alloc
[ 2137.310696] gspca: Unknown symbol video_device_alloc
[ 2137.310740] gspca: disagrees about version of symbol video_register_device
[ 2137.310742] gspca: Unknown symbol video_register_device
[ 2137.310980] gspca: disagrees about version of symbol video_device_release
[ 2137.310982] gspca: Unknown symbol video_device_release

----

 lsusb
Bus 001 Device 006: ID 046d:08d7 Logitech, Inc. 

-----

This is all over my head right now. Your help is much appreciated. 

sirtah

---

### Post by manosx on 2008-06-17
There is a bug about that here:
[https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/160814](https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/160814)

But it seems it's on 2.6.22 kernel. I have, like you the 2.6.24-18 kernel but works for me.. 
There are some workarounds there but i don't know if they work.. 2.6.24-19 is out as well.. So, maybe you want to update to the new kernel and if that doesn't work, try the workarounds..

---

### Post by sirtah on 2008-06-17
manosx, 

Thank you for all your help. I'll look into either updating my kernel or using one of the workarounds in the link you provided and let you know how it goes. 

Thanks again, 

sirtah

---

### Post by sirtah on 2008-06-20
manosx, 

Thanks for all the help. I upgraded my kernel to 2.6.24-19 and pointed camorama to /dev/video1 and I was all set. 

Thanks again and best wishes,  

sirtah

---

