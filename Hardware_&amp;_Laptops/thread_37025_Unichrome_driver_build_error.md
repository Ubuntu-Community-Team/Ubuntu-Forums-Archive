---
title: "Unichrome driver build error"
date: 2005-05-25
forum: Hardware &amp; Laptops
---

### Post by xethm55 on 2005-05-25
I have been trying to build the unichrome driver.  I have installed build-essential. I downloaded the latest via driver.  when i am trying to build the package, i get the following error:
```

make -C /lib/modules/2.6.10-5-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
/home/xethm55/unichrome/via-20050517-linux.i386.tar.bz2_FILES/dripkg/drm/linux-core/Makefile:279: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
make[1]: *** [_module_/home/xethm55/unichrome/via-20050517-linux.i386.tar.bz2_FILES/dripkg/drm/linux-core] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make: *** [modules] Error 2
```

How do i remedy this error?

Thank you for any help,
xethm55

---

### Post by xethm55 on 2005-05-26
I found a solution to my problem.  I needed to install the latest linux image, source and headers for K7.  The unichrome drivers do not seem to work with a 386 linux image.  I am not sure if others have ran into this problem, if they do, i hope this will help.  

P.S.  I was successful at getting the unichrome drivers to work.  Atlest to the point of the glxinfo now saying that direct rendering is turned on. glxgears says that i have about 650fps.  I really makes a difference in some of the games and overall performance of the machine.  

Thanks,
-Xethm55

---

### Post by ganatronic on 2005-05-29
Just curious: Are you using the howto on the sourceforge unichrome project page? Or something else.... or just winging it 'cause you're smart?

I need to do this soon, and am trying to figure out what my options are.

---

### Post by xethm55 on 2005-06-02
[QUOTE=ganatronic]Just curious: Are you using the howto on the sourceforge unichrome project page? Or something else.... or just winging it 'cause you're smart?

I need to do this soon, and am trying to figure out what my options are.[/QUOTE]
Sorry about the delay in reply.
I am used the documentation at [sourceforge](http://sourceforge.net/docman/display_doc.php?docid=26963&group_id=102048) .  The part about compiling the Xorg source, you do not need to do, since Hoary already has the driver that you need. The rest of the document, though, is needed.  The biggest thing is that when you get done "glxinfo" should say that direct rendering is enabled.

---

### Post by ganatronic on 2005-06-03
No prob about the delay. Thanks for the info. 

So basically I just need to build and configure the DRM kernel modules and the Unichrome-3D drivers? which means I'd skip parts "b" in sections 2 and 3, which have to do with xorg drivers?

I'll give it a try! ...in a few days.

---

### Post by LongTooth on 2005-06-03
Well, this is too much for me. But there is hope. If I read the sourceforge article correctly these drivers will be included in the near future. I think I'll wait. Like one of my favorite movie character said: 'A man has to know his limitations'. And I see clearly where they are. As a permenate intermediate Linux user I consider this way beyond my capacity. But not to fear, I can wait. Unless some kind soul is willing to write an auto script? Maybe? 

Not being a gamer I though I would give intergrated video a try  with my next home built PC. And I did. I was also interested in a PC with a smaller foot print. The Shuttle type were beyond my price range and so I looked into the microATX. I purchased a Gigabyte 7VM400M-RZ microATX mother board and haven't been happer. Besides this machine being smaller that the full ATXs, the on board graphics chip set handles everything I throw at it very well. But never the less I still want my PC to take advantage of any drivers. 

This microATC MoBo uses the Unichorme chipset. I hope to someday install the Via drivers. But until that day comes, I'll sit here and enjoy it as is. Thanks for the post. I"ll keep my eye on it.

---

### Post by ganatronic on 2005-06-04
Ditto here. I'm hoping support for it gets included in Breezy. I'll probably try and do it myself -- just to see if I can, and to learn, etc. but I'm not very optimistic about succeeding. Who knows, though, maybe it'll be smooth. I seem to eventually figure out most things that I build myself.

Also, lack of total unichrome support is not detrimental to my computing right now, as I'm not playing any 3D games at the moment, or doing any other big things that require sick graphics. I have, though, noticed that I might be having some video playback issues (there are slight tracers during movement, and noticible slowdown during info-heavy shots -- even with DMA turned on) which, at the moment, I'm attributing to my current support set-up. I'd also like to play Tuxracer, since that game seems pretty cool. It was choppy as all heck when I tried it.

I'm guessing that, at the moment, Hoary has recognized my card (because I seem to remember it saying something about identifying VIA. It supports it and everything, but it's just not taking full advantage of it.

Hopefully when Breezy comes around we'll be able to smoothly sail down the icy slopes of Tuxracer.

---

### Post by Tomy on 2005-06-07
[QUOTE=ganatronic]Ditto here. I'm hoping support for it gets included in Breezy. I'll probably try and do it myself -- just to see if I can, and to learn, etc. but I'm not very optimistic about succeeding. Who knows, though, maybe it'll be smooth. I seem to eventually figure out most things that I build myself...[/QUOTE]
During the Hoary testing phase I figured out how to do this and made this simple script so I wouldn't have to type all the commands in again everytime xorg was updated. As you can see, I am an end user not a programmer:???:.

 ```
#!/bin/sh
# 
# Unichrome 3d-HOWTO for Ubuntu 5.04 (Hoary)
# These instructions are based on the Unichrome 3d-HOWTO posted here: http://sourceforge.net/docman/?group_id=102048 
#
# This is how I got tuxracer to work on an MSI KM4AM-V motherboard (AMD k7 with onboard VIA S3 UniChrome graphics)
#
# This script must be run as root. Maybe you can "sudo" run it but I have a root login and do not use sudo.
#
# Make sure the linux kernel headers are installed
#
# Before running this script download and extract two files:
#
# file #1: via-20050608-linux.i386.tar.bz2
# can be found here:
# http://dri.freedesktop.org/snapshots/
#
# file #2: opensource_ubranch_20050302.tbz2
# can be found here:
# http://sourceforge.net/project/showfiles.php?group_id=102048
#
# STEP 1. Set the directory where the install files have been extracted
#		 (from the file browser I right-clicked on the file and clicked on "extract here")
#		 (this extracts the files to a subdirectory fileName_FILES) 
# *** edit this line and then run the script *** good luck *** maybe it will work **
dir=/home/tomy/install
#
# STEP 2. Create drm.ko and via.ko
#
cd $dir/via-200500608-linux.i386.tar.bz2_FILES/dripkg/drm/linux-core
make DRM_MODULES="via"
echo "drm.ko and via.ko created"
#
# STEP 3. Copy drm.ko and via.ko to proper directory
#
cd $dir/via-20050608-linux.i386.tar.bz2_FILES/dripkg/drm/linux-core
cp -f drm.ko via.ko /lib/modules/2.6.10-5-k7/kernel/drivers/char/drm/
echo "via.ko and drm.ko copied"
#
# STEP 4. Add via DRM module to the kernel
#
depmod -ae
modprobe via
echo "via DRM module added to kernel"
#
# STEP 5. Replace ubuntu via_drv.o with unichrome project via_drv.o
#
mv /usr/X11R6/lib/modules/drivers/via_drv.o via_drv.o.bak
cd $dir/via-20050608-linux.i386.tar.bz2_FILES/dripkg/via
cp -a via_drv.o /usr/X11R6/lib/modules/drivers
echo "unichrome project via_drv.o copied" 
#
# STEP 6. Replace ubuntu libGL.so.1.2  with unichrome project libGL.so.1.2 
#
mv /usr/X11R6/lib/libGL.so.1.2 libGL.so.1.2.bak
cd $dir/opensource_ubranch_20050302.tbz2_FILES
cp -a libGL.so.1.2 /usr/X11R6/lib/
echo "unichrome project libGL.so.1.2 copied"
#
# STEP 7. Replace ubuntu "unichrome_dri.o" with unichromeProject "unichrome_dri.o"
#
mv /usr/X11R6/lib/modules/dri/unichrome_dri.so unichrome_dri.so.bak
cd $dir/opensource_ubranch_20050302.tbz2_FILES/modules/dri
cp -a unichrome_dri.so /usr/X11R6/lib/modules/dri/unichrome_dri.so
echo "unichrome project unichrome_dri.o copied"
#
# end of script
#
# LAST STEP: edit xorg.conf and reboot
echo "you now need to edit /etc/X11/xorg.conf and then reboot"
#
# change the "Device" section to look something like this:
# Section "Device"
#	    Identifier	  "VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
#		Driver		  "via"
#		BusID		   "PCI:1:0:0"
#		Option		  "DisableIRQ"
#		Option		  "EnableAGPDMA"
# EndSection"
``` 

Hope this is useful. Good Luck!
Tomy

ps. I have edited the script to reflect the proper location to download the newest version of the "via" file, but I have not tested it. Let me know if it works.

---

### Post by ganatronic on 2005-06-08
Thanks! I'll give this a try. However, I can't locate "# file #2: via-20050314-linux.i386.tar.bz2" on that sourceforge page. Is there another place to find it? I really want to give this script a try.

---

### Post by xethm55 on 2005-06-08
You can use this [file](http://dri.freedesktop.org/snapshots/via-20050608-linux.i386.tar.bz2) you will just have to change any where the script contains "via-20050314-linux.i386.tar.bz2" to   "via-20050608-linux.i386.tar.bz2" then it should work.

-Xethm55

---

### Post by Tomy on 2005-06-08
[QUOTE=ganatronic]Thanks! I'll give this a try. However, I can't locate "# file #2: via-20050314-linux.i386.tar.bz2" on that sourceforge page. Is there another place to find it? I really want to give this script a try.[/QUOTE]

I found the file here:

[http://dri.freedesktop.org/snapshots/]("http://dri.freedesktop.org/snapshots/")

but now there are much newer ones and I can't even locate the 20050314 version in the archive.

As xemth55 noted above you will now have to edit the script.

Sorry about that. Tomy

ps I made the edits to the script so you can just copy it from the previous post.

---

### Post by ganatronic on 2005-06-08
Gotcha. Thanks.

Edit: Sweet. Ran smoothly.

after reboot, glxgears is only showing around 155fps. Are there any other ways to troubleshoot or configure to see if all my settings are optimized? Perhaps I need to alter the xorg.conf file a little more...


edit again, I spelled xorg wrong.

---

### Post by ganatronic on 2005-06-08
Once I'm off work and back on my 'puter, I'll check my xorg.conf against the one on the unichrome project's howto. And then I'll go through those troubleshooting steps.

But thanks for the script. I just had to change a few referential things (locations; from "k7" to "686"), and then it ran smooth. I love how public and verbose the logs are in linux, and how it's so easy to rectify problems that arise when executing things. The lack of errors when compiling leads me to believe my problem now just lies in xorg.

---

### Post by Tomy on 2005-06-08
Great!! glad the script worked - or appeared to work. Sometimes I have to run it a second time to really get dri working.

When you run glxinfo does it say
"direct rendering: Yes"
near the top?

glxgears reports around 450 fps with my Athlon XP 3200.

And the real question -- does tuxracer race? :)

Tomy

---

### Post by ganatronic on 2005-06-09
hrm, still says "Directed Rendering: No".

Although I am getting fps of around 240 now. but that might be because I switched default depth from 24 to 16.

I tried fiddling around with xorg.conf some more, but was only able to mess up X. I'll try some more things. I'll see if there are any more things I need to tweak on the script.

Tomy, would you be able to show me your xorg.conf file? I'm having problems finding full examples of ones using via unichrome. I mean, in theory all you really need to do is change "vesa" to "via", but there might be something else that I'm missing.

Also, when I open "Device Manager" pretty much all my devices except my usb ports are "unknown" - I wonder if those need to be recognized by the system.

---

### Post by xethm55 on 2005-06-30
[QUOTE=ganatronic]hrm, still says "Directed Rendering: No".
[/QUOTE]
That is not good.  You need that to say yes.  What is the output when you run:
```
sudo modprobe via
```

---

### Post by ganatronic on 2005-07-01
"sudo modprobe via" produces absolutely no output. It doesn't tell me anything. So I guess that means it's not configured.

One thing that's been worrying me is that when I open up Device Manager pretty much all my devices except for USB ports are "unknown". It's not recognizing the devices correctly -- monitor, hard drive, etc. I'm not sure if that would conflict with my xorg.conf file or not, but it still worries me. I've done a quick search, and no one else seems to have any similar problems with their device manager.

---

### Post by Rinnan on 2005-07-02
Hm, well, I got the script to work and get this error in my Xorg.0.log...

```
(II) VIA(0): 3D Engine has been initialized.
(EE) VIA(0): [dri] VIADRIScreenInit failed because of a version mismatch.
[dri] libdri version is 4.1.0 but version 5.0.x is needed.
[dri] Disabling DRI.
```

Tried various versions of the two files, but no difference in behavior.   I am using linux for 686 (not k7) since I have a Nehemiah M10000.  Made various changes to reflect that and other differences between my environment and the script.

Almost there... Any ideas?

---

### Post by Tomy on 2005-07-04
[QUOTE=Rinnan]Hm, well, I got the script to work and get this error in my Xorg.0.log...

```
(II) VIA(0): 3D Engine has been initialized.
(EE) VIA(0): [dri] VIADRIScreenInit failed because of a version mismatch.
[dri] libdri version is 4.1.0 but version 5.0.x is needed.
[dri] Disabling DRI.
```

Tried various versions of the two files, but no difference in behavior. I am using linux for 686 (not k7) since I have a Nehemiah M10000. Made various changes to reflect that and other differences between my environment and the script.

Almost there... Any ideas?[/QUOTE]
I've seen this "version mismatch" error before. I just got the S3 Unichrome Pro graphics chip to work on a AMD K8 motherboard using an experimental driver from the unichrome project that someone has packaged for ubuntu.

You can find some info [here.]("http://www.csd.uwo.ca/%7Emfgalizi/debian")

To install this driver you add this to /etc/sources.list
```
# Unichrome Packages (VERY EXPERIMENTAL)
deb http://www.csd.uwo.ca/~mfgalizi/debian hoary unichrome
deb-src http://www.csd.uwo.ca/~mfgalizi/debian hoary unichrome
``` 

and then try this:
 ```
# apt-get update
# apt-get install xserver-unichrome libviaxvmc1 libxvmcw1
```

Tomy

---

### Post by Tomy on 2005-07-04
[QUOTE=ganatronic]"sudo modprobe via" produces absolutely no output. It doesn't tell me anything. So I guess that means it's not configured.

One thing that's been worrying me is that when I open up Device Manager pretty much all my devices except for USB ports are "unknown". It's not recognizing the devices correctly -- monitor, hard drive, etc. I'm not sure if that would conflict with my xorg.conf file or not, but it still worries me. I've done a quick search, and no one else seems to have any similar problems with their device manager.[/QUOTE]
My device manager has always looked like that. I doubt that it has anything to do with xorg.

I have an experimental via driver running on an MSI K8MM-V motherboard -- dri is working, glxgears reports 575 fps, tuxracer races. When I do "sudu modprobe via" there is absolutely no output.

regards
Tomy

---

### Post by Tomy on 2005-07-04
[QUOTE=ganatronic]...

Tomy, would you be able to show me your xorg.conf file? I'm having problems finding full examples of ones using via unichrome. I mean, in theory all you really need to do is change "vesa" to "via", but there might be something else that I'm missing....
[/QUOTE]

The Device section looks like this:
 ```

Section "Device"
		Identifier      "VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
		Driver		  "via"
		BusID		   "PCI:1:0:0"
		Option		  "DisableIRQ"
		Option		  "EnableAGPDMA"
EndSection"
``` 
 
The options seem to be required on my systems. 

Tomy

---

### Post by Tomy on 2005-07-04
For what it is worth -- here is my 'new and improved' script. Yesterday I got a bag of Ubuntu Hoary cd's in the mail (I plan to pass them around RSN). Today I used one of these official hoary install cd's and this script and got the unichrome driver to work.

```
#!/bin/sh
# You can copy and save this and run it as a script.
# The instructions are all here as comments.
# I am an end-user and know-not what I am doing. Use at your own risk
# Good Luck! Tomy
 
# Unichrome 3d-HOWTO for Ubuntu 5.04 (Hoary)
# These instructions are based on the Unichrome 3d-HOWTO posted here:
# http://sourceforge.net/docman/?group_id=102048 
#
# Step 5. has been changed and now installs an experimental Unichrome Pro driver
# Info on this package and on mythTV and the VIA EPIA motherboards can be found at:
# http://www.csd.uwo.ca/~mfgalizi/debian

# This is how I got tuxracer to work on an MSI K8MM-V motherboard
# (onboard VIA S3 UniChrome Pro graphics)
# This board is designed for the AMD K8 Athlon64 (Socket 754).
# I have a 32bit K7 Sempron cpu installed and run the K7 linux kernel. 
# The old Step 5. worked for me on an MSI KM4AM-V with S3 Unichrome

# This script must be run as root. 
# Maybe you can "sudo" run it but I have a root login and do not use sudo.
# To create a root password just type "sudo passwd" from the command line.
# Then "su" will get you a root login.

## Before running this script edit /etc/sources.list to look something like this:
#
#	deb http://us.archive.ubuntu.com/ubuntu hoary main restricted universe
#	deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted universe

#	deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
#	deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

#	deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
#	deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe

#	# Unichrome Packages (VERY EXPERIMENTAL)
#	deb http://www.csd.uwo.ca/~mfgalizi/debian hoary unichrome
#	deb-src http://www.csd.uwo.ca/~mfgalizi/debian hoary unichrome

## and don't forget to run "apt-get update"

## Before running this script download and extract two files: (see Step 1. first)
#
# file #1: via-20050608-linux.i386.tar.bz2
# can be found here:
# http://dri.freedesktop.org/snapshots/
#
# file #2: opensource_ubranch_20050302.tbz2
# can be found here:
# http://sourceforge.net/project/showfiles.php?group_id=102048

## Make sure you have the development files installed.
# apt-get install build-essential

## Make sure your preferred kernel and headers are installed.
# apt-get install linux-image-2.6.10-5-k7
# apt-get install linux-headers-k7
## If you use a different kernel you will have to edit the script in several places.
  
# Reboot if you have just installed a new kernel and headers.

## And of course, :) you must install tuxracer from the universe repository
## (see /etc/sources.list above)
# apt-get install tuxracer

##### THE SCRIPT STARTS HERE ####### YOU MUST EDIT THE dir= LINE IN STEP 1.#####
# STEP 1. Set the directory where the install files have been extracted
#	 (from the file browser I right-clicked on the file and clicked on "extract here")
#	 (this extracts the files to a subdirectory fileName_FILES) 
# *** edit this line and then run the script *** good luck *** maybe it will work **
dir=/home/tomy/install
#
# STEP 2. Create drm.ko and via.ko
#
cd $dir/via-20050608-linux.i386.tar.bz2_FILES/dripkg/drm/linux-core
make DRM_MODULES="via"
echo "drm.ko and via.ko created"
#
# STEP 3. Copy drm.ko and via.ko to proper directory
#
cd $dir/via-20050608-linux.i386.tar.bz2_FILES/dripkg/drm/linux-core
cp -f drm.ko via.ko /lib/modules/2.6.10-5-k7/kernel/drivers/char/drm/
echo "via.ko and drm.ko copied"
#
# STEP 4. Add via DRM module to the kernel
#
depmod -ae
modprobe via
echo "via DRM module added to kernel"
#
# STEP 5. Replace ubuntu via_drv.o with Unichrome Pro via_drv.o from:
#  http://www.csd.uwo.ca/~mfgalizi/debian
#  These packages also install the XVideo Motion Compensation extension.
#
apt-get install xserver-unichrome libviaxvmc1 libxvmcw1
#
# old STEP 5. Replace ubuntu via_drv.o with unichrome project via_drv.o
#
# mv /usr/X11R6/lib/modules/drivers/via_drv.o /usr/X11R6/lib/modules/drivers/via_drv.o.bak
# cd $dir/via-20050608-linux.i386.tar.bz2_FILES/dripkg/via
# chown root.root via_drv.o
# cp -a via_drv.o /usr/X11R6/lib/modules/drivers
# echo "unichrome project via_drv.o copied" 
#
# STEP 6. Replace ubuntu libGL.so.1.2  with unichrome project libGL.so.1.2 
#
mv /usr/X11R6/lib/libGL.so.1.2 /usr/X11R6/lib/libGL.so.1.2.bak
cd $dir/opensource_ubranch_20050302.tbz2_FILES
chown root.root libGL.so.1.2
cp -a libGL.so.1.2 /usr/X11R6/lib/
echo "unichrome project libGL.so.1.2 copied"
#
# STEP 7. Install "unichrome_dri.o" from the unichromeProject
#
cd $dir/opensource_ubranch_20050302.tbz2_FILES/modules/dri
chown root.root unichrome_dri.so
cp -a unichrome_dri.so /usr/X11R6/lib/modules/dri/unichrome_dri.so
echo "unichrome project unichrome_dri.o copied"
#

#
# end of script
#

# LAST STEP: edit xorg.conf and reboot
echo "you now need to edit /etc/X11/xorg.conf and then reboot"
#
# change the "Device" section to look something like this:
# Section "Device"
#		Identifier      "VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
#		Driver		  "via"
#		BusID		   "PCI:1:0:0"
#		Option		  "DisableIRQ"
#		Option		  "EnableAGPDMA"
# EndSection"
#


```

---

### Post by Rinnan on 2005-07-04
Hey Tomy, thanks for the instructions.  drm is now enabled in my Xorg.0.log, however, when I run glxinfo or glxgears, I get this error message:

```
name of display: :0.0
__driCreateNewScreen - succeeded
glxinfo: ../common/drirenderbuffer.c:44: driNewRenderbuffe                                     failed.
Aborted
```

Closer...  I've mucked with my setup so much trying to get this to work I really have no idea what state everything is at however.  I am considering trying this on a fresh install of Ubuntu.  

Before I do that, however, I want to know if anyone has gotten this to work on a Nehemiah 10000, or another non-"Pro" version of Unichrome?

EDIT:  Got it to work.  Ran Tomy's new script, wch overwrote the mess I created earlier.  Works pretty well -- thank you! :)

---

### Post by Tomy on 2005-07-05
[QUOTE=Rinnan] ...
EDIT:  Got it to work.  Ran Tomy's new script, wch overwrote the mess I created earlier.  Works pretty well -- thank you! :)[/QUOTE]

Great!! glad to know you got my script to work. Half the time it doesnt' work for me;)

---

### Post by ganatronic on 2005-07-05
Yes! This script worked like a dream Tomy. Thanks a lot. I'm so glad to finally get dri working. 

```
3562 frames in 5.0 seconds = 712.400 FPS
```

Tuxracer runs smooth as ice.

---

### Post by Tomy on 2005-07-05
[QUOTE=ganatronic]Yes! This script worked like a dream Tomy. Thanks a lot. I'm so glad to finally get dri working. 

```
3562 frames in 5.0 seconds = 712.400 FPS
```

Tuxracer runs smooth as ice.[/QUOTE]

You are doing better than I am -- 575 FPS on my new setup.

glad it's finally working.

---

### Post by Rinnan on 2005-07-06
[QUOTE=Tomy]You are doing better than I am -- 575 FPS on my new setup.

glad it's finally working.[/QUOTE]

Which makes my experience odd ...

```

1480 frames in 5.0 seconds = 296.000 FPS
```

Much slower than either of you - why should there be such a difference at all? My machine is a "Nehemiah" M10000, with the onboard Unichrome graphics.

Oh well, it works (at some level) and is much better than before. Tuxracer is playable, screensavers work. It's 24bit, which I'm sure makes a difference.

EDIT:  in 16-bit:

```
3027 frames in 5.0 seconds = 605.400 FPS
```

I didn't expect such a big difference...

EDIT2 in 32 bit:

```
1883 frames in 5.0 seconds = 376.600 FPS
```

Curiouser and curiouser.  I guess 24 bit is out.

---

### Post by ganatronic on 2005-07-06
Ah, yes. I forgot to mention that I'm running in 16 bit.

I'll give it a try at 24 and 32, just to see if the results are at all similar to yours, Rinnan ('cause that's pretty bizarre). I'm on an averatec 3250. 


Also, one time I ran glxgears while the terminal window was directly below the gears window, so I had to cover up the gears window to see the data. And I was getting over 5000 fps. That was pretty exciting...until, of course, I realized why I was seeing those numbers.

---

### Post by cdean on 2005-07-18
Anyone got DRI working with a K8N800 board?  I've got an Averatec 3270 that would love to be able to let me enjoy a little Tuxracer here and there.

I tried about a month ago and couldn't get it to work.  My biggest reason for wanting to get the unichrome drivers to work, however, is the proper screen power management.  When X starts/exits, the screen gets all colorful and nasty looking, and I can't power off the screen instead of just blanking it when Xscreensaver comes on.

---

### Post by gray-squirrel on 2005-07-18
I would like to say "thank you" for sharing this information.  It is a valuable timesaver.

Finally, I have a chance to try out the VIA Unichrome drivers with Kubuntu 5.04.  I did follow the steps listed (I didn't run the script, but finished the last three steps by hand after I discovered I didn't need to get the x.org source), and upon reboot, the screen seemed to be better looking.

The only problem is that I'm stuck again at 640x480, and despite my having 16, 24, and 32-bit depths listed in my /etc/xorg.conf file, along with the 800x600 and 1024x768 resolutions listed, they're all ignored.  I also kept the modeline for 1024x768 @ 75 Hz in xorg.conf from when I was using the vesa driver, so it should have still been the default with the new drivers.  But right now, 640x480 is the only option, and I can't change the refresh rate either - which is at 60 Hz.  At least the screen is stable (not fuzzy as it was under the original VIA drivers).  Also, DRI was not enabled in that situation.  :-(   {**Edit**: direct rendering was not enabled, even though DRI appeared to be loaded.}

I'm currently using an Abit VA-20 board, which features the KM-400.

I'm not at home, so I won't be able to post the xorg.conf or Xorg.0.log here until tomorrow morning (Eastern Time).  In the meantime, if you have enough information now to suggest how I can get more choices for resolution and refresh rate, please advise.  I'll try using the via_drv.o file which came with DRI snapshot and see what happens.

Thanks for your help.



p.s. Is using the "common" snapshot at [http://dri.freedesktop.org](http://dri.freedesktop.org) recommended for Unichrome users?

---

### Post by gray-squirrel on 2005-07-19
Never mind, I finally got direct rendering on, but the resolution and refresh rate is still messed up.  However, that is a monitor issue which I will have to deal with separately.

It turned out I missed something when downloading the necessary packages earlier.  So early this morning I went into Synaptic, downloaded the unichrome and libxvmcw1 packages.  At the beginning of package installation a box popped up asking me for the method of direct rendering, and I changed it from "Software" to "Unichrome Pro".  Then the configuration and installation finished several seconds afterward.  I changed the xorg.conf file again, and rebooted to see what happened.  Even though I still had 640x480, I wanted to test to see if DRI was activated.  A look at Xorg.0.log showed that it indeed was.  So, going into a terminal window, I ran glxgears and this is what I got after running it for about a minute or so:

```

1237 frames in 5.0 seconds = 247.400 FPS
1531 frames in 5.0 seconds = 306.200 FPS
2592 frames in 5.0 seconds = 518.400 FPS
6225 frames in 5.0 seconds = 1245.000 FPS
6256 frames in 5.0 seconds = 1251.200 FPS
6041 frames in 5.0 seconds = 1208.200 FPS
4536 frames in 5.0 seconds = 907.200 FPS
```

Not bad for a Sempron 2400+ system.  When the gears moved differently from the way they have been, I knew I was going in the right direction.  By the way, I set aside 64 M out 768 M of RAM for video.  That may also play a part in the frame rate.  I'll see what I get after my monitor is put back in its place.

I can't wait to start playing Foobillard. . .

---

### Post by Lem on 2005-08-10
[QUOTE=Tomy]I've seen this "version mismatch" error before. I just got the S3 Unichrome Pro graphics chip to work on a AMD K8 motherboard using an experimental driver from the unichrome project that someone has packaged for ubuntu.

You can find some info [here.]("http://www.csd.uwo.ca/%7Emfgalizi/debian")

To install this driver you add this to /etc/sources.list
```
# Unichrome Packages (VERY EXPERIMENTAL)
deb http://www.csd.uwo.ca/~mfgalizi/debian hoary unichrome
deb-src http://www.csd.uwo.ca/~mfgalizi/debian hoary unichrome
``` 

and then try this:
 ```
# apt-get update
# apt-get install xserver-unichrome libviaxvmc1 libxvmcw1
```

Tomy[/QUOTE]

This worked a treat on my epia m2-6000e! Thanks
glxgears runs about 3 times faster and video playback is now possible on many files.

I've built this system to test if a SP-1300 board with Kubuntu would a be a usuable system. I've been running Linux for a whole 3 days now, on a very slow processor and wlan - mainly thanks to the info on this site!  :grin:

---

### Post by LongTooth on 2005-08-14
Tomy, first of all let me thank you for all of your hard work. And to the others who contribute. 

I've got two questions. 

First question: On running glxgears here are my results:

:~$ glxgears
849 frames in 5.0 seconds = 169.800 FPS
648 frames in 5.0 seconds = 129.600 FPS
777 frames in 5.0 seconds = 155.400 FPS
647 frames in 5.0 seconds = 129.400 FPS
777 frames in 5.0 seconds = 155.400 FPS
648 frames in 5.0 seconds = 129.600 FPS
647 frames in 5.0 seconds = 129.400 FPS
777 frames in 5.0 seconds = 155.400 FPS
648 frames in 5.0 seconds = 129.600 FPS
777 frames in 5.0 seconds = 155.400 FPS

It doesn't seem as if I have a problem on speed. I wonder if installing this driver will give me much of an improvement over what I'm running at the moment? But I'd like to find out anyway.  And no the  direct rendering NOT on. So maybe proceding with this just might be called for. 

My second question pertains to the script. I'm basically a lazy geek wannbe. So if I fine an auto script that make my like easier, I'm all for it. Be gentle and take me by the hand and tell me how to 'run' your script posted on page #3, dated 07/04/05. I take it that this is the lastes one and the 'bugs' are ironed out? 

Thanks.

---

### Post by Tomy on 2005-08-16
[QUOTE=LongTooth]...
I've got two questions. 

First question: On running glxgears here are my results:
:~$ glxgears
849 frames in 5.0 seconds = 169.800 FPS
648 frames in 5.0 seconds = 129.600 FPS
777 frames in 5.0 seconds = 155.400 FPS

It doesn't seem as if I have a problem on speed. I wonder if installing this driver will give me much of an improvement over what I'm running at the moment? But I'd like to find out anyway. And no the direct rendering NOT on. So maybe proceding with this just might be called for. [/QUOTE]
Speed is relevant to what apps you want to run. OpenOffice runs fine without accelerated video but if you want to edit home movies or run games it may be worth trying to install dri.

[QUOTE=LongTooth] ...
My second question pertains to the script. I'm basically a lazy geek wannbe. So if I fine an auto script that make my like easier, I'm all for it. Be gentle and take me by the hand and tell me how to 'run' your script posted on page #3, dated 07/04/05. I take it that this is the lastes one and the 'bugs' are ironed out? 
Thanks.[/QUOTE]
No, the bugs are not ironed out. This is more of a guide to what might work depending on your hardware. You should really be familar with editing xorg.conf and killing and restarting gdm and xorg if you want to try this. 

If you want to live on the cutting edge you might try and set up a separate partition and install Ubuntu Breezy. The via unichrome drivers almost work in Breezy and I am hopeful by next month things will be ironed out.

Tomy

---

### Post by ganatronic on 2005-08-17
Everything Tomy says it true. But you simply can't play tuxracer with an fps like that. It's the plain simple truth, and I hate to be the one to have to jap the blunt shiv of truth straight into your kidney...

However Longtooth, if you're prepared to become a less-lazy geek wannabe (e.g. wing the script, and possibly mess things up and then have to figure out how to fix it) and you don't know how to simply run it, then just copy the text into gedit, edit those specifics within the steps that pertain to your system (e.g. directory in step 1 should be the directory where you save this file you're making; in step 3 change the kernel info on the second line to match whatever kernel you have), and then save the file with the extension .sh.

Then navigate to the directory in a terminal and type "sudo sh myscriptiscool.sh"
Then do the whole cross your fingers thing that real geeks do. Then edit xorg and (if you don't know how to kill things) restart your computer. Or just wait a few months. And read the script carefully, because there might be more to edit - I'm too tuxracered-out to remember.

---

### Post by LongTooth on 2005-08-17
ganatronic, I like your statement, ¨..Then do the whole cross your fingers thing that real geeks do.¨ Over the years I´ve taken the easy way out. But sometimes there is no easy way. So I´ve been forced to learn, whether I want to or not. And this is what make me learn more about Linux. God! I remember the first time I popped a Linux CD in a PC. Shudder! But I dirgress. 

I´ve got Breezy installed on a thrown down 10Gb HD and I´ll try this out. Thanks to Tomy for the hard work and you for the push.

Later,

---

### Post by Tomy on 2005-08-17
[QUOTE=LongTooth]ganatronic, 

I´ve got Breezy installed on a thrown down 10Gb HD and I´ll try this out. 

Later,[/QUOTE]
I am not sure the script will work in Breezy which has a new and improved modularized (sp) xorg. If you run the 2.6.10-5 kernel it may work. The newer 2.6.12 (or whatever) kernel I believe has the drm stuff (step 2) already there.

Short story - I have only gotten the script to work in Hoary. I have screwed up Breezy several times and am currently running the vesa driver.

Tomy

---

### Post by phibxr on 2005-08-27
I tried to run this script (with the k7-kernel as I have an Acer Aspire 1362LC with an AMD Sempron 2800+), but when I added the Via-device to xorg.conf and rebooted I was greeted with a flicker, a black screen and a hard lock-up.

Any suggestions?

---

### Post by undeadsoldier on 2005-09-01
Hi all,

I know this is strange for my first post and all, and I didn't think it was wise to create a new thread for my post, so here goes.

Can anybody create both drm.ko and via.ko modules for me, i have absolutely tried effortly to compile the kernel and tried pretty much everything, but no luck ](*,)

Please, can anybody help me, I am running the 2.6.10-5-386 kernel on a EPIA SP-1300. Thank you in advance to anybody that helps me in anyway !!

---

### Post by suoko on 2005-09-02
command make DRM_MODULES="via"  ends up with folowing error:

rm -f linux
ln -s . linux
make -C /lib/modules/2.6.10-5-k7/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[1]: Entering directory `/lib/modules/2.6.10-5-k7/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.10-5-k7/build'
make: *** [modules] Error 2

I followed the script step by step.
what can I do?

---

### Post by suoko on 2005-09-03
I successfully created the driver and completed the script. Unfortunately when I try the via driver  the whole pc freezes  leaving me with a black screen. I then have to brutally shutdown the pc and when I reboot no xorg log has been created.
Any hints?

---

### Post by suoko on 2005-09-03
1

---

### Post by gray-squirrel on 2005-09-06
[QUOTE=suoko]I successfully created the driver and completed the script. Unfortunately when I try the via driver  the whole pc freezes  leaving me with a black screen. I then have to brutally shutdown the pc and when I reboot no xorg log has been created.
Any hints?[/QUOTE]

If everything is done properly, and the computer still crashes, there's one other thing to try.

I followed the directions at the Unichrome site, and even went to the trouble of downloading updates to recompile, etc. and either couldn't get the drivers to work or ended up running a program which crashed the computer (especially those wonderful OpenGL screen savers).

I stumbled onto something yesterday in one of the Slackware forums (I wish I had written down the site address), where someone had problems getting DRI to work.  I don't think his computer crashed, but he did say he found something.  He said he had to add the following line to his xorg.conf file:

```
          Option          "AllowInsecureDRI"
```

and everything was fine after that.

He said the reason for the addition was that in late 2004 someone had discovered there were possible security issues with DRI, so the developers went to work on fixing the problems.  I don't remember the rest of the story, but they did allow for operation under the old way, hence the new option listed above.

I tried it as well, and now it appears 3D acceleration will stick for a long time (at least until the Breezy Badger release is out next month).  The OpenGL screen savers work and don't crash the computer now!

---

### Post by phibxr on 2005-09-26
Has anyone been able to get their Unichrome chipsets working under Breezy?

I get this in the first step (issuing the make-command without the script):

```

make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-k7'
  CC [M]  /home/phibxr/Desktop/unichrome/dripkg/drm/linux-core/drm_auth.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/phibxr/Desktop/unichrome/dripkg/drm/linux-core/drm_auth.o] Fel 127
make[1]: *** [_module_/home/phibxr/Desktop/unichrome/dripkg/drm/linux-core] Fel 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-k7'
```

Is GCC 3.4 required to compile the modules?

---

### Post by Tomy on 2005-09-28
[quote=phibxr]Has anyone been able to get their Unichrome chipsets working under Breezy?

I get this in the first step (issuing the make-command without the script):

```

make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-k7'
  CC [M]  /home/phibxr/Desktop/unichrome/dripkg/drm/linux-core/drm_auth.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/phibxr/Desktop/unichrome/dripkg/drm/linux-core/drm_auth.o] Fel 127
make[1]: *** [_module_/home/phibxr/Desktop/unichrome/dripkg/drm/linux-core] Fel 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-k7'
``` 
Is GCC 3.4 required to compile the modules?[/quote] Well.. no. I tried but gave up. In Breezy the xorg file locations are a little different. Someone should start a thread in the Breezy forum.;)

But the answer to your error message is:

sudo apt-get install gcc-3.4
 
or something like that. 'Out of the box' Breezy only has gcc 4.0 and you have to install the older versions.

Tomy

---

### Post by xethm55 on 2005-10-01
I was able to get this to work under Breezy.   It seems that some of the directories do not exist.  However, all i did was create them and then copy the files to them manually, using the script contained in this thread as a guide.  Oh, you will have to install build-essential AND GCC-3.4 in order to compile the unichrome drivers.  the VIA support for XORG, i believe is already compiled into it.  So you will not need to install a special xorg-server or recompile the XORG source.  This seemed to work for me.  However I am running on a custom server install with XFCE at the moment, do not know if that matters, but it might.  I did see a small (about 25 FPS) gain in performance between hoary and breezy, using glxgears.  I know that it is not a great bench mark, but it works for me.

P.S.  I did start a thead about this a while back.  Goto 
[http://www.ubuntuforums.org/showthread.php?t=67458&highlight=xethm55](http://www.ubuntuforums.org/showthread.php?t=67458&highlight=xethm55)

---

### Post by wezlo on 2005-10-17
[QUOTE=Tomy]The Device section looks like this:
 ```

Section "Device"
		Identifier      "VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
		Driver		  "via"
		BusID		   "PCI:1:0:0"
		Option		  "DisableIRQ"
		Option		  "EnableAGPDMA"
EndSection"
``` 
 
The options seem to be required on my systems. 

Tomy[/QUOTE]

Tomy, what happens when you don't have those options enabled?
I got dri working, but if I have it turned on my system freezes when I try to start up my network interfaces

---

