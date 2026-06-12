---
title: "HP zv6000 semi-guide"
date: 2005-08-01
forum: Hardware &amp; Laptops
---

### Post by OneSeventeen on 2005-08-01
I just thought I would start a thread and document my progress here, including every command I issue the computer, and a few log files to show what my hardware is like.

If anyone sees that I've done something stupid, go ahead and correct me.  I'm perfectly willing to correct the issue, or even start over if I have to.  Afterwards I'll grab all the correct stuff from this thread and write a quick guide.

My overall PC stats:
```

HP Pavillion zv6000 laptop
15.4" widescreen monitor with brightview
AMD 64 3800+
512MB RAM (one stick)
ATI Radeon Xpress 200M w/128MB RAM
Wireless B/G combo card (Broadcom chip)
4 USB 2.0 ports and 1 firewire port
80GB HDD
DVD +-R/RW (DL)
digital media reader.

```

Progress report:
[list=1]
[*]I installed XP home on a small 20GB partition (sorry, this is a work machine and I need to get stuff done now.  After Ubuntu is working to my satisfaction I'll format and reinstall nothing but ubuntu.)
[*]Booted from Ubuntu 5.04 for AMD64T/EM64T Install CD
[*]typed linux vga=771 and hit enter.
[*]Chose all the English/United States language, keyboard, and time settings that were offered.
[*]Told it to install on the largest nonpartitioned space.  (the left over 60GB)
[*]Gave it a name
[*]Waited while it partitioned the drive
[*]Waited while it installed the Ubuntu base system
[/list]
Surprisingly, with this new laptop, I did not have any keyboard issues.  With my previous zv6000 I had to hold [fn]+[left-shift] for a few seconds to get ubuntu to recognize my keyboard.  (that laptop had an AMD 64 3200+ in it)

I'll post back later with my next few steps.

---

### Post by OneSeventeen on 2005-08-01
Results of base system:
[COLOR=DarkRed]Base system installation error[/COLOR]
```

The debootstrap program exited with an error (return value 1)

Check /var/log/messages or see virtual console 3 for the details.

<Go Back>                                      </Continue>
```

Basically console 3 told me there was a fatal error inserting floppy: No such device.

and no, I don't have a floppy, 

So now it says that the base system installation into /target/ failed.

Which then triggered an "Installation step failed" that took me to the Ubuntu installer main menu.  I then told it to copy the remaining packages to hard disk (that was the item right below 'install the base system'.)

Looks like I might be starting over.  any tips on being sure it doesn't try to write to the floppy disk?

(oh, and I'm using the CDs from shipit.ubuntu.com )

---

### Post by OneSeventeen on 2005-08-01
Rebooted the computer after it copied all of the packages to the hard drive, and after I told it I use "Mountain Time".

It appears as though it is unable to access the Hardware clock via any known method.

It is now installing all of the packages that make up the base system.


[quote=dpkg error message]architecture 'amd64' not in remapping table[/quote]
(I'm hoping this is still okay to continue installing, because it is unpacking all sorts of .deb files right now.)

---

### Post by OneSeventeen on 2005-08-01
All went well, and when I was prompted for my username via gdm's "welcome screen" I hit [ctrl]+[alt]+1 to go to screen 1 and start messing around with stuff.

```

#sudo pico /etc/X11/xorg.conf

```
I then added:
```

Option  "noaccel"

```
Then I saved the file (using [alt]+[x] and pressing [Y] to save changes)
Then restarted gdm with:
```

#sudo /etc/init.d/gdm restart

```

Logged in and everything works great so far!

---

### Post by OneSeventeen on 2005-08-01
Okay, I've just copied the wireless drivers for windows into my /home/oneseventeen/windows_drivers folder.
The files were:
bcmwl564.sys
and
netbc564.inf

Now I just downloaded and unpacked the source for ndiswrapper-1.2 from [ndiswrapper.sf.net](ndiswrapper.sf.net)

I changed "i386" to "amd64" in all of their control.* files in the ndiswrapper-1.2/debian/ folder (I think there were 3 files altogether)

Then I went back to the directory (~/ndiswrapper-1.2/ for me) and typed "make deb"

it thought about things, gave me a warning about substitue variable names that I ignored.

Then I typed
> 
#sudo dpkg -i ndiswrapper*amd64.deb

watched it do its thing, then redownloaded the wireless drivers from [linuxant's website](http://www.linuxant.com/driverloader/drivers.php), just to be sure, and put them in my ~/windows_drivers/ folder.
Then...
```

#sudo ndiswrapper -i ~/windows_drivers/netbc564.inf
        {lots of Forcing Parameter details}
#ndiswrapper -l
Installed ndis drivers:
netbc564   driver present, hardware present
#sudo modprobe ndiswrapper
#sudo ndiswrapper -m
#sudo pico /etc/modules
{I then added "ndiswrapper" without the quotes as the last line}
[ctrl]+[x] 
then 
[y] (to save and exit)
#iwconfig
wlan0  IEEE 802.11g  ESSID:off/any
   {tons of other details}

```

So now the laptop recognizes the wireless device!!
I don't have a wireless network around me, so I'll have to test this out at home and describe my steps then.

---

### Post by OneSeventeen on 2005-08-01
Okay, now I went to [www.ati.com](www.ati.com) and clicked on drivers & software from their top menu.
Then I chose Linux Drivers and Software, and on that page chose "Motherboards with ATI Graphics" from the Linux x86_64 list.

From there I chose "ATI Proprietary Linux x86_64 Driver 8.13.4 for Radeon Xpress 200 Series. and clicked the "Download" link next to X.Org 6.8

Despite the urge to do so, I chose "Save to Disk" instead of "Open with Totem Movie Player" :p

now, I went back to my trusty terminal and:
```

oneseventeen@laptop:~/downloads$ sudo alien -d fglrx64*.x86_64.rpm
fglrx64-6-8-0_8.13.4-2_amd64.deb generated

```
I then used synaptic to make sure I didn't already have any fglrx stuff on my laptop, and also made sure I had the kernel-headers and gcc compiler installed.
Now I'm running regular updates, because I'd rather my system be as up-to-date as possible before messing with the rest of this install process.

---

### Post by OneSeventeen on 2005-08-01
okay, so I ran a sudo dpkg -i --force-overwrite fglrx*.deb and the only downside was it overwrote /usr/X11R6/lib/libGL.so.1.2 (which is also in package xlibmesa-gl)

I don't like overwriting stuff, but this was the only way I could get it to install.

---

### Post by OneSeventeen on 2005-08-01
Okay, now I've had to modify some files, after installing the fglrx  deb installer, go to /lib/modules/fglrx/build_mod and change pci_find_class to pci_get_class in the agpgart_be.c file.

then, for some reason I changed /lib/modules/fglrx/build_mod/make.sh to add CC=gcc -V 3.3 to make it use version 3.3

I then made sure I was in /lib/modules/fglrx/build_mod and ran a "sudo sh make.sh" and went up a directory to the fglrx folder and ran sudo sh make_install.sh

Now I get a Fatal Error stating that it couldn't insert fglrx, that the operation was not permitted.

I'd also like to mention that my monitor is horribly faded, so I have to hold my face 3 inches from the screen in order to read anything when not in a graphical environment.

**EDIT**  After going back into gdm and manually making/make_installing/moving fglrx.ko where it should be, running modprobe fglrx still returns "Operation not permitted"

With the amount of crap I did, I'm thinking I will probably be reinstalling everything again.

---

### Post by kokomo on 2005-08-01
[QUOTE=OneSeventeen]**EDIT**  After going back into gdm and manually making/make_installing/moving fglrx.ko where it should be, running modprobe fglrx still returns "Operation not permitted"

With the amount of crap I did, I'm thinking I will probably be reinstalling everything again.[/QUOTE]

What does dmesg say??

I've had the same trouble with ATI's fglrx drivers.  dmesg tells me I don't have the hardward or extensions.  Some people with zv6000 have luck getting these drivers loaded.

When did you get your zv6000?  I just got mine a week ago, and a lot of the guides online for the zv6000 display different hardware versions. Where i've seen a lot of people have the BCM[COLOR=Red]4306[/COLOR] 802.11b/g Wireless LAN Controller (rev 03) , and I have BCM[COLOR=Red]4318[/COLOR] 802.11b/g Wireless LAN Controller (rev 02) )  However, the ATI hardware versions all seem to be the same.

Try running **lspci** to see what hardware you have.  I know the 64-bit drivers for Broadcom's 4318 wireless card can be found here... [http://www.runithard.com/HOWTO-BCOM64WIRELESS/Acer80211g.rar](http://www.runithard.com/HOWTO-BCOM64WIRELESS/Acer80211g.rar)  
I'm not sure if these work for ndiswrapper because I'm running the 32-bit version, and I didn't know these drivers existed when I had the AMD64.

As far as video drivers, I have no clue what to use.  I'm currently running my ati driver with Option "NoAccel" "true" which sucks because the glxgears only run at a max of 300 FPM and gnome is so freakin slow.  I've tried EVERYTHING!!!!  All the way to a unsuccessful custom kernel... 

Sorry I don't have much of an answer for your solutions, I hope someone comes out with a solution soon!

Good Luck!
-Mike



BTW, Here is the output of my lspci:

> 0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5950 
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f 
0000:00:04.0 PCI bridge: ATI Technologies Inc: Unknown device 5a36 
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4374 
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4375 
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4373 
0000:00:14.0 SMBus: ATI Technologies Inc: Unknown device 4372 (rev 10) 
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4376 
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 4377 
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4371 
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc: Unknown device 4370 (rev 01) 
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 4378 (rev 01) 
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge 
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge 
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge 
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge 
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5955 
0000:03:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) 
0000:03:02.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02) 
0000:03:04.0 CardBus bridge: Texas Instruments: Unknown device 8031 
0000:03:04.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033 
0000:03:04.4 0805: Texas Instruments: Unknown device 8034 
0000:03:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by OneSeventeen on 2005-08-01
I've been able to get the wireless working fine (I'm posting this via my wireless network at home) but I'm still having issues with fglrx.  I had the fglrx module compiled and loaded on this laptop with a 32-bit version of ubuntu, but I really want to get the most out of this laptop.
[quote=lspci]
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5950
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:04.0 PCI bridge: ATI Technologies Inc: Unknown device 5a36
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4374
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4375
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4373
0000:00:14.0 SMBus: ATI Technologies Inc: Unknown device 4372 (rev 10)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4376
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 4377
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4371
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc: Unknown device 4 370 (rev 01)
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 4378 (rev 01)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 595 5
0000:03:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000  Controller (PHY/Link)
0000:03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless  LAN Controller (rev 03)
0000:03:04.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:03:04.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
0000:03:04.4 0805: Texas Instruments: Unknown device 8034
0000:03:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
[/quote]

---

### Post by DAVIUR on 2005-08-13
[QUOTE=OneSeventeen]Okay, now I've had to modify some files, after installing the fglrx  deb installer, go to /lib/modules/fglrx/build_mod and change pci_find_class to pci_get_class in the agpgart_be.c file.

then, for some reason I changed /lib/modules/fglrx/build_mod/make.sh to add CC=gcc -V 3.3 to make it use version 3.3

I then made sure I was in /lib/modules/fglrx/build_mod and ran a "sudo sh make.sh" and went up a directory to the fglrx folder and ran sudo sh make_install.sh

Now I get a Fatal Error stating that it couldn't insert fglrx, that the operation was not permitted.

I'd also like to mention that my monitor is horribly faded, so I have to hold my face 3 inches from the screen in order to read anything when not in a graphical environment.

**EDIT**  After going back into gdm and manually making/make_installing/moving fglrx.ko where it should be, running modprobe fglrx still returns "Operation not permitted"

With the amount of crap I did, I'm thinking I will probably be reinstalling everything again.[/QUOTE]


Hi  :smile: , ...

I had only to do:

1° :  cd /lib/modules/fglrx/build_mod/2.6.x/
2° :  make  
3° :  cd ..  (Got to /lib/modules/fglrx/build_mod/ )
4° :  . make.sh
5° :  cd ..  (Got to /lib/modules/fglrx/ )
6° : chmod u+x make_install.sh
7° : ./make_install.sh

**NOTE:** I did not change any file in /lib/modules/fglrx and i am using 2.6.10-5-amd64-k8 kernel
           
Next, i modified my /etc/X11/xorg.conf:

[PHP]
Section "Device" 
         Identifier  "ATI Tecnologies, Inc. Radeon Xpress 200M (RS480)"
         Driver       "fglrx"
 ------> Option      "NoAccel"   <------ "COMMENT OR CLEAN THIS LINE"
         BusID       "PCI:1:5:0"
         Option      "UseInternalAGPART" "no"   <------ "IMPORTANT!!"
[/PHP]

**NOTE:** Be sure that you load DRI and GLX modules in Section "Module", and that you have the Section "DRI" with Mode 0666.

You shoud have normal acceleration with 700 odd fps ... :) 

I am working in order to improve that.....

Greetings...

---

### Post by tmilam on 2005-08-16
I don't have the zv6000...but I have a notebook with the same video card. The compaq v2000z. I tried that and got:

```
FATAL: Error inserting fglrx (/lib/moFATAL: Error inserting fglrx (/lib/modules/2.6.11-1-amd64-k8/kernel/drivers/char/drm/fglrx.ko): Operation not permitted
failed.
```

........on the last step.

dmesg says:

```
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 608 MBytes.
ACPI: PCI interrupt 0000:01:05.0[A] -> GSI 10 (level, low) -> IRQ 10
[fglrx:firegl_stub_register] *ERROR* Unable to the open some already present DRM kernel module!
```

I don't get it. There is no DRM kernel module there! I'm currently using vesa. Does that count?

 ](*,)

---

### Post by DAVIUR on 2005-08-18
[QUOTE=tmilam]I don't have the zv6000...but I have a notebook with the same video card. The compaq v2000z. I tried that and got:

```
FATAL: Error inserting fglrx (/lib/moFATAL: Error inserting fglrx (/lib/modules/2.6.11-1-amd64-k8/kernel/drivers/char/drm/fglrx.ko): Operation not permitted
failed.
```

........on the last step.

dmesg says:

```
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 608 MBytes.
ACPI: PCI interrupt 0000:01:05.0[A] -> GSI 10 (level, low) -> IRQ 10
[fglrx:firegl_stub_register] *ERROR* Unable to the open some already present DRM kernel module!
```

I don't get it. There is no DRM kernel module there! I'm currently using vesa. Does that count?

 ](*,)[/QUOTE]


Hi tmilam...

Have you tried installing the ATI X300 X400 X... Ubuntu driver (from apt-get)?

I know that it could be a little rare and nothing elegant, but I have found that in some cases installing and then uninstalling this driver, makes accessible the option of installing the proprietary drivers (8.13.4 X200)...

Obviously this driver does not work for your card.!!!! [-X 

Actually I do not know which is the reason :-| ... but try...  only lose a little of time...

Let me know if that work for you...

luck..!! :)

---

### Post by tmilam on 2005-08-19
Thanks for your reply :)

I tried installing xorg-driver-fglrx then uninstalling it. Then installing the 200m driver from ati again. It didn't work :(

So then I tried removing the driver I installed myself and then installing the xorg-driver-fglrx with kernel 2.6.11-1-amd64-k8. No luck here either. 

Oh, I forgot to mention I switched from hoary 32bit to amd64 :D

Now there error message I get is different, but just as hopeless:

```
Trying to register duplicated ioctl32 handler c0246400
[fglrx:firegl_init_32compat_ioctls] *ERROR* unable to register ioctl32 0
[fglrx:firegl_init] *ERROR* Couldn't register compat32 ioctls!

```

Funny thing is that I get this message with either ati driver that I try.  :roll: 

I have tried searching the forums for this error message. Sure, other people are having the same message but nobody is posting a solution! The consensus is 'wait till a new ati driver comes out or try a different kernel....'   :neutral:

---

### Post by OneSeventeen on 2005-08-21
Here's the forum I followed:
[http://zv6000forums.com/viewtopic.php?t=291](http://zv6000forums.com/viewtopic.php?t=291)

Unfortunately I haven't updated this thread again, but I've been keeping notes.  I'll post my steps later on in the week.

Here's the overall results:
Roughly 1200FPS in glxgears and 120FPS in fgl_glxgears!

The first thing I did to get into my system was modify /etc/X11/xorg.conf and add:
```

  option  "noaccel"

```
in the ati driver section.

Then I could boot into the system (using 1280x800, just no 3d accelleration)

Then I upgraded my system, downloaded ati's x200 drivers for "motherboards with built-in graphics", used
$alien -d ati_driver.rpm
$dpkg -i --force-overwrite ati_driver.debhttp://zv6000forums.com/viewtopic.php?t=291

then I changed "pci_find_class" to "pci_get_class" in /lib/modules/fglrx/build_mod/agpgart_be.c, and told /lib/modules/fglrx/build_mod/make.sh to use "gcc-3.3" 
old make.sh:
```

# default options
OPTIONS_HINTS=1
if [ -z "${CC}" ]; then 
	CC=gcc
fi

```
new make.sh:
```

# default options
OPTIONS_HINTS=1
if [ -z "${CC}" ]; then 
	CC=gcc-3.3
fi

```

Then I ran make.sh, then up a directory and make_install.sh

Then, I messed with xorg.conf a ton... heres the graphics portion I ended up with:
```

#NEW VIDEO CARD STUFF
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
#    Option "DesktopSetup"               "0x00000200"  #horizontal LCD=primary
#    Option "DesktopSetup"               "0x00000201"  #horizontal LCD=secondary
#    Option "DesktopSetup"               "0x00000300"  #virtical LCD=primary
#    Option "DesktopSetup"               "0x00000301"  #virtical LCD=secondary
#    Option "DesktopSetup"               "0x00000100"  #clone
#    Option "DesktopSetup"               "0x00000000"  #single
    Option "DesktopSetup"               "0x00000000" 
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "IgnoreEDID"                 "off"
#    Option "HSync2"                     "31.5 - 60.0" 
#    Option "VRefresh2"                  "60 - 85" 
    Option "ScreenOverlap"              "0" 
# === TV-out Management ===
    Option "NoTV"                       "no"     
    Option "TVStandard"                 "NTSC-M"     
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "yes"
    Option "ForceGenericCPU"            "no"
#    BusID "PCI:1:0:0"    # no device found at config time
#    BusID "PCI:1:5:0"    # no device found at config time
    Screen 0
EndSection

```

And, just for fun, I've got a 5 button Microsoft Intellimouse Explorer that I configured, but I'll post that later (time to head to bed, and I want to find the link first anyway so I can give credit where it is due)

But like I said, I used that link and with the help of "hasr4000" and finally have my system up and running!

I'll post more later.

---

### Post by jamesrw on 2005-08-22
i have a v2000z and loaded the driver for the 200m :) 
found a great post:

[http://www.ubuntuforums.org/showpost.php?p=306640&postcount=9](http://www.ubuntuforums.org/showpost.php?p=306640&postcount=9)

---

### Post by tmilam on 2005-08-23
I keep getting different results with basic performance issues, disk transfer rates and the ati driver because I keep reinstalling  :roll: 

I built my own 2.6.12.5 kernel from vanilla sources and built the ati driver off of that and now it's working (all 32 bit system). And BTW I haven't noticed any speed differences between ubuntu 32 and 64 bit, so I'm not bothering with 64 bit 

So yes, I have the ati driver working in 32 bit. I had it working before getting 370FPS in glxgears. Now that I have the ati driver working once again I'm getting 340FPS tops (68FPS in fgl_glxgears). I know this card could probably do over 1,000FPS easily in glxgears and have no clue why it's doing so poorly. 

Another problem I'm seeing is that even with atiixp and everything else built into a custom kernel, I'm only seeing hdparm do 16MB/s. What are you guys getting?

```
vitriol@solstice:~$ sudo hdparm -t /dev/hda
Password:

/dev/hda:
 Timing buffered disk reads:   52 MB in  3.07 seconds =  16.94 MB/sec

```

This especially doesn't make sense since I used the 2.6.11 kernel before on 32 bit and got 33MB/s. But everytime since then, it has been 16MB/s :(


We've all gone through an amazing amount of trouble.......there are alot of very tiny detailed steps to go through to get everything working and it seems we really haven't worked this all out, either. The only thing that is different for any of us in this thread is essentially screen size! Some have 1280x768 and others have 1280x800. Output from lspci looks exactly the same. We should write a HOW-TO for the zv6000/v2000z/m2000. I've seen other posts throughout the forums about these models and answered the questions, but we should put it all in one place with the first post being a definitive guide on getting these beasts working :D

---

### Post by tmilam on 2005-08-23
I was experimenting with different kernel configuration, and I found that certain settings were not correct. The first involved the graphics.....once this was fixed, my FPS in glxgears more than **doubled**!!

Also, I noticed that my ATA driver was not correct either. atiixp needs to be set in the kernel configuration ;) Yes, you can load the atiixp module, but if you are using the 2.6.10 kernel you'll only see a transfer rate of 16mb/s (with the 5400rpm hard drive, some of us have the 4200rpm drive, so it will be slower). Maybe the atiixp module has matured?

Now I'm going to play with the xorg.conf some more and see if I can tweak 1200fps out of it as you did, OneSeventeen!

---

### Post by jared85 on 2005-08-27
Hello I have been following your advice ([http://www.ubuntuforums.org/showpost.php?p=311391&postcount=15](http://www.ubuntuforums.org/showpost.php?p=311391&postcount=15)) along with the thread on the other forum.

Everything runs fine with minimal amount of errors until I make.sh.

its telling me the device is not found :(
```

- trying a sample load of the kernel module
[fglrx:firegl_init] *ERROR* Device not found!
FATAL: Error intserting fglrx (lib/modules/2.6.10-5-amd64-generic/kernel/drivers/video/fglrx.ko): No such device
failed.

```

Any ideas. This thread has been a big help so far on my compaq V2000 which has a turion and the bastard 200m.

Any insight on this error would be appreciated.

/me goes to rape the search button.

Thanks

---

### Post by jared85 on 2005-08-28
ok well I did what you had in the fglrx-install.txt and everything went ok.

Been changing a couple things in the xorg.conf.

Even with the ati driver I am only getting 280 in glxgears and 63 in fgl_glxgears.

I did what was suggested in a previous post, made sure it was using the correct .ko. Results are the same.

I still need to fix the DMA and 2x timer issue. Could those two problems be keeping me at such low fps as opposed to 1000+ fps?

Will I even be able to do those fixes since I am using the amd64 install?

---

### Post by mcoliver007 on 2005-08-29
Hi,
(that's the first time I use the power of a forum!)
I'm seeing that you have an broadcom 4318, me too,
you seem to have installed successfully your network,
could you give me some information about the installation
of your chip ?

(
What I have already done:
1)installation of ndiswrapper (under debian).
2)installation of windows drivers given by the laptop manufacturer (acer aspire 3022)
3)my hardware is detected
4)I have done 'iwlist scan' ... no network found.
perhaps it's necessary to write /etc/networks even if it is just to
scan networks around my laptop?
)

(please help me  ](*,)  !)
best regards,
mco

---

### Post by tmilam on 2005-09-01
did you do 

```
modprobe ndiswrapper
``` 

After doing that run

```
dmesg | grep wlan0
``` 

If you don't see something relating to your network card, you installed the wrong driver. This is a common issue with people running 64 bit ubuntu (trying to use the 32bit driver). Or vice versa. Good luck :)

---

### Post by mcoliver007 on 2005-09-02
thanks for your answer tmilam,
I use the 32-bit driver from ACER, my chip broadcom 4318 is recognized, but my debian doesn't find any network (window$...finds them...)
so, I continue searching solutions !
see you later :D

---

### Post by mcoliver007 on 2005-09-03
[QUOTE=mcoliver007]thanks for your answer tmilam,
I use the 32-bit driver from ACER, my chip broadcom 4318 is recognized, but my debian doesn't find any network (window$...finds them...)
so, I continue searching solutions !
see you later :D[/QUOTE]
 I have positive news:
my broadcom BCM 4318 (wireless) on my laptop ACER Aspire 3022WLMi works !!!! :D
(e.g iwlist wlan0 scan gives me good  results)

What have I done ? => go on the web site "http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html"
and install **acer_acpi module**

with this module I can control 3 things:
- Enable/Disable radio wireless
- Enable/Disable radio bluetooth
- Blink/Shutdown Mail LED.

now, I have to configure my wireless network.

I hope this forum could help many people, because I have seen a lot of them with the same
issue.

---

### Post by soulminer on 2005-12-06
Hello I have tried to follow this guide to the letter, without luck.

When I installed Breezy 64 for AMD, I could never complete the install due to it locking up at various stages of progress.

Next, while I install Breezy 32, I cannot get the X server started, and I get a message to check the Xorg.

While I pride myself on being able to do most of the investigation myself, this seems to be a stopping point for me.

Since I am new I would also like to find some basic information on how to install video drivers.

I'm including relevant logs and conf file.  

I have a Pavillion zv6000, Radeon 200M 512, 100 GB, etc,
I did not see a setting for Cool'n 'Quiet in the BIOS either.


Any help would be greatly appreciated.


Thanks very much.
-RS

---

