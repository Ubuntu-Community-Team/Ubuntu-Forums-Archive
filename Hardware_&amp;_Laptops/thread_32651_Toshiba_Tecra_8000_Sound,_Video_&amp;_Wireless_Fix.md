---
title: "Toshiba Tecra 8000 Sound, Video &amp; Wireless Fixes"
date: 2005-05-08
forum: Hardware &amp; Laptops
---

### Post by dbott67 on 2005-05-08
_**Installing Ubuntu Linux on a Toshiba Tecra 8000 Laptop**_

**Major disclaimer**

Virtually eveything here has been compiled based upon the work of others in these forums, most noticably **Buellman** who has come off the bench to [blast a couple of home runs](mms://a1503.v108692.c10869.g.vm.akamaistream.net/7/1503/10869/v0001/mlb.download.akamai.com/10869/library/open/ws_history/93ws_gm7_phitor_carter_350.wmv?ct1=mlb)*for me in getting my sound card working (in both Warty & Hoary)!  The only thing I've done is to make some minor changes to the hard work of others so that that I don't have to use **vi** ever again in my life! :)

I also had to do some major googling to find out about hsync & vsync rates and Modelines to get my display resolution working.  Again, all I've done is compile it in one spot.

The wireless fix/workaround for my D-Link DWL-650+ was borrowed from a post by **snop**; I just changed the module for my NIC (acx_pci).  It does not appear to be an issue for me any longer now that I'm running Hoary, but I used it frequently in Warty.

Anyhow, I've put this together for my own reference for future re-installs and thought that I would share it with other Tecra users.

-Dave

* Oh, the irony of posting a Windows Media Video file in a Linux forum, but this is a great video of Buellman (wearing a Joe Carter uniform)!  Bottom of the ninth, two out, two on, two strikes...

**************************************************************
**************************************************************
**************************************************************

Specifications for my Toshiba Tecra 8000:

Model: PAT800C R000
CPU: Intel PII-300 MHz
Memory: 256 MB **
Hard Drive: 8 GB Hard Drive
Video Card: NeoMagic NM2200 [MagicGraph 256AV] (2.5 MB RAM)
Sound Card: Yamaha 3D sound effect-enabled OPL3-SA3
LCD: 14.1"
DVD
NIC: D-Link DWL-650+ (uses axc_pci driver, not acx_100)

More info about Toshiba Laptops here: 
[http://linux.toshiba-dme.co.jp/linux/eng/spec.php3?model=PAT800](http://linux.toshiba-dme.co.jp/linux/eng/spec.php3?model=PAT800)
[http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/tecra_8000.pdf](http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/tecra_8000.pdf)

**************************************************************
**************************************************************
**************************************************************

_**Issues with Ubuntu Linux 5.04 (Hoary):**_

**A. Video Resolution:**

After fresh installation of Ubuntu 5.04, video resolution was only 640x480 with 1" black band along right side and 1/4" along bottom.  Issue appears to be related to hsync & vsync, as well as Modeline settings.  Secondary issue with performance may be related to default colour depth of 24 (changing colour depth to 16 increases performance noticably).

1. Edit /etc/X11/xorg.conf

Added/changed the following lines in "Monitor" Section:

Section "Monitor"
	Identifier	"Generic Monitor"
	***HorizSync	30-64***
	***VertRefresh	50-100***
	Option		"DPMS"
	***Modeline "640x480"     25.175 640  664  760  800   480  491  493  525 #60Hz***
        ***Modeline "800x600"     40     800  848  968 1056   600  601  605  628 +hsync +vsync***
        ***Modeline "1024x768"    65    1024 1032 1176 1344   768  771  777  806 -hsync -vsync***
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NeoMagic Corporation NM2200 [MagicGraph 256AV]"
	Monitor		"Generic Monitor"
	***DefaultDepth	16***

2. Save file and restart

**************************************************************

**B. Sound** (many thanks to Buellman who posted the fix --- I've made a few changes for the newbie, such as using gedit rather than vi and changed the location of step 2):

1.) sudo apt-get install esound-clients
2.) sudo mv /etc/modprobe.d/alsa-base /home/your_name/backup
3.) sudo gedit /etc/modprobe.d/tecra_sound
# ALSA Configuration.
alias snd-card-0 snd-opl3sa2

# some stuff for the OSS drivers
alias char-major-14 snd-pcm-oss
alias sound-slot-0 snd-card-0

# aliases for sound card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
4.) sudo gedit /etc/modules
snd-opl3sa2 dma1=1 dma2=0 fm_port=0x388 irq=5 isapnp=0 midi_port=0x330
port=0x538 sb_port=0x220 wss_port=0x530 <--- its one long row!
5.) refering to this link [http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567) i
only did:
sudo apt-get install libesd-alsa0
6.) restart
7.) have fun 

**************************************************************

These 2 things are the only problems I've noticed in Hoary.  
Everything else appears to work as it should.


**************************************************************
**************************************************************
**************************************************************

_**Issues with Ubuntu Linux 4.10 (Warty):**_

**A. Wireless Problems:**

In Ubuntu 4.10 (Warty), wireless access seemed to drop out with some regularity.  Some research in ubuntuforums led me to *borrow* the following script from **snop** (who wrote the original):

#############################################

#!/bin/bash

rmmod acx_pci
modprobe acx_pci
/etc/init.d/networking restart

##############################################

The issue appears to be resolved in Ubuntu 5.04 (Hoary)

**************************************************************

**B: Sound Issues** in Ubuntu 4.0 (Warty)

Enabling Sound on Toshiba Tecra 8000 in Ubuntu Linux 4.0 (Warty).  I'm pretty sure Buellman posted this fix as well (apologies to the original author if I'm mistaken).

1) Edit /etc/modutils/alsa-base

# ALSA Configuration.
alias snd-card-0 snd-opl3sa2

# some stuff for the OSS drivers
alias char-major-14 snd-pcm-oss
alias sound-slot-0 snd-card-0

# aliases for sound card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

2) Open terminal and type "sudo update-modules"

3) Edit /etc/modules

snd-opl3sa2 dma1=1 dma2=0 fm_port=0x388 irq=5 isapnp=0 midi_port=0x330 port=0x538 sb_port=0x220 wss_port=0x530 <--- its one long row!

4) Re-boot

**************************************************************
**************************************************************
**************************************************************

Thanks to all who shared their knowledge & wisdom in getting these things to work!

-Dave

---

### Post by samstarling on 2005-11-26
Thanks very much Dave, this is really useful! Looks like you've got the exact same laptop as me - although I've not got a DVD drive... My thanks also to all the people whose tips you've brought together here.

---

### Post by louman on 2006-02-18
Very nice guide, especially the more-elaborate fix for the video issues..
but I have one question:
Do you use the "vesa" video driver instead of "neomagic"?
Is it normal that the "vesa" video driver outperforms the "neomagic" driver with flying colors? Does the vesa driver even make use of the Neomagic card's GPU, or is it all software rendering? 
For some reason, vesa is far superior (at least with my Tecra 8000) than neomagic as a video driver for X. 
Any insight would be appreciated, thanks!

---

### Post by dbott67 on 2006-02-20
Hi louman,

I've been using the neomagic driver (the device was detected during installation & I never tried changing it).

I have noticed that the rendering is slow with the 'neomagic' driver, but I figured it was more related to the age of my laptop, as opposed to the driver.  I'm going to try the vesa driver & see what happens (I'll post my findings).

As for whether vesa uses the gpu on the card, I don't know.  Perhaps someone else with more knowledge in this area can fill us in).

-Dave

---

### Post by dbott67 on 2006-02-20
I've loaded the vesa driver as opposed to the neomagic and have not really noticed that much of a difference (although scrolling up & down through web pages does seem a little faster with the vesa... hard to tell). 

Running video in VLC offers pretty decent performance.

I'll run it like this for a while and see if I notice any major differences.  Where do you notice the biggest differences between neomagic & vesa?

-Dave

---

### Post by louman on 2006-02-21
interestingly enough, I managed to get the neomagic driver to perform just about as good as the vesa driver was before, perhaps better. the only issue is that direct rendering is disabled, and im not sure if it's even supported by the card (GL anything is HORRIBLY slow)

I'll look back at what I did to see if there's an explanation of why the card started performing normal again.

---

### Post by gmmech on 2006-04-16
Thank You Thank You, I have been struggling with the sound issue on the Tecra 8000 for 4 days, none of the other related threads worked. Yours worked Like a charm!

---

### Post by mjoethvitnir on 2006-04-19
The video fix worked when I had "30 - 64" and "50 - 100" (with spaces) but I can't get the resolution to 1024.768 without most of the screen actually disappearing off the screen. That isn't the problem though, my issue at the moment is still with the sound, I did everything exactly as written here to fix the sound and I'm not getting anything. It did work with gnome on one install but I'm trying things according to this thread at the moment -> [http://www.ubuntuforums.org/showthread.php?t=86586](http://www.ubuntuforums.org/showthread.php?t=86586) , so I started with a server install and then installed xubuntu-desktop. Are there more things I need to install? At the moment there still doesn't appear to be any soundcard detected at all.

It probably goes without saying that I'm also only a beginner linux user and very little of this makes any sense to me, so any help will be greatly appreciated.

Edit: I should also mention I'm running breezy, but like I said this fix worked once on an install last week, now I'm stuck again.

---

### Post by Tom Tiger on 2006-04-19
I've ran several 8000's with debian (mostly knoppix machines) and video I could allways get to work, usually after editing the xf86config (xorg.conf in ubuntu) for sound I allways had a problem, but you can also use OSSfree and then it works.

---

### Post by mjoethvitnir on 2006-04-19
Well for some strange reason the sound fix always seems to work if I do that before altering the xorg.conf file, but I'm still stuck with a horribly annoying resolution of 800x600.

---

### Post by SteveHoffmanUK on 2006-10-03
Excellent HOWTO on this laptop. Have the same problem on the display as described above, Edited the xconfig files using copy/paste, put in the spaces between "30 - 60" and "50 - 100" as suggested, restarted but I am still geting the black band on the right and bottom and find only these options for display settings:

Default
320x240@95
324x240@75
320x240@73
320x240@60

One question: am I correct to assume that you leave in the "DPMS" and just inset those three lines after that? (Newbie here)

Many thanks

---

### Post by dbott67 on 2006-10-03
I'm pretty sure that I left the "DPMS" in my xorg.conf file (in my first post, I just copied & pasted the text in, so I'm pretty sure it's correct).  Having said that, I have re-installed Ubuntu a few times since then, going to Breezy and recently to Dapper.  I don't recall having to piddle around with *anything* to get Dapper working.  I'm pretty sure that everything worked right after first install --- video, audio & wifi.

-Dave

---

### Post by SteveHoffmanUK on 2006-10-03
Dave

Thanks for the reply. I forgot to say in my message that I am working with a Dapper Xubuntu install, even though the message is in a Warty forum - I just replied to the thread that seemed most helpful and relevant.

I can't imagine that it makes any difference that this is Xubuntu and not Ubuntu, but maybe I should try Ubuntu install just in case. Given the small memory in my Tecra, Xubuntu seemed the best solution.

So, Dapper doesn't overcome the problem for my Tecra, at least. Any other suggestions would be welcome.

Steve

---

### Post by dbott67 on 2006-10-03
I think you're correct in stating that there won't be any difference.  As far as I know, the only difference between the (kx)ubuntu distros are the actual DE (Gnome installs 'ubuntu-desktop', KDE installs 'kubuntu-desktop' and XFCE installs 'xubuntu-desktop').  You can install any or all of these packages through Synaptic to switch between desktop environments.

I can post the xorg.conf from my Tecra 8000 tonight when I get home (at work right now... won't be home for another 8 hours)

---

### Post by dbott67 on 2006-10-03
Here's the xorg.conf from my Tecra 8000 running Dapper
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"NeoMagic Corporation NM2200 [MagicGraph 256AV]"
	Driver		"neomagic"
	BusID		"PCI:0:4:0"
EndSection

Section "Monitor"

	Identifier "Generic Monitor"

	HorizSync 30-64

	VertRefresh 50-100

	Option "DPMS"

	Modeline "640x480" 25.175 640 664 760 800 480 491 493 525 #60Hz

	Modeline "800x600" 40 800 848 968 1056 600 601 605 628 +hsync +vsync

	Modeline "1024x768" 65 1024 1032 1176 1344 768 771 777 806 -hsync -vsync

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NeoMagic Corporation NM2200 [MagicGraph 256AV]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

-Dave

---

### Post by SteveHoffmanUK on 2006-10-04
Dave

Brilliant. I don't know how your version differs, but I just copy/pasted the whole thing to replace mine, and the horrible black bands have disappeared and the graphics look beautiful.

Thanks so much for your help.

Two further questions: 

1.Did you run the automatic xorg update coding suggested in the comments?
2. This Tecra has only 64Mb of RAM and is pretty slow. Would adding another 64Mb speed things up, or am I bound by processor speed?

Steve

---

### Post by SteveHoffmanUK on 2006-10-04
Now onto the sound problem. I've followed your HOWTO for the Tecra sound:
> 1.) sudo apt-get install esound-clients
2.) sudo mv /etc/modprobe.d/alsa-base /home/your_name/backup
3.) sudo gedit /etc/modprobe.d/tecra_sound

but there is no tecra_sound file in my modprobe.d folder. There is something called toshiba_acpi.modprobe if that's at all relevant?

---

### Post by dbott67 on 2006-10-04
> **SteveHoffmanUK said:**
> Dave

Brilliant. I don't know how your version differs, but I just copy/pasted the whole thing to replace mine, and the horrible black bands have disappeared and the graphics look beautiful.

Thanks so much for your help.


Glad it worked.

> **SteveHoffmanUK said:**
> Two further questions: 

1.Did you run the automatic xorg update coding suggested in the comments?
2. This Tecra has only 64Mb of RAM and is pretty slow. Would adding another 64Mb speed things up, or am I bound by processor speed?

Steve

1. Nope... just did the Dapper install and it configured automagically.  I've left it alone since then.

2. Yes... in fact, if you can add the max (256 total, I think) it would give you the best performance.  When I first installed Ubuntu (Warty, circa Mar. 2005) I tried all of the desktop environments and window managers, looking to increase performance.  I did a memory test of a few of the major DEs here:
[http://www.ubuntuforums.org/showpost.php?p=337695&postcount=4](http://www.ubuntuforums.org/showpost.php?p=337695&postcount=4)

Although some DEs use less memory, as soon as you open some apps (OpenOffice, Firefox, etc.) the memory usage jumps through the roof.  Even XFCE used 172 MB of RAM with nothing running.  I found that Opera gave the best browsing performance & AbiWord was a nice WP.

-Dave

---

### Post by dbott67 on 2006-10-04
> **SteveHoffmanUK said:**
> Now onto the sound problem. I've followed your HOWTO for the Tecra sound:


but there is no tecra_sound file in my modprobe.d folder. There is something called toshiba_acpi.modprobe if that's at all relevant?

I'll have to take a look at my sound configuration tonight. With Dapper, I never have to configure the sound, video or wifi --- it just worked.  I'll post any config files here --- it may be a little later than last night as I probably won't get a chance to post until after 9 pm EST (GMT -5).

Have you tried just creating the 'tecra_sound' file and pasting the contents into it?

-Dave

---

### Post by SteveHoffmanUK on 2006-10-04
Dave

No, haven't tried creating the tecra_sound file because I wasn't sure whether what you quoted was the whole of its contents or just an excerpt. I guess it won't do any harm to do that and see what happens.

Thanks again for continuing to help. It is clear that my Tecra is going to be more difficult to get working properly than yours, but I always enjoy a challenge (up to a point).

---

### Post by dbott67 on 2006-10-04
I don't have a 'tecra_sound' either.  A little deductive reasoning here leads me to believe that the file in question is 'alsa-base', as the original post I made instructs us to move alsa-base to another directory.

So, with that in mind, here is the contents of my 'alsa-base' in Dapper:
```

dbott@tecra:/etc/modprobe.d$ cat alsa-base

# autoloader aliases
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd modprobe --ignore-install snd $CMDLINE_OPTS && { modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe -Qb snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe -Qba snd-seq-midi snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
```

Here is the output of 'sudo lsmod | grep snd' (shows all sound driver modules):

```
dbott@tecra:/etc/modprobe.d$ sudo lsmod | grep snd
snd_opl3sa2            17640  1
snd_opl3_lib           10624  1 snd_opl3sa2
snd_hwdep               9376  1 snd_opl3_lib
snd_cs4231_lib         26752  1 snd_opl3sa2
snd_mpu401_uart         7808  1 snd_opl3sa2
snd_rawmidi            25504  1 snd_mpu401_uart
snd_seq_device          8716  2 snd_opl3_lib,snd_rawmidi
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_opl3sa2,snd_cs4231_lib,snd_pcm_oss
snd_timer              25220  3 snd_opl3_lib,snd_cs4231_lib,snd_pcm
snd                    55268  13 snd_opl3sa2,snd_opl3_lib,snd_hwdep,snd_cs4231_lib,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_cs4231_lib,snd_pcm
```

Hope this helps.

-Dave

---

### Post by SteveHoffmanUK on 2006-10-05
Dave

I'm not that confident with terminal and I think you assume that I am more skilled than I am with Linux. No luck so far with the sound. Here is what I've done so far:

I moved backup (created by following the procedures in your original posting) back to its original folder and renamed it 'alsa-base'.
2. Overlaid the contents of my alsa-base with yours.
3. Ran a sudo lsmod | grep snd command and got this:
```
snd_opl3sa2            17640  1
snd_opl3_lib           10624  1 snd_opl3sa2
snd_hwdep               9376  1 snd_opl3_lib
snd_cs4231_lib         26752  1 snd_opl3sa2
snd_mpu401_uart         7808  1 snd_opl3sa2
snd_rawmidi            25504  1 snd_mpu401_uart
snd_seq_device          8716  2 snd_opl3_lib,snd_rawmidi
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_opl3sa2,snd_cs4231_lib,snd_pcm_oss
snd_timer              25220  3 snd_opl3_lib,snd_cs4231_lib,snd_pcm
snd                    55268  13 snd_opl3sa2,snd_opl3_lib,snd_hwdep,snd_cs4231_lib,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_cs4231_lib,snd_pcm

``` 

Restarted, but no sound. So then I went back to your original post and tried to execute the rest of the recommended steps, but they refer to a file called /etc/modules, and I have no such file.

I am at this point mystified about what I should be doing next and not sure whether what I've done so far is correct. Maybe you can straighten me out, but you'll need to assume in your instructions I'm an idiot.

---

### Post by dbott67 on 2006-10-05
Hi Steve,

Just don't give up! :)  Sometimes these things can be a royal P-I-T-A, but if you're like me, it can be very satisfying to solve the problem.  I'm not an expert (in linux, anyways) but I'll try to be as explicit as I can (not only for you, but for all the future people that might come across this thread.

Anyhow, it appears as though your sound drivers are loaded (which is good) and that they are the same as mine (also good).  I found this very comprehensive guide here about getting sound working in Ubuntu: [http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound)

Here's a couple of screenshots of my sound config from Gnome (as you're running XFCE, you may have to hunt around for the 'sound settings').  Notice my sound card is set to ALSA-mixer (not OSS-mixer).

A few things before doing anything too drastic, though.  I recall that sometimes the sound card would just be 'muted' and it was as simple as clicking the mouse to solve it (or pressing M in alsamixer).  You can type 'alsamixer' in the terminal and you should see a screen similar to my screenshot **alsa3.jpg**.  Make sure that the MASTER channel is unmuted (muted channels display MM under the vertical bar) and that the volume is set to a reasonable level (mine is 87).  Use the left & right arrow keys to navigate to the different channels, and the up & down arrows to adjust the volume.  The M key toggles between muted and unmuted.

As for the link above, here's what I get when I run 'aplay -l' & 'lspci -v':
```
dbott@tecra:~$ aplay -l

**** List of PLAYBACK Hardware Devices ****

card 0: OPL3SA23 [Yamaha OPL3-SA23], device 0: CS4231 [Yamaha OPL3-SA23]

  Subdevices: 1/1

  Subdevice #0: subdevice #0


dbott@tecra:~$ lspci -v

0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 02)

	Subsystem: Toshiba America Info Systems: Unknown device 0001

	Flags: bus master, medium devsel, latency 64

	Memory at e0000000 (32-bit, prefetchable) [size=256M]



0000:00:04.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 12) (prog-if 00 [VGA])

	Subsystem: Toshiba America Info Systems: Unknown device 0001

	Flags: bus master, medium devsel, latency 64, IRQ 11

	Memory at df000000 (32-bit, prefetchable) [size=16M]

	Memory at ff800000 (32-bit, non-prefetchable) [size=4M]

	Memory at ff700000 (32-bit, non-prefetchable) [size=1M]

	Capabilities: <available only to root>



0000:00:05.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)

	Flags: bus master, medium devsel, latency 0



0000:00:05.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])

	Flags: bus master, medium devsel, latency 64

	I/O ports at fe60 [size=16]



0000:00:05.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])

	Flags: bus master, medium devsel, latency 64, IRQ 11

	I/O ports at ffe0 [size=32]



0000:00:05.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)

	Flags: medium devsel, IRQ 9



0000:00:09.0 Communication controller: Toshiba America Info Systems FIR Port (rev 23)

	Subsystem: Toshiba America Info Systems: Unknown device 0001

	Flags: bus master, slow devsel, latency 64, IRQ 11

	I/O ports at ff80 [size=32]



0000:00:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC95 (rev 07)

	Subsystem: Toshiba America Info Systems Satellite Pro

	Flags: bus master, slow devsel, latency 0, IRQ 11

	Memory at 28000000 (32-bit, non-prefetchable) [size=4K]

	Bus: primary=00, secondary=01, subordinate=04, sec-latency=0

	Memory window 0: 20000000-21fff000 (prefetchable)

	Memory window 1: 22000000-23fff000

	I/O window 0: 00001000-000010ff

	I/O window 1: 00001400-000014ff

	16-bit legacy interface ports at 0001



0000:00:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC95 (rev 07)

	Subsystem: Toshiba America Info Systems Satellite Pro

	Flags: bus master, slow devsel, latency 0, IRQ 11

	Memory at 28001000 (32-bit, non-prefetchable) [size=4K]

	Bus: primary=00, secondary=05, subordinate=08, sec-latency=0

	Memory window 0: 24000000-25fff000 (prefetchable)

	Memory window 1: 26000000-27fff000

	I/O window 0: 00001800-000018ff

	I/O window 1: 00001c00-00001cff

	16-bit legacy interface ports at 0001



0000:00:0d.0 Multimedia controller: C-Cube Microsystems Cinemaster C 3.0 DVD Decoder (rev 02)

	Subsystem: C-Cube Microsystems Cinemaster C 3.0 DVD Decoder

	Flags: bus master, medium devsel, latency 64, IRQ 11

	I/O ports at ee00 [size=256]

	Capabilities: <available only to root>



0000:05:00.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface

	Subsystem: D-Link System Inc DWL-650+ PC Card cardbus 22Mbs Wireless Adapter [AirPlus]

	Flags: bus master, medium devsel, latency 64, IRQ 11

	I/O ports at 1800 [size=32]

	Memory at 26010000 (32-bit, non-prefetchable) [size=4K]

	Memory at 26000000 (32-bit, non-prefetchable) [size=64K]

	Capabilities: <available only to root>
```

The 'lspci -v' command does not seem to show any sound devices, but 'aplay -l' does --- not sure what that means, but I've definitely got sound, so I know it works.


-Dave

BTW, I'm connecting remotely to my Tecra laptop in the screenshots, so the images are **VNC: LibVNCServer** window in the lower right-hand corner.

---

### Post by dbott67 on 2006-10-05
Okay... how's this for weird?  I ran the update manager just after I posted & I lost my sound.  A couple of reboots and some fiddling with alsamixer, etc. and still no sound.  My music player (beep) and video player worked, just no sound.  Anyhow, I read through more of the post above and tried this part:
> 
**_Getting the ALSA drivers from a *fresh* kernel_**

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.

A faster way, is to just remove the problematic packages and reinstall them cleanly.

(1) Remove these packages
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```

(2) Reinstall those same packages
```
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

* VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
      
```
sudo apt-get install gdm ubuntu-desktop
```

(3) Reboot

* VERY IMPORTANT NOTE: Xubuntu (XFCE) users have reported that packages 'gdm' and 'xubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following

```
sudo apt-get install gdm xubuntu-desktop
```

(3) Reboot

In your case, you might need to re-install **gdm & xubuntu-desktop** (I needed to re-install **gdm & ubuntu-desktop**).  Anyhow, after re-booting everything worked again.  Perhaps there was some update in the past few weeks that borked the sound & seeing as I just updated this morning, mine got borked, too (just guessing here).

-Dave

---

### Post by SteveHoffmanUK on 2006-10-05
Dave

Weird, yes. Probably caused not by a dodgy update but by your trying to help me! :) 

I also did the uninstall/reinstall as per the instructions you copied, and I don't seem to have any sound, although, come to think of it, how do I know? Is there some easy app or function to test it with? Must check that.

I do wish they didn't have to delete the desktop when they do these things. It is always a heart-stopping moment for newbies.

Anyway, I shall not give up, but will explore the Comprehensive Sound Problems thread and see where it gets me. I am planning to deliver this laptop to my daughter tomorrow, so I only have a few hours left, otherwise she will get a mute laptop for the moment. I have ordered some additional memory for the Tecra and when it comes I will get the laptop back for the installation, will probably then install Ubuntu rather than Xubuntu and then really try to sort the problem out. We're also shortly off to Spain for two weeks, so it may be a while before I reappear. 

For further report, as they say.

---

### Post by gainground on 2006-12-18
Hi

I tried the video fix mentioned in this thread, and it hasn't worked for me yet.  I've triple checked the syntax and I'm still stuck at low res. with no way to change it (though I'm not very familiar with any linux distro yet).  Would someone please give me some troubleshooting tips?

Thanks

---

### Post by dbott67 on 2006-12-18
What make & model computer do you have?  Can you post the output of:
```
dbott@thedrake:~$ **sudo lshw -C video**
Password:
  *-display:0
       description: VGA compatible controller
       product: RV350 AP [Radeon 9600]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@01:00.0
       version: 00
       size: 256MB
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master cap_list
       configuration: driver=fglrx_pci
       resources: iomemory:e0000000-efffffff ioport:d800-d8ff iomemory:bf800000-bf80ffff irq:217
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV350 AP [Radeon 9600] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@01:00.1
       version: 00
       size: 256MB
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       resources: iomemory:c0000000-cfffffff iomemory:bf000000-bf00ffff

```
and your xorg.conf file:
```
cat /etc/X11/xorg.conf
```

Thanks,
Dave

---

### Post by jon.nichols on 2007-01-08
New to Linux/Ubuntu and this thread was a GODSEND.  Thanks for all the great info.  I'm running a Toshiba Tecra 8000 as well and the info here was enough to get it configured properly.  I'm actually posting this reply from the laptop now.

That's an amazing feat for me...since this is my first time using a non-microsoft OS.

Are there any other tweaks one would suggest for the Toshiba Tecra 8000 laptops?  Thanks again!

---

### Post by imho74 on 2007-01-26
Hello,

maybe that's interresting for some one: I've got TV-out working on my Toshiba Tecra 8000. The output is monochrome, bumpy and I can only see a little section of my screen but it works.

Note first my hardware:

```
christian@Unaha-Closp:~$ sudo lshw -C video
  *-display
       description: VGA compatible controller
       product: NM2200 [MagicGraph 256AV]
       vendor: Neomagic Corporation
       physical id: 4
       bus info: pci@00:04.0
       logical name: /dev/fb0
       version: 12
       size: 16MB
       width: 32 bits
       clock: 33MHz
       capabilities: vga bus_master cap_list fb
       configuration: depth=16 frequency=75.69Hz mode=1024x768 visual=truecolor xres=1024 yres=768
       resources: iomemory:df000000-dfffffff iomemory:ff800000-ffbfffff iomemory:ff700000-ff7fffff irq:11

```

Secondly my xorg.conf:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load	"dbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NeoMagic Corporation NM2200 [MagicGraph 256AV]"
	Driver		"neomagic"
	BusID		"PCI:0:4:0"
EndSection

Section "Monitor"
	Identifier	"Standardbildschirm"
	Option		"DPMS"
	## New values:
	HorizSync 	36-52
	VertRefresh 	36-60
	Modeline 	"640x480" 25.175 640 664 760 800 480 491 493 525 #60Hz
	Modeline 	"800x600" 40 800 848 968 1056 600 601 605 628 +hsync +vsync
	Modeline 	"1024x768" 65 1024 1032 1176 1344 768 771 777 806 -hsync -vsync
	
	## Old values:
	## HorizSync	36-52
	## VertRefresh	36-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NeoMagic Corporation NM2200 [MagicGraph 256AV]"
	Monitor		"Standardbildschirm"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Now what I have done to get a video output to my TV screen:

I put the *vesafb* module into the file */etc/modules*:

```
# /etc/modules: kernel modules to load at boot time.

lp
psmouse
vesafb
snd-card-0
opl3sa2 io=0x220 mss_io=0x530 mpu_io=0x330 irq=5 dma=1 dma2=0
mpu401
sound
ad1848

``` 

And I put the following line to the kernel command line in */boot/grub/menu.lst*:

```
append="video=vesafb:ywrap,mtrr" vga=791
```

Now the relevant section of my *menu.lst* looks like this:

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 append="video=vesafb:ywrap,mtrr" vga=791 ro
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot
```

After a reboot I can switch to the TV screen by pressing [FN] + [F5] three times.

I think that can be improved. Maybe someone has an idea?

Regards,
imho

---

### Post by mleung on 2007-04-03
David,
Thanks for your assistance in setting up my Toshiba Tecra 8000 with Ubuntu!  At first, I was having a lot of frustration running the Live CD to install Ubuntu onto the Tecra.  I couldn't get Ubuntu installed via traditional means because of all the time it took (CD drive kept spinning and spinning), and then because of all the font and VGA resolution problems.  I solved it though via an un-elegant and unconventional means... by using a second laptop to load the OS.  Here's what I did:

1.  Took the hard drive out of my Toshiba Tecra 8000 laptop.
2.  Put my old 6.4 Gb hard drive from the Toshiba Tecra into and IBM T42 Thinkpad.
3.  Ran the Ubuntu Live CD install disk.  Installed all of Ubuntu onto the hard drive.
4.  Took the hard drive out of the T42 and put it back into the Toshiba.
5.  Booted the Tecra 8000.  Tecra could not boot because of problems processing the xorg.conf file.
6.  (here's where you helped!)  Put the hard drive back into the T42.  Booted up Ubuntu on the T42.  Took your xorg.conf file and replaced it in the etc directory.  Hit Ctrl-Alt-Backspace to restart X.  Nothing happens.  
7.  Took out the hard drive from the T42 and placed it back into the Toshiba.  Booted up Ubuntu and it works perfectly!

I wish there was an easier way to do this.  Say, at the point of turning on the Tecra, if you could exit into a terminal mode so that you can vi the xorg.conf file to your liking.  Then, I would have had one less swap of hard drives from one computer to another!

Thanks again.  I'm one happy Ubuntu camper now!
Marty

---

### Post by dbott67 on 2007-04-03
Hi Marty,

Glad you found some answers in the Tecra How-To.

As for the HD switch, there may be an easier way.  Ubuntu also offers an "alternate installation CD." Go to one of the download sites (such as [http://mirrors.gigenet.com/ubuntu/6.10/](http://mirrors.gigenet.com/ubuntu/6.10/)) and look for the appropriate ***alternate*** .iso (probably [http://mirrors.gigenet.com/ubuntu/6.10/ubuntu-6.10-alternate-i386.iso](http://mirrors.gigenet.com/ubuntu/6.10/ubuntu-6.10-alternate-i386.iso) for your Tecra).

The only difference is that the alternate is not a "Live CD"; it has the command-line installer and is generally required when you have video problems during installation using the Live CD.

-Dave

---

### Post by kemo on 2007-04-04
Can someone PLEASE help as i have very little hair left to pull out!!!!!

Can someone please advise me where to get video drivers for my tecra 8000.

I am using XP, with the Neomagic driver, which works fine for one monitor, but I cannot get it to work with multi-monitor.  It is possible in Win 98, but I have software that needs 2000 or beter to run.

Thanks in advanced

Kemo

<keeping fingers crossed>

---

### Post by dbott67 on 2007-04-18
Try these drivers:
[http://www.video-drivers.com/drivers/113/113152.htm](http://www.video-drivers.com/drivers/113/113152.htm)

-Dave

---

### Post by Lgbrave on 2007-06-08
I followed ur video fix u posted up, and it didnt work the way u posted, im also using 6.10 
i had to edit the screen one the most and drop in       Modeline "1024x768" 65 1024 1032 1176 1344 768 771 777 806 -hsync -vsync  in the moniter part and got it to work

Section "Screen"
	Identifier	"Default Screen"
	Device		"NeoMagic Corporation NM2200 [MagicGraph 256AV]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600"
	EndSubSection
EndSection


and this for moniter 

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	30-64
	VertRefresh	50-100
      Option		"DPMS"
      Modeline "1024x768" 65 1024 1032 1176 1344 768 771 777 806 -hsync -vsync  
EndSection


and got it working

---

