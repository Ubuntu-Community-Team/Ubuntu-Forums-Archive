---
title: "Low resolution of external monitor with Intrepid"
date: 2008-11-04
forum: Hardware
---

### Post by michaelc.nash on 2008-11-04
Hi guys,

I've got a clean install of Intrepid on my laptop (IBM/Lenovo Thinkpad R60e) and need to use an external monitor at work.

What I would like to do is have the laptop monitor off, and the external monitor on. Just plugging in the monitor's cable was enough to get the Monitor Resolution Settings window up, and turning off the laptop screen was a doddle.

The remaining trouble is that the resolution of the external monitor is pathetic. It's a 21" NEC, so it ought go have a huge resolution and I am stuck at 1024x768.

Does anyone know how I persuade my laptop to turn off its own monitor and (most importantly!) use the external monitor at maximum resolution, just by booting it with the external monitor corrected?

If that's not possible, just knowing how to get the maximum external monitor resolution possible would be fantastic.

(I'm rather a newbie, sorry! I understand what is meant by command line and the simpler command line commands, but I know nothing of monitors, monitor drivers, or the guts of Linux.)

Thanks in advance!

---

### Post by nixscripter on 2008-11-04
It could be a couple of things.

1. The monitor isn't telling the graphics card it can support higher than 1024x768.
2. The graphics card isn't telling the graphics driver to use higher than 1024x768.
3. The graphics driver is too stupid to support higher than 1024x768, even though the card can.
3. X windows isn't telling the graphics driver to use higher than 1024x768.

Starting with the last one, post the contents of **/etc/X11/Xorg.conf**. Please put it in [code] forum tags so it's readable.

---

### Post by michaelc.nash on 2008-11-05
My /etc/X11/xorg.conf is:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2048 768
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

I left off the comment spiel at the beginning of the file. Thanks for your help :)

---

### Post by nixscripter on 2008-11-05
That "Virtual" line jumps out at me.

It says that X windows is creating an imaginary 2048x768 screen (two 1024x768 screens next to each other) and having each monitor display half of it. I would say that the problem is, when you try to increase your resolution, it runs out of screen to display (it thinks).

I'm afraid the only solution (at least the one based on this information) is to change your monitoring setup. Either you will have to make both monitors the same, larger resolution (which may be impossible) or only have part of the screen displayed on one monitor (because the virtual screen is larger than the physical screen).

However, I'm not an X windows expert. Hopefully, someone else can give you a better answer.

---

### Post by michaelc.nash on 2008-11-06
Eurk, that does sound rather horrid.

Is it not possible to just get rid of the virtual screen business? When the external screen is connected I don't want the laptop screen on at all.

---

### Post by nixscripter on 2008-11-06
It's possible, but depending on how that was set up, it might have been for a reason. It looks like a generic sort of file that allows something else to do all the hard work.

The alternative would be to have two separate screens -- one internal, one external -- and tell the card to drive them both. However, whether the card (and the driver) will do that requires trial and error.

What video card and driver do you use? If you don't know, you can start out by posting the output of ```
lspci
```

---

### Post by michaelc.nash on 2008-11-07
I'm afraid I don't know what I've got, but the output of lscpi is here:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 21)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

```

Thanks for your help :)

---

### Post by nixscripter on 2008-11-07
Er, whoops, I meant to say ```
lspci -k
```

Because I'm curious about the kernel driver.

---

### Post by michaelc.nash on 2008-11-07
Not to worry, we all make mistakes!

Output of lspci -k:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	Kernel modules: intelfb
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Kernel modules: intel-rng, iTCO_wdt
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Kernel modules: i2c-i801
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 21)
	Kernel driver in use: tg3
	Kernel modules: tg3
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
```

---

### Post by nixscripter on 2008-11-08
Okay, looks like you're using the Intel Framebuffer driver. Good, nothing weird there.

Time for a little editing. First, make a backup copy of your xorg.conf file. 

You should have a section something like this:

```

Section "Monitor"
    Identifier "Configured Monitor"
    # more junk here...
EndSection

```

First add another section entry for the second monitor, using a format similar to the first one.

```

Section "Monitor"
    Identifier "External Monitor"
    DisplaySize # X-size Y-size
    HorizSync # min-max
    ModelName # what it is
    VendorName # blah
    VertRefresh # min-max
EndSection

```

Set up the values for your monitor. 

Second add a screen section to utilize all that huge real estate:

```

Section "Screen"
    Identifier "Screen1"
    Device "Configured Video Device"
    Monitor "External Monitor"
    DefaultDepth 24
    SubSection "Display"
    Viewport 0 0
    Depth 8
    Modes "1024x768" "800x600" # add whatever huge mode you want here
    EndSubSection
    SubSection "Display"
    Viewport 0 0
    Depth 16
    Modes "1024x768" "800x600" # add whatever huge mode you want here
    EndSubSection
    SubSection "Display"
    Viewport 0 0
    Depth 24
    Modes "1024x768" "800x600" # add whatever huge mode you want here
    EndSubSection

EndSection

```

Finally, edit one more section at the bottom. There should be one called "ServerLayout" Add the second screen you created to it. Instead of the screen entry, put in both screens like this:

```

Screen 0 "Default Screen" 0 0
Screen 1 "Screen1" RightOf "Default Screen"

```

Cross your fingers. If we're lucky, it will work. I don't know how well it will plug and play, so I would suggest first trying this (reboot) with the monitor plugged in.

---

### Post by michaelc.nash on 2008-11-10
Right, I think I've written my new xorg.conf correctly, but I just want to check before I use it:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Monitor"
	Identifier	"External Monitor"
	DisplaySize 	1600 1200
	HorizSync 	31.5-91.1
	ModelName	2170NX
	VendorName	NEC
	VertRefresh	56-85
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device	   	"Configured Video Device"
	Monitor	   	"External Monitor"
	DefaultDepth	24
	SubSection "Display"
		   Viewport	0 0
		   Depth	8
		   Modes	"1600x1200" "1280x1024" "1280x960" "1152x870" "1152x864" "1024x768"
	EndSubSection      
	SubSection "Display"
		   Viewport	0 0
		   Depth	16
		   Modes	"1600x1200" "1280x1024" "1280x960" "1152x870" "1152x864" "1024x768"
	EndSubSection      
	SubSection "Display"
		   Viewport	0 0
		   Depth	24
		   Modes	"1600x1200" "1280x1024" "1280x960" "1152x870" "1152x864" "1024x768"
	EndSubSection      
EndSection

Section "ServerLayout"
	Screen 0 "Default Screen" 0 0
	Screen 1 "Screen1" RightOf "Default Screen"	
EndSection
```

That's it in its entirety (except for the standard commented-out blurb at the beginning). Just in case it matters, here's the original xorg.conf:
```

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 2048 768
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection
```

Thanks again.

---

### Post by nixscripter on 2008-11-10
First: are you sure there didn't used to be anything else in the ServerLayout section? Mine's a lot bigger than that.

Second: you might want to change that virtual screen to the size of your actual screen (1024x768 or whatever it is) on the built-in screen.

Other than that, it looks like it should work -- I hope ;-).

---

### Post by michaelc.nash on 2008-11-10
There was definitely nothing mentioning ServerLayout at all, and this is a clean install of Intrepid not an update.

Hang on, I am confused. I have no mention of VirtualScreen in the *new* xorg.conf I made, following your prescription. It's only mentioned in the *old* xorg.conf.

Does this mean that there are elements of the old xorg.conf I need to keep in the new one, which I haven't put back in yet?

(The code in my previous post is, respectively, the *entire* new and *entire* old xorg.conf respectively, with the blurb at the beginning removed.)

Thanks (again!),

Michael

---

### Post by nixscripter on 2008-11-11
Okay, let me clarify.

You need both of the two things you posted above with the changes I made. In other words, the following sections:

Monitor for Configured Monitor
Monitor for External Monitor
Screen for Screen1 (the new one)
Screen for Default Screen (with my change of display)
Device for Video Device
ServerLayout (the new one)

Sorry if I wasn't clear.

---

### Post by mingohills on 2008-11-19
So I am having nearly the same problem

I am running Intrepid on an old Dell XPS M140. Basically I am just trying to use my sharp flat screen as a second monitor for video editing, hulu, and other streaming media (mirror or otherwise). My standard default resolution is 1280x800, but when I plug the external monitor in all resolution options under gdm max out at 1024x768.  As soon as I unplug and "detect displays" my options are back up and running.

I followed your instructions, when I logged off, I had a text message saying "Stopping GNOME Display Manager" and then it froze.  After a manual shutdown. I booted up and there was no gui.  All log in etc. was command line.  So I reverted to the old xorg.conf file and rebooted and back to square one.  

Here is the code from my modified xorg.conf that caused the "crash"
```
Section "Device"

	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Monitor"
    Identifier 	"External Monitor"
    DisplaySize 1366 768
    HorizSync   31.5-60.0
    ModelName   LC32SB24U
    VendorName  Sharp
    VertRefresh 56-75
EndSection

Section "Screen"
    Identifier "Screen1"
    Device "Configured Video Device"
    Monitor "External Monitor"
    DefaultDepth 24
    SubSection "Display"
    Viewport 0 0
    Depth 8
    Modes "1024x768" "800x600" # add whatever huge mode you want here
    EndSubSection

    SubSection "Display"
    Viewport 0 0
    Depth 16
    Modes "1024x768" "800x600" # add whatever huge mode you want here
    EndSubSection
    SubSection "Display"
    Viewport 0 0
    Depth 24
    Modes "1024x768" "800x600" # add whatever huge mode you want here
    EndSubSection
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Screen 0 "Default Screen" 0 0
	Screen 1 "Screen1" RightOf "Default Screen"	
EndSection

```

And here is the default xorg.conf file that I am running with now.
```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Any thoughts or suggestions would be much appreciated!!!!  I am decent at following directions, I promise.

---

### Post by nixscripter on 2008-11-20
I'm starting to wonder if I'm missing something, because "configured video device" seems to involve black magic somewhere. Let me see if I can get someone's help on this.

---

