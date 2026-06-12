---
title: "Video Driver for Intel D201GLY (SiS662 - Mirage*1)"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by kmseck on 2007-06-03
Hi,
I have been struggling with my new IntelD201GLY motherboard's video display, after installing Ubuntu v7.04, distorted display at 1024x768, can only run at 800x600, Tested with various settings, but failed.

Kindly advise. Thanks.

KMS

---

### Post by GreenPC on 2007-06-05
Hi all - I am also having issues with the SiS662 graphics under Ubuntu 7.04  - running at 800x600 is acceptable - but any higher any vertical 'noise' is seen on the screen - as resolution is incresed so is the 'noise' .

changed RAM, PSU and HDD, all to no avail...  

This MUST be a workable solution (as Dell have done it OK) - so any recommendations are welcome.

We manufacture and supply ultra reliable, low cost, green systems, and getting Ubuntu running well, is important for our range of TGV ([www.tranquilpc.co.uk/TGV.htm](www.tranquilpc.co.uk/TGV.htm)) systems.

Any advise much appreciated.

---

### Post by NBaran on 2007-07-06
I was going to buy this board next week. It does not support 1280x1024, right?

---

### Post by PeteZA on 2007-07-07
Hi there,

This doesnt help at all but, i am having the same problems with a cheap as hell ecs board. I am a COMPLETE newb to linux, but i searched for a linux driver for this chipset and it does not appear that there are any. could this not be the problem?

Pete

---

### Post by mccann.matt on 2007-07-19
Hello,

I'm having a similar issue with the "vertical" noise and flickering at resolutions above 800 x 600. I have a D201GLY motherboard that has a SiS 662 -Mirage*1 graphics engine. I am using an ASUS AL1917 LCD Monitor. Any help on this would be MUCH appreciated. Anyone with a solution, please email me at [email]mccann.matt@gmail.com[/email].

Thanks

---

### Post by HowardDrake on 2007-08-22
> **NBaran said:**
> I was going to buy this board next week. It does not support 1280x1024, right?

Actually with Win2k it ran with 1280x1024 just fine, so I'm sure the chipset can handle it, just the drivers suck.

---

### Post by dannyk6 on 2007-08-29
Hi,

Same problem here. Have the Intel D201GLY motherboard with the SiS 662 -Mirage*1 graphics engine.  I'm using a 19" Dell Monitor and get vertical lines through my screen at 1280x1024 or higher.  1024x768 is usable, but there are very faint lines and flickering. Any suggestions would be appreciated!! Thanks!

---

### Post by HowardDrake on 2007-09-01
Well I actually figured it out somewhat by accident. In my desire to try LinuxMCE I tried loading Kubuntu 7.04 on my D201GLY and instead of saying start normally, I told it to start in "safe graphics" mode.

Lo and behold, it comes up rock solid in 1280x1024 on my 17" LCD, as a matter of fact I'm typing in my reply in it right now. I checked and its running the "vesa" driver instead of the "sis". Next up is a HD install, and I'm going to configure X to use the "vesa" driver there. If its solid, I'll report back. It's funny that the "sis" driver looks like crap, but the "vesa" driver is perfect :)

:lolflag:

Just FYI....

---

### Post by dannyk6 on 2007-09-03
Great news! If that works please let us know what you did (I'm still a n00b). Thanks!

---

### Post by PeteZA on 2007-09-06
Ok, so it appears to work if you run> sudo dpkg-reconfigure xserver-xorg

and instead of using the sis driver, select the vesa driver (its one of the first thing you configure) and just follow the rest of the steps. At the end, restart, and it works.
 Thanks to HowardDrake for the idea, works like a charm.

---

### Post by HowardDrake on 2007-09-12
You are quite welcome, hopefully it will get better in the future. This little Intel board has a ton of potential.

---

### Post by steven_ellis on 2007-09-20
Anyone tried to get the S-VIdeo out working under Linux on these boards? Then it might make an ideal MythTV Frontend.

---

### Post by rhealy on 2007-09-22
> steven_ellis: Anyone tried to get the S-VIdeo out working...?

I am researching this board for use as a MythTV front end. I don't have an answer to your question but I do have some information. 

According to [intel ]("http://www.intel.com/products/motherboard/D201GLY/configs.htm") version LAD201GLYLT of this board comes with S-Video out. Unfortunately, the only version I can find for sale right now is the BLKD201GLYL. If I manage to find a LAD201GLYLT for less than $95 USD I'll definitely be giving it a try.

---

### Post by forumworx on 2007-10-04
Not sure the VESA driver is what you want.

Sure it may provide teh resolution needed but will not provide the hardware acceleration that the SiS driver would provide.


From another board: [http://forums.anandtech.com/messageview.aspx?catid=29&threadid=2069391&enterthread=y]("http://forums.anandtech.com/messageview.aspx?catid=29&threadid=2069391&enterthread=y")


"On the Linux side, the frame buffer mode or just vesa works ok, with a max of 1024-768 resolution. At least with SuSE 10.2 and 10.3, while it was detected ok, the video driver used caused major tearing on the screen. If you install the driver from Intel's site by using rpm -if , to force it to overwrite the current driver, it solves the issue. Sound works ok. "


Problem is I cannot find the Linux drivers Intel provides for this board.


This thread: [http://www.2x.com/forums/viewtopic.php?p=6081&sid=e219f88ca2d8178f92e809221b4634f1]("http://www.2x.com/forums/viewtopic.php?p=6081&sid=e219f88ca2d8178f92e809221b4634f1")

Supposedly they made the drivers available @ [http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2773&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21]("http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2773&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21")


Anyone know where we can get the released drivers for this board?

Please post a link.

Thanks

---

### Post by HowardDrake on 2007-10-04
No argument that a proper Intel driver would be tons better than using the "vesa" driver, but until they provide one, the "vesa" driver is a lot more useful than the POS  "sis" driver.

](*,)

](*,)

---

### Post by forumworx on 2007-10-05
From the article I mentioned, it appears that Intel at one point did provide the drivers.

It's a matter of getting them.

I'll send an email to Intel regarding this, lets see what they say.

In the meantime, we shoudl be scouring the net for this driver. I'll post a link once we get info.

L8tr

---

### Post by skiselev on 2007-10-05
sis_drv.so from SuSE10.2 rpm package works for me (on Gutsy Gibbon/Ubuntu 7.10).

Here is the URL for downloading RPM package from Intel:
SuSE 10.2 driver: [http://downloadmirror.intel.com/13374/eng/4180_sis_drv_suse_10_2-1.0-021307.i586.rpm]("http://downloadmirror.intel.com/13374/eng/4180_sis_drv_suse_10_2-1.0-021307.i586.rpm")

You can use rpm4cpio + cpio to extract /usr/lib/xorg/modules/drivers/sis_drv.so from RPM packages. Replace your /usr/lib/xorg/modules/drivers/sis_drv.so with extracted file (make a backup of original file first!)

---

### Post by HowardDrake on 2007-10-05
> **skiselev said:**
> sis_drv.so from SuSE10.2 rpm package works for me (on Gutsy Gibbon/Ubuntu 7.10).

Here is the URL for downloading RPM package from Intel:
SuSE 10.2 driver: [http://downloadmirror.intel.com/13374/eng/4180_sis_drv_suse_10_2-1.0-021307.i586.rpm]("http://downloadmirror.intel.com/13374/eng/4180_sis_drv_suse_10_2-1.0-021307.i586.rpm")

You can use rpm4cpio + cpio to extract /usr/lib/xorg/modules/drivers/sis_drv.so from RPM packages. Replace your /usr/lib/xorg/modules/drivers/sis_drv.so with extracted file (make a backup of original file first!)

Excellent work! Do you get any of the Compiz-Fusion effects with the SIS driver? Also, I'll try this this afternoon and I'll post a quick HOWTO if successful for anyone else :)

---

### Post by forumworx on 2007-10-09
Great job guys getting this info.

I'm sure this will help all the others going mad over the driver problem.

I'm not sure how you found it but you did ;)

I'll be posting info on ther sites as well, put this beast to rest.

---

### Post by forumworx on 2007-10-09
> **HowardDrake said:**
> Excellent work! Do you get any of the Compiz-Fusion effects with the SIS driver? Also, I'll try this this afternoon and I'll post a quick HOWTO if successful for anyone else :)


Never heard of Compiz/Fusion niiiice stuff. I'd love to have time to fudge around with this stuff.

---

### Post by forumworx on 2007-10-09
Heres some more info:

[http://www.winischhofer.eu/linuxsispart4.shtml#download]("http://www.winischhofer.eu/linuxsispart4.shtml#download")


This gentlemen has been developing this... SiS/XGI graphics chipsets and X.org/XFree86/Linux


Source available for compilation.


1. The Premium X.org/XFree86 driver (pre-compiled = binary)

(2007/10/06) Despite of what is written below: Development is ceased. The source of the Premium version is available for download here. THERE IS NO SUPPORT WHATSOEVER FOR THIS CODE. A BINARY IS NOT AVAILABLE.

The Premium Version has the following features not found in the Free Version*:

    * Hardware accelerated display/screen rotation support, including support for video playback (315 series only; 180 degree rotation and video playback in rotation mode only supported on SiS M650/651, 330, 661/741/760, XGI V3XT/V5/V8). [Requires X.org 6.9/7.0 or later for optimum performance]
    * Real CRT1/VGA and CRT2/LCD hotplugging, redetection and modelist rebuilding; if you hotplug a VGA monitor (or projector or any other analog device) which is DDC2-capable, the driver can detect this, rebuild its modelist and adapt it thereby to the new monitor's frequency capabilities. The same applies to hotplugging LCD panels.
    * Advanced video blitter Xv adaptor (including scaling support)
    * Advanced Xv video support for overcoming most overlay size/dotclock/etc limitations/restrictions (only on SiS M650/651, 661/741/760, 330, XGI V3XT/V5/V8).
    * Screen enlargement after server start: For example, if your LCD is 1280x800 and you start X, all modes beyond this resolution are usually not available afterwards. The Premium version allows switching to larger modes (such as eg 1280x1024) later, if you, say, switch from LCD to a VGA monitor. (Not supported in MergedFB mode.) [Requires X.org 6.9/7.0 or later for optimum performance]
    * Advanced MergedFB mode display device placement specification, including swapping (reversing) the relative position for specific metamodes.
    * Optional: TV (analog) copy protection support for SiS video bridges. (Available for companies only)
    * Optional: Customized LCD support for ICOP/Vortex86 or other embedded boards
    * Optional: Other customizations (upon request; hardware sample eventually required)
    * Eventual bugs might be fixed quicker than in the Free Version.
    * And for those who unfortunately can't read: No, the premium version does not support DRI(OpenGL).

Features named as "optional" are subject to a separate agreement and a separate fee. Extended support is available upon request.

(* Note that some of these features might at a later time show up in the Free Version as well as development progresses.)

---

### Post by forumworx on 2007-10-09
Latest from 2x.com site - [http://www.2x.com/forums/viewtopic.php?p=6360#6360]("http://www.2x.com/forums/viewtopic.php?p=6360#6360")


thanks to nzsteve

"Ive uploaded the Redhat4 and Fedora5 drivers to [http://www.megaupload.com/?d=1S55LHGM]("http://www.megaupload.com/?d=1S55LHGM")

The intel downloads for them seem to have disapeared.

I never for them working, so let me know if you have more luck!

steve"

---

### Post by skiselev on 2007-10-10
sis premium driver won't compile as it is on Ubuntu 7.10, due to version numbering changes (driver uses  XORG_VERSION_CURRENT >= XORG_VERSION_NUMERIC in macros, and version of Xorg now 1.3.0 instead of 7.1.0+) but this is relatively easy to fix. Another problem - xorgGetVersion() function is no longer supported. At least I am getting something like "symbol not found".

After all modifications, driver compiles and works properly on SiS662. It seems that some support for DRI is also included in driver, but I didn't tested it yet.

---

### Post by PeteZA on 2007-10-10
> **skiselev said:**
> After all modifications, driver compiles and works properly on SiS662. It seems that some support for DRI is also included in driver, but I didn't tested it yet.

Hi there, great work, any chance you post a bit more of a detailed howto on this so that the noobs like me can get it to work too :) (btw, I am on Feisty, if that makes a difference)

---

### Post by skiselev on 2007-10-13
Here is the compilation procedure. It works for me on Ubuntu 7.10 beta.

1. Prerequisites: development packages (gcc, x11proto-*-dev, *mesa-dev, etc.), backup your current driver and Xorg configuration.
2. Download sisp.tar.gz from here: [http://www.winischhofer.eu/linuxsispart4.shtml#download](http://www.winischhofer.eu/linuxsispart4.shtml#download)
3. Download my patch (see attachments)
4. Unpack / patch / compile / install:

$ mkdir sisp
$ cd sisp
$ tar zxf ../sisp.tar.gz
$ patch -p1 < ../sisp_xorg_version.txt
$ ./configure --prefix=/usr
$ make clean
$ make
$ sudo make install

5. Restart

Status of driver's features:
- 2D acceleration (XAA) - works
- 2D acceleration (EXA) - crashes then starting gnome terminal, and probably some other programs
- 3D acceleration (DRI) - not supported.
- XVideo - overlay method - not usable, glitches
- XVideo - blitter method - works. Add 'Option "XvDefaultAdaptor" "Blitter"' to 'Device' section of your /etc/X11/xorg.conf file, to use blitter method by default

So, not everything is working, but still it's better than current Xorg's SiS driver (no noise, XV works).

---

### Post by diimka on 2007-10-16
Hi all,

could anyoe who was enough lucky to get this driver -- send it to me, for example, by dimka at pervushin dot msk dot ru ? Unfortunately, link from [http://www.winischhofer.eu](http://www.winischhofer.eu) does not respond...

TIA!

---

### Post by Yurand on 2007-10-16
Can anyone place sisp.tar.gz driver on ftp/http?

---

### Post by PeteZA on 2007-10-16
Thanks skiselev for the reply, 

I am unfortunately a bit of a noob, and can't seem to get your instructions to work. I am getting errors with make....

any ideas?

---

### Post by skiselev on 2007-10-16
I've posted sisp.tar.gz, my patch, and binary driver for Xorg 7.2 / Ubuntu 7.10 here: [http://cs.haifa.ac.il/~skiselev/]("http://cs.haifa.ac.il/~skiselev/")

---

### Post by ccantaga on 2007-10-17
I am having the same problem, and am trying to compile the drivers as per skiselev's instructions, and having a few build issues.

However, I am wondering if this is even necessary for me. I am using this board for a homemade digital picture frame, and so far everything else is working. The vesa drivers are working, but they won't allow me to get the 1680x1050 resolution that my monitor can do. All I really need however, is to be able to display 2D pictures to the monitor. Are there generic drivers other than the vesa driver which will allow more flexibility with screen resolutions? Once this is running, I don't even plan on running xwindows.

Thanks,
Chris

---

### Post by HowardDrake on 2007-10-17
Fortunately my D201GLY is going to a non-widescreen display. I think I'll stick with the vesa driver, I'd try the new one but if I don't get Compiz goodness what's really the point?:-|

---

### Post by skiselev on 2007-10-17
Well... one of the reasons, at least to me, is XVideo extension (meaning that I can see full-screen movies). Other reasons: 2D acceleration, non-standard/wide display resolution...

BTW, folks with compile problems: Feel free to send me a private message or leave a post in the thread with error message included. I'll try to help. ;-) But before doing that, make sure that you have all needed development packages installed. If you're getting an error message about missing file or library, probably you missed one of these packages.

---

### Post by ccantaga on 2007-10-17
I actually did manage to get it compiled. I was missing one of the development packages that were needed.

However, now when I try to startx, I just get a blank screen. The error has to do with xorgGetVersion being an unidentified symbol. I know you mentioned in an earlier post that you encountered this and managed to work around it.  Do you mind expanding on that a little?

Thanks,
Chris

---

### Post by jlewin on 2007-10-22
Last week while trying the Gutsy beta on my new motherboard I also ran into this issue. After troubleshooting for way too long I finally came across an article which described a fix for the existing SIS driver. I wish I had bookmarked it so I could give due credit, but basically it pointed out that dropping the color depth down to 16 bit resolved most of the problems. I'm not too savvy yet with linux but the following seems fairly effective:

[LIST=1]
[*]Edit the .conf file
[INDENT]$ sudo gedit /etc/X11/xorg.conf[/INDENT]
[*]Change both **"24"** values to **"16"** under the "Screen" section
[*]Save and Exit
[*]Log Off
[/LIST]

The one catch is the UI tool resets the .conf file to 24 every time you use it. Just make sure to dial in the preferred display settings before you edit the file and change the color depth manually. Maybe there's a way to set the color depth from the UI?

---

### Post by LasVegas on 2007-10-22
I had a problem with X failing to start with the Winischhofer premium version of sis_drv.so.  I have the D201GLY MB.  I tried the precompiled version of sis_drv.so (link above), and also compiled my own with Gutsy, with the same result.  After some thrashing around, I identified the problem as the EDID probe of my monitor.  So I started X with the monitor disconnected, and it started o.k.  I.e., after X started, I plugged the monitor back in again to find a nice X with Blitter and tvtime/xine that scale properly.  Screen is 24 pixel?(=32 bit?), 1280x1024, with no apparent problems (other than having to unplug the monitor before starting X).

So, I'd have to say that there is a bug in the EDID probe.

(I tried the option:  "         Option          "NoDDC"     "1"    " set in the Device section, but it seems to have made no difference.)

---

### Post by Mr_J on 2007-10-23
Wow, LasVegas, you're a lifesaver.  I've been battling the D201GLY2 board for a couple of days now wondering why I couldn't get the Ubuntu 7.10 instructions working...Tried your monitor unplug workaround, and it worked great.  Thanks!

---

### Post by jackobean on 2007-10-23
Hi all
I havent tried for a while, but previously attempted getting the winischhofer drivers working for my sis-m650 on feisty. has anyone else managed to succeed? i would love to get compiz working :)
I'm not sure if skislev's patch will work for feisty, but if someone could tell me how to modify it that would be splendid.

---

### Post by LasVegas on 2007-10-24
>Hi all
>I havent tried for a while, but previously attempted getting the winischhofer drivers 
>working for my sis-m650 on feisty. has anyone else managed to succeed? i would 
>love to get compiz working I'm not sure if skislev's patch will work for feisty, but if someone could tell me how 
>to modify it that would be splendid.

I first tried the binary driver "premium" on feisty and found that there was an X version mismatch of some sort.  So I think that binary driver is DOA for feisty.  When I ran into that I upgraded to Gutsy (no problems to speak of, other than the 6 hrs downloading it took) and then got the "premium" version working.

The version from the Intel rpm works o.k. on fiesty, but it does not work all that well for tvtime or DVDs.

I suspect if you compiled the premium version yourself on fiesty, and tried the disconnect the monitor trick above, it might work.  I think I had compiled this on fiesty and thought it didn't work, which is why I upgraded to Gutsy.  But perhaps it works o.k. on feisty if started with the monitor disconnected.

Anyone know how to stop the EDID probe?  As near as I can tell that isn't possible; there is such an option for nvidia drivers, but not for sis.  Pretty annoying, and probably not that healthy for a monitor, to be disconnecting it all the time.

Anyone with care to develop a patch to add to the one above? Hint, hint...:)

---

### Post by Yurand on 2007-10-24
> **LasVegas said:**
> >Hi all
Anyone know how to stop the EDID probe?  As near as I can tell that isn't possible; there is such an option for nvidia drivers, but not for sis.  Pretty annoying, and probably not that healthy for a monitor, to be disconnecting it all the time.

Anyone with care to develop a patch to add to the one above? Hint, hint...:)

I don't really understand what do you mean, but premium driver crashed Xorg with one of my monitor. I had to disable internal ddc to make it running. Maybe this patch help with you problem.

I am not ubuntu user, so I din't try this on ubuntu. But I belive skiselev instruction should be updateted to this.

$ mkdir sisp
 $ cd sisp
 $ tar zxf ../sisp.tar.gz
 $ patch -p1 < ../sisp_xorg_version.txt
 $ patch -p1 < ../disable_internal_ddc.txt
 $ ./configure --prefix=/usr
 $ make clean
 $ make
 $ sudo make install

---

### Post by LasVegas on 2007-10-24
Thanks for the patch - that seems to have bypassed the problem at least.  I tried attaching my sis_drv.so with this patch, but it is too big, alas.

I spoke too soon - I attach a "strip"'ed version of the driver binary, which is much smaller and still seems to work o.k. (using it now).  No guarantees, of course; you get what you pay for.  This has been compiled on Gutsy and includes the patch to skip the DDC probe.

---

### Post by jackobean on 2007-10-26
sorry for being such a n00b, but i'm having some problems (os=Gusty, chipset = m650)
1. running configure has some dependencies problems - package 'xorg-server' etc. missing and i cant find this package anywhere.
2. i've tried using the pre-compiled driver from sekelev and managed to get it running, but when i run glxinfo it says no acceleration. how do i find out the new functionality with this driver - 2D/3D etc. ?
3. I've noticed that my xorg.conf has been generated by some failsafe function. this seems wrong

note: i'm sure the m650 is one of the good ones, i remember reading it somewhere on winischhofer's docs.

Thanks in advance guys, i'd really like to get even just a bit of compositing going :)

here is my xorg.conf:
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"sis"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1400x1050"
	Horizsync	31.5-65.5
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1400	1050
		Modes		"1400x1050@60"	"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"sis"
	Screen	1
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by LasVegas on 2007-10-27
The advantage of the premium driver is that it allows tvtime/dvd's to be seen in good quality.  I don't believe it has 3D acceleration for, e.g. penguin racer.  glxgears gives me a framerate of merely ca. 280.

You need the 
  "        Option          "XvDefaultAdaptor"      "Blitter"  "
line in the Device section at least.  Then you'll get nice TV/DVD and also be able to scale the video to arbitrary size.   See the xorg.conf  at the link above (I'll attach it as well - you may need to tweek it to your situation).  I don't believe you need to specify modes explicitly, but that may depend on your monitor.

And yes, I think failsafe is not quite the thing.  I don't know quite what that is, but I was getting that before when the sis driver would not start properly.

The "premium" driver does indeed work a lot better than other drivers I know of (vesa, sundry other sis_drv's).

---

### Post by jackobean on 2007-10-28
thanks LasVegas

I managed to get it working with that xorg.conf :), and the above binary :)

---

### Post by ernia on 2007-10-28
> **jackobean said:**
> thanks LasVegas

I managed to get it working with that xorg.conf :), and the above binary :)

me too (debian lenny). thanks a lot

---

### Post by ernia on 2007-10-28
Skiselev's patch worked to me (debian lenny) . driver compiles cleanly. Thanks a lot

---

### Post by HowardDrake on 2007-11-12
[The new IntelD201GLY2]("http://www.logicsupply.com/products/d201gly2") This driver just got a whole lot more useful with this board update :)

---

### Post by Bartender on 2007-11-13
I've been trying to follow this but getting a little confused.  How hard is it to do this video update that you guys are referring to?  I've been dinking with Linux for a couple of years but at a surface level.  Haven't compiled or any of that other fancy stuff.  That little Intel board sure does look interesting, especially now with SATA.

---

### Post by LasVegas on 2007-11-17
> **Bartender said:**
> I've been trying to follow this but getting a little confused.  How hard is it to do this video update that you guys are referring to?  I've been dinking with Linux for a couple of years but at a surface level.  Haven't compiled or any of that other fancy stuff.  That little Intel board sure does look interesting, especially now with SATA.

The update is simple:
(1) replace the /usr/lib/xorg/modules/drivers/sis_drv.so binary library with the one given above (well, on the previous page of this mail list); and
(2) replace the /etc/X11/xorg.conf with the one given above (or edit the one you have to match the one above).

That's all - then your video will work much better.  (but no 3-D graphics)

---

### Post by Master One on 2007-11-18
Can anybody tell me, what max. resolution @ 60 Hz this SiS Mirage* 1 is capable of?

I was wondering, if there is any possibilty to use it with 1920x1200@60 on a nice large 28" LCD display.

---

### Post by BCBill on 2007-11-18
I just checked how high a D201GLY will go driving a 19" Hitachi CM801 CRT.
1600x1200 at 94KHz HSync & 75Hz VSync is rock-solid and stunning.
1920x1440 at 90KHz HSync & 60Hz VSync is stable & acceptable though
I wouldn't want to do much close work with _any_ CRT with a VSync of 60Hz.
That shouldn't be a problem with an LCD..

---

### Post by Master One on 2007-11-19
That's great news, but can you check, if 1920x1200@60 are possible as well?

The problem is, [Windischhofer](http://www.winischhofer.net/) lists a lineup of

...
1600x1200
1680x1050
1920x1080
1920x1440
2048x1536

as available built-in modes on the 315, 330 and 340 series (I guess SiS662 is 315 series), but no 1920x1200, which is the native resolution of all recent 24" - 28" LCD screens.

If using the Linux driver with Xorg, can this problem be solved by generating a modeline for 1920x1200?

---

### Post by BCBill on 2007-11-19
Adding a "modeline" to the xorg.conf file _will_ let my D201GLY drive
my ~20" Hitachi CM801 at 1920x1200 with a VSync of 70Hz.

After a little fiddling with the VSize and HSize buttons on the CRT,
I have a rock-solid image that is 16" wide and 10" tall, hence 8x5 as is 1920x1200.

All I had to do is add the modeline "1920x1200" 227.98 1920 1984 2216 2616 1200 1204 1208 1245
and an entry for "1920x1200" to my xorg.conf file.

Testing with xvidtune shows

31.00-96.00	// KHz HSync
50.00-160.00	// Hz VSync

Resolution	     PixClk  HSync  VSync
Clock units	  (MHz)	 (KHz)	 (Hz)
2048x1536	267.27	95.45	60.07	// 4 x 3
1920x1440	233.10	89.68	59.79	// 4 x 3
1920x1200	227.98	87.15	70.00	// 8 x 5 <<======!!
1600x1200	202.50	93.75	75.00	// 4 x 3
1280x1024	157.50	91.40	85.02	// 5 x 4
1152x0864	135.22	76.14	83.85	// 4 x 3
1024x0768	113.03	81.43  100.0	// 4 x 3

I think it is safe to assume that if this is possible
with a VSync of 70 HZ it should be possible with
a VSync of 60 Hz. But to be safe, I'll actually try it.
But not this evening. Late in the day, any CRT
driven with a VSync of 60Hz is hard on the eyes.

---

### Post by Master One on 2007-11-20
Thanks a lot, BCBill, that's great news.

Which SiS driver are you using (since there are 3 around: one from Xorg, one from Winischhofer, and the binary one from Intel)?

How did you exactly get that modeline, and the shown output? I just tried xvidtune on my laptop, but it only showed me the modline of the actual resolution, when using "Test" and "Show":```
$ xvidtune
Vendor: , Model: 
Num hsync: 0, Num vsync: 0
"1600x1200"   162.00   1600 1656 1848 2160   1200 1202 1205 1250
```

---

### Post by BCBill on 2007-11-20
I'm using the driver Las Vegas attached to post #40 in this tread.

I generated the mode lines I've experimented with using the generator at [http://zaph.com/Modeline](http://zaph.com/Modeline)

The monitor section of my xorg.conf file is:

Section "Monitor"
	Identifier	"CM801"
	Option		"DPMS"
	HorizSync	31-96
	VertRefresh	50-160
# 60Hz VSync
	Modeline "1920x1200" 184.36 1920 1968 2152 2480 1200 1204 1208 1239
EndSection

xvidtune reports:
Vendor: , Model: 
Num hsync: 1, Num vsync: 1
hsync range 0:  31.00 -  96.00
vsync range 0:  50.00 - 160.00
"1920x1200"   184.36   1920 1968 2152 2480   1200 1204 1208 1239

My CRT confirms a VSync of 60Hz and and HSync of 74KHz.

A word of warning. The Hitachi CM801U that I've used in these cursory tests
is an astonishingly good CRT. You cannot safely assume that since it has handled
wickedly fast signals with ease a Black Friday Special flat panel display will too.
Your mileage _is_ going to vary.

---

### Post by Master One on 2007-11-20
Thanks again, BCBill, that's really fabulous.

I have no doubt that the intended LCD will be able to handle that matter :)

---

### Post by sprockkets on 2007-11-26
Thanks for the link. I am the person over at anandtech.com who posted that message, and was surprised Intel pulled the drivers. I have the newer version of that board and probably will work even though it was for an older SuSE distro.

Thanks again.

---

### Post by Cruxic on 2007-12-01
Does the video driver (or the VESA driver) support power saving features (DPMS)?

This board sounds nice to me but I'd be hesitant to buy it if it won't let the monitor go to sleep.  (I have this problem on with my old laptop (Sony Vaio with Neomagic MagicGraph 256AV)).

Will somebody please try this command: **xset dpms force standby**

If that causes your monitor to enter standby mode sweet!!!  (You should be able to tell by a blank unlit screen and the power LED will probably be orange, or at least a different color).

However, if the screen simply goes black then too bad.  (The LCD is still lit as you will notice if you turn up the brightness).

Note: You may need to add *Option "DPMS"*  to  *Section "Monitor"* in /etc/X11/xorg.conf
	
I'd really appreciate it if somebody tried this because this is looking like a sweet platform.

---

### Post by BCBill on 2007-12-02
I have confirmed with a 'scope that the "dpms" commands work on Debian-Lenny
as described at [http://webpages.charter.net/dperr/dpms.htm](http://webpages.charter.net/dperr/dpms.htm)
PROVIDING the test xset command is preceded by the command
xset -dpms

xset dpms force standby
stops the HSync signal 

xset dpms force suspend
stops the VSync signal

xset dpms force off
stops both the HSYnc & Vsync signals

All three commands cause the Red, Green and Blue signals to be driven low
and held there until the D201GLY is awakened by moving the mouse
or depressing a keyboard key.

---

### Post by Cruxic on 2007-12-03
Thanks, BCBill.  If I follow you correctly, this driver correctly implements the DPMS standard.  Sweet!  I've gotta get one.

---

### Post by yavor_bg on 2007-12-05
> **LasVegas said:**
> The update is simple:
(1) replace the /usr/lib/xorg/modules/drivers/sis_drv.so binary library with the one given above (well, on the previous page of this mail list); and
(2) replace the /etc/X11/xorg.conf with the one given above (or edit the one you have to match the one above).

That's all - then your video will work much better.  (but no 3-D graphics)

Thank you LasVegas, It's realy work! The performance Is't the great but much better than   default ubuntu driver :). I hope we will see soon any 3D support for SiS662.

---

### Post by zorglups on 2007-12-08
Special thanks to LasVegas but to the rest of the community as well !!!
I installed Gentoo on my D201GLY2 board and was so annoyed by the noisy display when using the default sis drivers.
I installed the driver from LasVegas as well as the xorg.conf file.

I still have a problem:
mplayer won't work with the video output set to xv:
mplayer -zoom -quiet -vo xv test.avi
...
   Error opening/initializing the selected video_out (-vo) device.

The result is quite an heavy CPU usage when playing a video because, if I understand correctly, the 2D acceleration is not used.

I'm not new to Linux but never used multimedia on linux before...

Can anyone shed some light on this ?

Thanks,

Pierre.

---

### Post by skiselev on 2007-12-11
Add
Option "XvDefaultAdaptor" "Blitter"
line to the "Device" section of your /etc/X11/xorg.conf file to make XVideo extension work properly.
The default "Overlay" adaptor doesn't work properly on SiS662...

---

### Post by Doom5 on 2007-12-11
So with the Premium driver, is this a good board for a MythTV box? Do XV and TV-Out through s-video work?

Thanks!

---

### Post by zorglups on 2007-12-11
Thanks for your reply skiselev. I will try tonight.

Doom5,

As soon as I have a correct Divx playback on it using mplayer, I will say a big YES !!!
Just imagine the silence !!! You should think twice about your acquisition needs since there is only one PCI slot.

I will document my hardware choices and settings when I'm happy with the video... 
Hopefully tomorrow morning.

BEst regards,

Pierre

---

### Post by Doom5 on 2007-12-11
> **zorglups said:**
> Thanks for your reply skiselev. I will try tonight.

Doom5,

As soon as I have a correct Divx playback on it using mplayer, I will say a big YES !!!
Just imagine the silence !!! You should think twice about your acquisition needs since there is only one PCI slot.

I will document my hardware choices and settings when I'm happy with the video... 
Hopefully tomorrow morning.

BEst regards,

Pierre

This board would be perfect for a non-hd MythTV Front-end, assuming tv-out works! Yes, and of course, silent! I'd install a linux distro on a USB Flash drive most likely, or a microdrive with an ide adapter.

---

### Post by zorglups on 2007-12-12
Thanks skiselev, it worked. I copied your 2 files and only modified the keyboard and monitor settings in the conf file.

Doom5, I played some divx yesterday and it was fine. There is no TV-out but you can find some VGA-to-Svideo converter for about 5USD.

I'm quite new to MythTV and once I have my set completed, I will post my thoughts on this hardware together with the log of my installation.

---

### Post by Master One on 2007-12-12
BCBill (or someone else with some knowledge about it), can you please have a look at [this](http://ubuntuforums.org/showpost.php?p=3939228&postcount=2) posting?

It's not related to the D201GLY / SiS issue, but about my tests with a S3 Savage integrated graphics chipset on a 24" LCD, which is causing a similar issue like my former concern about the SiS662 with the resolution of 1920x1200@60. I am not that much into Xorg configuration, and that thing with creating a modeline did not seem to hit the point, so maybe someone with more knowledge about Xorg config can help.

---

### Post by BCBill on 2007-12-12
I think I know what the problem is.
Please post the "Modes" line from
the /etc/X11/xorg.conf file that you are using
when you boot Ubuntu on your D201GLY
with your mystery monitor attached.

---

### Post by twkisner on 2007-12-14
I was looking to see if there was a solution to this this and I came across this site, that claims they have a new driver directly from sis that fixes all the problems *plus* XvMC:

[http://www.imedialinux.com/latest_news/sis_video_driver_for_intel_d201_with_2d_and_xvmc_acceleration_fixed](http://www.imedialinux.com/latest_news/sis_video_driver_for_intel_d201_with_2d_and_xvmc_acceleration_fixed)

Now I'm interested in this for Ubuntu because I want to use this board for an HD frontend with Mythbuntu.  To use it with HDTV, I need XvMC working for sure.

I may pick one up anyway, and use a Nividia 5200 PCI card with it.  But I could use a smaller enclosure if I didn't need the PCI card.

Think they will share with the world, or are they going to keep this to themselves?  I'm willing to pay for the distro, but Mythbuntu is already so easy to setup it just seems silly.

---

### Post by zorglups on 2007-12-15
twkisner,

I'm quite new to graphics things under Linux (I work on Unix systems for 10 years but doing anything but graphics !). I mean that the driver I got thanks to this forum thread probably fills the bill...

This is true until I have enough time to learn the difference between the xv and xvmc... So far, I'm still playing around to try to get Mythbuntu to display nicely divx and DVD onto my LCD TV. Still not 100% OK.

Nevertheless, like you, I searched the WEB quite a lot about this sis driver and saw the imedia solution.

I would not go with their solution for 2 reasons:
- I'm ready to pay a license but not one every 6 monthes.
- I'm not ready to go for a distribution which has no compiler and no easy solution to install packages.

Nevertheless, I still had a 4GB disks in a shelve and installed their MMS Settop box. This is one of their freeware showcase. It is based on their latest 5.0.4 iMedia Linux and has the sis drivers as well as one xorg.conf
I got a backup of the .so file and the xorg.conf file and restored it onto my Mythbunto.

I'm in a rush (for other familial reasons) and can't remember the result of my tests but I think that this was working.

I don't know if I was allowed to make such a post because I felt like doing something I shouldn't but I thought "only the ones who try knows"...

If you do not want to install, I can upload somewhere a big tgz of this installation on my D201GLY2 (for reference and educational purposes only).

Best regards,.

EDIT: The MMS Settop box can be found here: [http://www.imedialinux.com/MMS-Settop-box]("http://www.imedialinux.com/MMS-Settop-box")

---

### Post by cremersdh on 2007-12-16
I have installed the mentioned driver above and now have a nice looking desktop.

I am using mythbuntu on my system and noticed the following. When I use mplayer with the option "-vo x11" the output looks MUCH better then when I do with option "-vo xv"

But within mythtv it seems the internal player only knows of xv. Anyone any idea how I can have the internal player use the x11 video output???

But for all the others outthere. Do try the option -vo x11 and be suprised what an increased quality this gives.

---

### Post by zorglups on 2007-12-16
> **cremersdh said:**
> I have installed the mentioned driver above and now have a nice looking desktop.

Do you speak about the driver compiled by skiselev or the imedia one ?

> 
I am using mythbuntu on my system and noticed the following. When I use mplayer with the option "-vo x11" the output looks MUCH better then when I do with option "-vo xv"

But within mythtv it seems the internal player only knows of xv. Anyone any idea how I can have the internal player use the x11 video output???

But for all the others outthere. Do try the option -vo x11 and be suprised what an increased quality this gives.

Did you checked the CPU consumption of mplayer and xorg while playing the same divx with the xv and the x11 driver ? I guess that the x11 does not benefit from the hardware while xv does.

---

### Post by cremersdh on 2007-12-17
[QUOTE=zorglups;3963799]Do you speak about the driver compiled by skiselev or the imedia one ?

The one from skiselev!

Can I get the one from imedia somewhere ??

---

### Post by twkisner on 2007-12-17
> **zorglups said:**
> twkisner,

...

This is true until I have enough time to learn the difference between the xv and xvmc... So far, I'm still playing around to try to get Mythbuntu to display nicely divx and DVD onto my LCD TV. Still not 100% OK.

Nevertheless, like you, I searched the WEB quite a lot about this sis driver and saw the imedia solution.

I would not go with their solution for 2 reasons:
- I'm ready to pay a license but not one every 6 monthes.
- I'm not ready to go for a distribution which has no compiler and no easy solution to install packages.

....

If you do not want to install, I can upload somewhere a big tgz of this installation on my D201GLY2 (for reference and educational purposes only).

Best regards,.

EDIT: The MMS Settop box can be found here: [http://www.imedialinux.com/MMS-Settop-box]("http://www.imedialinux.com/MMS-Settop-box")

I appreciate your offer.

I didn't know they had the driver in the free download.  But, I thought it was just a 1 time fee for $20?  No free updates?

I don't know the legality of posting the imedia driver and config file.  One would think it's open source GPL, as all of their stuff is.  Open source licencing gives me a headache.

  Their distro is really just a stripped down Gentoo Linux 2006.  It would be a pain, but you could setup another Gentoo box and compile anything you want and copy it over.  That's more work than I want to do for sure, if their distro didn't have everything I wanted.

Honestly, I don't know the difference between xv and xvmc.  I just know that XvMC uses the hardware accelleration on the video chip instead of the CPU.  From what I've read, the CPU looks like it would clock about the same as an AMD 64 2400+.  I know thats proably -almost- but proabaly not quite enough for HD.  So it would probably need to offput the video playback to the video chipset with XxMC, like they do with the Via boards.

Anyway, I might pick one up and try.  I could always buy and use a Nvida 5200 PCI with it, and I know I wouldn't have any problems.  Still, I would be nice to know if someone has had success.

---

### Post by racerx90 on 2007-12-20
> **zorglups said:**
> Did you checked the CPU consumption of mplayer and xorg while playing the same divx with the xv and the x11 driver ? I guess that the x11 does not benefit from the hardware while xv does.

While this is *NOT* meant as a thorough or completely accurate test,  I did measure between X & mplayer processes that it's about 19% of cpu using X11 vs. 12% of CPU using xv for a 480 x 360 video (so about a 7% difference in CPU processing.) The problem is the xv output is just way too messed up to view that this is really the only option you have. The tests were ran on the D201GLY2 motherboard.

Also, I want to thank everyone on the ubuntu forum for working on a solution to this with at least using the SiS Premium drivers to get viewable video. It's way better than the VESA drivers I was using. 

Even though I'm not using Ubuntu (I'm not trying to start a holy war here), I did manage to work on creating a Fedora 8 source rpm which automatically patches, builds (full compile from source) and installs the "sisp_drv.so" driver (which will allow you to install it along with the regular sis driver and this way you don't have to be afraid of this driver getting upgraded with a yum update in case there's an update of the "broken" sis driver.) It should work with 32-bit and 64-bit (I have Fedora x86_64 installed since the CPU supports 64-bit extensions.) I also have the x86_64 driver built if anyone wants it in binary form, but I didn't build the i386 one (I'm sure anyone can build this easily.)

The only thing you need to do is edit your xorg.conf file if you want to change the name of the driver (i.e. boardname option).

If someone will host it for me (I have no way to host it - but it's only 855kb), I'll be more than happy to give out my source rpm for people to use. It will probably also work on other RH-based distributions, but I haven't tested it. Either way, it should be easy enough to patch the source rpm to do it since it's all been packaged.

Does anyone have the source code to the imedia driver? I'd like to see if there's anyway we can patch the old driver with the fixes and submit back to xorg to be included in future releases. I'm not a driver expert, but I suspect I could find someone to do the work for us who is.

Thanks!

---

### Post by zcream on 2007-12-26
Can I grab the extracted driver binary and xorg.conf ? 

E: 
amish153 AT hotmail DOT com 

Thanks!


> **zorglups said:**
> twkisner,

I'm quite new to graphics things under Linux (I work on Unix systems for 10 years but doing anything but graphics !). I mean that the driver I got thanks to this forum thread probably fills the bill...

This is true until I have enough time to learn the difference between the xv and xvmc... So far, I'm still playing around to try to get Mythbuntu to display nicely divx and DVD onto my LCD TV. Still not 100% OK.

Nevertheless, like you, I searched the WEB quite a lot about this sis driver and saw the imedia solution.

I would not go with their solution for 2 reasons:
- I'm ready to pay a license but not one every 6 monthes.
- I'm not ready to go for a distribution which has no compiler and no easy solution to install packages.

Nevertheless, I still had a 4GB disks in a shelve and installed their MMS Settop box. This is one of their freeware showcase. It is based on their latest 5.0.4 iMedia Linux and has the sis drivers as well as one xorg.conf
I got a backup of the .so file and the xorg.conf file and restored it onto my Mythbunto.

I'm in a rush (for other familial reasons) and can't remember the result of my tests but I think that this was working.

I don't know if I was allowed to make such a post because I felt like doing something I shouldn't but I thought "only the ones who try knows"...

If you do not want to install, I can upload somewhere a big tgz of this installation on my D201GLY2 (for reference and educational purposes only).

Best regards,.

EDIT: The MMS Settop box can be found here: [http://www.imedialinux.com/MMS-Settop-box]("http://www.imedialinux.com/MMS-Settop-box")

---

### Post by zorglups on 2007-12-28
cremersdh, twkisner, zcream, and all the other waiting...

Sorry for this long delay... I was abroad for a while...

I finished uploading the imedia.5.0.4.tgz file onto rapidshare:
[http://rapidshare.com/files/79535848/imedia.5.0.4.tgz.001.html]("http://rapidshare.com/files/79535848/imedia.5.0.4.tgz.001.html")
[http://rapidshare.com/files/79541326/imedia.5.0.4.tgz.002.html]("http://rapidshare.com/files/79541326/imedia.5.0.4.tgz.002.html")
[http://rapidshare.com/files/79541328/imedia.5.0.4.tgz.003.html]("http://rapidshare.com/files/79541328/imedia.5.0.4.tgz.003.html")

The file being 134MB big, I had to cut it first. I used for this [hjsplit]("http://www.freebyte.com/hjsplit/").

This tgz file is a backup of a running [iMedia MMS Settop box 5.0.4]("http://www.imedialinux.com/MMS-Settop-box").

I have no issue if this post gets removed would the moderator feels this might run the forum into troubles. I do not think so because this is only a link to a tar file of a non modified version of something available freely at iMedia.

I hope this will help the community to get video running fine on this nice board.
The driver included in the tgz is supposed to allow xvmc and they say that even 3D hardware acceleration is working.

Could the one trying this report their tests results for Divx playback and DVD playback ?

Best regards,

Pierre.

---

### Post by floatinginspace on 2007-12-28
> **racerx90 said:**
> 
Even though I'm not using Ubuntu (I'm not trying to start a holy war here), I did manage to work on creating a Fedora 8 source rpm which automatically patches, builds (full compile from source) and installs the "sisp_drv.so" driver (which will allow you to install it along with the regular sis driver and this way you don't have to be afraid of this driver getting upgraded with a yum update in case there's an update of the "broken" sis driver.) It should work with 32-bit and 64-bit (I have Fedora x86_64 installed since the CPU supports 64-bit extensions.) I also have the x86_64 driver built if anyone wants it in binary form, but I didn't build the i386 one (I'm sure anyone can build this easily.)

The only thing you need to do is edit your xorg.conf file if you want to change the name of the driver (i.e. boardname option).

If someone will host it for me (I have no way to host it - but it's only 855kb), I'll be more than happy to give out my source rpm for people to use. It will probably also work on other RH-based distributions, but I haven't tested it. Either way, it should be easy enough to patch the source rpm to do it since it's all been packaged.


can you kindly send the x86_64 binary sis_drv.so (or sisp_drv.so) to me?
i am also willing to host the source rpm, as long as i can handle the bandwidth.
please send to:       t (d0t) webc (at) gmx (d0t) net

i'm using 64 bit ubuntu (feisty iic, need to use kernel 2.6.19.7 because my dvb card only works up to that version (hauppauge hvr-3000)), so i think the binaries here are of no use to me. i tried compiling the driver from the source and patch posted earlier without success (i tried installing all -dev and other packages make complained about, but have no success with drm.h)

cheers

---

### Post by racerx90 on 2008-01-03
> **floatinginspace said:**
> can you kindly send the x86_64 binary sis_drv.so (or sisp_drv.so) to me?
i am also willing to host the source rpm, as long as i can handle the bandwidth.
please send to:       t (d0t) webc (at) gmx (d0t) net

i'm using 64 bit ubuntu (feisty iic, need to use kernel 2.6.19.7 because my dvb card only works up to that version (hauppauge hvr-3000)), so i think the binaries here are of no use to me. i tried compiling the driver from the source and patch posted earlier without success (i tried installing all -dev and other packages make complained about, but have no success with drm.h)

Check your inbox. Also, let me know if you have any success with it.

---

### Post by floatinginspace on 2008-01-10
> **racerx90 said:**
> Check your inbox. Also, let me know if you have any success with it.

i have put your rpms up here: [http://ft.dyn-o-saur.com/sis/](http://ft.dyn-o-saur.com/sis/)
for the reference: at the link above you will find a (fedora 8) source rpm and x86_64 binary rpm of the sis662 driver provided by racerx90 (i have not tried them yet)

---

### Post by celtic_druid on 2008-01-12
Nov 15th, 2007 - This will be included in the next release.
Sep 4th, 2007 - 5.0.4 has been released

So that means that any downloads from imedia would include an older driver until they release 5.0.5, which from looking at their past releases is about due (previous releases were 1/2/3 months apart). Not sure why they couldn't have released the driver as an update.

---

### Post by donhamilton on 2008-01-13
I have this same problem on a Shuttle SS30G2.

[http://global.shuttle.com/product_detail.jsp?PI=254](http://global.shuttle.com/product_detail.jsp?PI=254)

I can not load any Mythtv disty because of this.

Also most versions of Linux displays this problem. :(

How does the configuration select a driver ?

thanks

donhamilton

---

### Post by SirWizz on 2008-01-17
Hello everyone, just wanted to confirm that the solution posted by Las Vegas works on my Intel D201GLY2 board.

Thank you everyone for your hard work and for offering a solution to this problem! :)

---

### Post by celtic_druid on 2008-01-18
If it helps anyone:
[http://www.celticdruid.info/sis-accell.2.0.minibox.i686.tgz](http://www.celticdruid.info/sis-accell.2.0.minibox.i686.tgz)

Taken from imedia 5.0.4, so not the one talked about with the 2D/xvmc fixes.

etc/rcS.d/M10-sis
etc/X11/xorg.conf
lib/modules/2.6.20-imedia-i686/kernel/drivers/char/agp/agpgart.ko
lib/modules/2.6.20-imedia-i686/kernel/drivers/char/agp/sis-agp.ko
lib/modules/2.6.20-imedia-i686/kernel/drivers/char/drm/drm.ko
lib/modules/2.6.20-imedia-i686/kernel/drivers/char/drm/sis.ko
usr/lib/dri/sis_dri.so
usr/lib/xorg/modules/drivers/sis_drv.so
usr/lib/xorg/modules/extensions/libGLcore.so
usr/lib/xorg/modules/extensions/libglx.so -> //usr//lib/opengl/xorg-x11/extensions/libglx.so
usr/lib/libdrm.so -> libdrm.so.2.3.0
usr/lib/libdrm.so.2 -> libdrm.so.2.3.0
usr/lib/libdrm.so.2.3.0
usr/lib/opengl/xorg-x11/extensions/libglx.so
usr/lib/opengl/xorg-x11/lib/libGL.so -> libGL.so.1.2
usr/lib/opengl/xorg-x11/lib/libGL.so.1 -> libGL.so.1.2
usr/lib/opengl/xorg-x11/lib/libGL.so.1.2
usr/lib/libGL.so -> //usr//lib/opengl/xorg-x11/lib/libGL.so
usr/lib/libGL.so.1 -> /usr/lib/libGL.so

---

### Post by odenwell on 2008-01-18
Another n00b here.  Tried using the sis_drv.so file attached on page 4 (I think) of this thread and it gets rid of the noise, but when I try to display at my monitor's native resolution of 1440 x 900 the desktop is larger then the viewable screen.  I was hoping that the premium driver might do the trick so I spent a bunch of time getting the development environment set up.  I managed to get pretty far.  I get through some of the steps that skiselev posted on page 3.  I am stuck running the make.  Below is a portion of the errors I get when I run the make file.  Can anyone enlighten me?  Thanks in advance.  Bob

init301.c:11654: error: 'struct SiS_Private' has no member named 'SiS_Part2Port'
init301.c:11658: error: 'struct SiS_Private' has no member named 'SiS_Part2Port'
init301.c: In function 'SiS_SearchVBModeID':
init301.c:11668: error: 'struct SiS_Private' has no member named 'SiS_VGAINFO'
init301.c:11673: error: 'struct SiS_Private' has no member named 'SiS_VBModeIDTable'
init301.c:11674: error: 'struct SiS_Private' has no member named 'SiS_VBModeIDTable'
init301.c: In function 'SiS_OEM300Setting':
init301.c:11694: error: 'struct SiS_Private' has no member named 'UseCustomMode'
init301.c:11699: error: 'struct SiS_Private' has no member named 'SiS_VBInfo'
init301.c:11701: error: 'struct SiS_Private' has no member named 'SiS_IF_DEF_LVDS'
init301.c:11705: error: 'struct SiS_Private' has no member named 'UseCustomMode'
init301.c:11706: error: 'struct SiS_Private' has no member named 'SiS_VBInfo'
init301.c:11708: error: 'struct SiS_Private' has no member named 'SiS_VBType'
make[2]: *** [init301.lo] Error 1
make[2]: Leaving directory `/home/bob/sisp/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bob/sisp'
make: *** [all] Error 2

---

### Post by celtic_druid on 2008-01-18
Check your monitors manual/specs and set the correct refresh settings in your xorg.conf. Should solve the oversized resolution problem.

The attached binary is the premium driver? If so, then compiling it yourself shouldn't make any difference. Anyway changing refresh values has solved the above problem for me in the past.

---

### Post by lemaymd on 2008-01-19
Thanks for the great effort, guys!  I tried both the binary and source RPM versions on my Fedora 8 D201GLY2 box, and got the following output from X:

```


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Fedora 8 Red Hat, Inc.
Current Operating System: Linux localhost.localdomain 2.6.23.9-85.fc8 #1 SMP Fri Dec 7 15:49:36 EST 2007 x86_64
Build Date: 13 December 2007
Build ID: xorg-x11-server 1.3.0.0-37.fc8 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan 19 16:22:14 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Videocard0"
(WW) No monitor specified for screen "Screen0".
	Using a default monitor configuration.
(**) |-->Input Device "Keyboard0"
(==) |-->Input Device "<default pointer>"
(WW) The core pointer device wasn't specified explicitly in the layout.
	Using the default mouse configuration.
(WW) No FontPath specified.  Using compiled-in default.
(==) FontPath set to:
	catalogue:/etc/X11/fontpath.d,
	built-ins
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib64/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7bee60
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib64/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1039,0662 card 0000,0000 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1039,0003 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0964 card 0000,0000 rev 36 class 06,01,00 hdr 80
(II) PCI: 00:02:5: chip 1039,5513 card 8086,d61f rev 01 class 01,01,80 hdr 00
(II) PCI: 00:02:7: chip 1039,7012 card 8086,d61f rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 8086,d61f rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 8086,d61f rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:2: chip 1039,7001 card 8086,d61f rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:3: chip 1039,7002 card 1039,7002 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:04:0: chip 1039,0900 card 8086,d61f rev 91 class 02,00,00 hdr 00
(II) PCI: 00:05:0: chip 1039,0181 card 8086,d61f rev 01 class 01,01,85 hdr 00
(II) PCI: 00:06:0: chip 1131,7133 card 1461,f31f rev d0 class 04,80,00 hdr 00
(II) PCI: 00:1f:0: chip 1039,0004 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 01:00:0: chip 1039,6330 card 8086,d61f rev 04 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00001000 - 0x00001fff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0x4a000000 - 0x4a0fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x40000000 - 0x47ffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:31:0), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x3e000000 - 0x3e0fffff (0x100000) MX[B]
(--) PCI:*(1:0:0) Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter rev 4, Mem @ 0x40000000/27, 0x4a000000/17, I/O @ 0x1000/7
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0x48000000 from 0x49ffffff to 0x47ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0x4a105000 - 0x4a1057ff (0x800) MX[B]
	[1] -1	0	0x4a100000 - 0x4a100fff (0x1000) MX[B]
	[2] -1	0	0x4a101000 - 0x4a101fff (0x1000) MX[B]
	[3] -1	0	0x4a102000 - 0x4a102fff (0x1000) MX[B]
	[4] -1	0	0x4a103000 - 0x4a103fff (0x1000) MX[B]
	[5] -1	0	0x4a104000 - 0x4a104fff (0x1000) MX[B]
	[6] -1	0	0x48000000 - 0x47ffffff (0x0) MX[B]O
	[7] -1	0	0x4a000000 - 0x4a01ffff (0x20000) MX[B](B)
	[8] -1	0	0x40000000 - 0x47ffffff (0x8000000) MX[B](B)
	[9] -1	0	0x00002200 - 0x0000227f (0x80) IX[B]
	[10] -1	0	0x00002300 - 0x0000230f (0x10) IX[B]
	[11] -1	0	0x00002330 - 0x00002333 (0x4) IX[B]
	[12] -1	0	0x00002320 - 0x00002327 (0x8) IX[B]
	[13] -1	0	0x00002334 - 0x00002337 (0x4) IX[B]
	[14] -1	0	0x00002328 - 0x0000232f (0x8) IX[B]
	[15] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[16] -1	0	0x00002280 - 0x000022ff (0x80) IX[B]
	[17] -1	0	0x00002100 - 0x000021ff (0x100) IX[B]
	[18] -1	0	0x00002310 - 0x0000231f (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x00001000 - 0x0000107f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x4a105000 - 0x4a1057ff (0x800) MX[B]
	[1] -1	0	0x4a100000 - 0x4a100fff (0x1000) MX[B]
	[2] -1	0	0x4a101000 - 0x4a101fff (0x1000) MX[B]
	[3] -1	0	0x4a102000 - 0x4a102fff (0x1000) MX[B]
	[4] -1	0	0x4a103000 - 0x4a103fff (0x1000) MX[B]
	[5] -1	0	0x4a104000 - 0x4a104fff (0x1000) MX[B]
	[6] -1	0	0x48000000 - 0x47ffffff (0x0) MX[B]O
	[7] -1	0	0x4a000000 - 0x4a01ffff (0x20000) MX[B](B)
	[8] -1	0	0x40000000 - 0x47ffffff (0x8000000) MX[B](B)
	[9] -1	0	0x00002200 - 0x0000227f (0x80) IX[B]
	[10] -1	0	0x00002300 - 0x0000230f (0x10) IX[B]
	[11] -1	0	0x00002330 - 0x00002333 (0x4) IX[B]
	[12] -1	0	0x00002320 - 0x00002327 (0x8) IX[B]
	[13] -1	0	0x00002334 - 0x00002337 (0x4) IX[B]
	[14] -1	0	0x00002328 - 0x0000232f (0x8) IX[B]
	[15] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[16] -1	0	0x00002280 - 0x000022ff (0x80) IX[B]
	[17] -1	0	0x00002100 - 0x000021ff (0x100) IX[B]
	[18] -1	0	0x00002310 - 0x0000231f (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x00001000 - 0x0000107f (0x80) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x4a105000 - 0x4a1057ff (0x800) MX[B]
	[5] -1	0	0x4a100000 - 0x4a100fff (0x1000) MX[B]
	[6] -1	0	0x4a101000 - 0x4a101fff (0x1000) MX[B]
	[7] -1	0	0x4a102000 - 0x4a102fff (0x1000) MX[B]
	[8] -1	0	0x4a103000 - 0x4a103fff (0x1000) MX[B]
	[9] -1	0	0x4a104000 - 0x4a104fff (0x1000) MX[B]
	[10] -1	0	0x48000000 - 0x47ffffff (0x0) MX[B]O
	[11] -1	0	0x4a000000 - 0x4a01ffff (0x20000) MX[B](B)
	[12] -1	0	0x40000000 - 0x47ffffff (0x8000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00002200 - 0x0000227f (0x80) IX[B]
	[16] -1	0	0x00002300 - 0x0000230f (0x10) IX[B]
	[17] -1	0	0x00002330 - 0x00002333 (0x4) IX[B]
	[18] -1	0	0x00002320 - 0x00002327 (0x8) IX[B]
	[19] -1	0	0x00002334 - 0x00002337 (0x4) IX[B]
	[20] -1	0	0x00002328 - 0x0000232f (0x8) IX[B]
	[21] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[22] -1	0	0x00002280 - 0x000022ff (0x80) IX[B]
	[23] -1	0	0x00002100 - 0x000021ff (0x100) IX[B]
	[24] -1	0	0x00002310 - 0x0000231f (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x00001000 - 0x0000107f (0x80) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib64/xorg/modules//extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib64/xorg/modules//extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib64/xorg/modules//extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib64/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "type1"
(II) Loading /usr/lib64/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "record"
(II) Loading /usr/lib64/xorg/modules//extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib64/xorg/modules//extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "sisp"
(II) Loading /usr/lib64/xorg/modules//drivers/sisp_drv.so
(II) Module sisp: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.9.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib64/xorg/modules//input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib64/xorg/modules//input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) SISP: driver for SiS chipsets: SIS5597/5598, SIS530/620,
	SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
	SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
	SIS[M]661[F|M]X/[M]741[GX]/[M]760[GX]/[M]761[GX]/662, SIS340,
	[M]670/[M]770[GX]
(II) SISP: driver for XGI chipsets: Volari Z7 (XG20),
	Volari V3XT/V5/V8/Duo (XG40/XG42)
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset SIS[M]661[F|M]X/[M]741[GX]/[M]760[GX]/[M]761[GX]/662 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x4a105000 - 0x4a1057ff (0x800) MX[B]
	[5] -1	0	0x4a100000 - 0x4a100fff (0x1000) MX[B]
	[6] -1	0	0x4a101000 - 0x4a101fff (0x1000) MX[B]
	[7] -1	0	0x4a102000 - 0x4a102fff (0x1000) MX[B]
	[8] -1	0	0x4a103000 - 0x4a103fff (0x1000) MX[B]
	[9] -1	0	0x4a104000 - 0x4a104fff (0x1000) MX[B]
	[10] -1	0	0x48000000 - 0x47ffffff (0x0) MX[B]O
	[11] -1	0	0x4a000000 - 0x4a01ffff (0x20000) MX[B](B)
	[12] -1	0	0x40000000 - 0x47ffffff (0x8000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00002200 - 0x0000227f (0x80) IX[B]
	[16] -1	0	0x00002300 - 0x0000230f (0x10) IX[B]
	[17] -1	0	0x00002330 - 0x00002333 (0x4) IX[B]
	[18] -1	0	0x00002320 - 0x00002327 (0x8) IX[B]
	[19] -1	0	0x00002334 - 0x00002337 (0x4) IX[B]
	[20] -1	0	0x00002328 - 0x0000232f (0x8) IX[B]
	[21] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[22] -1	0	0x00002280 - 0x000022ff (0x80) IX[B]
	[23] -1	0	0x00002100 - 0x000021ff (0x100) IX[B]
	[24] -1	0	0x00002310 - 0x0000231f (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x00001000 - 0x0000107f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x4a105000 - 0x4a1057ff (0x800) MX[B]
	[5] -1	0	0x4a100000 - 0x4a100fff (0x1000) MX[B]
	[6] -1	0	0x4a101000 - 0x4a101fff (0x1000) MX[B]
	[7] -1	0	0x4a102000 - 0x4a102fff (0x1000) MX[B]
	[8] -1	0	0x4a103000 - 0x4a103fff (0x1000) MX[B]
	[9] -1	0	0x4a104000 - 0x4a104fff (0x1000) MX[B]
	[10] -1	0	0x48000000 - 0x47ffffff (0x0) MX[B]O
	[11] -1	0	0x4a000000 - 0x4a01ffff (0x20000) MX[B](B)
	[12] -1	0	0x40000000 - 0x47ffffff (0x8000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00002200 - 0x0000227f (0x80) IX[B]
	[19] -1	0	0x00002300 - 0x0000230f (0x10) IX[B]
	[20] -1	0	0x00002330 - 0x00002333 (0x4) IX[B]
	[21] -1	0	0x00002320 - 0x00002327 (0x8) IX[B]
	[22] -1	0	0x00002334 - 0x00002337 (0x4) IX[B]
	[23] -1	0	0x00002328 - 0x0000232f (0x8) IX[B]
	[24] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[25] -1	0	0x00002280 - 0x000022ff (0x80) IX[B]
	[26] -1	0	0x00002100 - 0x000021ff (0x100) IX[B]
	[27] -1	0	0x00002310 - 0x0000231f (0x10) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x00001000 - 0x0000107f (0x80) IX[B](B)
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Enabling PCI device
(II) SISP(0): SiS driver (2006/09/29-1, compiled for X.org 1.3.0.0)
(II) SISP(0): Copyright (C) 2001-2005 Thomas Winischhofer <thomas@winischhofer.net> and others
(II) SISP(0): *** See http://www.winischhofer.eu/linuxsisvga.shtml
(II) SISP(0): *** for documentation, updates.
(II) SISP(0): Licensed to X.org
(--) SISP(0): sisfb not found
(--) SISP(0): Relocated I/O registers at 0x1000
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(**) SISP(0): Depth 24, (--) framebuffer bpp 32
(==) SISP(0): RGB weight 888
(==) SISP(0): Default visual is TrueColor
(--) SISP(0): Video BIOS version "3.72.10" found (new SiS data layout)
(**) SISP(0): Option "NoAccel"
(**) SISP(0): Option "RenderAcceleration" "no"
(**) SISP(0): Option "DRI" "off"
(**) SISP(0): 2D Acceleration disabled
(==) SISP(0): RandR rotation support enabled
(==) SISP(0): Color HW cursor is enabled
(II) SISP(0): Using VRAM command queue, size 512k
(==) SISP(0): Hotkey display switching is enabled
(II) SISP(0): WARNING: Using the Hotkey might freeze your machine, regardless
(II) SISP(0):          whether enabled or disabled. This is no driver bug.
(==) SISP(0): SiSCtrl utility interface is disabled
(II) SISP(0): For information on SiSCtrl, see
		http://www.winischhofer.at/linuxsispart1.shtml#sisctrl
(==) SISP(0): Dynamic mode list support is enabled
(==) SISP(0): X server will not keep DPI constant for all screen sizes
(**) SISP(0): DRI disabled
(--) SISP(0): DIMM0 is DDR2 SDRAM
(--) SISP(0): DIMM1 is not installed
(--) SISP(0): 32768K shared video RAM (UMA)
(--) SISP(0): DRAM type: DDR2 SDRAM
(--) SISP(0): Memory clock: 397.722 MHz
(--) SISP(0): DRAM bus width: 64 bit
(--) SISP(0): Linear framebuffer at 0x40000000
(--) SISP(0): MMIO registers at 0x4A000000 (size 64K)
(--) SISP(0): VideoRAM: 32768 KB
(II) SISP(0): Using 32192K of framebuffer memory at offset 0K
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(==) SISP(0): Using gamma correction (1.0, 1.0, 1.0)
(II) SISP(0): Gamma correction is enabled
(II) SISP(0): Separate Xv gamma correction is disabled
(--) SISP(0): Memory bandwidth at 32 bpp is 795.444 MHz
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib64/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib64/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) SISP(0): initializing int10
(II) SISP(0): Primary V_BIOS segment is: 0xc000
(II) SISP(0): VESA BIOS detected
(II) SISP(0): VESA VBE Version 3.0
(II) SISP(0): VESA VBE Total Mem: 32768 kB
(II) SISP(0): VESA VBE OEM: SiS
(II) SISP(0): VESA VBE OEM Software Rev: 1.0
(II) SISP(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
(II) SISP(0): VESA VBE OEM Product: 6330
(II) SISP(0): VESA VBE OEM Product Rev: 3.72.10
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) SISP(0): VESA VBE DDC supported
(II) SISP(0): VESA VBE DDC Level 2
(II) SISP(0): VESA VBE DDC transfer in appr. 1 sec.
(II) SISP(0): VESA VBE DDC read successfully
(--) SISP(0): VBE CRT1 DDC monitor info:
(II) SISP(0): Manufacturer: DEL  Model: 400c  Serial#: 1094791500
(II) SISP(0): Year: 2005  Week: 26
(II) SISP(0): EDID Version: 1.3
(II) SISP(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) SISP(0): Sync:  Separate  Composite  SyncOnGreen
(II) SISP(0): Max H-Image Size [cm]: horiz.: 38  vert.: 31
(II) SISP(0): Gamma: 2.20
(II) SISP(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) SISP(0): Default color space is primary color space
(II) SISP(0): First detailed timing is preferred mode
(II) SISP(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) SISP(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) SISP(0): Supported VESA Video Modes:
(II) SISP(0): 720x400@70Hz
(II) SISP(0): 640x480@60Hz
(II) SISP(0): 640x480@75Hz
(II) SISP(0): 800x600@60Hz
(II) SISP(0): 800x600@75Hz
(II) SISP(0): 1024x768@60Hz
(II) SISP(0): 1024x768@75Hz
(II) SISP(0): 1280x1024@75Hz
(II) SISP(0): Manufacturer's mask: 0
(II) SISP(0): Supported Future Video Modes:
(II) SISP(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) SISP(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) SISP(0): Supported additional Video Mode:
(II) SISP(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) SISP(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) SISP(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) SISP(0): Serial No: T611656LAA1L
(II) SISP(0): Monitor name: DELL 1905FP
(II) SISP(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) SISP(0): EDID (in hex):
(II) SISP(0): 	00ffffffffffff0010ac0c404c314141
(II) SISP(0): 	1a0f01030e261f78eeee95a3544c9926
(II) SISP(0): 	0f5054a54b00714f8180010101010101
(II) SISP(0): 	010101010101302a009851002a403070
(II) SISP(0): 	1300782d1100001e000000ff00543631
(II) SISP(0): 	313635364c4141314c0a000000fc0044
(II) SISP(0): 	454c4c203139303546500a20000000fd
(II) SISP(0): 	00384c1e510e000a202020202020007b
(--) SISP(0): According to DDC size, CRT1 aspect ratio is 1.23:1 (normal)
(--) SISP(0): End of VBE CRT1 DDC monitor info
(==) SISP(0): Min pixel clock is 10 MHz
(--) SISP(0): Max pixel clock is 340 MHz
(II) SISP(0): Replaced entire mode list with built-in modes
(II) SISP(0): Using fake widescreen modes for CRT1 VGA devices
(II) SISP(0): 	[Use option "ForceCRT1VGAAspect" to overrule]
(II) SISP(0): Substituting missing CRT1 monitor HSync range by DDC data
(II) SISP(0): Substituting missing CRT1 monitor VRefresh range by DDC data
(II) SISP(0): Desired maximum virtual screen size is 0x0
(II) SISP(0): "Unknown reason" in the following list means that the mode
(II) SISP(0): is not supported on the chipset/bridge/current output device.
(II) SISP(0): <default monitor>: Using hsync range of 30.00-81.00 kHz
(II) SISP(0): <default monitor>: Using vrefresh range of 56.00-76.00 Hz
(WW) SISP(0): Unable to estimate virtual size
(II) SISP(0): Clock range:  10.00 to 340.00 MHz
(II) SISP(0): Not using default mode "800x600" (vrefresh out of range)
(II) SISP(0): Not using default mode "800x600" (vrefresh out of range)
(II) SISP(0): Not using default mode "800x600" (vrefresh out of range)
(II) SISP(0): Not using default mode "800x600" (hsync out of range)
(II) SISP(0): Not using default mode "640x480" (vrefresh out of range)
(II) SISP(0): Not using default mode "640x480" (vrefresh out of range)
(II) SISP(0): Not using default mode "640x480" (vrefresh out of range)
(II) SISP(0): Not using default mode "640x480" (hsync out of range)
(II) SISP(0): Not using default mode "640x480" (hsync out of range)
(II) SISP(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SISP(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SISP(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SISP(0): Not using default mode "1024x768" (hsync out of range)
(II) SISP(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) SISP(0): Not using default mode "1280x1024" (hsync out of range)
(II) SISP(0): Not using default mode "1600x1200" (hsync out of range)
(II) SISP(0): Not using default mode "1600x1200" (hsync out of range)
(II) SISP(0): Not using default mode "1600x1200" (hsync out of range)
(II) SISP(0): Not using default mode "1600x1200" (hsync out of range)
(II) SISP(0): Not using default mode "1600x1200" (hsync out of range)
(II) SISP(0): Not using default mode "1920x1440" (hsync out of range)
(II) SISP(0): Not using default mode "1920x1440" (hsync out of range)
(II) SISP(0): Not using default mode "1920x1440" (hsync out of range)
(II) SISP(0): Not using default mode "1920x1440" (hsync out of range)
(II) SISP(0): Not using default mode "1920x1440" (hsync out of range)
(II) SISP(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) SISP(0): Not using default mode "2048x1536" (hsync out of range)
(II) SISP(0): Not using default mode "2048x1536" (hsync out of range)
(II) SISP(0): Not using default mode "2048x1536" (hsync out of range)
(II) SISP(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) SISP(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) SISP(0): Not using default mode "800x480" (vrefresh out of range)
(II) SISP(0): Not using default mode "1024x576" (vrefresh out of range)
(II) SISP(0): Not using default mode "1280x720" (hsync out of range)
(II) SISP(0): Not using default mode "1280x960" (hsync out of range)
(II) SISP(0): Not using default mode "1280x768" (hsync out of range)
(II) SISP(0): Not using default mode "1152x864" (vrefresh out of range)
(II) SISP(0): Not using default mode "1280x800" (hsync out of range)
(II) SISP(0): Not using default mode "1280x854" (hsync out of range)
(II) SISP(0): Not using default mode "1440x900" (hsync out of range)
(II) SISP(0): Not using default mode "1440x900" (hsync out of range)
(II) SISP(0): Not using default mode "1920x1200" (hsync out of range)
(II) SISP(0): Not using default mode "1920x1200" (hsync out of range)
(II) SISP(0): Not using default mode "1920x1200" (hsync out of range)
(II) SISP(0): Not using default mode "1920x1200" (hsync out of range)
(II) SISP(0): Not using default mode "1920x1200" (hsync out of range)
(II) SISP(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(--) SISP(0): Virtual size is 0x0 (pitch 0)
(**) SISP(0): *Default mode "1600x1200": 175.4 MHz, 81.2 kHz, 65.0 Hz
(II) SISP(0): Modeline "1600x1200"  175.40  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync
(**) SISP(0): *Default mode "1600x1200": 161.8 MHz, 74.9 kHz, 59.9 Hz
(II) SISP(0): Modeline "1600x1200"  161.79  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync
(**) SISP(0): *Default mode "1680x1050": 147.1 MHz, 65.2 kHz, 60.0 Hz
(II) SISP(0): Modeline "1680x1050"  147.08  1680 1784 1968 2256  1050 1051 1054 1087 +hsync +vsync
(**) SISP(0): *Default mode "1400x1050": 155.7 MHz, 81.4 kHz, 74.7 Hz
(II) SISP(0): Modeline "1400x1050"  155.71  1400 1464 1528 1912  1050 1052 1064 1090 +hsync +vsync
(**) SISP(0): *Default mode "1400x1050": 122.9 MHz, 65.4 kHz, 60.1 Hz
(II) SISP(0): Modeline "1400x1050"  122.90  1400 1488 1640 1880  1050 1051 1054 1087 +hsync +vsync
(**) SISP(0): *Default mode "1280x1024": 135.2 MHz, 80.1 kHz, 75.1 Hz
(II) SISP(0): Modeline "1280x1024"  135.22  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) SISP(0): *Default mode "1280x1024": 107.9 MHz, 63.9 kHz, 59.9 Hz
(II) SISP(0): Modeline "1280x1024"  107.86  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) SISP(0): *Default mode "1440x900": 131.2 MHz, 67.2 kHz, 60.0 Hz
(II) SISP(0): Modeline "1440x900"  131.25  1440 1504 1824 1952  900 1008 1012 1120 +hsync +vsync
(**) SISP(0): *Default mode "1280x960": 107.9 MHz, 59.9 kHz, 59.9 Hz
(II) SISP(0): Modeline "1280x960"  107.86  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync
(**) SISP(0): *Default mode "1280x854": 135.2 MHz, 80.1 kHz, 75.1 Hz
(II) SISP(0): Modeline "1280x854"  135.22  1280 1296 1440 1688  854 958 962 1066 +hsync +vsync
(**) SISP(0): *Default mode "1280x854": 107.9 MHz, 63.9 kHz, 59.9 Hz
(II) SISP(0): Modeline "1280x854"  107.86  1280 1328 1440 1688  854 958 962 1066 +hsync +vsync
(**) SISP(0): *Default mode "1360x768": 87.7 MHz, 48.5 kHz, 60.0 Hz
(II) SISP(0): Modeline "1360x768"   87.70  1360 1416 1696 1808  768 770 782 808 +hsync +vsync
(**) SISP(0): *Default mode "1280x800": 135.2 MHz, 80.1 kHz, 75.1 Hz
(II) SISP(0): Modeline "1280x800"  135.22  1280 1296 1440 1688  800 931 935 1066 +hsync +vsync
(**) SISP(0): *Default mode "1280x800": 107.9 MHz, 63.9 kHz, 59.9 Hz
(II) SISP(0): Modeline "1280x800"  107.86  1280 1328 1440 1688  800 931 935 1066 +hsync +vsync
(**) SISP(0): *Default mode "1152x864": 107.9 MHz, 67.4 kHz, 74.9 Hz
(II) SISP(0): Modeline "1152x864"  107.86  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(**) SISP(0): *Default mode "1152x864": 89.9 MHz, 53.5 kHz, 60.0 Hz
(II) SISP(0): Modeline "1152x864"   89.89  1152 1216 1472 1680  864 869 877 892 +hsync +vsync
(**) SISP(0): *Default mode "1280x768": 135.2 MHz, 80.1 kHz, 75.1 Hz
(II) SISP(0): Modeline "1280x768"  135.22  1280 1296 1440 1688  768 915 919 1066 +hsync +vsync
(**) SISP(0): *Default mode "1280x768": 107.9 MHz, 63.9 kHz, 59.9 Hz
(II) SISP(0): Modeline "1280x768"  107.86  1280 1328 1440 1688  768 915 919 1066 +hsync +vsync
(**) SISP(0): *Default mode "1280x720": 135.2 MHz, 80.1 kHz, 75.1 Hz
(II) SISP(0): Modeline "1280x720"  135.22  1280 1296 1440 1688  720 891 895 1066 +hsync +vsync
(**) SISP(0): *Default mode "1280x720": 107.9 MHz, 63.9 kHz, 59.9 Hz
(II) SISP(0): Modeline "1280x720"  107.86  1280 1328 1440 1688  720 891 895 1066 +hsync +vsync
(**) SISP(0): *Default mode "1024x768": 78.7 MHz, 60.0 kHz, 75.0 Hz
(II) SISP(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) SISP(0): *Default mode "1024x768": 75.2 MHz, 56.6 kHz, 70.2 Hz
(II) SISP(0): Modeline "1024x768"   75.17  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) SISP(0): *Default mode "1024x768": 65.1 MHz, 48.5 kHz, 60.1 Hz
(II) SISP(0): Modeline "1024x768"   65.15  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) SISP(0): *Default mode "1024x576": 78.7 MHz, 60.0 kHz, 75.0 Hz
(II) SISP(0): Modeline "1024x576"   78.75  1024 1040 1136 1312  576 686 690 800 +hsync +vsync
(**) SISP(0): *Default mode "1024x576": 65.1 MHz, 48.5 kHz, 60.1 Hz
(II) SISP(0): Modeline "1024x576"   65.15  1024 1048 1184 1344  576 688 694 806 +hsync +vsync
(**) SISP(0): *Default mode "960x600": 41.5 MHz, 37.1 kHz, 60.0 Hz
(II) SISP(0): Modeline "960x600"   41.50  960 1008 1088 1120  600 603 609 618 +hsync +vsync
(**) SISP(0): *Default mode "960x540": 37.3 MHz, 33.8 kHz, 60.0 Hz
(II) SISP(0): Modeline "960x540"   37.29  960 976 1008 1104  540 543 549 563 +hsync +vsync
(**) SISP(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) SISP(0): Modeline "800x600"   49.52  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) SISP(0): *Default mode "800x600": 50.1 MHz, 48.2 kHz, 72.4 Hz
(II) SISP(0): Modeline "800x600"   50.11  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) SISP(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) SISP(0): Modeline "800x600"   39.97  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) SISP(0): *Default mode "800x600": 36.1 MHz, 35.2 kHz, 56.3 Hz
(II) SISP(0): Modeline "800x600"   36.06  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) SISP(0): *Default mode "768x576": 35.0 MHz, 35.9 kHz, 60.1 Hz
(II) SISP(0): Modeline "768x576"   35.00  768 792 872 976  576 578 581 597 +hsync +vsync
(**) SISP(0): *Default mode "720x576": 32.7 MHz, 35.9 kHz, 60.1 Hz
(II) SISP(0): Modeline "720x576"   32.73  720 744 816 912  576 578 581 597 +hsync +vsync
(**) SISP(0): *Default mode "856x480": 33.9 MHz, 31.7 kHz, 59.8 Hz
(II) SISP(0): Modeline "856x480"   33.94  856 872 1000 1072  480 492 495 529 -hsync -vsync
(**) SISP(0): *Default mode "856x480": 33.9 MHz, 30.5 kHz, 76.5 Hz (I)
(II) SISP(0): Modeline "856x480"   33.94  856 904 1048 1112  480 672 680 797 interlace +hsync +vsync
(**) SISP(0): *Default mode "848x480": 33.7 MHz, 31.0 kHz, 60.0 Hz
(II) SISP(0): Modeline "848x480"   33.75  848 864 976 1088  480 486 494 517 -hsync -vsync
(**) SISP(0): *Default mode "848x480": 33.9 MHz, 30.5 kHz, 76.5 Hz (I)
(II) SISP(0): Modeline "848x480"   33.94  848 904 1048 1112  480 672 680 797 interlace +hsync +vsync
(**) SISP(0): *Default mode "800x480": 49.5 MHz, 46.9 kHz, 75.1 Hz
(II) SISP(0): Modeline "800x480"   49.52  800 816 896 1056  480 551 554 624 +hsync +vsync
(**) SISP(0): *Default mode "800x480": 39.8 MHz, 37.7 kHz, 60.0 Hz
(II) SISP(0): Modeline "800x480"   39.77  800 840 968 1056  480 552 556 628 +hsync +vsync
(**) SISP(0): *Default mode "720x480": 28.3 MHz, 31.6 kHz, 61.0 Hz
(II) SISP(0): Modeline "720x480"   28.28  720 728 840 896  480 490 492 517 -hsync -vsync
(**) SISP(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) SISP(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) SISP(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) SISP(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) SISP(0): *Default mode "640x480": 25.1 MHz, 31.3 kHz, 59.7 Hz
(II) SISP(0): Modeline "640x480"   25.06  640 656 752 800  480 490 492 525 -hsync -vsync
(**) SISP(0): *Default mode "640x400": 25.1 MHz, 31.6 kHz, 71.6 Hz
(II) SISP(0): Modeline "640x400"   25.06  640 656 752 792  400 413 415 442 -hsync +vsync
(**) SISP(0): *Default mode "512x384": 32.6 MHz, 48.5 kHz, 60.1 Hz (D)
(II) SISP(0): Modeline "512x384"   32.57  512 528 592 672  384 385 388 403 doublescan -hsync -vsync
(**) SISP(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) SISP(0): Modeline "400x300"   19.98  400 416 480 528  300 300 302 314 doublescan +hsync +vsync
(**) SISP(0): *Default mode "320x240": 12.5 MHz, 31.3 kHz, 60.7 Hz (D)
(II) SISP(0): Modeline "320x240"   12.53  320 328 376 400  240 245 246 258 doublescan -hsync -vsync
(**) SISP(0): *Default mode "320x200": 12.5 MHz, 31.3 kHz, 70.9 Hz (D)
(II) SISP(0): Modeline "320x200"   12.53  320 328 376 400  200 206 207 221 doublescan -hsync +vsync
(--) SISP(0): Display dimensions: (380, 310) mm
(--) SISP(0): DPI set to (112, 98)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib64/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0x4a000000 - 0x4a01ffff (0x20000) MX[B]
	[1] 0	0	0x40000000 - 0x47ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0x4a105000 - 0x4a1057ff (0x800) MX[B]
	[7] -1	0	0x4a100000 - 0x4a100fff (0x1000) MX[B]
	[8] -1	0	0x4a101000 - 0x4a101fff (0x1000) MX[B]
	[9] -1	0	0x4a102000 - 0x4a102fff (0x1000) MX[B]
	[10] -1	0	0x4a103000 - 0x4a103fff (0x1000) MX[B]
	[11] -1	0	0x4a104000 - 0x4a104fff (0x1000) MX[B]
	[12] -1	0	0x48000000 - 0x47ffffff (0x0) MX[B]O
	[13] -1	0	0x4a000000 - 0x4a01ffff (0x20000) MX[B](B)
	[14] -1	0	0x40000000 - 0x47ffffff (0x8000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[18] 0	0	0x00001000 - 0x0000107f (0x80) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00002200 - 0x0000227f (0x80) IX[B]
	[22] -1	0	0x00002300 - 0x0000230f (0x10) IX[B]
	[23] -1	0	0x00002330 - 0x00002333 (0x4) IX[B]
	[24] -1	0	0x00002320 - 0x00002327 (0x8) IX[B]
	[25] -1	0	0x00002334 - 0x00002337 (0x4) IX[B]
	[26] -1	0	0x00002328 - 0x0000232f (0x8) IX[B]
	[27] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[28] -1	0	0x00002280 - 0x000022ff (0x80) IX[B]
	[29] -1	0	0x00002100 - 0x000021ff (0x100) IX[B]
	[30] -1	0	0x00002310 - 0x0000231f (0x10) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x00001000 - 0x0000107f (0x80) IX[B](B)
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib64/xorg/modules//libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib64/xorg/modules//libint10.so
(II) SISP(0): initializing int10
(II) SISP(0): Primary V_BIOS segment is: 0xc000
(II) SISP(0): VESA BIOS detected
(II) SISP(0): VESA VBE Version 3.0
(II) SISP(0): VESA VBE Total Mem: 32768 kB
(II) SISP(0): VESA VBE OEM: SiS
(II) SISP(0): VESA VBE OEM Software Rev: 1.0
(II) SISP(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
(II) SISP(0): VESA VBE OEM Product: 6330
(II) SISP(0): VESA VBE OEM Product Rev: 3.72.10
(==) SISP(0): Write-combining range (0x40000000,0x2000000)
(II) SISP(0): Setting standard mode 0x66
(WW) SISP(0): Current dotclock (175Mhz) too high for video overlay on CRT1

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x6d) [0x494c6d]
1: /lib64/libc.so.6 [0x3638630f30]
2: /usr/lib64/xorg/modules//drivers/sisp_drv.so(SiS315AccelInit+0x511) [0x2aaaabc5d361]
3: /usr/lib64/xorg/modules//drivers/sisp_drv.so [0x2aaaabc7755c]
4: /usr/bin/X(AddScreen+0x222) [0x4328b2]
5: /usr/bin/X(InitOutput+0x269) [0x462b99]
6: /usr/bin/X(main+0x275) [0x4330c5]
7: /lib64/libc.so.6(__libc_start_main+0xf4) [0x363861e074]
8: /usr/bin/X(FontFileCompleteXLFD+0x259) [0x432579]

Fatal server error:
Caught signal 8.  Server aborting

(II) SISP(0): Restoring by setting old mode 0x03

```

Here's my xorg.conf:

```

# Xorg configuration created by pyxf86config

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us+inet"
EndSection

#Section "Module"
#Disable "dri"
#Disable "glx"
#Disable "int10"
#Disable "dbe"
#Disable "vbe"
#EndSection

Section "Device"
	Identifier  "Videocard0"
#	Driver	    "vesa"
	Driver      "sisp"
	Option "UseSSE" "yes"
	Option "RenderAcceleration" "no"
	Option "NoAccel"
	Option "UseInt10Module" "no"
	Option "DRI" "off"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Videocard0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection



```

I was disabling a bunch of stuff to see if that would resolve the issue, but it didn't.  I tried compiling using GCC 4.1.2-33.  That's a pretty cryptic error, but hopefully somebody who runs across this can decipher it.  Until then, I'll probably be picking up an old PCI FX5200 on eBay or something.

---

### Post by celtic_druid on 2008-01-20
You are missing a monitor section by the looks of it.

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Unknown"
	ModelName  "Unknown"
	#HorizSync 30-80
	#VertRefresh 30-100
	Option "dpms"
EndSection
```
Something like that with a matching entry in Screen
```
	Monitor "Monitor0"
```

Hopefully adding a specific monitor section with the correct values will solve your problem.

---

### Post by lemaymd on 2008-01-20
Well, adding a monitor section didn't change anything, but I finally noticed the xorg.conf in the imedia tar file, and modified it as follows:

```

Section "ServerLayout"
	Identifier "XFree86 for SIS chipsets"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    FontPath	"/usr/share/fonts/misc/"
    FontPath	"/usr/share/fonts/75dpi/:unscaled"
    FontPath	"/usr/share/fonts/Speedo/"
    FontPath	"/usr/share/fonts/75dpi/"
    FontPath	"/usr/share/fonts/100dpi/"
    FontPath	"/usr/share/fonts/100dpi/:unscaled"
    FontPath	"/usr/share/fonts/TTF/"
EndSection

# Module loading section

Section "Module"
	Load  "dbe"		# Double-buffering
	Load  "extmod"		# Misc. required extensions
	# Load  "GLcore"		# OpenGL support
	Load  "dri"		# Direct rendering infrastructure
	Load  "glx"		# OpenGL X protocol interface
	# Load  "v4l"		# Video4Linux
	# Load  "pex5"		# PHIGS for X 3D environment (obsolete)
	# Load  "record"	# X event recorder
	# Load  "xie"		# X Image Extension (obsolete)
	Load  "freetype"	# TrueType font handler
	Load "bitmap"
	Load  "type1"		# Adobe Type 1 font handler
EndSection

Section "ServerFlags"
    Option "DefaultServerLayout" "XFree86 for SIS chipsets
    Option "DontVTSwitch" "false"
    Option "DontZoom" "false"
    Option "HandleSpecialKeys" "Always"
    Option "XkbDisable" "true"
    Option "AllowMouseOpenFail" "true"
    Option "AllowKeyboardOpenFail" "true"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us+inet"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option      "Device" "/dev/input/mice"
	Option      "Protocol" "IMPS/2"
	Option      "Emulate3Buttons" "on"
	Option      "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier "Monitor0"
	VendorName "Unknown"
	ModelName  "Unknown"
	#HorizSync 30-80
	#VertRefresh 30-100
	Option "dpms"
EndSection

Section "Device"
	Identifier "Device0"
	Driver "sisp"
	BoardName "SIS Mirage"
	Option "NoAccel" "off"
#	Option "XvDefaultAdaptor" "Blitter"
EndSection


Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	Subsection "Display"
		Depth 24
		Modes "1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "DRI"
	Group 0
	Mode 0666
EndSection


```

That works great, although MythTV still skips and jumps.  Hopefully the Matrox PCI G200 TV/VGA combo card I ordered will be the final solution to these woes without totally destroying the energy efficiency of the platform.  I sure wish Intel had increased the cost of the board a bit and put in a G35 chipset or something.  Anyway, thanks for the help, this is much better than vesa!

---

### Post by davide caminati on 2008-01-21
Hello everyone, i have D201GLY  with S-video out , but tvtime can't render  output  (black screen) of my hauppauge hybrid tv tuner USB :confused: , someone tell my why? with VGA out no problem.
I use ubuntu 7.10.


Thanks.

---

### Post by zorglups on 2008-01-22
> **celtic_druid said:**
> Nov 15th, 2007 - This will be included in the next release.
Sep 4th, 2007 - 5.0.4 has been released

So that means that any downloads from imedia would include an older driver until they release 5.0.5, which from looking at their past releases is about due (previous releases were 1/2/3 months apart). Not sure why they couldn't have released the driver as an update.

It seems you are right. Sorry for this mistake.

> **celtic_druid said:**
> If it helps anyone:
[http://www.celticdruid.info/sis-accell.2.0.minibox.i686.tgz](http://www.celticdruid.info/sis-accell.2.0.minibox.i686.tgz)

Taken from imedia 5.0.4, so not the one talked about with the 2D/xvmc fixes.

etc/rcS.d/M10-sis
etc/X11/xorg.conf
lib/modules/2.6.20-imedia-i686/kernel/drivers/char/agp/agpgart.ko
lib/modules/2.6.20-imedia-i686/kernel/drivers/char/agp/sis-agp.ko
lib/modules/2.6.20-imedia-i686/kernel/drivers/char/drm/drm.ko
lib/modules/2.6.20-imedia-i686/kernel/drivers/char/drm/sis.ko
usr/lib/dri/sis_dri.so
usr/lib/xorg/modules/drivers/sis_drv.so
usr/lib/xorg/modules/extensions/libGLcore.so
usr/lib/xorg/modules/extensions/libglx.so -> //usr//lib/opengl/xorg-x11/extensions/libglx.so
usr/lib/libdrm.so -> libdrm.so.2.3.0
usr/lib/libdrm.so.2 -> libdrm.so.2.3.0
usr/lib/libdrm.so.2.3.0
usr/lib/opengl/xorg-x11/extensions/libglx.so
usr/lib/opengl/xorg-x11/lib/libGL.so -> libGL.so.1.2
usr/lib/opengl/xorg-x11/lib/libGL.so.1 -> libGL.so.1.2
usr/lib/opengl/xorg-x11/lib/libGL.so.1.2
usr/lib/libGL.so -> //usr//lib/opengl/xorg-x11/lib/libGL.so
usr/lib/libGL.so.1 -> /usr/lib/libGL.so

Did you get better result with this setup than with the provided binaries from page 4 ?

I'm mostly interrested in MythVideo for Divx playback and MythDVD.

Thanks...

Pierre.

---

### Post by celtic_druid on 2008-01-23
Only got my D201GLY2 the other day. Got as far as testing the CPU temp during BIOS. As has been said elsewhere, it gets very hot with just the stock heatsink. A 14dBA 40mm fan on top made a huge difference though. Unfortunatly, it is going in a case with no room on top.

Will see about running some tests later. Don't really have the time now.

---

### Post by zorglups on 2008-01-23
celtic_druid,

Seing the pretty complete tgz file you posted, I really thought you had it up and running with video applications...

I'll wait your conclusions.

In the mean time, I will try to find some time to test those myself.

Note: I'm currently spending my time in making the case. I choose not to change any heatsink (maybe the Northbridge's one will be changed) but will probalby put in the case a quite 120mm fan.

EDIT: Oh... maybe you got the tgz somewhere ??? If this is the case, would you be so kind to tell us where so we can check other users experience. If you did it yourself, congratulations.

---

### Post by celtic_druid on 2008-01-24
Even less time now since my main work (multimedia/web design) machine died and I had to replace it.

The tgz was extracted from the package in the ISO. So basically what would be installed if you were running imedia 5.0.4. Not sure if anyone else has tried it. Could just be one of the more standard drives out there anyway.

Until 5.0.5 comes out with the fixed driver from SiS, could be better off using the one posted earlier.

---

### Post by zorglups on 2008-01-27
> **celtic_druid said:**
> 
Until 5.0.5 comes out with the fixed driver from SiS, could be better off using the one posted earlier.

I will try both and see which one gives me the best results...
I will write a small shell helping me to switch easily my environment so I can evaluate both quite easily.

Good luck with your main system...

Pierre.

---

### Post by menoz on 2008-01-30
Hi guys, I saw that this mornig imedialinux has announced the 6.0 version of their distro, has somebody already tried the new driver? In the changelog they claim they have resolved all the 2d/3d acceleration problems,but as of now  max resolution is 800x600 (they claim to release a bug fix soon).

I think these can be good news! I'm trying to download the vmware image, but it takes fooooooooooooooorever!

Hope to have good news soon... Bye! :KS

---

### Post by celtic_druid on 2008-01-30
From the 6.0 ISO:
[http://www.celticdruid.info/sis-accell.0.9.3.minibox.i686.tgz](http://www.celticdruid.info/sis-accell.0.9.3.minibox.i686.tgz)
```

etc/rcS.d/M10-sis
etc/X11/xorg.conf
etc/X11/XvMCConfig
lib/modules/2.6.23-imedia-i686/kernel/drivers/char/agp/agpgart.ko
lib/modules/2.6.23-imedia-i686/kernel/drivers/char/agp/sis-agp.ko
lib/modules/2.6.23-imedia-i686/kernel/drivers/char/drm/drm.ko
lib/modules/2.6.23-imedia-i686/kernel/drivers/char/drm/sis.ko
usr/lib/dri/sis_dri.so
usr/lib/xorg/modules/drivers/sis_drv.so
usr/lib/xorg/modules/extensions/libGLcore.so
usr/lib/xorg/modules/extensions/libglx.so
usr/lib/libdrm.so -> libdrm.so.2.3.0
usr/lib/libdrm.so.2 -> libdrm.so.2.3.0
usr/lib/libdrm.so.2.3.0
usr/lib/opengl/xorg-x11/extensions/libglx.so
usr/lib/opengl/xorg-x11/lib/libGL.so -> libGL.so.1.2
usr/lib/opengl/xorg-x11/lib/libGL.so.1 -> libGL.so.1.2
usr/lib/opengl/xorg-x11/lib/libGL.so.1.2
usr/lib/libGL.so -> /usr/lib/opengl/xorg-x11/lib/libGL.so
usr/lib/libGL.so.1 -> /usr/lib/libGL.so
usr/lib/libGL.so.1.2
usr/lib/libXvMC.so -> libXvMC.so.1.0.0
usr/lib/libXvMC.so.1 -> libXvMC.so.1.0.0
usr/lib/libXvMC.so.1.0.0
usr/lib/libXvMCW.so -> libXvMCW.so.1.0.0
usr/lib/libXvMCW.so.1 -> libXvMCW.so.1.0.0
usr/lib/libXvMCW.so.1.0.0
usr/lib/libSiSXvMC.so.1 -> libSiSXvMC.so.1.0.0
usr/lib/libSiSXvMC.so.1.0.0

```

---

### Post by DrFreeze on 2008-02-01
Hi guys

Just yesterday i got my d201gly2 board in, which im gonna use for a media center (playing ripped DVDs from hard disk) on my LCD TV

now ive tried the following drivers:
- standard ubuntu sis
- premium sis binary (linked in this thread)
- imedia packaged sis binary

now the first one was obviously horrible, the vertical noise was just plain terrible
the second and the third work OK, no noise, but it seems like the resolution is off, the image on my TV is a lot blurrier then with the original sis driver, even though the resolution is set correctly, to 1360*768.

Can anyone advise how i can get the image clarity of the original driver back, but without the vertical noise?

obviously the vesa driver is a no go, as i need a widescreen resolution

thanks in advance for any help you can offer!

---

### Post by rbeaudry on 2008-02-08
I found an Intel Linux driver at one of the first links mentioned in this thread:

[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2773&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2773&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

I downloaded the binary, un-tar'd it, and replaced the /usr/lib/xorg/modules/drivers/sis_drv.so binary library with the one from the tar file.  I also copied sis_drv.la into the same directory (although it was not there originally).

I didn't have to edit any configuration files.  I rebooted the computer, and 1024x768x85Hz came up clear as glass.

My monitor is an old beast that does not support higher resolution, so I have no idea if this will work at higher res.  Also, I did not test out 3D or media playing.  I'm planning on using this box as a back-room server, so I don't need super graphics, just wanted to get rid of the "snow" :-)

Also, this was a GLY2 board, though I think the GLY board uses the same chipset.

RCB

---

### Post by celtic_druid on 2008-02-09
Looks like a version of the pro driver posted earlier. Modified by Chaoyu Chen from Sis, who also worked on the driver that comes with iMedia.

Found some more info here, including source and a kernel patch:
[http://www.linuxconsulting.ro/xorg-drivers/](http://www.linuxconsulting.ro/xorg-drivers/)

---

### Post by Adahn on 2008-02-10
> **celtic_druid said:**
> Looks like a version of the pro driver posted earlier. Modified by Chaoyu Chen from Sis, who also worked on the driver that comes with iMedia.

Found some more info here, including source and a kernel patch:
[http://www.linuxconsulting.ro/xorg-drivers/](http://www.linuxconsulting.ro/xorg-drivers/)

does this do 3d?

---

### Post by earthdragon49 on 2008-02-18
> **HowardDrake said:**
> Well I actually figured it out somewhat by accident. In my desire to try LinuxMCE I tried loading Kubuntu 7.04 on my D201GLY and instead of saying start normally, I told it to start in "safe graphics" mode.

Lo and behold, it comes up rock solid in 1280x1024 on my 17" LCD, as a matter of fact I'm typing in my reply in it right now. I checked and its running the "vesa" driver instead of the "sis". Next up is a HD install, and I'm going to configure X to use the "vesa" driver there. If its solid, I'll report back. It's funny that the "sis" driver looks like crap, but the "vesa" driver is perfect :)

:lolflag:

Just FYI....

Thanks! Total noob here, just built a Shuttle barebone, spent a week reading about Linux, spent all day downloading Ubuntu 7.0 live CD, first boot on my new unit, and got the screen interference. Came here, found this thread on the second try, read down to post #8, and...bam! Yep, rock solid 1280x1024 in the safe/generic/vesa mode. Even though this is an Intel thread, it also worked like a charm on my Shuttle/AMD 64 X2/Sis Mirage 1. I'm sure it will probably require some further reading, but for now, it's great! Thanks again for posting the tip.

earthdragon49

---

### Post by tuneable on 2008-02-19
Short report on my experiences today with the SiS on this mainboard and Ubuntu 7.10:

Standard 'sis' driver -- glitches

Using 'vesa' driver -- 1280x1024, no glitches, but also no 'xo' video output in Mplayer.

Using the the linux* binary Xorg driver provided by Intel (support on Intel website, I downloaded the 'sis_drv_i386.tar.bz2' file yesterday) -- 1280x1024, 32 bit, with 'xo' video output in Mplayer (quick estimate ~10% CPU load for gmplayer). 

 :)

Note: The .la file in the Intel driver archive seems to suggest a '/usr/local/....' location for the driver. This did not work for me, so I replace  '/usr/lib/xorg/modules/drivers/sis_drv.so'
with the one from the archive, and ran:
> sudo dpkg-reconfigure xserver-xorg
...followed by a restart.

---

### Post by Adahn on 2008-02-24
slightly off topic, but has anyone gotten cpu scaling to work with this mobo?

---

### Post by s_r_g on 2008-02-27
> **Adahn said:**
> slightly off topic, but has anyone gotten cpu scaling to work with this mobo?
It's work fine under gentoo with ACPI p4-clockmod. Right now  cpu freq 499Mhz ondemand governors. ([http://www.gentoo.org/doc/en/power-management-guide.xml](http://www.gentoo.org/doc/en/power-management-guide.xml))
But how undervolt cpu & how overclock -- i don't know :(

---

### Post by giedz on 2008-02-27
Hi

How about this version : [http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2873&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2873&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

it's been released at the end of Jan this year - how things work with this one? I will be able to test it next week but thought that somebody did it already and can share its knowledge. 

Regards,
Marcin

---

### Post by s_r_g on 2008-02-27
readme.txt from downloaded sis_drv_src_300407.tar.bz2

> This driver is written by Thomas Winischhofer and is a (nearly)
  complete re-write of a driver written for the SiS6326 and SiS530 by
  Alan Hourihane and others.

Also directory with sources was named "2d-driver'
looks like it does not support 3d hardware acceleration. :(

---

### Post by cremersdh on 2008-03-02
> **s_r_g said:**
> It's work fine under gentoo with ACPI p4-clockmod. Right now  cpu freq 499Mhz ondemand governors. ([http://www.gentoo.org/doc/en/power-management-guide.xml](http://www.gentoo.org/doc/en/power-management-guide.xml))
But how undervolt cpu & how overclock -- i don't know :(

Weird. With Ubuntu I get this error while loading p4-clockmod on my D201GLY2 board

FATAL: Error inserting p4_clockmod (/lib/modules/2.6.22-14-generic/kernel/arch/i386/kernel/cpu/cpufreq/p4-clockmod.ko): No such device

Because of this I can not use cpufreq at all, although I want to badly. Anyone any ideas how to fix this ? I am running Gutsy....

---

### Post by srggal on 2008-03-03
> **cremersdh said:**
> Weird. With Ubuntu I get this error while loading p4-clockmod on my D201GLY2 board

FATAL: Error inserting p4_clockmod (/lib/modules/2.6.22-14-generic/kernel/arch/i386/kernel/cpu/cpufreq/p4-clockmod.ko): No such device

Because of this I can not use cpufreq at all, although I want to badly. Anyone any ideas how to fix this ? I am running Gutsy....
Gkhm..
I use D201GLY (Yonah) with p4_clockmod and kernel 2.6.23.

Are you try other cpufreq drivers?
Especially - Intel Enhanced SpeedStep & ACPI Processor P-States driver?

---

### Post by sooraj_s on 2008-03-07
> **rbeaudry said:**
> I found an Intel Linux driver at one of the first links mentioned in this thread:

[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2773&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2773&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

I downloaded the binary, un-tar'd it, and replaced the /usr/lib/xorg/modules/drivers/sis_drv.so binary library with the one from the tar file.  I also copied sis_drv.la into the same directory (although it was not there originally).

I didn't have to edit any configuration files.  I rebooted the computer, and 1024x768x85Hz came up clear as glass.

My monitor is an old beast that does not support higher resolution, so I have no idea if this will work at higher res.  Also, I did not test out 3D or media playing.  I'm planning on using this box as a back-room server, so I don't need super graphics, just wanted to get rid of the "snow" :-)

Also, this was a GLY2 board, though I think the GLY board uses the same chipset.

RCB

Hi,
I am a newbie to linux, saw ur post and glad u got the solution..
can give me step by step instruction how to install..would greatly appreciate the help...

---

### Post by techpr on 2008-03-13
> **rbeaudry said:**
> I found an Intel Linux driver at one of the first links mentioned in this thread:

[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2773&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2773&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

I downloaded the binary, un-tar'd it, and replaced the /usr/lib/xorg/modules/drivers/sis_drv.so binary library with the one from the tar file.  I also copied sis_drv.la into the same directory (although it was not there originally).

I didn't have to edit any configuration files.  I rebooted the computer, and 1024x768x85Hz came up clear as glass.

My monitor is an old beast that does not support higher resolution, so I have no idea if this will work at higher res.  Also, I did not test out 3D or media playing.  I'm planning on using this box as a back-room server, so I don't need super graphics, just wanted to get rid of the "snow" :-)

Also, this was a GLY2 board, though I think the GLY board uses the same chipset.

RCB

Had the same video problem as everybody, This worked for me, very easy to apply. Thank You.

---

### Post by Nomisdk on 2008-03-25
Any had luck playing x264 720p movies at this?

Im planing buying one and use it as small media center.

---

### Post by tuneable on 2008-03-25
> **tuneable said:**
> Short report on my experiences today with the SiS on this mainboard and Ubuntu 7.10:

Standard 'sis' driver -- glitches

Using 'vesa' driver -- 1280x1024, no glitches, but also no 'xo' video output in Mplayer.

Using the the linux* binary Xorg driver provided by Intel (support on Intel website, I downloaded the 'sis_drv_i386.tar.bz2' file yesterday) -- 1280x1024, 32 bit, with 'xo' video output in Mplayer (quick estimate ~10% CPU load for gmplayer). 

 :)

Note: The .la file in the Intel driver archive seems to suggest a '/usr/local/....' location for the driver. This did not work for me, so I replace  '/usr/lib/xorg/modules/drivers/sis_drv.so'
with the one from the archive, and ran:

...followed by a restart.

So, four weeks further and I have had some more experience with this driver. 

A)
Did anyone find a solution for the "crashes after using gnome terminal"? 

Problem: In 80-90% of the cases I use some sort of 'interactive' program (less, vi, screen, cfdisk) in a gnome-terminal the machine freezes. After reboot it appears a backup xorg.0.log file has been created during the freeze with a massive size. The last line is long... and filled with endless repeats of "SIS (II) --Garbage". I found out that X can be killed and restarted through a ssh connection to solve the problem, but I do not always have a laptop at home. 

My own workaround, ugly as it is, is to use ALT-F1 to go to a console, or change to a previously saved "vesa" version of xorg.conf in case I have to do a lot of things in terminals. Yes, I know this is a sad solution. 

Is there perhaps a way to ignore these "SIS (II) --Garbage" logs? Perhaps the system will not freeze then.

B)
Is there anyone having good experiences with the (Intel provided) SIS drivers on Hardy Beta?

Problem: I have tried and Hardy beta crashes on the 32 and 64 bit drivers by Intel. The sis_drv.so included in Hardy shows the distorted lines (unbearable) so it is back to vesa again... *sigh*


The struggle goes on.

---

### Post by zorglups on 2008-03-28
> **tuneable said:**
> 
B)
Is there anyone having good experiences with the (Intel provided) SIS drivers on Hardy Beta?

Problem: I have tried and Hardy beta crashes on the 32 and 64 bit drivers by Intel. The sis_drv.so included in Hardy shows the distorted lines (unbearable) so it is back to vesa again... *sigh*


The struggle goes on.

I tried Hardy Beta and lost some hairs too !!!
I just found a thread in this forum speaking about this but I'm too bad with compilation things...
[http://ubuntuforums.org/showthread.php?p=4558160]("http://ubuntuforums.org/showthread.php?p=4558160")

Just in case you want to give it a trial...

Pierre

---

### Post by tuneable on 2008-03-29
:-k  Found that thread too, and had the same thought about compiling from source. 

I'll try again with compiling. I was unsuccessful with the Intel source before, but that could be because I am not an expert. :)

---

### Post by Xtrmi on 2008-04-05
has anybody got the resolution to 1920 x 1200. I want to use this as a green pc but with my big monitor.

---

### Post by ottod on 2008-04-11
See [here]("http://ubuntuforums.org/showpost.php?p=4697207&postcount=4") for some help.

---

### Post by Master One on 2008-04-11
So is there any difference now between the actual version from iMedia and the patched one from Intel?

Why does the iMedia version need a kernel patch, and the Intel version not?

Can someone please publish a binary for 64bit Hardy (would save a lot of hassel)?

P.S. I've been away from Ubuntu for some time, but I am just downloading the 32- & 64-bit alternate-daily, so I haven't really followed the progress on the SiS issue since January.

---

### Post by Master One on 2008-04-14
Ok, looks like the patched Intel driver is the way to go. I could not make the iMedia driver to compile on 64bit Hardy, it already failed with autogen.sh (don't recall the problem right now).

The patched Intel driver compiled, but for some strange reason it did not work (I got some pretty strange think on my display, which looked like the into for a fancy screensaver, nothing else, and it kind of locked up my LCD, even making it impossible to call the display's menu, never seen something like this before).

Because it was just a test-setup, I will now do a complete reinstall with todays hardy-alternate-amd64, and then try it again.

Isn't it quite strange, that ppl report the driver to be working just fine, although they didn't recompile the kernel with the mentioned patch:> It requires a kernel patch to add SIS 671 PCI ids (0x0671) and a new entry on sis-agp.c to detect the chipset.
?

I mean, without that patch, no AGP support, resulting in comparably poor performance, right?

---

### Post by celtic_druid on 2008-04-23
Well the PCI ids were added to the main kernel branch 1-2 months ago, so if you have an upto date kernel, then no patch would be required.

---

### Post by Master One on 2008-04-24
These PCI IDs are not in the latest Hardy 2.6.24 kernel. With Hardy's up-to-date stock-Ubuntu-kernel you will find the "No APG found" message in /var/log/Xorg.0.log. Patching a git-checkout of the Ubuntu kernel works fine using the iMedia kernel patch for 2.6.23, and after rebuiding the kernel & rebooting you can see that APG has been found and 32MB have been assigned to it in the xorg log.

---

### Post by celtic_druid on 2008-04-24
You would I guess need 2.6.25.

---

### Post by wasutton3 on 2008-05-05
has anyone had any success using this card and hardy? such a patch/driver would be most appreciated
thanks!

---

### Post by JasonGraham on 2008-05-10
I'm brand new to linux myself and I've been struggling with this one. In Gutsy I was able to replace the driver and everything works, but Hardy is a different story. Since 
```
sudo dpkg-reconfigure xserver-xorg
``` doesn't do the same thing it did in Gutsy, I just tried replacing the driver and restarting since that seemed to work for some people under Gutsy. No luck, I get a console login. I also tried using the xorg.conf provided earlier in the thread in conjunction with replacing the driver and still got a console login. I'm out of ideas... if anyone gets it working please post the solution!

---

### Post by tuneable on 2008-05-17
For graphics support in Hardy: there is a solution for sis Xorg drivers  posted in [another]("http://ubuntuforums.org/showthread.php?t=728147") thread (i.e. post #4 and #10 in that thread). 

It resulted in a working xorg SIS driver (after compiling the source posted in that thread) on Hardy AMD64 running on a D201GLY2 motherboard. There is also a compiled binary posted for Hardy i386 that I have not tested.

---

### Post by v314m on 2008-06-05
I tried the solution. Everything works ok. Still, there is a problem; movies cannot be resized (in particular, not possible to zoom videos to the full screen)

---

### Post by juppepuputti on 2008-06-06
> **v314m said:**
> I tried the solution. Everything works ok. Still, there is a problem; movies cannot be resized (in particular, not possible to zoom videos to the full screen)
same 'problem' here. can't resize any video. I'am using 19" tft in 1280X1024 resolution.

---

### Post by tuneable on 2008-06-07
I have set up Mplayer to use the Xv driver in the "Video" tab of the preferences - not sure if that is the solution but I can report that video windows can be resized and set to full screen. And VLC works with resize/fullscreen without extra settings. 

> I'am using 19" tft in 1280X1024 resolution.

Me too.

Did you have a look at the /etc/X11/xorg.conf file as well?

Below the "device" section I currently use (Ubuntu 8.04):
```
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"SiS 671/771"
	Busid		"PCI:1:0:0"
	Driver		"sis"
	Screen	        0
	Vendorname	"SiS"
	**Option		"EnableSiSCtrl"		"yes"**
	**Option		"XvDefaultAdaptor"	"Blitter"**
EndSection
```

---

### Post by yanok on 2008-06-08
Hello,

After upgrading my distrib (debian testing) few days ago, I had the binary version of the iMedia driver that stop working (X was  update to version 7.3). This version is the one that allow good performance on D201, video playback with resize working well, etc.

In fact, X was crashing at startup after installing the freshly compiled driver. I discover that the issue is due to a mutex that was not initialized properly.

Well, as I had some little issue while making the sis_drv.so from _[iMedia sources]("http://www.linuxconsulting.ro/xorg-drivers/")_, I explain here the procedure that make it work properly :

First, the patch attached will avoid this mutex issue.

It is applicable on iMedia source code this way:
[FONT="Courier New"]
cd xf86-video-sis-imedia
patch -Np1 < ../iMedia_update.patch[/FONT]

After that :

[FONT="Courier New"]autoreconf
./configure --prefix=/usr
make
sudo make install[/FONT]

This will replace the /usr/lib/xorg/modules/drivers/sis_drv.so file. (Feel free to backup it before.)

On my side, this was sufficient for good X configuration....


BUT there is also another thing that is not clear for me.
I hope some guys could highlight this:

The iMedia driver is delivered with a XvMC library that should allow Xine/Mplayer/? players to use HW acceleration. Right.

Compilation and installation is ok (with kernel source available in your /usr/src/linux) :

[FONT="Courier New"]cd src/xvmc
make
make install[/FONT]

This install dynamics lib here : /usr/lib/libSiSXvMC.*
Then we need an appropriate XvMCConfig in /etc/X11


BTW, trying to launch "mplayer -vo xvmc ..." does not succeed, while the Xorg.log file show that XVmc is activated :

[FONT="Courier New"](...)
(II) SIS(0): Using SiS300/315/330/340/350 series HW Xv by default on CRT1
(II) SIS(0): [MC] XvMC adaptor is initialized succfully.
(II) SIS(0): Default Xv adaptor is Video Overlay
(...)[/FONT]

Does somebody know why ?

As some mutex inside the driver itself does not seems to be complete, I am thinking that the XvMc is maybe not working also... but I do not khow to check that ?

Any highlight will be appreciate.

Regards,
Yanok

---

### Post by v314m on 2008-06-10
> **tuneable said:**
> I have set up Mplayer to use the Xv driver in the "Video" tab of the preferences - not sure if that is the solution but I can report that video windows can be resized and set to full screen. And VLC works with resize/fullscreen without extra settings. 



Me too.

Did you have a look at the /etc/X11/xorg.conf file as well?

Below the "device" section I currently use (Ubuntu 8.04):
```
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"SiS 671/771"
	Busid		"PCI:1:0:0"
	Driver		"sis"
	Screen	        0
	Vendorname	"SiS"
	**Option		"EnableSiSCtrl"		"yes"**
	**Option		"XvDefaultAdaptor"	"Blitter"**
EndSection
```

thanks. Still, same situation after trying your solutions posted above here - no video resizing. Do you have D201GLYx? Which driver are you using; can you provide it?

---

### Post by crustyoz on 2008-06-18
Ubuntu 8.04 Hardy updates last night included replacements for many xorg component files. With previous releases, I could not use any of the instructions given in this thread with my D201GLY board and a plug and play 1680x1050 (or 1440x900) lcd monitor to display at these screen resolutions.

This new update improves the situation but does not solve the problem. The standard boot-up video detection selects 1680x1050 but shows bad vertical striping/image tearing in many columns across the screen. Changing to 1440x900 reduces but does not eliminate the vertical stripes. No changes were made to the "Configured Video Device" section of the /etc/X11/xorg.conf file.

To get rid of the stripes I must revert to "vesa" as the driver. That requires adding the line: '\tDriver "vesa"' line to the 'Section "Device"' part of /etc/X11/xorg.conf and that limits screen resolution to 1280x1050.

Since I do a lot of computer aided design (CAD) work, having correct aspect ratio means that circles need to look like circles, not ellipses, and squares need to look like squares, not rectangles. That is what the 1280x1050 and lesser vesa resolutions cause.

I want to make a vote of encouragement for the Ubuntu / xorg maintainers who are tackling this problem. I wish you the best of success in the near future.

---

### Post by lajthabalazs on 2008-06-28
Hi!

I'm a real noob when it comes to linux. But after finishing university I had enough of steeling software and media all day long from torrent sites, and decided to change. I also changed to a more economic system, based on the Intel D201GLY2 motherboard. After installing, I eventually faced the video driver problem, and got really confused when reading through this topic. I tried the Intel official drivers, then gave up, as Xorg failed to load, and I ended up whit an unfriendly terminal.

After a while, I installed Ubuntu Hardy Heron on my secondary rig (primary is for gaming only, but that one I don't use, enormeous power and time consumption), an Intel 945GZ based HTPC. As everything worked fine, I decided to retry the smaller PC.
Same problem, but this time, I didn't gave up, downloaded the Intel stuff [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=N&Inst=Yes&ProductID=2773&DwnldID=15443&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=N&Inst=Yes&ProductID=2773&DwnldID=15443&strOSs=39&OSFullName=Linux*&lang=eng) and was looking around for the proper way of installing. And then I found this thread:
[http://ubuntuforums.org/showthread.php?t=728147](http://ubuntuforums.org/showthread.php?t=728147)
I didn't want to recompile, so took the easy way: did step by step what ottod said to do in #4, downloaded the files too, didn't use Intels official drivers. And it worked just fine. Except of login screen not showing, because of refresh rate out of tolerable (I have a 22" LG TFT display). Also the language settings were all mixed up. I tried to login blind, and succeded. Searched for the solution, and ended editing my xorg.conf manually. Added some lines, based on

[http://en.wikipedia.org/wiki/Xorg.conf](http://en.wikipedia.org/wiki/Xorg.conf)

Basicly replaced my Monitor and Screen sections. With

        Identifier      "Generic Monitor"

Added lines 

        Horizsync       28-96
        Vertrefresh     43-60

And in Screen did some changes too:

        Identifier      "Default Screen"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1680x1050"
        EndSubSection
EndSection

Thoght that I have to share this with you.

---

### Post by repu1sion on 2008-07-03
where can i get version for Xorg 6.8.1? One from [http://www.winischhofer.eu](http://www.winischhofer.eu) works so bad. Should i update to 7.3 ?
This question is not about my home desktop system but industrial purposes. So its hard to update. And one more thing. Can some1 says is it really stable on this mobo with 17' Samsung 740N under X.Org 7.2-7.3

---

### Post by tuneable on 2008-07-20
> **v314m said:**
> thanks. Still, same situation after trying your solutions posted above here - no video resizing. Do you have D201GLYx? Which driver are you using; can you provide it?

Sorry for the late reply and sorry to see there is still trouble with your video scaling. 

My 8.04 is up-to-date and I have not noticed changes in the last few weeks. Video scaling is still working :???:

If you are still searching for a solution: The working drivers are already provided in the thread linked in post #125, so please get them there. And I hope it can be somehow be reassuring to know that the combination of the compiled drivers from that thread and the suggested changes to the xorg.conf (see also post #128 ) still work today to get scaling on 1280x1024.

---

