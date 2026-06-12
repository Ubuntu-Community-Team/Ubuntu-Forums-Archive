---
title: "Can't install ATI driver, error: &quot;unable to detect&quot;"
date: 2008-09-23
forum: Hardware
---

### Post by kendall14 on 2008-09-23
Hi, I recenlty installed Xubuntu and I am trying to install the srivers for my ATI Radan 9200 PCI video card but this is what I get:
```
kendall@kendall-ubuntu-desktop:~/Desktop$ sh ./ati-driver-installer-8.28.8.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: unable to detect
Removing temporary directory: fglrx-install
kendall@kendall-ubuntu-desktop:~/Desktop$ 

```

Any clues?:confused:

---

### Post by Neo_The_User on 2008-09-23
Go to Synaptic Package manager > search > xserver-xorg

tell me what version of xserver-xorg you have installed.

---

### Post by Nettoyer on 2008-09-23
Not sure if you did, but when I just did mine, do it via sudo as well.
Try this and see if it helps you?  You basically have most of it done ^^


1. install fglrx: ```
sudo apt-get install xorg-driver-fglrx
```
2. Went to ati site and downloaded the linux driver for my card
     ```
http://ati.amd.com/support/driver.html
```
3. Ran the install from the terminal instead of a gui: 
      ```
sudo sh ./ati-driver-installer-8-9-x86.x86_64.run
```
4. Follow the step-by-step directions in the terminal.
5. Reboot.


I know next-to-nothing about linux (I've been using it less than a week) but I hope this can help you.
-Nett

Edit: I just noticed that you were using xubuntu, whereas I was using ubuntu.

---

### Post by Neo_The_User on 2008-09-23
I'm afraid he has xserver-xorg 7.3 but his card driver only goes up to 6.9 or whatever. If his xserver-xorg is 7.3 then he needs to download the driver not for his card (The drivers from 9500 to HD 4800 series are all the same drivers)

---

### Post by Bablefish on 2008-09-23
WARNING!!!! This is not a joke, I am very serious. Some people including me have had trouble installing ATI drivers, so much so they have actually crashed there OS. That is what happened to me. I am not saying this will happen to you but there is a chance. So please back up everything on that computer you want to save, and keep your install disc handy. You might even have to find a HDD erasing program. Only then if you want install those drivers.

---

### Post by Neo_The_User on 2008-09-23
I installed the ATi drivers just fine. I'm actually really really good at installing the Ati drivers from the website including the ATi accelerator (not just the catalyst because the 60+ MB file also has a graphics accelerator kind of hidden in it) because I tinker a lot with my stable system because it is very fun to mess with drivers and stuff for me but its broken now.

As far as the booting goes, my Radeon 9800 just blew I think. I'm going to change graphics cards in a little bit probably. I get this stupid power extension cable issue that drives me crazy. Is that the problem you are talking about it not booting? If so, it's a software problem. If not, then I need to swap the GPUs around.

---

### Post by kendall14 on 2008-09-23
I do have the newer xorg which is 7.3. I tried using the newer drivers like suggested and I had it make the packages for ubuntu 8.10 and then I installed all the packages, I figured it would be better to use the packages. Then I restarted and it said it was in low res and needed set up. I set it up. Then the resolution staied low so I tried to up in when I got logged in and the only options where default and 640X480X(don't remember the refresh). The screen messed up and put a bunch of lines on it, looks bad. So I manged to log out, just knew hwere the button was even though I couldn't see it. Login looks ok, I login and still messed up. So rebooted, came up with the low resolution and still messed up desktop. Any one can help me?

---

### Post by markbuntu on 2008-09-23
fglrx does not work in Intrepid. You really need to read the release notes for these things:


[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_89_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_89_linux.html)

---

### Post by kendall14 on 2008-09-23
I'm sorry but I'm quite a bit a nood with linux, I'm not even sure what Intrepid is. But can anyone suggest any way to configure the resolution correctly. I am going to try to uninstall all the packages via apt-get remove and seeing if that works.

---

### Post by markbuntu on 2008-09-23
Intrepid Ibex is Ubuntu 8.10 and is still in testing. Xorg7.3 is part of it and is also still in testing phase. These are very unstable and should not be used except for testing purposes. You really need to go back to xorg7.1.

Besides that, your 9200 card is not supported by the proprietary ati driver fglrx. You need to be using the open source Radeon driver. You can do a google search and find instructions for it fairly easily.

---

### Post by cantinnr on 2008-09-29
I'm running a Kubuntu Hardy with xorg 7.3 I guess.
Open driver doesn't provide vga output support on my D600 laptop. I am trying to install ati driver.
I'm trying to install the 8.27.10 driver but I get the message "X Server: unable to detect".
I guess this is because of my xorg version. Is there a way to fool the ati installer so it would see my Xserver?

---

### Post by kendall14 on 2008-09-29
I did install the wrong package and even when I installed it correctly it still was funny. I ended up editing the /etc/X11/xorg.conf directly and got my display working ok. I will upload it as soon as I can and you could try basing your's off of it, you will have to edit it though.

EIDT:: HERE you go.

> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Module"
  Load  "glx"
  Load  "dri"
  Load  "drm"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 9200"
	Driver 		"radeon"
 	Option 		"XAANoOffscreenPixmaps" "true" #needed for aiglx
	Option		"AGPMode"		"4"
	Option 		"AGPFastWrite"		"yes"
        Option          "AccelMethod"    	"EXA"  #either XAA or EXA. "XAA" is the default and safe choice
        Option          "ColorTiling"   	"on"
        Option          "EnablePageFlip" 	"on" #only works with accelmethod "XAA"
        Option          "AccelDFS"       	"true" #seemed to speed things up using EXA acceleration
        Option          "TripleBuffer"   	"true" #This *might* help if you use something like Beryl and have slow video playback.
        Option          "DynamicClocks"  	"off"   #This is for laptop users, it saves energy when in battery mode.
        Option          "DMAForXv"       	"true" #This can speed up movie playback but can in rare cases case instability
        Option          "GARTSize"       	"64"   #This is the size of the "GART" that xorg will use.
	Option		"DMAForXv"	 	"true"
	Option		"ForceTVOut"	 	"true"
        Option          "monitor-VGA"	 	"Compaq 7500"
        Option		"MonitorLayout"  	"LCD, CRT"
        Option		"CRT2Position"   	"RightOf"
        Option		"MetaModes"      	"1280x1024-1024x768"
        Option		"MergedXinerama" 	"on"
        Option		"MergedNonRectangular"  "true"
        Option		"MergedFB"              "true"
	Option		"RenderAccel"	 "true"
 	Option		"BusType"	 "PCI"
        BusID           "PCI:1:9:0"
EndSection

Section "Monitor"
        Identifier      "Compaq 7500"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-140
EndSection

Section "Screen"
        Identifier      "Default Screen1"
        Device          "ATI Technologies, Inc. Radeon 9200"
        Monitor         "Compaq 7500"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "DRI"
 Group        "video"
 Mode         0666
EndSection

#Section "Extensions"
#        Option "Composite" "Enable"
#EndSection

Section "ServerLayout"
        Option          "AIGLX"         "true"
        Identifier      "Default Layout"
        Screen          "Default Screen1"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

---

### Post by cantinnr on 2008-09-30
Kendall14, from your xorg.conf, it looks like you're using the radeon driver
> Section "Device"
Identifier "ATI Technologies, Inc. Radeon 9200"
Driver "radeon"

I think this is the xorg open driver for ati. The ati
 driver is fglrx.
I'm also using the radeon driver, which works for vga/TV out but I'm experiencing problems with desktop effects on KDE4.

---

### Post by kendall14 on 2008-09-30
I ment I'm not using the one from ati. At least I believe I'm not lol I had to search to just get this far. Could you post yours, I'm curious as to the tv part since I can't get mine working on tv.

---

### Post by Bizkit45 on 2008-11-18
first of all hy to all btw i am newbie to the linux, but getting bette every day :)

second of all : HELP ME PLZ

i have radeon 9000 ans as i can see there are no that "propiearity" or somthing, drivers for this card. so now i am wondering how to install drivers so i can get COD to play by wine.

p.s. : radeon 9000 rv250 i think it is 32RAM is it enough to run COD by wine? or am i missing something here?

output of fglrx :

fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

tnx in advance........for the record i tryed a lot of solutions over the internet but none show any resoults.

---

