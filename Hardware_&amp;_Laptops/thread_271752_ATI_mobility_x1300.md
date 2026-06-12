---
title: "ATI mobility x1300?"
date: 2006-10-05
forum: Hardware &amp; Laptops
---

### Post by jinxen on 2006-10-05
Hi! Have someone got the x1300 card working good? I installed the ati drivers (it said to support xorg 7.1 in the install instructions) Seemed to work out just fine, resolution changed. But the 3d acc seems to be really messed up? When i run glxgeras, the geas move, but very very very slow. It almost went better when i had with the vesa driver.

Someone who has had the same problem? Or is it just that ati sucks so bad in linux :P

Regards, Tommy

---

### Post by Crooksey on 2006-10-05
I have the drivers installed, but my glxgears suck aswell, no idea what it is :(

---

### Post by jinxen on 2006-10-05
ooh, ok :) Maybe the hardware acc doesnt work? But do you get a "line" under you pointer sometimes? I get one, but it dissapears somtimes, but then i comes back again. Any idea?

---

### Post by Crooksey on 2006-10-05
I was kinda hoping someone here could point me in the right direction >>

---

### Post by inktaylor on 2006-10-05
I have gotten this to work pretty well on my Dell E1505 laptop with the x1300 card.  I even got XGL/compiz working as well after the latest update.  The method that I used was to install the propriety driver from ati's website.  I can't seem to find the guide that I used, but this looks pretty similar as far as setting up the video driver goes:  [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by mattyj on 2006-10-05
Check this out.


[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by jinxen on 2006-10-06
Hi! I tried the url:s and did what was written. But It still wont load it. In the Xorg log file the loading of the module is fine, it finds the card x1300, but when it comes to dri it fails and loads 2d acc, and when i run fglrxinfo i get 
> Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


I will post the log file + xorg.conf file below.. I really want to get this to work :) I really appriciate every help i can get!

[http://noshitsherlock.se/Xorg.0.log](http://noshitsherlock.se/Xorg.0.log)

> Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "aticonfig-Device[0]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


---

### Post by jinxen on 2006-10-08
None who have the time to look at the files and help me? ;)

---

### Post by tuke81 on 2006-10-08
Well I don't have ati(luckily I have nvidia). But this line in xorglog seems to be reason:
> (II) fglrx(0): Composite extension enabled, disabling direct rendering

So you have to disable composite extension. Add this lines to bottom of the xorg.conf
```
Section "Extensions"
        Option "Composite" "false"
EndSection
```

After that restart x, and check if 3d is working(direct rendering: Yes)
```
glxinfo | grep direct
```

---

### Post by jinxen on 2006-10-09
Hi! Thanks for taking the time looking through my log file! But that didn't work :(. Ohhhh, i would have liked to have a nvidia card aswell :P Do you have any other ideas? ](*,) 

> glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect


If i look in the log file now  it says:

> (**) Extension "Composite" is disabled

So that must be right anyway :P Also i run the 8.29.06 drivers from ati.

also i noticed:

> [drm] failed to load kernel module "fglrx"
(WW) fglrx(0): Failed to open DRM connection

---

### Post by tuke81 on 2006-10-09
Sad to hear. How many different ways have you tried to installing them. What says command **dmesg | grep fglrx**. Hmm 8.29.06 driver that must be use [*offical drivers*]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Dapper_Manually").

And what disables direct rendering now?
flashback:
> (II) fglrx(0): Composite extension enabled, disabling direct rendering

Or you just might try to install grafics card guru tseliot's *[drivers]("http://www.ubuntuforums.org/showthread.php?t=255929")*(note if you blacklisted fglrx you have to remove it from blacklist).

---

### Post by jinxen on 2006-10-09
Getting tired of this now :P hehe.. I dont really know what ticks it off.. But i can quote the stuff before direct rendering is disabled. I attatched the log file to, just change the file extension to view it ;)

> (WW) fglrx(0): Failed to open DRM connection

> (II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xd8000000 FBMappedSize: 0x03fe0000
(II) fglrx(0): Splitting WC range: base: 0xd8000000, size: 0x3fe0000
(II) fglrx(0): Splitting WC range: base: 0xda000000, size: 0x1fe0000
(II) fglrx(0): Splitting WC range: base: 0xdb000000, size: 0xfe0000
(II) fglrx(0): Splitting WC range: base: 0xdb800000, size: 0x7e0000
(II) fglrx(0): Splitting WC range: base: 0xdbc00000, size: 0x3e0000
(II) fglrx(0): Splitting WC range: base: 0xdbe00000, size: 0x1e0000
(II) fglrx(0): Splitting WC range: base: 0xdbf00000, size: 0xe0000
(II) fglrx(0): Splitting WC range: base: 0xdbf80000, size: 0x60000
(==) fglrx(0): Write-combining range (0xdbfc0000,0x20000)
(==) fglrx(0): Write-combining range (0xdbf80000,0x60000)
(==) fglrx(0): Write-combining range (0xdbf00000,0xe0000)
(==) fglrx(0): Write-combining range (0xdbe00000,0x1e0000)
(==) fglrx(0): Write-combining range (0xdbc00000,0x3e0000)
(==) fglrx(0): Write-combining range (0xdb800000,0x7e0000)
(WW) fglrx(0): Failed to set up write-combining range (0xdb000000,0xfe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xda000000,0x1fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd8000000,0x3fe0000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1408,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1408,1050) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled

---

### Post by jinxen on 2006-10-09
I tried installing the other drivers you named, but the same there to... But the fireglcontrol looks better now, with fonts and etc ;) Always nothing.. hehe. I still get

> jinxen@skynet:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


btw i got 1400x1050 to work now after installing the driver you suggested :P But still the same with dri... :(

---

### Post by jinxen on 2006-10-09
I solved it! I mailed a guy Felipe Alfaro Solana just on random seeing he just made a remark in one thread i was reading in.

> 
On 10/9/06, Felipe Alfaro Solana <felipe_alfaro@linuxmail.org> wrote:

    Try the following:

    # mv /etc/modprobe.d/fglrx /tmp
    # reboot

    I had problems with Edgy not loading the fglrx module which turns out
    causes problems and doesn't allow DRI to work.


Now it works perfect! :) OOO, i am so happy.. hehe ;)

> jinxen@skynet:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300 Generic
OpenGL version string: 2.0.6065 (8.29.6)


---

### Post by jinxen on 2006-10-12
Now its not working again :( I updated edgy, and after that the packages broke. Kernel version does not match module version. ATI should be shut down, and their factorys burned down to the ground ](*,) 

Regards, Tommy

> (II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.28.8
(II) fglrx(0):     Date: Aug 17 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work

---

### Post by xurizaemon on 2006-10-12
Did you see this
> ```

$ sudo dpkg -i *.deb
$ sudo module-assistant prepare,update
[B]$ sudo module-assistant build,install fglrx-kernel
$ sudo depmod
[/B]
```
You need to repeat last step - building kernel modules - everytime you upgrade kernel. 

in [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) ?

I still haven't got my Radeon 9550 3d going. Aie! I wish mine worked for a bit at least :) But, I only installed it last night ... at least big desktop works!

---

### Post by jinxen on 2006-10-16
Got it working again, but now i skipped the ati official drivers and went with the ones that follow x-org. Don't really know why the official ones just broke after some minor updates. But now with 8.28.8 it works again :P

---

### Post by galroth on 2006-12-21
jinxen, I'm at the same place you were, right before you ran this:
```
mv /etc/modprobe.d/fglrx /tmp
```
When I ran that, I received a message "No such file or directory"

---

### Post by sqken on 2006-12-23
> **jinxen said:**
> Got it working again, but now i skipped the ati official drivers and went with the ones that follow x-org. Don't really know why the official ones just broke after some minor updates. But now with 8.28.8 it works again :P

Would you please to share how did you solve it?
Can you write a list down?
Thanks in advance:)

---

