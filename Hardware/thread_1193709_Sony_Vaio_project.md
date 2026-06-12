---
title: "Sony Vaio project"
date: 2009-06-21
forum: Hardware
---

### Post by VaioPengiun on 2009-06-21
I am currently working on getting my Sony Vaio (PCG-FX310) to work properly with Ubuntu 9.04.  In my searches for clues, information, and solutions I have found that others are having the same problems on their similarly configured Vaio's.  I have started this thread to share my successes (on seemingly unresolved issues), rather than my woes, with anybody with similar issues and encourage anyone else to add their successes as well.

**System Specs:**
Sony PCG-FX310
14.1" TFT LCD ( 1024x768 )
Mobile Intel Celeron 900MHz
Intel 815EM Integrated Video (11MB shared memory)
Intel 815EM Integrated Audio
512MB PC100 RAM
80GB HDD w/ Ubuntu 9.04
PCMCIA:
    LINKSYS Wireless-G Notebook Adapter (Model No.:WPC54G ver.4)
    USB2.0 CardBus 4 port expander (Model:QFASCB)
USB:
    Novatel Wireless -- Verizon Broadband Access (USB727)

**First issue resolved: 800x600 max resolution (should be 1024x768 )**
After reading every man page, any related thread, and trying just about anything, I have been able to solve my video issue using the following entries in */etc/X11/xorg.conf* :
```

Section "Device"
    Identifier    "Intel"
    **Driver        "intel"**
EndSection

Section "Monitor"
    Identifier    "LVDS"
    VendorName    "Sony"
    ModelName    "Sony Vaio XGA 1024x768"
    [B]Option        "DDC"    "false"
    HorizSync    35.00-50.00[/B]
EndSection

Section "Screen"
    Identifier    "Vaio Screen"
    Monitor        "LVDS"
    Device        "Intel"
    DefaultDepth    24
    [B]Subsection "Display"
    Depth 24
    Modes "1024x768" "800x600" "640x480"
    EndSubsection[/B]
EndSection
```The above sections in **bold** were key.

I hope this helps!

Note: The following link is a fix that didn't work for me.  *ddcprobe* and *read-edid* would return bogus information.
[http://ubuntuforums.org/showthread.php?t=998642#postmenu_6489466](http://ubuntuforums.org/showthread.php?t=998642#postmenu_6489466)

---

### Post by VaioPengiun on 2009-07-12
[B]Second issue resolved: LinkSys Wireless card no-worky

[/B]Okay, this one was easy.... after I found the original Winders driver disc.  I have a **LinkSys WPC54G Ver.4** and, of course, you can't get the driver from their website.  If their is anybody that is in need of this driver, let me know and I'll share the iso of the disc I have.

First thing, verified if the system could see my hardware:
```
kobbler@SaltyDog:~$ sudo lspci
[sudo] password for kobbler: 
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 11)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 03)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 03)
01:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AA22 IEEE-1394 Controller (PHY/Link Integrated) (rev 02)
01:02.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
01:02.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
02:00.0 USB Controller: NEC Corporation USB (rev 43)
02:00.1 USB Controller: NEC Corporation USB (rev 43)
02:00.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
**06:00.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)**

```Next I needed to install *ndiswrapper*, but after looking through the Synaptic Package Manager, I noticed a GUI called *ndisgtk* and decided to give it a try.

First run gave me this:
[IMG]http://i918.photobucket.com/albums/ad26/kobbler248/ndisgtkerror.png[/IMG] 
But continued anyway... (thinking it's a permission problem, but haven't really investigated further)

Click [+ Install New Driver]
[IMG]http://i918.photobucket.com/albums/ad26/kobbler248/ndisgtkinstallnewdriver.png[/IMG]

Navigate to driver *inf* file location (cdrom/wlipnds.inf):
[IMG]http://i918.photobucket.com/albums/ad26/kobbler248/ndisgtkSelectinfFile.png[/IMG]

Click [Open] and receive same error message Click [OK] and:
[IMG]http://i918.photobucket.com/albums/ad26/kobbler248/ndisgtksuccessfuldriverinstall.png[/IMG]

Not sure if security encryption works yet, as I've only connected to an open wireless access point.

Again, I hope this helps!

---

### Post by CerealKiller93 on 2009-09-01
Whats up. 
This happens to be my first post on the forums here. I just registered yesterday. 

I also am running Ubuntu 9.04 on my Sony Vaio PCG-FRV26. I just upgraded to 9.04 yesterday, had been running 8.1 since January on it. I resolved almost all my issues, and yesterday i actually got my wireless adapter working.
I also have a WPC54g VER 3 Wireless adapter. I had tried using ndiswrapper with no luck. I succesfully got it installed, but could not ever find a windows driver that would work with it. After i upgraded yesterday i got the "broadcom" linux driver to work. 

I take my laptop to work with me for when theres nothing to do at work. I don't use wireless there, i just plug into the network. I got home today and put my wireless card in the card slot, and now Linux doesn't even recognize it. 

I'm not sure if the Version 4 driver you have will work with the version 3, but it would be awesome if i could get that iso. 

I'm going to send you a private message with this reply in case you don't check this thread very often. I noticed you posted it a couple months ago, so i figure this is a good idea to give you a heads up.

---

### Post by CerealKiller93 on 2009-09-01
Linux is recognizing that my wireless card is installed, but it is not showing it in networking.

Any ideas:confused:

---

### Post by VaioPengiun on 2009-09-06
Post your ifconfig details for some more insight on the issue...
 
You might have to wait a few moments for Ubuntu to show it in the toolbar drop down. It usually takes mine some time after bootup and when card is first inserted.
 
> I got home today and put my wireless card in the card slot, and now Linux doesn't even recognize it. 

Does this mean that it was working before with your ndis-wrapped Linksys driver and Ubuntu?

---

