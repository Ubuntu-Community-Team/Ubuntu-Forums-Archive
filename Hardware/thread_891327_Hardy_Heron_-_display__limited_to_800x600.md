---
title: "Hardy Heron - display  limited to 800x600"
date: 2008-08-15
forum: Hardware
---

### Post by genoteich on 2008-08-15
I searched for someone with a similar problem and didn't find anything close - if there is a thread already dealing with this, please point me to it.  [-o<

I installed Hardy Heron on an old Sony PCG-R505TE laptop a few days ago and I've been fighting with the display ever since. Display hardware is Intel 8215 integrated chipset.

No matter what I do, I cannot get Ubuntu to recognize that the display is capable of 1024x768. The highest I can get is 800x600 which creates a desktop screen that is more than an inch too small around the whole perimeter of the display and is very hard to use and read.

I have tried everything I've read in the Ubuntu Documents and in the forums including changing the display driver and changing the xorg.conf file both manually and through the update interface. When I access the list of possible display settings in the GUI, it always says that only 800x600 and 640x480 are available.

Please help - I would be happy to post the results of some troubleshooting steps.

---

### Post by cdtech on 2008-08-15
First, have you tried:
```
$ sudo dpkg-reconfigure -phigh xserver-xorg
$ sudo /etc/init.d/gdm restart
```

---

### Post by genoteich on 2008-08-16
> $ sudo dpkg-reconfigure -phigh xserver-xorg
$ sudo /etc/init.d/gdm restart

Thanks for the suggestion but this didn't work either.  The dpkg command seemed to work, but on the restart the GUI didn't come up (blank screen) and I had to shut it down by holding the power button down.  

Then when I turned it on again, only 800x600 and 640x480 are available as choice for screen resolution.  Information on the graphics card shows as Intel 815 even though I have the 8215 chipset (same thing?) and it detects my display as a generic "Plug n Play" with limited resolution as noted above.

---

### Post by greymoose58 on 2008-08-30
genoteich,
Did you ever resolve this problem?
I have exactly the same symptoms on an older machine. I had to install a S3 video card when the onboard video died. I have the latest driver and, like you, have searched for an answer and tried various fixes to no avail.
Cheers.

---

### Post by pablopanama27 on 2008-08-30
I have the same problem. I can't seem to find  a way to get it to 1024 x 1280, im stuck with lousy 800*600. Funny thing is that before, i had xp on a different partition with the drivers and ubuntu worked well, now i reinstalled and wiped xp, to find myself with this problem.

---

### Post by cdtech on 2008-08-30
Do you have your restricted modules installed:
```
sudo apt-get install linux-restricted-modules-$(uname -r)
```

Just a thought........

---

### Post by pablopanama27 on 2008-08-30
This worked for me.
The options suggested above did not work for me. I tried this and worked. Just exploring a few options i used the demo cd which recognized immediately my optimal resolution and this time I installed it from there instead of direcly from the blackscreen. When you get into the demo ubuntu theres an option to install directly from that screen, i used it and worked.
Don-t know exactly why but worked for me just before writting this post. Thanks. Pablo

---

### Post by kagashe on 2008-08-30
> **genoteich said:**
> Thanks for the suggestion but this didn't work either.  The dpkg command seemed to work, but on the restart the GUI didn't come up (blank screen) and I had to shut it down by holding the power button down.  

Then when I turned it on again, only 800x600 and 640x480 are available as choice for screen resolution.  Information on the graphics card shows as Intel 815 even though I have the 8215 chipset (same thing?) and it detects my display as a generic "Plug n Play" with limited resolution as noted above.Now try this solution.

Open xorg.conf to edit:
> $ gksudo gedit /etc/X11/xorg.conf

Scroll down to Device section and add this entry:
> Driver "intel"

The section should now read:
> Section "Device"
Identifier "Configured Video Device"
Driver "intel"
EndSection


Reboot or restart xserver with:
> $ sudo /etc/init.d/gdm restart

If you still don't get higher resolution post the output of:
> $ xrandr -q

and attach this file with your post:
> /var/log/Xorg.0.log

kagashe

---

### Post by acrousey on 2008-08-30
It could be something with the video card.

Also, have you tried playing around with your xorg file? I know a lot of people wouldn't recommend it, but sometimes one just has to manually tell the computer what resolutions it has instead of just letting it detect for them.

The way into your xorg file is ```
sudo nano /etc/X11/xorg.conf
```

*note that X is capitalized in X11. If you do x11, you will not get into it.

However, I would suggest on looking up more on manually configuring your xorg.conf . If you change something you shouldn't have, it isn't that hard to change it back, but it can really start to be a hassle.

Best of luck!

---

### Post by greymoose58 on 2008-08-31
Thanks for the many suggestions:

> **cdtech said:**
> Do you have your restricted modules installed:
Yes, they are all up to date

I've played with xorg.conf while trying to fix this problem. The "Configured Video Device"section is identical to what kagashe suggested except the driver is vesa rather than intel.
```
xrandr -q
``` resulted in

```
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  
```

I have had my screen running at much higher resolutions through the on board video. 

I tried to upload /var/log/xorg.0.log but was told it was an invalid file type. If you tell me what part of it you are interested in I can post it here if that would help.

---

### Post by kagashe on 2008-08-31
> **greymoose58 said:**
> The "Configured Video Device"section is identical to what kagashe suggested except the driver is vesa rather than intel.Why don't you change "vesa" to "intel"? "intel" is the driver for your graphic card.

> xrandr -q resulted in

Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0
This will change when you change the driver in xorg.conf from vesa to intel. intel driver will get you higher resolutions. If you don't get it automatically post the output of "xrandr -q" here once again.

> 
I tried to upload /var/log/xorg.0.log but was told it was an invalid file type. If you tell me what part of it you are interested in I can post it here if that would help.It is not required now.

kagashe

---

### Post by genoteich on 2008-08-31
> Do you have your restricted modules installed:

sudo apt-get install linux-restricted-modules-$(uname -r)Thanks cdtech but, yes, restricted modules are up to date when I run this command.

From kagashe ......

> [SIZE=1]Now try this solution.

Open xorg.conf to edit:[/SIZE]              [SIZE=1]                              $ gksudo gedit /etc/X11/xorg.conf                      [/SIZE]           
[SIZE=1]Scroll down to Device section and add this entry:[/SIZE]              [SIZE=1]                              Driver "intel"                      [/SIZE]           
[SIZE=1]The section should now read:[/SIZE]              [SIZE=1]                              Section "Device"
Identifier "Configured Video Device"
Driver "intel"
EndSection                  [/SIZE]           
[SIZE=1]Reboot or restart xserver with:
[/SIZE]                         [SIZE=1]                              $ sudo /etc/init.d/gdm restart[/SIZE]This caused a major hang after the item:

Running local boot scripts (/etc/rc.local)  [ ok ]

and I I had to press the power button to get past it which just shut everything down.  Then after rebooting the resolution is the same.

I know this display can use 1024 x 768 because it was that way when it ran Windows and Ubuntu is not using the whole display space right now.

Results of the command "xrandr -q"

> Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0 File Xorg.0.log is attached

Thanks for the suggestions so far, but no luck yet.  Any further help is appreciated.

---

### Post by kagashe on 2008-08-31
> **genoteich said:**
> 

File Xorg.0.log is attached

Where is it? You can change filename Xorg.0.log.txt if the server is not accepting.

kagashe

---

### Post by genoteich on 2008-08-31
> Where is it? You can change filename Xorg.0.log.txt if the server is not accepting.

kagasheSorry, it appears that there is a very low limit set for txt files so I had to name it with a .doc extension.  It is attached now.  

Occasionally the GUI pops up a message and says that Ubuntu is running in low res mode and that I can configure it if I want to.  I tried just about every combination of display adapter, resolution and frequency that exists and none of them worked and then I had to reboot because the colors were so messed up I couldn't use it.  I got some errors during the reboot so I think I'm also having boot issues now.  I've turned boot logging on in /etc/default/bootlogd and I'll see what comes up the next time I restart.

---

### Post by kagashe on 2008-09-01
@ genoteich
Xorg.0.log attached by you indicates the following at line no 23
> (==) Using config file: "/etc/X11/xorg.conf.failsafe"

Normally xorg uses /etc/X11/xorg.conf but falls back to /etc/X11/xorg.conf.failsafe if xorg.conf does not work (which indicates that intel driver is not working).

Since the launch of Hardy Heron many xorg drivers have been updated to remove bugs. If you have not updated your system you can try:
> $ sudo apt-get update
$ sudo apt-get install xserver-xorg-video-intel

and see whether your intel driver is updated or not and try the updated driver by rebooting.

The driver for your graphic card in earlier Ubuntu versions was i810. Subsequently intel driver was introduced which is suppossed to give better performance but may not be working for you. Fortunately Hardy Heron has the old driver (i810) also.

If you conclude that intel is not working you can edit xorg.conf once again and change the Driver to "i810" and see whether it works.

You can check a few lines in the begining of Xorg.0.log to see whether xorg finally using xorg.conf or not.

kagashe

---

### Post by genoteich on 2008-09-01
[SIZE=2]
> Since the launch of Hardy Heron many xorg drivers have been updated to remove bugs. If you have not updated your system you can try:
$ sudo apt-get update
$ sudo apt-get install xserver-xorg-video-intel
[/SIZE][SIZE=2]After running these commands, the prompt says 
"xserver-xorg-video-intel is already the newest version"
"0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded"

When rebooting, Ubuntu hangs for a long time during the title screen with the animated horizontal loading bar and then before the login screen, I get a popup that says Ubuntu is running in low-graphics mode because my screen and graphics card could not be detected correctly.

I checked Xorg.0.log and it still said:
> (==)  Using config file:  "/etc/X11/xorg.conf.failsafe"Then I edited Xorg.conf as you instructed to use "i810" instead of "intel" and rebooted.

Still no difference in resolution but I couldn't find any display errors in Xorg.0.log this time.  A new copy is attached.
[/SIZE] [SIZE=2]
[/SIZE]

---

### Post by cdtech on 2008-09-01
Have you tried "sudo mv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf.failsafe.back and then "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.failsafe". See if this will let you boot to the proper resolution.

Just a thought......

---

### Post by greymoose58 on 2008-09-01
Thanks for your help.

I changed vesa to intel and made sure that the intel drivers are up to date. No change.
I also noticed that the available resolutions in xorg.conf had been reduced to only "800x600"so I added "1024x768". This didn't seem to make any difference either.

xrandr -q gives the same output: 
```
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  
```

When I boot the machine I get a warning saying that the screen and graphics card could not be detected properly. Might this mean that the video card is faulty? I used an old card from a canabalised computer (as you do). Do you think it would be worth swapping it out for another?

Thanks again.

---

### Post by cdtech on 2008-09-01
I've noticed "envy" has not be mentioned here. Have you given "envy" a shot?
```
sudo apt-get install envyng-gtk
```

---

### Post by Zimmer on 2008-09-01
Your screen is not being auto detected.

(II) VESA(0): VESA VBE DDC read failed

from your log.
I have a similar problem with an ATI9600 running an ACER AL1511. Not detected when attached to a VGA extension cable . A tweaked xorg.conf with Monitor settings solves the problem.. and may be your salvation,too.

However, my problem gets worse if I plug the monitor in without the extension lead  and it gets detected... cannot get the correct resolutions so far after 2 weeks of tweaking... the  same xorg.conf settings just do not override I end up in low res hell.

---

### Post by greymoose58 on 2008-09-01
> **cdtech said:**
> I've noticed "envy" has not be mentioned here. Have you given "envy" a shot?
```
sudo apt-get install envyng-gtk
```

I just tried it now. I'm all up to date. Thanks for the thought.

---

### Post by greymoose58 on 2008-09-01
> **Zimmer said:**
> Your screen is not being auto detected.

My log is showing
```
(II) VESA(0): VBESetVBEMode failed...Tried again without customized values.
```

It goes on to set the defaults as far as I can see.

Does that help diagnose the problem?

Cheers.

---

### Post by Scunge on 2008-09-01
I would like to add my voice to this thread since I am seeing pretty much the same with an S3 video card in my "experimental" Hardy instllation: 800x600 max, doesn't work properly even with "s3" as the driver, "vesa" works but it's slooooowww (you can see it redrawing each part of every window), and the configuration window doesn't seem to help find any settings of any use.

I have tried the following, from this thread:
- "sudo dpkg-reconfigure -phigh xserver-xorg" does nothing
- "sudo apt-get install linux-restricted-modules-$(uname -r)" is up-to-date
- "sudo apt-get install xserver-xorg-video-intel" is up-to-date
- driver "intel" in the xorg file messed it up completely, and had to sort it via SSH from another machine
- "xrandr -q" gives the exact same output as above
- using "i810" as the driver means that xorg.conf.failsafe was used, which didn't contain "i810", so it clearly doesn't like it
- "sudo apt-get install envyng-gtk": I get the options for ATI and NVIDIA; I figured out from some other thread that it's not NVIDIA, and in the ATI section, only one driver is shown for manual installation, "8-3", but when I run that or the automatic installation, I get "Exception: EnvyNG ERROR: ATI card not found"

Some additional information...

I've recently discvovered the command *lshw*, so here's the output from it for the S3 card:
```
        *-display
             description: VGA compatible controller
             product: 86c764/765 [Trio32/64/64V+]
             vendor: S3 Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller
             configuration: driver=s3fb latency=0 module=s3fb


```

And here's some output taken from /var/log/Xorg.0.log:
```
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
[...]
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 00:12:0
(WW) VESA: No matching Device section for instance (BusID PCI:1:0:0) found
(--) Chipset vesa found
[...]
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 1.2
(II) VESA(0): VESA VBE Total Mem: 1024 kB
(II) VESA(0): VESA VBE OEM: S3 Incorporated. Trio32
(II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 16/16
(**) VESA(0): Depth 16, (--) framebuffer bpp 16
(==) VESA(0): RGB weight 565
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) VESA(0): Searching for matching VESA mode(s):
[...]
(II) VESA(0): Total Memory: 16 64KB banks (1024kB)
(II) VESA(0): Generic Monitor: Using hsync range of 28.00-40.00 kHz
(II) VESA(0): Generic Monitor: Using vrefresh range of 43.00-60.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(--) VESA(0): Virtual size is 800x600 (pitch 800)
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(==) VESA(0): DPI set to (96, 96)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (114)
(II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (111)
(**) VESA(0): Using "Shadow Framebuffer"
[...]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 1.2
(II) VESA(0): VESA VBE Total Mem: 1024 kB
(II) VESA(0): VESA VBE OEM: S3 Incorporated. Trio32
(II) VESA(0): virtual address = 0xb71e6000,
	physical address = 0xa0000, size = 65536
(II) VESA(0): VBESetVBEMode failed...Tried again without customized values.
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(**) Option "dpms"
(**) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
[...]

```

Thanks for any help with this.

---

### Post by genoteich on 2008-09-01
> I've noticed "envy" has not be mentioned here. Have you given "envy" a shot?  Tried this with no result - documentation says that Envy is only for AMD and Nvidia so this wouldn't work with the Intel graphics chipset.  Might be a good suggestion for people with this specific hardware though.

---

### Post by GlennW on 2008-09-02
Hi kagashe,

I've been following this thread with interest since I'm stuck in the same boat. I can't get my resolution above 800x600. I'll attempt to give you enough info so that you can make a proper diagnosis.

I run hardy and have been since the first upgrade from gutsy was available. I have a Samsung SyncMaster 205bw (20" inch screen 1680x1050) which I've had since Feisty. I love the widescreen and the res is fabulous. Even after the upgrade to hardy, I had full res and compiz running with smooth rendering and happiness! Now, after some little tweak, upgrade, whatever, I've lost it (at times really lost it!) and am stuck at 800x600. I've been searching through the threads for any shred of help and found nothing that has changed my situation. I have a Nvidia GeForce 6200 256Mb card with a P4 1.6 chip. 

I'm still quite the n00b and know just enough to be dangerous! I apologize for the lack of pertinent info but I'll get it for you once I know what you need.

Thanks a bunch!!

---

### Post by Horacioklm on 2008-09-02
> **cdtech said:**
> First, have you tried:
```
$ sudo dpkg-reconfigure -phigh xserver-xorg
$ sudo /etc/init.d/gdm restart
```

I got same problems. I started use ubuntu as the unique OP in my computer (compaq presario v3000 AMD sempron and nvidia card) and it was ok until an actualization in nvidia drivers was avaiable. After rebooting, the resolution was reseted to 800 x 600. I tryed everything (in my yet poor knowledge:confused:) to return to the anterior resolution (about 1270 x 700) but no good results.... until i found this command you post.

Can you explain me what does it do??, i am starting learn ubuntu... i really dont want to go back to windows:mad:

Thanks a lot!!!

---

### Post by cdtech on 2008-09-02
Software contained in Debian packages which make use of debconf can usually be configured by running:
```
dpkg-reconfigure "package_name"
```
The -phigh flag is explained within the man page:
> -pvalue, --priority=value
           Specify the minimum priority of questions that will be displayed.
           dpkg-reconfigure normally shows low priority questions.

Hope this helps.......

---

### Post by GlennW on 2008-09-04
Bump!

---

### Post by Zimmer on 2008-09-04
> **GlennW said:**
> Bump!

 What does your xorg log tell you?

[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/index.html)

I have the same Nv card and have had to construct my own config for the same reason as you. Stuck in low res.

[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/chapter-06.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/chapter-06.html)

---

### Post by rcastevet on 2008-09-06
This worked for me.  nvidia riva tnt/tnt2 on a Norwood f199 flatscreen monitor and Compaq Deskpro en 866.

# xorg.conf (X.Org X Window System server configuration file)
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

Section "Device"
	Identifier	"Configured Video Device"
	
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	
	Horizsync	30.0-55.0
	Vertrefresh	50.0-120.0
	
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	
	SubSection "Display"
		Depth	24
		Modes		"1024x768"
	EndSubSection
	
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by genoteich on 2008-09-07
Hooray!!  I seem to have stumbled onto a solution for my laptop.  :lolflag:
I don't really know what I did but I'll describe the steps and events that happened in the slim chance that this might help someone else that is locked into a low resolution with Hardy Heron.

First of all, I tried to put the install CD back in the drive and boot from it to do a repair or something.  When I didn't find any help there, I checked the contents of /var/log/Xorg.0.log again and found that Xorg.conf.failsafe was still being used.  So I followed the advice of cdtech earlier in this forum:

> Have you tried "sudo mv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf.failsafe.back and then "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.failsafe". See if this will let you boot to the proper resolution.
... and the most recent post by rcastevet.  I copied and pasted the following sections into Xorg.conf between the mouse section and server section.

```
Section "Device"
    Identifier    "Configured Video Device"
    
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    
    Horizsync    30.0-55.0
    Vertrefresh    50.0-120.0
    
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    
    SubSection "Display"
        Depth    24
        Modes        "1024x768"
    EndSubSection
    
    Defaultdepth    24
EndSection
```Then, as cdtech suggested, I saved the Xorg.conf file and also copied it over the Xorg.conf.failsafe file.

When I rebooted, the display went to 1024x768 but it was washed out and not readable or useable.  So I was forced to reboot again (install cd still in the drive) and this time while rebooting, Ubuntu said that the file system check "fsck" failed and needed to be run from maintenance mode.  I entered the root password to start maintenance mode and then entered "fsck" at the command prompt.  The file system check found all kinds of errors and I just kept pressing "Y" to fix them.  Then it reached the end and said Ubuntu needed to reboot again so I pressed  "CTL-D" to do this.

On boot up the Ubuntu loading splash screen showed up at 1024x768 so my hopes were up.  When I entered a username and password however, the GUI came up as 800x600 just like it always used to and I thought I was foiled again.  However, this time when I went into System / Preferences / Screen Resolution, all the resolutions were there to choose from and I only had to select 1024x768.  Now my display is normal and as good as it ever was with Windows.

I don't know exactly what it was that actually fixed the issue, but maybe someone who knows more than I do can work this into an actual solution for others that have the low resolution problem.

Cheers and thanks to all that made suggestions to help.  Support forums and open license software are truly the most powerful parts of the internet.  :)

---

### Post by johntc23 on 2008-09-08
mine is stuck on 640x480 works ok on hardy heron desktop but once your online with firefox your having to scroll around screen rather than page fitting on screen. I've tried new drivers,another graphics card couldn't get anything to work differently. There are numerous different suggestions here. Thanks

---

### Post by cdtech on 2008-09-08
> **johntc23 said:**
> mine is stuck on 640x480 works ok on hardy heron desktop but once your online with firefox your having to scroll around screen rather than page fitting on screen. I've tried new drivers,another graphics card couldn't get anything to work differently. There are numerous different suggestions here. Thanks

First you should find out what card you are using with the command:
```
lspci
```
[COLOR="Blue"]00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)[/COLOR]
This is the output from my results.

Be sure you have the "System > Administrator > Software sources" under Ubuntu software select "proprietary drivers for devices" and "software restricted" is selected. Do a "sudo apt-get update". Then look in the "System > Administrator > Hardware Drivers" and see if your new drivers are there. If they are just select and restart system.

I downloaded the program "envyng-gtk" to help with the install of my drivers for the nVidia card. This program can be used for the "nVidia and the ATI".

---

### Post by GlennW on 2008-09-11
> **Zimmer said:**
> What does your xorg log tell you?

[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/index.html)

I have the same Nv card and have had to construct my own config for the same reason as you. Stuck in low res.

[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/chapter-06.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/chapter-06.html)

Hi Zimmer, sorry for not getting back to you earlier. Life sometimes has a nasty way of intruding on one's plans and routine. Deepest apologies!!

Here's the Xorg.log you asked for: 

[PHP]
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux glenn-desktop 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 11 13:11:41 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first mouse device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1039,0645 card 0000,0000 rev 01 class 06,00,00 hdr 80
(II) PCI: 00:01:0: chip 1039,0001 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0961 card 0000,0000 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:02:1: chip 1039,0016 card 0000,0000 rev 00 class 0c,05,00 hdr 00
(II) PCI: 00:02:2: chip 1039,7001 card 1039,7001 rev 07 class 0c,03,10 hdr 00
(II) PCI: 00:02:3: chip 1039,7001 card 1039,7001 rev 07 class 0c,03,10 hdr 00
(II) PCI: 00:02:5: chip 1039,5513 card 1039,5513 rev d0 class 01,01,80 hdr 80
(II) PCI: 00:02:7: chip 1039,7012 card 13f6,0300 rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,0900 card 1039,0900 rev 90 class 02,00,00 hdr 00
(II) PCI: 00:08:0: chip 10d9,0531 card 0000,0000 rev 25 class 02,00,00 hdr 00
(II) PCI: 00:09:0: chip 1057,5600 card 1057,0300 rev 00 class 07,80,00 hdr 00
(II) PCI: 00:0a:0: chip 1274,5880 card 1274,8001 rev 02 class 04,01,00 hdr 00
(II) PCI: 00:0b:0: chip 1033,0035 card 2098,2100 rev 41 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 1033,0035 card 2098,2100 rev 41 class 0c,03,10 hdr 00
(II) PCI: 00:0b:2: chip 1033,00e0 card 2098,2000 rev 01 class 0c,03,20 hdr 00
(II) PCI: 01:00:0: chip 10de,0221 card 1682,2152 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdbe00000 - 0xdfefffff (0x4100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xbbc00000 - 0xdbcfffff (0x20100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV44A [GeForce 6200] rev 161, Mem @ 0xde000000/24, 0xc0000000/28, 0xdd000000/24, BIOS @ 0xdfee0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xdfffce00 - 0xdfffceff (0x100) MX[B]
	[1] -1	0	0xdfffb000 - 0xdfffbfff (0x1000) MX[B]
	[2] -1	0	0xdfffa000 - 0xdfffafff (0x1000) MX[B]
	[3] -1	0	0xdbdfff00 - 0xdbdfffff (0x100) MX[B]
	[4] -1	0	0xdfffcf00 - 0xdfffcfff (0x100) MX[B]
	[5] -1	0	0xdfffd000 - 0xdfffdfff (0x1000) MX[B]
	[6] -1	0	0xdffff000 - 0xdfffffff (0x1000) MX[B]
	[7] -1	0	0xdfffe000 - 0xdfffefff (0x1000) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[10] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000cc00 - 0x0000cc3f (0x40) IX[B]
	[14] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[18] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[19] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdfffce00 - 0xdfffceff (0x100) MX[B]
	[1] -1	0	0xdfffb000 - 0xdfffbfff (0x1000) MX[B]
	[2] -1	0	0xdfffa000 - 0xdfffafff (0x1000) MX[B]
	[3] -1	0	0xdbdfff00 - 0xdbdfffff (0x100) MX[B]
	[4] -1	0	0xdfffcf00 - 0xdfffcfff (0x100) MX[B]
	[5] -1	0	0xdfffd000 - 0xdfffdfff (0x1000) MX[B]
	[6] -1	0	0xdffff000 - 0xdfffffff (0x1000) MX[B]
	[7] -1	0	0xdfffe000 - 0xdfffefff (0x1000) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[10] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000cc00 - 0x0000cc3f (0x40) IX[B]
	[14] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[18] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[19] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
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
	[4] -1	0	0xdfffce00 - 0xdfffceff (0x100) MX[B]
	[5] -1	0	0xdfffb000 - 0xdfffbfff (0x1000) MX[B]
	[6] -1	0	0xdfffa000 - 0xdfffafff (0x1000) MX[B]
	[7] -1	0	0xdbdfff00 - 0xdbdfffff (0x100) MX[B]
	[8] -1	0	0xdfffcf00 - 0xdfffcfff (0x100) MX[B]
	[9] -1	0	0xdfffd000 - 0xdfffdfff (0x1000) MX[B]
	[10] -1	0	0xdffff000 - 0xdfffffff (0x1000) MX[B]
	[11] -1	0	0xdfffe000 - 0xdfffefff (0x1000) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[14] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000cc00 - 0x0000cc3f (0x40) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[24] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[25] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.12  Thu Feb 14 18:45:56 PST 2008
(II) Loading extension GLX
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.1.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) v4l driver for Video4Linux
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
	GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
	GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
	GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
	GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
	Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
	Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
	GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, GeForce 8800 GTS,
	GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600, GeForce 8600 GTS,
	GeForce 8600 GT, GeForce 8600 GT, GeForce 8400 GS, GeForce 8600M GT,
	GeForce 8700M GT, Quadro FX 370, Quadro NVS 320M, Quadro FX 570M,
	Quadro FX 1600M, Quadro FX 570, Quadro FX 1700, GeForce 8500 GT,
	GeForce 8400 GS, GeForce 8300 GS, GeForce 8400 GS, GeForce 8600M GS,
	GeForce 8400M GT, GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M,
	Quadro NVS 130M, Quadro NVS 135M, Quadro FX 360M, Quadro NVS 290,
	GeForce 8800 GT, GeForce 8800 GS, GeForce 8800 GS, GeForce 8800 GT,
	Quadro FX 3700, GeForce 9600 GT, GeForce 8400 GS
(II) Primary Device is: PCI 01:00:0
(--) Chipset GeForce 6200 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfffce00 - 0xdfffceff (0x100) MX[B]
	[5] -1	0	0xdfffb000 - 0xdfffbfff (0x1000) MX[B]
	[6] -1	0	0xdfffa000 - 0xdfffafff (0x1000) MX[B]
	[7] -1	0	0xdbdfff00 - 0xdbdfffff (0x100) MX[B]
	[8] -1	0	0xdfffcf00 - 0xdfffcfff (0x100) MX[B]
	[9] -1	0	0xdfffd000 - 0xdfffdfff (0x1000) MX[B]
	[10] -1	0	0xdffff000 - 0xdfffffff (0x1000) MX[B]
	[11] -1	0	0xdfffe000 - 0xdfffefff (0x1000) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[14] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000cc00 - 0x0000cc3f (0x40) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[24] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[25] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfffce00 - 0xdfffceff (0x100) MX[B]
	[5] -1	0	0xdfffb000 - 0xdfffbfff (0x1000) MX[B]
	[6] -1	0	0xdfffa000 - 0xdfffafff (0x1000) MX[B]
	[7] -1	0	0xdbdfff00 - 0xdbdfffff (0x100) MX[B]
	[8] -1	0	0xdfffcf00 - 0xdfffcfff (0x100) MX[B]
	[9] -1	0	0xdfffd000 - 0xdfffdfff (0x1000) MX[B]
	[10] -1	0	0xdffff000 - 0xdfffffff (0x1000) MX[B]
	[11] -1	0	0xdfffe000 - 0xdfffefff (0x1000) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[14] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000cc00 - 0x0000cc3f (0x40) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[24] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[27] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[28] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce 6200"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xC0000000
(--) NV(0): MMIO registers at 0xDE000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...found one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: SAM  Model: 21e  Serial#: 1212232240
(II) NV(0): Year: 2006  Week: 33
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max H-Image Size [cm]: horiz.: 43  vert.: 27
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) NV(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@67Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): 1152x870@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 146.2 MHz   Image Size:  433 x 271 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 160 MHz
(II) NV(0): Monitor name: SyncMaster
(II) NV(0): Serial No: HVYL800816
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff004c2d1e0230324148
(II) NV(0): 	21100103802b1b782aee95a3544c9926
(II) NV(0): 	0f5054bfef80b30081808140714f0101
(II) NV(0): 	01010101010121399030621a274068b0
(II) NV(0): 	3600b10f1100001c000000fd00384b1e
(II) NV(0): 	5110000a202020202020000000fc0053
(II) NV(0): 	796e634d61737465720a2020000000ff
(II) NV(0): 	004856594c3830303831360a2020002f
(II) NV(0): Probing for EDID on I2C bus B...
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: SAM  Model: 21d  Serial#: 1212232240
(II) NV(0): Year: 2006  Week: 33
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NV(0): Sync:  Separate  Composite  SyncOnGreen
(II) NV(0): Max H-Image Size [cm]: horiz.: 43  vert.: 27
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) NV(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@67Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): 1152x870@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 146.2 MHz   Image Size:  433 x 271 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 160 MHz
(II) NV(0): Monitor name: SyncMaster
(II) NV(0): Serial No: HVYL800816
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff004c2d1d0230324148
(II) NV(0): 	211001030e2b1b782aee95a3544c9926
(II) NV(0): 	0f5054bfef80b30081808140714f0101
(II) NV(0): 	01010101010121399030621a274068b0
(II) NV(0): 	3600b10f1100001c000000fd00384b1e
(II) NV(0): 	5110000a202020202020000000fc0053
(II) NV(0): 	796e634d61737465720a2020000000ff
(II) NV(0): 	004856594c3830303831360a202000a2
(--) NV(0): CRTC 1 is currently programmed for DFP
(II) NV(0): Using DFP on CRTC 1
(--) NV(0): Panel size is 1680 x 1050
(II) NV(0): EDID vendor "SAM", prod id 542
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) NV(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NV(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) NV(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) NV(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) NV(0): Panel is TMDS
(--) NV(0): VideoRAM: 262144 kBytes
(**) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Configured Monitor: Using hsync range of 31.50-65.50 kHz
(II) NV(0): Configured Monitor: Using vrefresh range of 56.00-65.00 Hz
(II) NV(0): Configured Monitor: Using maximum pixel clock of 160.00 MHz
(II) NV(0): Clock range:  12.00 to 400.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "832x624" (vrefresh out of range)
(II) NV(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x768" (vrefresh out of range)
(II) NV(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using driver mode "640x480" (vrefresh out of range)
(II) NV(0): Not using driver mode "640x480" (vrefresh out of range)
(II) NV(0): Not using driver mode "640x480" (vrefresh out of range)
(II) NV(0): Not using driver mode "720x400" (vrefresh out of range)
(II) NV(0): Not using driver mode "1280x1024" (hsync out of range)
(II) NV(0): Not using driver mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using driver mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using driver mode "832x624" (vrefresh out of range)
(II) NV(0): Not using driver mode "800x600" (vrefresh out of range)
(II) NV(0): Not using driver mode "800x600" (vrefresh out of range)
(II) NV(0): Not using driver mode "1152x864" (hsync out of range)
(II) NV(0): Not using driver mode "1152x864" (hsync out of range)
(**) NV(0): Virtual size is 1680x1050 (pitch 1680)
(**) NV(0): *Mode "1680x1050@60": 147.1 MHz, 65.2 kHz, 60.0 Hz
(II) NV(0): Modeline "1680x1050@60"x60.0  147.14  1680 1784 1968 2256  1050 1051 1054 1087 -hsync +vsync (65.2 kHz)
(**) NV(0): *Mode "1600x1024@60": 136.4 MHz, 63.6 kHz, 60.0 Hz
(II) NV(0): Modeline "1600x1024@60"x60.0  136.36  1600 1704 1872 2144  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
(**) NV(0): *Mode "1440x900@60": 106.5 MHz, 55.9 kHz, 60.0 Hz
(II) NV(0): Modeline "1440x900@60"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(**) NV(0): *Mode "1280x800@60": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x800@60"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 -hsync +vsync (49.7 kHz)
(**) NV(0): *Mode "1280x720@60": 74.5 MHz, 44.8 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x720@60"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(**) NV(0): *Mode "1280x768@60": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x768@60"x60.0   80.14  1280 1344 1480 1680  768 769 772 795 -hsync +vsync (47.7 kHz)
(**) NV(0): *Mode "800x600@60": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600@60"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0): *Mode "800x600@56": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600@56"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NV(0):  Driver mode "1680x1050": 146.2 MHz, 65.3 kHz, 60.0 Hz
(II) NV(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(**) NV(0):  Driver mode "1680x1050": 146.2 MHz, 65.3 kHz, 60.0 Hz
(II) NV(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(**) NV(0):  Driver mode "1680x1050": 119.0 MHz, 64.7 kHz, 59.9 Hz
(II) NV(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(**) NV(0):  Default mode "1680x1050": 147.1 MHz, 65.2 kHz, 60.0 Hz
(II) NV(0): Modeline "1680x1050"x60.0  147.14  1680 1784 1968 2256  1050 1051 1054 1087 (65.2 kHz)
(**) NV(0):  Default mode "1600x1024": 106.9 MHz, 64.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1600x1024"x60.0  106.91  1600 1620 1640 1670  1024 1027 1030 1067 -hsync -vsync (64.0 kHz)
(**) NV(0):  Default mode "1400x1050": 122.0 MHz, 64.9 kHz, 60.0 Hz
(II) NV(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(**) NV(0):  Driver mode "1280x1024": 109.0 MHz, 63.7 kHz, 59.9 Hz
(II) NV(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(**) NV(0):  Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) NV(0):  Default mode "1440x900": 108.8 MHz, 56.9 kHz, 60.2 Hz
(II) NV(0): Modeline "1440x900"x60.2  108.84  1440 1472 1880 1912  900 918 927 946 +hsync +vsync (56.9 kHz)
(**) NV(0):  Driver mode "1280x960": 101.2 MHz, 59.7 kHz, 59.9 Hz
(II) NV(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(**) NV(0):  Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(**) NV(0):  Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 (49.7 kHz)
(**) NV(0):  Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x768"x60.0   80.14  1280 1344 1480 1680  768 769 772 795 (47.7 kHz)
(**) NV(0):  Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NV(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NV(0):  Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0):  Driver mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NV(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NV(0):  Driver mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0): Display dimensions: (430, 270) mm
(**) NV(0): DPI set to (99, 98)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdd000000 - 0xddffffff (0x1000000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] 0	0	0xde000000 - 0xdeffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xdfffce00 - 0xdfffceff (0x100) MX[B]
	[8] -1	0	0xdfffb000 - 0xdfffbfff (0x1000) MX[B]
	[9] -1	0	0xdfffa000 - 0xdfffafff (0x1000) MX[B]
	[10] -1	0	0xdbdfff00 - 0xdbdfffff (0x100) MX[B]
	[11] -1	0	0xdfffcf00 - 0xdfffcfff (0x100) MX[B]
	[12] -1	0	0xdfffd000 - 0xdfffdfff (0x1000) MX[B]
	[13] -1	0	0xdffff000 - 0xdfffffff (0x1000) MX[B]
	[14] -1	0	0xdfffe000 - 0xdfffefff (0x1000) MX[B]
	[15] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[16] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[17] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[18] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[19] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000cc00 - 0x0000cc3f (0x40) IX[B]
	[26] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[27] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[28] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[29] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[30] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[31] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xc0000000,0x10000000)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(II) NV(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc101"
(**) Generic Keyboard: XkbModel: "pc101"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetGrabKeysState - disabled
SetGrabKeysState - enabled[/PHP]

I'm quite the n00b when it comes to Linux and even though I've been (this time) bailed out my Mr. Gates, I am so looking forward to getting back to hardy.

Thanks for your help!

---

### Post by GlennW on 2008-09-13
Bump...

---

### Post by Zimmer on 2008-09-14
@GlennW:
Sorry, was away for a few days.
From your log you are using the 2D driver, NV. To enable 3D and fancy stuff you will need first to activate the NVIDIA driver (System>Administration>Hardware Drivers) 
and (if that process does not automatically do it, can't remember myself) use
sudo nvidia-xconfig    from the terminal to do it.
The basic command just writes "nvidia" to the driver section of you xorg.conf and makes a backup of your previous xorg.conf file.
see this for details...
[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/chapter-06.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/chapter-06.html)
Note that the X server must be restarted for any changes to its configuration file to take effect. (That means restart to us idle noobs who can't remember the keys to restart just the X server, and if they do, panic when an unfamiliar black screen and text prompt appear ;) )
After this, maybe the Nvidia driver will play nicely with the monitor.

If it doesn't at first reboot see
[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/chapter-24.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/chapter-24.html)
and use the  nvidia-settings   program to try and alter your resolutions.

Restart and see where that gets us , before we get messy with xorg.conf ...

---

### Post by Mike_cog on 2008-09-15
I have been using this computer on Ubuntu since 6.06 and recently updated to Hardy Heron and everything was just fine then a few days ago bang just went to 800x600 and cant set it to anything else. Must have been something in one of the recent updates that`s upset everything.

---

### Post by GlennW on 2008-09-15
> **Zimmer said:**
> @GlennW:
Sorry, was away for a few days.
From your log you are using the 2D driver, NV. To enable 3D and fancy stuff you will need first to activate the NVIDIA driver (System>Administration>Hardware Drivers) 
and (if that process does not automatically do it, can't remember myself) use
sudo nvidia-xconfig    from the terminal to do it.
The basic command just writes "nvidia" to the driver section of you xorg.conf and makes a backup of your previous xorg.conf file.
see this for details...
[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/chapter-06.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/chapter-06.html)
Note that the X server must be restarted for any changes to its configuration file to take effect. (That means restart to us idle noobs who can't remember the keys to restart just the X server, and if they do, panic when an unfamiliar black screen and text prompt appear ;) )
After this, maybe the Nvidia driver will play nicely with the monitor.

If it doesn't at first reboot see
[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/chapter-24.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/chapter-24.html)
and use the  nvidia-settings   program to try and alter your resolutions.

Restart and see where that gets us , before we get messy with xorg.conf ...

Hi Zimmer,
Well, I guess it's time to get messy!! I followed your suggestions several times to make sure that I didn't leave anything out. I still have the same issues. 

When I initially looked to see if the NVIDIA driver was activated, it was not. So, I activated it and restarted X. It made no difference whatsoever. I checked to make sure if it was still activated and it was but still no joy. I used nvidia-xconfig and restarted, no change. nvidia-settings just came up with a box saying that the nvidia X driver wasn't activated and that I should use nvidia-xconfig and then restart! So, I'm stuck in some crazy loop! 

I really need some help. I've been stuck in this situation now for a month with little forthcoming help. I really need to get this machine up and running since it's my primary workhorse here at home. Your help is greatly appreciated.

Let me know what you need to look at...

---

### Post by Zimmer on 2008-09-15
double check you have enabled the proprietary drivers in
System>Administration>Hardware Drivers
let me know what happens..any error messages etc...

let me have your xorg.log and xorg.conf 

I am still struggling to understand whether or not my monitor is in the 'indicated ' res. Conflicting reports from xrandr and nvidia-settings. 
It now looks right after spending the best part of the day rebooting, but I at least have some relatively consistent results. I may yet add my voice to the X bugs...

---

### Post by GlennW on 2008-09-15
> **Zimmer said:**
> double check you have enabled the proprietary drivers in
System>Administration>Hardware Drivers
let me know what happens..any error messages etc...

let me have your xorg.log and xorg.conf 

I am still struggling to understand whether or not my monitor is in the 'indicated ' res. Conflicting reports from xrandr and nvidia-settings. 
It now looks right after spending the best part of the day rebooting, but I at least have some relatively consistent results. I may yet add my voice to the X bugs...

Hi Zimmer,

Thanks for quick response. I booted up and immediately checked the enabled proprietary drivers in System>Administration>Hardware Drivers and it was the Nvidia driver. As it should be. There was no error message of any kind.

The xorg.log is as follows:

```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux glenn-desktop 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Sep 15 17:49:11 2008
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first mouse device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1039,0645 card 0000,0000 rev 01 class 06,00,00 hdr 80
(II) PCI: 00:01:0: chip 1039,0001 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0961 card 0000,0000 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:02:1: chip 1039,0016 card 0000,0000 rev 00 class 0c,05,00 hdr 00
(II) PCI: 00:02:2: chip 1039,7001 card 1039,7001 rev 07 class 0c,03,10 hdr 00
(II) PCI: 00:02:3: chip 1039,7001 card 1039,7001 rev 07 class 0c,03,10 hdr 00
(II) PCI: 00:02:5: chip 1039,5513 card 1039,5513 rev d0 class 01,01,80 hdr 80
(II) PCI: 00:02:7: chip 1039,7012 card 13f6,0300 rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,0900 card 1039,0900 rev 90 class 02,00,00 hdr 00
(II) PCI: 00:08:0: chip 10d9,0531 card 0000,0000 rev 25 class 02,00,00 hdr 00
(II) PCI: 00:09:0: chip 1057,5600 card 1057,0300 rev 00 class 07,80,00 hdr 00
(II) PCI: 00:0a:0: chip 1274,5880 card 1274,8001 rev 02 class 04,01,00 hdr 00
(II) PCI: 00:0b:0: chip 1033,0035 card 2098,2100 rev 41 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 1033,0035 card 2098,2100 rev 41 class 0c,03,10 hdr 00
(II) PCI: 00:0b:2: chip 1033,00e0 card 2098,2000 rev 01 class 0c,03,20 hdr 00
(II) PCI: 01:00:0: chip 10de,0221 card 1682,2152 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdbe00000 - 0xdfefffff (0x4100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xbbc00000 - 0xdbcfffff (0x20100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV44A [GeForce 6200] rev 161, Mem @ 0xde000000/24, 0xc0000000/28, 0xdd000000/24, BIOS @ 0xdfee0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xdfffce00 - 0xdfffceff (0x100) MX[B]
	[1] -1	0	0xdfffb000 - 0xdfffbfff (0x1000) MX[B]
	[2] -1	0	0xdfffa000 - 0xdfffafff (0x1000) MX[B]
	[3] -1	0	0xdbdfff00 - 0xdbdfffff (0x100) MX[B]
	[4] -1	0	0xdfffcf00 - 0xdfffcfff (0x100) MX[B]
	[5] -1	0	0xdfffd000 - 0xdfffdfff (0x1000) MX[B]
	[6] -1	0	0xdffff000 - 0xdfffffff (0x1000) MX[B]
	[7] -1	0	0xdfffe000 - 0xdfffefff (0x1000) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[10] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000cc00 - 0x0000cc3f (0x40) IX[B]
	[14] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[18] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[19] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdfffce00 - 0xdfffceff (0x100) MX[B]
	[1] -1	0	0xdfffb000 - 0xdfffbfff (0x1000) MX[B]
	[2] -1	0	0xdfffa000 - 0xdfffafff (0x1000) MX[B]
	[3] -1	0	0xdbdfff00 - 0xdbdfffff (0x100) MX[B]
	[4] -1	0	0xdfffcf00 - 0xdfffcfff (0x100) MX[B]
	[5] -1	0	0xdfffd000 - 0xdfffdfff (0x1000) MX[B]
	[6] -1	0	0xdffff000 - 0xdfffffff (0x1000) MX[B]
	[7] -1	0	0xdfffe000 - 0xdfffefff (0x1000) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[10] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000cc00 - 0x0000cc3f (0x40) IX[B]
	[14] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]


	[16] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[18] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[19] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
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
	[4] -1	0	0xdfffce00 - 0xdfffceff (0x100) MX[B]
	[5] -1	0	0xdfffb000 - 0xdfffbfff (0x1000) MX[B]
	[6] -1	0	0xdfffa000 - 0xdfffafff (0x1000) MX[B]
	[7] -1	0	0xdbdfff00 - 0xdbdfffff (0x100) MX[B]
	[8] -1	0	0xdfffcf00 - 0xdfffcfff (0x100) MX[B]
	[9] -1	0	0xdfffd000 - 0xdfffdfff (0x1000) MX[B]
	[10] -1	0	0xdffff000 - 0xdfffffff (0x1000) MX[B]
	[11] -1	0	0xdfffe000 - 0xdfffefff (0x1000) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[14] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000cc00 - 0x0000cc3f (0x40) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[24] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[25] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.12  Thu Feb 14 18:45:56 PST 2008
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfffce00 - 0xdfffceff (0x100) MX[B]
	[5] -1	0	0xdfffb000 - 0xdfffbfff (0x1000) MX[B]
	[6] -1	0	0xdfffa000 - 0xdfffafff (0x1000) MX[B]
	[7] -1	0	0xdbdfff00 - 0xdbdfffff (0x100) MX[B]
	[8] -1	0	0xdfffcf00 - 0xdfffcfff (0x100) MX[B]
	[9] -1	0	0xdfffd000 - 0xdfffdfff (0x1000) MX[B]
	[10] -1	0	0xdffff000 - 0xdfffffff (0x1000) MX[B]
	[11] -1	0	0xdfffe000 - 0xdfffefff (0x1000) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[14] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000cc00 - 0x0000cc3f (0x40) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[24] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[25] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfffce00 - 0xdfffceff (0x100) MX[B]
	[5] -1	0	0xdfffb000 - 0xdfffbfff (0x1000) MX[B]
	[6] -1	0	0xdfffa000 - 0xdfffafff (0x1000) MX[B]
	[7] -1	0	0xdbdfff00 - 0xdbdfffff (0x100) MX[B]
	[8] -1	0	0xdfffcf00 - 0xdfffcfff (0x100) MX[B]
	[9] -1	0	0xdfffd000 - 0xdfffdfff (0x1000) MX[B]
	[10] -1	0	0xdffff000 - 0xdfffffff (0x1000) MX[B]
	[11] -1	0	0xdfffe000 - 0xdfffefff (0x1000) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[14] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000cc00 - 0x0000cc3f (0x40) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[24] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[27] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[28] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so

(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 262144 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 5.68
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: nv44 Board - p382h1  
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(==) VESA(0): Depth 16, (--) framebuffer bpp 16
(==) VESA(0): RGB weight 565
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: SAM  Model: 21d  Serial#: 1212232240
(II) VESA(0): Year: 2006  Week: 33
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) VESA(0): Sync:  Separate  Composite  SyncOnGreen
(II) VESA(0): Max H-Image Size [cm]: horiz.: 43  vert.: 27
(II) VESA(0): Gamma: 2.20
(II) VESA(0): DPMS capabilities: Off; RGB/Color Display
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) VESA(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) VESA(0): Supported VESA Video Modes:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@67Hz
(II) VESA(0): 640x480@72Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@56Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@72Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 832x624@75Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): 1024x768@70Hz
(II) VESA(0): 1024x768@75Hz
(II) VESA(0): 1280x1024@75Hz
(II) VESA(0): 1152x870@75Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported Future Video Modes:
(II) VESA(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) VESA(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) VESA(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) VESA(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 146.2 MHz   Image Size:  433 x 271 mm
(II) VESA(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) VESA(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) VESA(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 160 MHz
(II) VESA(0): Monitor name: SyncMaster
(II) VESA(0): Serial No: HVYL800816
(II) VESA(0): EDID (in hex):
(II) VESA(0): 	00ffffffffffff004c2d1d0230324148
(II) VESA(0): 	211001030e2b1b782aee95a3544c9926
(II) VESA(0): 	0f5054bfef80b30081808140714f0101
(II) VESA(0): 	01010101010121399030621a274068b0
(II) VESA(0): 	3600b10f1100001c000000fd00384b1e
(II) VESA(0): 	5110000a202020202020000000fc0053
(II) VESA(0): 	796e634d61737465720a2020000000ff
(II) VESA(0): 	004856594c3830303831360a202000a2
(II) VESA(0): EDID vendor "SAM", prod id 541
(II) VESA(0): Using EDID range info for horizontal sync
(II) VESA(0): Using EDID range info for vertical refresh
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) VESA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) VESA(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) VESA(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) VESA(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) VESA(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) VESA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) VESA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) VESA(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) VESA(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) VESA(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) VESA(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 101 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 10
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 102 (800x600)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 100
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 103 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 104 (1024x768)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 128
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 128
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 105 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 106 (1280x1024)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 160
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 160
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 107 (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0

	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 10e (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 10f (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 111 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 112 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 114 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 115 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 117 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 118 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 11a (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 11b (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 130 (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 62
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 62
	LinNumberOfImagePages: 62
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 131 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 132 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 133 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 134 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 135 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 19
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 19
	LinNumberOfImagePages: 19
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 136 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 10
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 13d (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 13e (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 147 (1400x1050)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 1400
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1400
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 148 (1400x1050)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009d81
	BytesPerScanline: 2800
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2800
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000

(II) VESA(0): Total Memory: 4096 64KB banks (262144kB)
(II) VESA(0): Configured Monitor: Using hsync range of 30.00-81.00 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 56.00-75.00 Hz
(II) VESA(0): Configured Monitor: Using maximum pixel clock of 160.00 MHz
(II) VESA(0): Not using built-in mode "1400x1050" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1280x1024" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1024x768" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(--) VESA(0): Virtual size is 800x600 (pitch 800)
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0):  Built-in mode "640x480"
(**) VESA(0): Display dimensions: (430, 270) mm
(**) VESA(0): DPI set to (47, 56)
(II) VESA(0): Attempting to use 72Hz refresh for mode "800x600" (114)
(II) VESA(0): Attempting to use 73Hz refresh for mode "640x480" (111)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfffce00 - 0xdfffceff (0x100) MX[B]
	[5] -1	0	0xdfffb000 - 0xdfffbfff (0x1000) MX[B]
	[6] -1	0	0xdfffa000 - 0xdfffafff (0x1000) MX[B]
	[7] -1	0	0xdbdfff00 - 0xdbdfffff (0x100) MX[B]
	[8] -1	0	0xdfffcf00 - 0xdfffcfff (0x100) MX[B]
	[9] -1	0	0xdfffd000 - 0xdfffdfff (0x1000) MX[B]
	[10] -1	0	0xdffff000 - 0xdfffffff (0x1000) MX[B]
	[11] -1	0	0xdfffe000 - 0xdfffefff (0x1000) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[14] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000cc00 - 0x0000cc3f (0x40) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[24] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[27] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[28] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 262144 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 5.68
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: nv44 Board - p382h1  
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(==) VESA(0): Write-combining range (0xc0000000,0x10000000)
(II) VESA(0): virtual address = 0xa6e7f000,
	physical address = 0xc0000000, size = 268435456
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc101"
(**) Generic Keyboard: XkbModel: "pc101"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
```

And here is the xorg.conf:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008

# xorg.conf (X.Org X Window System server configuration file)
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

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc101"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

```

Thanks again for taking the time to have a look at this.

---

### Post by Zimmer on 2008-09-16
@GlennW
have sent you the text of an xorg.conf you can try.
In terminal type
gksudo nautilus

navigate to /etc/X11

rename your current xorg.conf to lastoxorg.conf
Right click in a space and create an empty file and name it xorg.conf 
Copy the text into the new file and save it.

reboot or restart the X server
Check the xorg.log first to see what has happened.You are looking for lines starting NVIDIA and not VESA.
And if you are lucky you will be able to go 
sudo nvidia-settings, pick the res you want, write it to the xorg.conf and merge it.

---

### Post by GlennW on 2008-09-16
> **Zimmer said:**
> @GlennW
have sent you the text of an xorg.conf you can try.
In terminal type
gksudo nautilus

navigate to /etc/X11

rename your current xorg.conf to lastoxorg.conf
Right click in a space and create an empty file and name it xorg.conf 
Copy the text into the new file and save it.

reboot or restart the X server
Check the xorg.log first to see what has happened.You are looking for lines starting NVIDIA and not VESA.
And if you are lucky you will be able to go 
sudo nvidia-settings, pick the res you want, write it to the xorg.conf and merge it.

Hey Zimmer,
No dice! The nVidia proprietary driver is still enabled but the highest rez available is 800x600. I used the xorg.conf file that you sent and restarted X but to no avail. I had to reboot twice and I'm still back at the same old place. In the xorg.log file there are NO lines that begin with NVIDIA! There are a lot that begin with VESA!! 

What's happening?
Thanks for the help.

---

### Post by Zimmer on 2008-09-17
my best suggestion is that the NVIDIA driver module is not enabled due to a kernel update(or something!)  you should uninstall the proprietary NVIDIA driver and then re install it from the system>administration>hardware drivers  gui..

and try again, check that the xorg.conf is the one I sent before you reboot.

---

### Post by swbrenton on 2008-09-17
> **cdtech said:**
> 

Be sure you have the "System > Administrator > Software sources" under Ubuntu software select "proprietary drivers for devices" and "software restricted" is selected. Do a "sudo apt-get update". Then look in the "System > Administrator > Hardware Drivers" and see if your new drivers are there. If they are just select and restart system.


I'm fixed. I installed 8.04.1 today.  I also was stuck with 800x600 as my highest available resolution.  I kept reading this thread until I found the above advice.  

I went to System >  Administer > Hardware Drivers
The Device driver NVIDIA accelerated graphics driver was un-Enabled.  
I checked the Enabled box.  Closed that box.  Restarted my computer.  
Then went to System > Preferences > Screen Resolution.  
Then I looked at the resolution option and 1440x900 was there.
All is good.

PS for what it's worth I bought Ubuntu Linux for Dummies on Monday.  That was my start date for Linux.  So far so good.:)

---

### Post by GlennW on 2008-09-18
> **Zimmer said:**
> my best suggestion is that the NVIDIA driver module is not enabled due to a kernel update(or something!)  you should uninstall the proprietary NVIDIA driver and then re install it from the system>administration>hardware drivers  gui..

and try again, check that the xorg.conf is the one I sent before you reboot.

Well, I'm truly and thoroughly frustrated! I've gone through I don't know how many posts/threads and done everything I can think of and to no avail. I followed your above advice and, like everything else, nothing has changed. The proprietary NVIDIA drivers are installed and enabled but the the highest rez available is 800x600. 

My only thought, at this point, is to re-install hardy! I don't want to do that since I'm sure that one simple command or the edit of one line will restore order! I've enjoyed my widescreen monitor for a long time and now, for the past month, I've been reduced to this!!

Please, Zimmer, anyone, I need this resolved...

---

### Post by Zimmer on 2008-09-18
The system is still using a failsafe config, Glenn. See the log..
(==) Using config file: "/etc/X11/xorg.conf.failsafe"

Please check (because I cannot see from here ;)  ) that you have saved the config I sent you correctly as xorg.conf  in the /etc/X11  folder.
You will need to do this as the root user (gksudo nautilus entered in the terminal will give you the graphical file system as root)

Without finding another logfile that will show me why the failsafe is being used I can only guess that there is something amiss with the xorg.conf file (ie does not exist/invalid whatever..)
I am at a disadvantage at the moment for diagnosing because my wife's XP computer died and I have had to purchase a new laptop for me! (Great excuse!) and put her XP HDD in my Biostar machine which only holds one HDD. So my Ubuntu HDD is sitting forlorn on the bookshelf until I can find out how to boot it using my USB caddy.
I am currently using the laptop with a Live CD , wondering whether to dual boot  with the Vista ... which I could use for my Line6 equipment..

decisions, decisions..

---

### Post by GlennW on 2008-09-20
> **Zimmer said:**
> The system is still using a failsafe config, Glenn. See the log..
(==) Using config file: "/etc/X11/xorg.conf.failsafe"

Please check (because I cannot see from here ;)  ) that you have saved the config I sent you correctly as xorg.conf  in the /etc/X11  folder.
You will need to do this as the root user (gksudo nautilus entered in the terminal will give you the graphical file system as root)

Without finding another logfile that will show me why the failsafe is being used I can only guess that there is something amiss with the xorg.conf file (ie does not exist/invalid whatever..)


Sorry Zimmer! Being such a linux n00b, you'll have to slow down a bit. I know just enough to be dangerous.......

Just go step by step and I'll follow you to the letter.

---

### Post by GlennW on 2008-09-22
Bump!

---

### Post by Zimmer on 2008-09-24
> **GlennW said:**
> Sorry Zimmer! Being such a linux n00b, you'll have to slow down a bit. I know just enough to be dangerous.......

Just go step by step and I'll follow you to the letter.
Step by step into the abyss :)

Ok, I have just installed Ubuntu Hardy as dual boot on the new laptop.
I followed the regular instructions for installing the NVIDIA driver and all is well. 

So... have you looked at the etc/X11/xorg.cong file to see if it is the one I sent?
Open a Terminal:
type
gksudo nautilus

 enter your password
Navigate to the etc/X11 folder
right click on xorg.conf and check the properties.
Check the owner (should be root)  permissions, read and write for root.

View the file. Is it the one I sent you?

If so, look in the folder for a xorg.conf.failsafe files and rename it to 
xorgfails.conf (so if it all goes pearshaped when you reboot you can go back and rename it back.

---

### Post by owyn on 2008-09-30
Had the same problem with a S3 Unichrome chipset. Checked log and saw that problem was Monitor sync settings were incorrect. Added explicit settings to /etc/X11/xorg.conf Monitor section.

```

Section "Monitor"
	Identifier	"Configured Monitor"
HorizSync 30-69
VertRefresh 50-120
EndSection

```

These settings are correct for MY monitor. Apply with care for other monitors.

---

### Post by jerlinux on 2008-10-09
I blew out a mother board and my new board has the nvidia chipset.  And like the last five pages, I cannot get better than the 600X800 on this machine.  BUT I put the hard drive into an old Shitbomb Compaq, entered the recovery mode, and picked fix the x server.  The old Compaq will now run in the better mode.  So, in my case, it has to be the nvidia chipset.
I am going to carefully review the last five pages to see if any of those fixes will help me.  But I am left with two questions:
Will the update of Ubuntu save me?  Maybe even by coincidence?
And how do I remove all of the backup xorg.conf files that I generated in my vain attempts to get back to the better graphics?

Thanks

---

### Post by snipe6006 on 2008-10-11
Please Help Me!
I tried to change the vesa to intel in the xorg.conf as suggested for someone early in this thread. I restarted and my computer does not run. It stays in low graphics mode and does not allow me to even get the the login screen. What can I do? I dont want to reinstall!

Please Help ME!

EDIT: OK it is fixed now, i just ran nano in recovery mode to undo what i edited.

---

### Post by kavman51 on 2008-12-05
> **cdtech said:**
> I've noticed "envy" has not be mentioned here. Have you given "envy" a shot?
```
sudo apt-get install envyng-gtk
```

your my new hero i found this site by google searching and i have an nvidia integrated 7030 series and envy worked like a champ thanks a lot ;):guitar::biggrin:=D>\\:D/ sorry all the smileys are too fun here

---

### Post by lavallie on 2009-07-20
CDHECH your the bomb!!!  It worked for me after hours of muddleing around these boards.

---

