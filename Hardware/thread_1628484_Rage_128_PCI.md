---
title: "Rage 128 PCI"
date: 2010-11-22
forum: Hardware
---

### Post by joshuajon on 2010-11-22
Hey all. 

I'm trying to set up a Rage 128 PCI graphcis card.  It appears here in "lspci |grep VGA"

> 01:04.0 VGA compatible controller: ATI Technologies Inc Rage 128 RE/SG

I know that the r128 kernel module is loaded as it is explicitly listed in /etc/modules and appears in "lsmod |grep r128"

> r128                   35235  0

I added the card to the xorg.conf with the following 

> Section "Device"
        Identifier      "PCI"
        BusID   "PCI:01:04:0"
        Driver  "r128"
        Screen 1
EndSection

Now what I don't understand is why I get no output on the monitor??  The driver is loaded the device is configured.  It shows up in /var/log/Xorg.0.log
> 
(--) PCI: (0:1:4:0) 1002:5245:b530:0408 ATI Technologies Inc Rage 128 RE/SG rev 0, Mem @ 0xf8000000/67108864, 0xfeafc000/16384, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072

but I get no output and it shows up in "lshw -C display" as UNCLAIMED
> 
*-display UNCLAIMED
       description: VGA compatible controller
       product: Rage 128 RE/SG
       vendor: ATI Technologies Inc
       physical id: 4
       bus info: pci@0000:01:04.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 mingnt=8
       resources: memory:f8000000-fbffffff(prefetchable) ioport:d000(size=256) memory:feafc000-feafffff memory:fea00000-fea1ffff(prefetchable)


Anybody have any guesses on what I should try next?

---

### Post by Fafler on 2010-11-23
Are you trying to setup a dual monitor setup or is it the only graphics device in your system?

The answer really should be in Xorg.0.log. Look at the last few lines before it crashes.

---

### Post by mastablasta on 2010-11-23
> **joshuajon said:**
>  
 
Now what I don't understand is why I get no output on the monitor?? **The driver is loaded** the device is configured. It shows up in /var/log/Xorg.0.log
 

 
which driver? did you try to install the one from ATI website? because that one won't work.
 
i am not sure about PCI version but AGP version worked out of the box last i tried.

---

### Post by joshuajon on 2010-11-23
I didn't install anything from the ATI website so the driver must have been included by default in 10.04.  

Yes, I am trying to set up a dual monitor situation with this ATI card as the secondary monitor.  I don't really see any errors in the Xorg.0.log.  In fact I don't see any mention of the device at all or the r128 driver except in the very beginning of the log where it mentions the configuration pulled from my /etc/xorg.conf:
> 
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Screen "Screen2" (1)
(**) |   |-->Monitor "PCImon"
(**) |   |-->Device "PCI"
(**) Option "Xinerama" "true"
(==) Automatically adding devices
(==) Automatically enabling devices
(**) Xinerama: enabled

The only other mention I see of the card is further down where it says:

> (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
        965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
        4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 0.0.2
        ABI class: X.Org Video Driver, version 6.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:01:04.0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0



Which looks like everything worked, except there's no mention of the r128 driver being opened.  I'm attaching the entire Xorg.0.log as well as my xorg.conf.  (Xorg.0.log had to be broken into 3 parts because of the bizarre restriction on attachments here)

Thanks for your help so far I'd love to see this resolved.  This has been the single biggest headache in my 3 years of using Ubuntu.

---

### Post by joshuajon on 2010-11-24
Am I doomed to suffer this dark, unforgiving world with only one monitor forever?

---

### Post by Fafler on 2010-11-25
I wonder where my other post went... Anyway, you should try writing a complete Xorg.conf including both cards. I'm not sure it will help, but it seems to be worth a try. Also double check the names you have given the graphics adapters and monitors check those in the serverlayout section.

---

### Post by joshuajon on 2010-11-25
Thanks for sticking with me!  I've created a full xorg.conf (attached) and it fails, but in new and interesting ways.  It appears that the r128 driver is at least being loaded now, but I get a blank black screen and nothing else.  Xorg.0.log shows this:

> (--) RandR disabled
(EE) R128(1): Unable to map FB aperture. Argument list too long (7)

Fatal server error:
AddScreen/ScreenInit failed for driver 1


Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
Please also check the log file at "/var/log/Xorg.1.log" for additional information.

 ddxSigGiveUp: Closing log


Also perhaps this error is relevant?  
> 
(EE) R128(1): Cannot read V_BIOS (3) Input/output error
(--) R128(1): Chipset: "ATI Rage 128 GL RE (PCI)" (ChipID = 0x5245)
(--) R128(1): Linear framebuffer at 0xf8000000
(--) R128(1): MMIO registers at 0xfeafc000
(--) R128(1): VideoRAM: 4194303 kByte (64-bit SDR SGRAM 1:1)
(**) R128(1): Using external CRT for display
(WW) R128(1): Failed to read PCI ROM!
(WW) R128(1): Video BIOS not found!



I'm thinking something wasn't specified properly in the xorg.conf but I'm not sure what parameters are missing!  I set the HorizSync and VertRefresh of the monitor, and included Option "NoAccel" "true" in order to not attempt to use the 3d acceleration.

> VideoRAM: 4194303 kByte  This seems wonky!

---

### Post by Fafler on 2010-11-26
Try specifying the amount of memory. The video BIOS is typically because the onboard graphics device already reserves that space. It could cause issues with autodetecting memory and other things, but it should still be still possible to make it work.

---

### Post by joshuajon on 2010-11-29
Well I've given up on the r128 card and I'm trying to get things going with a TNT2 card now.  I've successfully gotten X to boot with both displays, and it correctly spreads the desktop across both monitors but the second monitor only displays weird ugly green lines.

From the multiple monitor configuration window if I click Identify Monitors the second one flashes a bit (the green lines fluctuate) and I can move windows onto it by dragging them to the edge of the screen. 

The monitor is a Dell e153fp which shouldn't require any configuration from what I can tell, but I went ahead and specified the horizsync, vertrefresh, and mode lines anyway.  Any guesses what would cause this funky behavior or how to fix it?

---

### Post by joshuajon on 2010-11-29
After messing with modelines and explicitly setting a display size I now have colored vertical lines instead of just green... but no flashing anymore.  It looks similar to this:  

[http://ubuntuforums.org/attachment.php?attachmentid=68285&d=1209646998](http://ubuntuforums.org/attachment.php?attachmentid=68285&d=1209646998)

I really don't get this.  The card seems to be working, and I've seen this monitor work before.  I've even seen other people configuring the same hardware in ubuntu so I don't know what I'm doing wrong.  Maybe It's time to try a third video card.

---

### Post by Fafler on 2010-11-30
BIOS related? It can be quite troublesome to setup more than one PCI graphics device. Try a old Matrox card if you can get a hold of one. Back in the day, they where really god for multimonitor setups.

---

### Post by joshuajon on 2010-12-04
Could be BIOS related, I don't really know at this point.  The card might be bad, or a problem with the PCI bus I suppose. 

It turns out there's a PCI-e slot but I haven't got any PCI-e cards to try so I think this project is going to have to go on the back burner for now.  

Thanks for your help though, cheers!

---

