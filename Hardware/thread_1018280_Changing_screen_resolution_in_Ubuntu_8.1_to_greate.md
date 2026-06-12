---
title: "Changing screen resolution in Ubuntu 8.1 to greater than 800x600"
date: 2008-12-21
forum: Hardware
---

### Post by mossrunner02 on 2008-12-21
I recently installed Ubuntu 8.10 on my laptop.  My machine is a Sony Vaio VGN-FW170J with a hi-def widescreen with a 1600x900 resolution.  Currently everything in Ubuntu 8.10 seems to be working fine, but I have not been able to figure out how to increase the screen resolution.  The highest resolution I can select under the Screen Resolution option is 800x600 and with my laptop screen it obviously doesnt look right.  If anyone could help me fix this so that I can view configure my display settings to the right configuration, I would greatly appreciate it.  Thanks.

---

### Post by SlidingHorn on 2008-12-22
try running

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by mossrunner02 on 2008-12-22
I tried running that and went through the steps but all that it referred to was the keyboard layouts.  Nothing about changing the screen resolution was mentioned.  Is there another way of doing this?

---

### Post by SlidingHorn on 2008-12-22
Option #1:
-backup your xorg.conf (sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old)
-run the "sudo dpkg-reconfigure xserver-xorg" again

Option #2:
you can also try editing your /etc/X11/xorg.conf file and manually adding resolutions in the display & screen sections.

If these don't work, I would think it's a driver issue.  If that's the case, I'd just download the manufacturer's proprietary drivers

---

### Post by mossrunner02 on 2008-12-22
I typed in sudo mv/etc/x11/xorg.conf into the terminal in an attempt to manually add the resolutions in the display and screen sections but it says command not found.  did i type this in correctly?

---

### Post by SlidingHorn on 2008-12-22
looks like you're missing a space b/t "mv" and "/etc/..."

--edit--

FYI you may need to copy the contents of your old xorg.conf file and paste it into the new one to start off...then make your adjustments

---

### Post by mossrunner02 on 2008-12-22
do you have any recommendations for where to download the drivers from?  I am have an Intel 915GM card.  I am really new to ubuntu and linux in general and nothing I type into the terminal seems to be working.

---

### Post by SlidingHorn on 2008-12-22
> **mossrunner02 said:**
> do you have any recommendations for where to download the drivers from?  I am have an Intel 915GM card.  I am really new to ubuntu and linux in general and nothing I type into the terminal seems to be working.

Guide:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

Packages:
[http://packages.ubuntu.com/feisty/x11/xserver-xorg-video-intel](http://packages.ubuntu.com/feisty/x11/xserver-xorg-video-intel)

You'll need to have the universe & multiverse repos enabled if I remember correctly.

---

### Post by mossrunner02 on 2008-12-22
ok, through my synaptic manager I downloaded and installed the package named 'xserver-xorg-video-intel' which provides the driver for the intel i8xx and i9xx family of chipsets, including i810, i815, i830, i845, i855, i865,i915, i945, an di965 series chips.  This package includes mine (the i915) so i figured i was on the the right track.

I went into the terminal window and typed in 'sudo apt-get install 915resolution' and what i got was as follows:

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package 915resolution is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source.
E: Package 915resolution has no installation candidate

I am not sure what to do now...

---

### Post by SlidingHorn on 2008-12-22
I have one more source: [http://ubuntuforums.org/showthread.php?t=207794](http://ubuntuforums.org/showthread.php?t=207794)

Hope this helps!

---

### Post by mossrunner02 on 2008-12-22
I followed the directions and I am currently inthe gedit screen but it is a blank screen...am I supposed to type in:

Section "Device"
Identifier "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
Driver "i810"
Option "XAANoOffscreenPixmaps"
BusID "PCI:0:2:0"
EndSection 

and then save it?

---

### Post by SlidingHorn on 2008-12-22
> **mossrunner02 said:**
> I followed the directions and I am currently inthe gedit screen but it is a blank screen...am I supposed to type in:

Section "Device"
Identifier "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
Driver "i810"
Option "XAANoOffscreenPixmaps"
BusID "PCI:0:2:0"
EndSection 

and then save it?

Yes.  Save, close and then reboot.  Should be smooth sailing from there :)

---

### Post by mossrunner02 on 2008-12-22
ok, so i installed the driver using synaptic, entered into the terminal and typed in gksudo gedit /etc/X11/xorg.conf.  The gedit window popped up but there was no text in the window. am i supposed to manually type in the Section changes?  I did just to see what would happen but when I went to save it i get an error message saying "could not find the file /etc/x11/xorg.conf, please check that you typed the location correctly and try again."

do you know what it would do this?

---

### Post by SlidingHorn on 2008-12-22
> **mossrunner02 said:**
> ok, so i installed the driver using synaptic, entered into the terminal and typed in gksudo gedit /etc/X11/xorg.conf.  The gedit window popped up but there was no text in the window. am i supposed to manually type in the Section changes?  I did just to see what would happen but when I went to save it i get an error message saying "could not find the file /etc/x11/xorg.conf, please check that you typed the location correctly and try again."

do you know what it would do this?

it's case-sensitive "X11" instead of "x11"

---

### Post by mossrunner02 on 2008-12-22
ah ok.  i made the change as stated in the link that you sent me.  i restarted and what i get now is a message saying 'ubuntu is running in low-graphics mode.  the following error was encountered.  You may need to update your configuration to solve this.  (EE) No devices detected."  When I hit OK it gives me 3 options: 1) Run Ubuntu in low-graphics mode 2)Reconfigure graphics 3)Troubleshoot the error

any ideas?

---

### Post by SlidingHorn on 2008-12-22
> **mossrunner02 said:**
> any ideas?

hmm...fresh out at this point.  I'll keep running it over in my head...I'm sure someone smarter than myself will be by sometime shortly...it's 4am  lol

---

### Post by mossrunner02 on 2008-12-22
true..thanks for your help though!

---

### Post by densou on 2008-12-22
try with my xorg.conf --> [http://spazioinwind.libero.it/densou/xorg.conf.new](http://spazioinwind.libero.it/densou/xorg.conf.new) 

check /etc/modules (with gedit), look for:
```
agpgart
intel-agp
drm
```
if you haven't these lines, just add them!


afterwards, you could also update Intel video drivers (stable backports) on [https://launchpad.net/~intel-gfx-testing/+archive](https://launchpad.net/~intel-gfx-testing/+archive) (I don't recommend to use these from Jaunty repositories ;) )

---

### Post by mossrunner02 on 2008-12-22
> **densou said:**
> try with my xorg.conf --> [http://spazioinwind.libero.it/densou/xorg.conf.new](http://spazioinwind.libero.it/densou/xorg.conf.new) 

check /etc/modules (with gedit), look for:
```
agpgart
intel-agp
drm
```
if you haven't these lines, just add them!


afterwards, you could also update Intel video drivers (stable backports) on [https://launchpad.net/~intel-gfx-testing/+archive](https://launchpad.net/~intel-gfx-testing/+archive) (I don't recommend to use these from Jaunty repositories ;) )
when i tried to access the first link you posted, the website says 'Method Not Allowed: The requested method POST is not allowed for the URL /densou/xorg.conf.new.'

---

### Post by densou on 2008-12-22
[-( :-k  that's odd or it doesn't work with some browsers #-o

well, I think you would be able to read it this time:
[http://phpfi.com/391038](http://phpfi.com/391038)

:)

---

### Post by mossrunner02 on 2008-12-22
> **densou said:**
> try with my xorg.conf --> [http://spazioinwind.libero.it/densou/xorg.conf.new](http://spazioinwind.libero.it/densou/xorg.conf.new) 

check /etc/modules (with gedit), look for:
```
agpgart
intel-agp
drm
```
if you haven't these lines, just add them!


afterwards, you could also update Intel video drivers (stable backports) on [https://launchpad.net/~intel-gfx-testing/+archive](https://launchpad.net/~intel-gfx-testing/+archive) (I don't recommend to use these from Jaunty repositories ;) )
ok, i modified the link first link you sent me and copied your lines of code and pasted it in my edit window.  I modified it abit, and pasted what i currently have below:

Section "Module"
	Load 	"bitmap"
	Load 	"ddc"
	Load 	"dbe"
	Load 	"dri"
	Load 	"extmod"
	Load 	"freetype"
	Load 	"glx"
	Load	"GLcore"
	Load 	"int10"
	Load 	"type1"
	Load	"v4l"
	Load 	"vbe"
EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"it"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#EndSection

Section "Device"
        Identifier 	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Boardname	"Intel 945"
	Busid		"PCI:0:2:0"
        Driver     	"i810"
	Option          "AccelMethod"   "EXA"
	Option 		"AddARGBGLXVisuals" "On"
	Option 		"XAANoOffscreenPixmaps"		"true"
	Vendorname	"Intel"
EndSection

I restarted my system after saving this but received a message that Ubuntu is running in low graphics mode and it gave me the option of loading in low graphics mode, reconfiguring graphics or troubleshooting the error.  

I added the 3 lines to the module edit screen but when I went to save the module, it said i dont have the permissions necessary to save that.  so those remain unchanged.  

lastly i went to the last link you sent but could not fiugre out how to download/update the intel video drivers.

---

### Post by densou on 2008-12-22
> **mossrunner02 said:**
> ```
Section "Device"
        Identifier 	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Boardname	"Intel 945"
	Busid		"PCI:0:2:0"
        Driver     	"i810"
	Option          "AccelMethod"   "EXA"
	Option 		"AddARGBGLXVisuals" "On"
	Option 		"XAANoOffscreenPixmaps"		"true"
	Vendorname	"Intel"
EndSection
```

#-o Replace all quoted stuff with:
```
Section "Device"
        Identifier 	"intel"
        Driver     	"intel"
EndSection
```
(you could leave the three 'Option' lines or discard them, it doesn't matter)


> I added the 3 lines to the module edit screen but when I went to save the module, it said i dont have the permissions necessary to save that.  so those remain unchanged.  

:confused: did you try using this command ' sudo gedit /etc/modules ' on a prompt window ?

> lastly i went to the last link you sent but could not fiugre out how to download/update the intel video drivers.

Just as in Windows. Those are .deb packages, so you could install with a simply double-click (and typing root password when asked); note: they need to be installed in a fixed order, so don't be afraid if a "can't install this package / dependencies not satisfaid / similar phrases" notify appears, 
try to install another thing.

Right order: (I assume you're using the 32 bit version of Ubuntu, if not change 'i386' to 'amd64' in the below URLs)
[https://launchpad.net/~intel-gfx-testing/+archive/+files/libdrm2_2.4.1-0ubuntu7~intrepid_i386.deb](https://launchpad.net/~intel-gfx-testing/+archive/+files/libdrm2_2.4.1-0ubuntu7~intrepid_i386.deb)
[https://launchpad.net/~intel-gfx-testing/+archive/+files/libdrm-intel1_2.4.1-0ubuntu7~intrepid_i386.deb](https://launchpad.net/~intel-gfx-testing/+archive/+files/libdrm-intel1_2.4.1-0ubuntu7~intrepid_i386.deb)
[https://launchpad.net/~intel-gfx-testing/+archive/+files/libdrm-dev_2.4.1-0ubuntu7~intrepid_i386.deb](https://launchpad.net/~intel-gfx-testing/+archive/+files/libdrm-dev_2.4.1-0ubuntu7~intrepid_i386.deb)
[https://launchpad.net/~intel-gfx-testing/+archive/+files/xserver-xorg-video-intel_2.5.1-1ubuntu5~intrepid_i386.deb](https://launchpad.net/~intel-gfx-testing/+archive/+files/xserver-xorg-video-intel_2.5.1-1ubuntu5~intrepid_i386.deb)
[https://launchpad.net/~intel-gfx-testing/+archive/+files/xserver-xorg-video-intel-dbg_2.5.1-1ubuntu5~intrepid_i386.deb](https://launchpad.net/~intel-gfx-testing/+archive/+files/xserver-xorg-video-intel-dbg_2.5.1-1ubuntu5~intrepid_i386.deb)


:popcorn:

---

### Post by mossrunner02 on 2008-12-22
ok i did everything you suggested and everything seemed to work fine.  I restarted my machine but it loaded into a greyish screen of varying gradients before turing into a dark grey screen.  I could still hear the ubuntu log in sound though.

---

### Post by niceguy123 on 2009-01-10
Any news on this. I I have a Sony Vaio with 16.4inch  1600X900 screen and too would like to configure it in Ubuntu 8.10

---

### Post by densou on 2009-01-12
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)
[http://www.phoronix.com/scan.php?page=article&item=927](http://www.phoronix.com/scan.php?page=article&item=927)

Read carefully ):P

A similar xorg.conf (**NOT TRY IT!**), it lacks of needed values for fixing 1600x900 {I used '*' as a jolly char :p ) 
```
Section "Device"
        Identifier 	"Intel Graphics Adapter"
        Driver     	"intel"
	Option		"AccelMethod"	"EXA"
	Vendorname	"Intel"
EndSection

Section "Monitor"
	Identifier   	"LVDS"
	Option "DDC" 	"False"
# 1600x900 @ 60.00 Hz (GTF) hsync: **.** kHz; pclk: **.** MHz
  Modeline "1600x900_60.00"  **.**  **** **** **** ****  *** *** *** ***
-HSync +Vsync
	Option 	"PreferredMode" "1600x900_60.00"
EndSection

Section "Screen"
        Identifier 	"Default Screen"
	Monitor		"LVDS"
	Device 		"Intel Graphics Adapter"
EndSection
```

---

### Post by KC5SDY on 2009-02-20
While we are on the subject, what about a Dell Inspiron 5000e?  I have been following along with what I could but replacing all the Intel stuff with the ATI garbage that this laptop uses but still cannot seem to get anywhere.

---

### Post by manilaph on 2009-02-25
it seems that 8.10 has a lot of "screen resolution" issues as seen when doing a search in this forum.

is this 
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) 
the best solution?

or is this 

[http://ubuntuforums.org/showthread.php?t=980983&highlight=displayconfig-gtk](http://ubuntuforums.org/showthread.php?t=980983&highlight=displayconfig-gtk) 

a better solution?

or what is the best and easiest (for newbies) solution?

---

### Post by KC5SDY on 2009-02-27
> **manilaph said:**
> it seems that 8.10 has a lot of "screen resolution" issues as seen when doing a search in this forum.

is this 
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) 
the best solution?

or is this 

[http://ubuntuforums.org/showthread.php?t=980983&highlight=displayconfig-gtk](http://ubuntuforums.org/showthread.php?t=980983&highlight=displayconfig-gtk) 

a better solution?

or what is the best and easiest (for newbies) solution?

I did try both links but found limited help.  What I did find was this...
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide")

This was at least some help right up to the point when it is talking about Finishing the install.  I changed xorg.conf like it said and then went to run the next command but got an error message saying there were no detected devices.  For grins and giggles, I tried this in both Kubuntu and Ubuntu and got the exact same error.

---

### Post by RgnKjnVA on 2009-04-20
Subscribing. I have the same issue with my Dell Latitude D610 with 915GM/GMS/910GML. I'm stuck with 1024x768 though the specs say it should be able to run at up to 1400 x 1050 (SXGA+). I want 1280x1024

---

### Post by RealG187 on 2009-04-21
> **SlidingHorn said:**
> try running

```
sudo dpkg-reconfigure xserver-xorg
```

I don't think that command works anymore in newer versions of Ubuntu.

PS What GFX card is it?

---

