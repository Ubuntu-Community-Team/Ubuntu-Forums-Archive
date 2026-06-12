---
title: "ubuntu for hp dv2845se"
date: 2008-10-16
forum: General Help
---

### Post by j_rob313 on 2008-10-16
i'm thinking about putting kubuntu on my hp dv2835se instead of vista.  i've been having lots of problems with vista and xp is not working much better as lots of the drivers don't work for this particular model.  is kubuntu a good solution to this problem? does kubuntu offer all the drivers available? 

here are some of the specs for the laptop:

Processor
AMD Turion 64 X2 mobile technology TL-62 / 2.1 GHz
Multi-Core processor technology
Dual-Core
64-bit processor
Yes
Data bus speed
800 MHz

Cache Memory

Type
L2 cache
Cache size
1 MB

RAM

Installed Size
4 GB / 4 GB (max)
Technology
DDR II SDRAM
RAM form factor
SO DIMM 200-pin
RAM configuration features
2 x 2 GB

Storage Controller

Storage controller type
Serial ATA
Storage Controller / Serial ATA Interface
Serial ATA-150

Storage

Floppy Drive
None
Hard Drive
250 GB - Serial ATA-150 - 5400 rpm
Storage Removable
None
Hard drive type
Portable

Optical Storage

Type
DVD±RW (±R DL) / DVD-RAM
Disc Labeling Technology
LightScribe Technology

Optical Storage (2nd)

2nd optical storage type
None

Card Reader

Card reader type
5 in 1 card reader
Supported flash memory cards
Memory Stick, MultiMediaCard, SD Memory Card, XD-Picture Card, Memory Stick Pro

Display

Display Type
14.1 in TFT active matrix
Max Resolution
1280 x 800 ( WXGA )
Widescreen Display
Yes
Features
BrightView

Video

Graphics Processor / Vendor
NVIDIA GeForce 7150M Shared video memory (UMA)
Total Available Graphics Memory
1071 MB

Audio

Audio output type
Sound card
Audio Output Features
Altec Lansing speakers
Audio Input
Microphone

Notebook Camera

Camera Type
Integrated

Multimedia Functionality

TV Tuner Type
None

Input Device(s)

Input device type
Keyboard, Touchpad, QuickPlay

Telecom

Modem
Fax / modem
Max transfer rate
56 Kbps

Networking

Networking
Network adapter
Networking / Wireless LAN Supported
Yes
Data link protocol
Ethernet, IEEE 802.11b, IEEE 802.11g, Fast Ethernet
Networking standards
IEEE 802.11b, IEEE 802.11g

Expansion / Connectivity

Expansion Slots Total (Free)
2 ( 0 ) x Memory - SO DIMM 200-pin, 1 ( 1 ) x ExpressCard/54
Interfaces
3 x Hi-Speed USB - 4 pin USB Type A, 2 x Headphones - Output - Mini-phone stereo 3.5 mm, 1 x Microphone - Input - Mini-phone 3.5 mm, 1 x Display / video - VGA - 15 pin HD D-Sub (HD-15), 1 x Display / video - S-video output, 1 x Modem - Phone line - RJ-11, 1 x Network - Ethernet 10Base-T/100Base-TX - RJ-45, 1 x Docking / port replicator, 1 x IEEE 1394 (FireWire) - 4 pin FireWire, 1 x Remote control - Infrared

Miscellaneous

Included Accessories
Remote control

Power

Power device form factor
External

Operating System / Software

OS Provided
Microsoft Windows Vista Home Premium 64-bit Edition


any help or advice that you can give me about the pros and cons of this system will be greatly appreciated! thanks!

---

### Post by Sam on 2008-10-16
Can you provide more info about your wifi adapter ?


For everything else it should work.

---

### Post by j_rob313 on 2008-10-16
network interface: Integrated 10/100BASE-T Ethernet LAN (RJ-45 connector)

and the network adapter is broadcom 802.11b/g WLAN

from what i've been reading it seems this model has some problems with wifi and video resolution.  have those problems been fixed or were they more of case by case situations?

also is there any specific site that might have a majority of the drivers or should i just look for them individually?  thanks again for all the help!

---

### Post by Sam on 2008-10-16
I found on [this page](http://www.ciao.com/HP_Pavilion_Dv2845se_Special_Edition__15538540) (emphasis mine):
> Good computer for those who do their work mostly on the internet or for doing bills, etc. Not good for gamers. Freezes during game play. Volume driver bad, so volume must be raised and lowered through windows and not on the actual hardware. This is also a common complaint on forums throughout the internet although HP customer service swears they've never heard of this. Gets warm, but not hot. Good on power, nicer design than many HPs. Holds a lot of data and works well. **Came with Vista, but it didn't run well on Vista, now running on Ubuntu and it works great. I suggest Ubuntu or another Linux based system with this and really any laptop that HP has released with Vista.**

> **j_rob313 said:**
> also is there any specific site that might have a majority of the drivers or should i just look for them individually? thanks again for all the help!
This should work "out of the box", however you may get issues with the wifi. According the above review it works (although it didn't mention wifi). For my experience I never had too much trouble with HP dvXXXX (once was broadcom 43xx (used [this method](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)) and once it was a 802.11b/g/n wlan which didn't work with hardy but was successful with intrepid).

---

### Post by j_rob313 on 2008-10-17
yeah i decided to go with a kubuntu/windows xp dual boot.  it seems like everythings fine now and most everything in kubuntu worked out of the box like you said. 

 i haven't looked too deeply into it to see if my wireless card is working since i've been more focused on learning how to install linux drivers in the first place.  

i've been reading and found an app called Gdebi that supposedly works something like Windows Install Wizard.  is this a good program to use and if not do you have any other options?

---

### Post by j_rob313 on 2008-10-17
i'm trying to install the broadcom driver right now, but its asking me to download firmware.  is this going to conflict with my xp firmware?  will i only be able to run the internet on one of the os?

---

### Post by Sam on 2008-10-17
> **j_rob313 said:**
> i've been reading and found an app called Gdebi that supposedly works something like Windows Install Wizard.  is this a good program to use and if not do you have any other options?

Gdebi is just a front-end for debian packages, the base packaging system for Ubuntu. You can install applications from "Synaptic Package Manager" or "Add/Remove..." or download .deb files which are installed to the system with Gdebi.

> **j_rob313 said:**
> i'm trying to install the broadcom driver right now, but its asking me to download firmware.  is this going to conflict with my xp firmware?  will i only be able to run the internet on one of the os?

No, one OS will not interfere with the other.

---

### Post by Statik on 2008-10-18
The latest ubuntu update had a new broadcom STA driver that 'fixed' my supposedly broken wifi on a DV2310CA.

Statik

---

### Post by m42h31 on 2009-07-25
i buy a new Hp compaq cq40-337tu with no OS. i'm gnome desktop user and want to try new experience with KDE desktop. i think to install kubuntu 9.04 on my laptop. all installation process running well, the desktop effect running on best performance.but, i found problem with altec lansing sound driver. i can't hear any sound.

any help or advice for altec lansing solution ?
thanks,

---

