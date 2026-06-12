---
title: "Desktop Hardware Compatibility List."
date: 2007-02-14
forum: Hardware
---

### Post by frodon on 2007-02-14
Welcome to the Hardware Compatibility List.

The purpose of this thread is for you, the user, to post what hardware/hardware combination works with Ubuntu for you. If you wish, you may post how the hardware works (configuration related), and the steps you took setting it up. These informations will help other users to choose new hardware and it will also help the UDSF archivers to update the Hardware Compatibility Guide.

Everyone is welcome to post here, as long as it is hardware related data. For help with hardware problems, please use the standard procedure of searching the forums, and starting your own thread for assistance if no answer is found.

**_Give detailed explanations when reporting compatible hardware._**

**Also Do not post any lspci outputs in this thread as they will be removed with out question.**

[B]Please Only List
1)Version Of Ubuntu 
2)Type Of Hardware
3)Hardware Maker
4)Hardware Model[/B]

[COLOR="Red"]***NOTE* This thread is exclusively for the listing of compatible hardware. Any idle chatter or unrelated posts will be moved/removed accordingly. *NOTE***[/COLOR]

Thank you.

**PS: the old compatibilty list thread can be found here and will remain closed** :
[http://ubuntuforums.org/showthread.php?t=183664](http://ubuntuforums.org/showthread.php?t=183664)

---

### Post by jkzubu on 2007-02-17
Welcome to the Hardware Compatibility List. ....

The purpose of this thread is for you, the user, to post what hardware/hardware combination works with Ubuntu for you. ...and it will also help the UDSF archivers to update the Hardware Compatibility Guide.


[COLOR=Red]***NOTE* This thread is exclusively for the listing of in_compatible_ hardware. Any idle chatter or unrelated posts will be moved/removed accordingly. *NOTE***[/COLOR]


Do you mean to state, "This thread is exclusively for the listing of COMPATIBLE hardware?"  -J

---

### Post by ChrisLilley on 2007-02-22
Ubuntu 6.10
Dell Precision M90 laptop workstation:
2.0 GHz Core 2 Duo T7200, 4Mb cache | 2Gb (2*1024) Samsung DDR2-667 5.0-5-5-13 | Seagate Momentus 7200.1 100GB 7200, 8MB cache | NVIDIA Quadro FX2500M, 512Mb, driving 1920x1200  LCD | Maxtor 3200 USB2 500GB 7200, 16MB cache | Sony DVD+/-RW DW-Q58A  |  Broadcom gigabit ethernet

The processor is not recognised, but runs, and is correctly shown as two cores.
The video card - the OpenGL version of the G71 core as used on 7900GTX - is not recognised, shown as an 'unknown device 029a', but runs at native resolution and full color depth. Adding the NVIDIA-supplied binary driver enables full OpenGL support which works well.

The Ricoh SD/MMC/MemoryStick/xD reader is partially recognised.

I have not tried the IEE1394 port or the smart card reader.
Sound works, burning DVD works.

---

### Post by lamadredelsapo on 2007-02-23
Ubuntu version: 6.06
Type Of Hardware: USB Bluetooth Dongle
Hardware Maker: MSI
Hardware Model: BToes 2.0 EDR

It works out of the box. I just pluged it in, installed gnome-bluetooth from the repos and followed this how-to:
[http://www.ubuntuforums.org/showthread.php?t=94713]("http://www.ubuntuforums.org/showthread.php?t=94713")

---

### Post by autocrosser on 2007-02-25
I just need to include this:

I checked for a replacement printer for my aging Epson Stylus Photo 820 (worked very well in Linux) & finally decided on a Brother HL-2070N Laser printer. 

To make a story short & sweet: After downloading two small files from Brother Support (both .debs), I just plugged in the unit & after printer setup--cleanly printed the test page & several jobs I needed to do-----all within 20 minutes of walking in the door with the unit. Brother's support was very clear & to the point. All-in-all, a very positive experence!!! 

I wrote the following to Brother's tech support:

I am just writing to thank you for excellent support for my new Brother HL-2070N Laser printer. i downloaded your two drivers & installed them--then setup the printer & printed a test page within 20 min of walking in the door with the new unit.

BRAVO!!!!
I had used a Epson Photo Stylus 820 & several HP products prior--none were as easy to setup & use as your unit!!!

Thank You for a job VERY well done.

Dean Loros
Performance by Design Ltd.



This is for hoping that this becomes the "norm" for equiptment suppliers!!!

---

### Post by bodcod on 2007-03-03
Ubuntu version 6.10
Motherboard : Gigabyte GA-K8N51PVMT-9
Processor : AMD 64 Athlon 3200+ socket 939
Ram :  Kingston PC3200 512Mb x2
HDD : Maxtor 6Y060l0 60GIG ATA
Ubuntu installed perfectly, everything working, ethernet,usb,and sound.

Nvidia 6150 on board gpu on first install ran with visa driver, NVIDIA-supplied binary driver installed and works perfectly native resolution of monitor recognised and Beryl 0.2.0 rc1 installed and works perfectly.

Have not tested the firewire port as yet but is recognized.

UPDATE: As above with Feisty 7.04. and & 7.10 Gutsy
Plus logitech quickcam connect   works out of the box, tested with kopote and amsn and works as should, Plugged it in to usb and came  right up in both IM clients no problem. Have not tested sound with webcam as yet.


Bodcod

---

### Post by bodcod on 2007-03-03
[PHP][/PHP]Ubuntu version 6.10
Motherboard : Gigabyte GA-K8N51PVMT-9
Processor : AMD 64 Athlon 3200+
Ram :  Kingston PC3200 512Mb x2

Ubuntu installed perfectly, sound working, usb working, 

Nvidia 6150 on board gpu on first install ran with visa driver, NVIDIA-supplied binary driver installed and works perfectly native resolution of monitor recognised and Beryl 0.2.0 rc1 installed and works perfectly.

Have not tested the firewier port as yet but is recognised.

THIS IS A DUPLICATE POST, COULD A MOD PLEASE DELETE, THANKS

Bodcod.

---

### Post by firedrow on 2007-03-08
Mini-ITX System

OS: Edgy Eft
Motherboard: VIA EPIA MII-12000 Mini-ITX
Processor: VIA C3 1.2GHz
RAM: pqi POWER series DDR266 1GB
HDD: Toshiba 40GB 2.5"
PCMCIA: Zoom Bluetooth Adapter
PCMCIA: Linksys WPC54G 802.11b/g

Linksys WPC54G PCMCIA card, it is recognized, but I haven't tested it yet.


Laptop

OS: Edgy Eft
Model: Toshiba Satellite P15-S479
Processor: Intel Pentium 4 HT 2.8GHz
RAM: 1GB
HDD: Hitachi 100GB 2.5"
DVD: NEC DVD+-RW DL Burner
Graphic: nVidia Go5200
Net: Onboard NIC 10/100 and Onboard Atheros 802.11a/b/g

Texas Instruments onboard SD card reader doesn't work.  I will get the info and put it up on the Incompatible board.

---

### Post by Skefflock on 2007-03-09
Laptop

Sony Vaio VGN-FS840/W (PCG-7G2L)
OS:Edgy
Processor: Intel Pentium M 1.7Ghz
RAM: 512 MB (DDR2 SDRAM) *2
HDD: 100 GB Ultra ATA, 4200 RPM
Chipset: Intel 915GM
Graphic: Intel Graphics Media Accelerator (GMA) 900
Net: Integrated 10/100/1000 Network Card • Integrated Wireless LAN
+
1 x Type I/II PC Card Slot, 1 x Memory Stick Card Slot, Docking Station/Port Replicator, 1 x Memory Stick PRO, 1 x Memory Stick DUO

Everything works fine, but card-reader. Also i've spend 30 minutes on dial-up modem installation. It does work with freeware Connexant driver. Guess they are all the same on all Sony laptops. Media buttons don't work as well, but i didn't even try to install whether card-reader or media controls. Probably it has an easy solution.

---

### Post by jrcanedo on 2007-03-10
OS: Ubuntu 6.10
Processor: AMD Sempron 64 3000+ Socket AM2
Motherboard:  Redfox K8M800-AM2,Audio,Video,Lan,Socket AM2, SATA, IDE,DDR2
[INDENT][INDENT]VIA Chipsets[/INDENT][/INDENT]
Memory: 512MB DDR2 Apacer
HDD: 80GB SATA Seagate
CD-Rom: Lite-On CD-ROM Drive

Findings:
[LIST]
[*]All systems are functioning well, that means .....audio, video, lan, USBs, CD-ROM, HDD are detected. Redfox or Biostar mainboard is working well with Ubuntu 6.10. 
[*]Ubuntu 6.10 is operating smoothly with the set-up above, however, it is advisable to use 1GB DDR2 memory for better performance.
[/LIST]
 
********************************************************************

OS: Ubuntu 6.10
Processor: AMD Athlon 64 X2 Dual Core 5000+ (2.6 Ghz) Socket AM2
Motherboard:  Redfox GEForce 6100-AM2,Audio,Video,Lan,Socket Am2, SATA, IDE,DDR2
[INDENT][INDENT]nVidia Chipsets[/INDENT][/INDENT]
Memory: 1GB DDR2 Apacer
HDD: 120GB SATA Seagate
CD-Rom: Lite-On DVD Drive 

Findings:
[LIST]
[*]All systems are functioning well.....the set-up above are design for heavy graphics and gaming. I used this set-up right now for graphics and web development, e-commerce and e-learning development using LAMP set-up and most importantly watching DVD Movies or listening music ....while writing documents and codes.
[/LIST]

---

### Post by stig on 2007-03-20
Two Brother HL2030 laser printers (monochrome) using Ubuntu 6.06 Dapper, each on a 2.8GHz PC.

I bought one printer about a year ago for the first PC and found it so easy to instal and it worked so well that I have bought the same model printer for a second PC. The HL2030 is 16 pages per minute, 8MB memory, 2400 x 600 dpi and connects via USB 2 cable.

I have just bought the second one from Amazon UK for £60.85 plus VAT (and a USB cable at £2.55 plus VAT).  [Make sure you are buying direct from Amazon and you can use "Supersaver" to get free delivery in the UK.]

I downloaded drivers from the Brother Linux printer driver pages. Instal the LPR driver first from:
[http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)
The method is here:
[http://solutions.brother.com/linux/sol/printer/linux/lpr_install.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_install.html)

Then the CUPS driver from:
[http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html)
The method is here:
[http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install3.html](http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install3.html)

Check in Systems | Administration | Printing to make sure the printer is shown.

Connect the printer to the power and switch on. Connect the USB cable to the PC, then to the printer. Press the "Go" button on the printer to print a test page

Happy printing! :)

---

### Post by Austrian_Prototype on 2007-03-23
ubuntu 6.10 - 2.6.17-11-386
USB-HSDPA Modem
Huawei
E220

Works fine needs to be plugged in twice

---

### Post by todir on 2007-03-31
Ubuntu version: Kubuntu 6.10
Type Of Hardware: Laptop
Hardware Maker: Benq
Hardware Model: Joybook R53 EG

Intel 915PM
Celeron M 380 1.6Ghz
ATI X600 128MB VRAM on PCIE
RAM 512MB  DDR2
HDD 60GB Hitachi
Wireless Atheros AR5005G
DVD Philips DVD+-RW SDVS8441
Card  reader Texas Instruments PCIxx21
Intel HD audio

- Wireless adapter Atheros needs Madwifi driver from [http://madwifi.org/](http://madwifi.org/)
- Motorolla SM56 modem is not working(Hopeless)
- ATI X600 card works better with the open source driver than with the binary driver from ati.com. The binary driver is causing random lockups (8.28.x to 8.34.8 tested)
- Card reader works with SD cards (1 GB tested). Some additional steps needed [http://www.ubuntuforums.org/showpost.php?p=1614392&postcount=1](http://www.ubuntuforums.org/showpost.php?p=1614392&postcount=1)
- Fn+F1+F2.... keys are working
- DVD  is OK (DL burn not tested)
- Audio is OK
- Synaptics touch pad works great with KSynaptics

This laptop has broken DSDT, although no problem encountered with Edgy(I had a lot of problems with SUSE). Fixed DSDT is avaliable on [http://acpi.sourceforge.net/](http://acpi.sourceforge.net/) .

---

### Post by mahiyar on 2007-04-02
**Processor **-- Intel Pentium 2.8 OK :Hyperthreading recognized and all
**MOBo** -- Intel 865 GBF :OK 
**RAM **-- Transcend DDR 512 x 2 :OK
**Video card** -- AGP Nvidia 5200 FX : Started with "nv" drivers, now have nvidia glx driver, beryl works.
**CDRW -- **LG 52x24x52: Can record R/RW.
**Printer -- **HP Deskjet 5438/5440. Works, took some time to install HP panel, however much more controll desired.
**Scanner -- **HP Scanjet 2400: Does not work, no drivers provided.
**Sound Card -- **Built in, can record from line in, mic.

---

### Post by pappy on 2007-04-03
The configuration of my PC

OS: Kubuntu 6.10
CPU:Athlon XP 2800+
MB: Abit Nvidia 2 chipset
RAM: 1.5GB Apacer
VGA: Albatron Geforce 7600 GS256MB
Scanner; HP ScanJet 4P
SoundCard: Build in 
DVD+-RW: NEC x52x16x24
HDD: 2x Western Digital SATA 200GB 
SCSI: SCSI card Initio for scanner
Everything works fine. The scanner though MUST be turned on during boot otherwise the OS doesn't see it. The same happened in Windows 2000/XP also so it's common practise for SCSI devices

---

### Post by haemphyst on 2007-04-04
I couldn't actually FIND a database, but here, so far, in all it's Ubuntu/Linux nooby glory is what I have:

Averatec 5428HX laptop.  Hardware complement is:
AMD Mobile64 2800+
1GB RAM
100G 5400RPM Seagate HD
VIA AC97 integrated audio
RhineII integrated 10/100 NIC
RaLink RT2500 802.11g wireless card
Keyboard inerface works perfectly, i.e. volume, mute, contrast, etc...
I don't know what video card is in it, but it seems to work well, also.

Here are the distros and experiences I have tried on this machine.

Feisty.  DVD Image from internet, via BitTorrent, all hardware was recognized, and all seemed to run perfectly, except the wireless.  It was seen, and it could see the router, but it would never acquire an address.  If I statically assigned an address, it still wouldn't go anywhere, network-connectivity-wise. It would even see the Cox DNS servers on the other side of the cablemodem, but still no love.  I was never able to figure that out.  Cut the losses, and went back a step to:

Edgy.  Oh, JOY!  Every device, nailed.  Wireless works perfectly, after about 7 seconds of massaging.  The massaging involves adding the name of your WAP to the network card settings.  Happy, happy, joy, joy.  I even recommended the release to my buddy, who D/L'd the CD image...  He is as in love with it as he can express in words!  I'll be providing him with a DVD image as soon as I see him in two weeks.  Can anybody tell me the difference (besides the SIZE, thanks...) between a CD image and a DVD image?

---

### Post by skip27 on 2007-04-08
Compaq R3120US notebook computer.

[LIST]
[*]AMD Athlon(tm) XP-M 3000+ Processor (based on AMD64 K8 core)
[*]512MB DDR SDRAM (PC2700) -- I added another 1GB of Kingston memory, no problems.
[*]15.4" WXGA Display (up to 1280x800)
[*]nVidia GeForce4 420 Go, 32M dedicated
[*]Hitachi IC25N 60GB hard drive (not tested)
[*]Hitachi-LG GCC-4241N CD-ROM (24X/10X/24X CD, 8X DVD-ROM)
[*]nVidia nForce3 AC97 audio interface
[*]RealTek RTL-8139 Ethernet controller (chip type RTL-8101)
[*]Broadcom BCM4306 802.11b/g WiFi controller (rev. 03)
[*]Texas Instruments PCI1620 CardBus controller
[*]nVidia nForce3 winmodem (not tested)
[/LIST]

Everything works out-of-the-box with the notable exception of the BCM4306 wifi controller. Solutions include:

1) ndiswrapper, confirmed to work. Use the sp29361.exe driver. Search for it on the ndiswrapper compatibility hardware wiki ([http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)). Cabextract the files out and use bcmlw5.inf & bcmlw5.sys.
2) bcm43xx kernel driver /w firmware. Use the Ubuntu wiki ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)) for assistance.

The Ubuntu hardware wiki suggests installing with "linux noapic," but I had no problems installing normally. Use your discretion.

Using 6.10 Edgy Eft.

---

### Post by MKenney on 2007-04-20
Processor: 3000+ AMD 939 
RAM: A-DATA 3200
GPU: ATi X850XT -- This is the problem.
Harddrive: Seagate Barracuda 250gb, and a Western Digital Raptor 32gb.
Sound: Creative X-Fi
Motherboard: TUL 939 Motherboard ATi chipset.


The installation CD has problems with my GPU.

---

### Post by ali4949 on 2007-04-21
Hardware: IBM Thinkpad T30
RAM: 768 MB
Ubuntu Version: EDGY EFT

No problems with any services. Everything works out of the box. Netgear PCMCIA wireless card does not work but that due the marvell chip set which is made in TIAWAN, the china made chip set is reported to work.
COMPIZ and BERYL both perform decently on the 16MB video card (ATI Radeon 7500). sound and USB support out of the box with no tweaks.
suspend and hibernate also work without any problems. IBM hot keys work after installing thinkpad packages from the ubuntu repositeries.

Will post results of the FEISTY install soon

---

### Post by roar on 2007-04-21
I have the Dell Inspiron 6000. I don`t know the names of all the specific hardware. Everything seems to work out of the box with Feisty, what a great OS, it` s just amazing

---

### Post by Hex_Mandos on 2007-04-21
My desktop is a bit old (3.5 years), but works perfectly with the following hw: 

[LIST]
[*]AMD Athlon 2400+
[*]MB: ASUS A7V8X-X 
[*]NVidia GeForce Mx 5200
[*]Maxtor 120 MB HD
[*]LG DVDRW (I can't remember the speeds...)
[/LIST]

---

### Post by NullHead on 2007-04-22
Ubuntu Feisty  7.04 x64
MSI k8-neo4
2x PQI 512mb ram = 1gm
Amd Athalon 64 4000 
Maxtor 60gb= PATA    |   Sedgate 160gb=SATA
Nvidia e-GeForce 7600 GTS
U.S Robotics 5417 (or broadcom 4318 ) pci with ndiswrapper and bcmwl5.inf and BCMWL564.sys
Realtek ac97
Viewsonic P220f Moniter

---

### Post by spikeyone on 2007-04-22
Feisty 7.04 (and previously Edgy)

Dell Dimension Desktop 8200

Pentium 4 2.0 Ghz
256MB RDRAM
Soundblaster Live!
Benq 1620 DVD-RW
nVidia Gefore 4 MX420

Everything's perfect!

---

### Post by Mopana on 2007-04-23
Ubuntu 7.04 and Edgy

Thinkpad T40p
1.6 GHz
64 MB ATI Mobility Fire GL 9000
Atherols Wireless Network adapter (Ubuntu says it's not supported, but it works without configuration)

---

### Post by jdietz on 2007-04-24
6.10 Edgy Eft
Wireless NIC
Zonet
ZEW1602
Notes: Works with ndiswrapper.  No native linux driver.  Also works with wpa_supplicant.
Works with ndiswrapper in 7.04 Feisty Fawn.  Does not work with wpa_supplicant in 7.04 Feisty Fawn.

---

### Post by kevinsun on 2007-04-26
Hi, I have upgraded the latest Feisty 7.01 from Edgy in a Dell Optiplex GX150 with PIII and 256 MB ram...

It's very old PC but Ubuntu works pretty good.

[B]Please Only List
1) Feisty
2) PIII, 256 RAM
3) Dell 
4) GX150

---

### Post by bonzini on 2007-04-27
Laptop: Toshiba A70
Model number: PSA70C RX100E
OS: Ubuntu 7.04 (has run 6.10, 6.06, 5.10)
CPU: Pentium® 4 supporting Hyper-Threading 3.20 GHz
Video: ATI 9100 IGP RS300M, 64MB-128MB shared memory
Screen: 15.4 inch wide (aka short) screen, 1280X800
Sound: ATI IXP AC97 / Realtek ACL202
Modem: ATI IXP AC97 Modem
Ethernet: Realtek RTL8101L
Wireless: Atheros AR5212 802.11abg
Firewire: Texas Instruments TSB43AB21
Cardbus: ENE Technology CB-710/2/4
RAM: 1.0Gb DDR
DVD/CD: Matsushita DVD-RAM UJ-820S, ATAPI CD/DVD-ROM 
HDD: Samsung HM120JC ATA 5400rpm (replaced original Toshiba)
Touchpad: AlpsPS/2 GlidePoint

I have not tested / used:
  - the Firewire or Cardbus capabilities;
  - suspend/resume capabilities;
  - the modem.

Both sound and wireless worked fine right from the install with 6.06, 6.10, and 7.04.  I recall having some difficulties with wireless in 5.10, but can't recall what they were.  Also, in 6.10 it was difficult to connect to a new wireless service.

The graphics card is not well-supported by the proprietary ATI drivers, so I use the Radeon free driver.  This seems reasonably fast - glxgears gives ~ 660 fps with no tuning.  Compiz works fine, except that there seems to be a known bug involving the interaction between Java 5 and Compiz - nothing shows up in Java windows with the desktop effects enabled.  This is not a problem with the desktop effects disabled.

I had a huge problem, since 6.10, with the window system hanging, reported as bug #98999.  In Feisty I noted a boot message about "8254 timer not connected", which seems to have been noted before, reported it as well.  After inserting "noapic" in # defoptions in /boot/grub/menu.lst the hanging problem seems to be gone.

For my purposes, now that the hanging thing seems to be gone :) I really enjoy this laptop again - it was great in Breezy and Dapper too.  The monitor is very bright, though 1280 X 800 is a bit too low-resolution for my taste, and the keyboard has a pleasant amount of feedback.  I really disklike the touchpad, and use a nice USB optical mouse designed / imported by Chameleon.  In terms of processing, the machine is very fast.

---

### Post by calgarystevens on 2007-04-28
Feisty 7.04
Toshiba A100 Laptop
Celeron M1.46 
ATI Radeon Xpress 200M
Realtek AC97 sound
Atheros AR5211 wireless
Epson CX3810 All-in-one

Sound was down on startup so I did this:
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop ubuntu-minimal
sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=auto
sudo gedit /etc/modprobe.d/alsa-base
and add "options snd-hda-intel probe_mask=8 model=auto" to the end of the file

Network Manager worked great, my Atheros wireless worked out of the gate with the ath0 driver Feisty installed. To get wep working I had to check my router settings to 'Open Key' not managed or otherwise.

Video is an ATI Radeon Xpress 200M and worked at 1280 on startup and after checking the box in the 'Restricted Drivers' box it was off to the 3d races, very nice.

Printer is an Epson CX3810 All-in-one. The built-in driver prints beautifully, but scanning was a challenge. So, I found [http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html) for scanner drivers (printers too apparently). And did this to make it work:
install sane libsane-backends then uninstall libsane-backends (weird yes, need pieces, but it then had trouble overwriting the backend driver, and this worked) *shrug*
install iscan *.deb
make menu item for iscan
I love that scanner driver, it's beautiful, simple, and makes nice scans.

The Big One! Suspend-to-ram with the ATI fglrx drivers (your mileage may vary, I doubt I can help more, but here's how I did it)
sudo gedit /etc/acpi/sleep.sh
On second line put: sudo chvt 1
sudo gedit /etc/acpi/lid.sh
On second line put: sudo chvt 1
sudo gedit /etc/acpi/resume.sh
On last line put: sudo chvt 7
sudo gedit /etc/default/acpi-support
Edit lines thusly:
MODULES_WHITELIST="fglrx"
SAVE_VBE_STATE=false
POST_VIDEO=false
DOUBLE_CONSOLE_SWITCH=true

OK, I now have suspend working with AC plugged in, plus closing the lid works for suspend. But, on battery power it gets stuck going down to suspend, and comes to the locked screen and will not take keyboard input. But it does work!!

---

### Post by necromancer_final on 2007-04-28
Feisty 7.04
Toshiba A135
Intel Core Duo 1.7 GHz
Intel 945 graphic Card
1 GB RAM

The sound was down, I followed the step-by-step guide.
It worked after this:
sudo modprobe snd-hda-intel
sudo gedit /etc/modprobe.d/alsa-base, added "hda-intel" at the end of the file.

The wired network worked find. I have a static IP and I used a proxy server.
Didn't test the WLAN yet.
Didn't test the modem.

The suspend and hibernate options are working fine too.
3D desktop working great :)

That's all I tested till now, I'm new a Linux user by the way.

---

### Post by GeneWine on 2007-05-04
Ubuntu: Feisty
Hardware: Laptop
Model: Inspiron 9400 (Centrino Duo - T2300, 1.66 GHz)
Manufacturer: Dell

Main details: SATA disk, nVidia GeForce 7800 GO, Intel HDA STAC 92xx, Ricoh SD card reader, Intel/PRO Wireless 3945ABG.

Works like a charm.

---

### Post by th3rmite on 2007-05-16
Ubuntu 7.04

Toshiba Satellite M35X-S114
Haven't tried modem
Haven't tried burning cd's
Everything else works, kudos to ubuntu team

---

### Post by IntuitiveNipple on 2007-05-22
**[COLOR="RoyalBlue"][URL="http://vaio.sony.co.uk/view/ShowProduct.action?product=VGN-FE41Z&site=voe_en_GB_cons&category=VN+FE+Series"]Sony Vaio VGN-FE41Z & Feisty/Gutsy/Hardy/Intrepid[/COLOR]**
[IMG]http://sp.sony-europe.com/media/18/8618[/IMG][/URL]

**Updated for Gutsy, Hardy, and Intrepid**

I was pleased to find that Feisty supports all the hardware on this laptop without any hassles. There are issues with suspend and hibernate. Suspend/Resume will mostly work but sometimes isn't reliable. These can usually be traced back to a known bug with the uvcvideo driver. The solution is to have it unloaded before suspend. The way to so that is to add the module name to the MODULES="" setting in /etc/default/acpi-support, e.g 
```

MODULES="iwl3945 uvcvideo r5u870"

```

If using Compiz/Desktop Effects the Compiz option 'sync to vblank' should be disabled otherwise the Gnome desktop won't be displayed on resume. A bug in Feisty's 2.6.20 kernel will cause the HDA audio to loop and crackle after resume. This is caused by an overwrite of the HDA PCI register TCSEL when the 2nd core of the CPU is started. I have published a patch to fix this against the bug [snd-hda-intel: distorted sound after resume, until the module is reloaded](https://bugs.launchpad.net/ubuntu/+bug/100114). I've found that more than one resume causes the screensaver to loose keyboard input, and any attempt to restart gdm leads to an Nvidia driver failure that requires a restart to fix. Gutsy, Hardy and Intrepid seem fine.

The alternative [COLOR="Blue"]**Fn-blue**[/COLOR] function keys are not currently supported by the *sonypi* module. It appears they are managed by the newer Sony Notebook Control ACPI device via the Embedded Controller (EC) hardware. This is being actively worked on - see the [Calling All Vaio Owners thread]("http://ubuntuforums.org/showthread.php?t=465491") for how you can help the new **sony-laptop** kernel driver support all the custom hardware options on Vaios: Programmable S1 S2 keys, Fn keys, radio power for WiFi and Bluetooth, power for LAN, Audio, Camera and CD, Screen brightness, contrast, and switching to external displays.

**Vaio Gnome panel applet**. I am writing an easy-to-use control applet that will allow users to easily configure all functions of the Sony Notebook Control, Sony PI, and EC. It is a multi-tabbed applet with controls grouped logically. It will ensure your preferences are saved and applied at startup. 

The external ExpressCard/34 5-in-1 Flash card reader adapter works with SD cards. I've not had chance to test it with MMC, xD, or MemoryStick Pro. With SD cards there is sometimes a problem with older cards that are physically just *slightly* thicker than usual. This prevents the contacts from touching the pins in the adapter unless you put it under physical pressure which is not a workable solution, so ensure you're using *thin* cards.

The internal Texas Instruments 5-in-1 Flash card chip-set that is connected to the internal MemoryStick 2 slot is also recognised. However, the kernel modules to support MemoryStick or xD cards on the TI chip-set are [in the early stages](http://openfacts.berlios.de/index-en.phtml?title=TI_FlashMedia_xx12/xx21_driver) and not available unless you build them yourself. As on Intrepid the tifm and memstick modules will be available as they are in the mainline kernel. I'm working on an Ubuntu DKMS package to backport them to Hardy LTS.

The Nvidia proprietary drivers work fine driving both the DFT, as well as external VGA and S-Video displays. TwinView with the desktop spanning both displays works fine. With the NVIDIA X Server Settings utility (Applications -> System Tools) choose **X Server Display configuration** and then press **Detect Displays**. When the display appears in the Layout window choose it and then press **Configure...** and choose **TwinView**. After unplugging a display press **Detect Displays** again to return to a single screen.

I've tested the VGN-FE41Z with 32-bit and 64-bit Feisty/Gutsy/Hardy/Intrepid Desktop and found no problems due to Ubuntu.

Originally I kept the existing disk partitions (sda1=Sony Vista Recovery, sda2=Vista Home Premium) and added swap (2GB) partition in sda3, sda4 is an extended partition for sda5=/boot (256MB), sda6=/ (32-bit 9GB), sda7=/ (64-bit 9GB), sda8=/home. Now, I've removed Sony Vista Recovery, moved and shrunk Vista Home Premium, and put all but /boot in an encrypted LVM volume that requires a USB key to unlock (no password is assigned).

[INDENT]**Note:** The easy way to shrink the Vista partition is to use Vista itself. Unlike XP, Vista can shrink its own partitions! Go to Control Panel, System Administration, Disk Management, select the Vista partition, right-click, and choose Shrink. I made it 27GB.
[/INDENT]
The only devices not supported immediately are the Intel High Definition Audio HSF V92 SoftModem and the built-in Motion Eye video camera. The camera has a Ricoh chip-set and Alex Hixon now maintains the r5u870 driver (originally by Sam Revitch). Project details can be found at [ R5U870 driver]("http://wiki.mediati.org/R5u870") and Ubuntu packages for Gutsy/Hardy/Intrepid are [url="https://launchpad.net/~intuitivenipple/+archive"]available from my PPA[url].

Until you install the drivers you'd not notice the modem in Hardware Information at all. Linuxant have created [proprietary drivers for the Intel HDA HSF V92 software modem](http://www.linuxant.com/drivers/hsf/index.php). The driver is available as a $19.99 fully capable driver or a free 14,400 baud speed-limited version. The installation process was smooth (I used the automatic Internet installation method). The big drawback is it conflicts badly with the Intel HDA sound driver and generates a lot of spurious messages to the log files which show it is not entirely production-quality. I'd avoid it unless it is essential.

I have created a Gnome panel applet to control the Nvidia display brightness because it isn't supported by the default tools. You can [get SmartDimmer here]("http://ubuntuforums.org/showthread.php?t=451781"). Again, packages for Feisty/Gutsy/Hardy/Intrepid are [url="https://launchpad.net/~intuitivenipple/+archive"]available from my PPA[url].

The FE41Z has the Intel Core 2 Duo T7200, a CPU that supports VMX (Virtualisation). Unfortunately Sony do not provide a BIOS option to enable VMX and the BIOS locks the MSR register 0x3A, preventing other software from doing so. I'm hoping Sony will eventually provide the option but I'm also working on a BIOS hack so that VMX is available - it was a prime reason why I chose this model!

I finally managed to manually re-program the NV-RAM settings using a DOS utility called symcmos, once I'd identified which tokens to alter. Unfortunately these token locations change in different BIOS versions so there is no universal way to enable VMX across models and BIOSes. [Details of my research]("http://tjworld.net/wiki/Sony/Vaio/FE41Z/HackingBiosNvram").

During my snc module investigations I **discovered an ACPI battery bug** in the Differentiated System Description Table (DSDT) **in the BIOSes of every Sony Vaio** model we've seen so far. You can [read about it here](http://ubuntuforums.org/showpost.php?p=2855943&postcount=55) and find a fix for it in the thread [ ACPI: battery-technology reported as non-rechargeable](http://ubuntuforums.org/showthread.php?t=475801).

---

### Post by p1977p on 2007-05-30
Compaq Presario laptop with
Processor: AMD Turion 64 bit, 2.0 GHz, 512 KB cache
Nvidia GeForce 6150 on board graphics card
512 MB RAM
DVD writer
80 GB SATA HDD
integrated SD/MMC card reader
integrated WiFi, LAN 100Mbps

OS: Xubuntu Feisty fawn 7.04 64 bit AMD dual boot with Windows XP

I had problems installing the standard Ubuntu 64 bit ( the installer seemed to hang while partitioning the drives), but the Xubuntu installer worked flawlessly. it detects most of my harware automatically, even the card reader! However there are some issues:

1. The laptop function keys do not work. I guess other laptop users face a similar problem.. it's been reported

2. laptop screen brightness cannot be adjusted. smartdimmer doesn't work... gives "init_nvclock() failed!" message.

3. hibernate is quite slow .... as compared to windows XP. switch user tends to hang sometimes

4.nvidia driver doesn't get installed; i still have to use the Nv driver (tried apt-get)

 Otherwise, it's been a welcome change from XP, much faster! (except for the internet speed)

---

### Post by Desd on 2007-05-31
The machine worked like a charm from first install, but had to put some work in getting it fine tuned; see notes.

Asus F3M-AP034A-A

Mobile AMD Sempron 3400+
Speed 2000 MHz
Intern mem 2048 MB (the full mounty to try to speed up Vista... unsuccesfully)

TFT 15,4&#8221; Res 1280 x 800
Video nVidia GeForce Go6100 (onboard) (had to work on this one a bit to get the right res.)
Internal webcam	DOES NOT WORK YET, but put no serious effort in it
Sound onboard
HD 80 GB, 5400 rpm DVD±RW DL, cardreader
ethernet, USB 2.0, Wireless LAN
FireWire 400 (IEEE 1394), modem, TV-out, DID NOT TEST THIS YET, but seems ok to me.
6 cells Li-Ion

Dual boot Ubuntu 7.04 // Vista (paid for it, so it is going to be there till my wallet no longer aches :p)

Works fine with:
Samsung ML3050ND network and usb printer (work both)
KPN / Siemens Experiabox modem / router
Canon Pixma IP2200 usb printer

---

### Post by djorzgul on 2007-06-03
Few things are to be edited when I finish with them, but right ''out of the box'' situation is like this:

Ubuntu 7.04 Feisty Fawn
              +
Sony VAIO VGN A317M

specs:
[COLOR="Green"]**working right after the installation (out of the box):**[/COLOR]
Mobile Intel® Pentium® M Processor 740;
2gb DDR2 SDRAM (PC2-3200-DDR2 400);
80 GB (S-ATA 5400);
Double layer DVD±RW Drive;
X-black LCD 17" WXGA+ (1440x900);
[COLOR="Orange"]ATI MOBILITYTM RADEON® X600 PCI Express with 128 MB VRAM[/COLOR] resolution is right, even working in blender is by default ok, openGL is not ok, but that is general problem with ati/linux combination, and tweaking is necessary ;
Intel® High Definition Audio compatible, 3D audio (Direct Sound 3D support);
Network: Ethernet 10 BASE-T/100 BASE-TX/1000 BASE-T;
WIRELESS LAN:IEEE 802.11b/g standard;
BLUETOOTH;
BATTERY/ Lithium-Ion;
Wireless mouse;
Firewire;
USB;
Audio/Video in and outs;


INTERFACES: 
[COLOR="Green"]working: dvd tray button, mute button, power off;[/COLOR]
[COLOR="Red"]not working: +-volume, +-brightness, auto brightness, zoom, special (useless) button;[/COLOR]

**[COLOR="RoyalBlue"]NOT TESTED:[/COLOR]**
Memory StickTM slot (Memory StickTM Pro, Memory StickTM Duo}, I don't have memory stick with me right now so I don't know if it works without problems, however , little light is on and it looks like it is recognized by system;
DOCKING STATION: I do not have one;
Modem: Built-in V.92/V.90 (56 kbps) data/fax modem: I didn't use it for a looong time;
PC CARD SLOTS (PCMCIA): I don't have a card to test it right now.

---

### Post by Tourmaline on 2007-06-13
version of Ubuntu : Kubuntu 6.10

computer type : Desktop Computer

hardware : 

Asus P5PL2-SE mainboard
Intel Core2Duo E4300
Galaxy 7900GS 256 MB video card
Seagate 320 GB SataII hard disk
Seagate 250 GB IDE hard disk
Kingston 2x1 GB DDR2 667
Linksys Wifi Adapter WMP54G
Asus DRW 1612-BL dvd burner
Samsung 226BW monitor

Everything worked out of the box except for the HDA Intel AD1986A sound chip. Refer to the following thread to get it working : [http://ubuntuforums.org/showthread.php?t=231032](http://ubuntuforums.org/showthread.php?t=231032) (MCMC).  After this fix all audio connections are working perfectly. 

Of course the wifi adapter had to be installed using the Broadcom 43xx firmware. [http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm+43xx](http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm+43xx)

NVidia 100.14.09 driver is fully functional with 3D acceleration and Beryl 0.2.0 running in Samsung 226BW native resolution (1680x1050).

---

### Post by Necrome on 2007-06-16
Hi there,

I have not been able to find any info if Feisty works fine with Sony Vaio VGN-TX3XP. Does anone know? The graphics card (Mobile intel 945GM Express Chipset Family) gave me a lot of problems with Fedora Core 6. 

Thanks in advance.. (Sorry if this is the wrong place to post this question)

---

### Post by amirms on 2007-06-17
Ubuntu 6.10
ASUS A9Rp Laptop
1.8 Ghz Celeron,ATI Radeon Xpress 200M,ZyDAS 1211B Wireless,Realtek HDA Audio

Every thing is detected but WIRELSS,Audio(Built in speakers are OK but the 3.5 mm jack has weak sound),Modem

I could solve audio and wireless problems:D, users follow the instructions bellow:

1-Download and install kernel sources, I copied it to /usr/src/

2-Get this patch for audio and decompress to your kernel source root folder, mine is:/usr/src/linux-2.6.21-5
   [ftp://ftp.alsa-project.org/pub/kernel-patches/alsa-git-2007-05-03.patch.gz](ftp://ftp.alsa-project.org/pub/kernel-patches/alsa-git-2007-05-03.patch.gz)
   so, you should have alsa-git-2007-05-03.patch in your linux kernel source folder

3-Open console and run:
   patch -p1 <alsa-git-2007-05-03.patch
   OK, Now kernel is patched for audio, we proceed to wireless.

4-Say your kernel source folder is like mine, /usr/src/linux-2.6.21-5, open this file:
/usr/src/linux-2.6.21-5/drivers/net/wireless/zd_usb.c and add this line to the ZD1211-B section:
  { USB_DEVICE(0x0b05, 0x171b), .driver_info = DEVICE_ZD1211B }, 
  Save the file.

5-Now you should download this file and decompress the content into /lib/firmware/zd1211(if this directory does not exist, create it)
  [http://sourceforge.net/project/showfiles.php?group_id=129083](http://sourceforge.net/project/showfiles.php?group_id=129083)

OK,we are almost done!Now, you should compile the new kernel and install it.You can open /usr/src/linux-2.6.21-5/README.txt to find out how to do so. what I did:

cd /usr/src/linux-2.6.21-5
Make oldconfig
Make
Make modules_install
Make install

If using GRUB, you are done!Reboot and enjoy:)
If using LILO, reinstall LILO and reboot and enjoy!

The above procedures should work with other versions of ubuntu as well as other distributions. One of my friends has done it in OpenSUSE 10.2 without any problem.

---

### Post by tiepi on 2007-06-26
> **IntuitiveNipple said:**
> 

**[COLOR="Red"]Update (29th May 2007):[/COLOR]**
[INDENT]I've created a custom BIOS that enables VMX. It turns out that module BIOSCODE6 already includes the instruction to set the VMX bit, but that it is jumped-over because a check of the user's Setup configuration says VMX is disabled (the user never gets the chance to enable it!). For this custom BIOS I simply over-write the jump instruction with 2 no-op (NOP) op-codes so the instruction that sets bit 2 of MSR 0x3A is executed.
Unfortunately, the tool from Phoenix that allows the BIOS to have its modules extracted and re-catenated, BIOS Editor Pro v2.2, isn't totally reliable and can corrupt the resulting BIOS image such that when it is programmed by Phoenix WinPhlash the PC becomes a brick.



can u share your custom BIOS with other sony viao user?

---

### Post by praxis22 on 2007-06-27
Feisty 7.04 64bit
Core 2 Du0 E6700 2.6Ghz, (overclocked slightly to about 2.71Ghz to see if it could be done)
ASRock 775i65G (rev 2.0) Motherboard. AMI BIOS, (Integrated Intel Extreme Graphics 2)
1Gb OCZ Voltage Extreme DDR (PC400) RAM
ATI X800XT (AGP) Graphics card
Cmedia 9761A (on-board) 5.1 sound
LITE-ON DVDRW SHW 16H5S (DVD writer)
2x Seagate ST3320620A Barracuda 7200.10 (320GB Ultra ATA) hard drives.

I love ASRock boards, cheap, and rock solid. No problems at all expect Grub hates ATI cards, add "nosplash" to you boot line, to get around the splash freeze problem. However the 32bit 7.04 boot CD has no problems with the splash image.

---

### Post by AllenGG on 2007-07-09
Dell Latitude CPx    (old)  laptop
P3, 20gig HDD, D-Link wireless DWL G630 card

Dual Boot !!!!   Feisty 7.04  and Windows 2000 Pro easy setup. wireless card was set up using direct connect eth1 then switched.
Even Skype !
a walk in the park !8) did it for a friend, added Ubuntu stickers !

---

### Post by mrazster on 2007-07-11
Xubuntu 7.04  *(did a CLI install and then added all packages manually with apt/synaptic)*

Using it as Desktop Computer,,,gaming and multimedia.

Asus P5N-E SLI
Intel QX6700
2x2gb A-Data PC2 5300
MSI 7900GTO 512mb
Soundblaster Live 5.1
1x36gb WD Raptor
2x500gb Samsung T166 *(16mb cache, SATA2, NCQ e.t.c)*
Samsung SATA DVD-RW

Everything worked perfectly well right out of the box. I have however turned of everything I don't use in bios such as firewire, IDE ports, onboard sound e.t.c
I also compiled the lates 2.6.22 kernel and install nvidia driver with "Envy Script"

---

### Post by gpilkay on 2007-07-12
This setup works very well for an inexpensive XP/Feisty duel boot with no repartitioning risk:

E-Machines T3828
Celeron D Processor
512 MG RAM
two Western Digital 80 Gig Hard drives.
Embarq 100Mb/s Ethernet box, E100 driver.
Ubuntu 7.04

Starting with a normal XP-box, make existing XP-drive Slave, install new blank drive as Master.  Install Ubuntu to Master drive, GRUB will load with Ubuntu, no changes made to XP drive.  A useful setup for a desktop that requires XP for work.  No risk to Windows files.

---

### Post by Motomo on 2007-07-15
1)Ubuntu 7.04
2)Desktop Computer
3)Gateway
4)Model 504GR


Everything worked fine installing with the Live CD

---

### Post by be4truth on 2007-07-21
I lost my passwd for :
[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)

Any idea what to do?
Thx

---

### Post by gevoelig on 2007-07-23
Hi,

I've installed Feisty (Ubuntu 7.04) on my company-laptop this weekend.

It worked mostly out of the box :guitar:.

The only thing I had to customize was the resolution; it booted with 1280x1024.
To switch to native 1280x800 I installed 915resolution and set the mode to 1280x800 16bit

$sudo 915resolution 38 1280 800

Custom steps:
- Resized existing windows-partition using gparted.

Type: Dell Latitude D620
Version: Ubuntu Feisty 7.04
RAM: 2GB
LAN: wifi/cable
HD: 75 GB 
Secc. OS: MS windows

---

### Post by Cappy on 2007-07-23
Toshiba A135-S4666
Works fine. Suspend works. Hibernate works too. Like the rest of the A135 series you need to compile your ALSA drivers to get the sound to turn off on the laptop when you plugin a headset.
[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteA135](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteA135)
It's "Dual Core" but won't run 64-bit. Battery seems to last about 2 hours and a half.
Very good buy.

---

I also took Vista off because it's so slow. XP = huge speed boost. Anyway, I had to locate the XP drivers so I'll list them here for anyone interested.

I have this for Mobile Intel 945GM Express drivers: 
[http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=2301](http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=2301)

Using Atheros AR5xxx 5.3.0.35 for wireless drivers:
[http://www.opendrivers.com/downloadopendrivers.php?href=47456](http://www.opendrivers.com/downloadopendrivers.php?href=47456)

Realtek High Definition Audio 5.10.0.5436
[http://drivers.softpedia.com/get/SOUND-CARD/REALTEK/Realtek-High-Definition-Audio-Codec-Driver-R170.shtml](http://drivers.softpedia.com/get/SOUND-CARD/REALTEK/Realtek-High-Definition-Audio-Codec-Driver-R170.shtml)

SmartCard 2.0.0.6
Haven't looked

Intel Chipset 8.3.0.1013
[http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=816&DwnldID=13499&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=816&DwnldID=13499&lang=eng)

Realtek RTL8139/810x Fast Ethernet NIC
[http://www.versiontracker.com/dyn/moreinfo/win/54582](http://www.versiontracker.com/dyn/moreinfo/win/54582)

---

### Post by sanderella on 2007-07-24
Is there a list of printers that work perfectly with Ubuntu 6.10?

---

### Post by sanderella on 2007-07-24
ok, found it!:)

---

### Post by be4truth on 2007-07-24
....

---

### Post by be4truth on 2007-07-24
Feisty and Linux Mint (32 bit version) on Intel D945GCCR with Intel P4, 512 RAM DDR2 

Everything works out of the box.

---

### Post by be4truth on 2007-07-24
Feisty and Linux Mint (32 bit version) on Intel D945GCCR with Intel P4, 512 RAM DDR2 

Everything works out of the box.

Dapper (32 bit version) on ASROCK K7VM3 with AMD Semptron  512 RAM DDR 

Everything works out of the box.

---

### Post by be4truth on 2007-07-24
Dapper, Feisty and Linux Mint (32 bit version) on ASUS A7V400-MX with AMD , 512 RAM DDR

Everything works out of the box.

---

### Post by be4truth on 2007-07-25
I have problems to load this page since 24 hours. Maybe it doesn't have a visa for India...

[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)

I lost my password, page doesn't load, maybe next I forget my username. Then I am ready for Ubuntu Crazy Crack:)

---

### Post by radicalspud on 2007-07-26
ASUS A7N8X-VM Socket A mATX board
Athlon XP 2800+
768MB PC2700 RAM
ATI Radeon 8500 LE Video Card
Western Digital 80GB IDE HD
Seagate 200GB IDE HD
Creative Soundblaster Live! 24-bit PCI
Philips DVD-R/RW drive
Dell FP1707 17" LCD monitor

the first time i installed Ubuntu Feisty, (nearly) everything worked great and even the ATI card used native resolution of the monitor (1024x768 ) without any extra configuration. had a little trouble enabling the sound correctly on the SB Live! card, mostly because there's 4 different CA1086 items listed with no indicator as to which is what. in spite of that, i was able to get sound output from the hardware. had some trouble with VLC player not putting out sound, but that's a software issue.

after hacking around with different stuff, installing Fedora onto the same drive (and over the top of Ubuntu by accident), i formatted and re-installed Feisty again last night. now ATI card only goes to 800x600 res. not sure about anything else yet; haven't had much time to look at it more in-depth.

the holy grail for me on this computer is to be able to use the TV-Out on the ATI card to play stuff on my HDTV from Ubuntu. currently i do that with Catalyst Control Center in Windows XP via S-Video (this is dual-boot machine.) if i can do that via the DVI port to HDMI, that would be the best, but i'd settle for S-Video *if* it works correctly from w/in ubuntu.

---

### Post by lielf on 2007-07-26
Desktop

motherborad:MSI P965 NEO.

DVD Burner:LG DVD RW GSA-H12N x18.

Dispaly Card:Nvidia GeForce FX 7300GT PCX.

Processor:INTEL CONROE 2.13GHz E6400 s-775 2MB.

Hard Disk:SEAGATE 200Gb 7200rpm SATA2.

Display Monitor: MAG 17" LP717 TFT LCD.

ubuntu cannot boot after install.

can help me?

---

### Post by be4truth on 2007-07-26
> **be4truth said:**
> I have problems to load this page since 24 hours. Maybe it doesn't have a visa for India...

[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)

I lost my password, page doesn't load, maybe next I forget my username. Then I am ready for Ubuntu Crazy Crack:)

OK- got a new login. This page is often disfunctional. It doesn't load. I can't edit. Could the maintenance team give a sign. A simple note : We are working on it' or something? 
My internet connection is fine. Everything works except this page. Any idea?

---

### Post by Cryptic1911 on 2007-07-27
Gigabyte GA-N680SLI-DQ6 (Ver. 2.0)
Intel Q6600 2.4Ghz quad core / 8mb cache
4x1gb OCZ pc800 ddr2
4x gigabit nics (marvell chip - onboard)
Nvidia 6600GT 256mb pci-e (don't remember brand, but doesnt matter really)
Soundblaster Audigy 2zs
Plextor 32x cdr
Sony 16x dvdr
Seagate 80gb boot + 500gb secondary hdd's
2x Dell 2007FP 20" lcd monitors @ 1600x1200 (3200x1200 res desktop in X)

bootcharted to a 36sec startup


This install started as a 6.06 but I have upgraded it to 7.10 through apt-get over the past couple months. It was actually in a Dell E521 pc with the same parts as above except the mobo / cpu / ram, but I just plugged it into this new system and it booted right up. No complaints, and the ONLY thing I had to fix was the time. works perfectly.

The only thing that I don't know works is the onboard soundcard (cmedia?) as I haven't tried it. It probably will though.


:guitar:

---

### Post by bonestonne on 2007-07-27
never realized how much of a help this was.

Specs:
Dual Pentium 3 Xeon processors [783Mhz, 2Mb L2Cache per CPU]
Supermicro S2DGU
1152MB SD RAM
ATi Radeon 9200 128MB AGP4x [in 2x slot]
Trendnet PCI 10/100 Ethernet Adapter
Soundblaster Live PCI
Enermax 300W PSU
DVD drive [no name brand]

specs:
Pentium D940 [3.2Ghz]
MSI Neo P965
1GB G-Skill DDR2 667 Dual Channel RAM
nVidia GeForce FX5200 PCI 128MB DDR
Western Digital SATA 1.5gb/s 250GB HDD
Benq DVD+/-RW 16x
Fortron Source 300W Green PSU [82% efficiency]

overall performance is great, i've only used 64bit to date however, i dual boot with winblows for other apps that aren't available in linux that i use.

i have no trouble with Ubuntu, but other distros i've tried have only worked in VMWare, outside of that they don't work...not sure what to think about that.

just don't make the mistake of running dual channel ram in single channel mode...it hindered my performance until i realized it.
---------
i'm about to look into dual display graphics cards, any suggestions on ATi or nVidia [i realize i will most likely have to reinstall the OS for it].

---

### Post by LordRajaGoombaI on 2007-07-28
Hiyawl,

Since mine is a home brew computer (it's about 3 years old, so I'll try to remember what I put in it), this might help a few:

Athlon 64 3000+
Gigabyte KV8M (or something similar - it has a VIA chipset and video driver)
DVD Burner (I painted it, so I can't remember) but I've had an Optorite work on another machine, sorry found it - it is an LG.  I bought a pioneer on the advice of a computer mag and it shat itself (with very little use too) within a couple of months and took down the IDE on the previous boardto this one (The gigabyte is a replacement board- cost about $50 AUD)  I digress
Sapphire ATI (I know, I bought it when I was still a windblower) 9550 - 256mb RAM

---

### Post by bme on 2007-08-06
Dell Inspiron 640m/1405 Laptop
With 1024 MB Ram
Ubuntu 7.04 Feisty Fawn
Dual Boot with Vista Home Basic

Ubuntu is very much faster than Vista...

---

### Post by tjksn on 2007-08-07
I am a definite newbie to Linux and especially to Ubuntu.  I've attempted various distros in the past and am so far fairly impressed with Feisty Fawn (I'm using Ubuntu Ultimate).  So, the hardware list: 1) Asus motherboard about 3 years old - I forget which model - with onboard sound, 2) Sapphire Radeon 9200 128Mb video, 3) USRobotics wireless USB network adapter, 4) two IDE hard drives.

Ubuntu detected all my hardware and even the wireless adapter works right off the bat.  The only thing with the wireless is it will give me a WPA option, only WEP.

I've gotten Compiz-fusion to work, although it has a problem similar to Beryl in that it won't work on more than one user at a time, even if you log off the first user where it was running.  Example: I log into my user and run Compiz it is fine.  I log off and log into another user and run Compiz then I get blank windows.  This is with version 0.5.1.

The only thing I haven't gotten to work yet is setting up a printer.:(

---

### Post by be4truth on 2007-08-08
Usage of [http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page) I get this error:

Database error
From Ubuntu Document Storage Facility
A database query syntax error has occurred. This may indicate a bug in the software. The last attempted database query was:

    (SQL query hidden)

from within function "Block::load". MySQL returned error "1205: Lock wait timeout exceeded; try 
restarting transaction (localhost)".


The general performance is far too slow. It needs sometimes 5 min for a request to edit to come back. 
I am happy to contribute to this wiki but I am not interested if every link takes 5 mins to load.

---

### Post by tnc on 2007-08-09
Hiya all.
We have installed 7.04 The Fawn.  Works very well.  Quick and consistent.  We are very happy with our switch from Mandriva; which we ran for the last 5 years or so.

 PIII 1700 500M ram nividia TNT card. Two 20gb HDs.  Dual boot w/ neutered XP(for the 5 mins here and there) on Master and /home on slave.

Haven't gotten around to installing our Brother printer yet though....

Thanks to all who put in the hard work to make Ubuntu what it is!
Tim

---

### Post by klytu on 2007-08-10
Newly built system two weeks ago (07/30/07). Dual booting Vista Home Premium and Feisty.

Intel D975XBX2 motherboard
Intel Core Due E6600 2.4 Ghz processor
2GB Kingston DDR2800 (PC2 6400) KVR800D2K2 RAM
320 GB Western Digital SATA II WD3200AAKS Hard Drive
Radeon Sapphire 512MB X1650PRO PCI-e x16 video card
PCTEL 789T HSP MicroModem 56K (cheap spare one I had lying around - used for faxing)
Mitsumi FA404M combination 1.44mb floppy drive/USB card reader
Philips 20X SPD2413BD DVD Burner

Booted right up on the first try! All hardware except winmodem worked right "out of the box" - even the video card which I had expected I would have some difficulty with before loading restricted ATI drivers. After loading ATI's proprietary restricted graphics driver and compiling the modem drivers,  performance is excellent.  Bear in mind, though, that I am not a gamer.

---

### Post by 4KvRMU7Nnv on 2007-08-15
Compaq Presario R3370US Laptop
80GB hard drive
1.2GB DDR Memory
AMD Athlon 64 1.83GHz Processor
NVidia GeForce4 440 Go 64Mb Graphics Card
Broadcom BCM4306 Wireless Card
 ----------------------------------------------------------------

Everything but wireless detected out of the box.  I got wireless working with ndiswrapper using a guide found here.  The best functionality of wireless is with the actual drivers for my computer that I got on hp's homepage.  I got the latest supported graphics driver from alberto milone's Envy script which also compiled a kernel for complete stability.  I recommend this over the standard ubuntu restricted driver install of the driver.  

Overall I am very pleased with the functionality of Feisty on my laptop.  Everything works perfectly...just wish I had a better computer...oh well.

---

### Post by only1bobert on 2007-08-16
Acer Aspire 5920G
Intel Core2Duo 1.5 ghz 2 proccessers
2 gig of ram
160 gb sata hdd
hd dvd/dvdrw/cdrw combo drive-toshiba
Nvidia GeForce 8600m Gt 256mb dedicated with up to 1 gig hyper memory
Intel pro wireless 3905a/b/g

Can only get my video card to support 800x600 with no 3d accelleration.  Only the newest driver from Nvidias website would even get it to work.  Also the HD DVD Rom drive would not work unless you load the generic-ide modules.  wireless works great.

---

### Post by m@R3k on 2007-08-16
[COLOR="Red"]Acer Aspire 5920G[/COLOR]
Intel Core2Duo T7300 [COLOR="Blue"]2.0 GHz[/COLOR]
[COLOR="Blue"]2 GB[/COLOR] RAM
HDD [COLOR="Blue"]160 GB[/COLOR]
DVDRW/CDRW
nVidia GeForce [COLOR="Blue"]8600M GT 512 MB[/COLOR] GDDR3
WiFi, Bluetooth, Infra

> **only1bobert said:**
> Acer Aspire 5920G

Can only get my video card to support 800x600 with no 3d accelleration.  Only the newest driver from Nvidias website would even get it to work.  Also the HD DVD Rom drive would not work unless you load the generic-ide modules.  wireless works great.
I had the same problem with my 8600M GT GPU, I resolved it by installing [COLOR="Blue"]_ENVY_[/COLOR]. You can find it there: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by pdamsten on 2007-08-17
Kubuntu Gutsy
AMD64 X2 and Leadtek WinFast PX8600 GT
Did not work with nvidia-glx-new 1.0.9755 but works with nvidia drivers 100.14.11 updated with envy.

---

### Post by m9ke on 2007-08-18
Here is some info on a PCI USB 2.0 upgrade I did that worked out swell.

Hardware
========
Old PC (768 MB PC133 RAM); Mobo K7SEM. ([http://www.klondike.ru/spec/MotherBo...ketA/k7sem.htm](http://www.klondike.ru/spec/MotherBo...ketA/k7sem.htm))
     *-cpu
          product: AMD Athlon(tm) XP
          version: 6.6.2
          size: 1550MHz
          width: 32 bits
     *-pci
          description: Host bridge
          product: 730 Host
          vendor: Silicon Integrated Systems [SiS]

Software
========
Ubuntu 7.04 (Fiesty Fawn)

Compatible USB Upgrade
======================
Installed a Rosewill RC-101 USB 2.0 5-port PCI adapter.  Less than $10 US from NewEgg.

Did not install any drivers.  It just worked out of the box.

---

### Post by anagor on 2007-08-19
Kubuntu Gutsy 7.10 tribe 3 upgraded to 4 and beyond.

==Hardware==
CPU - Core2Duo 6300
M/B - MSI P6N SLI - Nvidia nForce 650i SLI chipset
RAM - Generic DDRII 667
Video- Nvidia 7600 GS
Sata HD
Audio - On-Board Nvidia
FireWire - VIA on-board
Ethernet - Nvidia on-board
==============
All works fine, except for M/B sensors,which recognized by lm-sensors, but they don't have any drivers for it yet, so I'm unable to monitor and change FAN speed, and Voltage.
Intel's Core2Duo CPU has it's own temp sensors and works under Linux.

No special adjustments were needed, everything worked out of the box.

---

### Post by Steve1961 on 2007-08-19
Desktop

1)Version Of Ubuntu - Feisty
2)Type Of Hardware  - MSI K8N Neo4 Platinum, AMD 64 3800+, Asus Nvidia 6600GT PCI Express, 3xSATA HDD (Maxtor and Samsung), 1GB (2x512) OCZ Premier DR400
3)Hardware Maker - self-build

Laptop

1) version of Ubuntu - Feisty
2) IBM Thinkpad
3) Hardware Maker - Mainly Intel
4) Hardware Model - R50e

Everything works out of the box.

---

### Post by hayesben on 2007-08-20
AsRock ConRoeXFire-eSATA2
1.5GB Crucial RAM (DDRII)
2 x 160GB SamSung HD160JJ SATA HDD
Intel Pentium 4 3.40Ghz Processor (LGA775)
nVidia 7600GS PCI-E Video Card
Creative Labs SB Audigy 2 Value

Ubuntu v7.04 detects H/W and works without any issues.  Not test with pre 7.04 distro's.

Ben

---

### Post by jlh68 on 2007-08-23
Ubuntu version:  7.04
Type of Hardware:  Laptop
Hardware maker:  ACER
Hardware model:   TravelMate 2480-2943 Notebook PC

Intel Celeron M processor, DDR2 Ram (original 512) current 1.5GB, 40 GB Hatachi Hard drive (original) 80 GB Hard drive current, CD-RW/DVD-ROM Combo Drive, Intel chip set 945GM, 14.1 WXGA TFT LCD

Ubuntu worked on installation, with the following changes, I had to add Synaptics Touchpad driver [gsynaptic] to get the small square scroll button between the left and right buttons to work correctly AND to be able to turn OFF the tap feature.  Secondly I had to install the Intel video driver [xserver-xorg-video-intel] using the Synaptic package manager.  The Intel install was very easy and now my screen resolution is correct (which appears very clear).  By the way all I did is to add the Intel driver and the system did every thing else to make the changes.

The SD card reader worked without any changes, the WiFi worked without any changes, after getting the needed codecs the DVD player plays movies, and CD music.

Update:  I was able to rip a CD and then burn a blank with the ripped material, using Sound Juicer + Serpentine.

---

### Post by Dark Star on 2007-08-23
Ubuntu Ver. 7.04
Hardware: Desktop
Manufacturer : HCl
Mode : Beanstalk 4458

Intel P4 2.8 , 256MB DDR400 , 80 GB IDe hard disk..Intel 845 Chipset with inbuilt VGA.. 
The problem is some times it hangs a lot.. I know due to ram :( But try making newer Driver cause am gng to update thanks.. Like driver for P35 :D

---

### Post by likemindead on 2007-08-23
I have an HP Pavilion 522n that's been great so far, 100% Ubuntu. My only issue is that I can't burn a CD. I've tried both Serpentine and GnomeBaker to no avail. Searched the forums for info on the hardware, a **MITSUMI CR-48X9TE**, but can't find any thing. Any help would be very welcome. 

Everything else is great.

---

### Post by WIREHEAD on 2007-09-02
PIII 700 MHZ ,500M PC133 RAM , bulit from old parts runs Dapper slowly but surely.
This has been running for over a year with no real problems after install.

Dell Optiplex GX260 ( 1.8 MHZ , 500M PC2100 RAM ) seems to be getting along fine with Feisty , About 2 months of casual usage .

Athlon 1.0 GHZ ( overclocked to 1430 MHZ ) Shuttle AK31 motherboard 
1.0 G PC3200 memory at 266 MHZ CAS 2.5
Soundblaster Audigy card 
ATI Radeon 256M PCI video card
PCI 2.0 card and NIC card are unknown MFG.
Sony DVD+RW
Dapper installed just fine with the exception of the audio card , which had to be declared as default before it would work.

A BIG THANK YOU to all the folks who have contributed to the Ubuntu project !

---

### Post by spikeyone on 2007-09-02
Self-built:

1) Ubuntu 7.04 and 7.10 Tribe 5 (Feisty and Gutsy)

2) Type of hardware:
**Case**: Antec Nine Hundred (900)
**Motherboard**: Gigabyte GA-P35-DS3L
**CPU**: Intel Core 2 Duo E6750 2.66 GHz w/ stock heatsink/fan
**PSU**: Antec Earthwatts 500
**RAM**: Crucial Ballistix DDR2 800 Mhz
**Video Card**: BFG NVIDIA GeForce 7900 GS OC 256MB
**Hard drives**: Western Digital WD5000AAKS 500GB SATAII 3.0Gb/s, Maxtor PATA 120GB
**Optical Drive**: BenQ DW1655 16x DVD-RW PATA

PERFECT compatibility with Feisty with zero tweaking. Everything detected: all hard drives, graphics card, sound, USB, and LAN worked out of the box. Very happy with my first builld! :)

/edit

If for some reason you install Windows XP after install Ubuntu, Windows will kill the ethernet for some reason. I thought I fried my motherboard, but happily found the fix: [here]("http://ubuntuforums.org/showthread.php?t=538448").

---

### Post by svtfmook on 2007-09-03
Feisty on:
Asus A8N32 SLI Deluxe
AMD Opteron 165
3 x WD 250GB SATAII Drives
2GB DDR500 Crucial Ballistix
Hyper 500w PSU
18x DVD
EVGA 7900GS
Logitech G15
Logitech MX518

Things i have gotten to work in the past 5 days of running feisty:
compiz-fusion
G15 tools
3d acceleration
networking, including dual lan
gaming (enemy territory, america's army, urban terror)
nvraid via dmraid

what i have not figured out yet:
multi-button support for my mouse

haven't tried:
burning

---

### Post by mujalan on 2007-09-03
Computer: Compaq 1750
Multifunction Machine: HP Laserjet 3050
Software: Feisty 7.04
Prints, scans with Kooka or XSane, copies.  Works well on all three although I had some initial difficulty deciding on the right driver.

---

### Post by shakma on 2007-09-05
Ubuntu version: 7.04
Type Of Hardware: Printer
Hardware Maker: HP
Hardware Model: Deskjet D2430

Works perfectly out of the box.  Plug in USB and go to System>Administration>Printing.  It will be detected. Use Deskjet D2300 drivers (it defaults to this anyway on the next screen).  Enjoy your printouts!

P.S. Americans: Set your paper size and print area to "Letter"!  (A4 is *NOT* the same... :()

---

### Post by svtfmook on 2007-09-05
plug and play on feisty:
Lexmark X3350 all in one printer (printing, no multi-function support from lexmark)
3.5" multi-reader drive (3.5", sd, md, etc.  this drive is found under a number of manufacturers, including rosewill and mitsumi)

---

### Post by 7Priest7 on 2007-09-07
This is not a Desktop! It is a laptop.

[http://www.walmart.com/catalog/product.do?product_id=5946677](http://www.walmart.com/catalog/product.do?product_id=5946677)
^ Works using WUBI and Ubuntu 7.04 alternate I386

Bugs: Before GUI displays it shows a glitchy screen...
Bugs: On Shutdown it shows a glitchy screen...
Bugs: Dialup/sound does not work (without additional drivers)

Some things I did not test (DVD Drive and External Monitor)

I will edit this if I deciede to reinstall/test it more...

I had to Re Image my computer (Windows Error)

Hope I Helped

Alex

---

### Post by kutitata on 2007-09-08
Ubuntu... It just works... really!!!

I am so happy i decided to go Linux...

I honestly had no idea it would be this easy...

My specs : -

AMD Athlon X2 4000

Asus M2N-E

Asus EN8500GT

D-Link DWL-G510

WD 320 GB SATA2

Everything worked perfectly out of the box... It was super!

---

### Post by Arkasai on 2007-09-08
Ubuntu version: 7.04
Type of Hardware: Laptop
Hardware maker: ACER
Hardware model: Aspire 5100

Running about 99% on 7.04, only problem is the memory card reader.  

lspci:

06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)

---

### Post by oubaas on 2007-09-09
Asus A7V8X-X
256Mb ram
ATI All-in-wonder 128 Graphics (not used as TV tuner anymore, never tried)

Booted live CD, able to access internet and email with absolute minimum of fuss.
Did dual boot install,  (with Win 2k), done in 20 mins.
Has been running for a year now, my wife uses it for web and email access, this machine runs
about 14 hrs a day, every day.
Have since blown the windows partition away to make space for our MP3 files.
As solid as a rock.

---

### Post by ferry on 2007-09-10
NEC LL570/H

AMD TURION 64x2 TL-50 , 1.6GHz x2
RAM : 1 GB DDR 5300
ATI 1100 video card

Everything is going fine, except brightness control applet 

I got this new machine 1 month ago with unbelievable price US$450 :)

Now I am felling the real 64 bit machine.

---

### Post by Dobbin on 2007-09-10
> **Necrome said:**
> Hi there,

I have not been able to find any info if Feisty works fine with Sony Vaio VGN-TX3XP. Does anone know? The graphics card (Mobile intel 945GM Express Chipset Family) gave me a lot of problems with Fedora Core 6. 

Thanks in advance.. (Sorry if this is the wrong place to post this question)

I have Feisty running very nicely on a TX3XP, all be it on an external USB drive.

---

### Post by bensam40 on 2007-09-12
ubuntu 7.04 installed in my desktop p4. 3.06 dual core, inter d865, 512 ram,80 gb sata hdd.
hdd is recognised as scsi
lg cd-rom crd 8522b2,01d & samsung cd-r/rw sw 252f r802 recognised as scsi instead of ide.
both cd roms dont display the files in disk

---

### Post by prevail89 on 2007-09-12
1)Version Of Ubuntu:7.04
2)Type Of Hardware: Printer
3)Hardware Maker: Brother
4)Hardware Mode: MFC-420cn

My laptop (hp pavillion zv6000) is working fine with Ubuntu but I can't get my mfc-420cn printer working. The list doesn't have it in it. can you plz tell me how i can get my printer and Ubuntu to work together?

---

### Post by MerlinX420 on 2007-09-12
Intel P3 500 Slot 1, 256 MB,nvidia TNT , D-Link DWL (Atheos based),unknown sound card.
gateway 2000 GP7-500
ubuntu/kubuntu 7.04

install went fine with either distro, wireless networking , sound all work perfect.
When upgradeing restriced drivers to support nvidia-leagecy drivers system crashes.
Screen goes white and then upon reboot goes to fatal io error 104.
Looks like I "HAVE TO" upgrade my computer

---

### Post by TennesseeAborigine on 2007-09-12
ubuntu feisty fawn:guitar:

---

### Post by marine64 on 2007-09-15
mobo: asus p5k SE 
cpu: intel e6750 2,67GHZ 1333 fsb
ram: 2GB g.skill dual channel 800
vidcard: foxconn 8800gts 320mb OC (ubuntu messed up when i set restricted drivers enabled)
hdd: seagate 320GB
dvd burner: lite-on 20x dvd burner

ubuntu: 7.10 tribe 5

---

### Post by tooCanad on 2007-09-15
Everything works just fine

ram: 1.5 GB PC 3200
video:  on board video NVidia 6100
ACER 19" Widescreen Monitor ( acceptable but not great)

---

### Post by Jeroen Vernooij on 2007-09-16
ubuntu 7.04
lian li cr-33a cardreader 50in1

only tried CF and SD cards, works fine out-of-the-box.

keywords for search: lian li lian-li cr-33 cr 33 cr-33a cr-33b

---

### Post by victorgreen on 2007-09-16
OS: Fiesty
Hardware- Abit AN8-SLI, AMD 3500+ (socket 939), 2x 1gb Corsair XMS PC3200, Nvidia 7800gt, Creative Audigy2 ZS Platinum- but only 2.1 out of 7.1 system, Seagate 320gb 7200rpm sata

---

### Post by PsycoGeek on 2007-09-18
Acer Aspire 3680-2682
Celeron M 440 1.86ghz, 512mb RAM, ICH 7M southbridge
Intel Mobile 945GM integrated graphics controller w/ up to 256mb shared memory
14.1" Crystal Bright WXGA (1280x800)
80gig Western Digital SATA hard drive, WDC [W800BEVS-22]("http://www.westerndigital.com/en/products/Products.asp?DriveID=202")
Sony CRX880A/10 Slim 24x24x24x8x CD-R/CD-RW DVD COMBO
Marvell Yukon 88E8038 PCI-E Fast Ethernet Controller, RJ45
Atheros AR5BXB63 WiFi mini PCI-E
5-in-1 media card reader, one PCMCIA type II

Installed Ubuntu 7.04 Feisty Fawn

Working: [video (1280x800), sound, touchpad]("http://ubuntuforums.org/showthread.php?t=429182"), wired ethernet, easy launch keys (see below), 5-in-1 reader, all usb 2.0 ports (3 total), FN keys, CD-R/CD-RW DVD COMBO (read cd's & dvd's, dvd playback, cd data write).

Not working:  Atheros WiFi, tried everything to get it to work.  Watch [this]("http://ubuntuforums.org/showthread.php?t=551621") thread for a coming update on a way to solve this.

[COLOR="Purple"]*STATUS CHANGE*  WiFi is now enabled.  Installed the Corsair 2gig ram upgrade and it is working fine.  Much snappier now.[/COLOR]

Untested:  Modem, VGA out, S-Video out, PCMCIA slot.

Easy Launch Keys:  The keys for e-mail and web browser work for me using Thunderbird and Firefox, respectively.  Had to set each application to check if it was the default when they started, and hit the check now button to make sure they were before they would launch with the buttons.  Have not found a way to set the other two buttons (Acer Empowering Technology- the "e" button, and the "P" user programmable button) yet.  If anyone knows how please post it somewhere and let me know.

[COLOR="Purple"]*edit*  Easy Launch Keys are easily configurable under Keybord Shortcuts.[/COLOR]

Planned upgrades:   CORSAIR ValueSelect 2GB (2 x 1GB) 200-Pin DDR2 SO-DIMM DDR2 667 (PC2 5300) Dual Channel Kit from Newegg (should enable dual channel mode on the motherboard according to Acer), Intel PRO Wireless 3945ABG mini PCI Express WiFi (internal)... see above for the watch thread.

-edit-  I have replaced the Atheros WiFi card with the Intel PRO 3945ABG card and now have WiFi out of the box!  See above link under "Not Working"

---

### Post by bigpetey44 on 2007-09-19
Laptop : Gateway MX6439

Feisty 7.04
Sempron 3400+ (1.8GHZ)
512 DDR2 
80 GB HDD (4200rpm)
Broadcom 43xx (working just fine with ndiswrapper)
Wired Lan Controller works just fine
Sound: HDA ATI SB (ALSA) works just fine
DVD Burner
ATI 200M Chipset

End Result : No Conflicts

Server: Custom

Feisty 7.04 (Server)
Athlon 2400+
1.5 GB DDR
120GB ATA133 7200RPM
Onboard LAN (might switch to a basic linksys card)
ASUS Socket A Mobo
Generic CD Burner
ATI 9600XT AGP 8X (128MB)

End Result : No Conflicts

PC : Custom

Feisty 7.04
Athlon 64 3000+
3 GB DDR
80 GB X 2 (haven't got raid successful yet)(VIA VT8237)(SATA)
ATI X1650 512 DDR2 AGP 8X (Conflict)
ASUS K8V-SE Deluxe
Linksy Network card
Audigy SE 
DVD Burner

End Result : 2 Conflicts

Everything seems to work just fine and im quite satisfied with ubuntu, the only drawback im having is getting the raid device to install and bootup correctly. The other drawback is the ATI card not wanting to work correctly. I recommend not getting the x1650 for it has been a pain in linux for me, and i will have another post (in another section) on my x1650 card and what seems to be the problem.

---

### Post by keeper-of-the-real on 2007-09-20
Feisty 7.04

Koolance tower case - H20 cooled the processor, and cooled raptor drives..
change fluid annually.

Intel Pentium 4HT Northwood 2.4C (overclocked to 3.2GHZ)
ABIT IG7-G (5.4 years running almost continuously overclocked- best board I ever owned!)
1.5 GB DDR- Corsair
2 - 37GB 10,000 rpm Western Digital Raptors in mirror RAID 
2- 250 GB Western Digital (for storage)
DVD/CD Lightscribe Samsung burner 
nVidia 7600GS (I'm 99% that's the model #)
Sound Blaster Live!  
on board ethernet, usb

Everything works great.  

USB auto mounts multiple USB drives.
USB DVD CD burner (SONY) auto mounts and works.

nVidia drivers are the latest from nVidia I dloaded on 9/20/07
-3d games flawless w/default settings!

I also use a 2GB iPod nano with rhythmbox.

*ALL hardware worked by the default feisty install and updates, w/ only addition of latest nVidia driver.*


NO CONFLICTS!

---

### Post by chinaski on 2007-09-21
Ubuntu 7.04 Feisty fawn

• Processor: Intel Core 2 Duo E6550 - 2,33 GHz, FSB 1333 MHz, Cache 4 MB
• Motherboard: Asus P5K/SE intel P35, FSB 1333 MHz, 4xDDR2 800 dual channel, 8xUSB 2,0
• RAM: 1 GB, V-DATA, DDR2 800, CL 5
• Hard Disk: 320 GB, Maxtor DiamondMax Plus 21, 4 MB Cache, SATA2
• DVD: Optiarc SATA DVD RW AD-7170S
• Video Card: Asus EN7200GS, NVIDIA 7200GS, 256 MB
• Audio: 6 channel SoundMax AD1986A Audio Codec
• Network Card: Realtek Gigabit LAN

everything works fine out of the box

---

### Post by heroedeleyenda on 2007-09-22
1) 7.04 (Feisty)
2) Laptop
3) Packard Bell
4) MX36-U-050W

All works, including Atheros Wifi chip with WPA

---

### Post by runemaste644 on 2007-09-23
Ubuntu 7.04 (Wubi)

Lenovo 3000 N100

***Worked from the start***

Volume controls
Power button
CD/DVD drive
HD audio
display 1680x1050
Bluetooth
USB ports
Touchpad

***Partially works***
Fingerprint reader (doesnt really work)
Card reader (SD works only)

***Had to get a driver, but works***
N Wireless (I found a magical BCM43XX script)
Webcam (Low quality, but works)

***Doesn't work***
Card Reader (only SD works currently)


The card reader is Ricoh and can also do Memory Sticks and xD cards

---

### Post by startherepodcast on 2007-09-25
I got a CanoScan Lide 50 from Canon Scanner to work like this (should work with all other Lide Models):

Type in the Terminal:
sudo apt-get install sane sane-utils

Then install XSane Image Scanner via Add/Remove Menu

Connected the Scanner, started XSane, full success!

PS: Ubuntu 7.04 Feisty Fawn

---

### Post by neorou on 2007-10-02
Kubuntu 7.10 (Gutsy Beta using Alternate Install CD)

Dell Inspiron 1100 with:
1. Celeron 2GHZ processor
2. 1GB RAM
3. DVD-ROM/CD-R/W

what works:
1. DVD
2. sound
3. 1024x768 res at 24-bit
4. ethernet

what does not:
1. Dell TrueMobile 1150 is not supported by [http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)

Notes:
Install encountered problems with xserver. Turns out I needed a new BIOS (A32). If you are thinking of installing UBUNTU on this machine, flash the BIOS from Windows first - it's the easiest way, especially if you only have one computer. Otherwise you will have to create a bootable DOS CD with the executable for the BIOS loaded.

Any X11 configuration will NOT work if BIOS is not at least A32. 
Better write your xorg.conf file and follow the one posted on this site:
[http://geocities.com/randomnumbergenerator2001/](http://geocities.com/randomnumbergenerator2001/)

---

### Post by noynac on 2007-10-04
1) Version Of Ubuntu  -  7.10 beta 1

2) Type Of Hardware  -  Inkjet printer

3) Hardware Maker  -  HP

4) Hardware Model  -  Deskjet 6988

Gutsy recognized this printer when I plugged in the USB cable and made the necessary entry in the "Printer Configuration" dialog. The HPIJS driver was selected and worked fine.

I tried to use the HPLIP Toolbox, but it reported device not found, even though it did show the printer. I corrected this by upgrading to HPLIP 2.7.9, which is the most current version on the HPLIP website.

---

### Post by NotTheMessiah on 2007-10-08
Feisty Fawn 32bit & gutsy32
&#8226;Samsung syncmaster 2232GS 22" 
&#8226; DFI LanParty UT NF3 250GB
&#8226; AMD Athlon 64 +3700 clawhammer(socket 754)
&#8226; Gigabyte Nvidia 6600GT AGP
&#8226; LifeView(FlyDVB-T)(works partially -after modprobe and with kaffein- doesn't 
  find every digital channel  -works with gutsy)
&#8226; printer Canon iP4200
&#8226; camera Benq DC 1300(works with Ekiga &#8211; tough to adjust colors)
&#8226; LAN(Nvidia nForce) &#8211; I am able to share my internet connection(dial up-external     serial modem 56k) with my laptop via a crossover cable
 (Host: desktop Ubuntu >>  Client: laptop Ubuntu OR XP

---

### Post by gobuntu on 2007-10-09
Ubuntu Feisty arch = i686

Hardware: KONICA-MINOLTA magicolor 2430 DL

Printer supported natively by Feisty.

Only caveat: There are TWO magicolor 2430 DL. Older one made by Minolta-QMM and newer one made by KONICA-MINOLTA.

I have KONICA-MINOLTA newer model. The native support, though is for the Minolta-QMM version.

However, the drivers installed work OK, but do as follows:

1. Install straightforward via System/Administration/Printing

2. In the case of the KONICA-MINOLTA, it wil be detected as KONICA-MINOLTA at the USB-port where it is plugged into, and of course printer is to be ready.

3. The installation will offer other models, none being for the 2430 DL. Don't choose any of those.

4. Instead, click tab to CHANGE MANUFACTURER and change it to "Minolta".

5. Under the manufacturer "Minolta" the 2430 will indeed show-up. Click on that one. Click proceed. Do not install any drivers.

6. Printer will be correctly installed.

7. Double click on resulting icon (PROPERTIES) to make it DEFAULT printer.

8. It if by default 'monochrome'. Change it to print in color, where would hereby recoomend:

9. Do not use icm files. Set it for Color Photos and Text, and Calorimet ric Intent.
Why? That's what got me the best match of color. However, verify for yourself, under the caveat that under SOME choices, the printer MIGHT NOT PRINT.

Also, a resolution of 2400 points is there,  but not in the printer. Choosing THAT resolution the printer still printed.  I set my resolution to 600 x 600, though, and noticed no eye differencce.

Good luck.

---

### Post by NinjaMidget on 2007-10-12
MSI K9VGM-V - VIA K8M890 Chipset AMD Athlon 64 X2 5000 AM2 processor
LG GSA-H55NK 20X DUAL DVD RW Drive

Installed using the 7.04 Alternate CD

The install detected the motherboard and all on-board components with no problems

---

### Post by thedarky on 2007-10-16
Hardware:  Clevo M550SE basic build without wireless networking, modem, card reader or camera. 
processor: x86 Family 6 Model 14 Stepping 12 Genuine Intel ~1729 Mhz  DUAL
RAM: 1GB 667MHz (highest amount possible for the single slot)
BIOS Version/Date	Phoenix Technologies LTD 6.00, 16/08/2007 
Manufacturer's web page for specs
[http://www.clevo.com.tw/en/products/prodinfo_2.asp?productid=26](http://www.clevo.com.tw/en/products/prodinfo_2.asp?productid=26)

Ubuntu Feisty 7.04 live CD kernel 15 install as dual boot with Win XP Pro - done as a comparison between each OS out-of-the-box (without proprietary drivers and without extra Ubuntu drivers).

All basics work first up, with about 30s to boot.  A bios bug and a memory resource allocation error message flash by, but don't influence booting.  Will probably need to be tracked down for fine video resolution later on, but it looks like there's enough memory to run all kinds of video.
Screen resolution defaults to a slightly too anamorphic 1024x768 at 61hz, ( and the resolution can't be changed with the Gnome UI)  but it is a better read than the default Win XP Pro "safe"-like resolution out of the box.   And even with the proprietary drivers, the Win experience is underwhelming.  The Gnome desktop has just so much more clarity and reading-friendliness on these small lcds.

Battery management is as desired, with hibernation smoothly enabled in the prefs and with all function keys for screen power responding as expected.  This includes default screen off with lid closing.
NOTE that the default power applet misreports the power source in the narrative balloon, even though the system prefs respond correctly.  AND the screen doesn't automatically dim when battery power is chosen.
There are fewer power management options in the Win out of the box.

Audio works as a muted compromise driver for all application outputs, the mixer hasn't been tried to increase the volume of output or for recording from the inbuilt mic, nor has the spid interface been tried.
With the Win XPPr0 SP2 (up to date) out of the box, zero audio.  

Optical drive plays basic discs on default apps.  Of course, there aren't enough default codecs for a good range of read operations.

After applying all Ubuntu auto updates - to kernel version 16 - the installation remains stable,  but with no extra fine function added so far.

The machine has been acquired as a basically un-networked book reader for a disabled user.
Ten out of ten for the functionality overall.
8 out of ten for a few fine tunings, and it looks as though Gutsy will have those answers without the user needing to do too much manual driver installation.

---

### Post by trebach on 2007-10-18
Gusty 7.10 on Dell Inspiron XPS
Hardware:
3.4 GHz Desktop P4 with HyperThreading
1GB RAM
Radeon 9800 videocard
Broadcom 4306 Wireless
Broadcom Ethernet Card
4x DVD+-R/RW 24x CD-RW
touchscreen
eraser nub mouse

Works out of the box:
Display
Ethernet
Reading CD's
touchscreen
eraser nub
network printing

Needed work:
Wireless (took 4 hours to configure, still have to reinstall driver in ndis after reboot every time)
Sound (30 sec: PCM actually controls volume)

Have not tried:
Burning CD's or DVD's

---

### Post by viriatus on 2007-10-20
Ubuntu 7.10
Acer Aspire 1692 WLMI

1GB RAM
ATI Mobility Radeon X700 64MB
80GB Hard Drive
Pentium M 1.7GHz

- Ethernet card (OK)
- wireless (OK)
screen and graphics card ( with the correct 1280*800 resolution right out of the box, installed ati drivers through repositories and worked fine , FINALLY!!!, although Urban Terror for example is slower than on XP, in Ubuntu i get ~30fps, on XP ~70fps or plus, Desktop effects works OK, I'm using XGL but there is a problem that i can't play any games if i have XGL installed.... :(
Modem (didn't tested but i think drivers are OK)
Mousepad (OK)
FN Keys (OK)
Sound (OK)

:KS

BUT
i have this problem:
[http://ubuntuforums.org/showthread.php?t=385869](http://ubuntuforums.org/showthread.php?t=385869)
it's annoying, I installed Ubuntu in Dual-Boot with XP. In older versions of Ubuntu i never had that problem... If don't i press any key it takes 2 minutes to boot (i don't see any progress bar, black screen until login screen, but if i press ctrl-alt-f1 it boots immediately

:(

---

### Post by Super Nade on 2007-10-20
**Version Of Ubuntu **
7.10 Gutsy x86

** Type Of Hardware**
* Motherboard:* ASUS P5K Vanilla (JMicron, ICH9R, Intel P35, Attansic LAN) BIOS 603
* Video Card:* x1900xtx 512 Mb (built by Sapphire, but with ATI's label on it)
* RAM: *Crucial Ballistix PC6400 (dunno if this is necessary)
*CPU: *Intel Core2Duo E6550
*DVD Drive: *LG Lightscribe
*SATA Hard Drives: *Western Digital Raptor 36Gb, Maxtor 300Gb

[B] Comments:
[/B]Ethernet -[COLOR=Red] o.k for x86 only.  Module atl1 is BROKEN for AMD64...[/COLOR]
Video - o.k (Compiz-Fusion)
Wireless Mouse, USB Keyboard - O.K
Detects Jump drive, SD card+adapter, Sandisk Sansa mp3 player and my Sony DSC-H2 digital camera
Logitech USB Headset - o.k after fiddling around a bit. -->[http://ubuntuforums.org/showthread.php?t=509598](http://ubuntuforums.org/showthread.php?t=509598)
Dual boot with WinXP on another HDD - O.K

---

### Post by Rex_Mundi on 2007-10-22
Ubuntu 7.04 feisty fawn
Notebook
HP
DV9055ea
nVidia 6700 Go
Core 2 Duo T5500 processor
2GB RAM (upgraded)
External display functioning properly with laptop display turned off

Ubuntu 7.10 Gutsy Gibbon
Works but external display not recognized.

---

### Post by MrBordello on 2007-10-22
**Gigabyte W551N Laptop**
Gutsy runs perfect, except for the env. light-sensor, that doesn't work in Win XP either (and isn't needed). In battery lifetime gutsy kicks *** on this device. XP: 1.5h max vs. Ubuntu: 2.5+h (with compiz fusion). Can't explain why ...

---

### Post by alwayswiththefailing on 2007-10-22
OS: Ubuntu 7.10 64bit

Processor: AMD Athlon 64 1.8Ghz Socket 939
Motherboard: DFI LP UT NF4 Ultra-D nVidia Socket 939 ATX Motherboard / Audio / PCI Express / Gigabit LAN / USB 2.0 & Firewire / Serial ATA / RAID (D452-2030)

Memory: 1GB DDR2 

HDD: 160GB SATA Wester-Digital
        160GB IDE Wester-Digital
        250GB UBS Seagate FreeAgent
CD-Rom: Sony Dual Layer +- DVD Drive

Video: Gigabyte GForce 6600 128MB PCIe
          22" Widescreen LCD 1680 x 1050

Dual Boot (works great)
Ubuntu 7.10 64bit
Windows XP SP2

So far so good, almost.  The USB drive is partitioned with a swap and two fat partitions. (incase I want to install an OS on it) On the second partition there is a backup folder that has all 90GB of my saved media.  That is the only folder I can't access in ubuntu. Windows can read it alright.
$ ls -la
total 48
drwx------ 5 sean root 16384 1969-12-31 19:00 .
drwxr-xr-x 8 root root   304 2007-10-21 17:55 ..
?--------- ? ?    ?        ?                ? backup
drwx------ 2 sean root 16384 2007-10-16 17:40 progs
drwx------ 4 sean root 16384 2007-10-12 22:28 System Volume Information
 
Also had some trouble with the install, same problem with 7.04.  It would boot the live CD, start the install.  Hit about 70%, installing locales and it would hang without fail.  I finally found some help on here, sorry I can't find the original post.
They suggested pressing Esc at the live CD prompt, pressing ok. then typing:
live acpi = off
The system installed without crashing until I rebooted.
I had to edit the first line of the grub boot loader and added 
acpi = off
as the second last line.

I use the system for playing/streaming media, hosting my Django powered website and everything else I need a computer for.

---

### Post by Christmas on 2007-10-23
**Ubuntu version:**
Kubuntu 7.10 'Gutsy Gibbon'

**Hardware:**
Motherboard: Asus P5B-E (Integrated ICH8 sound chip and Ethernet)
CPU: Intel Pentium Core 2 Duo E4300 1.8 GHz
Memory: Kingmax 2x512 DDRAM2 Dual-Channel
Hard-Disk: Maxtor 160GB, 7200 RPM, 2MB Cache, IDE Interface
Video: Gigabyte GeForce FX 7600GS, 256 RAM
CD-RW Asus
DVD-RW LG, SATA Interface
TV-Tunner Leadtek WinFast TV2000 XP Deluxe

Processor works, internet works, video card works, burning CDs and DVDs works, tv-tunner works. Sound works, however it seems to me like the maximum level is only at about 60% than it should be, but this probably is a problem which I can repair.

---

### Post by jackfusion on 2007-10-25
> **Cryptic1911 said:**
> Gigabyte GA-N680SLI-DQ6 (Ver. 2.0)
Intel Q6600 2.4Ghz quad core / 8mb cache
4x1gb OCZ pc800 ddr2
4x gigabit nics (marvell chip - onboard)
Nvidia 6600GT 256mb pci-e (don't remember brand, but doesnt matter really)
Soundblaster Audigy 2zs
Plextor 32x cdr
Sony 16x dvdr
Seagate 80gb boot + 500gb secondary hdd's
2x Dell 2007FP 20" lcd monitors @ 1600x1200 (3200x1200 res desktop in X)

bootcharted to a 36sec startup


This install started as a 6.06 but I have upgraded it to 7.10 through apt-get over the past couple months. It was actually in a Dell E521 pc with the same parts as above except the mobo / cpu / ram, but I just plugged it into this new system and it booted right up. No complaints, and the ONLY thing I had to fix was the time. works perfectly.

The only thing that I don't know works is the onboard soundcard (cmedia?) as I haven't tried it. It probably will though.


:guitar:

What did you do to get the Soundblaster Audigy 2zs working in 7.10?

---

### Post by djairjr on 2007-10-25
Pentium III - Coppermine
384 Mb Ram
HD Samsung 80Gb
Video ATI Rage Mobility M3 - With Default Ati Driver and no DRI Acceleration
Synaptic Touchpad
LCD 15 Pol
Wireless Card Dlink DWL-G630

The Laptop is fully working, except for the 3D acceleration, but this is a problem well known with the Mach64 Ati driver. The Wireless networks is now suporting WPA Keys and the roaming mode is supperb!

The machine is not a hurricane, but is fast even using Gnome.

---

### Post by cursebg on 2007-10-27
CPU:  	AMD Duron XP, 1600 MHz (12 x 133)
   Mother Board: 	Gigabyte GA-7VM400AMF (3 PCI, 1 AGP, 2 DDR DIMM, Audio, Video, LAN, IEEE-1394)
   Chipset:  	VIA VT8378A UniChrome KM400A
   BIOS Type:  	Award Modular (04/21/04)
   System Memory:   256 MB (PC2700 DDR SDRAM)  

Dispaly: 
   AGP:   NVIDIA GeForce FX 5500 (128 MB)  
   Monitor:  LG Flatron ez T710BH [17" CRT] (141934608)  
   
Sound Card:   Realtek ALC655 @ VIA AC'97 Enhanced Audio Controller  
   
Storage:
   IDE Cotroller:   VIA Bus Master IDE Controller      
   2x Maxtor 6Y080L0 (80 GB, 7200 RPM, Ultra-ATA/133)  
   CD-R: SONY CD-ROM CDU5221 (52x CD-ROM)  
   CD-RW:   TEAC CD-W552G (52x/32x/52x CD-RW)  
  

Ubuntu Gutsy Gibbon with all the updates.
Everything works just perefectly!

---

### Post by ARhere on 2007-11-06
1. Ubuntu Desktop 7.10
2. [Belkin Shutdown Software]("http://www.belkin.com/support/article/?lid=en&pid=F6C120-UNV&aid=5398&scid=2") (Bulldog [UPS]("http://catalog.belkin.com/IWCatSectionView.process?Section_Id=76") Controller and Drivers)
3. [Belkin]("http://www.belkin.com/")
4. [F6C120-UNV]("http://www.belkin.com/support/product/?lid=en&pid=F6C120-UNV&scid=2") 1200VA battery backup.

I used the install CD and simply unpacked and ran ```
sudo ./install
``` 
It was written and tested on Red Hat 8 & 9 but I had no problems what-so-ever.  The install was terminal only but very simple.  Control of the UPS is available through the terminal through easy to use scripts.  A GUI is also available and is well done.
:guitar:
At least Belkin understand to write its drivers in Linux if it is to make sever related hardware!  [<wink wink>]("http://ubuntuforums.org/showthread.php?t=603967"):mad:

---

### Post by auisce on 2007-11-07
**Netgear WG311T 802.11G 108Mbps wireless ethernet card**
works flawlessly with all Ubuntu distros. Just push it in the PCI slot, no software config required at all.

**ZyDas 802.11G 54Mbps wireless dongle**
this is unbranded but the chip is a ZyDas
ZyDas doesn't exist now but they did supply a Linux driver and the card works flawlessly if it's plugged in during install but I can't make it work otherwise. (dapper/feisty).

---

### Post by LeJediGris on 2007-11-08
Home made Desktop:

1)
Asus A7N8X-X
Sempron 2800+
1,3G DDR
Nvidia 5900XT
Netgear WG311v2 WiFi G

Works well with compiz effects, WIFI OK with ndiswrapper+WICD

2) 
ASUS P5B DeluXe WiFi Ed
Core 2 duo 6600
2Go DDR2
160G Maxtor IDE
Nvidia 7600GT

Works fine also for compiz

---

### Post by geolr on 2007-11-11
Type: PS2-Keyboard, Laptop-Style
Brand: Sansun
Model: SN-113
(as sold in Germany, I paid 5 Euros)

I use this keyboard since two weeks but only today discovered that the multimedia-keys do work out of the box! 
Volume up/down/mute, featuring nice Head-Up-Display on Screen
Email (Evolution)
Browser (Firefox)
File Search Dialog

This is amazing! :cool:
Many thanks to the Ubuntu-Developers: Great Job!

3D-Desktop-Effects work on my Nvidia Geforce 5800 just by selecting it the visual effects in the system settings option.

So long
Rudy

---

### Post by dheg on 2007-11-11
HP C4385 PhotoSmart Printer

FYI,  I've been running Ubuntu 7.10 on my laptop for a couple weeks now.  I needed to be print some things so I went to Best Buy and purchased a HP C4385 PhotoSmart Printer.   I went through the setup, plugged the USB into my laptop and Ubuntu recognized it and automatically installed the HP C4200 Foomatic driver.   I printed my stuff immediately and it worked flawlessly.    Pretty cool.   I haven't tried the scanner yet.   I think that might be a bit more challenging.

---

### Post by samadams on 2007-11-13
Ubuntu 7.10 Gutsy
Color Laser Printer
Brother
HL 4070CDW

Worked perfect out of the box - literally.  I plugged in the USB (even though the instructions for Mac & Windows say to install their software first) and after about 30 seconds Gutsy recognized the printer and I got to test it out.  It couldn't find the specific PPD file even though it was on a CD loaded and mounted in my CD drive, but it worked with the generic PPD driver just fine.  Since I had the specific driver provided by Brother, I went ahead and installed it when prompted by Gutsy to replace the generic one.  All is well.  Now I have to try to install this thing for XP........

---

### Post by mash35231 on 2007-11-13
Is the link to the list down, dead or gone? I get an error everytime I try to access the                     list....All I want to know is which of the ATI video cards are supported under Ubuntu 7.10. I want to upgrade from the onboard Intel 950 graphics. I'm new to Ubuntu so I'm still feeling my way around.
 Thanks for any help you guys/gals can give me.

   Asus P5GZ-MX Mobo
   E2140 cpu
   1 gig Buffalo ram
   2 160 gig WD eide drives
   Samsung Sata Dvd burner

---

### Post by MrSpiffdifilous on 2007-11-13
Ubuntu 7.10 Gutsy Gibbon with all updates as of today

Intel P4 Northwood overclocked 30%
XFX GeForce 6800XT overclocked ~45%
Creative SB Audigy 2 ZS Platinum with all faceplate connections working as well as full surround sound! remote does not work(no driver)
ASUS P1 Phys-x Card causes no issues
NEC 16x DVD-R/W reads and writes fine
2x 1GB Corsair RAM (cant remember model numbers)
40GB partition on SATA drive for Ubuntu
210GB NTFS Partition for Media
20GB IDE drive for WinXP MCE
80GB IDE drive for Games + Progs
120GB External USB 2.0 for more Media
Sony Ericsson w810i syncs fine with Ubuntu also
Razer Copperhead Mouse works with 7 of 9 buttons functional (attempted to enable last 2, screwed up order of buttons)
Razer Tarrantula Keyboard works. Macro keys not functioning since no driver support. USB1.1 ports on keyboard work, as do Headphone and Mic jacks.

I'll update if i think of anything else or If someone wants/needs more info

---

### Post by rickbeton on 2007-11-15
*** Version Of Ubuntu**
Gutsy Gibbon

*** Type Of Hardware**
Samsung Monitor with ATI graphics card

*** Hardware Maker / Model**
Samsung Syncmaster 2032BW with ATI Radeon HD2400 Pro

*** Issue That Had To Be Resolved**
With the Vesa driver, widescreen modes are not available. Once the ATI proprietary driver is correctly installed, the screen can operate correctly in widescreen nodes.  I had to do the driver installation manually (the APT installation was unsuccessful)

See [**manual installation of ATI driver**]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually") for the procedure that worked for me.

Rick :)

---

### Post by dpodo on 2007-11-16
Runing Ubuntu 7.10 x64 on Lenovo 3000 V100 (Intel chip set)

wirless, touch pad, usb, sound, microphone most of the hotkeys are working.

---

### Post by saransk on 2007-11-16
Home built for a project - PowerMac G4 replacement
Ubuntu 7.10
Tyan Tiger i7501 motherboard
Dual 1.8 gHz Xeon processors (604)
1 GB Micron memory
Adaptec AHA-2940UW Card
Seagate Barracuda 181gb SCSI160 drive
ATI Radon 9250 PCI card (128Mb)
Adaptec AU 3020A USB/Firewire

System "screams."  Much faster than the XP box I have, blows the G4 10.4 out of the water.
No problems loading OS, easy to connect to network, printers and scanner.
Very Very stable - and VERY fast.

With case, etc. spent less than $300.00 - all parts were new or NOS.

Michael Baker
Leaving Leopard behind!!!!

---

### Post by jespdj on 2007-11-19
**Dell XPS M1330 Laptop**

Specs:

Intel Core 2 Duo T7200 (2.0 GHz, 4 MB cache)
2 GB RAM
160 GB 7200 RPM Seagate harddisk
Intel 4965 AGN WiFi adapter
Bluetooth
nVidia 8400M GS video card (128 MB video memory)
WLED screen (1280 x 800)
Built-in VGA webcam (640 x 480)

Installing Ubuntu 7.10 went without any problem on this laptop. After installation I got a notice to enable the restricted driver for the video card; after doing this and rebooting again, Compiz desktop effects work. All hardware including wireless networking and the webcam work out of the box.

There is only one thing that does not work: the internal microphone. This is a known bug: [bug #147682](https://bugs.launchpad.net/dell/+bug/147682).
*edit*: I see that there is a fix available for the internal microphone. I installed it and now it works.

---

### Post by synt on 2007-11-20
* Version Of Ubuntu
7.10

* Type Of Hardware
Samsung Monitor with ATI graphics card

* Hardware Maker / Model
Samsung Syncmaster 757NF with ATI Radeon 9800  Pro

* Issue That Had To Be Resolved
My Monitor is not supported, i can's see him in the monitor list, can't put refresh rate higher than 85 hz (i need 100hz,and yes in windows all works perfect)  That's the only reason i don't use ubuntu for the moment. tried everything.

---

### Post by Sbarton on 2007-11-23
Ubuntu Ver: Gutsy Gibbon 7.10
Hardware: HP All in one Printer 'Photosmart C4280'
Maker: Hewlett Packard
Comment: Print, Copy, Scan worked out of the box

---

### Post by simple_3 on 2007-11-23
Desktop PC Specs:

OS: Ubuntu 7.10
Intel Pentium 4 (3.4GHz, 2 MB cache,HyperThreading)
2 GB RAM
200 GB 7200 RPM Seagate harddisk
Chronos Bluetooth
ATI Radeon X300 video card (128 MB video memory)
ACER AL507 15" LCD monitor

No problem after install. Problems occurs after installing GFX Card driver from restricted driver. After booting, the screen is blank(black). Same problem on my laptop :

OS: Ubuntu 7.10
Intel Pentium 4 mobile (2.0Ghz)
1GB RAM
80GB HDD
nVidia GeForce 4Go (128MB)

[Sorry with my english. (Maap aken kulo ne'e ono salah kata)]

---

### Post by stijngysemans on 2007-11-24
toshiba a100 00n
works out of the box with gutsy
grahics card (intel) and atheros wireless chipset
hibernate works also
great

---

### Post by andreasbayu on 2007-11-25
Hello, everybody! I'm the newbie. I have experience in using linux. I've tried OpenSuse 10.2, Mandrive Spring 2007, Ubuntu 7.04, and latest Ubuntu 7.10. It was seem everything okay. But was not with the sound. My computer is mute! Here's my Audio details from my Control Panel (Windows):
[LIST]
[*]Wearness speaker
[*]Legacy Audio Drivers, status working properly
[*]media control devices
[LIST=1]
[*]mciavi32.dll
[*]mcicda.dll
[*]mciqtz32.dll
[*]mciseq.dll
[*]mciwave.dll
[/LIST]
[*]Unimodem Half-Duplex Audio Devices, driver was from Microsoft, version 5.1.2535.0
[/LIST] 
thank you so much for your help. God Bless all of You :)

---

### Post by andreasbayu on 2007-11-25
whew, Indonesian Linuxer Too : )

---

### Post by franket on 2007-11-27
> **kutitata said:**
> Ubuntu... It just works... really!!!

I am so happy i decided to go Linux...

I honestly had no idea it would be this easy...

My specs : -

AMD Athlon X2 4000

Asus M2N-E

Asus EN8500GT

D-Link DWL-G510

WD 320 GB SATA2

Everything worked perfectly out of the box... It was super!


So cool !!! I want to buy this mainboard.  Thank you !!!! :)

---

### Post by nathanhillinbl on 2007-11-27
Ubuntu 6.10 
ECS n-Force 4m-a Motherboard
AMD Athlon 64 X2 4200+
EVGA Nvidia Geforce 7300
WD Caviar 320GB IDE 
WD Caviar 80GB IDE
Dell OEM CD/DVD Burner
MSI CD Burner
Netgear WG311 v3 using ndiswrapper 1.4
Gateway EV700 CRT Screen (Sucks)

---

### Post by abrianb on 2007-11-29
Recent build:
								 								 										**[GIGABYTE GA-M61P-S3  ]("http://www.newegg.com/Product/Product.asp?Item=N82E16813128034")**motherboard. Likes LInux no problems.
MSI Video card NX7300LE-TD works great. Mobo has 4GB of ram. Desktop effects no problem.
Lite-On DVD [B][IDE Model LH-20A1P-186                                                                                             - Retail]("http://www.newegg.com/Product/Product.asp?Item=N82E16827106050") works well with Ubuntu.
[/B] 								 								 										[B][Rosewill RCR-102 52-in-1 USB 2.0 Black Card Reader  ]("http://www.newegg.com/Product/Product.asp?Item=N82E16820223073")Works Fine.
[/B] 								 								 										[B][Rosewill RM800P Black 3 Buttons 1 x Wheel PS/2 Wired Optical Mouse - OEM ]("http://www.newegg.com/Product/Product.asp?Item=N82E16826193001")
all these worked well with Ubuntu 7.10. I only used a single SATA hard drive. Got Questions PM me.
[/B]

---

### Post by Melcar on 2007-12-08
My desktop as of now:

DFI  Lanparty NF4 Ultra
Opteron 165
X1950XT (the usual Compiz issues)
Audigy 2ZS (had to switch out my X-Fi:( )
Seagate Barracuda SATAII 160GB
Samsung SH-S183L
Airlink AWLL3055 WLAN adapter* 
                                  
* works with WPA out of the box but kernel module caps speeds at 36Mbps.  Ndiswrapper works better.

---

### Post by blu-skies on 2007-12-09
Edubuntu 7.10 works out of the box

I think these computers are 8 years old (1999 vintage)

Intel SE440BX2 Motherboard Revision 17 BIOS / P3 850Mhz / 500Mhz / 450Mhz processors / 512 MB PC100 SDRAM on each computer
various sized IDE hard drives - 20 - 120GBs - no CD-ROM drives (just used 1 drive between the systems to install the intial system onto each computer)
nVidia FX 5200 video cards
Linksys LNE100TX cards

only needed the restricted reponsitory for the nVidla drivers

got a small 16 computer  Edubuntu network running with a single HP2500 Color LaserJet Ethernet (using JetDirect) network printer all with Internet Access

They run much better under Edubuntu than they did under Win2000 and I was very much surprised how easy and fast it was to set up.  (Compared to getting all of them working under Windows, then installing Office onto each one.)

---

### Post by Melcar on 2007-12-09
Just got a new printer (one that actually works with Linux).  HP 5610 AIO.  Works out of the box.  Scanning did not seem to work with the normal hpijs driver, but it does with hplip.  Works fine as a network printer too.  The printer itself is small but a bit noisy (compared to my old monster of a Lexmark).

---

### Post by _davenc on 2007-12-11
Ubuntu 7.10

The logitech usb premium notebook headset works out of the box. I use it for Skype and the only thing I changed was the audio device settings within skype.

---

### Post by klhoard on 2007-12-12
Just got a Logitech MX 5000 Laser package for my birthday. . . wireless keyboard and mouse.  So far everything works great!!

Plugged in the bluetooth dongle, installed batteries in the keyboard, charged up the mouse and it all works.  Press the e-mail button, and Evolution pops up.  The media sliders on the side all work.  I'm sure I will soon figure out how to program all of the other keys on the keyboard.

So far, I'm very happy with this package.

Oh yeah,

Ubuntu 7.10
Gateway P4
1GB Ram
Nvidia 6200
250 & 80 GB HD

---

### Post by mozkill on 2007-12-12
The hardware in my signature (below) works fine.  Ubuntu 7.10 (32-bit) suprisingly sees the motherboards onboard RAID mirror transparently.  I didn't have to configure anything.  I am booting from a 3rd IDE drive though, which might be why it was so easy.

---

### Post by akniss on 2007-12-16
Ubuntu 7.10 (Gutsy)
Brother HL-5240 Laser Printer
Works flawlessly with no configuration required.  Plugged in USB 2.0 cable, logged in, printer was immediately available.  Prints fast and quality is very good.

---

### Post by ApOgEEs on 2007-12-18
**Ubuntu 7.0 Gutsy Gibbon**

Just assemble this PC about 3 days ago. Everything run smoothly out of the box

[B]Intel Desktop Board D945GCPE Motherboard [ Build in V + S + L ]
Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz
Seagate 160GB SATA II
Kingston 1GB 667MHz DDR2
Hauppauge WinTV-PVR 150 - Media Center Kit
Sony Internal Multi Card Reader
Samsung 20x DVDRW - IDE
Samsung SyncMaster 732N Plus
Samsung Pleomax Keyboard & Mouse
Altec Lansing BXR1120[/B]

This is a total Ubuntu Workstation. Ubuntu Installation is way too easy and real fast... 
Booting up and shutdown is fast too!
Now, I'm using this box to surf internet, photo editing, video authoring, TV recording, programming and enjoy the tasty juice of Ubuntu... I'm damn satisfied with this!! I've already forget Microsoft Windows and will stick with this great OS... Thanks All people who make this happen!! :) Cheers!!!

---

### Post by dnvikram on 2007-12-24
1)Ubuntu 7.10
2)Notebook-x86 Intel Core 2 Duo ,Santa Rosa Chipset,Nvidia 8400GeForce Graphic Card,1440x900 Ultrasharp Display,1gb RAM,120gb sata drive
3)Hardware Maker - Dell
4)Hardware Model - Inspiron 1420N

**TIPS***
1)Use the alternate cd( instead of the usual one) to install the OS.99% out of the box.
2)Install the package CHEESE to get webcam running
3)Download the restricted drivers
4)Download the compiz manager from the reps.
***

Unresolved issues:The only problem I am facing currently is the microphone or audo recording.Inspiron 1420N has issues with this and even Dell has acknowledged it and working on fixing this problem.

---

### Post by uwishurockedthishxc on 2007-12-29
Please Only List
1)Version Of Ubuntu
2)Type Of Hardware
3)Hardware Maker
4)Hardware Model

ubuntu 7.10
biostar tforce 520
asus silent en7300gt
1 gig buffalo budget ram
amd x2 4000+ 

booted up and ran perfectly out of the box.  no drivers need for ethernet or sound.  graphics card worked great with restricetd drivers

---

### Post by nerderello on 2007-12-30
Please Only List
1)Version Of Ubuntu
2)Type Of Hardware
3)Hardware Maker
4)Hardware Model
[B]
1) v7.10
2) Motherboard
3) ASROCK
4) AM2NF3-VSTA (running with a single core AMD Athlon)
[/B]

Comments: onboard sound works with ALSA if you set the card to number "1" and not "0" in your .asoundrc file . Restricted video driver for ATI AGP video card causes re-boots. nb. manual says that you cannot use this motherboard with ATI video cards if you run a dual core Athlon processor, then only runs NVIDIA AGP cards..

---

### Post by por100pre1 on 2008-01-01
1)Version Of Ubuntu: 7.10 Gutsy
2)Type Of Hardware: Desktop Computer
3)Hardware Maker: hp
4)Hardware Model: a1719n ([specs available]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00841356&lc=en&cc=us&dlc=en&query=a1719n&product=3347765"))

Comments:

The installer may select the **intel** driver for the integrated graphics, be sure to use the **i810** driver instead. The change can be easily done using:
```
gksu displayconfig-gtk
```

The tested computer came with a **Conexant HSF 56k Data/Fax Modem**, the **Dell driver** can be used:
[http://linux.dell.com/files/ubuntu/modem-drivers/hsf/hsfmodem_7.60.00.18oem_i386.deb](http://linux.dell.com/files/ubuntu/modem-drivers/hsf/hsfmodem_7.60.00.18oem_i386.deb).
Dialup users should have the deb file readily available before installing Ubuntu for a painless configuration.

---

### Post by nDrewPJ on 2008-01-02
1)Ubuntu 7.10 Gutsy
2)Notebook-x86 Intel Core 2 Duo ,Santa Rosa Chipset,Nvidia 8400M GS GeForce Graphic Card,1280x800 ,1gb RAM,160gb sata drive, AES2501 fingerprint reader, HP webcam
3)Hardware Maker - HP
4)Hardware Model - Pavilion DV2530ER

---

### Post by grokwik on 2008-01-02
1)** Gutsy** [7.10]  (I didn't try any other) 
2) The main parts of my **Acer Aspire 7220** are working but I still have to configure some others :

** The video card** is a geforce 7000M
[LIST=1]
[*] Make sure the restricted driver is installed (nvidia-glx-new)
[*]execute ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
[*] Open Restricted Drivers Manager and enable the nVidia driver.
[*]reboot and it should be OK[/LIST]**Wireless** (Atheros AR9006EG lspci id : 168c : 001c)
```

mkdir /tmp/wifi
cd /tmp/wifi
wget http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz
tar -xvzf madwifi-ng-r2756+ar5007.tar.gz
cd madwifi...
make
sudo make install

```

**Sound card**
Download : *linux-backports-modules*
And edit this file : /etc/modprobe.d/alsa-base
To add the following line :
options snd-hda-intel model=acer

My next step is the webcam : Acer Crystal Eye Webcam (recognized but doesn't seem to work)
And then bluetooth (not tested), memory card reader (not tested neither)...

---

### Post by wearekosh on 2008-01-03
ubuntu 7.10 / dual boot XP
3Gig intel Core 2 duo 
ASUS P5K 1394 Mothre Board - 2Gb DDR2 677 kinston ram kit
GIGABYTE Ge 8600 gts - dual DVI - 2 x asus VW192t monitors

Install to dual boot went easily - 
dual monitor with nVidia restricted drivers and nvidia-settings - was simple
dumped firefox and thunderbird data to new install
all seems to work well - impressed with ease of dual monitor install

---

### Post by Kevbert on 2008-01-04
Ubuntu 7.10/dual boot with WinXP Pro
AMD Athlon 64 X2 3800+ CPU
Foxconn NF4UK8AC Motherboard with on-board audio
1Gb DDR RAM
Seagate 300 8Mb cache SATA2 160Gb Hard drive
Logitech wireless mouse and keyboard
Liteon DRW6S160P DVD/CD Rewriter
Asus GeForce 7600GS 256Mb PCIe Display adapter
APC 620 Smart UPS
WP-RT2561T wireless PCI LAN adapter

Installed OS without any major problems.  Only item not recognised is APC Smart UPS which is connected to COM1. Had trouble with wireless card authentication (WPA-PSK), but may have been due to problems with signal strength.

---

### Post by dcstar on 2008-01-06
Ubuntu 7.10 64bit
AMD Athlon 64 X2 4000+ (upgraded from original Sempron 3400), 2GB RAM, 80G IDE disk, Lightscribe DVD burner
Compaq
Presario SR1915AN (Asus A8M2N-LA M/B, Compaq name: NodusM3-GL8E)

Worked right away with integrated NVIDIA GeForce 6150LE graphics & chipset, install needs to be kicked off with "safe mode" graphics to fit on screen correctly before Restricted driver is installed.

Audio worked ok, occasional video freeze up on boot seems to be better after recent BIOS update to V3.10.

System runs Vmware server with Ubuntu 32bit VM, Kubuntu 64bit VM & Windows XP Home VM (from original install on PC).

---

### Post by styven on 2008-01-06
Ubuntu 7.10.
 All in one Printer, Scanner, Copier
 Hardware Maker - Hewlett Packard
 Hard Model - Deskjet F390

---

### Post by dark_ixion on 2008-01-10
1) Ubuntu version: Ubuntu 7.10
2) Type Of Hardware: Laptop (Intel Celeron Mobile M530, 1GB DDR2 667MHz, 80GB SATA, Intel GMA X3100 Graphics)
3) Hardware Maker: Novatech
4) Hardware Model: Sorar

---

### Post by Jeff Rage on 2008-01-12
I can't find the coptability list on [www.doc.gwos.org](www.doc.gwos.org) .  Is there a new link for it?

---

### Post by machs_fuel42 on 2008-01-13
1) Ubuntu version: XUbuntu 6.06
2) Type Of Hardware: IBM X20 laptop.  PIII 600Mhz, 3xx Megs ram
3) Hardware Maker: IBM
4) Hardware Model: 2662-35U
Sound is a little iffy after resume. Hibernate and suspend work well.

Other : D-Link Wireless card, WNA-1330 selected for ATH0 support

---

### Post by big dizzle on 2008-01-14
> **Brownjohn said:**
> Ubuntu 7.10 64-bit
Athlon 64 X2 4200+ 65W Windsor Core
ATI Radeon x1950 PRO 256MB PCI-E
2 x 1GB Wintec AmpX DDR2 800
Cooler Master TX2 CPU Cooler
DFI Ultra M2 Motherboard

After install I would get a black screen when I tried to boot into the OS.  I found a post that showed me how to fix the problem, and i wish i remember which one it is, but alas, i do not... I fixed it by booting into recovery mode and doing this:

lower the splash screen resolution to 1024x768
```
sudo nano /etc/usplash.conf
```

edited the kernel line in the grub boot config:
```
sudo nano /boot/grub/menu.lst
```
1) remove quiet splash and add nosplash noapic nolapic
2) add vga=791 to the end

then i made one more change before i rebooted:
```
sudo update-initramfs -u -k `uname -r`
```

Overall, though.  I do like Gutsy.

I have the same problem when I try to activate the ATI drivers for my ATI Radeon x1600 pro, do you think that this could have been the same problem you were having?

---

### Post by smartroger on 2008-01-18
Ubuntu version 7.10
Motherboard : Gigabyte 
Processor : intel 1.7 celeron
Ram : Kingston PC3200 128Mb x2

i need lan driver << Realtek RTL8139 Family PCI Fast Ethernet NIC >>

---

### Post by rosegarden78 on 2008-01-19
Try typing the following command in a terminal:

xgamma -gamma 0.75

If that doesn't work you need to install xgamma from the repos.

I have posted my own solution here on setting it up:

[http://ubuntuforums.org/showthread.php?p=4168042#post4168042](http://ubuntuforums.org/showthread.php?p=4168042#post4168042)

P.S.  Always use the latest distro ... Gutsy or Hardy.

---

### Post by cogitordi on 2008-01-25
1) 7.10, 64-bit
2) mainboard, CPU, GPU
3) ASUS, Nvidia, AMD
4)ASUS K8N-VM, (Nvidia 6100 graphics (integrated), AMD Turion/64 ML-37 CPU

This is a cool and quiet configuration. The only problem is the driver for Nvidia's GPU. The screen flickers every time the CPU speed changes.

---

### Post by m.capurso on 2008-01-25
Toshiba Satellite Pro 2100 - 512 Mb RAM 30 Gb HD
Mobile Intel(R) Pentium(R) 4 - M CPU 1.90GHz
FireWire (IEEE 1394)
82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
82801CA/CAM AC'97 Audio Controller
82801CA/CAM AC'97 Modem Controller (proprietary driver)
NV17 [GeForce4 420 Go]   (with VESA driver)
Am 1771 MBW [Alchemy] Advanced Micro Devices [AMD] Wifi (NOT WORKING)

Ubuntu 7.10  working perfectly
Help needed with NVIDIA driver and Wifi

---

### Post by cviorel on 2008-01-25
MSI MegaBook L720
Processor & Cache: Intel® Celeron® M processor 2MB L2 Cache, FSB 533 MHz
Chipsets: Intel® 915GM + ICH6-M Chipset
System Memory: 1.5 GB DDR333 SO-DIMM
Display: 17" WXGA+ Glare Type with Brightness controlled by K/B hot-keys
Graphics & Video Module: Intel 915GM(Sharing system memory)
Audio: Sound Blaster compatible
HDD: 80GB IDE HDD
Optical Drive: DVD-Dual Layer
Communication Port:
	Built-in Gigabit Ethernet LAN and Modem Module
	Built-in 802.11b/g WLAN card
	Built-in Bluetooth(Optional)
Card Reader: 4-in-1 Card Reader, SD/MS/MMC/MS Pro

I/O Port:
	-Graphics Card Output (15-pin, D-Sub) x 1
	-USB2.0 Port x 3
	-IEEE 1394 Port x 1
	-Mic-in Port x 1
	-RJ11 Port x 1
	-RJ45 Port x 1
	-Headphone out/ SPDIF out x 1
	-TV-Out x 1 (S-Video)
PC Cards Slot:
	-PCMCIA 2.1 Compliant, Type II x 1
	-PCI Express Card x 1

Everything works under Gutsy!

---

### Post by Clifton396 on 2008-01-26
Version Of Ubuntu: 7.10
Type Of Hardware: Laptop
Hardware Maker: Sony
Hardware Model: PCG-K33

Everything detected and working off a clean install; however, this particular laptop contains the Radeon IGP 345m video chipset which is still not fully supported so there is no Accelerated 3D.

---

### Post by toriam2006 on 2008-01-29
I had a surprise when Gutsy auto recognised a USB audio card, which i bought to try and get my windows-busted laptop sound working.
Please Only List
1)Version Of Ubuntu- 7.10
2)Type Of Hardware- USB Audio out
3)Hardware Maker- Turtle Beach
4)Hardware Model- Micro Audioadvantage (the black one)

It wouldn't work untill I changed some settings in the audio, to usb out.
We don't need no steenkin' drivers!!!!

Also my printers loaded up automatically- HP D1320 and Epson CX1500v

---

### Post by kriket on 2008-01-30
I have loaded UBUNTU 7.10 on to my COMPAQ ARMADA E500 Laptop.
Had to load in SAFE GRAPHICS MODE.
All keys work.
Mouse Pad & Buttons work
USB works
Ethernet works
CD Drive works
Floppy Drive Works

Have not tried anything else yet.
Also hope this is okay as NEW to LINUX. :)

---

### Post by fusionisthefuture on 2008-01-30
ubuntu 6.10 up to 7.10
HP pavillion laptop dv2200 cto
amd turion 2 Ghz
nvidia 6150 go
broadcom 4310 wireless card
soundmax hd audio

6.10 worked alright, Feisty worked well, and Gutsy works awesomely.  
upon clean install gutsy automatically installs correct video card driver, no messing with xorg.conf required.  it also installs sound card perfectly, so that the control buttons for volume work and the headphones jack turns off the speakers when its hot plugged.  
the wireless is a bit tricky.  i have to uninstall network-manager-gnome which is the network applet that tells you what network youre on, and lets you change networks with the gui on the taskbar.  this is no big deal to me becuase theres another different applet you can put on the taskbar that tells you the same thing, and you can change your networks manually by doing
sudo network-admin

i love ubuntu!

---

### Post by Sh@rk on 2008-01-31
I have Ubuntu 7.10 Gusty

CPU: AMD Athlon 64 X2 6000+/5000+ Black Edition
MB: ASUS M2A-VM HDMI BIOS rev. 1603
RAM: 2x1 GB DDR2-800 Dl-Ch OCZ Reaper HPC
GPU: ATi Sapphire HD 2600 XT
HDD: Seagate Barracuda 7200.10 320GB SATA 2 @ IDE Controller from BIOS
WLAN Adaptor: Edimax (Based on RaLink RT61 "RT2600 Chip") 7128G

Able to boot the kernel but the Display Server always falls just after completing the boot and starting the OS, that happened after upgrading the BIOS to the 16xx series.

Ubuntu 7.04 worked after the upgrade but with problems, at least no problems with DisplayServer, LTS Version also worked to me, but it's old!
The problem is with all the Debian-Based Linux, but not with Debian itself!!

---

### Post by websiterepairguys on 2008-01-31
(K)Ubuntu Gutsy 7.10
Motherboard:
ECS GF7100PVT-M3 (Purchased 2008/01/28 at Fryes)
500 GB Seagate PATA-100 hd
2GB Memory 
NVidia nForce 630i/GF7100 on board video/lan/sound

Problems:
Install works fine.
Boots, you can see Kubunut loading screen, the it goes away and text mode comes back.  NVidia graphics driver problem.  Used Envy, installed "latest", boots into Gui, now no sound.  Reboot, no more gui.  Have to use Envy each time i boot.  No good.  Going back to store for an Intel board.

---

### Post by I_ch on 2008-02-01
Hi all.

Ubuntu 7.10 Gutsy amd64 release

Toshiba L40-14f 
**CPU** Intel® Core Duo T2310 1.46Ghz
**RAM** 1024Mb
**HDD**  120Gb SATA
**VIDEO**  	Intel X3100 128Mb
DVD-RW, built-in modem, sound, wifi.

**Out-of-the-box:** almost all except compiz and wlan. 

Please pay attention that my video adapter is officially blacklisted by compiz developers - you may have it to work with some magic, but there will be no ability for video playback with 3d desktop enabled (I can't get it work).

Internet threads says that wlan works as usual, nevertheless I can't get it work properly still (the problem is in my arms, I'm afraid ') I hope that the solution for Intel X3100 Graphics chipset will be available soon...

**Also there are some problems with ACPI (attempts of suspend and hibernation modes causes system hang-ups from time to time)**

---

### Post by Kevbert on 2008-02-02
Acer Travelmate 803Lci laptop installed with Win XP and then Ubuntu 7.10 Gutsy Gibbon 32 bit.
Acer comes with built in wifi, bluetooth, sound on board, built in ATI Radeon 9000 and in based on the Intel Centrino 959 chipset.
Installed Ubuntu with manual partitioning as only way to use two operating systems.
Dual boot works fine.
Complained that battery was faulty or old (still using original).
No other problems noted

---

### Post by froy02 on 2008-02-02
Brother MFC665CW networked Multi-function machine in Gutsy i386 and AMD64.  
It was easy to set up in the 32 bit version of Gutsy. I followed the instructions in the Brother website,[http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)

I had to read the FAQ's for the setup in 64-bit version (am a newbie in Ubuntu but a guru in Dos/Windows).

---

### Post by Herber on 2008-02-03
Linux version: Ubuntu 7.10
Hardware: Dell Inspiron 7000
Ram: 313.3Mb
CPU: Pentium 2 300MHz
Only problems with installation:
      Linksys wireless card required Broadcom 43xx restricted Drivers.   Took a while for me to work that out and I can't use a configured connection (must use an open wireless connection without encryption)
      CD/DVD ROM not reading DVDs, I am working on that now.  If there are any suggestions about the Toshiba SD-C2102 I'd appreciate it.  It will read CD's.

---

### Post by mighty1307 on 2008-02-03
Just changed from SUSE to UBUNTU 7.10! The right decision!
Had SUSE since 9.0 (10.3 is now), but since 9.2 it gets more and more redmond!
2much4me

Hardware:
Asus A7N8X rev 2.0
AMD Athlon XP Mobile CPU (1800MHZ real @ 2400MHz real)
2 x 512 MB PC3200 Siemens DDR
2 x 300GB Samsung IDE HD
Club 3D NVIDIA 6200 VGA card
Siemens 19" CRT MCM 1902
Canon S520 (no driver --> runs as S500)
Brother HL 1050
Hama Keyboard (all Mutimedia Extra Keys work !!!!!!)
Benq DW 1620 DVD-Baker

Full Enhanced 3D desktop, cube and so on; everything perfekt!
Need to find out, how to enable 6CH surround sound, 2CH perfekt.

---

### Post by madverb on 2008-02-04
Ubuntu 7.10

Hardware:
Gigabyte GA-P35-DS4 rev 2.1
Intel E6750
2x1G Kingston Value RAM (KVR800D2N5K2)
200GB Western Digital IDE HDD (WDC WD20 00JB-00K)
160gb Seagate IDE HDD (ST316002)
Gigabyte 8600GT 512MB GDDR2 (NX86T512H)
LG SATA DVD Burner (GH20NS10)

Had problems with the DVD Burner not able to read some DVDs. Same DVDs read fine in Windows XP.
Have a weird problem with the 200GB WD HDD where windows fails to install if the HDD has multiple partitions. Sometimes it won't load into the windows first part of setup. Sometimes I get through that and then get disk read errors or ntloader not found once rebooting after setup files have been copied to the HD. I managed to install Windows by removing all the partitions.
Need to get me some SATA HDD's when I gets money.

---

### Post by zzztownsend on 2008-02-07
Hi folks - a bit of positive feedback.

I just bought a Samsung Colour Laser Printer CLP-350N. (the N suffix indicates that it has a network connection port)

Setup on Ubuntu (7.10 Gutsy) was easy as a postscript printer

1- plug printer into my router
2- add printer in admin-->printing
3- printer found on network
4- install printer using PPD file on disk supplied (smc350.ppd)
job done. seems to produce perfect prints from Firefox, GIMP, Openoffice etc

there is also a proprietry linux driver on the disk, but I didn't bother with this

Only one complaint - doesn't come with either a USB lead or a RJ45 network lead - I had a spare one but it would be very annoying if I hadn't!

Very very relieved that my post here wasn't a cry for help!!!

Take it steady folks
Cheers

Matt

---

### Post by Todaviafrito on 2008-02-09
Xubuntu 7.10
Digital Camera
Rollei
d330m

recognised as mass storage device
no installation needed =D> well done Xubuntu

---

### Post by bandito40 on 2008-02-11
Ubuntu 7.04

HP Deskjet 3550 USB printer

1) Connect your printer. 

2) Install driver via 'sudo apt-get install hplip'. 

3) GO to System > Printing. Let it your printer, then select it from the list.  

4) Test it with the HP-Toolbox by typing hp-toolbox at the shell prompt.  

5) Also try printing a page form something some other program.


If you need more information, refer to this tutoial 
[https://help.ubuntu.com/community/Hp...ntenanceDapper](https://help.ubuntu.com/community/Hp...ntenanceDapper)

Happy printing.


Carl



[http://www.gaihosa.com](http://www.gaihosa.com)

---

### Post by andrewjoy on 2008-02-14
Printer
BrotherHL2030
Works out of the box
Ubuntu 7.10

I will post the rest of my hardware later

---

### Post by foridea on 2008-02-18
> **stig said:**
> Two Brother HL2030 laser printers (monochrome) using Ubuntu 6.06 Dapper, each on a 2.8GHz PC.

I bought one printer about a year ago for the first PC and found it so easy to instal and it worked so well that I have bought the same model printer for a second PC. The HL2030 is 16 pages per minute, 8MB memory, 2400 x 600 dpi and connects via USB 2 cable.

I have just bought the second one from Amazon UK for £60.85 plus VAT (and a USB cable at £2.55 plus VAT).  [Make sure you are buying direct from Amazon and you can use "Supersaver" to get free delivery in the UK.]

I downloaded drivers from the Brother Linux printer driver pages. Instal the LPR driver first from:
[http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)
The method is here:
[http://solutions.brother.com/linux/sol/printer/linux/lpr_install.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_install.html)

Then the CUPS driver from:
[http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html)
The method is here:
[http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install3.html](http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install3.html)

Check in Systems | Administration | Printing to make sure the printer is shown.



Connect the printer to the power and switch on. Connect the USB cable to the PC, then to the printer. Press the "Go" button on the printer to print a test page

Happy printing! :)

thanks man

---

### Post by hackle577 on 2008-02-20
Ubuntu 7.10 (Gutsy)
External Hard Drive
Seagate
FreeAgent Go 160 GB

Comes formatted as NTFS, but can easily be changed to ext3 with GParted or similar tools. Actual capacity is about 6 or 7 GBs less than 160 due to [the way memory is calculated]("http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion"). Also comes with preloaded software, incompatible with Linux, which can be easily erased from the drive.

I've heard several people complain about power issues with the USB ports, but so far I have not experienced this. With just one USB cord plugged in, I backed up my 26 GB home folder with no problems.

---

### Post by benste on 2008-02-23
Printer
HP Deskjet D1360
Works out of the box (HP Lib)
Ubuntu 7.10

---

### Post by Iam138 on 2008-02-29
Ubuntu 7.10 AMD64/i386
Opteron 1212 Dual Core socket AM2 (CPU is recognized as such in both i386 and 64 bit).
Gigabyte GA-M61P-S3 with nVidia MC61P single chipset solution (6150SE/430 integrated graphics).
Samsung Spinpoint SATA II
Amigo AME-CA95 56Kbps External V.92 DATA/FAX/TAM RS232 serial modem.

Everything works flawlessly on install with both AMD64 and i386.

Olympus D-545 ZOOM digital camera.
Creative NX Ultra webcam.

Both work out of the box.

---

### Post by DM was on fire! on 2008-03-07
Ubuntu 6.06.1 LTS (will probably upgrade in a little bit)
I'm unaware of my other hardware, but my new **nVIDIA GeForce 4 MX 4000** video card works out of the box...and after the problems I had with an ATI Radeon 7000, I'm very happy to get a new video card.

However, [StepMania](http://www.stepmania.com) crashes for unknown reasons. It loads, and then just shuts off. :\ I'll yak at the folks there and see if they know a fix for it.

---

### Post by quadrasteer on 2008-03-08
Newbie to Ubuntu 7.10 Gutsy

Laptop 17" Screen
HP DV9743CL
Intel T7250 Dual Core, 2GHz
3 GB Memory, Dual 160GB HD
NVidia 8600 GS video card 512MB

Installed OK, wireless works, no sound though, will work on this:)

---

### Post by ManiDhillon on 2008-03-09
I have Xubuntu 6.06.1 [Dapper Drake] installed on an IBM Thinkpad 600E having 300MHz Intel P2, 192 MB RAM and 6.4 GB HDD.
The builtin track point works perfectly but the PS/2 mouse doesn't work at all.
That same mouse used to work on Zenwalk, Ubuntu 7.10.
Can anyone please help.

---

### Post by kurotenshi on 2008-03-16
Ubuntu 7.10 on Toshiba Satellite A200-1SX
Core2Duo 2.2GHz / 2Gb RAM

All works well except card reader, the external speakers have to be controlled independently of the headphone jack, the multimedia buttons, the dual mode touch pad has only normal mode and the Antheros Wifi only stays connected if the connection doesn't go idle

---

### Post by falkTX on 2008-03-20
Ubuntu Gutsy 7.10
Fujitsu Siemens Computers - Amilo Pa1538

What Works:
 - Battery/AC Power
 - Dual Core Processor
 - NVIDIA G-Force Go 7400 (Works in 16bit colors without drivers, 32bit-512Mb when installed)
 - CD/DVD burning (never tried DVD-RAM)
 - Volume +/-/mute; WiFi On/Off and [Fn] buttons
 - Connection to an external TV and LCD works (only when configured with "NVIDIA Settings Manager"; "Screen and Graphics" always messes up with the resolutions, but my Ubuntu is offline, so not updated)
 - USB connections
 - Card Reader (5 in 1)
 - Speakers
 - Mic/Input

What works (external devices)
 - HardDrive 1TB SATA/USB2
 - Pinnacle DVB-T Device (330e using driver from Video4Linux em28xx)
 - Bluetooth pen disk
 - PS3 SixAxis Joystick
 - ThunderPad Joystick (no vibration/rumble)
 - Logitech Racing Wheel (no vibration/rumble)
 - USB-Keyboard+Mouse
 - HP Deskjet 2450 Color Printer

What I didn't tried yet:
 - SPDIF 5.1 Audio
 - Firewire Connections

All this works except the Brightness +/- button (I use F9 in Compiz-Fusion to change brightness)
(that's all)

---

### Post by Naqash on 2008-03-21
I have acer 5720, 
Intel core 2 Dou T5250
Intel Media acceleator X3100
2 GB DDR2

OS: UBUNTU 7.10

every thing is working fine expect integrated acer crystal eye web cam.

---

### Post by adun07 on 2008-03-21
Processor: AMD Athlon X2 4400+
Motherboard: ASUS M2N-MX SE
   Chipset: NVIDIA GeForce6100 / nForce430 
Memory: 2GB ddr2 800 (dual channel)

Ubuntu 7.10, 7.04, 5.10 (32-bit and 64-bit alike) and openSUSE 10.3 didn't work.

In the versions of 32-bit ubuntu says: 
MP-BIOS bug: 8254 timer not connected to 10-APIC
Kernel Panic-not syncing:
IOAPIC +timer doesn't work!
Boot with apic=debug and send report. Then try booting with the 'noapic' option.

Please help. :cry:

---

### Post by jebasan on 2008-03-22
Version of ubuntu: Ubuntu 8.04 LTS 
Type of hardware: HP Laptop Pavilion Entretainement DV 6629ca 
Intel Centrino 2 Duo core, 2gb ram, 250 hd, dvd w/ ligthscribe cap ..

I have installed [fresh install] Gutsy 7.10 in my computer. Since the instalation, about a month or so ago, i had constant problems with internet connection freezing, system unstable, sound never worked, grafic effects worked once then, died. as for hardware related, everything else but the sound, worked just fine. (webcam, usb's (3), wireless, network jack, memory slots, eireless mouse "microsoft", dvd writer,)HP scanner. 
Ubuntu 0.08LTS
Day one [Mar 21-2008]
>>> just downloaded the 8.04 LTS and im runing from a Live CD. So far only the microhpone is not working. The sound came back to live! and work just fine.(still testing!!) 
Ive installed in a 7GB partition and still have Gutsy 7.10 [dual boot linux,linux!!]
>> Ive just tryed the hardware testing applic. and it frozed in "Mouse testing part". 
>> I have one CPU at 100% @ all times alternating with the other one @ 30% during the first test!(in gutsy 7.10 ive never saw my CPU's @ 100%!) 
>> Memory @ 30% always! 
im keeping opening aplic. so far; gedit, gimp, system monitor, file browsrer, office writer, office spread sheet, mozzila Firefox, hardware testing, 
Switched to desktops, no problems so far! 
The web cam is working with Ekiga.
The ear jacks are working perfect [both] 
so far just the mic is not working.
System has never frozen yet, no metter what ive done so far.

---

### Post by drawmada on 2008-03-22
System Number One

Processor: AMD Sempron 2400+
Motherboard: Foxconn Winfast K7S741GXMG-6L
Chipset: SiS 741GX + 963L
Memory:512 mb ddr 266 
Hard Drive: Western Digital WDC WD800BB-00FJ (80 gb IDE)
Video Card: ATI AIW Radeon AIW Pro (tV not working)
DVD Drive: LG DVD-RAM GSA-4018B
Ubuntu Version: 7.10 for PC Everything works except for TV-IN and OUt capabilities.


System Number Two
Dell Dimension 3100
Processor: Pentium 4 HT 3.06 ghz @ 533 mhz FSB EM64T (64 bit emulation) (Socket 775)
Motherboard Chipset: Intel 915G
Video: Onboard Intel 915GL
Hard Drive:Samsung 160JJ SATA
DVD Drive: DVD-RW ND-3570A
Ubuntu Version: 7.10 64 Bit Edition ... Runs well except for a few hang-ups on Flash player

System Number Three
Hewlett Packard Pavilion a1020n 519j
Processor: Pentium 4 3.06 ghz @ 533 mhz FSB  (Socket 775)
Motherboard: Asus PTGD-LA Goldfish3-GL8E
Video: Onboard 915GL
Hard Drive: Seagate 200 gb SATA
DVD Drive: HP DVD-RW w/ Lightscribe
CD Drive: Asus 48x CDROM
Ubuntu Version: 7.10 for PC ... runs exceptionally well

All three aforementioned computers run their new Operating systems quite well, except for the Dell having hang-ups with flash on Mozilla Firefox.  Other then that ... absolutely no complaints :) (Edit Will be re-installing Ubuntu for PC on Dimension 3100)

---

### Post by fallendarling on 2008-03-23
1) Ubuntu 7.10 Gutsy Gibbon
2) Digital Concepts 21-in-1 Card Reader/Writer
3) Sakar
4) CR-70R, V506

All I had to do was plug in the USB cable, and this thing worked like a charm. I was quite pleasantly surprised. You do not see a desktop icon when you plug in the device, unless there is a memory card already inserted into the card reader -- but this seems to make sense to me.

---

### Post by RebelwithoutaClue on 2008-03-23
IBM T41 Laptop (no bluetooth or native wi-fi)

Ubuntu 7.10 Gutsy Gibbon
Intel Pentium M 1600
768MB RAM
Radeon Mobility 7500
Synaptic trackpoint
+
3Com PCMCIA 3CRPAG175B
DVD/CDRW

Everything worked at install including sound.  Yet to try the mic, but the external sound is fine.

Did need to update totem to play DVD's.

---

### Post by jra007 on 2008-03-23
Recently installed Unbuntu 7.10 on an older machine of mine  with no problems at all.

Gigabyte GA-7ZXE, via KT133a chipset
AMD XP 1800+
768mb Micron PC133 ram
Hitachi 80g IDE hd
Gigabye AGP 4/8x video card GV-R925128DE Radeon9250
Netgear GA311 nic

Not the fastest ride on the block, but everything works.

---

### Post by ztomic on 2008-03-24
1) 7.10 (gutsy)
2) Sound
3) Edirol/Roland
4) UA-700

This is USB sound capture hardware. Capture from microphone and guitar works great and panel effects work. MIDI also works. Effects work in both standard and advanced mode.  have not tested patches. Please read owners manual for exceptions.

---

### Post by Azureskies on 2008-03-25
Version of Ubuntu: 7.10 Gutsy Gibbon
Laptop, Toshiba Satellite A135-S2386
Motherboard/Chipset/Graphics: ATI Radeon Xpress 200M
Memory: 2 x 1GB Samsung
Hard Drive: Toshiba ATA 80GB
Internet: Atheros 5006EG Wireless B/G, RTL8139
Display: Laptop Display 15.4" 1280x800
Optical Drive: TSST (Toshiba) 8x Superdrive. (DVD/RW)
Audio: Realtek High Definition Onboard.

Wireless seems to go of an off, but it seems to be my router's problem. Haven't tested the PCMCIA slot and VGA or S-Video ports yet. Nor have I tried the DVD burner.

---

### Post by thebigbluecan on 2008-03-30
Desktop system:

Ubuntu 7.10 (gutsy) and Ubuntu studio 7.10 (gutsy) works...
Motherboard: PCCHIPS with VIA chipsets ...AGP VERSION....Cant remember model... sorry
CPU: Intel Pentium D 3.0ghz 
Video card: AGP Nvidia GeForce 7800gs BFG version 256mb
Sound Card: Turtlebeach Rivera 7.1.... [COLOR="Red"]SPDIF DOES NOT WORK![/COLOR][COLOR="Black"]Analog does[/COLOR]
Mouse: Logitech G5

---

### Post by imperius69 on 2008-04-01
Ubuntu 7.10 [aka] Gutsy Gibbon on a 

Laptop Acer Aspire 1604LC with
ATI Mobility Radeon 9000
1 giga Ram
40 Giga HD
Cpu Intel P4 2800 MHz

PCMCIA, Keyboard, MousePad, USB, Ethernet, CD/Dvd Drive, Sound, Floppy Drive, Compiz - all Working out the box

Boot as to have "pci=noacpi noapic" as options.

Bugs:
Boot was very long, corrected with changing the usplash screen size.[Solved]

PCMCIA wireless cards have some bug that are corrected with "pci=noacpi" on boot as option.[Solved]

On boot there is an error corrected with "noapic" on boot as option.[Solved]

No video/movie display due to Hardware bug on the ATI wich ACER never corrected with a BIOS update
So the only video/movie compatible drivers are the Catalyst 4.1 (the ones on their site) or below,
anything over that wont show video/movies. (if anyone know some linux drivers based on cat4.1 let me know :p )

Hybernate / Suspende Dont work.

Cant Detect The CPU Temperature Sensor to show on Screen.

Not tested yet:

Microphone and Audio Recording.
Printing and Scanning.

:guitar:

---

### Post by jojopumpkin on 2008-04-02
**_Dell Inspiron 2600_**

**Running:**
Ubuntu 8.04 Beta

**Configuation:**
Bios: **A08** ***this is important**
Intel Celeron 1.2 GHZ
Video/Display Intel 82830 CGC **Must be configured as i810 in xorg.conf**
384MB Ram

**Accessories:**
Netgear 54 Mbps Wireless PC Card WG511 v2 using original windows drivers installed through ndiswrapper
Canon  ZR830 DV Camera using Firewire IEEE1394a Cardbus and RAW1394 from the repository.

This was a bit taxing being relatively green to Linux. I had a hard time finding the proper info in one place to get Ubuntu to show from behind the blank screen. Once I put it all together it took no time at all.

*if you need to downgrade your BIOS you'll need a windows machine then download the driver from [ftp://ftp.dell.com/bios/I2600A08.exe](ftp://ftp.dell.com/bios/I2600A08.exe) , create a boot floppy per instructions provided by the .exe when executed. You can also create a bootable CD that wll emulate your A:/ drive by downloading an .ISO image and using Nero to burn it. Get that [here]("http://www.bay-wolf.com/flashbios.htm"). It should be noted that flashing your BIOS can be tricky so caution should be used in doing so.If you have a floppy handy use that. It's a lot easier.

Info regarding xorg.conf can be found [here]("http://www.apfrod.com/works/2008/03/15/ubuntu_8_04_hardy_heron_on_dell_inspiron_2600").

---

### Post by EyePeaSea on 2008-04-04
**Ubuntu v7.10**

HP / Compaq 8510p Laptop
Radeon 2600HD Video Card
Intel Gb Internal NIC
Bluetooth
WiFi (Broadcom?) - using driver: iwl4965
Dual booting with WinXP SP1
HP Colour LaserJet 4650dn works 100% over the network (haven't tried local printing).
USB tested with a small USB drive - works perfectly.


**_What worked:_**
Basic installation went without issue.
My NTFS Partition (WinXP) was easily and safely resized.  I left it so that the WinXP/Bootloader wasn't overwritten (Grub went directly onto the partition, not the MBR).
Gb NIC works.
Wifi works (see note)
Sound works.
DVD/CD Player works
Bluetooth Works (see note)
Graphics Work (2d, no hw acceleration or 3d)


**_What I had problems with:_**
Sound works fine but not recording.  Haven't looked at this yet, so it may be something simple.

Neither Suspend nor Hibernate appear to work. However, I haven't looked at this in depth and it also may be because I'm dual booting?

**Problems with the Radeon 2600 HD video card.**
This is the single biggest problem I'm having with Ubuntu on this particular laptop.  I just can't seem to get the 3d drivers from ATI (or OpenSource equivalents) to work.  There are so many forum threads and lots of people saying that they've solved their problem,  but either the solutions are quite specific to some hardware (and therefore don't work for me) or I'm just doing something dumb.
The initial problems I had were that my laptop seemed stuck in 1280x1024 (compared to my normal 1680x1050) and I couldn't get the desktop to use some of the better 'Visual Effects' (it was stuck on 'None')
The resolution problem was solved by going into  'System | Administration | Screen and Graphics' and changing the model from 'plug-n-play' to 'LCD Panel 1680x1050'.  I still can't get that actual resolution, but I can now get up to 1400x1050.  I'm guessing that the resolution (no pun intended) to this problem is the video driver - when I get the correct driver installed,  I'll have all the features including the highest resolution that my screen can do.
Essentially, the things I've tried are to select a new graphics card manually (Screen and Graphics), choosing by model, selecting various ATI Radeon options, trying both 'opensource' and 'proprietary'.  Either nothing happens or I get an error and, upon logging back in, it's reset itself to the default (Vesa - Generic VESA-compliant video driver).
I've also downloaded the driver from ATI, followed the instructions and the package then created the Debian/Ubuntu 7.1 specific packages.  I installed them (and that seemed to go ok) but no change - I'm still stuck with the VESA driver.  I get this feeling from some forum posts that I need to remove some of the fglrx (what is that?) drivers,  but Synaptic sees all the dependencies and it suggests that I have to uninstall Gnome and X to remove it all (which kind of defeats the purpose??).


**_Some problems that I had because I'm a noob:_**
Screen Brightness on Battery - I couldn't get the screen to stay 'bright' when on battery.  I right-clicked on the battery icon and selected preferences.  The tabs (AC, Battery, General) are familiar to people from Windows.  There is a slider on the AC page that says display brightness and it's all the way to 100%.  I clicked on the Battery tab, looked for a similar slide bar and saw that it was set to 75% (or something).  I slid the bar to 100% because I wanted it to be 100% (just like the AC setting), but it didn't make the screen any brighter.  Why?  On the AC tab, the slider relates to brightness (100% = max), but on the battery tab, the slider actually means "what %'age should I dim the screen, when on battery".  *If* I'd read the text rather than making an assumption, I wouldn't have got it wrong - so I made a mistake. However, having similar sliders acting in different ways is counter-intuitive and there's no real reason for it.  It's a bit like having a sentence in a book with double negatives;  it can be read correctly and it can make sense, but it does complicate the sentence and adds little value....  I got it wrong (1st and foremost) but the app could be more intuitive.

Wifi - Booted up the laptop without Wifi enabled, and logged in.  I wanted to see if Wifi worked, even if the hardware wasn't enabled when Linux was booting - and it did.  I clicked on the network icon (top right), selected my wifi network, entered the passkey and it connected perfectly.  Next time I rebooted, I got an error about the Gnome Keyring manager - "Enter password for default keyring to unlock.  The application nm-applet wants access to the default keyring, but it is locked.".  I tried my user password and the root password, but had no joy.  I didn't (don't) yet know what the keyring manager is, but assume it's some sort of Password / SSO DB.  After giving up on that prompt (had to click 'Deny'), I had to manually enter the Wifi key again.  And enter it again each time I rebooted...  The fix was to click on the Network Icon (top right), select Manual and then, in the Wireless Connection section, Select 'Enable Roaming mode', select my Wifi network from the drop down box, enter the passkey, select DHCP and then click OK.  The passkey is now remembered.  Clearly, this is what I should have done, but when I wasn't connected to any network, I got a nice easy to understand list of possible networks and clicking on 'my' one and entering the passkey seemed to be the obvious way to connect (it was easy).  Perhaps there should be a 'remember passkey' option?  I'm not sure how this is going to work when I'm in a different location and do want to make an ad-hoc connection to another WiFi provider...

Bluetooth appears to work.  My phone sees my laptop.  However, as Bluetooth on my phone is a bit cranky (with everything) I haven't actually tested transferring files etc.

Rather than clog up this thread, if anyone has any ideas or suggestions, if they are mailed to me (ubuntu [at] lennington.co.uk) then I'll just edit this post and add in the comments.

Also,  if I make any progress myself (miracles may happen) then I'll obviously update this post as well.

---

### Post by flaviocpontes on 2008-04-08
Ubuntu 7.10 (Gutsy)

Ahtlon 64 3000+
Motherboard Abit NF8
Chaintech GeForce 5500
Samsung Syncmaster 940B

Works perfectly al around.

---

### Post by king gary on 2008-04-09
i need to know if my parts will work ubuntu 7.10i've searched the forums 
thermaltake tr2 w007ruc psu
kingston 2gb ddr2 667mhz 
evga e-7050 matx mobo
logitech r-20
motorola sbg900
netgear rangemax wireless router 
thermaltake max orb
western digital my book 500gb

---

### Post by Sportdeck on 2008-04-12
Ubuntu 8.04 Beta
Acer Aspire 5520-5912 Laptop running Vista Home Premium on primary partition.
AMD Athalon 64 X2 Dual-Core Processor, 2GB memory, 160GB HD, NVIDIA GeForce 7000M graphics

Installed 8.04 beta on secondary partition without issue and all functions have worked so far. The graphics card was recognized and installed ok without having to manually search for drivers.  All updates have loaded and installed ok.

I have been a Ubuntu user on my work desktop and my laptop since the 5.0x days, and was disapointed when I got my new laptop and I couldn't get 7.10 to install due to problems with the graphics card not being recognized.  :(  Since I couldn't get the current version to load, I gave the new beta a try, and have been very happy with the results.  :)

Bravo Zulu to the Developers for enabling 1000s of pieces of new hardware to work with my favorite operating system. :KS

---

### Post by Trollslayer on 2008-04-13
I run 7.10 on a X1250 using the restricted driver, it works fine.

---

### Post by Trollslayer on 2008-04-13
HTPC using Abit integrated motherboard

Abit F-I90HD with
Core Duo E6420 dual core 2.3GHz
ATI X1250 graphics with HDMI
Realtek ALC885 sound
Realtek RTL8110 Gbit Ethernet
Silverstone HTPC case with iMon VFD and iPad remote

2GB RAM
1 x 160GB Maxtor SATA (OS)
3 x 500GB Seagate SATA (logical volume)

Mythbuntu 8.04 (Ubuntu 8.04, Gnome, MythTV 2.1)

**Good:**
Video and audio working over HDMI - restricted driver working

**Bad:**
Restricted video driver goes straight to silly line rate in 7.10, intall without it then enable afterwards.
Have to install patch for lirc to use remote pad.
[Fixed] Installed default card selector to enable HDMI audio

---

### Post by Tom--d on 2008-04-13
Ubuntu 7.10

Toshiba A200 Laptop 

Mostely everything Worked 'out of the box' but wireless didn't. It can be eaily fixed through ndiswrapper. 
Graphics is blacklisted but can be taken off and video playback works aswell (have to change some settings)

Sound works...Basically everything works :) 

And a great laptop!

---

### Post by friedbrains on 2008-04-14
hi newb here...

have done a little with RHL before, but just recenlty got Ubuntu

HP-Compaq Presarion V6000 (V6450ee)
Dual Boot  Windows Vista HP (pre-installed 1st) with Ubuntu 7.10
CPU: Intel Core Duo T2450 2.0GHz
RAM: 2GB 
Graphics: Intel 945
Sound Card: Intel 8281G with Conexant sound chip
NIC: Intel PRO 3945 (restricted driver but works great)
HDD: 160GB SATA

So far so good, even with limited Linux knowledge...  :guitar:

---

### Post by IBMX40 on 2008-04-14
Just installed Ubuntu.
Celeron 366
256 Ram (maxed out)
30GB Hd
Wireless was the trick. Hawking Technologies HWC54G (ti chipset)

1. Install from add/remove programs, "windows wireless drivers"
2. Copy driver files to a folder the program can see.
3. Insert card.
4. Start program, it should see the card.
5. Copy driver files to a folder the program can see.
6. Find driver files from program.
7. Set up network manually from program, roaming doesn't work.
8. Reboot with card out.
9. After restart, insert card, wait a few seconds the green activity light will flash with activity.
10. You are ready to go with some really slow internet access. old computer.
11. The net work icon in the top panel will not indicate any type of activity or signal strength.

for some reason the machine will not boot with the card in, no problem just leave it out, boot then put it in and start browsing.

Hope this helps, I don't know how to code and can't understand it, learning disability, so I have to find other ways to get these things to work with Linux.

---

### Post by ruru on 2008-04-15
1)
Xubuntu 7.10 AMD64
Asus ASUS M2N32-SLI DELUXE with built-in Wireless
AMD Athlon X2 6000+
4x 1G Corsair PC2-6400 CL4 RAM (4-4-4-12)
1x Seagate ST 3320620AS Seagate  SATAII/300 320GB
1x Samsung HD160JJ S-ATA II 160GB 7200, 8 MB Cache, NCQ
Sony DVD-RW
(Asus) Nvidia 7300 GS Graphics card
using nvidia driver 169.12

2)
Ubuntu 7.10 AMD64
ASUS M2NPV-VM, S.AM2 NVIDIA Nforce6150+430, mATX (on-board graphics)
AMD Athlon 64 X2 4600+
1x Hitachi 80GB S-ATA2 8MB
2GB DDR2 PC-533 Kingston Kit (KVR533D2N4K2/2G)
Sony NEC AD5170 DVD-ROM
using nv driver

No hardware problems on either of these two machines (except the nvidia drivers are a little erratic - still not happy with overall graphics performance. nv is very stable for me (when glx isn't required)). Ethernet on both fine. Wireless on box 1 worked straight off, but drops connection once in a while - haven't worked out why yet...



3)
Ubuntu 7.10 AMD64 / Mac OSX Leopard (dual-boot)
Apple Macbook (White 2.2GHz - late 2007)

installed fine, ethernet, graphics, video (iSight), all out-of-the-box...but;
no sound
no wireless
no trackpad extras (multi-finger/tapping)
no brighness control
suspend to RAM works fine, but screen is almost black on restore (and no brightness settings!) so the X server needs to be restarted, which kinda defeats the point of suspend...
what works runs well and useable as a dual-boot (useful enough for me to persist!), but until the many driver issues are sorted, definitely not a hardware I would recommend as a primary Ubuntu machine.

---

### Post by suncreative on 2008-04-17
Ubuntu 7.10
HP 530 laptop
Intel Core Duo T2400 1.83GHz &#9553; 2*512 DDR2 PC2-5300 (333 MHz) Samsung &#9553; PRO/Wireless 3945ABG &#9553; 82801G High Definition Audio Controller 

But the wired nic don´t work, only work the wireless.

Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 01)

If anybody can help me please contact me...

[email]sundary@hotmail.com[/email]

---

### Post by darolu on 2008-04-26
Ubuntu 8.04 Hardy Heron
PC Pentium 4 HT @ 2.8Ghz 512MB DDR Pc3200
Dell Dimension 8300
Graphics: ATI Radeon 9550 256MB
Sound: SoundBlaster Audigy 2
Wireless Microsoft Keyboard + Mouse with multimedia functions working.

Works like a charm, COMPIZ FINALLY WORKS WITH ATI RADEON, without moving anything at all; just downloaded CCSM and that's it, new effects are sweet btw.

---

### Post by reeg99 on 2008-04-29
Ubuntu 8.04
IBM ThinkPad R40e
BlueNEXT BN-WD54G Wireless USB Adapter

Very much a Linux newbie I was extremely pleased when this adapter worked straight out of the box. Just plugged it in, the wireless network nm-applet loaded, choose my home wireless network and away we go.

One note: I have only tried this with an unsecured wireless network connection. Not tested with WEP or WPA

---

### Post by roma2 on 2008-04-29
[B]1) Ubuntu 8.04 LTS (Release Version)
2) Lenovo ThinkPad T61
3) IBM/Lenovo
4) Model 6460[/B]

_All hardware detected and works perfectly:_
Intel Core2Duo 2.0Ghz
Intel 4965 802.11 a/b/g/n (iwl4965 driver)
Seagate Barracuda 160gb 5400rpm sata300
Nvidia Quadro NVS 140 M
*(Using proprietary drivers - Installer picked it up and installed everything for me - great job.)*
ThinkPad lights and buttons all get picked up and work great.
*(Exception: The wireless light does not function.)*
DVD+-RW DL drive works perfectly in Hotbay.
Extra battery in Hotbay works fine.
[U]
**Caveats:**[/U]
Switching from spare battery in hotbay to DVD drive works ok. The OS picks up the switch and works fine. Switching from DVD drive to battery locks up the laptop - everytime without fail.

---

### Post by eentonig on 2008-04-30
[B]1) Ubuntu 8.04 LTS (Release Version)
2) HP Pavillion
3) HP
4) DV9540EB[/B]

Hardware:
- LiveCD and initial install give you some very ugly colors. Screen resolution looks ok. Restricted Driver Manager picks up the Nvidia GeForce GPU and proposes to use the drivers. After reboot, screen and colors work perfect. Compiz ok.
- Mousepad/keyboard are ok. Special keys for sound work fine.
- bluetooth, Wired and Wireless are fine out of the box.
- All HP indication lights seem to work fine.

No extensive testing yet.

---

### Post by phlembob on 2008-05-01
Hi,  ASUS A8N5X motherboard, AMD 4800 2.4 MgHz processor, 2G memory, 2 Samsung writemonster CD/DVD w/ laserscribe, Flash memory SD card reader/writer, NVIDIA 6600 video card, onboard LAN, onboard audio, Samsung CLP-300 color laser printer all work fine in Ubuntu 64bit version.  I haven't figured out how to get 4 speaker operation yet, but in stereo fine. :guitar:

---

### Post by Fenris_rising on 2008-05-01
Ubuntu 8.04 Alternate CD
Asus A8V-VM mainboard
Radeon X300 PCIE graphic card
Samsung DVD writemaster
Gigabyte AirCruiser G Desktop Adapter GN-WP01GS (wireless card)
HP1740 LCD monitor

forgot to mention all USB devices ok including my PEAK scalable R/W multi card reader
just found out my wireless is only running at 1Mb/s with the rt61pci driver in HH i
have used ndiswrapper and my driver disk to set it back up, works @54Mb/s now.
All worked out of the box

Fenris

---

### Post by adi_8079 on 2008-05-01
1) Ubuntu 8.04 LTS x86_64
2) Lenovo ThinkPad T61p
3) Lenovo
4) Model: 6459

Hardware:
Processor: Intel Core2Duo 2.5Ghz (T9300)
Wireless:  Intel 4965AGN 802.11a/b/g/n, Bluetooth
HDD:       Hitachi Travelstar 160gb 7200rpm SATA
Memory:    1x2 GB DDR2 SDRAM 667Mhz PC5300
Graphics:  NVIDIA Quadro FX 570M (256MB) (Using proprietary drivers - EnvyNG did a good job ;))
OpticalDr: DVD+-RW RAM DL drive works perfectly.

ThinkPad lights and buttons work well (got the wireless light working after reading [**this**]("https://bugs.launchpad.net/linux/+bug/176090"))
I was not able to get suspend and hibernate to work (this was possible in Ubuntu 7.10).

---

### Post by gfxguy on 2008-05-01
Ubuntu 8.04 (Hardy Heron) LTS Desktop Version, 32bit.
Hardware:
[LIST]
[*]Toshiba Satellite Pro 105A
[*]Video: ATI RC410 (Radeon Xpress 200M)
[*]Audio: SB4x0 HD Audio Controller (rev 01)
[*]Wireless: Atheros AR2413 (rev 01)
[*]Wired: Realtek RTL-8139/8139c/8139c+ (rev 10)
[/LIST]
The great news is everything works without ANY tweaking, right out of the box.  The bad news: upgrading didn't work, it had to be a clean install.  Using 7.10, neither wireless nor audio worked; Thanks for some great work!

---

### Post by mannheim on 2008-05-02
Ubuntu 8.04 (Hardy Heron) LTS, 64bit, with generic kernel.

Hardware:
[LIST]
[*]Dell Precision Workstation T3400
[*]Intel Core 2 Quad Q6700
[*]One SATA drive, no RAID
[*]nvidia Quadro FX 570
[*]SoundBlaster Live 5.1
[*]DVD+-RW TS-H653B
[/LIST]

All installed and worked without problems. I did install the binary nvidia driver 169.12 from nvidia's site, in place of the package from the repositories, because the latter caused "pink or yellow shadows" in compix (a problem reported elsewhere). With the nvidia installer, 3D works well.

---

### Post by markbuntu on 2008-05-03
Ubuntu 8.04 LTS

Hardware:

HP 1330n Media Center
Athlon 64 3800+ 2.4Ghz, 939 socket
ATI Raedon Xpress 200
3GB PC 3200 RAM
AC97 Audio
Realtek 810L 10/100
Epson 925 printer

Install went very easy but had a few small problems. Needed restricted ATI driver to get fglx working. Installed Ubuntu Studio on top and needed to change input and output devices in Jack from default to hw:0,0 ATI IXP AC97 to get MIDI working. 

Got most of the effects in Compiz Fusion working but no cube, so a little dissapointed about that. Tried Envy but no help.

Overall I am very satisfied and glad to be back using Linux again after so many years. Far easier than Linux 1.2 I can tell you that.

---

### Post by captainskyhawk on 2008-05-03
1)Ubuntu 8.04
2)Laptop
3)Dell
4)Inspiron 2650 (with Nvidia Geforce 2 Go 8MB graphics)

Everything seems to work okay -- volume, touchpad (though you need to add the "SHMConfig" line to xorg.conf), though video seems to be dithering, as if it's only showing up in 16-bit instead of 24 (32?) like it used to under 7.10.  No compiz, either, since it seems to be using the opensource "nv" drivers.

---

### Post by Neovos on 2008-05-04
Ubuntu 8.04 (hardy)
ASUS M51Sn Laptop
Intel(R) Core(TM)2 Duo CPU T8300 @ 2.40GHz
4bg Ram (only 3 in use due to 32bit os)
GeForce 9500M GS with 512 MB

Everything worked out of the box except for some special function buttons and sound. The wrong model in "/etc/modprobe.d/alsa-base" was selected by default. Details here: [http://ubuntuforums.org/showthread.php?t=753679](http://ubuntuforums.org/showthread.php?t=753679)

---

### Post by Bram1943 on 2008-05-05
I Use: Ubuntu Hardy Heron
Desktop
Fujistu Siemens
Scaleo Pi2668 (3GB intern)
Works fine and out of the box!:)

---

### Post by tubbygweilo on 2008-05-05
ThinkPad R61e 7650DNG NG1DNUK
Intel® Core 2 Duo T8100 2GB
Graphics X3100
Intel Wireless WiFi Link 4965AGN
Ubuntu 8.04

All works right out of the box, nothing extra required.

---

### Post by margni on 2008-05-05
Laptop:
Dell Latitude D820
Ubuntu 7.10 - Gutsy
Gnome 2.20

Intel Core 2 Duo T7200
3 GB RAM
160 GB SATA Laptop Drive (multi-boot with XP Pro SP2)

nVidia GeForce 7400 (worked after download of driver)

Intel Pro 3945 Wireless -worked out of the box!
BroadCom BCM5752 Ethernet - Worked out of the box!

Intel 82801G Audio Controller - Alsa

Bluetooth works
Multiple media reader worked/recognized my SD Cards
Printer - HP PSC500 (old and reliable) worked
Scanner - Epson 4490 Perfection - worked after adding package from sane
Samba - networks with other XP and Linux here.

I have all the functions of: Network/internet,  Printing/scanning, interop with my other computers...  !!!  What can I say, it works!  All of it worked very well!

---

### Post by zorba_the_greek on 2008-05-07
Motherboard: MSI P6N SLI (works fine with Gutsy Gibbon and Hardy Heron)
VGA: nVidia 7600GT (works fine with Gutsy Gibbon and Hardy Heron, compiz-fusion works perfect but sometimes visual effects change to none and I have to change them back to extra)

---

### Post by rawr215 on 2008-05-08
Installed 8.04 via WUBU (dunno if this effects my current problem but let's keep moving along)

Mobo:Gigabyte GA-P35-DS3l rev 2.0
CPU:E6750 - OK
RAM: 4gb - OK
Sound: Main concern... Doesn't work right off the bat
GPU: Nvidia 8600 gt - due to sound issues, didn't try yet, but it said restricted driver, didn't install/test yet, but i bet it works.

So sound card is an integrated with mobo.  Too lazy to figure it out since i just ran a mile and half.  research it at work tomorrow or something (feel free to fix it for me LOL)

---

### Post by can8dnSix on 2008-05-09
Ubtunu 8.04LTS

Lenovo N100 Laptop
Dual Core Pentium (1.6Ghz)
Everything works perfect, just need to enable the restricted drivers for the wireless.

---

### Post by housam on 2008-05-09
HP Compaq nx7400 Laptop
intel centrino core Due T2500 - 2GHz - 2MB Cash
1 GB RAM
VGA card intel GMA 950 
Hardy ubuntu + kubuntu
wired internet is ok
wireless still need some adjustement to work.( in Gutsy work out of the box)

---

### Post by phread59 on 2008-05-09
Total custom build:

Asus P5N-E SLI
4 gig Patriot 64 bit (2 gig per stick) DDR 2 800 mhz memory
Intel E6750 CPU
XFX 6800 GT (256 meg DDR 3 version)
Seagate 320 gig Sata 2 HD (currently Windows only drive, That'll change)
Seagate 80 gig ATA drive (set as master on primary channel has Grub and  Ubuntu on it)
HP C-5140 all in one printer
HP DVD 1040i burner with lightscribe
Lite on DVD burner
Microsoft 6000 series chordless keyboard and mouse (some custom features do not work, such as keyboard zoom and scroll wheel side switches, haven't tried all the gadgets, but home and back/forward buttons work all important features work fine)
Logitec LX7 chordless mouse
Maxtor one touch4 500 gig external hard drive (USB)
Lynksis generation 1 cable modem hooked up with eternet

Absolutely flawless, worked perfect with 7.10 (32 bit) and firing on all cylinders with 8.04.  It is stable and positively flys with 8.04 (32 bit).  Works just as impresivly with XP Pro 64 bit.  Will add 8.04 64 bit to afformentioned XP drive in the near future.  Good combination of parts.

Mark Shuman

---

### Post by blankphoto on 2008-05-12
Hardy
Laptop
Acer
Aspire 1680

Everything worked Out of box, even the media keys.

---

### Post by fignig on 2008-05-12
1.)  Hardy Heron 8.04

2.)  DFI Infinity NF UltraII-M2 Motherboard. NVIDIA nForce4 Ultra chipset, w/ the AMD2 socket.

3.)  DFI 

4.)  UltraII-M2



jw how to make the sound better, and how to load the sound drivers and maybe that would work? lmk.

---

### Post by glasen on 2008-05-13
Notebook **Dell Latitude D505** - **Ubuntu Version 8.04**

1. WLAN -> Intel Pro Wireless 2200BG : Works out-of-the-box. Driver name "ipw2200".

2. Graphics card -> Intel 855-Chipset. Works out-of-the-box. Without the following modification in xorg.conf, the X-server, when using the "intel"-driver, repeatedly crashes after logging out :

```
Section "Device"
        Identifier      "Intel"
        Busid           "PCI:0:2:0"
        Driver          "intel"
        Option          "AccelMethod" "exa"
        Option          "MigrationHeuristic" "greedy"
        Option          "ExaNoComposite" "true"
        Option          "ForceEnablePipeA" "true"
        Option          "FramebufferCompression" "on"
        Option          "Tiling" "on"
EndSection

```
The "i810"-driver needs the package "i915-resolution" to support the native resolution "1400x1050" of my notebook.

3. Soundcard -> See above chipset. Works out-of-the-box.

4. Bluetooth -> Dell Truemobile 300. Works out-of-the-box. One important tip : Turn on the bluetooth-radio under Windows (Blue light must be on!). Otherwise the dongle does not work correctly under Hardy (The radio is turned off and no connection is possible). 

5. Suspend and Hibernate : Suspend works out-of-the box. No changes are needed. Hibernate fails for me, but because i don't use it, i never tried to fix it.

6. Misc :

- Downgrade BIOS-Version to A09. All above versions (A10 and A11) will corrupt the display under X11.

- Append "hpet=force" to kernel-line in /boot/grub/menu.lst to enable HPET (High Precision Event Timers). This will increase battery life and decrease heat output significantly.

---

### Post by sirzepp on 2008-05-16
1)Ubuntu Hardy Heron 8.04
2)Acer Aspire 1640 WLMi

I listed this computer before with Gutsy.  I wanted to re-list it because Suspend and Hibernate now work flawlessly.  I am no longer jealous of my Mac using friends.

Thanks to all who have been working on these issues for laptop users...your hard work is paying off.

---

### Post by Judge P on 2008-05-17
Dell inspiron 1525 laptop, 8.04 Hardy Heron, HP Photosmart C5180 printer scanner, Belkin wirless G router & wirless G print-server

Laptop came pre-installed with 7.04 Gusty Gibbon from Dell, well done Dell, all worked ok. Upgraded to 8.04 & lost sound this link fixed problem [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound)
Set usb printer up as C5100 printing & scanning ok, set wirless printing using AppSocket 192.168.2.3 port 9100 all ok. Life is good!

---

### Post by sbazin on 2008-05-18
Custom build

Using Ubuntu 8.04

Athlon X2 3800+
Asus A8N-SLI
2x OCZ 512MB DDR2
250MB WD Caviar HDD
Asus EN7300GT Graphics with NVidia 3D drivers
LG DVD Writer
Mitsumi 7-in-1 Card Reader
Antec P-150 Case
Samsung SyncMaster 931bw Monitor
Logitech Cordless Wave KB & Mouse with Keytouch for special keys

All works great out of the box including all features of the A8N-SLI (audio, LAN, etc) no extra configuration needed

---

### Post by VinylPusher on 2008-05-18
Dell M1730

2.2GHz Core 2 Duo
2GB RAM
2 x GeForce 8700GT (SLI-on-a-card config)
Aegia physics PPU
Logitech G15 compatible LCD display
SATA HD


Tested with Ubuntu 7.10, Kubuntu 8.04 + KDE4 and Ubuntu 8.04.

7.10 works flawlessly. Only untested devices are the G15 compatible LCD, built-in webcam and SPDIF audio.

8.04 Kubuntu = network not working via either wired or wireless. Failed to pick up DHCP and failed to transfer data with static IP.

8.04 Ubuntu = wireless network will pick up an IP via DHCP but fails to transfer data. Wireless activity indicator LED fails to light. Network manager fails to hold 'WPA2' setting, reverts to 'WPA' every time. Possibly the reason the link fails.

---

### Post by thelugnut on 2008-05-19
1)Version Of Ubuntu - Hardy 8.04

2)Type Of Hardware - Webcam

3)Hardware Maker - Vimicro

4)Hardware Model - C-91C

This is a product made in China. It works well with Windows XP as well as Ubuntu 8.04.

The web site is [www.vimicro.com](www.vimicro.com)

I could not get it to work at all with Ubuuntu 7.10.

---

### Post by candtalan on 2008-05-19
Hardy 8.04 Ubuntu installed on new Desktop computer from Novatech UK (purchased with no operating system) The mainboard uses integrated on board audio:

Ubuntu 8.04 gives sound out from front jack but NOT from rear panel. Microphones front and back  seem not working.

Motherboard believed to be
MSI P6NGM-FD motherboard
[http://www.msicomputer.com/product/p_spec.asp?model=P6NGM-FD&class=mb](http://www.msicomputer.com/product/p_spec.asp?model=P6NGM-FD&class=mb)
uses motherboard Intel MCP73V Chipset MicroATX for smart audio jack sensing.

 Ubuntu 8.04 gives sound out from front jack but not from rear panel. This is believed to be lack of driver for (jack sensing)
      High Definition 7.1 Azalia Audio
      • Audio codec Realtek 888
      • Compliance with Azalia 1.0 spec
      • Flexible 7.1 Ch. audio with jack sensing

command lspci gives line:
NVIDIA MCP73 high definition audio

the computer is
[http://www.novatech.co.uk/novatech/specpage.html?PC-1147](http://www.novatech.co.uk/novatech/specpage.html?PC-1147)

MSI mainboard believed to be P6NGM Latest Drivers download offers:
[http://global.msi.com.tw/index.php?func=proddesc&prod_no=1330&maincat_no=1&cat2_no=170](http://global.msi.com.tw/index.php?func=proddesc&prod_no=1330&maincat_no=1&cat2_no=170)
(there are some drivers but only windows drivers found here)

realtek offers
[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)
which includes a linux driver
at [http://152.104.125.41/](http://152.104.125.41/)
HD Audio Codec Driver
Linux driver (2.4 or 2.6) 5.03 2008/5/15 4951k
which I tried to use, but I do not know what I am doing mostly and I screwed up, sorry, so I dont know if they might work.

BUG #231926 refers

My immediate solution is to use a separate PCI audio card, and not make use of the on board facility.

---

### Post by CalvinK on 2008-05-19
Toshiba A200
Installation works flawlessly. 
Now hibernate works and sleep also...
Little problem with overhead projector. I shall work on it when I'm not busy. Maybe a flaw of the Nvidia driver. 
My headphone doesn't shut the sound when I plug it. I am trying to connect a Motorola S9 bluetooth headphone.:(

---

### Post by laluz on 2008-05-23
Hi, I have submitted this as an "Ask Slashdot" question. Not sure if it will be published. I use Ubuntu, so I thought this may be also good to ask here.
> 
All the hardware I am using works with Linux. None of it comes with "Linux compatible" stamp on it. The information on compatibility has to be looked up on message boards or specialized web sites.
Why the vendors are afraid of confirming the compatibility?

I have heard that vendors do not want to confirm that their hardware works with Linux because they do not see it economical to offer Linux support line. Linux users market is still too small and the OS is too fractured. Well, if the hardware does work with Linux, why not state it and just let users know, that they may not count with customer support yet? This would be a great help for Linux users already.

I can imagine the main problem here is to legally exclude support while stating compatibility. Wouldn't it be a high time for Linux community to set up a framework legalese to lower the barriers for the vendors?

I am sure this is related to this thread but may still be off-topic. I have not found a suitable forum yet. Should it be deleted, could you please advise per personal message where to post it?

---

### Post by Totempoles on 2008-05-23
Hardy Heron 8.04 
Lenovo ThinkPad
T60p (purchased 4/07)

Installation without trouble with dual-boot with Vista. However, trouble with wireless card Atheros 5418. Could not associate an AP with Windows driver and NDISwrapper nor with Linux-based driver from Madwifi. No joy. Ethernet connection, flawless. System crashed when trying to use substitute for Network Manager--Wicd

Second issue: from sleep, wake would cause computer to enter cycle of reboot and attempted sleep--this was intermittent.

Note: Vista completely unstable on this system forcing downgrade to Windows XP

---

### Post by laluz on 2008-05-23
Hardy Heron
USB Bluetooth Dongle D-Link DBT-122
USB Bluetooth Dongle A-Quip A/BT-1. Although it claims Class 2 transmission power, range is the same as with the D-Link above.
A2DP stereo bluetooth headset naviPlayRemote (Ten, Zeevo)
Connected running kbluetooth as root.

---

### Post by Sense on 2008-05-24
Asus EN9600GT 512MB HDMI (nVdidia Geforce 9600GT) 
Asus M2NPV-VM (Motherboard)
Linksys Wireless-G WMP54G (wireless adapter)

They all three work with Hardy Heron amd64 2.6.24, out of the box.
With earlier versions of Ubuntu the motherboard needs to get its kernel updated. The graphics card isn't tested with older versions, the linksys doesn't work with older kernels.

(NB: The EN9600GT doesn't work with the M2NPV-VM due a lack of compatibility of PCIe2.0 with PCIe 1.0)

---

### Post by silvanus2005 on 2008-05-24
I`m using Kubuntu 8.04 (KDE 3.5.9) on my laptop Toshiba Satellite A110-153. My CPU is Intel Centrino Duo T 2050, 1 Giga RAM, HDD 100 Giga. I`m able to use wireless conection using my device Intel PRO/Wireless 3945 ABG and wired connection through Realtek RTL 8139/810x Family Fast Ethernet NIC. Everything worked out of the box; the only problem I`m having is my scanner, a CanoScan LiDE 90, curently unsupported by SANE.

---

### Post by laluz on 2008-05-24
gutsy gibbon
printer
brother 
HL 2030L 
works with CUPS out of the box.

hardy heron
scanner
Fujitsu 
ScanSnap S500 
all functions out of the box except for the buttons (not tried to configure)

gutsy gibbon
PCMCIA WLAN card
Belkin
F5D6020 ver. 2100


gutsy gibbon
PCMCIA USB 2.0 32Bit CardBus card 
Hama 
49279

---

### Post by crawall on 2008-05-26
> **glasen said:**
> Notebook **Dell Latitude D505** - **Ubuntu Version 8.04**

1. WLAN -> Intel Pro Wireless 2200BG : Works out-of-the-box. Driver name "ipw2200".

2. Graphics card -> Intel 855-Chipset. Works out-of-the-box. Without the following modification in xorg.conf, the X-server, when using the "intel"-driver, repeatedly crashes after logging out :

```
Section "Device"
        Identifier      "Intel"
        Busid           "PCI:0:2:0"
        Driver          "intel"
        Option          "AccelMethod" "exa"
        Option          "MigrationHeuristic" "greedy"
        Option          "ExaNoComposite" "true"
        Option          "ForceEnablePipeA" "true"
        Option          "FramebufferCompression" "on"
        Option          "Tiling" "on"
EndSection

```
The "i810"-driver needs the package "i915-resolution" to support the native resolution "1400x1050" of my notebook.

3. Soundcard -> See above chipset. Works out-of-the-box.

4. Bluetooth -> Dell Truemobile 300. Works out-of-the-box. One important tip : Turn on the bluetooth-radio under Windows (Blue light must be on!). Otherwise the dongle does not work correctly under Hardy (The radio is turned off and no connection is possible). 

5. Suspend and Hibernate : Suspend works out-of-the box. No changes are needed. Hibernate fails for me, but because i don't use it, i never tried to fix it.

6. Misc :

- Downgrade BIOS-Version to A09. All above versions (A10 and A11) will corrupt the display under X11.

- Append "hpet=force" to kernel-line in /boot/grub/menu.lst to enable HPET (High Precision Event Timers). This will increase battery life and decrease heat output significantly.
I'm new to ubuntu so how can i make all those changes to my dell latitude D505?

Any help would be appreciated

---

### Post by mapes12 on 2008-05-27
1. Gutsy Gibbon 7.10
2. Laptop
3. Thinkpad T22 with RAM upgraded to 1GB
4. IBM

Standard spec does not include wireless support. Therefore, I installed a Comtrend RT2500 PCMCIA wireless card.

Everything works just great! No further tinkering around required. :)

---

### Post by Gannon8 on 2008-06-03
Ubuntu version: 8.04
Type Of Hardware: USB Bluetooth Dongle
Hardware Maker: Kensington
Hardware Model: USB Micro Adapter

I don't know if this is the real model name of it. What I do know is that it's the part that goes into the usb port and about 2/3 cm sticking out. No special configuration needed.

---

### Post by wabbalee on 2008-06-04
like to keep it short:

acer laptop travelmate 2480 all works well as far as i know, opengl, wireless (ndiswrapper), 'fn' key combinations. 

using hardy herron

---

### Post by AMD_infinium05 on 2008-06-05
Ubuntu 8.04

**works with:**
[B][COLOR="Red"]AMD Athlon64 X2 5200+
Emaxx NF7050HD-Pro
    - Generic Marvell Yukon ethernet adapter
2gb Corsair XMS2 dual channel
Inno3D 9600GT 512mb 256bits OC
Sounblaster Audigy 2 5.1[/COLOR][/B][COLOR="Yellow"]OKAY!!! WITH THESE[/COLOR]

NOTES:
still figuring out installing Nvidia Supplied drivers, upon installation ubuntu uses the monitors native resolution 1280*1024.

Processor Dual Core is fine... 2 Cores detected
RAM is superb 2gb detected
Sounds are fine,

Harddisks are fine, ubuntu reads windows and other ntfs partitions FINE.

I'll update this post as soon as i see some problems / improvements.

---

### Post by neasteflorin on 2008-06-08
I have an Acer Aspire 5100AWLMI:
Processor  	AMD Turion 64 Mobile Technology TL-48 (2x256KB L2 cache, 2.2GHz)
Memory 	1GB (512/512) DDR2 SDRAM
Hard Drive 	120GB hard drive
Display 	15.4" WXGA (1280 x 800) TFT display, Acer® CrystalBrite Technology
Graphics 	integrated ATI Radeon&#8482; Xpress X200M graphics
Optical Drive 	integrated Super-Multi drive (DVD+R, DVD-R, DVD-RAM)
Communications 	802.11b/g WLAN, 10/100 LAN, V.92 modem
Special Features 	5-in-1 card reader, Acer® OrbiCam camera

Memory Stick support is not implemented, also the Atheros 5007EG wireless card needs to compile special madwifi driver. Microphone for the ALC/Realtek HD chip doesn't work. Pulse Audio doens't work.
Ubuntu 8.04.

---

### Post by mlapaglia on 2008-06-11
Ubuntu 8.04 x64

Gigabyte GA-P35-DS3L motherboard
4GB G.Skill DDR2 memory
nVidia GeForce 8500GT video card
Intel Pentium D Dual Core Processor (1.8GHz)

Everything works OOB perfectly. Computer boots up in 25 seconds.
I've overclocked the FSB to 3.105GHz, and the memory to 886MHz.

Ubuntu absolutely flies on this machine.

---

### Post by confused57 on 2008-06-12
New build, similar to the previous poster:

MB Gigabyte EP35-DS3L
Gskill 2x1 Gb PC8500
Intel E2200 2.2 Ghz Dual core
Lite-On IDE DVD
WD SATAII HD
EVGA 8400GS($25 after rebate)


Everything worked OOB with Hardy 8.04 x32...Linux only box.

---

### Post by heatblazer on 2008-06-16
I`ll add this:
1.Motherboard: Gigabyte GA-P35-DS3R (rev. 2.1) 
2.CPU: Intel Core 2 Duo/45 nm arch./Wolfdale/e8400@3.0 GHz
3.Sys RAM: 2 x 2GB DDR2 800 MHz "Elixir"(dual channeling)
4.Sys RAM: 2 x 1GB DDR2 800 MHz "Elixir"(dual channeling)
5.VGA: ATI x800 XL 512 MB/256 Bit
6.HDD: Seagate Baracuda 80 GB/ 7200 rpm/ 8MB cache
7.HDD: Seagate Baracuda 320 GB/ 7200 rpm/ 16MB cache

---

### Post by sadohert on 2008-06-17
> **klhoard said:**
> Just got a Logitech MX 5000 Laser package for my birthday. . . wireless keyboard and mouse.  So far everything works great!!

Plugged in the bluetooth dongle, installed batteries in the keyboard, charged up the mouse and it all works.  Press the e-mail button, and Evolution pops up.  The media sliders on the side all work.  I'm sure I will soon figure out how to program all of the other keys on the keyboard.

So far, I'm very happy with this package.

Oh yeah,

Ubuntu 7.10
Gateway P4
1GB Ram
Nvidia 6200
250 & 80 GB HD

Hey Buddy... can you (*or anyone else) comment at all on the ability to use the bluetooth dongle for other devices?  I'm thinking of getting this so I can also connect my blackberry over bluetooth to Ubuntu.

Thanks a lot.

Stu

---

### Post by digitall.doc on 2008-06-17
1)Kubuntu 8.04 x64
2)Desktop, 'home-made':
- Motherboard Asus P5K/EPU (P35 chipset)
- Intel Quad Core 6600
- Asus Graphic Card, Nvidia GeForce 8400 GS.
- 4 GB, DDR2 - 800, G-Skill
- SATA Western Digital harddrive
- SATA Asus DVD burner
- LAN on board (Marvell 88E8056 PCIe Gigabit)
- Sound on board (Realtek ALC883 8-channel)

Everything working well with kubuntu 'out-of-the-box'. Well, sound odesn't work from time to time...

---

### Post by bkline on 2008-06-17
HP Slimline s3400f
AMD Athlon 64 X2 dual 5200+ (2.70GHz)
NVIDIA nForce 430 chipset
3GB PC2-6400 DDR2 SDRAM
500GB 7200RPM SATA drive
NVIDIA GeForce 6150 SE graphics (128MB)
10/100BaseT Ethernet
Wireless 802.11b/g
on-board audio

Ubuntu 8.04/i386 (not brave enough yet for the 64-bit)
All updates current

First attempt didn't get past pressing Enter to start the install process: just hung there with a black screen and a cursor blinking in the upper left corner.  I tried falling back on upgrading my current Windows XP workstation to Ubuntu and using the new machine as my Windows system, but that would have boxed me into the corner of having to use the Vista that came installed on the machine instead of XP, and besides, things weren't working well in Windows, either.

So after a couple of days going back and forth with HP support, I decided the machine must be a lemon.  Took it back to the store, swapped it for another of the same model and started over.  Smoothest installation of any operating system I've ever installed.  Graphics came right up into the monitor's native 1920x1200, sound worked perfectly, wireless worked without any hand-holding whatsover (other than plugging in the WEP key), DVD burner worked flawlessly.  Wireless has a little hum if the sound is turned up, but I don't plan to use the wireless on this system anyway.  One moment of panic came when I looked at the output from `cat /proc/cpuinfo` which gave bogomips of only 2000 per CPU (running at 1GHz) but with a little research I found that this is just the energy saving feature preventing the system from using more juice than is necessary when you're not asking it to do any real work.

In short, looks like a success story after the first couple of days.  (I do wish I had the 4GB of memory they accidentally installed in the first machine, but maybe that was part of the problem.)

---

### Post by jenny_thinkpad_t61p on 2008-06-18
Ubuntu Hardy Heron 8.04 (amd64)

Lenovo Thinkpad T61P type 6457-BQG

Intel Core 2 Duo (Penryn) 2.6ghz - WORKING both CPU cores / Power Management.
4gb RAM - WORKING with amd64 install.
200gb Full Disk Encryption HDD - WORKING

Windows Vista 32bit Ulitmate pre-install - WORKING /PART - Re-sizing vista works from within Vista BUT still takes up 100gb disk space + ThinkVantage Utility Partition. - Wiping Vista and Thinkvantage off altogether works the best! :twisted:Vista will only use 3gb ram.

NVidia Quadro FX 570m - WORKING / Propriatory Drivers Optimal - Doing an install with VESA driver selected will work, the packaged nv driver will not start. After getting the machine running with VESA driver running the ENVY application will install the Nvidia drivers and will work. The VESA driver will not support compiz-fusion but the Nvida propriatory driver works great.:popcorn:

Screen 15.4" WUXGA - WORKING, screen is excellent and works fine, though changing the brightness in the bios is recommended as it is dull.

Intel 4965agn WORKING / Part -Works fine from DVD install, software update seems to fix regular disconnection issue but disables LED indicator.

Modem - UNKNOWN / Probably broken.

Ethernet - WORKING out of the box (tested at 100mbps)

Soundcard - WORKING out of the box

Fingerprint reader - WORKING / Part (supposed) search for THINKFINGER, seems to only use one fingerprint rather than multi-finger enroll in vista. Also crashed my machine badly.

Touchpad etc, WORKING fine, both red "nipple" and Touchpad, right side of touchpad scrolls vertically, buttons fine.

DVD - WORKING - seems to prefer +RW's not -RW's

Buttons - Volume WORKING fine. Thinkvantage - Broken Function Keys [LOCK] works [Battery] Display battery info, [SLEEP] works - see below, [RADIO] operates bluetooth, upsets sound, [SCREEN] external monitor not working from O/S only on hard boot from bios [brightness and Keyboard light] Working [others] working.

Suspend / Hibernate - Was working out of the BOX but I broke it, therefore it depends on the software installed. 

PCMCIA / CARDBUS - UNKOWN wouldn't recognise my PCMCIA modem, but probably not the busses fault.

USB - WORKING / Firewire - Unknown 

Battery life - Not Great, if you need longer life buy 2 :biggrin:

seriously use powertop to sort out your apps and you can enable powersaving of the wireless card, subscribe to linux-thinkpad for more info.

Accessories

Virgin Media (uk) - If you subscribe you might not be able to complete the registration that you get as soon as you fire up the web browser. If this happens call them and tell THEM to complete the registration online because there servers are crap and don't want to support linux. They will say that Linux is not supported and that it won't work or some b/s, tell them your not paying for the phonecall and ask for the manager, when you find someone who knows what their doing it will be sorted.

Samsung CLP-300n - WORKING / Part out of the box. USB operation is flawless. When using with X-sane text may appear too dark / large. Network functionality seems a misnomer.

Cannon Lide 25 - WORKING out of the box with Xsane.

---

### Post by venglisch on 2008-06-20
Gateway MX3225 Notebook
-----------------------
Intel Celeron M Processor 370
Via VN800 chipset
512 MB DDR2 SODIMM 533 MHz
60GB 4200 RPM hard drive 
S3 UniChrome Pro integrated graphics processor
10/100 Mbps built-in Ethernet
802.11g integrated Wireless
56K ITU V.92 ready Fax/Modem (RJ-11 port) 
AC '97 2.3 Compliant audio 

I initially started Ubuntu 8.04 (Hardy) on this machine as a live CD and did install directly from the live CD but I had problems with
- the audio (no sound)
- the wireless
- the display (the desktop didn't fit on the display and there were about 10-15% of real estate missing to the right and bottom.

I got wireless working when using a PCI card but I couldn't get the integrated wireless to work.

After a while banging my head I re-installed Ubuntu, this time without going though the live CD but using the second option on the DVD to install Ubuntu - et voila, the graphics what recognized. 

The audio worked after pushing a couple of buttons in the Alsa mixer.
The external wireless (Linksys 802.11g PCI) worked right away after installing the driver.
The internal wireless worked after using the patch and instructions from 
   [http://willdaniels.co.uk/articles/howto-guides/10-howto/12-r8180-hardy](http://willdaniels.co.uk/articles/howto-guides/10-howto/12-r8180-hardy)
The graphics worked but only at a resolution of 800x600.  By using the vesa driver and selecting a resolution of 1280x768 though, this problem was resolved as well.

---

### Post by wpshooter on 2008-06-24
**HOW** can they label this thread as a "hardware compatibility **LISTING**", when the only way that you could possibly find if a particular piece of hardware is compatible with Ubuntu, is to read EVERY word in over 250 different posts ?  

And even then, I am not sure that you would have a definitive answer !!!

If someone wants to make an actual LISTING, only then should they label that thread as a **listing**.

Thanks.

---

### Post by benste on 2008-06-25
why can't we collext all inputs as adatabase seperated into GPU WLAN Input ...

like [http://www.openprinting.org/printer_list.cgi?make=Anyone]("http://www.openprinting.org/printer_list.cgi?make=Anyone")

There you would be able to search as fast as possible for vendor and product name

---

### Post by confused57 on 2008-06-25
Also, this link on Herman's site may be helpful:
[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

---

### Post by benste on 2008-06-25
a litle bit to complicated or?

---

### Post by mgame2k on 2008-06-26
Ubunutu currently 7.10
Will be upgrading to 8.04 64bit in the near future

Yes I will be using more than 3Gb of RAM.

My question is this.
Will my new nvidia 8600GT and a Creative Sound blaster Audigy SE 7.1 be autodetected and installed for me?

---

### Post by benste on 2008-06-26
confused57 you're "addicted to ubuntu"
do you have enough time to create a website - database where we alll can collcet these infos?

Or would someone like that I'll start to work on such a database as freetimefun? 

the DB should be official integrated into UF otherwise no one would care about it or?

---

### Post by StumpyMcDonut on 2008-06-26
Ubuntu 8.04 (Hardy)
Gigabyte P35-DS4 mobo
(Inno3d) Nvidia 8800gts 512 (G92) - works perfectly with everything although the linux performance is slower than I'd like, especially when gaming, and certain compiz effects seem to run horribly slow
Core 2 Duo e6750 (2.66ghz, works fine with the rt kernel overclocked)
OCZ RAM - 800mhz (4gb) (Cant remember the exact product name :S)
Samsung Spinpoint 500gb HDD (again, cant remember exact name)
The CD/DVD drive is DVD-RAM, I bought it as cheaply as possible so I'm not even sure what it is (no branding)


Samsung syncmaster 226bw monitor



Somewhere you can search for your hardware and see its compatibility would be brilliant

---

### Post by sop408 on 2008-06-27
Hardy 8.04 + Dell Inspiron 2650 Laptop

It works fine, and Hardy seems to detect pretty much most of hardwares in the laptop.
but, i think there is a problem if you enable the graphic card which is nvidia.

---

### Post by benste on 2008-06-27
Which grafic card do you own? - did you try envy to install the driver?
- the restricted module manager doesn't detect nvidia cards in 19 kernel

---

### Post by d_skillz on 2008-06-27
Sony Vaio vgn-n325e works fine out of the box. Every thing supported except the foll.
I am a new Linux user, Used to mess around the various distros, knoppix, redhat & mandrake. Using Pcs for 22 years from MSDOS & Win 3.1. I have just been using Ubuntu 8.04 Hard Herron for 2 weeks now on my Sony vaio vgn-n325e laptop and I have serious acpi problems. Machine wont shutdown without hard power-off, restarts fine, cant see battery state or ac adapter states. Please help, I have completely formatted vista, I am so impressed with the system responsiveness but need full laptop compatibility.

---

### Post by benste on 2008-06-28
Sadly we can't give you full functionality FN keys normally won't work.

---

### Post by dboes on 2008-06-28
Ubuntu 8.04 Hardy Heron
Webcam Trust WB 3500T

lsusb
Bus 005 Device 004: ID 04a9:221c Canon, Inc. 
Bus 005 Device 003: ID 0d49:3200 Maxtor 
Bus 005 Device 002: ID 2770:930c NHJ, Ltd      (this is the webcam)
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 03f0:0004 Hewlett-Packard DeskJet 895c
Bus 001 Device 001: ID 0000:0000  

lsmod | grep videodev

this command returns nothing.
But the light on the webcam goes on.
After that again nothing
No image in Camorama or Ekiga and so on.

Someone that have installed this particular webcam or webcam with simular hardware id?

Please tell how.

Tnks

---

### Post by ruminant1 on 2008-06-29
mythbuntu 8.04
Gigabyte ga-ma78gm-s2h motherboard
   Onboard ATI Radeon HD3200HD graphics
   Onboard Realtek ALC889a sound
   Onboard Realtek 8111C gigabit LAN
Athlon X2 5400+ processor
SUPER TALENT INT-AIN1-C All-in-one USB 2.0 Card Reader
Samsung SH-S203N DVD burner
Avermedia A180 tuner card
Microsoft Media Center Keyboard

Overall, worked great out of the box with standard install (nice work folks!)  I even got a friend to build a system based on this mobo and he got it up and running without ever having touched a linux box.  XVideo, Gigabit LAN, sound over SPDIF and analog, media card reader; you name it and it works.  There has been some grumbling about sound over hdmi, but I've never tried it.

The tuner card and keyboard require a little work to get running, which must be repeated when a new kernel is released, but it's otherwise been a relatively easy box to keep running.  (Is there any plan to pull lirc_mod_mce into the standard distro?  You already support the remote)

The video is pretty good.  I have XVideo running and I've watched HD programming with no problem.  Well, one problem: there is some tearing.  I tried the newest ATI drivers and the tearing is gone in GL, but still not in XV.  They caused all kinds of other headaches, however (looks like some sort of buffer issue - the screen sometimes doesn't redraw correctly when you move stuff) so I'm back to whatever's supported (partimage rocks!).

I currently give the box an "A" that will be changed to an "A+" when ATI gets their drivers worked out.

---

### Post by GriZzlEnLS on 2008-06-30
3 of 3 Computers working great with 8.04 Ubuntu (1 with 64bit other 2 with 32bit)

Frist "Frankie" 64bit (Dual boot w/Vista Home Premium 64bit)
Gigabyte GA-EP35-DS3R Motherboard
Intel E4300 @ 3.06 1360 FSB (Overclocked)
6GB @ 850MHz 4-4-4-12 RAM
EVGA Nvidia 8800GT 512mb
1 160GB & 250GB HDD
On board soundcard
On board NIC


Second Dell XPS 410 32bit (Dual boot w/Vista Home Premium 32bit)
Intel/Dell P35 chipset Motherboard
Intel E4700 @ 2.40 GHz
3GB @ 667MHz RAM
EVGA Nvidia 8600GT 512mb
2 250GB HDD
On board soundcard
On board NIC


Third Gateway MT3423 (Laptop) 32bit
Nvidia Chipset Motherboard
AMD Turion 64 X2 TL-56 @ 1.80GHz
2GB @ 667MHz RAM
Nvidia Go 6100 128mb
1 160GB HDD

---

### Post by cn23 on 2008-07-02
Dell Inspiron 8600
Ubuntu 8.04 
Intel Pentium M Processor 1.4Ghz
1 GB Ram
Nvidia GeForce Go 5200 64 MB
80GB HD (Hitachi)

---

### Post by cptasker on 2008-07-04
Ubuntu 8.04
Sony Vaio VGN N11M

Intel centrino core duo 1.60ghz/512 MB ram/80gb hdd/802.11 wlan Atheros wireless/Intel GMA 950 graphics

Worked straight off the cd, no problems whatsoever!

I can plug my Nokia in (Nokia PC suite is windows/mac only) using the usb lead and access all the files on the memory card with no trouble

Wireless worked straight away, just had to configure modem (Linksys) took about 2 hours to be fully operational from putting in the disc!
:)

---

### Post by abhilashkumar on 2008-07-07
1)Version Of Ubuntu: 8.04 LTS

2)Type Of Hardware: Laptop

3)Hardware Maker: Acer

4)Hardware Model: Aspire 4520

Everything except wifi worked out of the box. wifi working with ndiswrapper 1.52

---

### Post by loza on 2008-07-07
Toshiba Satellite Pro L-10 laptop (I upgraded RAM to 1GB) initially ran 7.04 and upgraded through to 7.10 and now 8.04. 

The only thing that has stopped working on the laptop itself is the Fn key to control the speaker sound. I first noticed this when upgrading from 7.10 to 8.04.

Peripherals I use on this laptop that work are:

Transcend SD and SDHC cards with no problems being read through a Bytestore Multi Card Reader.
Sandisk Curzer 1Gb pen drive - recognized ok
Corsair Flash Voyager pen drive - recognized ok
HPdvd1040 external DVD RW drive - Got this new when I was running 7.10 and it was only recognized as a CDROM drive. However I upgraded to 8.04 and that seem to fix the problem now - fully working.
Samsung CLX-2160 MFP colour laser printer - the scanner stopped working when I upgraded to 8.04. However after the help from the good people here its now working. [COLOR="Blue"]_[**[COLOR="Blue"]Here's how[/COLOR]**]("http://http://ubuntuforums.org/showpost.php?p=4776310&postcount=114")_[/COLOR]
Garmin Nuvi 760 GPS - recognized fine
Sony Erricson W880i - recognized fine
Wacom Wide A3 Graphics Tablet - works fine after following this [**_[COLOR="Blue"]How To[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=765915&highlight=wacom")


Also have Studio 8.04 on a Shuttle G40 with 2Gb RAM and can use all the above peripherals with this PC too with any problems.

---

### Post by Qinjuehang on 2008-07-09
Intel Q9300 (speedstep does not work out of the box, still working on it)
Intel High Definition Audio
Intel P35 Chipset
Realtek 8111C ethernet (slow, but works)
Leadtek Winfast PX9600GT (Nvidia 9600GT graphics Card)

Ubuntu Studio 8.04 x86_64 Dual booted with Windows Vista Home Premium.

---

### Post by mwgnz on 2008-07-12
Ubuntu 8.04 AMD64

Hardware:
Intel Q6600 CPU | Asus P5Q Pro M/B | XFX 9600GT | Samsung SATA DVDRW (AHCI) | WD 640GB SATA II (AHCI) | 4GB G.Skill RAM Dual-channel 

So far everything works. The only thing I had to do was compile the Aetheros NIC driver as per this thread:

[http://ubuntuforums.org/showthread.php?t=770173&highlight=P5Q]("http://ubuntuforums.org/showthread.php?t=770173&highlight=P5Q")

Installed the NVIDIA drivers and everything seems to be fine.

M

---

### Post by Niggle on 2008-07-12
Ubuntu Hardy Heron 8.04
Desktop system from Novatech
Model: ISys EX
[http://www.novatech.co.uk/novatech/range.html?t=pc&c=home&r=ISX]("http://www.novatech.co.uk/novatech/range.html?t=pc&c=home&r=ISX")

Motherboard: Foxconn M7VMX-K
Chipset: nvidia GeForce 7050 / nForce 610i
Graphics: NVIDIA 8400GS 256MB PCI-E

Purchased without OS. Hardy install went perfectly. Everything seems to work.
Haven't tested the LAN port since I'm using a wireless card, but it was recognised correctly.
Only minor thing so far is that after installing the (restricted) nvidia drivers, it no longer recognised my monitor (Iiyama S900MT1 CRT) so defaults to 1280x1024 rather than 1600x1200.
(edit an hour later) - Installing the "NVIDIA X Server Settings" package from the "System Tools" section of "Add/Remove" allowed me to select the correct resolution.

---

### Post by styrofoam cup on 2008-07-14
Worked straight away without any problem. is using WPA2 also.

Ubuntu 8.04 Hardy Heron i386
PCI Wireless Card
D Link
DWL G520

Printed on the box...
HW ver : 4B
FW ver : 4.40

Printed on the card...
AWL G520EU.B4G

ubuntu rocks
:guitar:

---

### Post by tulasidk on 2008-07-15
Is Sony laptop suitable for gaming and software development? Is this laptop suitable for me or not? My budget is around Rs 40000 to Rs 50000. Please suggest me?
------------------
tulsidk

[Guaranteed ROI](http://www.inspire-itsolutions.com)
[Viral Marketing](http://www.inspire-itsolutions.com)
[Social Media Marketing](http://www.inspire-itsolutions.com)
[Search Engine Submissions](http://www.inspire-itsolutions.com)
[Email Marketing](http://www.inspire-itsolutions.com)
[Search Engine Marketing](http://www.inspire-itsolutions.com)
[Search Engine Optimization](http://www.inspire-itsolutions.com)

[Inspire Internet Marketing](http://www.inspire-itsolutions.com)

---

### Post by Casper Hansen on 2008-07-16
Home buld computer system:

Ubuntu Hardy Heron

CPU: AMD Athlon64 X2 4000+
Mobo: ASRock ALIVENF6G-VSTA AM2 1000FSB
Graphics: Asus EN8600GT/SI/HTDP/256, PCI-E
HDD: Seagate 7200.10 320GB, 16MB, SATAII
Case: shg Case DeZen2, Black/Silver, 350Watt
RAM: Corsair Twin2X2048-5400C4, 4x1024MB

Printer/scanner:

HP Deskjet F2180

Everything works out of the box.

---

### Post by grss1982 on 2008-07-18
Ubuntu 8.04.1 (32-bit)

AMD Athlon64 X2 4000+
2GB Corsair Value Select DDR2 533Mhz (2x1GB)
256MB Inno3D Geforce 7300GT DDR3 (PCI-E)
MSI K9N Neo-F V3 (MS-7369) LINK: [http://www.msicomputer.com/product/p_spec.asp?model=K9N_Neo-F_V3](http://www.msicomputer.com/product/p_spec.asp?model=K9N_Neo-F_V3)
80GB Western Digital SATA HDD + 250GB Western Digital SATA HDD
LG Combo Drive (DVD-ROM/CD-RW)[IDE]

NOTES:
* Everything works, although USB data transfer speeds are kinda slow.  As noted in this thread: [http://ubuntuforums.org/showthread.php?p=5396406](http://ubuntuforums.org/showthread.php?p=5396406)

* AMD Cool N' Quiet works without any tweaking.

* Installed Nvidia Drivers (Version 173.14.05) through ENVY.

* I use Skype, and on this workstation I'm happy to report that the built-in sound card (input & output) works.

---

### Post by bhadotia on 2008-07-19
Ubuntu Hardy Heron

Hp 530 notebook:
CPU:Intel Core Duo 1.66 GHz
RAM:1 GB RAM
Ethernet card:Intel 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
Chipset (graphics):Intel Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
HDD:TOSHIBA MK8037GS 80GB
Wireless card:Intel PRO/Wireless 3945 abg
Audio:Conexant HDA sound card (mono speaker)


Everything works OOB . The only (minor) problem is that the LED indicating wireless does not work.

---

### Post by SeanCondon on 2008-07-20
Ubuntu Hardy Heron

Lenovo ThinkPad X61 Laptop 7675-7KU
4GB RAM
120GB HDD

Works very well OOTB. Wirless, Bluetooth, external monitor at 1680x1050, volume & brightness controls, suspend, hibernate, usb functions. Ubuntu is far better at recognizing this hardware, than OpenSuSE 10.3 had been. Well done Ubuntu team. 

P.S. WLAN LED does not illuminate, but this is not an issue for me.

---

### Post by razorfistman132 on 2008-07-20
I am using the Newest Ubuntu Available at the moment.

I am running an old Gateway GP6-350, and the CD-ROM will not load the CD's that are Put into drive. This Problem started just after Ubuntu v.7.10 Install.

Now the CD-ROM will not load any cd's. I tried to reinstall Ubuntu, but the Ubuntu v.8.04 won't allow the disk to be read. 

Please Help.

---

### Post by grss1982 on 2008-07-21
**Ubuntu 8.04.1 (32-bit)**

Intel Celeron D 3.06Ghz (533 FSB)
1GB Hynix DDR400 (1x1GB)
64MB Geforce MX-4000 (AGP)
AsRock 775i65gv LINK: [http://www.asrock.com/mb/overview.asp?Model=775i65gv](http://www.asrock.com/mb/overview.asp?Model=775i65gv)
200GB Western Digital SATA HDD + 160GB Seagate PATA HDD + 120GB Seagate PATA HDD
Unbranded DVD-RW[IDE]

NOTES:

* Installed Nvidia Drivers through ENVY.

* User uses Skype, and on this workstation I'm happy to report that the built-in sound card (input & output) works.

* USB VOIP Phone (**Description:** CyberPhone K **Model:** v652skMLR) in conjunction with Skype works flawlessly in this setup.


**Ubuntu 6.06.1 (32-Bit)**

30+ Units of:
Intel Celeron D 3.06Ghz (533 FSB) or Intel Celeron 420 (1.6 Ghz & 800FSB)
1GB Hynix DDR400 (1x1GB)
64MB ASUS Geforce MX-4000 or 64MB Inno3D Geforce MX-440 or 64MB Inno3D GeForce MX-400 or 256MB Geforce FX-5500 (ALL AGP)
AsRock 775i65gv LINK: [http://www.asrock.com/mb/overview.asp?Model=775i65gv](http://www.asrock.com/mb/overview.asp?Model=775i65gv)
80GB Seagate/Hitachi PATA HDD
Samsung/LG/Asus/Sony Combo Drive (CD-RW/DVD-ROM)[IDE]

NOTES:

* Only one system was installed with Ubuntu.  After that one system had Ubuntu installed on it the rest of the units were cloned using the **dd rescue** option in **Ghost 4 Linux**.  No problems were encountered in the cloning process.

* Installed Nvidia Drivers through Automatix2.

* Users use Skype, and on these workstation I'm happy to report that the built-in sound card (input & output) works.

---

### Post by odysseusjak on 2008-07-21
**_Ubuntu 8.04.1_**

Gateway M-6843

*  Intel Core2 Duo Mobile T5750 @ 2GHz
*  Intel® GM965 chipset
*  Intel® PRO/Wireless 3945 network connection (802.11a/b/g)
*  3GB PC2-5300 DDR2
*  Multiformat DVD±RW/CD-RW
*  15.4" WXGA TFT-LCD @ 1280 x 800 resolution
*  160GB Serial ATA hard drive (5400 rpm)
*  Intel® Graphics Media Accelerator X3100 with up to 384MB video memory *  Intel high-definition audio (2-channel support)
*  Built-in 1.3-megapixel webcam
*  5-in-1 digital media manager
*  3 high-speed USB 2.0 ports
*  ExpressCard/54
*  10/100 Mbps Ethernet LAN with RJ-45 connector
*  V.92 high-speed modem

---

### Post by Rhythmdvl on 2008-07-21
[list]
[*]Ubuntu Server 8.04.1, with the Desktop version overlayed afterwards (via sudo apt-get install ubuntu-desktop)
[*]Asus P3B-F
[*]Pentium III 550 (Katmai)
[*]3dFX Voodoo 3500 in the AGP slot (both VGA and S-Video work)
[*]2 X 256 DIMMS (can’t remember the vendor)
[*]SoundBlaster Live! Value (EMU10k1)
[*]Generic Sony DVD player (worked for install of the CD, have not tried a DVD in it)
[*]PCI0680 Ultra ATA-133 Host Controller (HD is plugged in here, not the EIDE port on the board)
[*]Western Digital Caviar 80 GB drive (WD800JB-00CR)
[*]National Semiconductor MacPhyter Ethernet Card 
[*]USB ports have read various flash drives
[/list]

NOTES:
This is my first Linux box, built out of old components. It seem to be working fine (SAMBA file serving, Apache, MySQL serving, MyPHPAdmin), but being a noob, I can’t say if I’ve overlooked a test or something is not working right. 

All parts have been stored in a basement for several years – no changes to them have been made (i.e., still the same CMOS battery). They are all circa 1999-2000. I have updated Ubuntu, but no individual drivers.

---

### Post by WestCoast on 2008-07-24
Ubuntu 7.10 - the Gutsy Gibbon
PRINTER
Hewlett Packard
(HP) DJD 4260

Printer only (no fax, scan, or copy)
Prints Color and Black/White
Connection:  USB
Ink cartridges: 2 (single black, single color combo) cost approx $30.00
Install:  Put in ink cartridges and paper,  
          Plug in power cord. 
          Turn printer on. Let printer configure itself. 
          Connect USB cord. 

 Setup: Open the Printer Configuration Window: System -> Administration -> Printing
          Select:  New Printer  
          Enter devise URI as:  HP DJD 4260  (press Forward)
          Select Printer from Database:  HP  (forward)
    
          At the New Printer configuration window
          Select 
                MODEL: Deskjet D4200  
                Drivers: HP Deskjet D4200 Foomatic/hpijs (recommended)
                (Forward)
          Printer Name:  (should fill in automatically)
          Description:  HP DJD 4260
          Printer Location:  Anywhere 
                 Note: Location must have an entry.  It cannot be left blank.
           Click Apply.  

Once the system has finished configuring use the Policies, Access Control, Printer and Job Options tabs in the Printer Configuration Window to set personal preferences for printer policy, user sharing, paper type, print quality, and job control.  Other than selecting printer sharing, paper type, print quality I used the default settings in this area.

To test the installation click on the Settings tab:  
         Select: Print Test Page.  Print Self-Test Page and/or Clean Print Heads.


This little printer works GREAT!  Couldn't beat the $39.00 sale cost either. I think the regular price was around 59 to 69 dollars.

Note:  Couldn't get my $400.00 All-in-One Lexmark to work.  Couldn't get my near $200.00 All-in-One Brother to work.  Couldn't get my $50.00 Dell to work.  But this little $39.00 HP DJD 4260 works like a charm, has a good print, and installed without a hitch.

---

### Post by ymo on 2008-07-26
Ubuntu 8.04.1 Desktop
AOpen XC-Cube EZ18
AMD Sempron 2300+ (Socket A)
SAMSUNG SP1203N
LITE-ON  DVDRW SHW-1635S
ASUS ATI 9600XT
AOC 2216Vw 1680x1050 LCD
HP LJ5L on SMC 4103P server

Only installed Ubuntu on it a few days ago (replacing Fedora Core 6 and Windows XP Pro). So far the only problem is resuming from hibernation - error message in bottom right of screen and windows have "noise" surrounding them. Hibernation under Fedora and XP worked fine.

---

### Post by markbuntu on 2008-07-26
Ubuntu Hardy

SIIG Serial ATA PCI card

works OOB. You may have to move it to a different slot if you have a problem at first.

If you need some more SATA plugs this will work for you. I got about 200mbs transfer rate. A little slow but plenty fast for transferring files from my old windoze drive.

---

### Post by c2olen on 2008-07-28
Ubuntu 08.04 on Notebook AMILO Si 2636
vendor: FUJITSU SIEMENS

Intel(R) Core(TM)2 Duo CPU     T7250
2 x 1024MB SODIMM (up to 2 x 2048MB)
Intel X3100 Graphics (128MB shared)
Intel 965 chipset
Sil 3531 [SATALink/SATARaid] Serial ATA Controller
SATA Disk 250GB WDC WD2500BEVS-2
MATSHITA DVD-RAM UJ-875S (Writer)
82801H (ICH8 Family) HD Audio Controller
Intel PRO/Wireless 4965 AG or AGN Network Connection
Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller
4-in-1 multicard reader.
Bluetooth
eSata

Everything worked in a single installation pass. No exceptions.
The graphics card is capable of running @1280x800 including all the eyecandy (compiz) you can throw at it, including the (built-in) HDMI connection to a HD television set.

Suspend to ram and suspend to disk also seem to work.

Firewire and webcam have not been tested (I do not use webcams) and I have no firewire equipment.

Also working: UMTS/3G (T-Mobile) though an OPTION expresscard.

---

### Post by barksten on 2008-07-29
1)Version Of Ubuntu: 8.04
2)Type Of Hardware: Laptop
3)Hardware Maker: HP (Compaq)
4)Hardware Model: 6710b

Best linux dist tested so far. WLAN works with WPA after a visit to System/Hardware Drivers and an automatic installation (requires a wired connection) of fwcutter + BCM FW.
GFX and Keyboard works perfect.

---

### Post by habibabid on 2008-07-29
ubuntu 7.10
intel p4 2.6 mhz
DDR 1GB
PCI Slot 2 NVIDIA GeForce FX 5200
INTELCHIPSET 82801

I Cant Install Ubuntu.. its gettin stuck @ bootin screen
i cant use live cd / cant install it..
hav tired no splash.

need help .. 
will b thankful ..

---

### Post by appier on 2008-07-29
**1)Version Of Ubuntu**

Ubuntu 8.04 LTS Hardy Heron

**2)Type Of Hardware**

Desktop PC Tower
Intel Pentium 4 CPU 1.80 Ghz
630 MB Memory

**3)Hardware Maker**

Compaq

**4)Hardware Model**

Evo D500

**Result:**

Enabled proprietary video driver.  It works.

---

### Post by Jive Turkey on 2008-07-31
My 2 month old newegg build:

Ubuntu 8.04 x86 and x64

Intel E8400 works 100%

Abit IP35 Pro works 100%

nvidia ECS 8800GT 512MB Fanless  Works well in 32-bit with current driver from restricted driver manager, too much PITA installing 64bit driver though, some claim to have done it.

Seagate 500GB SATA2 HD works 100%

2*2GB A-DATA DDR2 800 works 100%

Lite On 16x SATA DVD-ROM works 100%

Lite On SATA DVD +/- DL Burner I havent tried dual-layer yet, it burns +/- DVD with no coasters yet after about 20 (didnt try it in 64 bit

EPSON Perfection 3200 PHOTO Works in SANE 100% in 32-bit

Cannon iP1800 PIXMA printer 32-bit only using third party repackaged driver from here [http://hex1a4.net/]("http://hex1a4.net/")

Overall impression, works great, 64-bit would have been nice, maybe with intrepid...

---

### Post by Sense on 2008-08-02
Except for the IDE devices the Asus M3N78-EH does work. It doesn't work with the 2.6.24-16 kernel that was shipped with 8.10. However, it does at least work with 2.6.24-20; I'm not sure about previous versions though.

---

### Post by jhenager on 2008-08-05
jeff@jeff-desktop:/etc/sane.d$ uname -a
Linux jeff-desktop 2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008 x86_64 GNU/Linux


Mustek 600 III EP Plus
[http://penguin-breeder.org/sane/mustek_pp/](http://penguin-breeder.org/sane/mustek_pp/)
Make sure you follow the instructions carefully, including this line in the mustek_pp.conf file:
scanner Mustek-600-IIIEP * ccd300

Mine was set the the default parallel port address (0x378 ), and although the scanner was recognized, SANE couldn't use it. Changing that to "*" fixed the problem.

Edit #2 - just ran some updates which included the kernel. Maybe that date is when the kernel was compiled?
jeff@jeff-desktop:~$ uname -a
Linux jeff-desktop 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux

---

### Post by lucyrssll on 2008-08-07
Stinkyink now offer ink cartridges for the [HP Deskjet F2180 ink](http://www.stinkyinkshop.co.uk/acatalog/HP-Deskjet_F2180.html). Oh and it's free delivery too!

---

### Post by davidkl on 2008-08-08
Ubuntu 8.04LTS
CPU: E6400 Intel Core Duo
M/B: Gigabyte GA-965P-DS3
RAM: 2GB Kingston
HDD 160GB SATA
DVDRW: Matshita SATA
Graphics: MSI 8800GTS320OC

Works fine out of the box. Video drivers installed using Envyng, compiz working fine, all effects enabled. Ubuntu restricted drivers for video card caused mis-detection of card and forced VESA mode.


*speakers do not turn off when headphones are plugged into front panel, but that's not a big issue.

---

### Post by Brux on 2008-08-12
Hi guys,
I have just installed Ubuntu 8.04. I have got issues regarding hibernating/Suspend modes...i.e Resuming after a selection made to any of the two modes is resulting in certain messages.

I tried suspending...and this is the message i am getting
[103.736770] EXT3_fs error (device sdb1): ext3_find_entry: reading directory # 3088386 offset 0

Could someone help me out with this..:)
Regards
Brian

---

### Post by Regenpak on 2008-08-12
Ubuntu 8.04 on Jetway 7F2WE1G Mini-ITX board. Worked OOB. Removed CPU fan, case fan is sufficient to keep CPU a few degrees above ambient (idle). This is my seventh Linux system so far, and caused the least issues or problems :mrgreen: That said, this box is very basic, just 80 gig SATA disk, no video effects. Just browsing and downloading. And webserver. This box replaced an aging Via Epia (800 MHz C3) which was getting too slow. The Epia ran 7.04 with also few issues.

---

### Post by liam j dyer on 2008-08-14
[http://www.rewards1.com/index.php?referrer_id=89832](http://www.rewards1.com/index.php?referrer_id=89832)

rewards1 is a website where you fill out surveys for points from 0-4 each point is worth $1 and you can spend the money on what ever you want like a..ps3,ps2,psp,nintendo wii,ds,dildo if you really wanted :lolflag:

[http://www.xtremetop100.com/in.php?site=1132252565](http://www.xtremetop100.com/in.php?site=1132252565)
if you used the first link and liked it or using it then vote for it at the second link thanks XD

please vistit them and help me thank you XD

^&

---

### Post by liam j dyer on 2008-08-14
[http://www.rewards1.com/index.php?referrer_id=89832](http://www.rewards1.com/index.php?referrer_id=89832)

rewards1 is a website where you fill out surveys for points from 0-4 each point is worth $1 and you can spend the money on what ever you want like a..ps3,ps2,psp,nintendo wii,ds,dildo if you really wanted :lolflag:

[http://www.xtremetop100.com/in.php?site=1132252565](http://www.xtremetop100.com/in.php?site=1132252565)
if you used the first link and liked it or using it then vote for it at the second link thanks XD

please vistit them and help me thank you XD

^%

---

### Post by AceRimmer on 2008-08-15
Ubuntu 8.04

AMD Opteron 165 1.8Ghz (x2), 2GB PC3200 DDR, Epox 9na3j+ motherboard, ATI Radeon x800GTO AGP 256 MB, Creative Soundblaster 24Bit, 2x 750GB SATA Samsugn HD. 

It runs fine except for some video issues, I get frame tearing in playback and when I run an app that does 3d acceleration I often get flickering.

---

### Post by marine63 on 2008-08-16
hp dv6700t 15.4" notebook
works great 
the screen and wireless worked without fail :D
intel 2.0ghz
2gb ram
160gb hdd
nvidia 8400m gs
intel prowireless 3something 
12 cell battery
everything worked well even vista sp1 o.O

---

### Post by PHATSPEED7x on 2008-08-17
Compaq Persario 5003US desktop.
933mhz Pentium III processor.
384MB RAM.
80GB HD.
CD R/RW.
17" CRT montior.
MI internet USB keyboard.
MI usb wired optical mouse.
Ubuntu 8.04 OS.

Works great! Before Ubuntu the computer had Window's ME OS, and didn't work half the time. After upgrading the RAM so I could install from a live CD the computer has worked like brand new. Saved me $$$ that I would of used to buy a new desktop. Everything works awesome. Could max out my RAM at 512MB for a little faster performance.

---

### Post by SunLizard on 2008-08-19
HP Pavilion dv6000
Intel Core 2DuoT7500(2.2GHz/4MB L2)
2GB DDR2 Ram
383MB NVIDIA GeForce 8400 GS
Intel(R) PRO/Wireless4965AGN w/bluetooth
120GB 5400RPM SATA HD

Dual boot for now due to a CAD program I use in college that requires M$.
I also have a Xerox Phaser 6180 that Ubuntu recognized right off the bat with no problem.

This machine and Hardy seem to be a great match.  I have tried various flavors of Linux in the past and always grew tired of configuring hardware.  It is because of this match that I have become a Ubuntu follower.  I was amazed how easy it was to get a wireless connection with Linux or that it was even possible considering my past experience.
I would definitely recommend this laptop and Ubuntu.
On a side note I spent days and days trying to get mac mini loaded with Linux with no joy.  It has 10.3 loaded and the firmware that just will not coroperate.  After the ease of the install on this HP I was a little spoiled and have since sworn off Apple because they now seem just like M$ and just want your money.  Plus Ubuntu is now making life for the beginning programmer and want to be Linux user a whole lot easier.

---

### Post by wizardfait on 2008-08-19
Ubuntu 8.04.1

HP Pavilion ZE4800 (Actually ZE8405US)
2.1 Ghz AMD Athlon XP 2800+
768 MB Kingston PC2700 RAM (1X512 1X256)
60GB HDD
ATI Radeon 320M IGP (A.K.A. ATI Radeon U1)
Broadcom 4306 802.11b/g wireless card
MacPhyter LAN adapter
Conexant AC-Link Audio/Modem card

Everything works Out of the box, with exception of some errors at boot that can be ignored, and the obvious Broadcom 4306 issues.

As for the Broadcom 4306, simply using NDISwrapper fixed my problems.

---

### Post by sshlyk on 2008-08-19
deleted

---

### Post by kamolt on 2008-08-19
Ubuntu-8.04.1-desktop-i386
motherboard
Asus
A8N32SLI deluxe

Ubuntu hangs on installation or start up.
message : Busybox v 1.1.3
(initramfs)

This problem was solved by adding the following to boot options :

all_generic_ide floppy=off

First I erased "---" at the end of the boot line.

Asus A8N32 sli works fine now with Ubuntu 8.04

---

### Post by thetwilighthowl on 2008-08-22
On a Sony Vaio SZ Series (VGN-SZ691N/X)
Computer Type:Notebook
Running Ubuntu 8.04

# Sound System:Sony® Sound Reality™
# Multimedia Card Reader:Memory Stick DUO™ with MagicGate® functionality ExpressCard™/34 Slot: 5-in-1 Memory Card Adaptor (VGP-MCA20A) supporting Memory Stick®, Memory Stick PRO™, Secure Digital, xD-Picture Card, and MultiMediaCard (MMC) PCMCIA (Type II/Type I card slot with CardBus support)
# Action Buttons:S1, S2 (programmable) - Untested
# Wireless On/Off, stamina/speed hybrid graphics switch
# Security:Trusted Platform Module (TPM), TCG Ver.1.2 compliant Biometric Fingerprint Sensor - Not Working
# Chipset:Mobile Intel GM965 Express Chipset
# Interface:VGA out w/ Smart Display Sensor
# Processor:NVIDIA® GeForce® 8400M GS GPU (Works Great) and Mobile Intel® Graphics Media Accelerator X3100 (works, but not so well)
# Technology:Hybrid Graphics System
# Video RAM:831MB Total Available Graphics Memory13 (NVIDIA® GeForce® 8400 GS GPU) and 358MB Total Available Graphics13 (Mobile Intel® Graphics Media Accelerator X3100)
# Capacity:250GB2
# Impact Protection:G-Sensor™ Shock Protection - Hard Disk Drive Protection - Untested
# Interface-2:Serial ATA
# Speed:5400rpm
# Camera:Built-in Camera and Microphone - Not working
# Keyboard:QWERTY (86 keys with 3mm stroke and 19.05mm pitch)
# Pointing Device:Electro-Static touch pad
# DC-In:1
# Ethernet Connection (s):1
# Express Card™ Slot:1
# Headphone Jack:1
# i.LINK® Interface:1 (4-pin IEEE 1394) interface6
# Memory Stick® Media Slot:1
# Microphone Input:1
# Modem Jack:1
# Port Replicator Connector(s):1 (Bottom)
# USB Port(s):2 (2.0 compliant)
# VGA Output(s):1
# Installed:2GB (1GBx2) PC2-5300
# Maximum:4GB15
# Speed-2:667MHz
# Type:DDR2
# Bluetooth® Technology:Integrated Bluetooth® Technology5
# Ethernet Protocol:Fast Ethernet (RJ-45)
# Ethernet Speed:10Base-T/100Base-TX/1000Base-T
# Modem Type:Integrated V.92/V.90 Modem (RJ-11)
# Wireless LAN:Intel® PRO/Wireless 4965AGN Network Connection (802.11a/b/g/n)3
# Wireless WAN:Sprint® Mobile Broadband service1819
# DVD±RW:Yes4 (DVD±R DL/DVD±RW/DVD-RAM)
# Battery Type:Standard Capacity Lithium-ion Battery
# Estimated Battery Life:3 to 6 hours7 (Standard Battery)
# Front Side Bus Speed:800MHz
# L2 Cache:4MB
# Speed-3:2.41GHz1
# Technology-2:Intel® Centrino® Duo Processor Technology
# Type-2:Intel® Core™2 Duo Processor T8100


Right out of the box I popped in the 8.04 LTS cd and got everything working but the DVD player, camera/mic, and the little memory stick Pro DUO reader. I think that it's recognizing the hardware for the fingerprint scanner, but there's no software to tell it to do anything yet.

---

### Post by exowraith on 2008-08-25
ubuntu 8.04 x64

AMD Athlon X2 5200+
MSI K9N SLI Platinium
ASUS 7950GT 512MB SLI
Corsair Value Select 4GB PC5300
Creative X-Fi ExtremeGamer 
Samsung 16X LightScribe DVD-RW DL
TDK 16X DVD-RW
Western Digital 2500KS 250GB
Western Digital 5000AAKS 500GB
Western Digital 5000AAKS 500GB

Creative X-Fi not working. the rest are good.

ubuntu 8.04 i386

Fujitsu S6410
2Ghz Centrino Duo
2GB RAM
Intel Express 965M 

Only issue here is the brightness is very dim even with xbacklight at 100%, my brightness applet is not working, one red X there. Fn+F keys dun work to adjust brightness but work for volume and mute.

---

### Post by distrachi on 2008-08-27
Ubuntu-8.04.1-desktop-i386
Acer
Notebook
Acer Aspire 5583WXMi

Processor	Core 2 Duo
Processor speed	1.66GHz
Amt of RAM	512 MB (max 4096 MB)
Hard drive	120 GB
Optical drive	DVD Super Multi
Graphics hardware	Nvidia GeForce Go 7300
Diagonal screen size	14.1 inch
Wireless LAN	802.11a, 802.11b, 802.11g
Webcam	Yes 

Notes:
Could not enable hardware 3D graphics, would cause frequent freezes and lockups, found the solution to problem at [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/164589](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/164589). Solution prevents the graphics card from going into power saving mode so battery life is not very good.

Although the wifi button works, the wifi LED doesn't turn on.

VGA-out has some problems. The screen on external monitor blanks out (turns black) when i move the mouse. When I stop moving the mouse, the screen comes back.

Everything else works well:
1. Audio (needed to play around with mixer to get internal mic to work)
2. Ethernet/Wireless
3. Memory/SD card
4. DVD/CD Read/burn
5. Suspend/hibernate/power saving mode (dim display)
6. hardware buttons (volume control, brightness, email, web)
7. Webcam

Bluetooth hardware button appears to work but I have not tested if it actually connects to bluetooth devices. Built-in modem was not tested.

---

### Post by New_Guy08 on 2008-08-28
Ok I just got my beast built about a week ago and everything is running fine after updates etc.

Mobo:GIGABYTE MA78GM-S2H
CPU: AMD X2 5400 BE
VIDEO: ASUS EAH3450 After ATI restricted drivers dl and install Compiz works great!
PSU:Rosewell 550w
COOLING:Rosewell Z3
RAM:OCZ Reaper 2x 2Gb 800mhz
Harddrive: Seagate IDE 7200rpm 80GB
Keyboard & mouse: Logitech S510; volume controller works on it I'm happy!:)

---

### Post by Bruce S on 2008-08-31
> **WestCoast said:**
> Ubuntu 7.10 - the Gutsy Gibbon
PRINTER
Hewlett Packard
(HP) DJD 4260

Printer only (no fax, scan, or copy)
Prints Color and Black/White
Connection:  USB
Ink cartridges: 2 (single black, single color combo) cost approx $30.00
Install:  Put in ink cartridges and paper,  
          Plug in power cord. 
          Turn printer on. Let printer configure itself. 
          Connect USB cord. 

 Setup: Open the Printer Configuration Window: System -> Administration -> Printing
          Select:  New Printer  
          Enter devise URI as:  HP DJD 4260  (press Forward)
          Select Printer from Database:  HP  (forward)
    
          At the New Printer configuration window
          Select 
                MODEL: Deskjet D4200  
                Drivers: HP Deskjet D4200 Foomatic/hpijs (recommended)
                (Forward)
          Printer Name:  (should fill in automatically)
          Description:  HP DJD 4260
          Printer Location:  Anywhere 
                 Note: Location must have an entry.  It cannot be left blank.
           Click Apply.  

Once the system has finished configuring use the Policies, Access Control, Printer and Job Options tabs in the Printer Configuration Window to set personal preferences for printer policy, user sharing, paper type, print quality, and job control.  Other than selecting printer sharing, paper type, print quality I used the default settings in this area.

To test the installation click on the Settings tab:  
         Select: Print Test Page.  Print Self-Test Page and/or Clean Print Heads.


This little printer works GREAT!  Couldn't beat the $39.00 sale cost either. I think the regular price was around 59 to 69 dollars.

Note:  Couldn't get my $400.00 All-in-One Lexmark to work.  Couldn't get my near $200.00 All-in-One Brother to work.  Couldn't get my $50.00 Dell to work.  But this little $39.00 HP DJD 4260 works like a charm, has a good print, and installed without a hitch.

     If you want to be sure of a printer installing OK, I think the only one you can be sure of is HP . 
    My HP L7580 installed without a hitch .Plus HPLIP Toolbox available 
and have installed it. Makes using the printer very easy. Can check ink available , head info. etc.etc.
    Lexmark seems to be bottom of the heap !

---

### Post by latinoheat69 on 2008-09-07
DELL Inspiron 1420
Intel GMA X3100
Intel 3945 a/b/g
SATA 120 GB HDD
USB Belkin Mouse (I don't like the trackpad)
2 GB Ram
Core 2 Duo 1.5 GHz

---

### Post by Ken4000 on 2008-09-10
Please Only List
1)
Ubuntu 8.04.1 (Works out of the box!)

2)
1,7GHz Intel Centrino, 100Gb Hitachi hdd, 2Gb Kingston ram, Intel Wireless Card, ATi Radeon Mobility 9600 Turbo Pro 128Mb graphic card, 15,4" 1680x1050 TFT.

3)
Dell

4)
Inspiron 8600

---

### Post by Casper Hansen on 2008-09-10
Laptop:

Ubuntu 8.04.1 Hardy Heron

Lenovo 3000 N200

CPU: Intel Pentium Dual-Core 1,86 GHz
RAM: 2 GB
HDD: 160 GB

Sound fix: [https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N200_0769B2G](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N200_0769B2G)

I haven't tried SD-reader and fingerprint scanner, but other hardware works great. Actually the wireless is better than Vista. In Vista I could reach 60%, in Ubuntu I reach 86 - 95%!

---

### Post by Predator106 on 2008-09-10
OS#: Ubuntu 8.04.1 Hardy Heron kernel version: 2.6.24-21-generic

Memory: 2GB DDR2 Kingston Ram

Graphics:Integrated Intel seemed to work fine the little bit I tested it. I also have an XFX Nvidia 8600 GT. It works beautifully in here.

CPU: Intel Core2Duo E6420 @ 2.21 ghz (I believe it is overclocked a tiny bit, stock is 2.13 I think)

Motherboard: ASUS P5B-VM SE

Sound:Integrated works fine, but to achieve 5.1 digital (I actually think I can only get 5.0 digital (no center)), it requires a bit of tweaking, but basically works fine, Turtle beach Riveira.

No problems, runs perfectly other than what's noted. I did notice one weird thing, however, after resuming from standby in Hardy(by turning on my computer), my CD Drive will eject immediately and then go back in real quick. I have no idea what this is caused by, maybe a BIOS setting or BIOS confliction? I don't know, but it scared the **** out of me the first time it happened, because I have one of those case doors, so it flung it open.

I also used 2 adapters to convert 2 old hard drive from IDE to the SATA motherboard, works fine with every OS, so it most certainly wouldn't be prob with Ubuntu.

---

### Post by thepizzaman on 2008-09-10
Ok Ubuntu 8.04 Hardy Heron 32 bit (soon to add 64)
Acer Aspire M1201
works with SATA not ide
	these are the exact specs from tigerdirect
	  + ATI Readon HD3450, zonet ZEW1602, and a 500 gig SATA II Seagate harddrive
	
	  Processor Brand:  	AMD
	  Processor Class:  	Athlon 64 X2
	  Processor Number:  	5000
	  Processor Speed:  	2.60GHz
	  Memory Type:  	DDR2
	  Memory Size:  	1GB
	  Total Memory:  	2.0GB
	  Memory Speed:  	DDR2 800 (PC2-6400)
	  Interface:  	SATA II
	  Capacity:  	320GB
	  Speed:  	7,200RPM
	  Optical Drive Type:  	DVD±RW/-RAM Dual Layer
	  Audio Description:  	Integrated Audio
	  Channels:  	7.1
	  Graphics Description:  	Integrated Graphics
	  GPU/VPU:  	ATI Radeon 2100
	  Video Interface:  	DVI
	  	VGA (15-Pin D-Sub)
	  Maximum Resolution:  	NA
	  Communications Description:  	Integrated LAN Support
	  Interface Type:  	RJ-45 - Ethernet Connector
	  Data Transfer Rate:  	1000Mbps 10Mbps 100Mbps
	  Communications Description:  	56Kbps PCI Modem
	  Interface Type:  	RJ-11 - Phone Connector
	  Data Transfer Rate:  	up to 56Kbps
	  Protocols:  	V.92

---

### Post by joh12 on 2008-09-13
Hi,
This Desktop Hardware Compatibility site is very useful to know about the desktop hardwares and other things. I wnat to know more about UDSF. Give more details about that.

--------------
John

[widecircles](http://www.widecircles.ca)

---

### Post by zr0gee on 2008-09-18
1) Ubuntu 8.04(Hardy Heron) 64bit
2) Motherboard
3) Asus
4) Striker II NSE (chipset: Nvidia nForce 790i SLI)

Worked out of the box for me. Sound, networking etc. 

I spent a good amount of time searching for other people who might have tried this particular motherboard (or rather, the chipset) in Ubuntu, but I was unsuccessful.

---

### Post by hijk867 on 2008-09-19
&#27893;,&#19968;&#33324;&#21487;&#20197;&#29702;&#35299;&#20026;&#36755;&#36865;&#27969;&#20307;&#30340;&#26426;&#26800;&#35774;&#22791;&#12290;[&#35745;&#37327;&#27893;](http://www.gzlch.com/products.asp?cid=6)(metering pump),&#21487;&#20197;&#35745;&#37327;&#25152;&#36755;&#36865;&#28082;&#20307;&#30340;&#26426;&#26800;,&#20063;&#21483;&#23450;&#37327;&#27893;&#12289;&#27604;&#20363;&#27893;&#12290;&#20064;&#24815;&#21033;&#29992;&#25628;&#32034;&#24341;&#25806;&#30340;&#26379;&#21451;&#23601;&#20250;[SEO&#20248;&#21270;](http://www.tudou.com/programs/view/jdszYZ2v0ew) ,SEO&#20248;&#21270;&#19968;&#20999;&#20174;&#38646;&#24320;&#22987;..

---

### Post by muanis on 2008-09-19
Ubuntu Hardy Heron 8.04 on HP Compaq 6515b

Wifi working
Bluetooth working
PCCard not tested
CardReader not tested
Fingerprintscanner not tested
Sound working

---

### Post by botulismo on 2008-09-20
1. Ubuntu Gutsy and Hardy
32 bit fails to start properly and 64 bit won't load at all (on a dual core Athlon 64 5000+)
2. Motherboard
3. ASUS
4. M2N-MX SE

Back to Windows for now... :(

---

### Post by driven1 on 2008-09-22
I just put this together this weekend. My first build :)

Hardy Heron 8.04 amd64	

    GIGABYTE GA-MA78GM-S2H 780G HDMI  
    AMD Athlon 64 X2 5400+ Brisbane 2.8GHz 
    CORSAIR XMS2 2GB (2 x 1GB) DDR2 800 4-4-4-4-12
    ARCTIC COOLING Freezer 64 Pro 92mm CPU Cooler
    LG 22X DVD±R IDE Model
    HITACHI Deskstar P7K500 500GB SATA
    TRENDnet TEW-443PI PCI 2.2 Wireless
    ANTEC Sonata III

Everything works pretty much out of the box. Internal speaker doesn't work. Front audio jack works fine. I haven't tested the rear. Everything else seems to work so far. Have not tested the DVI/HDMI ports yet. Going to add a Radeon 3450 video card for future Crossfire (I also want s-video out for my tv).

---

### Post by packrat on 2008-09-24
New Build, MSI K9N SLI V2 mobo...Ubuntu v8.04

MSI K9N SLI V2 mobo
AMD Phenom X4 Processor 9550 2.2 cpu
GeFORCE 8500GT Graphics Card
4x 1 gig Corsair RAM sticks
500 gig Seagate Barracuda
Sony DRU-V200A DVD+-R
NZXT Hush Case
Corsair VX450W PS

Installed from first try...no problems...components work...

---

### Post by shockdesign on 2008-09-24
Hey guys,

Okay new simple desktop.


Asus M2N-MX-SE Motherboard
2Gb Kingston DDR2 (running in single channel mode)
Asus EAH3450 (ATI HD3450)
Running Hardy 8.0.4.1

Issues with the ATI propriety driver, if I install it and run with it, my desktop just freezes and thats it. I can reset back to not using the driver and it works fine, albiet slow.

Odd too because I've read reports on this topic stating it works fine, heh :) Run memcheck too and it comes up good!

---

### Post by soloman498 on 2008-09-28
Ubuntu 8.04
 H.P. Deskjet F2180 all in one Prints,Scans and copies,no driver problems at all.:)

---

### Post by ju2wheels on 2008-09-28
Works perfectly on Intrepid 64bit, video card was plug n play with nvidia drivers automatically installed.


MSI P7N SLI-FI 750i SLI Chipset LGA775
NVIDIA GeForce 8500 GT 512MB 16X PCI Express
Core 2 Quad Q6600 @ 2.4GHz 1066FSB 8MB L2 Cache 64-bit
4gb PC6400 DDR2/800 Dual Channel Memory

---

### Post by murphykieran on 2008-10-01
**Asus Eee PC 904 netbook**
Ubuntu 8.04

All the basics worked after installation apart from ethernet and wireless.  I had to download and install the latest Madwifi drivers and then enable them via *System>Administration>Hardware Drivers* to get the wireless working and it's working fine now.  Ethernet is not working but I haven't tried to get it working yet.  

I haven't tried connecting a display via the VGA port or using the microphone jack yet.
update: Audio jack works fine with headphones.

**Canon iP2000 inkjet printer**
**Canon CanoScan LiDE20 flatbed scanner**
Both of these just worked in both 7.10 and 8.04
No setup was necessary, I just connected them to the PC, and printing via all applications I tried and scanning via xscan worked fine.

**Creative ZEN 8Gb**
Didn't work automatically in 7.10,  I found instructions [here]("http://tiagoboldt.net/blog/creative-zen-linux/") that worked.
Worked automatically in 8.04 just by plugging it in and opening Banshee to import songs.

---

### Post by tydfil on 2008-10-07
Intrepid
XFX 8200 Mobo
Integrated sound and video
4GB DDR2 800
80Gig and 40Gig Drives

8200 chipset is a yet unsupported (xorg error log)
Everything works but grapphics will only boot into low graphics mode as not devices are detected.

nvidia driver can be be installed from CLI but it is unstable. Flicker, which appears to be an overlay of the background colour of the menu panel extending 2 thirds the way down the screen.

---

### Post by dartrod on 2008-10-15
I am looking for a recommendation for a LCD Monitor that is compatible with the following configuration:

AMD Athelon 64 LE 1640 2.6 GHZ 45 watt L2-1MB AM2
AMD Athelon 64 original Stock Fan and Heat sink
Kingston DDR2 PC2-5400 1GN/667 MHz
BIOSTAR MCP6P-M2 (NVIDIA GF6150, SATAII, RAID, DDR2-800
NVIDIA GeForce 6150 GPU Memory share up to 512MB
On board High Definition Audio
On board Network Card
450W ATX Power Supply
Western Digital Caviar SE 160GB 7200RPM SATA
LG DVD-RAM GSA-H55N
Ubuntu 8.04 Hardy Heron

Thank you

RSW

---

### Post by Ter Rymon on 2008-10-16
Converted an Win98 system two days ago with 8.04 LTS Live CD.  I knew the system well, I built it from parts back in 1990.

Intel SE440BX-2 Motherboard with Math Co-Processor installed next to Intel PIII 450Mhz CPU. 384 Ram (maxxed out)
Yamaha DS-XG built on the motherboard provides great sound.
ATI Rage Pro graphics card (release 6112) the stable one.
Seagate 6 Gig Hard Drive (that was as big as I could get back then... Yes it's slow.)
Memorex 48x CDR   (burns DV-CDs)
and a
HP CD-writer Plus 9100 (burns CDs that even MS-DOS understands)
I have a brand new Linksys Ethernet card (there wasn't one originally)
And I have a old Creative ModemBlaster 56 II ISA voice/fax/modem.

It actually runs faster NOW than when I put it together.
Oh and as an added bonus I can actually get it to sync with MyPDA (an old Palm IIIe)

I never could get the call attendant software or the caller id to work on the modem (Now the caller ID works, but the fax will ONLY send not Receive.

I'm happy enough I might break down and buy a different modem (probably used because I need the older chipsets so they talk nice to my two MinoltaFax 's (the 2600 one is connected to a Netgear print server.)

Oh and I installed "wine" so I don't have to give up cold turkey on that huge library of Win98 software. [http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif)

---

### Post by Therion on 2008-10-17
**1)Version Of Ubuntu:**  Hardy Heron - 8.04
**2)Type Of Hardware: ** Printer
**3)Hardware Maker:** HP / Hewlett Packard
**4)Hardware Model:**  Photosmart D7460

Plug 'n' Play with a USB connection.  No muss, no fuss, no bother.  Awesome printer.

---

### Post by Naiki Muliaina on 2008-10-18
Ubuntu 8.04 (and many derivatives mint, ozos, xubuntu and more)

Denver 10 Motherboard
Intel E1200 Processor
Radeon x1950 Graphics card
2gb Ram (unsure of brand)
400 watt Power Supply

Only setting up i had to do was the graphics (its an ATI, no suprises hehe). Even then it took 2 minutes, if that, following the Ubuntu/ATI wiki.

Never had any problems what so ever, nice little setup.

---

### Post by Cyberponcho on 2008-10-20
Reporting a HP Compaq nc4200 running 7.10 Gutsy, everything worked out of the box, hardware profile will be posted.

---

### Post by gmacor2 on 2008-10-22
Ubuntu Hardy Heron 8.04
Film Scanner
Minolta
Dimage Scan Dual 11

---

### Post by ash05 on 2008-10-25
Hardware Model: BToes 2.0 EDR
Ubuntu version: 6.06
Hardware Maker: MSI
Type Of Hardware: USB Bluetooth Dongle

[URL="http://www.audiomicro.com"]
Stock Music, Music Cues,Production Music[/URL]

---

### Post by blakwolf on 2008-10-30
Version: Kubuntu 8.04 LTS
PC: HP Pavilion ZE4355EA (notebook) 512MB RAM, 40 GB HD swap partition 1.5GB, ATI radeon Mobility U1
BIOS: KA.M 1.60
Installation was fine, but no suspend/hybernate

Workaround: 
1 - kernel command line option "acpi_sleep=s3_bios" 
2 - apt-get install powernowd 
3 - HYBERNATE = platform in /etc/default/acpi-support

fixed hybernate, suspend to ram working but the PC shutdown when trying to go back. 

Tried uswsusp, no change.

Probably buggy bios, decompiling/recompiling with INTEL iasl gives 3 warnings 1 error, I wasn't able to find a workaround

---

### Post by Rodney9 on 2008-10-31
Asus P5Q-Pro M/B
Intel E8400 CPU
Nvidia 9600GT Video Card
GSkill DDR2 800Mhz 8Gb Ram

Ubuntu 8.10 64bit Desktop. 
Sound, network and video all working perfectly.

---

### Post by francis_ba on 2008-11-01
[IMG]http://tinyurl.com/rerunner/[/IMG]
GOT IT WORKING, LOVE UBUNTU!!!

---

### Post by Hadraniel on 2008-11-02
Ubuntu 8.10

**Board:** Gigabyte [GA-MA78GPM-DS2H](http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2859)
**CPU:** AMD [4850e](http://products.amd.com/en-us/DesktopCPUDetail.aspx?id=426) (Chipset AMD780G)

**Graphics:** on-board ATI Radeon HD3200 (RS780)
I shared [this problem (click!)](http://ubuntuforums.org/showpost.php?p=6030745&postcount=10) first, even with 8.10 final (not 8.10rc), and fiddled a lot with drivers. Good thing is, if things go wrong, revert to standard xorg.conf or restore backup, you'll always have highres framebuffer graphics and never drop to textmode or lowres available (like in early Linux days)
Must read Wiki-pages: [RadeonDriver](https://help.ubuntu.com/community/RadeonDriver), [RadeonHD](https://help.ubuntu.com/community/RadeonHD), [RadeonHD](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) (fglrx)
For ATI-newbies (like myself): yes, there are three ATI-drivers. Two Open-Source, one from ATI itself (fglrx). Good start to aquire knowledge about differences: [Radeon vs. RadeonHD Drivers In H1'08](http://www.phoronix.com/scan.php?page=article&item=radeon_vs_radeonhd&num=1). And there are some tons of forum discussions and articles around, everywhere.
At some point, the Ubuntu-On-board fglrx drivers worked out: enable restricted drivers, activate - you win.

drawback: even with the latest 8.10-bundled catalyst 8.54-drivers, Hardware-Accelleration seems to be limited or instable. I tried EVE-Online for curiosity, and it does not work (uses some customized cedega).

Current status for me: 2D and softrendering fine, 3D .. well .. I gotta try some Linux shooters.


**Sound:** on-board (southbridge SB700)
Works out of the box. 5.1 surround, mic. Don't have working SP/DIF-out yet, though. My AC3-Decoder gets some Dolby Stereo signal, but is quiet :-(


**DVB-T/USB2:** MSI Digi Vox mini II (chipset em28xx)
Running and shows up as restricted driver, just like the ATI fglrx drivers. Takes some manual work, though. You wanna read: [MSI DigiVox mini II V3.0](http://www.linuxtv.org/v4lwiki/index.php/MSI_DigiVox_mini_II_V3.0), [em28xx driver compilation in Intrepid (Beta)](http://ubuntuforums.org/showthread.php?t=956353&highlight=dvb-t+usb), [DVB-T USB-Devices](http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices) and probably use the ubuntu installation package from [here](http://www.digittrade.de/shop/shop_content.php/coID/9) (I suceeded using the guides at the given URLs).
Switching channels regularly results in graphics going mad. Restarting the TV app is a workaround. Probably due to beta-fglrx-drivers (see previous paragraph on on-board-graphics).

---

### Post by ruff on 2008-11-02
1)Version Of Ubuntu: 8.10
2)Type Of Hardware: Digital TV Tuner Card (DVB-T)
3)Hardware Maker: Leadtek
4)Hardware Model: Winfast DTV2000 H

Worked out of the box. Installed Ubuntu 8.10 and then installed the Digital Television apps from the Add/Remove applications. This installed MeTV and everything autotuned and worked perfectly.

Also this is the first verion of Ubuntu to recognise the built in LAN controller on my Asus P5Q motherboard.

---

### Post by qrst472 on 2008-11-03
The real evils, indeed, of [wow gold](http://www.wowpowerleveling-wow.com/) Emma's situation were the power of having rather too much her own way, and a disposition to think a little [wow gold](http://www.wow-wowpowerleveling.com/) too well of herself; these were the disadvantages which threatened alloy to her many enjoyments. The danger, however, was at [wow power leveling](http://www.powerleveling-wowgold.com/wow-power-leveling.html) present so unperceived, that they did not by any means rank as misfortunes with her. Sorrow came--a gentle sorrow--but not at all in the shape of any disagreeable consciousness.--Miss Taylor married. It was Miss Taylor's loss which first brought grief. It was on the [wow powerleveling](http://www.wow-wowpowerleveling.com/) wedding-day of this beloved friend that Emma first sat in mournful thought of any continuance. The wedding over, and the bride-people gone, her father and herself were left to dine together, with no prospect of a third to cheer a long evening. Her father composed himself to sleep after dinner, as usual, and she had then only to sit and think of what she had lost.weiwei1978123

---

### Post by sandy8925 on 2008-11-07
Version: Ubuntu 8.04
Motherboard: KOBIAN KOBP4M266A
CPU:  Intel Pentium 4 1.8 Ghz (400 Mhz FSB)
RAM:  256 MB DDR-SDRAM (266 Mhz)
Graphics Card: Nvidia Geforce 6600 GT (AGP 4X)
Hard Disks:  1)Seagate 40 GB hard disk (master)
             2)Samsung 40 GB hard disk (slave)
DVD Drive:  Samsung DVD-RW/+RW drive

---

### Post by mannaa on 2008-11-07
FSC amilo pi3540
Ubuntu 8.10 32 bit
Intel P8400 - ok
webcam - ok
Synatic - ok
intel 5100 wifi - ok
etc etc

Geforce 9300m, needed property driver, then ok

Conclusion - ok =)

---

### Post by pablolie on 2008-11-08
Ubuntu 8.10 (Standard 64-bit Installation CD)

SG33G5 Mini Desktop with
- Intel Core 2 Duo E8400
- 4 GB of DDR2 RAM
- Asus EN8500GT Silent

[http://us.shuttle.com/barebone/Models/sg33g5_pro.html](http://us.shuttle.com/barebone/Models/sg33g5_pro.html)

Note: Installation was a total breeze, pop in standard CD and let it install itself. In fact I would say Ubuntu was easier to install than Vista Ultimate 64 bit!

---

### Post by moTaro on 2008-11-09
Ubuntu 8.10

Hardware: Notebook Lenovo R61

Fully Compatibile.

I had to use wicd instead of Network manager applet, rather than that it's all ok.

---

### Post by sledge73 on 2008-11-09
compaq presario c500, 1.6ghz celeron m, cpu 1.5gb ram, ubuntu hardy, everything works out of the box. also lite-on dx-20a4pu external dvd burner plug n play!!

---

### Post by merdenoms on 2008-11-09
Ubuntu Version: 8.10

Hardware: MSI VR 330 Notebook

Works perfectly! No problems

---

### Post by am7146 on 2008-11-09
Ubuntu 8.10
IBM Desktop w/USB 2.0 ports

Two webcams worked great straight out of the box:

Logitech Quickcam Communicate MP/S5500
Logitech Quickcam Pro for Notebooks (2007 model)

Did a fresh install, plugged them in, /dev/video* just showed up and worked right out of the box with luvcview and motion after doing an apt-get install of both progs.

Pro has better quality image. 

Andy-

---

### Post by Daktyls on 2008-11-09
Ubuntu 8.04 Linux Kernel 2.6.24
USB All-in-one Printer
Epson
Stylus CX9400

Works fine when using the following driver:

CUPS+Gutenprint(OpenPrinting LSB 3.2) v5.2.1 Simplified

and in the Printer Configuration menu under "Printer Options" with the Colormode set to "CMY Color".

---

### Post by Duroon on 2008-11-10
I just (a few hours ago) bought a brand new Acer Aspire 6930. Dumped Vista in favor of Intrepid and everything works right after install, wireless, compiz, sound, everything. Easiest install I have ever done.

---

### Post by PGHammer on 2008-11-11
Hardware: Wireless Ethernet (USB)
Manufacturer: SMC Networks ([http://www.smc.com](http://www.smc.com))
Product: SMC EZ Connect g

Surprise of surprises, all I had to do was point it at the folder containing the Vista drivers, and it configured itself with little prompting; all I was left to do was configure the type of security (WPA) and entering the passphrase.  Notice that I did it in the same way I would do it in Windows - while the system was running.

Shocking.

---

### Post by immerohnegott on 2008-11-11
Custom built machine:

Motherboard: Asus P5B (Intel P965 Express + ICH8 )
--onboard sound and ethernet work out of the box, southbridge allows for
--AHCI HDD operation, this works as well. Third party IDE/SATA controller --works, but is buggy with  IDE drives (have disabled, using SATA 
--DVD-Burner)

CPU - Intel Pentium D 930 (overclocked to 3.75ghz) - recognized fully.

Audio - Creative Audigy SE - works using ALSA CA0106 driver.

Video - BFG-made Nvidia GeForce 7950GTOC - works out of the box with
--xorg driver "nv". works well after enabling the proprietary driver
--in the "Hardware Drivers" dialogue (have also used Envy before with no issues)

Other notes - have been using Ubuntu (tried all flavors) on this machine since I believe 6.10, with very few issues.

---

### Post by PhantomGhost on 2008-11-12
Need a wireless card for your desktop computer or HTPC?

Try the D-Link DWA-556. It's a PCI Express desktop adapter. Works in x1, x4, x8, or x16 slots. Supports Wireless N (draft) and of course Wireless G. 

[http://www.dlink.com/products/?pid=549](http://www.dlink.com/products/?pid=549)

This card worked beautifully for me out of box. No configuration was required. None. Even the Live CD was able to make use of it. It connects to wireless networks in seconds. Probably the most flawless piece of expansion hardware in my setup. I'm thrilled with it.

It is also FAST, even with my wireless G router. Web pages load seemingly faster than on my other computers which are hooked up via Ethernet and run Windows.

I'm running the latest version of Ubuntu - Intrepid Ibex.

---

### Post by Peyote Coyote on 2008-11-12
PC104 Advantech Geode LX800 machine:

Advantech PCM-3353, 500 Mhz, 1Gb

Runs with 2.6.27 Xubuntu nicely, and also
with ACPI disabled in BIOS & kernel args

We also had luck cross-compiling the

APEX STX104 16bit ADC drivers & code
and
Symmetric Research PAR8CH 24bit ADC drivers & code

Only issue is that it will not mount USB memory sticks on reboot.

Still have not confirmed: watchdog, compact flash interfaces

Thanks for getting these LX800 patches in.  Now we can dump Fedora!

PC

---

### Post by HDTimeshifter on 2008-11-13
> **Rodney9 said:**
> Asus P5Q-Pro M/B
Intel E8400 CPU
Nvidia 9600GT Video Card
GSkill DDR2 800Mhz 8Gb Ram

Ubuntu 8.10 64bit Desktop. 
Sound, network and video all working perfectly.

Have you turned on hibernation?  I have nearly the same setup, but with an Intel Q6600 CPU and 2x2GB dual channel Corsair DDR2/800 MHz RAM.  I've been having bootup and hardware problems that I suspect are related to power management.  [http://ubuntuforums.org/showthread.php?p=6154425#post6154425]("http://ubuntuforums.org/showthread.php?p=6154425#post6154425")

---

### Post by slowlap on 2008-11-15
Ubuntu 8.11
Dell Vostro 1400 wifi
Cannot get printer to print anything through wifi.
Printer is Lexmark Z2490 wifi

---

### Post by AllenGG on 2008-11-16
Using 8.10
Mobo: Intel (POS) 
CPU: Intel(R) Core(TM)2 Duo CPUE8400@ 3.00GHz, OK, slightly faster than my AMD 64 Athlon at 5yrs old.
Video, NVidia 9800GT works OOB
Sound:  Sound Blaster Live 5.1 works well, must load drivers.

---

### Post by Olivier2371 on 2008-11-16
Hello everybody,

Acer Aspire 9302 AWSMI 

specifications:

AMD Turion 64 Mobile Technology MK38 (2.2 GHZ, 512KB L2 cache)
17" WXGA+ Acer CrystalBrite LCD
up to 384 MB NVIDIA Geforce Go Xpress 6100 TurboCache
120 GB HDD
DVD-Super Multi double layer
4 GB DDR2 Memory
802.11 b/g Wireless Lan
Mini pci extension slot for BlueTooth card
Windows Vista premium & Ubuntu 8.04 Lts

[CENTER]**[COLOR="DarkOliveGreen"][SIZE="5"]FULLY COMPATIBLE[/SIZE][/COLOR]**[/CENTER]

Good luck to all.

---

### Post by 00b00nt00 on 2008-11-16
Compaq Armada E500

Pentium III @ 800Mhz

512MB RAM

ATI Rage graphics

Ubuntu 8.10 works well, just don't expect any 3D graphics acceleration.

---

### Post by nickcannard on 2008-11-17
Dell Inspiron 8600
intrepid 8.10
Fully compatible

Pentium M 1.7ghz
1gb ram
Nvidia Geforce Fx Go 5650
Sigmatel audio (snd_intel8x0)
Alps Touchpad
Everything seems to work perfectly.

ONE COMPATIBILTY PROBLEM:
The Fn key combined with the up/down arrow keys used to adjust screen brightness causes the window manager and the panel at the top to FAIL TO OPEN, they highlight but will not pull down, any windows currently open can not be moved.

---

### Post by szale9001 on 2008-11-20
> **AllenGG said:**
> Using 8.10
Mobo: Intel (POS) 
CPU: Intel(R) Core(TM)2 Duo CPUE8400@ 3.00GHz, OK, slightly faster than my AMD 64 Athlon at 5yrs old.
**Video, NVidia 9800GT works OOB**
Sound:  Sound Blaster Live 5.1 works well, must load drivers.

You said the 9800GT works OOB for you. You mean 100% with 3d acceleration and all? I was thinking of picking one up but just want to make sure its fully functional in 8.10

---

### Post by AllenGG on 2008-11-21
RE: NVidia 9800GT , note that I loaded the restricted drivers, version 177

---

### Post by szale9001 on 2008-11-21
> **AllenGG said:**
> RE: NVidia 9800GT , note that I loaded the restricted drivers, version 177

Yea, I had thought so. I have heard a lot of people had trouble installing those in intrepid (but I'm not sure if those people were upgrading from Hardy). It worked for you no problem? I am assuming you installed the Driver from the repos/Restricted Drivers screen.

---

### Post by itsStephen on 2008-11-23
Tried with both Ubuntu and Kubuntu 8.10

Asus M2N-MX SE Plus motherboard works. I'm really not sure what graphics chipset it has. Aparantly the geforce 6100 which it is meant to have doesn't work. I got it working and installed the proprietary nvidia driver and it says I have the 6150SE.
Samsung HD161HJ 160gb hard drive... works. I've got Kubuntu installed on it now.
HP DVD-1070 DVD drive works. It has lightscribe but I haven't got around to playing with that yet.
AMD Athlon 64 LE-1620
Patriot 2GB kit Signature line ddr2 800mhz ram works fine with it.

I only built this computer yesterday by the way, have to see how it holds up.

---

### Post by antoni2 on 2008-11-23
Xubuntu 8.10
Compatible with Asus Eee PC 1000H. Originally came with Windows XP installed. Works fine in dual boot mode, with Xubuntu installed in a new partition. 

Only problem found was Wifi not detected. It is a

802.11n Wireless LAN Card
from Ralink Technology, Corp
Version: 1.1.2.0
Windows file for the driver: C:\WINDOWS\system32\DRIVERS\rt2860.sys

You just download and install (right button click) the debian package rt2860sta-dkms_1.8LK_all.deb  available from:

[http://www.mediafire.com/?jfrgzemgnjz](http://www.mediafire.com/?jfrgzemgnjz)

and everything is Ok !

---

### Post by glenngds2007 on 2008-11-25
Brother HL2140 works if you specify HL2060 instead of the HL2170 which the printer setup recommends.

---

### Post by seiserres on 2008-11-29
I installed Ubuntu 8.10 (Intrepid ibex) via Wubi installer in a Satellite A300-1II laptop (Wubi, as you sure know, allows you install and uninstall Ubuntu as any other Windows application). Restricted Drivers Manager did not work out for the graphic card so Drivers for Ati 3470 were downloaded from ATI [http://ati.amd.com/support/drivers/linux/linux-radeon.html]("http://ati.amd.com/support/drivers/linux/linux-radeon.html") and installed manually following the procedure described in [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually")
I hope it helps other Satellite A300 users.

Regards,

Characteristics

Processor:Intel® Core™2 Duo Processor T5800
Processor Type:Core™2 Duo
Processor Number:T5800
Processor Speed:2.0GHz
Front Side Bus:800MHz
Memory Size:4096MB
Memory Speed:PC6400 DDR2 800MHz SDRAM
Display Size:15.4" widescreen
Display Type:WXGA with TruBrite® Technology
Display Resolution:1280x800, Supports 720p content
Graphics Engine:Intel® Graphics Media Accelerator 4500MHD
Graphics Memory:128MB-1294MB dynamically allocated shared graphics memory
Hard Drive Size:320GB
Hard Drive Speed:5400rpm
Secondary Hard Drive Size:No Secondary Hard Drive Installed
Optical Drives: DVD-SuperMulti (+/-R double layer)

---

### Post by vishalrao on 2008-12-01
Quick success report:

See [https://lists.ubuntu.com/archives/ubuntu-in/2008-December/004358.html](https://lists.ubuntu.com/archives/ubuntu-in/2008-December/004358.html)

"[ubuntu-in] Ubuntu Intrepid 8.10 works very well on Acer Aspire 4730z laptop"

Hello,

Just another post (so that others might find it by search) about an
Ubuntu smooth run.
Will be useful I guess for anyone looking to purchase an
Ubuntu-friendly laptop...

Installed Ubuntu 8.10 Intrepid Ibex (amd64 desktop edition but 32bit
should be fine too) Linux on
a coworker's new Acer Aspire 4730z laptop.

Installation went fine and *everything* (LAN, video, sound, wifi,
special buttons, trackpad, compiz
effects etc) worked out of the box upon first reboot with absolutely
no additional configuration/tinkering :-)

Just wasn't able to try the card reader and the webcam was showing
all-green picture in ekiga... I ran an update but wasnt
able to reboot to check whether webcam might work better since we
(coworker and I) were leaving for the day.

Very impressed with this Intel-Montevina-based laptop... onboard Intel
graphics (compiz effects work) and Atheros based wifi.

- Vishal

PS: Also saw on a tech forum post that Hardy 8.04 worked fine on this
same laptop model.

---

### Post by Garric on 2008-12-01
Ubuntu 8.10
Graphics Card
Xfx (Nvidia partner)
XFX 9500GT 680MHz Edition 256MB DDR3 Dual DVI TV Out PCI-E Graphics Card

---

### Post by bubblefish on 2008-12-02
With Ubuntu 8.04 on an Asus motherboard, HP LaserJet 5L works great. Set up through Netgear PS 101 mini print server wired to network hub. Uses AppSocket setup.

---

### Post by jdc.84 on 2008-12-04
Ubuntu 8.1 installed earlier today.

Fujitsu Siemens Amilo M 1420

Mem upgrade to 1 gig

Everything so far seems to be working with one execption...

The memory card reader built into the front isn't seen anywhere

---

### Post by jdc.84 on 2008-12-04
oh...

the fan seems to be on all the time now. Music has to be on to try and drown out the mind numbing sound of the fan.

---

### Post by Riverside on 2008-12-05
Ubuntu version: 32-bit 8.04.1
Case: Antec P182
PSU: Corsair HX620W
Motherboard: Intel DP35DP
Graphics Card: Gigabyte GeForce 8800GT 512MB
CPU: Intel E8400
HDD: Samsung Spinpoint HD642JJ 640GB
Optical drive: Pioneer DVR-215BK
Memory: 4GB kit Crucial DDR2 PC2-5300
Mouse: Logitech MX620
Keyboard: Microsoft Natural Ergonomic 4000
Monitor: Iiyama B2403WS 24" widescreen

All working perfectly with 8.04.1 including onboard sound.  More detail at:

[http://forums.hardwareguys.com/ikonboard.cgi?act=ST;f=14;t=6566](http://forums.hardwareguys.com/ikonboard.cgi?act=ST;f=14;t=6566)

---

### Post by StormWalker on 2008-12-06
Ubuntu 8.10 64-bit
Graphic Card
Radeon HD 4850 512MB 256-bit 
MSI Radeon


Thank You.

---

### Post by boblee on 2008-12-09
Dell Precision M90 laptop workstation:
2.0 GHz Core 2 Duo T7200, 4Mb cache | 2Gb (2*1024) Samsung DDR2-667 5.0-5-5-13 | Seagate Momentus 7200.1 100GB 7200, 8MB cache | NVIDIA Quadro FX2500M, 512Mb, driving 1920x1200 LCD | Maxtor 3200 USB2 500GB 7200, 16MB cache | Sony DVD+/-RW DW-Q58A | Broadcom gigabit ethernet

The processor is not recognised, but runs, and is correctly shown as two cores.
The video card - the OpenGL version of the G71 core as used on 7900GTX - is not recognised, shown as an 'unknown device 029a', but runs at native resolution and full color depth. Adding the NVIDIA-supplied binary driver enables full OpenGL support which works well.
:guitar:

---

### Post by candela on 2008-12-10
1)Version Of Ubuntu : 8.04 Hardy Heron and 7.04 Feisty Fawn, Gnome 

2)Type Of Hardware : Laptop

3)Hardware Maker : Benq

4)Hardware Model : Joybook 7000

With Feisty every thing worked very well (thanks a lot)

With Hardy verything works ok but the temperature. The computer gets very hot because the fans don't start soon enough and i cant find a fan controller. I have an ATI MOBILITY RADEON 9700 with opensource x.org drivers and i can use the sensors and cpu scalling monitor applets to see the temperature. I have look in internet and in previous kernels it was possible to make a script to control fan speed through acpi but new kernels doesnt allow to write. I read that the ati propietary driver can control the fan but i much prefer to suport free software. I hope that in next realeases you can give us a solution. also, i detected that scrolling firefox 3.0.4 makes the computer very very hot but using other programs as kino (video) not  (thanks again for theses os)

---

### Post by tubbygweilo on 2008-12-12
Lenovo ThinkPad SL500 2746 - Core 2 Duo P7370 2 GHz - 15.4" TFT
2 GB (installed) / 3 GB (max) - DDR2 SDRAM - 667 MHz - PC2-5300 ( 1 x 2 GB )
NVIDIA GeForce 9300M GS - 256 MB
15.4" TFT 1280 x 800 ( WXGA ) - 24-bit
Intel WiFi Link 5100

Dual boot Vista Business 32bit Ubuntu 8.10 64bit

Nvidia restricted driver version 177 via Ubuntu repository

---

### Post by LinuxGuy1234 on 2008-12-13
Acer Aspire 5315-2153. Almost works out of the box. The new kernel supports sound, old ones don't. Only thing not working working out of the box is wireless.

---

### Post by dovalize on 2008-12-14
Hi,

I'm new...
My Specs:
Ubuntu 6.10
IBM X61 laptop workstation

It works great. Anyway, just wanna try out the function as I'm planning to switch back to windows and than get a dual boot, perhaps.

---

### Post by _geordi_ on 2008-12-14
Version(s): Ubuntu 9.04 / jaunty (32 & 64 bit)
Type of hw: graphics card
Vendor:   : Powercolor
Model     : ScS3 Radeon HD4650 (RV730 PRO) 512MB passive cooling

Works with the proprietary ATI fglrx driver (v 8.561).
should work with the next version of radeonhd (v 1.2.4), not tried.


System:
M/B: ECS Elitegroup A770M-A (AMD 770 + SB600)
CPU: AMD X2 BE2400 (2x2.3GHz)
RAM: 2GB DDR2-800

---

### Post by amdalex on 2008-12-14
Ubuntu 8.10 32 bit
Home build
Mobo-      Gigabyte GA-MA69G-S3H
CPU-       AMD Athlon 5000+ X2
RAM-       2gb DDR-2 800
CD/DVD-    Lite on DVD CD burner
GPU-       MSI Nvidia 8400GS
Sound-     Onboard

Everything works great. I installed Ubuntu then I installed the restricted Nvidia driver which it told me to do. Sound worked after install, no issues. :biggrin:

---

### Post by el02 on 2008-12-17
Ubuntu 8.10

DELL Latitude D630 laptop:
Intel Core 2 Duo CPU T7250 @2.00GHz | 2GB (2*1024) RAM | 160GB harddisk | Intel Mobile GM965/GL960 Integrated Graphics Controller | Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet | Broadcom Corporation BCM4312 802.11a/b/g Wireless | CD/DVD-RW

Wireless switch (located at left side) works perfectly to turn on/off wireless radio.

Standby, hibernate, wake up: no problem at all.

---

### Post by Nelsinius on 2008-12-17
Ubuntu 8.04
MSI K9MM-V MoBo
AMD64 Athlon X2 4000+
1 GB DDR2 PC2 5300
320 GB SATA Seagate HD
Nvidia GeForce FX 5500 256 MB DDR PCI
Lexmark X1240 All-in-one (with Z600 driver from [http://ubuntuforums.org/showthread.php?t=159704&highlight=Z600](http://ubuntuforums.org/showthread.php?t=159704&highlight=Z600))
HP Deskjet F2210 All-in-one (with HPLIP from [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html))
Dynex media reader (SD, MMC, SM, CF, MS)

---

### Post by scashcrate on 2008-12-20
Thanks


[http://cashcrate.com/889663](http://cashcrate.com/889663) 
It really works, try it, its free!

---

### Post by sprince09 on 2008-12-22
Gateway M-6862 Laptop
    - ATI-Raedon HD2600 video card
    - 4GB RAM
    - 2 x 2.2 GHz Intel
    - Intel Wireless Card (a/b/g/n)

I got Ubuntu 8.10 to work completely:
    - Install from live CD
    - Uninstall compiz and compiz core (caused problems installing raedon driver for me)
        sudo apt-get autoremove compiz
    - Get updates
        sudo apt-get update;sudo apt-get install upgrade
    - Reboot (maybe not necessary, but I always do after updates)
    - Get/Install envyNG (use to install raedon driver)
        sudo apt-get install envyng-core
    - Install Raedon driver with envy
        envyng -t
    - Reboot (again, maybe not necessary)
    - Re-install compiz if desired
        sudo apt-get install compiz
    - Reboot one last time just to make sure everything is set up properly

Now you should be running Ubuntu 8.10 :)

---

### Post by itsStephen on 2008-12-25
The Logitech LX310 keyboard and mouse set works fine with Kubuntu 8.10

---

### Post by armandh on 2008-12-25
DDS-32 printer works on LP1 with the Hatachi ddp-70 driver
including duplex [2 sided] no other features
no luck networking. [network printing in XP with win 2K beta drivers.][NOW SOLVED}

no luck so far with its close cousin [IBM infoprint 40]

---

### Post by FrankT-Qc on 2008-12-26
Hello !

Here's the desktop I just assembled : 

Motherboard : Asus M2N-MX SE Pro (Bios version 0503)
CPU : Amd Athlon X2 5000
Mem : Kingston 2048 MB DDR2 800
HDD : Seagate Baracuda SATA 3GB/S 500GB 32MB Cache
OPTICAL : LG GH22NS30

OS : Ubuntu Intrepid Ibex (8.10) 64 bit (32bit live CD works great too)
Display Driver : NVIDIA version 177

What works : Basically everything (Sound, Graphic, Compiz, USB, CD/DVD reading and burning)

Problems out of the box : 
- CPU Frequency scalling not working

- Window Title bars glitch and change color every now and then, not that big of a problem...

Have fun
Frank

---

### Post by andrewmv on 2008-12-26
Ubuntu 8.10
Kensington Slimblade mouse

All standard and special functions work out of the box, without any drivers or configuration.

The middle button is correctly emulated by chording the left and right buttons together (there is no physical middle button on this mouse), vertical and horizontal scrolling via the trackball both work.

The media buttons on the back of the mouse correspond to the XF86 keyboard shortcut keys for volume up, volume down, play/pause, previous track, and next track, and accordingly they integrate neatly into most media player programs.  The volume buttons control the system volume from any program.

---

### Post by Strid on 2008-12-30
Works out-of-the-box under Ubuntu 8.10 (Ibex):

**Xerox Phaser 6130/N color** laser printer, connected via. USB.
Plugged it in and turned on my computer and it was already recognized when I open the "Printer configuration" app. 

Please note that this is about the only small Xerox Phaser color laser printer that boasts Linux support from Xerox.

---

### Post by arohanui on 2008-12-31
Ubuntu version: 7.10
Type Of Hardware: Monitior
Hardware Maker: Viewsonic
Hardware Model: VA2226w

Out of the box.

---

### Post by AKADAP on 2009-01-01
Ubuntu 8.10 64 bit
Motherboard: Asus P6T Delux
Processor: Intel Core i7 920
Disk: Seagate 1.5 TB SATA drive
Optical Disk: LG Blu-ray/HD DVD-Rom & 16x DVD +-R DVD Burner (SATA)
Video: Powercolor AX4850 Radion HD4850 512MB.
Monitor: Dell UltraSharp 3008WFP using DisplayPort.
Mouse: Compaq CPQ750TP

Notes: Had to use video safe mode to install or I would end up with the monitor sleeping forever early in the install process. Once installed, changed to proprietary hardware driver from ATI to get full resolution.
Currently both the optical and coax digital sound outputs do not function. Analog outputs work fine.
Optical drive works for reading, have not yet tried burning a disk yet.
Mouse only works in compatibility mode, scroll ball only works as a scroll wheel (no horizontal control).

---

### Post by Raynman37 on 2009-01-01
Ubuntu version 8.10

LG GH22 22x Internal Super Multi DVD Rewriter: Works out of the box, no need for install CD.

Note: Make sure you have the jumper settings right :P

---

### Post by Aging Technogeek on 2009-01-02
Just installed Intrepid on a Dell Precision M60 workstation - Intel Pentium M 1.7 ghz, 2 gbyte ram, 60 gbyte HDD, Nvidia QuadroFX 700 (128 mbyte video mem.), Intel PRO/Wireless 2200BG wifi card. Easy install; everything working well. This is my first experience with linux OS. It is not as difficult as I was led to beliieve. Will definitely keep using Ubuntu or other linux distro.

---

### Post by cmay on 2009-01-06
video cards.

albatron:nvidia geforce 8400 gs

msi: nx7300 td256eh

motherboard:
msi:k9agm4

this works with ubuntu 8.04 , 8.10 and jaunty  jackalope.

---

### Post by frankelr on 2009-01-07
Ubuntu Intrepid amd64
Ubuntu Hardy amd64

works well with HP slimline s3600z

2 and 4 GB

---

### Post by kelvinblank on 2009-01-10
Currently using ubuntu 8.10 32-bit in my compaq cq40-107au

Specs:

AMD Athlon x2(1.9Ghz)
ATI Radeon HD 3200
2GB DDR2 667 
160GB HDD

All goes fine except when going to suspended mode, when loging in back, the keyboard is not responding (all buttons). I dont know if my integrated mic is working but the touchpad, sounds, integrated cam,USB mouse. I didnt try if i can connect using wifi since im using a wired network. video and sounds are ok. im currently using dual boot OS with Windows Vista - Starter(32-bit).

---

### Post by markbuntu on 2009-01-10
Ubuntu 8.04 32 bit and 64 bit, 8.10 64 bit, Mandriva 2009 One

Biostar TA790GX A2+ motherboard
AMD Athlon X2 6000 cpu
Corsair 800MHZ Ram 6GB (2 2GB, 2 1GB)
ATI HD3650 1GB PCIx16 gpu
SIIG Soundwave 7.1 PCI ( C-Media 8768 chipset )

---

### Post by ipatt on 2009-01-12
Hello, this is not strictly a compatibility issue nor is it only restricted to laptops. I encountered the problem on a laptop which is why I am posting it here.

 The "difficulty" was encountered after a Ubuntu 8.04 install and was intermittant. I tried previous Ubuntus (I have them back to 5.04 but did not go that far) with the same maddening failure. The machine would hang usually working with OOo. Much head scratching led me to suspect a hardware failure so I ran a memory test (Memtest86+ v 1.70) but all was OK and since I have a Hitachi drive I ran Hitachi's drive fitness test (DFT). Of course the laptop manufacturer's diagnostics revealed nothing and the machine was out of warranty.

 Still the problem persisted so I went looking for other tests. Among my search I discovered that there is an upgrade to Memtest86+; the current version is 2.11 and is more thorough than version 1.70 included in Ubuntu. I tried it and BINGO! after running it for ~5 1/2 hours I got memory errors. Replacing the SODIMM cured my problem.

 I hope that this might be useful to someone and is also a plea to the folks at Canonical to replace Memtest86+ v 1.70 with the newer v 2.11 in future distributions.

---

### Post by bendib on 2009-01-12
ubuntu 8.10 with just about every Desktop environment you can think of. along with nimblex linux and puppy linux installed on the same partition sometimes ran in virtualbox via iso file.
sony vaio pcg-nv170 notebook, made in 2001.
256 MB ram
1.5 ghz intel pentium four CPU
Every feature works perfectly.

---

### Post by beastrace91 on 2009-01-15
K/Ubuntu - 8.10
Asus F3Ka
GFX Card - Radeon HD2600 Mobility (512 Meg)

Issue: The live CD will not boot.

Solution: Download the alternate CD and one you have everything installed let the system try to boot then press ctrl+alt+f1 to get to a terminal login once you are logged in and at a console screen run the following: ```
sudo apt-get update
sudo apt-get upgrade
``` (I am not sure if it is needed but at this point I would always reboot the laptop and relog in) Once you are logged in again run the following lines: ```
sudo apt-get install build-essential xorg-driver-fglrx
sudo aticonfig --initial -f
``` After that finishes reboot boot once more and you should now have a login window :)

________

Ubuntu - 8.10
Asus G1Sn
GFX Card - nVidia 9500M GS (256 Meg)

Works like a charm so long as you have 2 gigs of ram or less.

~Jeff

---

### Post by raptor2552 on 2009-01-19
Ubuntu 8.10 64 bit with all current updates installed

Asus P5Q-E motherboard - AMI BIOS ver 1306 
	- Northbridge:  	Intel P45
	- Southbridge:  	Intel ICH10R
	- High Def Audio ADI AD2000B
	- LAN 2 x 10/100/1000Mbps Gigabit
	- ATI CrossFireX ready (Drivers available for Radeon 4800 series cards only)
	- Hardware RAID 0, 1, 5, 10 (no drivers needed)
	
Intel E7300 Core 2 Duo Processor, Socket 775, 45nm Multi-Core

OCZ Dual Channel 4096MB (2 x 2048MB) PC6400 DDR2 800Mhz Memory,  8 GB installed
	- model# OCZ2P8004GK (Recommended by Asus' VCL)
	
 Visiontek Radeon HD 3870 Video in PCIe x16 slot (system loaded latest correct driver and ATI Catalyst Control Center)
 
 CompUSA brand DVD writer 	DVD DW 8X16X8X16
 
 SATA Wetern Digital Caviar WDC WD3200AAKS-0, 320 GB HDD, 1 installed
 
 SATA Seagate Barracuda ST3160815AS, 160 GB HDD, 2 installed
 
 PC Power & Cooling 750-Watt Power Supply 
 
 Northgate OmniKey 102 keyboard (USA)
 
 Logitech Optical USB mouse
 
 Wacom Graphire tablet
 
 Dell S2409 LCD 16:9 format monitor using DVI interface (system correctly found and  set 1920x1080 res)
 
Comments: 
All hardware works flawlessly without having to hunt down drivers. The Audio sounds fantastic, and this setup is fast. 
 
BIOS SATA configuration is set by default to IDE compatability which needs to be set to AHCI in order to take advantage of the high speed SATA 3 Gb/s interface. This board comes with a fall back BIOS chip (redundant) and needed to set the BIOS to Keep Last Setting.
 
Both cores of the CPU where recognized as well as all 8 Gig of RAM. I'm running a guest OS Windows XP as a virtual machine (Virtualbox 64 bit) and is the reason I decided on 8 Gig. I have a need for my Sony Visual Studio software that seems to run better as a virtual machine than natively in Windows.
 
 There was one issue I noticed with the Radeon card; the video flickered during playback in VLC with Compiz enabled. This was fixed by setting VLC to use X11 as its output mode. 
 
 MikeMc

---

### Post by Aeling on 2009-01-26
Ubuntu Hardy
Laptop
MSI GX710

I tried Intrepid first, but after 4-5 hours of trying to install while waiting for the Hardy ISO to download Hardy worked just fine. Proprietary drivers for the ATI graphics card + madwifi drivers for the Atheros card worked with pretty simple setup, and bluetooth worked out-of-the-box. Webcam is as yet untested; no need for it.

---

### Post by raunhar on 2009-01-27
Ubuntu 8.10
Hardware : benq Scanner
Model :5000 USB scanner
Problem: Ubuntu does not detect the hardware

---

### Post by IdahoBackwoods on 2009-01-27
Running 64-bit Ubuntu Linux 8.10 (Intrepid Ibex) on

Toshiba Satellite P305-S8904 (PSPC8U-01400Q)
---------------------------------------------------------------
Intel Core 2 Duo T6400 @ 2.0GHz
Intel GM45 Express chipset
4GB PC6400 DDR2 800MHz
Intel GMA 4500MHD graphics, shared memory
17.0" TFT LCD display, 1440x900 resolution, supports 720p
Intel Wi-Fi Link 5100AGN
10/100 Ethernet
3 USB 2.0 ports, one FireWire port, one eSATA/USB port
DVD SuperMulti double-layer optical drive
104-key keyboard with separate numeric keypad
Intel ICH9 family 82801I HD audo controller
Chicony webcam

----------------------------------------------------------------

Everything worked in Intrepid with little trouble installing, except that 3D graphics in apps like Google Earth are broken.  As I understand it, this problem that has been reported in all flavors of Linux, and is probably the fault of the Intel video driver.

---

### Post by uberdonkey5 on 2009-01-29
HP 1005
(and probably most Hewlett Packard printers)

on Hardy (8.04) installed drivers DO NOT WORK.

However, go to this site and choose automatic installer:

[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

---

### Post by thepizzaman on 2009-01-29
just added a sapphire HD3650 and works great

---

### Post by saggitheman on 2009-01-31
Dell Latitude D600

Processor: Intel Pentium M (1.80 GHz)
RAM installed: 512 MB DDR SDRAM (2 x CPU cards, Each in 250++. But says 512)
Network: Broadcom wireless card (built in)
HardDrive: 80GB Hitachi HDD
Screen: 14.1 SXGA+ (1400x1050) display
CD: DVD/CD-RW
Softwear: Linux Ubuntu Intrepid Ibex 8.10
Battery: Standard. (if i use computer constantly it works maximum 1 hour - 50 min, but it is a wery old battery)

It works comletly problem free. All drivers works from installation. (Have to enable wireless card) It can seem a little bit slow, but only when i have all Compiz effects enabled and firefox + amarok + pidgin + a little other stuff. 
I think it works better than Windows. Faster if i don't run Compiz-Fusion.

---

### Post by grispa on 2009-02-01
**SONY VAIO FW21E [LAPTOP]**

*Ubuntu ver.*: Intrepid Ibex (8.10) kernels 2.6.27-9 through 11 AMD64
*Processor*: Intel Core 2 Duo T8400 2,26 Ghz 3MB - L2 on Centrino 2 Platform
*Chipset*: Intel PM 45 Express 
*Memory*: 4 GB (2x2MB) DDR2 SDRAM 800Mhz
*HD*: 320 GB Serial-ATA-150 5400rpm 8 MB cache
*Audio*: Realtek ALC262 HD audio Microsoft WSS 1.0/2.0 compatible
*Graphic*: ATI Mobility Radeon 3470 256 Megabytes DDR - II (1.4 GB shared), w ATI UVD Engine, VGA D-SUB, HDMI w HDCP, DX 10.1.
*Display*: 16.4" WXGA++ TFT, 1600x900, X-Black
*Opt. Drive*: Optiarc DVD±RW (±R DL) / DVD-RAM / BD-ROM
*Wireless Adapter*: Intel Pro Wireless 5100 a/b/g/n(draft) w Bluetooth 2.1 EDR
*Ethernet Adapter*: Marvell Yukon Gigabit Ethernet
*Various*:
    * Modem/Fax 56k
    * Webcam 1.3 Megapixels
    * 3 porte USB 2.0
    * Jack Audio in Audio Out
    * Kensington Lock
    * MMC SD card reader

**_All devices worked perfectly without any intervention needed_**, except for the graphic drivers (ATI's are needed for 3D acceleration).
It is yet (01 February 09) unavailable support for "fn" keys, including the fn-activated numpad and scroll-lock, though it is available a patch for the brightness adjustment keys.
The external keys work with the exception of the S1 (suspend) and AV MODE (switch to external display) ones.

---

### Post by bdcollignon on 2009-02-06
Ubuntu version: Tested on Ubuntu 8.04 and 8.10

Hardware: Brother DCP-7030 all-in-one B&W printer and scanner

Works well, with the following installation procedure and restrictions:

1. Installation:
Simply follow the instructions given at the Brother website:
- [http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)
- Be sure to follow all instructions, including the "Pre-required procedures" (for 8.04 & 8.10: [http://solutions.brother.com/linux/en_us/before.html#002](http://solutions.brother.com/linux/en_us/before.html#002))
- Installed printer first (Cups, Cupswrapper Driver Install), then scanner, and finally Scan-key
- You may get 2 DCP-7030 printers by the end of the installation. Just delete the one with the wrong URI (Should be: "usb://Brother/DCP-7030")

2. Restrictions:
- As in many cases, Linux drivers are not as optimized as Windows ones. Slower and less functions (eg Poster function unavailable under Linux).
- Attention: I have encountered problems with printing of files over 100-200KB when Scan-key is activated. How to stop Scan-key: terminal command "brscan-skey -t" (See: [http://solutions.brother.com/linux/en_u](http://solutions.brother.com/linux/en_u) … html#Inst2). And if you decide to un-install Scan-key, make sure you stop it before, or you may still have the printing problems after un-install. Once Scan-key is stopped, everything works perfect again.

---

### Post by hadji457 on 2009-02-06
Ubuntu 8.04
Laptop
Gateway 450ROG
 Everything works out of the box. This is the only distro in which suspend to ram and suspend to disk actually works. That is the main reason I settled with hardy on this machine ( and I've tried many distros ).

---

### Post by maxino on 2009-02-07
Ubuntu 8.10
(ancient) Nvidia GeForce 6200 (driver vers. 177.82)
(even more ancient) Desktop IBM Netvista P4 2GHz

just added an Asus VH226H 1920x1080 monitor.
Absolutely nothing to do, worked instantly, perfect resolution, pin sharp text

maxino

---

### Post by uberlinux on 2009-02-08
MSI Wind Desktop : Ubuntu 8.10
**[COLOR="SeaGreen"]Everything works flawlessly![/COLOR]**

MSI Wind details:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856167032](http://www.newegg.com/Product/Product.aspx?Item=N82E16856167032)

[COLOR="Blue"]CPU Type  	Intel 1.6GHz Atom processor on board
FSB 	533MHz
Chipset
North Bridge 	Intel 945GC
South Bridge 	ICH7
Memory Supported
Memory slot 	1 x 200Pin
Memory Type Supported 	DDR2 533/400
Max Memory Supported 	2GB
Expansion Slots
Other 	1 x CF Slot
Storage
Serial ATA 	2 x SATAII 300
Graphics
Onboard Video 	Intel GMA 950
Audio
Onboard Audio 	Realtek ALC858
Channel 	8 Channel
Communications
LAN 	Realtek 8111C(10/100/1000Mbps)
Max LAN Speed 	10/100/1000Mbps
Extension Bays
3.5" Internal Bays 	1
5.25" External Bays 	1
Front Panel Ports
Front USB 	2
Front Audio Ports 	2 jacks
Card Reader 	SD/MMC/MS/XD
Back Panel Ports
VGA 	1 x D-sub
Rear USB 	4
RJ45 	1
Rear Audio Ports 	6 jacks
Power Supply
Power Supply 	External 65W Power Adapter with Active PFC[/COLOR]

---

### Post by FrankT-Qc on 2009-02-09
Hi again !

Here are the details of a few computers running under Ubuntu. You might also want to go to the end to look for a few extra peripherals.

#1 :
Starting from a Dell OptiPlex GX260
Motherboard :  Dell 02X378
CPU : Intel Pentium 4 2.66GHz
RAM : 512MiB DDR 266 MHz (3.8 ns)
HDD : Western Digital WDC WD400BB-75JH 40GB EIDE5ce15c
CD :  Sorry, impossible to read the stickers... some generic cdrom...

Added to the OptiPlex package : D-Link DGE-530T Gigabit Ethernet Adapter 

Ran for many months under Hardy x86 Server without a glitch
Running since a few months under Intrepid x86 Server without a glitch

#2 :
Starting from a Seanix Desktop : 
Motherboard : Intel D845GRG
CPU : Intel Pentium 4 CPU 2.40GHz
RAM : DDR 266 MHz 2x 256MiB
HDD : Western Digital WDC WD400BB-00JH  40GB EIDE
CD-R/CD-RW writer, can't read the stickers

Added to the Seanix package : D-Link DGE-530T Gigabit Ethernet Adapter 

Has run under Hardy x86 for a few months without any problem
Running since a few months under Intrepid x86 without any problem

#3 : 
Home made desktop computer :
Motherboard : Asus M2N-MX SE Plus
CPU : AMD Athlon 64 X2 5000+
RAM : Kingston DDR2 800 MHz 2GiB (2x)
HDD : Seagate Baracuda ST3500320AS SATA II 500GB
DVD : LG GH22NS30 (22x DVD+/-RW)

Running since a few months under Intrepid amd64, I've had a few problems with DVD burning at full speed (when you fail in the middle of a DVD burning operation, the reader stops working until reboot. By the way, not such a good burner but works anyway). 

#4 : 
Starting from a (Old and beat up) Seanix Desktop :
Motherboard : Intel D850GB
CPU : Intel Pentium 4 CPU 1400MHz
RAM : RIMM RAMBUS 400 MHz (2.5 ns) 2x 64MiB and 2x 128MiB
Ethernet : Realtek RTL-8139/8139C/8139C + capacity: 100Base-T
HDD : SAMSUNG SV4084H 40GB (EIDE)
CD-R/CD-RW writer, can't read the stickers
DVD-ROM, can't read the stickers

Has run under Hardy x86 for a few months without any problem
Running since a few months under Intrepid x86 without any problem
(for those interested, has run FreeBSD for a short while and everything worked fine)

#5 : 
LG Notebook P1-KP01F1 (LG P1 Pro Express Dual)
CPU : Intel Core 2 T5600  1.83GHz
RAM : DDR2 667 2x 1GiB

Has run for a few months under Hardy x86
Has run for a few months under Intrepid x86
Running since a few months under Intremid amd64

Everything worked perfectly except for those problems :
Laptop speaker stops working a few minutes after the computer is turned on (under all versions of ubuntu; did not have this problem with Fedora or OpenSUSE) but the earphone jack works fine

Never could get any kind of sound recording, either Mic or Line-in
Installing the ATI driver under Intrepid amd64 was a little tricky : Bottom line you must, at FIRST boot, update you system and then install ATI's driver BEFORE any reboot

Other hardware that works fine :

Printer : Samsumg ML-1210 Laser printer : Works without any effort, shared with a few *nix clients and Windows clients without problem

Printer : Brother HL-2040 Laser (Driver : foomatic for HL-2060) Shared perfectly among *nix clients, for windows XP/Vista, use the HL-2060 and in the settings, turn off "advanced printing features" if printing seams to "hang"

Printer : 
Epson CX4450 : Well... The printer works but I never could get the scanner to work under Hardy. I never tried it with intrepid because I threw the thing away; it's the worst printer I've ever seen.

External hard drive :
WD MyBook Premium 500 GB, using the USB interface (just never tried the firewire). Works perfect. 20MB/s writing, 25 MB/s reading, quite the same as under windows. (Half NTFS, Half Ext3)

WD MyBook Home edition : 1TB using the USB interface, never tried firewire or eSATA. Works perfect. 20-25MB/s writing, 25-30 MB/s reading, quite the same as under windows. (XFS)

For both external hard drives, you won't get the capacity gauge working because you need a program that doesn't exist for Linux (feel free to try WINE if you can't live without another led flashing around your desktop...). Personally, I don't even install these on Windows boxes.

Have fun !
François ( questions : [email]francois.trahan@gmail.com[/email] )

---

### Post by jen1963 on 2009-02-11
Both the Gigabyte GA-MA790GP-DS4H motherboard and HP Photosmart C4480 All in one work like a charm in Ubuntu 8.10 intrepid; Ubuntu saw all my hardware without a hitch.

My Frankenbox Spec's:
Case: Antec Sonata III with a 500 watt Antec power supply
CPU: AMD Phenom X4 9950
Motherboard: Gigabyte GA-MA790GP-DS4H
Ram: 4 Gig of Kingston DDR2 Ram (PC2 8500) running at 1066 mhz
CD/DVD Drive: LG GH22NS30 (SATA)
Hard drives: 2 Western Digital WD5001AALS 500GB 7200 RPM SATA Drives


HUGGS,
Jen Cato
Systems Administrator,
tuxwerx.com
Grumpy Republican Blog:
www.tuxwerx.com/Blogs

---

### Post by neilevan814 on 2009-02-12
Hi could you tell me which Lite On DVD drive you have?  I ma looking to purchase one fairly soon for a new computer build.  Thanks a lot.

Cheers, Neil

---

### Post by praxis22 on 2009-02-12
Me?

A Lightscribe DVDRW SHW-16H5S 

[http://www.liteonit.com/global/index.php?option=com_content&task=view&id=31&Itemid=67](http://www.liteonit.com/global/index.php?option=com_content&task=view&id=31&Itemid=67)

---

### Post by mozkill on 2009-02-16
Is anyone running Ubuntu on a "Nvidia Ion" desktop yet? 

[IMG]http://hothardware.com/articleimages/Item1261/NV_SFF_reference_hand_2.jpg[/IMG]

---

### Post by usman4514 on 2009-02-18
HI guys I want to purchase a new laptop. Actually i want to boot my laptop from usb drive on which Linux is installed. I am interested in sony vaio. Is there any body guide me that which sony vaio laptop meet my requirements. thanks

---

### Post by Daystrom-CDW on 2009-02-19
Ubuntu 8.10
Laptop
Dell C400
PIII 1.2Ghz 
768MB Ram
20GB HD
Intel 2200 wifi card added (non-standard equipment, taken from a D5xx Dell laptop)

I had to disable COMPIZ otherwise it wouldn't boot after installation.  

_New Quick Fix_
Hit **Esc** at Grub boot menu
Boot recovery mode
Goto command prompt and run "Xorg -configure" (case sensitive capital "X")
/root/xorg.config.new will be generated
Take ONLY the settings for the "device" section(s) from xorg.config.new and overwrite the "device" section in /etc/X11/xorg.config
reboot

_Old Fix (takes a long time)_
To boot to console and have a wired network connection working I had to do the following:
Hit **Esc** at Grub boot menu
Hit **e** to edit default boot option
Highlight "kernel blah blah..." and hit **e** to edit
Remove **splash** and type **vga=773** then press enter
Press **b** to boot
At login prompt hit **ctrl-alt-F1** to get console login
To fix COMPIZ issue at the console I ran following commands:
**sudo apt-get update**
**sudo apt-get dist-upgrade**

This took a long time to download and install, I went out to dinner and it had rebooted and was working properly by the time I got back.

_Results_
There are still some minor video issues but it works.  As per Ubuntu 8.10 release notes there are bugs in the intel video driver for these old chipsets.  Via the GUI menus **System -> Preferences -> Appearances -> Visual Effects Tab -> "None"** is the setting you want to disable the COMPIZ effects.

_Video Card_
description: VGA compatible controller
             product: 82830 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation

---

### Post by neilevan814 on 2009-02-20
Version Of Ubuntu Hardy 8.04 32 bit
Asus M2N68-VM Motherboard
2gb Corsair XSM2 cl5 ddr2 Ram
AMD Athlon 64 x2 4850e 2.5ghz Processor
Lite-On DVDRW iHAP222-06  
Western Digital Caviar SE16 WD2500AAKS 250GB 7200 RPM SATA 3.0Gb/s Hard Drive 

So far this set up has worked great.  I am just now trying to troubleshoot the codecs issue and no being able to view dvd's in totem.

I only have this set up with a Dell CRT vga analog screen, usb logitech mouse, and IBM ps2 keyboard.

No hitches, just the dvd glitch so far

---

### Post by Niniel on 2009-02-20
8.10 Live CD
Dell Dimension XPS D333
PII 333 MHz, 192 MB RAM, nVidia Ti4200, Toshiba CD-ROM, 2 IBM hds on mainboard (10 & 8 GB), 2 more hds on Maxtor PCI100 card (2 x Maxtor 40 GB). MS Natural Keyboard (1st gen., via PS/2), MS optical trackball, Samsung Synchmaster 570V LCD monitor.

Runs without problems, although not surprisingly, slightly slowly. :)
I just needed GParted to examine/wipe a hd I want to throw away, so on a whim I put in the CD; I'm surprised at how well the OS runs. I don't plan on installing Ubuntu on that machine, but it looks like I could if I wanted to.

---

### Post by bodcod on 2009-02-21
1)Version Of Ubuntu: 8.10 Itrepid Ibex 32bit/9.04 32 bit
2)Type Of Hardware: Wireless pci card
3)Hardware Maker: Edimax
4)Hardware Model: EW-7128G (EU Model)

This is plug and play pretty much.
 Ubuntu regonised card , network manger pops up a message saying it has detected wirelees networks, I click on the message bubble up comes my wireless routers ssid , I cick on it enter my wpa2-psk password and it connects all in less than 2 minutes.

---

### Post by ajm422 on 2009-02-23
Intrepid Ibex 8.10 64-bit

BIOSTAR TA90GX Motherboard
AMD Athlon 64 X2 6000+ Windsor 3.0GHz CPU
G.Skill 4GB (2x2GB) DDR2 1066
WD Caviar Black 750GB HDD
Logitech PS/2 Mouse and Keyboard
ASUS VH222H 21.5" Monitor
LG 22x DVD+/-RW SATA DVD Burner

Plugged it all in and it just worked.  One minor problem:

The recommended resolution on the monitor is 1920x1080, but if I try to set it as such using the ATI drivers I downloaded it doesn't fill the whole monitor, and leaves black space around the edges.  I have to use 1680x1050 for it to fill the whole screen.  It's a long term problem I'd like to fix.

---

### Post by hellsgator on 2009-02-24
Acer 5715z
X3100 graphics card
dual core 1.87Ghz
160GB HD
3g RAM

Working just fine. No issue with 8.10, testing 9.04.

---

### Post by Kevoc on 2009-02-25
This system acts as a satellite receiver and media centre.

The system is based on an HP D530 small form factor PC with a microATX mainboard. The board is socket 478, supports 2 SATA devices, one low profile AGPx8 graphics card and has a PCI riser that supports two full height PCI cards. The system uses an 185W PSU, which is pretty amazing considering that the TDP for the CPU is 89 watts.

OS: Ubuntu Hardy 8.04 32 bit/Myth TV
CPU: P4 Prescott 2.8Ghz
HD: Samsung SpinPoint F1 500GB SATA-II 16MB Cache – OEM
RAM: 1 Gb, 2x PC2700 sticks
Graphics: PNY GeForce 6200 256MB Low Profile AGP Graphics Card (passively cooled)
DVD: Pioneer DVR-215DBK 20x DVD±RW SATA Dual Layer ReWriter (Black) – OEM
Receiver card: Hauppauge WinTV Nova S Plus
Monitor: Samsung SyncMaster 2233BW 22”
Networking: Netgear WG311 54Mbps Wireless Desktop PCI Network Adapter
Keyboard/mouse: Keysonic Wireless Keyboard/Touchpad ACK-540RF

I'm still trying to get the remote to work properly (surprise surprise) and need to replace the RAM to better complement the CPU.

---

### Post by neilevan814 on 2009-02-26
Hi have you tried your new monitor with a dvi or hdmi cable?  I am about to get this monitor and was wondering what your experience has been.  Thanks a lot.

---

### Post by Kevoc on 2009-02-26
> **neilevan814 said:**
> Hi have you tried your new monitor with a dvi or hdmi cable?  I am about to get this monitor and was wondering what your experience has been.  Thanks a lot.

If you are refering to the Samsung 2233BW, it only has D-Sub and DVI, it has no dedicated hdmi connector. However I do use the DBI and its fine, native resolution is correctly detected, desktop is fine, movies look fine too, though not as good as they would appear on a dedicated TV. It's far to bright out of the box though.

---

### Post by neilevan814 on 2009-02-26
Thanks Kevoc for the reply.  That helps a lot.  I am also considering the Asus VH226H.  Here's the link. [http://www.newegg.com/Product/Product.aspx?Item=N82E16824236051]("http://www.newegg.com/Product/Product.aspx?Item=N82E16824236051")  Do you think this would be much better?

---

### Post by Kevoc on 2009-02-26
> **neilevan814 said:**
> Thanks Kevoc for the reply.  That helps a lot.  I am also considering the Asus VH226H.  Here's the link. [http://www.newegg.com/Product/Product.aspx?Item=N82E16824236051]("http://www.newegg.com/Product/Product.aspx?Item=N82E16824236051")  Do you think this would be much better?

Presuming that you have a graphics card that will support the 1080p resolution then it looks like a good buy. It certainly gets good ratings on Newegg, and it also has a hdmi connector. I was tempted to go for a 1080p monitor myself but wasn't sure if my graphics card would support it. I did know that my GF 6200 would do 1680*1050 so I went for a monitor that would do that. Nice sized desktop, but I do get a slightly compromised TV experience, though it's not too annoying.

---

### Post by epidemiks on 2009-02-27
My new laptop :grins:

**Hardware:**

HP DV5 1139TX
Intel Core2Duo T9400 @ 2.53GHz
4GB RAM
400GB HD
Nvidia GeForce 9600M GT 512MB works ootb with restricted drivers
Intel 5100 AGN wifi
Touch sensitive buttons
Remote control
Lightscribe Dual Layer DVD burner

**OS:**

Intrepid Ibex 8.10 x86_64
2.6.27-11
Dual boots with Vista Home Premium (came with it, I didn't put it on:lolflag:)

**Everything working 100% out of the box except: **

[LIST]
[*]LED on MUTE touch sensitive button doesn't go red
[*]FF & RW on remote
[*]"Quickplay" touch button isn't assigned to any media player
[*]Doesn't resume from hibernate
[/LIST]

**Not yet tested:**

[LIST]
[*]4in1 card reader
[*]Lightscribe
[/LIST]

---

### Post by runemaste644 on 2009-03-02
Note that this has two different things in it, hope you dont mind.

This is my laptop.
Ubuntu 8.10
Notebook
Lenovo
3000 N100 | Screen 1680x1050 | AuthenTec AES2501 fingerprint reader | Broadcom bcm43xx wireless N card | dvd/dvdrw drive | Synaptic Touchpad | Ricoh ms/mspro/sd/mmc/xd card reader | digital audio | intel core 2 duo 2.2ghz | nvidia geforce go 7300 | bluetooth | 120gb sata drive | webcam | microphone

Things that work without drivers: DVD drive, Touchpad, SD card reader, Audio, bluetooth*
Things that work with drivers installable by the restricted drivers tool, add/remove or synaptic: Wireless card (no need to backup bcmwl5.sys) Nvidia card, Fingerprint reader, microphone**
Things that work with other drivers: Webcam (Get the microdia driver, it works great!) 
Things not working: MS/MSPRO/xD card reader.
*Note: the built in bluetooth radio was recognized out of the box, but I had to install gnome-obex-server to receive files.
**Note: I had to install the Gnome ALSA mixer settings to get it working.


This is just for a keyboard/mouse combo.
Version of Ubuntu: Ubuntu 8.04/8.10
Type: Wireless Keyboard/Mouse Combo
Manufacturer: Microsoft 0.o
Model: Microsoft Wireless Laser Mouse 6000/Wireless Laser Keyboard 6000 v2.0

Features that work (will update frequently as I test these out): 

Mouse: 
mouse has 5 mouse buttons (doesnt work so far)

Keyboard: 
25 hotkeys, including but not limited to: Browser fwd/back, home, documents, mail, zoom in/out, media controls, bookmark keys (Good luck configuring all of them)

I noticed the keyboard and mouse worked even before windows loads, so I thought it should work on Linux plug and play, which it does.

---

### Post by Screwdriver0815 on 2009-03-02
Ubuntu 8.10 on Lenovo 3000 N200 with Nvidia 7300GO graphics card, Intel WLAN chipset, 2 gb Ram, 250 Gb HDD, Intel soundchip

works nearly out of the box.

Improvements to be done: Nvidia screen-flicker Bug has to be fixed, cardreader doesn't work out of the box

---

### Post by HughHemington on 2009-03-03
I previously tried 8.04 on my HP Pavilion TX1000 laptop.  It came with Vista Home Premium.  When I tried to downgrade to XP Pro I found that the "NVIDIA GeForce Go 6150" was somehow not one because the NVIDIA drivers didn't recognize it.  In conjunction with the integration for AMD Turion, it was altered!

Ubuntu 8.04 did not recognize it.

It also would not work with the Broadcom wireless adapter b,g, (pre)N (a 4302 chipset I think)

Without video or wireless, I abandoned Ubuntu, going on to similar failure with Knoppix, and Mandriva -- nothing seems to support this thing.

I wanted to check here to see if anyone had any luck with 8.10.

A friend told me that the virtualization is really good -- much better than VMware, so I'll probably give 8.10 a try on my main desktop.

Is there a hardware compat. list?

Thanks,

---

### Post by cmay on 2009-03-08
i purchased this laptop x-one and it works straight out of the box with ubuntu 8.10
[http://www.linuxshoppen.dk/products.php?showvariant_id=6787](http://www.linuxshoppen.dk/products.php?showvariant_id=6787)

as a warning i been told that the model i have is a upgraded model and the original model that is used as base for these models is not working with linux due to some of the components in them. it was a matter of both sound and video card as i remeber it. 
however this configuration as mine has  works perfect with ubuntu.

---

### Post by Peter_L on 2009-03-11
Ubuntu 9.04 (Jaunty Jackalope) Alpha 5
Laptop
Sony
VAIO VGN-TT11M/N

To my surprise I've become an "alpha tester" of the upcoming release. "Jaunty" installed and runs well enough "out-of-the-box" on this Vaio. Only small niggles so far, but I haven't checked all hardware compatibility yet :D

Dual-booting with Vista OK.

Good work Ubuntu team!

Info:
I tried the three previous releases of Ubuntu on this laptop but all were unsuccessful! Each of the earlier releases exhibited some sort of display incompatibility (scrambled content) even when attempting to install in safe mode. Similarly using the "live" CD mode the display was useless. I also tried a text-only install of "Intrepid" but this fell-over at the partitioner stage.

Regards,
Peter_L

---

### Post by marinegundoctor on 2009-03-12
1)Version Of Ubuntu
  8.10 Intrepid Ibex
2)Type Of Hardware
  Printer
3)Hardware Maker
  Canon
4)Hardware Model
  PIXMA MP460

Ubuntu installed a generic driver upon plugging the MP460 into my usb port. I was prompted to search for a better driver and it brought up the list of manufacturers. I selected Canon and the PIXMA MP160. The MP460 was not listed but I have read in posts from last year (2008 ) that the MP160 driver works.
I have not tried to scan anything yet, but the printing is perfect.

---

### Post by fargly on 2009-03-14
uberlinux,
I have the same box and have been living in xorg hell for the last few days.  Would you mind terribly disclosing what kind of graphics resolution and monitor you have that's working?  

I have a Westinghouse LCM22W2 that I'm trying to configure to 1680x1050.  Under Ubuntu 8.10, 1368x768 (16:9) is the closest I can get.  I installed OpenSuSE 11.1 so I could access a tool (SaX2) other than VI :D to generate settings.  I'm running at 1600x1200 which still isn't right.  

If I could get a working xorg.conf, I could flip back to Ubuntu and get on with my life.

Any information you could furnish would be greatly appreciated.  Thanks.

-fargly


> **uberlinux said:**
> MSI Wind Desktop : Ubuntu 8.10
**[COLOR="SeaGreen"]Everything works flawlessly![/COLOR]**

MSI Wind details:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856167032](http://www.newegg.com/Product/Product.aspx?Item=N82E16856167032)

[COLOR="Blue"]CPU Type  	Intel 1.6GHz Atom processor on board
FSB 	533MHz
Chipset
North Bridge 	Intel 945GC
South Bridge 	ICH7
Memory Supported
Memory slot 	1 x 200Pin
Memory Type Supported 	DDR2 533/400
Max Memory Supported 	2GB
Expansion Slots
Other 	1 x CF Slot
Storage
Serial ATA 	2 x SATAII 300
Graphics
Onboard Video 	Intel GMA 950
Audio
Onboard Audio 	Realtek ALC858
Channel 	8 Channel
Communications
LAN 	Realtek 8111C(10/100/1000Mbps)
Max LAN Speed 	10/100/1000Mbps
Extension Bays
3.5" Internal Bays 	1
5.25" External Bays 	1
Front Panel Ports
Front USB 	2
Front Audio Ports 	2 jacks
Card Reader 	SD/MMC/MS/XD
Back Panel Ports
VGA 	1 x D-sub
Rear USB 	4
RJ45 	1
Rear Audio Ports 	6 jacks
Power Supply
Power Supply 	External 65W Power Adapter with Active PFC[/COLOR]

---

### Post by betterhands on 2009-03-16
Had great luck buying a new, relatively cheap Deskjet printer over the weekend:

1)Version Of Ubuntu - 8.10
2)Type Of Hardware - Printer
3)Hardware Maker - HP
4)Hardware Model - Deskjet 6940

worked out of the box.  and sometime after successful install and some test printing, an HP printer manager was installed/configured.  This printer was ready for Ubuntu.

---

### Post by frodon on 2009-03-17
New hardware:
Asus PQ5-pro
RAM 1066MHz Crucial Ballistix
Intel E7400 working at 3.5Ghz instead of 2.8Ghz
Nvidia 9800GTX+
Samsung spinpoint F1 1To
LCD samsung t220

All is working great and out of the box with ubuntu 8.10 intrepid ibex.

---

### Post by twyufe on 2009-03-17
Fujitsu Siemens Amilo Li 3910 notebook, with Core Duo T3200 (2 GHz) 3GB, 320GB, DVD+/-RW, 18.4-inch TFT.

Everything works with Kubuntu 8.10 x86_64, except for a few special keys (brightness). The touchpad does work after pressing Fn and F6 twice (instead of once for Vista). I haven't tried hibernating.

It does take some effort to get sound working; see [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810) for updating Alsa

Added on 4-4-2009: wireless works out of the box. However, when downloading big files, f.e. from my NAS, it stalls. The remedy is to install the latest version of the wireless drivers, as described here: [http://ubuntuforums.org/showthread.php?t=792092&page=26]("http://ubuntuforums.org/showthread.php?t=792092&page=26")

Kubuntu 9.04 x86_64 installs as well, only this has to be added in /etc/modprobe.d/alsa-base.conf
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=6stack-dig index=0

---

### Post by bcbotha on 2009-03-18
im running ubuntu 8.10 on my laptop. i have a amd dual core. how can i check if my processor is being used to the full? does ubuntu automatically read it as two processors?

---

### Post by opto-laptop on 2009-03-18
bcbotha,

right-click on the panel bar, select Add to Panel. From the list add System monitor. Under the resources tab you'll see a graph that will help.

---

### Post by bcbotha on 2009-03-18
Ok....thanks for that.

---

### Post by exozito on 2009-03-19
Ubuntu 8.10 Intrepid

Desktop Inkjet Printer

HP (Hewlett Packard)

DeskJet 840C

I just plugged it in once and after a few seconds, Ubuntu detected it as a printer and it worked. It's a very old printer btw, I had it since 1998 and its now just over ten years old.

---

### Post by diectus on 2009-03-21
HP Pavillion tx2000
ATI SBx00 azalia built-in audio card
After Intrepid install, and 258 updates... no sound--
try - "sudo gedit /etc/modprobe.d/alsa-base" in terminal no quotes
at the very end of the script add a line that says
"options snd-hda-intel index=0 model=toshiba position_fix=1" no quotes 
save - exit - restart - bingo! hope this saves others the HOURS of digging it caused me.

---

### Post by thelugnut on 2009-03-22
SONY VAIO VGN-NS105N
Processor - 2xIntel Core2 Duo CPU T5870 @ 2.0 GHz
Memory 4 GB
Display 15" 1280x800
Hard disk - 250 GB ATA Toshiba
Ethernet controller - Marvel Technology Group Ltd. 88E8055 PCI-E
                      Gigabit Ehthernet Controller
Printer - HP psc 1215 all-in-one
Web cam - Vimicro C-91C
Modem - Siemens Modem/Router SL2 - 141

Purchased the unit with Windows XP Pro installed. (Cost me extra from to *cough* upgrade from Vista.
Using Gparted , I partitioned the hard disk as follows:
sda1 - 5 GB - ntfs - Recovery
sda2 - 34 GB - ntfs - Windows XP
sda3 - 193 GB - extended
sda5 - 34 GB - ext3 - Ubuntu 8.10
sda6 - 34 GB - ext3 - not presently used
sda7 - 121 GB - fat32 - data
sda8 - 4 GB - linux swap

With respect to Ubuntu 8.10, everything worked "outof the box". I installed "Cheese" to check out the web cam and it picked it up immediately. Same thing with the printer. It was unbelievably simple. I did nothing but sit here and watch everything work. What a blessing! I used my AIPTEK vidcam to record a few frames of video on the PNY SD 1 GB memory card, and when I inserted the card into the built-in card reader it read it with no problems. I am not a "gamer" so can't comment on the performance there. I can't think of anything else to report, but am open to questions, if there be any.:D

---

### Post by nortexoid on 2009-03-25
Gateway NX100X
1.06Ghz Intel ULV Core Solo
Intel 945GM graphics
1GB DDR2 RAM
80GB SATA HDD
Intel "HDA" audio
UBUNTU 8.10 (wubi)

Audio doesn't work. Apparently some chap got it to work by flashing to the latest BIOS. I tried it and my computer failed to boot from any device. Had to purchase used NX100X motherboard just for the BIOS chip with original BIOS version! So maybe there is no problem with the latest BIOS, but the latest BIOS may not work! (I even reflashed the eeprom, removed from motherboard, on a chip programmer. Same problem.)

---

### Post by BFG on 2009-03-26
8.10 Intrepid
A lot of this is cut and paste so please ignore obvious.

Intel Core 2 Quad Q9550 2.83GHz 12M Cache S775 1333MHZ

Motherboard Gigabyte S775 Intel P45   GA-EP45-DS5
(haven't tested power efficiency yet, but all else works perfectly).

Corsair Memory 4GBKIT 
ATI Sapphire 512Mb Radeon HD 4670 PCI-Express VGA Card  "HD4670"
Worked on first install, improved using restricted drivers.  Not perfect.

Samsung SyncMaster 2232BW - Perfect.
Enermax Technology 385W 82+ ATX 84-88% Energy Efficent PSU
Western Digital 150GB VelociRaptor 10,000RPM SATA 16MB - Perfect
LiteOn 20X DVD-RW SATA LS black + Nero - Perfect

Wacom Bamboo tablet.  - Perfect, no driver needed.
Logitech 3dConnection Spacenavigator.  Worked after driver install.

Microsoft digital media keyboard 3000
Standard keys and volume keys work out of the box. Extended keys don't work.

HP Officejet 7310 All-in-one.
Does not work on ethernet, works perfectly on USB connection.

OCZ Rally 16Gb USB Flash drive - Perfect.
Canon Powershot S3 - Perfect.

---

### Post by Buzzygirl on 2009-03-26
HP Deskjet F380 (scanner-printer-copier) works 100% on all functions.

---

### Post by kennedy7 on 2009-03-28
I have an everex laptop the gbook VA1500V with gOS on it it mostly has via parts inside of it it has a chrom 9 igp graphics chip and ubuntu 7.10 works but uses the generic driver for it ubuntu 8.04 uses openchrome it is very buggy and doesnt work well, and 8.10 freezes unless i install in safe graphics mode. And also the audio jack doesnt work but the built in speaker works. But so far thats been the only bad computer ive ever put ubuntu on. All the other computers ive put it on have worked out of the box and done fine.

---

### Post by snocutt on 2009-03-30
1.)8.10 intrepid ibex
3.)lenovo
4.)g530

there are only two factory configurations for this model. I got the upgraded version. Everything works out of the box as they say. The one small issue is the "onekey" and "user defined" keys are not recognized at all.

---

### Post by ruf10 on 2009-03-31
> **bdcollignon said:**
> Ubuntu version: Tested on Ubuntu 8.04 and 8.10

Hardware: Brother DCP-7030 all-in-one B&W printer and scanner

Works well, with the following installation procedure and restrictions:



This is not true, see
[http://www.openprinting.org/show_printer.cgi?recnum=Brother-DCP-7030]("http://www.openprinting.org/show_printer.cgi?recnum=Brother-DCP-7030")

In short: works on *some* systems

---

### Post by rileinc on 2009-03-31
Ubuntu 8.04, 8.10, 9.04

CPU: Intel C2D E6750
Mobo: Gigabyte GA-P35C-DS3R rev 2.1
Video: Gigabyte Nvidia Geforce 8800GT 512MB G92
RAM: OCZ Reaper DDR2-800 2x2GB OCZ2RPR800C44GK
HDD: all Seagate barracuda series; Western Digital 74GB Raptor; Hitachi 1GB 7200rpm
Keyboard: NEC CKBM-001 (multimedia keys work, but do not function according to their labels. e.g., the eject button actually mutes all sound. This problem is experienced in Windows as well).
Mouse: Dynex DX-WOM2 5 buttons
Webcam: Logitech QuickCam Pro 5000 (works with Skype out of the box)

---

### Post by durward on 2009-04-02
HP Pavilion dv8315nr - EZ580UA
  AMD Turion 64 mobile Technology ML-34 1.8GHz
  1.00 GB Ram DDR - 2x512GB SODIMMs
  HDD: 
    1) Hitachi TravelStar IC25N060ATMR04-0 - 60GB - ATA
    2) Seagate Momentus ST9100825A - 100GB - ATA
  Optical: LG HL-DT-ST DVDRAM GSA-4084N
  Nic
    1) Broadcom 802.11b/g WLAN
    2) Realtek RTL8139/810x Family FastEthernet 
  Video: ATI Mobility Radeon Xpress 200 Series
  Sound: Conexant AC-Link Audio
  OS: Windows XP Media Center Edition w/ SP2
      Sun xVM Virtualbox Graphical User Interface version 2.1.4
      Ubuntu 8.04 - Hardy Heron - 
           Linux 2.6.24-23-generic #1 SMP i686 GNU/Linux

I installed the Sun xVM and then installed Ubuntu 8.04 as a virtual box. Sun xVM setup the networking automatically using the wired controller Realtek card routing to the Windows Broadcom wireless and my home network was available. I can connect to my local computers and to the internet. No fussing or fighting with Broadcom wireless incompatiblity in Linux.

I did the same using my HP Pavilion dv9008nr and my HP Pavilion dv9205nr. However, the Sun xVM on those uses the Broadcom wireless as the nic; these setup without any problems and run fine. Infact, Ubuntu runs faster under the Sun xVM box on my HP Pavilion dv9008nr than with Ubuntu installed directly on the harddrive as the main OS.

I also installed the Sun xVM on my desktop, a homemade unit with an AMD Phenom 9600 on an Asus M3A78 motherboard. I have Ubuntu 8.10 and Sun OpenSolaris under Sun XVM. I had tried Microsoft Virtual Box software, but it did not allow any USB connections through to Ubuntu; Sun xVM does.

---

### Post by maxino on 2009-04-04
Ubuntu 8.10 Intrepid Ibex.

Old IBM "NetVista" desktop, P4 2GHz.

Wireless mouse Nortek Activo WL Laser 2.4 with:
 - left button, right button,
 - wheel for vertical and horizontal scroll,
 - forward/backward browsing,
 - DPI selector (800/1600 dpi)

All buttons/functions work flawlessly after just plugging the receiver in.

---

### Post by Skara Brae on 2009-04-05
A colleague at work gave me the old, defective laptop of her kid-son, saying I could keep it for free if I could get it to work.
It just needed a new harddrive: it still works fine :-)

-oo-

Ubuntu version: Xubuntu 8.04 (Hardy Heron)
Type of Hardware: Laptop
Hardware maker, model: Compaq "Armada", E500

CPU: Pentium III, 500 MHz
CHIPSET: Intel 440BX/ZX/DX
GPU: Ati Rage Mobility, 8 MB RAM
RAM: 2 x 128 MB SDRAM (PC100)
HDD: WesternDigital Scorpio, E-IDE, 160 Gb (3 partitions: /root, /home, swap)
CDROM: 24x slimline CD-rom
AUDIO: Maestro 2E soundchip (ES1978 )
PCMCIA: Texas Instruments PCI1225
- PCMCIA 1: a 2-port USB 2.0-card (NEC Corp.)
- PCMCIA 2: a wired network card (brand Belkin, model F5D-5010)

All works fine (except for the screen, which turns black after about every minute, unless I use the keyboard/type, and for which I am searching the forums at this moment...).
 
I now use this laptop only for surfing and some simple word processing.

I had installed XP Pro "Corporate Edition" (...) on it, but that goes abit (too) slow on this old machine. I decided to try Xubuntu, hoping things would go (much) faster, but I am not really that impressed by the speed of Xubuntu (compared to XP Pro).
Still, I may keep Xubuntu on it.

Oh, btw, Ubuntu (7.10), on my desktop PC, rocks!!! OpenSUSE (10.3) on the other hand, in triple-boot with Ubuntu and XP Home, is crap... soon going to be replaced by Kubuntu.

---

### Post by dewbuntu on 2009-04-05
I have been using the following PC with Ubuntu for several years without error, just installed 9.04 Beta on an additional HD that I have, but have been running 8.10.

Compaq Evo D510 SFF
2.4 Ghz Intel
1 GB RAM
160 GB Maxtor
Cisco Aironet Wireless
nVidia GeForce 5200

Dewayne

---

### Post by jayleemor on 2009-04-06
My main rig is dual-boot with Vista 64bit (for gaming) and Ubuntu 8.10 64bit (for everything else)

1. Case:  Cooler Master HAF
2. CPU:   Intel Core2Quad (Q9650)
3. Mobo:  EVGA NFORCE 790i SLI FTW
4. RAM:   8GB mushkin DDR3 1600Mhz (4x2GB)
5. GPU:   (3x) EVGA GTX 280 (tri-SLI for Vista)
6. Sound: SB X-Fi Titanium Fatal1ty (PCI-e)
7. HDD:   (2x) WD 500GB Caviar Black (Vista/Ubuntu 8.10)
8. PSU:   ENERMAX REVOLUTION 85+ 1050W
9. Cooling: (2x) Coolit dual bay water coolers:
   a. 1 for CPU and 1st GPU
   b. 1 for 2nd and 3rd GPU's

All but SLI works fine.  Had to change Sound Card version in Creative sound card driver prior to install due to being PCI-e version.

---

### Post by rony0303 on 2009-04-10
evice 029a', but runs at native resolution and full color depth. Adding the N

---

### Post by cuteboysmith on 2009-04-10
Ubuntu version: 8.10
Type Of Hardware: graphics card
Hardware Maker:NVIDIA
Hardware Model: fx 5200
ubuntu does not recognise the card but when booted in windows xp it works fine...
help...

---

### Post by Yvan300 on 2009-04-11
For the guy above me, this is not the place to post problems :)

My computer is a dell inspiron 1501
Processor : AMD sempron 3600+
GPU: Ati raedon xpress 1150 but in ubuntu it says ati radeon 200 ?

Without the propieratary drivers you can't play games or use compiz. Like 5 fps when playing supertux racer with free drivers

Hibernation does not work but Suspend does.

---

### Post by kdashjl on 2009-04-12
Tested: Ubuntu Hardy 8.04 32 and 64 bits / Current: Intrepid 8.10 64 bits

• Processor: Intel Pentium Dual Core E2160 - 1,8 GHz, FSB 800 MHz, Cache 1 MB
• Motherboard: Gigabyte GA-945GCM-S2C, FSB 1333 MHz, 2xDDR2 667 dual channel, 8xUSB 2,0
• RAM: 2 GB, Kingston, DDR2 667
• Hard Disk: 40 GB, 6K040L0 Maxtor DiamondMax Plus 8, 2 MB Cache, IDE/133 and 160 GB 6Y160M0 Maxtor DiamondMax Plus 9, 8 MB Cache, SATA I
• DVD: Lite-On IDE DVD RW DH20A4H LightScribe
• Video Card: Gigabyte GV-NX71G512P8-RH, GPU NVIDIA GeForce 7100 GS, PCI-E, 128 MB On Board, 512 MB With TurboCache, With Adapted Fan.
• Audio: 6 channel Realtek ALC662 codec 
• Network Card: RTL 8101E chip (10/100 Mbit)
• Display: LG Studioworks 45i (1024*768@60hz) very ugly but still works
Everything Working!

---

### Post by Beowulf.1000 on 2009-04-12
Ubuntu 9.04 beta AMD64 live CD boots with 7.1 audio (on board the motherboard) and wireless internet (wifi card recognized) and wireless mouse and graphics and GUI on my new homebuilt system:

ASUS M4A79 Deluxe motherboard
AMD Phenom II quadcore cpu 3Ghz
  (motherboard and cpu were purchased as a combo at newegg.com)
4GB RAM (1066Mhz, 2 x 2GB 250pin DIMMs)
GeForce PCIe 7900 graphics card
3 Samsung 500GB SATA drives
Linksys RangePlus Wireless PCI Adapter wifi card, model WMP110
USB keyboard
Microsoft MX500 wireless mouse

---

### Post by Vostrocity on 2009-04-13
Ubuntu 8.10 Intrepid Ibex
Dell Vostro 1500 Laptop
1.4Ghz C2D, 2GB, 120GB, 128MB GeForce 8400m GS, Broadcom BCM4311 WiFi.
Everything so far works out of the box except the digital array mics.

---

### Post by balbecdaze on 2009-04-16
Jaunty

CPU: intel Core2Duo 4400
Mobo: Gigabyte ga-ep35-ds3l
RAM: 2 x OCZ Platinum 1Gb DDR2 800MHz
GPU: Inno3d Nvidia GeForce 8600GT
HDD: Seagate Barracuda 500Gb + Maxtor Maxblast 80Gb 

Microsoft Wireless Optical Desktop 2000
Trust 5.1 Surround Sound Speakers

Pretty much all worked perfectly - had to download Nvidia drivers and was a bit flummoxed by the Surround Sound options in ALSA mixer for a bit (just turn the volume up -doh!).  Seagate hard disk not read by Intrepid Ibex 8.10 (it is SATA, the Maxtor is IDE) but Jaunty read them both straight away.

---

### Post by alexpwalsh on 2009-04-18
Processor: Core i7-920
Ram: 9gb-DDR3
Graphics: ATI Radeon HD4870 1GB model - works fine with default drivers, ati drivers break

---

### Post by HousieMousie2 on 2009-04-20
Home-built: All Works
Mother board: MSI P7N Diamond LGA 775 NVIDIA nForce 780i SLI ATX Intel
CPU: Intel Core 2 Duo E8400 Wolfdale 3.0GHz LGA 775 65W Dual-Core Processor Model BX80570E8400
Video Card: NVIDIA XFX PVT96GYDSU GeForce 9600 GT XXX Alpha Dog Edition 512MB 256-bit GDDR3 PCI Express 2.0 x16
RAM: G.SKILL 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 1066 (PC2 8500) Dual Channel
HDD: Western Digital Caviar SE16 WD5000AAKS 500GB 7200 RPM SATA 3.0Gb/s 3.5"
Audio Card: ASUS Xonar D2X 7.1 Channels PCI Express

BIOS: Had to be updated before the CPU would work with that MoBo... not a Linux problem, just a hardware reality worth mentioning.

Video card: NVIDIA-Linux-x86-180.29 driver (from the NVIDIA web site) seems to work well, certainly better than the 170 series.  Driver must be reinstalled every time a new kernel image is released, but this is quick and easy.

Audio Card: Worked out of the box with ALSA version 1.0.16... with some resource-sharing issues, but nothing major.

---

### Post by evongugg on 2009-04-22
Jaunty 9.04

Phenom 9600
Corsair DDR2-800 4 GB
Asus 790GX motherboard: M4A78-E
EVGA 9800 GT
Onboard audio
Onboard NIC
2 SATA Hard disks
1 SATA DVD drive
USB mouse and keyboard

No sensors detected. Everything else works fine.

---

### Post by HunterNIN on 2009-04-22
Jaunty 9.04

Intel Pentium IV 2.66GHz
MSI ms-6769 mobo
Geforce Ti4400
bunch of generic parts, it's a cannibal system

As with previous releases everything works great. Although Jaunty is having issues with video when set to normal or extra.

---

### Post by dE_logics on 2009-04-23
Ubuntu 8.10

Graphs card

ATI

x1270 (IGP)(RS690)

No propitiatory drivers available (none work), open source drivers do not completely support 3-d, bad performance.

Following this article - 

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Will take you to the command line (i.e. ruin the graphs drivers completely).

Reconfiguring xorg.conf will bring back the GUI but after that the GUI works extremely slow and enhanced effects will not get enabled.

---

### Post by SpyroViper on 2009-04-24
Xubuntu 9.04

MSI Wind U100

Intel Atom 1.6Ghz
1GB RAM
Intel GMA Graphics
10" LCD Screen

Sound - ok
Wireless (Realtek) - ok
Stability/Functionality - ok
Trackpad/Keyboard/Screen Sizing - ok

The best distro I've used on a netbook.

---

### Post by elzo78 on 2009-04-24
Hi
i had a question have u had any problems with your motherboard? i just bought the same and its seems like its for an ATI system but im running an evga 9600gts.
have you installed the chipset drivers?
 
 
> **evongugg said:**
> Jaunty 9.04
 
Phenom 9600
Corsair DDR2-800 4 GB
Asus 790GX motherboard: M4A78-E
EVGA 9800 GT
Onboard audio
Onboard NIC
2 SATA Hard disks
1 SATA DVD drive
USB mouse and keyboard
 
No sensors detected. Everything else works fine.

---

### Post by klc5555 on 2009-04-25
1) Ubuntu 9.04 desktop.

2) Netgear WG511 (ver.1) wireless 802.11g PCMCIA adapter. 

    IBM Thinkpad T23, with onboard wireless 802.11b adapter.

Ubuntu does not detect the Netgear WG511 (version 1) at installation or bootup. Ubuntu does detect and configure the onboard 802.11b adapter.

Netgear WG511 (version 1) is activated from a terminal with: sudo modprobe prism54 This command (modprobe prism54) can later be added to /etc/rc.local to automatically start the card at boot.

Onboard IBM Thinkpad T23 wireless B adapter seems to interfere with Netgear WG511 card's ability to route. The onboard wireless adapter can be disabled by blacklisting the two modules orinoco_pci and hostap_pci in /etc/modprobe.d/blacklist.conf and then rebooting.

---

### Post by Sewje on 2009-04-25
I'm impressed, Jaunty works incredibly with my Acer 5920g.

Touchpad works completely!
Wireless works
Sound works
Media keys work and glow!
Damn even the SD Card Reader works!
Probably better to say what dosn't work, the IR Receiver ha!

Using livecd.

---

### Post by Joomla12 on 2009-04-25
Since I'm still new and just found this thread, here's my setup.

OS: Ubuntu 9.04
Hardware: nVidia 7150m/630m GeForce card. Running with nVidia 180 release
          Broadcom 4311 v2 wireless card. Running with BCMFWcutter 43xx.
          Conexant HD Audio speakers. Using default system drivers.
          nVidia GeForce Ethernet modem. Using default drivers.
Computer Model: HP Pavillion Notebook PC dv6607rs.

---

### Post by DrJohn999 on 2009-04-25
1)Version Of Ubuntu: 9.04 Jaunty i386 Desktop
2)Type Of Hardware: laptop
3)Hardware Maker: Samsung
4)Hardware Model: nc-10

Loaded all defaults, straight install, nothing special done.
Screen up in correct 16:9 1024x600 resolution
Wireless (ath5k_pci driver) and wired nets are up
touchpad is up
Bluetooth (HID -- wireless mouse anyway) is up
Keyboard blueFN keys are up (surprise!!)
Sound is up
Ran System Testing... nice feature!
IHMO -- huge improvement for this platform over 8.10. You guys nailed it!

---

### Post by allensaucier on 2009-04-26
Hi.  would you mind telling me how you got your combo to work?  I've got a evga nvidia 9600GT and the latest dev drivers just hang my system.  quad core intel, asus p5q-vm

Any suggestions would be appreciated.  Thx. 

> **evongugg said:**
> Jaunty 9.04

Phenom 9600
Corsair DDR2-800 4 GB
Asus 790GX motherboard: M4A78-E
EVGA 9800 GT
Onboard audio
Onboard NIC
2 SATA Hard disks
1 SATA DVD drive
USB mouse and keyboard

No sensors detected. Everything else works fine.

---

### Post by gyaneshwar on 2009-04-26
Ubuntu 8.10 and 9.04 
HP Officejet J4580 All in one works immediately.

Both do not work with Cannon 1500 printer.

Linksys bluetooth dongle usbbt100v2 does not work in both.

9.04
Ati Radeon x1650 does not work with proprietary drivers. 
and previous version has to be removed.
(sudo apt-get remove --purge xorg-driver-fglrx)
Detailed version is on this forum.

---

### Post by bodcod on 2009-04-26
Version Of Ubuntu: Ubuntu 9.04/8.04LTS

Type Of Hardware: External USB Desktop 3.5" HDD

Hardware Maker: Maxtor

Hardware Model: Maxtor Basics 1TB (Model Number STM310005EHD301-RK)


This is plug and play in Ubuntu 9.10 i386 Desktop, I plug it in to the usb port icon appears on desktop I double click on icon it takes a few seconds to do its thing then brings up nautilus windows with a 1Tb hard drive working and ready to go.

I have formated this with the gparted cd to fat32 for compatibility, it does come formatted to NTFS out of the box.

I can boot the pc with the drive plugged in with no problems either.IT does go onto standby mode to save power and i have had no problems with it coming out of that mode, it just spins back up no problems.


Have also tested with success in Linux mint 5 i386 Desktop which is based on Ubuntu 8.10 LTS, works just as it does in ubutu 9.04 Except it 8.10 does seem to not want to eject the volume manually it jsut says Error ejecting volume waits a few secons and mounts it again. ON this note i have installed pysdm storage device manager from synaptic and this allows me to unmount.

---

### Post by evongugg on 2009-04-27
> **elzo78 said:**
> Hi
i had a question have u had any problems with your motherboard? i just bought the same and its seems like its for an ATI system but im running an evga 9600gts.
have you installed the chipset drivers?
Worked out of the box with the proprietary Nvidia display drivers in Ubuntu 9.04.

---

### Post by evongugg on 2009-04-27
> **allensaucier said:**
> Hi.  would you mind telling me how you got your combo to work?  I've got a evga nvidia 9600GT and the latest dev drivers just hang my system.  quad core intel, asus p5q-vm

Any suggestions would be appreciated.  Thx.
I did not have any problems. Everything worked out of the box. Used Nvidia proprietary display drivers.
Try your integrated graphics instead of the video card.

---

### Post by retiredtechie on 2009-04-27
OS:    Ubuntu 9.04

Custom System:

    Motherboard: ASUS P5B-E
    CPU: Intel Core 2 duo 6600 2.4 GHz
    RAM: 2 Gb
    Video: nVidia GeForce 9800 GTX (3D driver version 180)
    Sound: on-board AD1988
    NIC: on-board Attansic Gigabit

Peripherals:

    Display: Viewsonic VX2235wm
    Scanner: Epson Perfection 1250
    Wacom 3.5 x 5 tablet
    Keyboard: USB
    Mouse: USB
    Hauppauge WinTV-PVR-USB2 analog video capture

    Printer: Canon Pixma iP5000 (attached to Vista PC on home Lan)

Notes:

    Monitor not recognized when connected via digital (DVI) input. 
    Maximum display resolution was 640x480. 
    Display was recognized when connected via monitor VGA input.
    Compiz now works like a top.
    Video capture worked using TV-Viewer after all dependencies were installed.

So far, all is great!

---

### Post by frodon on 2009-04-28
Hello,

There have been an increase of off topic post in this thread lately so i thought that should post a reminder.
This thread is for listing compatible hardware only, **_questions and idle chat are not welcome in this thread_** (the support area are made for this purpose).

Thank you very much for following these guidelines.

---

### Post by del_diablo on 2009-04-28
Fujitsu Siemens Amilo Pa 3553
Ubuntu 9.04 i386

What does NOT work:
*The buildt-inn Ralink card(2860 i belive), nor have i managed to get it to work
*It sounds like a jet engine(its however a bit more quiet than under 8.x), the hotkey for "downclocking" is not working either

What works:
*Hotkeys except downclock and wlan and LCD light controlls
*All ports work, yet to test the SDcard reader thoo
*Grapics(also got the correct resolution outofthebox)
*everything else

Edit: Installing the restricted ATI drivers WILL kill the system, or put another way: The screen remains black after GRUB.

---

### Post by ptn107 on 2009-04-28
1)9.04 64-bit
2)Video Card
3)nVidia
4)GeForce 7800 GS (rev a2)

---

### Post by skygazer on 2009-04-30
I have a vista home basic enabled laptop which was corrupted by the virtumonde virus and i couldnt get it to bootup. So i decided to install linux. I took a iso file of ubuntu 8.04 LTS to my friends XP machine and created a bootable Live USB using unetbootin. Install went perfectly, no hickups.This is my first linux install on a real computer and so far, i am amazed at how simple it is. Being from a windows background made me think i would have to deal with cryptic command lines and still not get anything working. But letme tell you, it all freaking works right out of the box. Here's my configuration

Compaq Presario V3702AU Laptop 

AMD Turion 64 X2, 1.9GHz
1 x 1GB, DDR2-667 Samsung
160 GB, 4200 rpm HDD Western Digital
Nvidia Geforce 7150M GS graphics card (287 MB shared RAM)
Nvidia MCP67M Chipset (Nforce 630M)
Integrated WLAN 802.11b/g Broadcom
Connexant HD Audio
SD Card Reader
Built In webcam 1.3 Mpixel

Installation took 15 minutes + 1.5 hrs to download/install updates. Then it prompted me to download and install propriotory drivers for wlan and gfx which i did and they work smooth. Then i installed compiz+emerald for 3d desktop.

I got the following hardware up and running out of box.
Audio, SD card reader, Webcam, Bluetooth, Volume up/down/mute buttons, Media player buttons play/pause/next/prev etc, Brightness up/down, hibernate button, inbuilt and external microphones, all led indicator lights. 

Yet to check out the following:
External monitor, PCI-express slot, firewire, s- video port, quick launch button, HDSOFT Data/Audio modem

I hope this helps other Compaq V3702X users out there who want to migrate to Linux. 

Regards,
Skygazer

---

### Post by non-prophet on 2009-04-30
Oops

---

### Post by non-prophet on 2009-04-30
**Ubuntu 9.04 on Compaq Presario C700 (C774TU)**

Celeron 550 2 GHz
RAM 1 GB 
HDD 80 GB
Mobile Intel 965 Express Chipset
DVD GSA-T40N
ALPS PS/2 GlidePoint Touchpad  
WLAN Artheros AR5007 b/g  (AR242x) 

Installed without a problem.  (I have had problems with other Distros with this Notebook.)

WLAN works well. Only had to activate proprietary driver (sorry !!) for WLAN using System -> Administration -> Hardware Drivers and enabling the use of the driver. Small problem - WLAN on/off switch does NOT work and WLAN light is RED whether WLAN is ON or OFF. 

I hate touchpads whic default to 'tap for mouse click'. You can turn it off from System -> Preferences -> Mouse -> Touchpad and disabling 'mouse clicks with touchpad'. 

I tried running from battery and the _Battery Indicator_ (when made 'always on') _showed 100% for well over 1 hour operation_. Forum search has not found a solution yet. 

Cheers,
non-prophet

---

### Post by Herber on 2009-05-01
Dell 8200
1GB Ram
2+MHz processor

Installed after truning on Safe Video installation

---

### Post by Herber on 2009-05-01
Dell Inspiron 7000 Laptop
300MHz Processor
ATI graphics
300+MB Ram 
No problems With Ubuntu 6.1-8.1


CANNOT INSTALL JAUNTY 9.04  SYSTEM HANGS DURING OS LOAD

---

### Post by YMS_1975 on 2009-05-01
Version Of Ubuntu: Ubuntu 9.04
Type Of Hardware: Networking Wireless Card
Hardware Maker: Linksys by Cisco
Hardware Model: WMP300N

Installed this card on Ubuntu 8.10 but couldn't get the OS to recognize the card. My understanding is that there is a workaround to this problem, but I just couldn't get it to work (even after trying the workaround).

I then upgraded to Ubuntu 9.04 and the card was instantly recognized. It works great & no tweaking was necessary.:)

I also wrote a quick review of this hardware at [http://www.ubuntuhcl.org/browse/product+linksys-wmp300n?id=6857](http://www.ubuntuhcl.org/browse/product+linksys-wmp300n?id=6857)

---

### Post by jayhel on 2009-05-01
1)Version Of Ubuntu: 9.04 Netbook Remix
2)Type Of Hardware: Netbook
3)Hardware Maker: Hercules
4)Hardware Model: Hercules eCAFE EC-900/H60G-IA (Linux)

I removed the preinstalled version of Linux that came with the netbook.
I installed Ubuntu 9.04 Netbook Remix on the 60 Gig hard disk from a USB Key...

Waw!

What a difference!!!

Everything is working!

- Wifi: 100%
- Sound: 100%
- Webcam: 100%
- Touchpad: 100%

Proprietary drivers: 0%

This little package is so nice! I can't go anywhere without it!

---

### Post by akakingess on 2009-05-02
Just FYI, I am new to this, but wanted to post what I have found thus far with my Gateway M-1628 Notebook (AMD64 Turion x2) W/ 3 GB RAM...Intrepid had trouble with wireless network card/chipset, installed Jaunty clean and have not had 1 problem, here is the lshw from my laptop:

description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
      *-memory
          description: System memory
          physical id: 0
          size: 2942MiB
     *-cpu
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-60
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
         
Sorry if it's too much info, like I said I am a noobie at this and just wanted to let everyone know how it's going with this model GW M-1628.

Earl

BTW - Running Jaunty 64-bit and runs like a champ

---

### Post by robertron76 on 2009-05-07
[LIST]
[*]Laptop
[*]Processor : T6400 2.00GHz,Intel Core 2 Duo CPU
[*]4GB RAM
[*]Sony VGN-FW390
[*]HDD : TOSHIBA MK2552GSX
[*]Dual Boot with Vista Ultimate 64-bit
[*]ATI Mobility Radeon HD3650
[*]250 GB HDD
[/LIST]

Ciao

---

### Post by cmsComptia on 2009-05-08
Laptop:     Dell Inspiron 1300/B130
OS:          Dual Boot - WindowsXP Pro   /    Ubuntu 9.04 Jaunty

-----------------------------------------------------------------------------------------------
Problem Device:     Dell 1370 WLAN MiniPCI Card 4.2
Router:                  2WIRE
DSL Provider:         AT&T Yahoo DSL
INF File:                 bcmwl5.inf
SYS File:                 bcmwl5.sys
Packages Installed: ndisgtk_0.8.4-1_0ubuntu2_1386.deb
                              ndiswrapper-common_1.53-2ubuntu1_all.deb
                              ndiswrapper-utils-1.9_1.53-2ubuntu1_i386.deb
-----------------------------------------------------------------------------------------------

AREA's of Troubleshooting Performed.

1.     Device Recognition:     network:0
                                          Broadcast=yes, driver=b44, driverversion=2.0
                                          Description: Ethernet Interface
                                          **This network does show the product and vendor along
                                              with the clock speed **

                                          network:1
                                          Product BCM4318 [AirForce One **g] 
                                          Description: Network controller, driver=b43-pci-bridge,
                                          Vendor Broadcom Corporation, version: 02

                                          network:0 DISABLED
                                          Description: Network Interface
                                          Physical ID: 1
                                          logical name: wlan0
                                          Broadcast=yes, has a serial number

                                          network:1 DISABLED
                                          Description: Ethernet interface
                                          physical ID: 2
                                          logical name: pan0
                                          Broadcast=yes, driver=bridge driverversion-2.3

2.    Using Windows Wireless Drivers: As I have mentioned above the packages I installed  to pursue this method. I copied the .inf and the .sys files in my home directory. I then clicked on <<Install New Driver>> under the Wireless Network Drivers window.The program asked me to select inf file, so I selected the browse and double clicked on the .inf file mentioned above then selected <<Install>>. A window appears stating "Unable to see if hardware is present" I clicked <<OK>>. Then to the left area of this window it shows in bold letters "bcmwl5" and under it are the words "Hardware present: Yes". I then highlighted this and clicked on <<Configure Network>>. Another window pops up stating "Could not find a network configuration tool."

3.    Using Network Tools:
                    Network Device: Loopback Interface
                    2 Protocols are assigned: IPv6 a #in IP Address & # in NetMask,Scope=Host
                                                           IPv4, a # in IP Address & # in NetMask
                                                           State: ACTIVE

                  Network Device: Ethernet Interface (eth0)
                  IPv6 & IPv4 both have 0's in NetMask and IPv4 has 0's in IP addr. IPv6 (blank)
                  This does have a hardware address and the State is ACTIVE

                  Devices: Unknown Interface(wmaster0), Wireless Interface (wlan0) and
                                Unknown Interface (pan) are all INACTIVE, but they do have a
                                Hardware Device numbers, but everything else is nothing but zero's

4.    Checked for Connection to the Router:
             
                   I typed the command "iwconfig" within the Terminal

                   lo = no wireless extensions
                   etho = no wireless extensions
                   wmaster0 = no wireless extensions
                   wlan0 = There is nothing assigned to the ESSID, Access Point: Not Associated
                                 Power Management: off
                   pan0 = no wireless extensions

I do have access to the routing address, dhcp range, access point's, IP Address, Sub Masks, Def. Gateway. I'm fairly new to this OS. I just thought It would help me to learn this OS. I'm new to Linux and I've always been a Microsoft fan but since I learned on my own that they Microduds have a Background Intelligent Transfer Service, I would like to learn this OS instead. Although I turned that (BITS) off, I would rather try to use a different OS for my needs.

I would like to get my laptop on the Internet ASAP. And if you or anyone you know may be of help please respond. I will give you more information, but I hope the infogiven already will be enough. I would rather fix it and move on than chatting back and forth.

Thanks in advance to everyone who takes their time in reading this long post and to those who reply.

cmsComptia

---

### Post by wjstarck on 2009-05-08
[LIST]
[*]Laptop
[*]Sony VAIO SR290
[*]Intel(R) Core(TM)2 Duo CPU T9600 @ 2.80GHz 64 Bit
[*]Mobility Radeon HD 3400 Series
[*]Intel Wireless WiFi Link 5100
[*]4 GB RAM
[*]SCSI HD 280 MB
[*]Jaunty 9.04 64 Bit; fresh format and install
[/LIST]

Installation was straightforward. Bluetooth works, wireless works. Compiz works, display is bright. Display brightness keys do not work, but sound keys do. Not sure if the lid latch puts the laptop to sleep properly, as I had it fully charged overnight and unplugged it before going to work, but when I came home today the battery was drained. I'll check on that and try to report back ASAP. Anything else you want checked please let me know :P

---

### Post by fela on 2009-05-10
Ubuntu 9.04 64 bit
Graphics Card
Palit
Nvidia Geforce 9800 GT 512MB

It works fine with the proprietary Nvidia drivers. With the open source nv driver, the fan is stuck on 100%.

Also, when booting up (before GDM is loaded), the fan is always on 100%. I suppose this is a VESA bug?.

---

### Post by fela on 2009-05-10
Ubuntu 8.10 32 bit
Laptop
IBM
Thinkpad T42

So far I haven't found anything that doesn't work.
WiFi, ethernet, USB, Graphics (compiz works), Suspend, Hibernate, Brightness hotkeys, etc. all 'just work'. :D

---

### Post by SoftPops on 2009-05-11
Ubuntu 8.10 and 9.04
Laptop
Fujitsu-Siemens
Lifebook e4010
 
Other than an oversensitive synaptics touchpad, works perfectly after install/upgrade.

---

### Post by Ceiling Fan Man on 2009-05-11
My latest system:

**Motherboard:** Asus M3N-HT Deluxe HDMI
**Processor:** AMD Phenom II 940 3.0GHz Black Edition (Deneb)
**Video Card:** XFX nVidia GeForce 260 896MB Black Edition
**RAM:** OCZ Reaper 4GB 1066 2.2V
**Power Supply:** Thermaltake Toughpower 850W, Modular
**HD0:** Seagate Barracuda 7200.11 500GB
  */* This drive is partitioned four times, with WinXP SP3 (32-bit) as the primary, then Ubuntu Jaunty (64-bit), a third one with Windows Vista Ultimate (64-bit), and the 4th is a swap space. */*
**HD1:** Western Digital Caviar Black 1TB
  *//Storage*

  This hardware configuration gave me a lot of difficulty with 8.10 Intrepid. All kinds of Buffer I/O errors when I was trying to install, and after I finally got it installed, the system speaker would beep constantly at me, and my monitor would go to sleep during boot and shutdown, which was especially annoying when FSCK decided to run, because I couldn't see it to tell what was going on.

  9.04 Jaunty seems to have fixed all these glitches. I did a fresh install over my Intrepid installation, had video the whole time and and zero Buffer I/O errors. I continue to have video during every boot and shutdown now as well. I can't say for sure if Jaunty fixed the system speaker beep, because I haven't plugged it back in yet, but I believe that it has. Previously, as it was booting, the system beep would quickly, only for a second, sound over my external speakers when the system speaker was unhooked. This has not happened yet in Jaunty.

  VERY happy with Jaunty, as it seems to have fixed all of my hardware incompatibility problems. :)

---

### Post by underdarkonsole on 2009-05-11
thank's guy's i find driver for via chrome9 that can enabled compiz. And finaly my laptop can run compiz ....

[http://underdarkonsole.blogspot.com/2009/04/axio-via-chrome9-cn896-compiz-is-done.html](http://underdarkonsole.blogspot.com/2009/04/axio-via-chrome9-cn896-compiz-is-done.html)

---

### Post by cabez0n on 2009-05-12
Ubuntu 9.04
Laptop
Acer
Aspire 5520

Internal Mic is not working as well as POWER OFF can't turn the laptop off, and it needs a couple of key-presses to turn completly off.

---

### Post by mouchkine on 2009-05-12
[B]Laptop Acer Aspire 5570-4315 with Ubuntu 9.0.4 Final
[/B]Intel Core Duo T2450 (2ghz), 1 gig PC-5300 Samsung, 160 gigs Samsung.

Intel GMA 950 (945) Working Out of  the Box
Sound HDA OOB[COLOR=SandyBrown] (with some glitches though...)[/COLOR]
Wireless Intel 3945 OOB (from Live CD)
SD Card Reader TI OOB
Webcam Acer Orbicam [COLOR=SandyBrown](with some fix... see [http://ubuntuforums.org/showthread.php?t=1136990](http://ubuntuforums.org/showthread.php?t=1136990))[/COLOR]

Bluetooth USB Dongle (ISSC EDR BTA) Piece of C... on Windows... OOB in Ubuntu!!! :P
Nokia E65, 6600 and Motorola V635 phones synched (thanks Ubuntu!)
Ipod Video 0 gigs detected by MPlayer...

Mouchkine-laptop -> Triple Boot... Ubuntu (main)...Swap... Windows 7... Mac OS X 10.5.6 (Hackintosh)... works great!

---

### Post by nerak on 2009-05-13
Laptop - **Dell Vostro 1400**

Processor : Intel(R) Core(TM)2 Duo CPU T5270 @ 1.40GHz
HDD: ATA FUJITSU MHY2120B, 120GB
Memory : 2060MB 
Operating Systems: Dual booting Windows XP & Ubuntu 9.04
Video card: GeForce 8400M GS/PCI/SSE2
Audio Adapter: HDA-Intel, 82801H, Dell device 0227 (Minor glitches)

The only issue seems to be the audio.  It plays the audio, but songs sound a bit...screechy.  Like there's something REALLY high pitched and it just makes my brain melt.

---

### Post by gan1708 on 2009-05-14
Type : Laptop
**Model : Lenovo-IBM ThinkPad SL400 (14'')**

***OS: Ubuntu 9.04 32bit (ext4 install***)

CPU : Intel Core2Duo T5870 2.0GHz
RAM : 3GB DDR-2
Graphics : Intel 4500
Wireless : Intel 5100 (Centrino)


CPU scaling works fine

Wireless works fine. No issues so far. Speeds are decent and signal strength is good.

Graphics work fine. Default screen resolution was set to 800x600 on first boot, but changing it to 1280x800 once in the Display Manager sorted it out. There seems to be slight tearing when playing videos on MPlayer and VLC, but I know this is a well documented issue with the Intel drivers and am confident updated drivers will fix the problem in the near future. Compiz seems to run fine. Played the Linux version of Bioware's Neverwinter Nights and it ran quite smoothly.

Sound works well. Volume levels are very good with headphones on (pretty good bass reproduction if plugged to good headphones).

USB ports work and transfer speeds are excellent. Tested with pendrives and Hitachi, Lacie and Transcend external drives.

DVD-RW works fine. Only problem I had was audio CD's I burned failed to play in my car CD player, but switching to GnomeBaker instead of the included Brasero solved that issue.

Webcam works with Cheese (not tested with Skype yet)
 
Card reader works with SD and SDHC cards (tested up to 4GB Sandisk Extreme III)

Trackpoint works and sensitivity is decent. Trackpoint center scroll button works as well. Touchpad works well with good sensitivity.

I get between 170 - 210 minutes of battery life with WiFi turned on, depending on what apps I run and whether I have a USB mouse and headphones attached. Pretty decent, considering the manufacturer rated battery life under Windows is said to be 3 hours. It came with a 6-cell battery as standard.

Wired LAN connection works. Not sure if the 56k modem works or not (I don't need it). Not tested Firewire, HDMI and ExpressCard slots yet.

System boots in around 25 seconds (maybe less) with concurrency enabled.

Suspend works well with very fast wake up time. Hibernate works but it takes rather long to wake up. I don't bother with hibernate anymore since it boots up so fast anyway.

System stays cool throughout heavy use. Fans hardly come on (or their very quiet when on, I dunno)


Minor niggles:
Volume buttons don't work (my main gripe).
Some FN key combinations don't work.
FN screen brightness control only seems to be able to change between 2 levels.
There's this very loud beep that occurs when I Shut Down or Restart. I've already turned off system sounds, but it's still there. (PC Beep type sound)


I'm pretty happy with the way this ThinkPad performs with Jaunty 9.04. Hope the small issues I stated above get resolved with future updates.

Cheers~

---

### Post by mustangzach on 2009-05-18
Okay, I'm very happy with Ubuntu. I will say, this is a viable alternative to Windows, even for people who don't know computers. This is the house we built, and we built it bigger. It is superior to Windows XP and Vista, and it looks better than Windows 7 could dream of looking. It's also bulletproof, I have blue screened my XP installation accidentally multiple times, I can't crash this when trying.



My system is as followed:

Acer Aspire One ZG5
Ubuntu 9.04 (no Netbook Remix just the default install)
Intel Atom 1.6GHz, 32-bit, I can't remember the model number atm
1GB 667MHz DRR2 RAM
Atheros AR5BXB63 Wireless
I can't remember my NIC, but it works
Sound works great, albeit it's a bit quite it seems, but I think it's just me
Webcam works on default install
Integrated graphics work fine.

There's no reason to use restricted drivers, NDISwrapper, anything really.. Ubuntu just works, I mean, the boot time is even faster than Windows. Thanks for proving the whole "*Nix takes longer to boot than Windows/DOS-like systems" myth wrong. With Windows XP on an NTFS drive, my boot time would be about 2 minutes. With this, I can be rocking out to my NOFX albums in about 30 seconds. Great job! The only thing I don't like is the little light on the wireless thing don't come on, and the on/off switch doesn't notify me. I'm not really compaining though..


The only issue I had was when I installed from Windows, the wireless drivers didn't work. At first, it would detect the hardware, but wouldn't connect, and after I chose to use the restricted drivers, it didn't work at all. I even tryed NDISWrapper to no avail, the drivers "worked" but the hardware wasn't detected. It does work however, on my old Thinkpad with the Linksys WPC54G v3.1 PCMCIA card though, and that's great. I ran Xubuntu on the Thinkpad, I will mention. Even the el weirdo flash drive I bought works.


So yes.. I'm very happy with Ubuntu 9.04, in my opinion, the years of the Linux desktop start here.  I am encouraging Windows users to upgrade to this, mainly by helping them install it face to face. Wish me luck, I will publish my results here once I'm done doing this.

-Zach

---

### Post by neo_1in on 2009-05-18
I have been using ubuntu since 5.04. Mine is a pretty old PC, which i have upgraded a little. 

Ubuntu 9.04
Compaq Presario S5030IL Desktop PC

Everything works out of the box great on the original hardware, i.e.
P4 2.5 GHz
15 inch Compaq 5500 (Coloreal) CRT Monitor
128 MB RAM (266 MHz)
CD-ROM
40 GB Seagate HDD
OnBoard SiS 650 Graphics Card (NO 3D though)
OnBoard Ethernet & Modem
and everything else.

Upgrades:
80 GB Seagate Barracuda HDD
512 (333 MHz) + 1024 MB (400 MHz) Kingston RAM
Moser Baer DVD (DVD-R DL) Writer
USB Modem.
All just work.

XFX nVidia GeForce 6200 256 MB Graphics Card (3D works with restricted drivers)

---

### Post by qfhcorrea on 2009-05-18
Ubuntu 9.04 Jaunty Jackalope
Laptop Acer Aspire 5315-2780
Intel Celeron processor 560 to 2,13GHz, 533MHz FSB, 1MB L2 cache
Intel Graphic MEDIA Accelerator X3100 up to 250MB
1 GB DDR2
15.4" WXGA Acer cristalbrite LCD
80GB (ext4 ¡¡¡¡)
DVD super multi DL
802.11 b/g WLAN

Greetings¡¡¡¡ of Chile

---

### Post by gradinaruvasile on 2009-05-20
Here it goes...

Type: Desktop
MB: ASUS M2V TVM
CPU: AMD Athlon 3200+ AM2
Memory: 2 GB DDR2 (667 Mhz dual channel)
Video: Galaxy Geforce 7600GS/128MB DDR3
HDD: 250 GB SATA2 (Hitachi something)
Ubuntu 7.10, 8.04, 8.10, 9.04
Everything (compiz, sound, 3d Acceleration, games) worked with all of the above Ubuntu versions out of the box. Of course with the Nvidia proprietary drivers.

Type: Desktop
MB: ASUS A7N8X
CPU: AMD Athlon 2500+
Memory: 1 GB DDRAM (400Mhz dual channel)
Video: Nvidia Geforce MX 440/64MB
HDD:40GB (dunno what type it is exactly)
Ubuntu 8.04, 8.10
Everything (compiz, sound, 3d Acceleration, games) worked with all of the above Ubuntu versions out of the box. Nvidia proprietary legacy drivers.

Type: Desktop
Dell Optiplex 755 / Intel Core2Duo E6550/ 2GB RAM (800 Mhz)/ 250 GB HDD Nvidia Quadro NVS 285 / 128 MB DDR2 / dual monitors
Ubuntu 8.04, 8.10, 9.04
Everything (compiz, sound, 3d Acceleration, games) worked with all of the above Ubuntu versions out of the box. Of course with the Nvidia proprietary drivers. I think this is the most stable system of the ones i used.

Type: Desktop
Dell Inspiron 530 /  Intel Core2Duo E4500 / 1GB RAM (800 Mhz) / 2x 500 GB HDD (SAMSUNG HD501LJ) / ATI RV530 [Radeon X1600] / 256 DDR3 (opensource radeon drivers)
Ubuntu 9.04
Sound, desktop effects working perfectly

Issues are all linked with the radeon opensource drivers
Problem with video overlay (OpenGL) applications like google Earth or (runs smoothly without Compiz) 
Some games (foobillard, yo frankie and in some cases nexuiz) lock the system - in these cases i was able to log in via ssh and reboot the system (killing the Xorg, gdm or the game processes didnt work, only the reboot command)
Some games (Enemy territory, Regnum Online) wont even start.
Others run very fast and stable (Urban terror, Openarena, billard-gl).

Type: Desktop
Dell Inspiron 530 /  Intel Core2Duo E4500 / 3 GB RAM (800 Mhz) / 200 GB HDD / ATI AIW RV515 (?not sure) [Radeon X1300] / 256 DDR3 (opensource radeon drivers) / Dual Head 1680 x 1050 
Ubuntu 8.10, 9.04
Sound, desktop effects working perfectly (the latter a bit smoother maybe then the fglrx on Ubuntu8.10, although the glxgears score went down 30 %)
All in all it seems 9.04 it is a bit more stable then the 8.10 - this computer had some crashes in 8.10 and 8.04 it seems related to the fglrx drivers...

Type: Laptop
Dell Latitude C640
Memory: 768 MB Ram
CPU: Intel Pentium M 1800 Mhz (i think)
HDD: 40 GB
Video: Ati Radeon Mobility 7500 / 32 Mb dedicated VRAM
Wireless: Orinoco something 802.11 b (no WPA yet in these versions)
Ubuntu 8.04, 8.10
Sound, Desktop effects working perfectly (surprisingly well for this ancient piece of hardware)
Problems - from 8.10 the FN Keys wont work after starting X (worked in 8.04)

Type: Laptop
Dell Latitude C630 / 2 GB RAM / Intel Core2Duo E7300 / 2GHz / 160 GB HDD / Nvidia NVS 135 / 256 MB / 802.11 bg wireless
All good, except i couldnt get the hacker light (or whatever it is called to light up...)

---

### Post by ajgreeny on 2009-05-21
Ubuntu 9.04
Laptop: Compaq CQ70-211EM
Intel Pentium Dual-core Mobile t3400
2gb Ram
Intel Mobile GMA 4500 MHD graphics
Built in webcam (Conexant?)
Built in card reader
Atheros wifi

Appears to work without problems though I have not yet tried suspend or hibernate.  Compiz works brilliantly, much better than I expected and I have had no difficulties which I thought might happen with the 9.04 Intel graphics incompatibility problem noted at first with 9.04.
Wifi works straight out of the box, no configuration, other than chosing the network from a list of about 5 found.
Webcam works out of the box, even with skype, as does the internal microphone.

Overall a superb buy for ubuntu, especially at the price Curry's (I would not usually use them, but the price!) has it in the UK at the moment, £349.

---

### Post by Freyra on 2009-05-22
Hello,

I want to install Ubuntu on my Laptop Toshiba Satellite P200

Intel (R) Core (TM) 2 Duo CPU T7250 @ 2.00 GHz 32 Bit

Has anybody tried to install Ubuntu on the same? 

When Yes, is there any problem with installation? 

Thank you in advance

---

### Post by paulororke on 2009-05-22
MB: ASUS M3N78 PRO GeForce 8300
RAM: 8GB (4x2GB) Corsair XMS2 PC8500 DDR2 1066MHz
CPU: AMD Phenom X4 9500 Socket AM2
HDD: 2 x 1TB Hitachi SATA 7200/16MB/SATA-3G
OS: Ubuntu Server x64 9.04

Vanilla install with RAID1, 9.04 (Jackalope) found the RAID set easily, LVM set up with ext4 LVs without a hitch.

ASUS provides no support for the RAID drivers and until this release I could not use Ubuntu on this hardware - Great job!

btw - thing thing is FAST for an $800 'server'!

---

### Post by coughlin on 2009-05-24
Ubuntu 9.04 64 bit
Lenovo U330 IdeaPad notebook
Ricoh multi-card reader

9.04-64 bit ... doesn't recognize the Ricoh multi-memory-card reader ... at least using an Olympus 16 Meg **xD** memory card.

---

### Post by FrankT-Qc on 2009-06-05
Hi. 

Using the drivers at :
[http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)

I have tried installed the HL-5370DW on EVERY combination of these Version/Interfaces

Ubuntu :
Hardy x86
Intrepid x86
Jaunty x86 server
Jaunty amd64

Interface :
USB
Ethernet
WiFi

And it works perfectly except that duplex printing logic is inversed (i.e. if you ask for long side, you get short side, if you ask for short side, you get long side...)

Even if it's quite easy to just inverse you choises, beware that if you're going to pool the printer with others that get the choice right, it might become a problem.

---

### Post by Kelvari on 2009-06-06
1)Version Of Ubuntu: Ubuntu 9.04 Jaunty 32-bit
2)Type Of Hardware: Video card
3)Hardware Maker: nVidia
4)Hardware Model: GeForce 7600 GT KO

---

### Post by spiceminesofkessel on 2009-06-08
Ubuntu 9.04 Jaunty Jackalope

**Main Board:**
GIGABYTE GA-M61PME-S2P AM2+/AM2 NVIDIA GeForce 6100 Micro ATX AMD Motherboard
(NOTE: The only trouble with this main board is sound input for the built-in sound card. It does not work out of the box. Sound output works, but not input. You can get it to work with a little patience and by adjusting the options in the Sound Preferences and the Preferences in the Volume Control.)

**Processor:**
AMD Athlon 64 X2 5000 Brisbane 2.6GHz Socket AM2 65W Dual-Core Processor Model ADO5000DOBOX

**Memory:**
OCZ 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 1066 (PC2 8500) Dual Channel Kit Desktop Memory Model OCZ2G10664GK

**Hard Drive:**
Western Digital Caviar GP WD5000AACS 500GB 5400 to 7200 RPM SATA 3.0Gb/s 3.5" Internal Hard Drive

**Video Card:**
XFX PVT96OS1S4 GeForce 9600 GSO Fatality Edition 768MB 192-bit GDDR2 PCI Express 2.0 x16 HDCP Ready SLI Supported Video Card

---

### Post by blackSP on 2009-06-09
Ubuntu 32-bit: 9.04, 8.10, 8.04
Asus F8P laptop
2gb ram, 250gb hdd, Radeon HD2400 with Catalyst 9.5 drivers, wifi, Bluetooth dongle
Runs everything out of the box. Compiz is OK and doesn't crash anything with the 9.5 drivers.

---

### Post by calebhoward on 2009-06-10
Version of Ubuntu: 
Linux Laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

Type of hardware:
product: G71G
product: Intel(R) Core(TM)2 Quad  CPU   Q9000  @ 2.00GHz
product: 4 Series Chipset DRAM Controller
product: 4 Series Chipset PCI Express Root Port
product: nVidia Corporation 9800M
product: 82801JI (ICH10 Family) USB UHCI Controller #4
product: AR928X Wireless Network Adapter (PCI-Express)
product: 82801JI (ICH10 Family) PCI Express Port 3
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
product: 82801JI (ICH10 Family) USB2 EHCI Controller #1
product: 82801 PCI Bridge
product: R5C832 IEEE 1394 Controller
product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
product: R5C592 Memory Stick Bus Host Adapter
product: xD-Picture Card Controller
product: 82801JIB (ICH10) LPC Interface Controller
product: 82801JI (ICH10 Family) SATA AHCI Controller
product: ST9320421AS
product: BD ROM BC-5500S
product: ST9320421AS
product: 82801JI (ICH10 Family) SMBus Controller

Hardware Maker:  Asus

Hardware Model: G71G

Notes:

- NetworkManager failed totally with this system.  WICD worked fine.
- Camera works.  
- Audio works.  
- Direct Console LED display has no driver SW
- Specialty Buttons unsupported
- Touch Pad cannot be disabled.

in all, it's pretty functional

---

### Post by kndfs3001 on 2009-06-17
Ubuntu 8.10,9.04

MacBook 4,1(Early 2008 )

Graphics: Intel GMA X3100
Wifi, Bluetooth, Compiz all work (Wifi requires install of proprietary driver)

Keyboard Functions all work

iSight Camera works after following these instructions: [https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight](https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight)

Trackpad works out-of-the box, but you can get it to behave like Mac OSX if you follow these instructions:
[https://help.ubuntu.com/community/MacBook4-1/Jaunty#Touchpad%20(appletouch]("https://help.ubuntu.com/community/MacBook4-1/Jaunty#Touchpad%20%28appletouch"))

---

### Post by The Real Dave on 2009-06-17
Ubuntu 9.04 Jaunty Jackalope x84

Acer Aspire T650

Intel LGA775 Pentium 4 3Ghz
Ati Radeon Xpress 200 Chipset
Hitachi Deskstar 7k2 SATAII
Samsung Spinpoint 7k2 SATAII
Raeltek HD Audio 
Generic (I presume) 7in1 Card reader
Standard v.92 internal modem
DVD-/+RW Multidrive
DVD-ROM drive

Cheap Bluetooth dongle
Netopia Network Router
Trust 120 Spacecam
iPod Nano 4th Gen
Various digital cameras
Generic Microphone
Sony Walkman
Sony Ericsson K800i phone

All works perfectly out of the box with 9.04. Sorry if mentioning generic hardware is pointless. Working with the router to see windows workgroups properly only required installing Samba as per usual. 

However, burning, or writing to discs on either drives puts alot of strain on the CPU. It didn't in Hardy. So far thats my only issue with Jaunty. Not sure what causes that, or how it can be fixed. Could simply be that my CPU isnt powerful enough, now that Ubuntu has progressed 2 releases

---

### Post by zuknivek on 2009-06-19
I bought an Asus eeepc 901 from newegg in about February. Originally it came with windows xp but installed ubuntu no problem. Everything worked out of the box except for some reason after the installation my bluetooth was turned off in the bios. Was an easy fix and I would recommend this netbook to anyone.

---

### Post by Anandavala on 2009-06-20
Ubuntu 9.04 Jaunty
Kernel 2.6.28-11-generic x86_64

**Sun Ultra 27 Workstation**
Intel Xeon W3520 8-core 2.66GHz
8MB shared Level 3 cache
256K Level 2 cache per core
3x2GB DDR3 ECC unbuffered DRAM 1333MHz
500GB SATA Disk Drive
NVIDIA Quadro FX 380 graphics accelerator
Gigabit Ethernet 10/100/1000BASE-T NIC
16x DVD Writer/48x CD-ROM Writer
Sun type 7 keyboard
SunL7ZF 17" LCD screen

Notes:
Virtually everything worked "out of the box".
The keyboard was not detected properly so some superfluous keys such as "find", "again" etc don't work.
The NVIDIA graphics drivers had to be loaded via *System > Administration > Hardware Drivers*.
Other than that everything was properly detected.
It was a clean install and the machine runs beautifully :D

---

### Post by nlegere on 2009-06-20
Laptop hardware incompatibility:

I can't seem to get the proper screen resolution.  Some menus are hard to use/see because they are bigger than the screen.  

My laptop is an HP pavilion dv 2000, not sure if it's the graphics card:

NVIDIA GeForce Go 7150M

or the display:

14.1" WXGA High-Definition BrightView Widescreen Display (1280 x 800)

that is causing the problem.  

When I open the 'display preferences' menu, it says the monitor is not recognized. 
I've already installed the most recent driver for the graphics card.  

Help please??  It's annoying!

---

### Post by opethfan89 on 2009-06-21
1) Kubuntu 9.04 (Jaunty)

**HP Pavillion 753n**
Intel Pentium 4A, 2533 MHz (4.75 x 533) Processor
1024 MB  (DDR SDRAM) Memory
500GB IDE Disk Drive HDD
NVIDIA GeForce FX 5600  (256 MB) GPU
Realtek RTL8139 Family PCI Fast Ethernet NIC  (192.168.0.101) Ethernet
PIONEER DVD-RW  DVR-105  (DVD:4x/2x/12x, CD:16x/8x/32x DVD-RW) Primary DVD-RW Drive
GVision L7EH  (131331301963) Monitor
FIC VC19  (6 PCI, 1 AGP, 3 DIMM, Audio, LAN) Motherboard

I am using a HP Pavillion 753n. I transplanted the motherboard from the original case into an Antec Three Hundred case, and the front-mounted USB ports and everything work fine.

Other than that, using a Logitech Wireless USB Mouse, standard PS/2 keyboard (with multimedia buttons, but I haven't tried using ndiswrapper to make that work since I only recently found the XP driver for it).

I have a HP Photosmart C4480 Printer but I haven't used it quite yet, haven't had to print anything in Kubuntu yet.

No special configuration settings, am plugged in hard-wire to ethernet so I haven't had to setup wireless internet yet, although I do have a D-Link DWL-132 wireless adapter that works fine.

Everything else worked fine, didn't need to install any special driver for the graphics card, as the default one works fine.
[B]
The only thing that did not work correctly was the LITE-ON DVDRW LDW-451S  (DVD+RW:4x/4x, DVD-RW:4x/2x, DVD-ROM:12x, CD-RW:40x/24x/40x . Will post details in the "hardware incompatibility list".

[/B]

---

### Post by david.birch on 2009-06-22
Asus P5B-VM, Nvidia 8600GT, Hauppague Nova-T-500, Leadtek usb dongle

8.04 & 8.10 intrepid 

no issues with live CDs - install was flawless

mainboard functions 100% - was using both IDE & Sata, and onboard lan, onboard video was fine, but i needed DVI & so used nvidia 8600GT (gigabyte), only mainboard issue was that i couldn't get onboard nic to work with WOL. I used latest v4l drivers for Nova-t-500 & leadtek dongle, and all functions worked correctly. SPDIF also worked off the mainboard headers with newer alsa versions - ac3 pass thru worked on mythtv, mplayer etc

---

### Post by chessnerd on 2009-06-23
Dell Optiplex GX240 with Ubuntu 8.04 Hardy Heron installed on a dual-boot system

Specs:
1.7 GHz Pentium 4 Processor
384 MB RAM (one 256 stick and one 128 stick) with 133 MHz FSB
Two hard drives, a 40 GB with Ubuntu and a 20 GB with Windows 2000
NVIDIA 3DForce FX-5200 128 MB video card (works with both Ubuntu's open source drivers and the proprietary drivers)
Dynex DX-SC51 sound card (mobo sound card had to be deactivated for this to work in Ubuntu)

Ubuntu runs pretty well, although not as fast as Windows 2000. RAM usually sits around 170 MB when idle and it's never peaked 300 MB (however, at it's peak, the swap has gotten up to 250 MB). The processor runs at it's peak when using YouTube and can't seem to handle playing Pandora in the background while doing anything mildly resource intensive. Sound is good quality and the video card/CPU can handle the cube desktop along with most other advanced settings (however, it can crash if too much is going on at the same time). Boot up time is pretty quick but it takes a while to load up GNOME (usually 1.5 to 4 minutes).

---

### Post by RJARRRPCGP on 2009-06-24
> **skip27 said:**
> 
[*]AMD Athlon(tm) XP-M 3000+ Processor (based on AMD64 K8 core)


Wrong, Athlon XP-M is not a K8-based processor! 

It's 32-bit only!

---

### Post by JayFunGee on 2009-07-01
Ubuntu 9.04 on:
FUJITSU SIEMENS  Dual core 3.06 Ghz P5SD1-FM2
ATI Technologies Inc RV515 [Radeon X1300]
1 Gig of RAM
250 GB HDD
SiS AC'97 Sound Controller 

Also running 
Epson TX100 Combo (Printer, Scanner)
AMW 19" Monitor

Everything worked with little need for configuration, EXCEPT the scanner. Info from the Ubuntu forums where not very helpful, in the end I used a driver from AVASYS. Easy install, worked straight out (once I managed to navigate through the site): [http://avasys.jp/hp/menu000000900/hpg000000859.htm](http://avasys.jp/hp/menu000000900/hpg000000859.htm)

---

### Post by Vasator on 2009-07-01
Gigabyte GA-MA69VM-S2 Mainboard
AMD64 4000+ 2.2Ghz
Gigabyte Nvidia Geforce 9500GT (GV-N95TOC-1Gl)
8GB of Crucial DDR2 800 RAM (2GB*4)
LG Flatron W2252TQ 22" Widescreen Monitor
Saitek Eclipse K/B (USB)
Kensington Expert Mouse (USB)
80GB + 250GB WD(SATA)
XP 64-bit / Ubuntu 9.04 64-bit Dual Boot

Only issue is with the 9500GT and 3-D Acceleration
VirtualBOX runs like a dream

---

### Post by mk1w86 on 2009-07-01
Ubuntu 9.04 Jaunty Jackalope AMD64

Intel Core2 Quad Q9550 2.83GHZ Processor
Asus P5Q SE Plus Motherboard
Corsair 2x2GB DDR2 1066MHZ Dual Channel RAM TWIN2X4096-8500C5
Palit/XpertVision Nvidia 9500GT 512MB Graphics Card (DVI and VGA work but have not tested HDMI)
Western Digital Black 1TB Sata Hard Drive WD1001FALS
Neovo H-W22 22" LCD Monitor works with DVI at 1680x1050 (Have not tested VGA but it should work)

---

### Post by ridowan007 on 2009-07-05
Ubuntu: 9.04(Gnome & KDE)
CPU: Pentium 4 2.0A GHz
GPU: Nvidia GeForce 6200(with Nvidia sites driver)
Network: Broadcom Prolink Lan Card, LG U8290 mobile(for GPRS/3G connectivity with wvdial)
DVD RW: Samsung DVD Writer

---

### Post by HavocXphere on 2009-07-05
1)Version Of Ubuntu
9.04 64bit No major modifications

2)Type Of Hardware
USB Headset w/ microphone

3)Hardware Maker
Microsoft

4)Hardware Model
Lifechat LX-3000

[http://www.microsoft.com/hardware/digitalcommunication/productdetails.aspx?pid=006](http://www.microsoft.com/hardware/digitalcommunication/productdetails.aspx?pid=006)

Details: Works as expected without drivers/custom config. The only thing that does not work is the button usually assigned to MSN Messenger. The other buttons (Vol up, Vol Down and Mute Mic) work perfectly. Build quality is good.

---

### Post by user11 on 2009-07-05
Ubuntu, all variants and releases, cannot utilize drivers for PCI video cards. There is no troubleshooting for this anywhere. So as usual, I have to keep windows XP.

---

### Post by Mike-Chopper-Reeves on 2009-07-06
Tmobile HUWAI E220 wireless broadband stick worked straight out of the box on my Ubuntu 9.04 powered acer travelmate 201dx (10 years old, surprised it still does anything!). I do however have a "spare" HDD with XP on it so I tried out the stick on that first and used the setup info to facilitate installation on Ubuntu. Must get a drive enclosure for the spare!

---

### Post by Estroyer on 2009-07-06
[B]1)Version Of Ubuntu: Ubuntu 9.04
2)Type Of Hardware: Wacom Bamboo Tablet
3)Hardware Maker: Wacom
4)Hardware Model: MTE-450
[/B]

---

### Post by Shikaku2 on 2009-07-07
MT6458 Gateway Laptop
Ubuntu 9.04 Jaunty
Out of the Box everything works except Wifi.  Required ndiswrapper.

I have attached the needed drivers for the Wifi.  This works for a lot of Marvell wireless cards.

---

### Post by deepakdeshp on 2009-07-13
Can I know if

[LIST=1]
[*]Is KVM virtualization is supported for  AMD 7750 and AMD 550 processosrs on Ubuntu 9.04 server and desk top.
[*]Does  Asus M2N68A plus motherboard  work on buntu 9.04 server and desk top?
[/LIST]

---

### Post by vioup on 2009-07-14
HARDWARE:
HP NX-6320 laptop
1.66 core 2 duo
945 graphics chip on Mboard.
2 x 1GB 667ddr2 SDRAM
320 gb HDD
SIL 32 RAID PCI-e card used for ESATA.

UBUNTU  VERSION;
super O/S 9.04 running for approx 2 weeks flawlessly.
Prior version was super o/s 8.10 (not so good with motherboard).

BIG HARDWARE PLUSES FOR THIS VERSION;
* Runs instantly + Flawlessly on live USB, + over previous Super_OS.
* All buttons work (volume, wireless etc). - unlike prior version.
* Keeps cool + can hibernate. - unlike last time.

POSSIBLE  FUTURE IMPROVEMENTS:
* Battery life's a little better than vista, but not as much as i expected (little effect from dimming screen, scaling down cpu, changing display resolution etc).
* Any Load seems to hardly affect the RAM usage (flat at approx 300MB), instead hitting the CPU.
* The 2 CPU cores appear to be a little less synchronised (lag of approx 1.5 seconds between them).

TIP THAT GOT eSATA CARD WORKING:
* Disable 'native' SATA mode in bios first.
* Transferring between laptop and TB drive (NTFS formats) not as good as vista (CPU + speed).

WATCHING VIDEO IS EXTRAORDINARILY FAST COMPARED TO VISTA. (e.g. 4-5 playing at once smoothly).

THE LIVE USB RUNS VERY VERY NICELY - will do a fresh install instead of putting it on top of version 8.10 partition.

---

### Post by Phlex_de on 2009-07-14
Ubuntu 9.04
Wlan Pci Card
Edimax
EW-7728In

Working out of the Box.
[SIZE="1"](I needed to turn SSID Broadcast on in my router settings.)[/SIZE]

---

### Post by veedubgent on 2009-07-15
re ASUS M3N78-EM
with ubuntu 9.04


what does not work
1. desktop effects
2. card reader or digital camera via usb
One can easiy be turned off but the camera problem is a nuisance.
Does anyone have the answer. 
A vista disk is on the desk and I want it to stay there!!!
Please help if you can. hope the download for the problem comes soon.

---

### Post by Raeannmac on 2009-07-23
Hardware:
HP DV6934ca laptop
2.0 ghz core 2 duo
Intel onboard graphics (can't recall).
3 gigs ram
320 gb HDD

Current Version:
-9.04 but about to test 9.10 (mint, kubuntu, sabayon, and opensuse all work as well...with their own respective problems)

Works well: 
-the HP quicklaunch buttons work Perfectly in ubuntu...no other distro worked out of the box like this!
-sound works fine as well...even on Youtube (which I've had problems with in every other distro I've tried)
-runs incredibly fast! (ext 4)

Not so good: 
-Online videos skip around which is most likely due to the intel graphics...to be fixed in 9.10 I hear.  Videos I actually have on my computer run perfectly, however (flash issue I believe)

Overall...it's about a Billion times better than Vista!...Just bought a brand new quad-core desktop and right off the bat Vista has frozen almost 10 times in less than a week!! I've never had any problems with freezing or anything related on Ubuntu or Kubuntu.

---

### Post by Idaho Dan on 2009-07-24
Jaunty Jackalope

Scanner

Xerox

Documate 510

---

### Post by linuxwonder on 2009-07-24
Linux: Jaunty (9.04)
System: Wind PC w/Atom CPU
Make: MSI

Canon Pixma Mp470 Scanner/printer(USB)
Dell 1100 Laser Printer(USB)
Logitech Optical Mouse(USB)
Sony CD/DVD reader/burner

---

### Post by conradin on 2009-07-25
OS == Jaunty 9.04
 description: 
*-Motherboard
       product: D845GVSR
       vendor: Intel Corporation
       physical id: 0
       version: AAC45439-303

*-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.80GHz
          vendor: Intel Corp.

*-storage (RAID - IDE)
                description: Mass storage controller
                product: PDC20268 (Ultra100 TX2)
                vendor: Promise Technology, Inc.

 *-pci
                description: PCI bridge
                product: DECchip 21152
                vendor: Digital Equipment Corporation

 *-disk
                description: ATA Disk
                product: WDC WD400BB-00DE
                vendor: Western Digital

 *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio   Controller
             vendor: Intel Corporation

 *-pci
                description: PCI bridge SCSI controller
                product: AHA - 2940W/2940UW 
                vendor: Adaptec

---

### Post by QKC on 2009-07-26
OS-Ubuntu 9.04
Motherboard-Intel D845GBV,Version-AAA84548-202
CPU- Intel(R) Pentium(R) 4 CPU 1.80GHz 
RAM-768(512+256)
Storage-Maxtor 6L080P0
CDRW-Model_CD_RW_CRW4048.Vendor-AOPEN 
Network Card-RTL-8139/8139C/8139C+.Vendor-Realtek Semiconductor Co.Ltd.

---

### Post by Harry83 on 2009-07-27
> **ChrisLilley said:**
> Ubuntu 6.10
Dell Precision M90 laptop workstation:
2.0 GHz Core 2 Duo T7200, 4Mb cache | 2Gb (2*1024) Samsung DDR2-667 5.0-5-5-13 | Seagate Momentus 7200.1 100GB 7200, 8MB cache | NVIDIA Quadro FX2500M, 512Mb, driving 1920x1200  LCD | Maxtor 3200 USB2 500GB 7200, 16MB cache | Sony DVD+/-RW DW-Q58A  |  Broadcom gigabit ethernet

The processor is not recognised, but runs, and is correctly shown as two cores.
The video card - the OpenGL version of the G71 core as used on 7900GTX - is not recognised, shown as an 'unknown device 029a', but runs at native resolution and full color depth. Adding the NVIDIA-supplied binary driver enables full OpenGL support which works well.

The Ricoh SD/MMC/MemoryStick/xD reader is partially recognised.

I have not tried the IEE1394 port or the smart card reader.
Sound works, burning DVD works.

Me too using the same laptop.

Regards

Harry

---

### Post by Sepanderi on 2009-07-31
Ubuntu 9.04

DVB card: TerraTec Cinergy C DVB-C PCI

Motherboard: Asus M3A78-EM AMD 780G mATX AM2+
Ethernet, sound and graphics adapters work fine.

HTPC case: OrigenAE S14V HTPC

IR module and VFD display VF210 VFD/IR Module
Works fine (follow manufacturer's instructions to install Linux drivers)

Philips RC197 Vista Media Center remote control
Works fine (follow manufacturer's instructions to install Linux drivers)

---

### Post by meka4996 on 2009-08-03
Ubuntu 7.04 and 8.04 and 8.10 and 9.04
MB: ASUS M2A-VM AMD Athlon(tm) 64 X2 4000+ AM2 Dual Core Processor 
Graphics: onboard ATI Technologies Inc RS690 [Radeon X1200 Series]
sound card: onboard SBx00 Azalia (Intel HDA)
RAM: Kingston KVR667D2N5 1GB DDR2

Wireless Adapter: 
TP-Link TL-WN321G 54M USB 148f:2573 Ralink RT2501USB
D-Link DWA-130, works with ndiswrapper, make sure to get rid of all other wireless drivers to avoid conflict

Microphone: Logitech USB Desktop Microphone AK5370
Printer: HP LaserJet 1022, downloaded driver is optional
WebCam: Logitech QuickCam Pro 9000, worked with Ekiga, but now it causes my usb wireless adapter not working, see [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

HDD: Seagate SATA2 80G ST380815AS
HDD: Western Digital SATA2 160GB WDC WD1600AAJS
DVDRAM+/-RW: LG HL-DT-ST  GH22NS30

no problems, everything works out of box! Thanks Ubuntu for my freedom!

---

### Post by Insomniacno1 on 2009-08-09
IBM Thinkpad 770Z, upgraded to 324MB Ram, 40GB HDD, Internal CD-rom drive, Ubuntu 9.04 Desktop.

Sound works now after using these guides:

[http://www.thinkwiki.org/wiki/Problem_with_broken_sound_on_some_ThinkPads](http://www.thinkwiki.org/wiki/Problem_with_broken_sound_on_some_ThinkPads)
[http://www.thinkwiki.org/wiki/Script_for_configuring_the_CS4239_sound_chip_in_PnP_mode](http://www.thinkwiki.org/wiki/Script_for_configuring_the_CS4239_sound_chip_in_PnP_mode)

an installing modconf by synaptic's package manager

Then run modconf from command line adding support for cs4236 and cs46xx which apperrently is blacklisted from start(not mentioned anywhere in ubuntu doc), then find ALSA blacklist conf and remove cs4236 and cs46xx from the list. If still not working then reinstall all to do with ALSA.

Video in 1024x768 works after adding the following to /etc/X11/xorg.conf, otherwise video only works in 800x600:

# xorg.conf (xorg X Window System server configuration file)
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

Section "Files"
EndSection


Section "Device"
   Identifier   "Trident Microsystems CyberBlade XPAi1"
   Driver      "trident"
   BusID      "PCI:1:0:0"
EndSection

Section "Monitor"
   Identifier   "Generic Monitor"
   Option      "DPMS"
   HorizSync   28-51
   VertRefresh   43-60
EndSection

Section "Screen"
   Identifier   "Default Screen"
   Device      "Trident Microsystems CyberBlade XPAi1"
   Monitor      "Generic Monitor"
   DefaultDepth   24
   SubSection "Display"
      Modes      "1024x768"
   EndSubSection
EndSection


SMC - SMCWUSB-G EU USB wifi stick (Works with WPA and WPA2 Personal - I have not tested other).

Otherwise Ubuntu runs just fine:)

---

### Post by rhapa' on 2009-08-10
ubuntu 9.04
mb ASUS m3a78-em , AMD athlon x2 64 5000+, GT 8600, LG dvd-ram gh22ns30, hd Samsung hd322hj 320gb, fonte 430 real watts.

OS doesnt work, crashing around 5 min after log on. Cant recognize any hardware configuration.

---

### Post by E-RPM SOFT COM on 2009-08-11
OS: Edgy Eft
Motherboard: VIA EPIA MII-12000 Mini-ITX
Processor: VIA C3 1.2GHz
RAM: pqi POWER series DDR266 1GB
HDD: Toshiba 40GB 2.5"
PCMCIA: Zoom Bluetooth Adapter
PCMCIA: Linksys WPC54G 802.11b/g

Linksys WPC54G PCMCIA card, it is recognized, but I haven't tested it yet.


Laptop

OS: Edgy Eft
Model: Toshiba Satellite P15-S479
Processor: Intel Pentium 4 HT 2.8GHz
RAM: 1GB
HDD: Hitachi 100GB 2.5"
DVD: NEC DVD+-RW DL Burner
Graphic: nVidia Go5200
Net: Onboard NIC 10/100 and Onboard Atheros 802.11a/b/g

Texas Instruments onboard SD card reader doesn't work

---

### Post by NM5TF on 2009-08-12
Dell Inspiron 531S
AuthenticAMD
AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ [Family 15 Model 107 Stepping 1]
(2 processors)
Linux 2.6.28-14 Generic Ubuntu 9.04
Memory 1 GB
HDD 226 GB

can't mount my Olympus MAUSB-10 Smart Card reader to read pix....

lsusb says it sees the reader....and I see the device in the Computer
screen, but it gives an error msg stating "can't mount device as it
contains no media"....the device worked splendidly in Win XP on my
Wife's laptop, so it's not a device/cable issue....

all the "gurus" say it should have been taken care of in 8.10 and 9.04
for certain by the new Alauda drivers....but it still doesn't work...

Tom

---

### Post by tonyps on 2009-08-15
Toshiba A505D-SS6958
AMD Turion-X2/64
4GB RAM
500GB HD
ATI Radeon 3100
Built-in Ethernet:
SUCKS!!- now using Netgear WG111v3 USB wireless adpater(awesome, plug-n-play) 02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)
Works, first time, no issues- 03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
 Realtek
Output from "lspci"
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
05:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
05:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
05:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)

---

### Post by Elijah on 2009-08-18
1) 9.04 Jaunty
2) Epson Stylus CX5500

*SCANNER DOESN'T WORK RIGHT OUT OF THE BOX* - strangely stopped working in 9.04
To make it work: 
[http://ubuntuforums.org/showthread.php?t=908443](http://ubuntuforums.org/showthread.php?t=908443)

---

### Post by #11u-max on 2009-08-21
ubuntu 9.10 karmic [testing]
acer aspire 4520
notes: everything seemed to work out of the box with the exception of having to install a driver for my nVidia GEforce graphics card.
kodak easyshare 5300 printer does not work with my computer but i think that falls on kodak because they don't supply **ANY **drivers for unix/linux.

---

### Post by Cavs23 on 2009-08-22
CPU: AMD X4 II Phenom 955 Black Edition
MoBo: Biostart TA900GX A3+
Video Card: Evga GTS 250
RAM: 8GB OCZ DDR3 memory
Jaunty

Upon first boot it seemed fine. After a while the xorg.conf file got a bit jumbled with the new hardware and the nvidia settings. Had to wipe it out, copy an older one into it, do a dpkg-reconfigure and reinstall nvidia settings. Other than that, this setup rolls.

---

### Post by COOLDUDEGAMER on 2009-08-22
A couple different video cards tested in Ubuntu by me.

Video card compatability - Ubuntu driver compatability status

Video card - ATi Radeon X1950XT

Ubuntu Version ----- Result

Ubuntu 8.XX --------- Pass, drivers available   
Ubuntu 9.XX --------- Fail, (card no longer supported by ATi - AMD)

Video card - NVIDIA GeForce2 MX200

Ubuntu 8.XX --------- Pass, drivers available
Ubuntu 9.04 --------- Pass, drivers available
Ubuntu 9.10 --------- Fail, 3D does not work when enabled; screen has messed up colors after reboot. Driver problem standard 96.XX driver. 

I will test and post results for more video cards in the near future when I have more time.

Edit 1 : Fixed formatting of text.
Edit 2 : New data about the GeForce2 MX200 compatability. I will retry and post as soon as I retest it with the new driver release from NVIDIA.

---

### Post by grayrainbow on 2009-08-22
HP Pavilion dv5 1210eq
Ubuntu 9.04(jounty)
AMD Athlon x2 dual-core QL-64
ATI Mobility Radeon HD 3400
Realtek Semiconductor RTL8111/8168B PCI Express Gigabit Ethernet controller
Atheros Communications AR242x 802.11abg Wireless PCI Express Adapter
sound - ATI Azalia (Intel HDA)

Almost everything working out of the box, notable exeptions - front speaker audio(hdmi still don't tested),  there's enough info in the forum sound to be configured(so it's work now :)). And other is dual display, enabled from ATI driver break all graphic, but can work with display preferences utilitie(can not set diferent resolution to displays). Everything else(including bluetooth, remote and touch buttons) works amazing

---

### Post by mexjim on 2009-08-24
Gateway NV58 T6500 4gb/320gb laptop.

Ran 9.04 live cd ok, usb stick 9.04 ok

Installed 9.04 dual boot with vista-no problems

Everything I've tried worked ootb including wireless, video, audio(mic and speakers), and webcam.  I haven't use firewire, ethernet, hdmi, or an external monitor yet.

---

### Post by Otustelija on 2009-08-26
Graphics card: Ati/His Radeon HD 4850, on Ubuntu 9.04 Jaunty.

The open source driver worked on first run with resolution 1920x1080 (monitor native).

Installing the proprietary driver through Hardware Drivers also allowed desktop effects.

---

### Post by djchandler on 2009-08-29
[COLOR=Red]_**Toshiba Satellite L305D-S5959 Laptop**_[/COLOR]
   Ubuntu 9.04-AMD64 (Jaunty Jackalope) Everything works OOTB
   **Processor and Chipset**
       AMD Athlon&#8482; X2 Dual-Core Processors for Notebook PCs QL-65
          2.1GHz, 1MB L2 Cache, 4.0GT/s
       AMD M780V Chipset
   2GB DDR2 800MHz (max 4GB)
   250GB (5400 RPM); Serial ATA hard disk drive
   DVD SuperMulti Drive
   **Display**
      15.4&#8221; diagonal widescreen TruBrite® TFT LCD display at 1280x800
      native resolution (WXGA)
      Native support for 720p content
   **Graphics**
      ATI Radeon&#8482; 3100 Graphics
   **Sound**
      Built-in stereo speakers
      Sound volume control dial
   **Input Devices**
      86 key US keyboard
      Synaptic TouchPad&#8482; pointing device
      TouchPad&#8482; Enable/Disable
   **Communications**
      Modem
      10/100 Ethernet - Realtek 8102
      Atheros® 802.11b/g wireless LAN10
   **Expandability**
      2 main memory slots. Both slots occupied.
      ExpressCard&#8482; slot (ExpressCard/34 and ExpressCard/54)
      Memory Card Reader - Secure Digital, Memory Stick&#8482;, Memory Stick PRO&#8482;, MultiMedia Card
   **Ports**
      Video - RGB (monitor Dsub-15) output port
      Audio - Microphone input port, Headphone output port
      Data - USB v2.0 &#8211; 3ports; RJ-45 LAN port; RJ-11 modem port
   **Physical Description**
      Matte Silver
      Dimensions (W x D x H Front/H Rear): 14.3&#8221; x 10.6&#8221; x 1.33&#8221; /1.51&#8221; without feet
      Weight: Starting at 5.49 lbs. depending upon configuration
   **Power**
      75W (19V x 3.95A) 100-240V AC Adapter

---

### Post by wm_brant on 2009-08-31
New system -- installed and running 64-bit Ubuntu 9.04 desktop on:

Motherboard: Gigabyte GA-MA770T-UD3P
CPU:  AMD Phenom II X4 945
Video:  []("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130485")EVGA 512-P3-N856-LR GeForce 9600GT Low Power
Disk:  []("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136284")Western Digital Caviar Black WD1001FALS 1TB (SATA interface)
Mouse:  Logitech MX 1100 Black 8 Buttons Tilt Wheel USB 2.4 GHz Cordless Laser Mouse

Has been running since last Thursday (5 days) without a single problem.  Used USB drives & mouse, Ethernet, hard disk and sound.  I've not tried the CD-Rom or FireWire.  I installed Ubuntu from USB thumb drive.

  -- Bill

---

### Post by techno-atom on 2009-09-02
Ubuntu 9.04 Desktop Edition
Acer Aspire One Netbook

Intel Atom 1.60 Ghz / 1.60 Ghz Processor
1GB DDRII Ram 533 Mhz
Intel GMA 950 Family Chipset
10.2 Inch Monitor
Integrated SD slot

Runs great, no problems.

---

### Post by gradinaruvasile on 2009-09-02
Ubuntu 9.04

Motherboard: ASUS M3N78-VM
CPU: AMD Athlon 3200+
Video: Integrated Nvidia 8200
MEM: 2 GB 800 MHz DDR2

Just works. I just replaced the motherboard, switched on, and everything was working (previously i had an ASUS M2V-TVM mobo). I had the proprietary drivers installed for my nvidia GS 7600 PciEx vid card.

I tried it with karmic alpha4 livecd (usb) and [COLOR="Red"]it seems the nv driver does not recognise the 8200 IGP[/COLOR] - i installed the proprietary drivers in livecd mode and that way it had it working.

---

### Post by techfanboy81 on 2009-09-04
I'm glad somebody posted the same specs as my PC no need to search for compatibility list.

---

### Post by julzius on 2009-09-06
Ubuntu 9.04

Intel i7 920 (2.66ghz)
Ati 4890 (envy drivers don't work properly, download them from the ati website)

Have compiz and all that working seemlessly.

---

### Post by niw_uk1964 on 2009-09-08
Ubuntu 9.04 32 bit.
HP all-in-one 4480 printer/scanner/copier.

Works perfectly with the appropriate hplib files installed.

---

### Post by fr4nky on 2009-09-11
[FONT=Tahoma][SIZE=2]**Hey guys, I am new to the linux world and i play i using the ubuntu 9.04 i have a dell gx280 does anyone know if all of ubunto 9 will work on my machine?? Also is there a list on what ubuntu 9.04 support's, like the newest hardware and all?**[/SIZE][/FONT]
[FONT=Tahoma][SIZE=2][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=2]**please email with info @ **[/SIZE][/FONT][EMAIL="Fulbldital@hotmail.com"][FONT=Tahoma][SIZE=2]**Fulbldital@hotmail.com**[/SIZE][/FONT][/EMAIL]
[FONT=Tahoma][SIZE=2][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=2][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=2][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=2]**Thanks.**[/SIZE][/FONT]

---

### Post by Turnitup on 2009-09-11
> **Bruce S said:**
> If you want to be sure of a printer installing OK, I think the only one you can be sure of is HP . 
My HP L7580 installed without a hitch .Plus HPLIP Toolbox available 
and have installed it. Makes using the printer very easy. Can check ink available , head info. etc.etc.
Lexmark seems to be bottom of the heap !
 
 
Did the bluetooth on your HP L7580 printer work as well?

---

### Post by tommy_m on 2009-09-17
[B]Info:

1)Version Of Ubuntu - ubuntu 9.04 x86_64
2)Type Of Hardware - laptop/notebook
3)Hardware Maker - ASUS
4)Hardware Model - x59gl

[/B]extra: works really good! only prob. so far is that there is no battery status when running on battery. make sure to install heath monitoring software and keep an eye on the stats.

---

### Post by austinjl on 2009-09-18
Does it work? It works.

Here's how I got the Hercules Dualpix HD Webcam (06f8:3003 Guillemot Corp.) webcam camera working in Ubuntu 9.04 Jaunty Jackelope.

When I plugged the camera in, lsusb showed it, but there was not a /dev/video0. To get this, I ran

```
sudo modprobe gspca_ov534
```Now CHEESE showed the camera, and it worked fine.

When I tried to use it in Skype, the video showed up green. This command fixed that.

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```I set the ALSA capture to the integrated microphone in gnome-sound-properties. Skype audio worked, but the integrated microphone was not working, even though it worked in other applications. The easy way to get this working was to kill pulseaudio (set its "autospawn = no" in /etc/pulse/client.conf).

```
pulseaudio -k
```

---

### Post by AJROKR on 2009-09-19
Hello Everybody, 
 
Respected mods, Gald to be in Ubuntu forum, as of now i am new to Ubuntu. I am having a dual boot with Ubuntu 9.04 32 bit edition with XP. Always facinated about linux based systems and finally installed ubuntu 9.04 2 weeks back in my Laptop. I want to migrate to Ubuntu completely in a shortwhile.
 
This is my sytem : Intel Core 2 duo T5750(2Ghz), 1GB RAM, 160GB 5400rpm HD, 14.1in 1280x800 LCD, Intel X3100, CDRW/DVDRW, Broadcom 802.11bg wireless, Bluetooth, Modem, 10/100 Ethernet, Touchpad, Camera Built-in, 6c Li-Ion.
 
Is there any specific drivers for my hardware, if so where is it available?
Everything is working as of now still i have some worries on the performance of the hardware compared to xp. will i get same or more performance with Ubuntu? How it can be achieved?
 
As of now i have some issues with audio, sometimes it creates some annoying sound. I have an realtek HD hardware with dolby in the system. 256 inbuilt intel graphics.
Bluetooth is working - as in detecting other devices but not able to transfer data.
Anysoftware where in i can switch on the cam in yahoo or any messenger - (Mywebcam is working)
 
I also want to shift to 64bit edition since my system is 64 bit - Need advice on this too.
Thanks

---

### Post by pdxie on 2009-09-20
[B]
1)Version Of Ubuntu: 9.04 
2)Type Of Hardware: Netbook 
3)Hardware Maker: Acer
4)Hardware Model: [/B]  [FONT=&quot]Aspire one D150-1165[/FONT]

---

### Post by pdxie on 2009-09-20
**_Give detailed explanations when reporting compatible hardware._**

**Also Do not post any lspci outputs in this thread as they will be removed with out question.**

[B]Please Only List
1)Version Of Ubuntu: 9.04 
2)Type Of Hardware: External Optical Drives on Acer Aspire One D150 Netbook
3)Hardware Maker: Acer
4)Hardware Model[/B]: Acer Aspire One  [FONT=&quot]D150-1165[/FONT] 

Ubuntu 9.04 clean installed (replaced Windows XP Home as shipped); System: Intel Atom  [FONT=&quot] N270, 1.60GHz[/FONT], 1 GB RAM, 10.1", 6-cell battery. BIOS name & version: InsydeH2O, v1.05. 

Used Synaptic Package Manager and/or Update Manager to update Ubuntu security as well as a myriad of open source apps. D-Link 614+ Home wireless network worked right off the bat, automatically, as did all sound and multimedia (Except for Skype with built-in web cam - no video, no sound input recording, while Ekiga worked automatically! Will be working on this problem.)

External drives worked plug n play:
New Samsung 8x DVD+/-RW slim USB drive, as did an
older Samsung TS-H552 4x DVD+/-RW drive via a Cables-to-go USB 2.0 TO IDE or SATA Drive Adapter

---

### Post by Drakebyte on 2009-10-04
**HP Compaq Presario CQ60**

_Tested Versions:_
Ubuntu 9.04
Ubuntu 9.10
Ubuntu 8.04 LTS
Ubuntu 8.10

_Per version notes:_

**Ubuntu 9.04 and 9.10**
Nothing to note, everything works out of the box, wireless card is found and works accordingly. All hardware is recognised, as well as the touch pad. All that doesn't work is the button that enables you to turn off/on the touch pad and the wireless button as they only work with HP proprietary drivers for Vista (only).

**Ubuntu 8.10**
Same as above, except that wireless does not work.

**Ubuntu 8.04 LTS**
Works fine until I install any video drivers, which means that after booting I have only a black screen, not even the splash comes up.

---

### Post by t0p on 2009-10-05
Even though I think this thread is crap (how the hell are we supposed to search it?!) I'll post some hardware compatibility info.

This is all based on **Ubuntu 9.04**:

**Fujitsu Storagebird** External Storage HDD 3.5" 400GB, USB connection - works fine.

**Huawei E160X aka Vodafone K3565** **GPRS/UMTS/HSDPA USB modem** - works fine with Network Manager, but no access to SMS.

---

### Post by timsdeepsky on 2009-10-07
Ubuntu 9.04....
Cirago Bluetooth USB adapter....
BTA-6210 V2.1....

This bluetooth adapter worked perfectly out of the box....
I use it to transfer to and from my Motorola V3C cell phone....
Works perfectly and i love it....
UBUNTU ROCKS BABY....

---

### Post by silvanus2005 on 2009-10-14
I am runnng Ubuntu netbook remix 9.04 on an Asus EeePc 1000H. Everything is working fine, out of the box.

---

### Post by Mi*6d@# on 2009-10-16
Here comes my list.

**Ubuntu version: 9.10 Karmic Koala x86-64**

**_LIST_**
**1) Joystick Logitech Cordless Freedom 2.4, USB** (out-of-the-box)
**2) Keyboard Logitech G15, USB** (partially ootb, fully with g15daemon package)
**3) Mouse Logitech MX Revolution, USB Bluetooth** (out-of-the-box)
**4) Microphone Logitech USB Desktop Microphone, USB** (out-of-the-box)
**5) Printer HP Deskjet D2563, USB** (out-of-the-box)
**6) Printer Canon BJC-250 Bubble Jet, LPT (1997)** (partially, as Generic Printer)
**7) Voice Recorder OLYMPUS WS-450S, USB for file downloading** (out-of-the-box)
**8) External HDD Seagate 500GB, Firewire, NTFS** (out-of-the-box)

---

### Post by pablolie on 2009-10-21
Ubuntu 9.04
(runs well with)
Shuttle X27 (Atom 230, 2GB RAM, Intel 945 driving 1600x1200))

Frequency stepping does not work, CPU loccked at 1.6GHz, but it is not an issue since CPU only consumes 4W and the entire computer just consumes 27-29W, tops.

Awesome little green machine, very usable.

---

### Post by jackharvest on 2009-10-21
1)Version Of Ubuntu: Jaunty 9.04
2)Type Of Hardware: Dell Precision m70 Laptop Workstation
3)Hardware Maker: Dell
4)Hardware Model: Precision m70

Other notes: Perfect out of the box. Quadro FX 1400 Go type video card. 2.0 Ghz, Intel Centrino (Pentium M) inside. Laptop is 5 years old, and running this without a hitch.

---

### Post by coller_girl on 2009-10-27
Karmic koala 
usb camera and microphone Microsoft Lifecam vx-1000
sound recognised / mouted as seen in sound pref yet no input on either mic or camera. merly screen of green and thin line of pixilation at the top

---

### Post by grayrainbow on 2009-10-29
HP Pavilion dv5 1210eq
9.10(Karmic Koala)
AMD Athlon x2 dual-core QL-64
ATI Mobility Radeon HD 3400
Realtek Semiconductor RTL8111/8168B PCI Express Gigabit Ethernet controller
Atheros Communications AR242x 802.11abg Wireless PCI Express Adapter
sound - ATI Azalia (Intel HDA)

Again(like 9.04) almost everything work(this time and a little audio tweak is not needed).
Just hdmi, remote controll, and dvd burner(don't think this will be problem) not tested. And still problems with compiz, got 3d acceleration, but effects are quite buggy(that's not new), however 3D games work fine.

---

### Post by plat4m on 2009-10-30
Ubuntu 9.10 -32bit

core2due e5500, 4gb ram, sata hd, sata dvd-rw-r, nvidia go7300, 15,4" 1680x1050 display.

Lenovo 3000 series, N100, 0768-bkg

Lenovo/IBM

Everything works perfectly out of the box, except webcam & fingerprint which needs some hacks. Nvidia drivers I (recommended #185) for use with compiz.

Enjoy
- Thomas

---

### Post by priegog on 2009-10-31
1)Version Of Ubuntu: 9.10 (64-bit)
2)Type Of Hardware: Laptop
3)Hardware Maker: Asus
4)Hardware Model: K50in

Everything pretty much works out of the box, except the webcam image is upside down. There is a fix for that somewhere in these forums.
edit: oh right, the ACPI calls seem to not be working perfectly, because the "restart" action does nothing. and you can only suspend the computer once per session.. after that, it just won't work.

---

### Post by Janneman27 on 2009-11-02
Acer Travelmate 5620 with Ubuntu 9.04 Jaunty (GTK+)

Intel Core 2 Duo T7200 CPU - 2GHz
Nvidia GeForce Go 7300 GPU - 128MB
DDR2 677MHz RAM - 2GB

Everything works perfectly, except the built-in webcam. It's alright though, 'coz I don't use it!

---

### Post by jrweiss on 2009-11-02
Works fine:

Ubuntu 9.04
Lenovo T500 2081CTO laptop
3 GB PC3-8500
Intel C2D T9400 2.53 GHz
ATI Mobility Radeon 3650
Intel 5300AGN WiFi
Boot from Patriot XT 16 GB USB stick

---

### Post by CDR Services on 2009-11-03
Installed 9.10 in an old Gateway 400vtx Laptop 2.0gz mobile p4 1.25 gig ram intel 855 graphics boots and works great. Oddly way better than 9.04! It found all the hardware SD card slots and all the only thing I havn't tested is the modem (but who uses them any more) the only issue I have with this machine is it reboots instead of shutting down, but it does that with every linux build i've tryed in it!!

---

### Post by jmore9 on 2009-11-03
Dug out my old CanonScan N650U scanner and hooked it up via usb and it worked first time,

Running 9.10 I had to do nothing special just worked,  Did not even have to reboot !!

---

### Post by sireon on 2009-11-08
Version: Ubuntu 9.10 32bit
Host: Asus k50 ab notebook

Seemingly everything works fine out of the box except:

- ati driver needed to be installed, but then works fine /haven't tried compiz though/

- issues with built-in microphone /needed pulseaudio to work and skype shouldn't control volumes/

- issue with built-in chicony UVC webcam /the video is upside-down, I tried everything (also like uvc patch or the libv4l thing), finally I post a reply in the appropriate thread to ask for help/

---

### Post by sciobivium on 2009-11-08
Ubuntu 9.10 on Lenovo x61 with 1 Gig RAM.  New install and everything seems to work great. Not done with testing but main components such as video, sound, wireless and wired Network all works as it should.  You can connect, disconnect multiple times from wireless Network and it works.  Very simple to add new wireless networks.  Very simple to adjust display settings.  

So far a very good release.  :-)

---

### Post by mrazster on 2009-11-08
```
)Version Of Ubuntu: 9.10 (32-bit)
2)Type Of Hardware: Laptop
3)Hardware Maker: Acer
4)Hardware Model: 5536G

```


Not much to say...everything seems to work. Using ati driver from synaptic. No problems detected yet.

---

### Post by monton on 2009-11-08
Laptop - Gateway ML6230

Celeron M 1.6
1.5GB RAM
WD Black 7200 160GB hard drive
Intel graphics
Ubuntu 9.04 ->Everything works

Fresh install 9.10 Everything works great, faster than 9.04, faster wireless connection. Internal modem driver must be deactivated for sound to work.

Hope it helps
M

---

### Post by Kuro-Chinko on 2009-11-19
Laptop - Lenovo ThinkPad SL-300

Core 2 Duo, 3GB RAM, 250GB HDD, Intel Graphics, Intel Wireless...etc.

I'm new to Linux. Installed Ubuntu 9.10 Karmic Koala on my laptop last week. Everything worked upon first boot, except for a few Fn+ key combos. Touchpad sensitivity needs some fiddling, but is mostly good.

I got some popping sounds when using headphones, but they're not there anymore, so I presume it was a glitch the the software updates patched up.

Overall, I'm having a very pleasant experience. Thank you, Ubuntu.

---

### Post by MIJ-VI on 2009-11-20
[B]32 bit Ubuntu & Ubuntu Studio 9.10:

[/B]- 3.20 GHz Pentium IV, 1 MB L2, 800 MHz FSB.

- ASUS P4P800-E Deluxe Rev. 1.02. BIOS Ver. 009 (The final stable ver. for this MoBo.)

- 3 GB DDR 400 RAM. (Running in dual-channel linear mode.)

- Nvidia-based EVGA e-GeForce 6200.

- SoundBlaster Live. (PCI card) (The MoBo's on-board audio works.)

- NEC FireWire 400/USB 2.0 PCI card. (The MoBo's on-board FW400 & USB 2.0 works)

- hField Technologies Wi-Fire. (USB WiFi adaptor)

- LG DVD-RAM GH22LP20 Firmware Ver. 1.03

[B]REGULAR HD's
[/B]
- WDC WD5000AAKS-0 (465.8 GB SATA II HD) Firmware Ver. 12.01C01

- WDC WD5000AAKB-2 (465.8 GB PATA HD) Firmware Ver. 12.01C02

**RAID 0**

- Maxtor 5T040H4 (38.2 GB PATA HD) Firmware Ver. TAH71DP0

- WDC WD400BB-00DG (37.3 GB PATA HD) Firmware Ver. 05.03E05

---

### Post by Sin@Sin-Sacrifice on 2009-11-20
This is a 9.10 x64, with studio affects added, box containing an XFX 750a SLI mobo with less than shabby acpi support, an AMD Phenom X2 9500 overclocked minimally to 2.6 GHz, Corsair 4GB RAM underclocked to 888 MHz, 2 WD SATA 500 GB hard drives, an old IDE 40GB WD hard drive, Wintv HVR-1600 tuner, an HP 15-in-1 media card reader I stole out of my mom's HP m8000n (What? I gave her the PC.), and the most compatible... a lot of love and care.

---

### Post by yasakbulut on 2009-11-23
Ubuntu 9.10 on Lenovo ideapad S10-2.
Everything works great, including built-in webcam and card reader. Display brightness can not be adjusted via the brightness applet, though. Anyways, that's not important, as the brightness can be set using Fn+up and Fn+down keys.

---

### Post by gslug79 on 2009-11-23
Desktop:
Ubuntu 9.10
Gigabyte MA790XT-UD4P
AMD Phenom II x3 720
4 GB DDR3
Asus EN9500GT video card (NIDIA)
1.5 TB HDD
VGA to a horrid little monitor - need to get a new one;)
Works except lmsensors does not support reading temp from Phenom II yet.

Mythbox (Frontend):
Mythbuntu 9.10
Gigabyte GA-73PVM-S2H Motherboard
Intel Pentium Dual Core E2200
1 GB DDR2
80 GB Laptop HDD
Onboard video (NVIDIA 7100)
HDMI to 32'' LCD TV - sound over HDMI has never worked.
Everything else works (though I haven't tried VDPAU)

Server/Mythtv backend (Headless):
Ubuntu 9.10, GDM disabled
Gigabyte GA-73PVM-S2H Motherboard
Intel Pentium Dual Core E2200
2 GB DDR2
3 Random HDDs
WinTV Nova-t PCI
Everything works.

Netbook:
EEEPC 1000HE
Ubuntu 9.10 Netbook Remix
Everything works, though 3G modem only works when it feels like it!

Laptop:
MacBook 2,1
Haven't tried 9.10 yet:redface:, but OS 10.5 works fine.....

---

### Post by uvaio on 2009-11-24
Sony Vaio VGN-SZ4VWN/X

using since 8.04
64 bit version of ubuntu

9.10 sorted out
1. no more issues with build in speakers, sometimes quite silent ticks are comming from built in speakers, but that is not a problem. Ubuntu thank you for fixing this ;o)
2. Memory stick duo slot is recognized and working now.

9.10 screwed up 
1. hibernation/sleep -> nvidia module doesn't want to unload resulting in screen locking only
2. webcam. due to different timings in new kernel module doesn't load properly in boot time. Must be reloaded manually. Then it works fine in skype and other apps. There are issues with flash. Video is distorted and once camera deactivated, it is not possible to activate again, you need to reload module in kernel again.

Never worked
1. fingerprint reader. The only driver I found that supports same hardware on other laptops is not workign and not supporting Sony laptops ;o(
2. functional keys (brightness) are not working out of the box, but this can be mapped manually.
3. webcam not working out of the box, you need to build driver module yourself.

Over all good job guys...

---

### Post by trevligsnubbe on 2009-11-25
These are the laptop computers I've tested :

**Dell D630** and **Dell D430** worked without problem on both 8.10x32 and 9.04x32

**Fujitsu Siemens S6120** worked without problem on 9.04x32 but was very slow, with 9.10x32 it run very smooth and nice --> 9.10 must be less hardware demanding

**Acer Aspire 4810TG** runs perfect on 9.10x64 on Intel Graphics only. The built-in ATI HD4330 doesnt work with the proprietary driver offered in Ubuntu.

---

### Post by almufadado on 2009-11-27
OS : Ubuntu 9.10 Karmic Koala (x64 i)
Kernel : Linux 2.6.31-15-generic
X: Gnome 2.28.1

Machine :
Processor : Intel Core2 Duo E6750 2.6GHz Socket 775
Motherboard : [Asus P5K SE]("http://asus.com/product.aspx?P_ID=I2f2e2yHI0XF2Vf9") 
Chipset     : Intel P35, Intel ICH9, Intel Fast Memory Access Technology 

Memory      : 4x 1Gb Kingston DDR2 1066MHz CL5 

LAN        : Integrated PCIe Gigabit LAN controller featuring AI NET 2
              Addon PCI Realtek 8129

Audio        : Integrated Realtek ALC 883 8 -Channel High Definition Audio CODEC     
              Analog speaker system 5.1

Storage     : Southbridge -> 4 xSATA 3 Gb/s ports
              Marvell 88SE6111 -> 1 xUltraDMA 133/100/66 for up to 2 PATA devices, 1 eSATA Gb/s port
Hardrives   : Seagate 500GB with 2 boot OS partitions (Ubuntu/Fedora), /home, /data
              Seagate 500GB with 2 boot OS partitions (XP / windows 7), /data 
              Samsung 1TB with /data /media /home_alt
              Seagate 200GB with /media

Graphics    : [Asus EN8600GT 512MB]("http://asus.com/product.aspx?P_ID=BWYIAFtkvwOAZ6UK") 
2 Monitors samtron 19" and samsung 17" on extended 1280x1024 (2560x1024) 

Printer : Epson dx4050 (dx4000 family)

Intro : My "baby" was getting sadder day by day with XP and got worse (a depression) with Windows 7 RC1. I am a "tuxer" since I first encounter MANDRAKE, a redhat distro, in some good old days. Tired of seeing my "baby" going some other way, where 60% of my processor power went to antivirus, antimalware, antispyware and so on, and to firewalls and as I was trying win7 facing the fact my "baby" was going to be a micro$oft zombie (sorry Balmer, no other way to call it !) I decided to go Ubuntu.

Installation: I first tried 9.04 x32 from a dvd and was pleased to see the installation process (I also tried Wubi) was fairly smooth. Then I when 9.10 x64 from a USB bootable (WOW !! nice feature !!).
When choosing a partition, the process was to not so fair. From what I read here most people have already or need to set a separate partition and most do not have it already so for me the options would be :
1- choose type of installation 
a) "/", swap
b) "/", "/home", swap
c) "/boot", "/", "/home", swap
D) choose your own
2 - get the space for it 
Notes:  The color bar should be proportional.
The optional partition manager should be it as it depics the system in a more intelligigle way  
3 - show what was chosen and ask al least 5 times if we are certain :)
    
Working : Everything is working ... and fast ... a "so fast" i was not use to.
The repositories and synaptic is a excelent idea for those who are "graphic" and for those like me that are attending the WA (Windows Anonimous) meetings. Joking !!! This software collections are marvelous and hassle free. 

Disks and Partitions : I have already understanding of the mount command that I had to refresh because of the many, many options. In "Places", all my drives appeared but then when going "FSTAB" things started to get somewhat confusing because of label mixup (I gparted and changed some to fit some needs). "Places" went nuts (doubled up) and found "Mtab" to have some disconnected entries, deleted all /dev related and restarted. Because of user priviledges, then found that (root alters root entries and user do not have write access to some /etc) root@nautilus did not match user@nautilus. The mount options "default,user, users" solve some of the problems.
NTFs-3g if awsome and the configuration tool is a dream come true :) - If the hard drive is alright all goes well but if it's starting to fail be aware (not ntfs-3g fault of course) so monitor closely ntfs drives/partitions .    

Setting a "/home" partition is also a good idea. In a different partition you can backup some of your system configuration files, data, vmware disks and so on.

Network : Easy to set in no time either using dhcp (default) from a router or modem or setting a static ip.
Internet is more secure than I ever had, firewall does not clog the system, can fully profit from having a broadband connection (thing I was not used to !!!) 
 
Sound : Everything went fine after setting up the 5.1 speakers. (Note to self: need to understand the ALSA and the others) Play all formats without trouble and without background interference like a trully multitask system.  
  
Graphics : After some missapps, (all my bad) and with Nvidia driver (keep up the good work !) my 2 screens are working flawlessly. Only be sure to restart as some settings need at least a session restart, and with the nvidia driver be sure when cool booting to have both monitor turned on.

Virtualbox : WOW ! I tried it in windows but did not harness the power that I get from it on ubuntu. And I have now the perfect windows (f*ck MS system restore!!) just install xp and your apps and tweaks then backup copy the vmware disk and you can system restore. It's not a game machine but you can not have it all. Now I can turn my partition XP professional into from game console (yes I can not stop playing games ... sorry!).
It's awsome to have ubuntu in one monitor and running a vboxed windows XP (windows 7 is lame and heavy!) for some apps that don't run in wine.     

Security system (read/write access) : Way simpler and, at first glance, way secure than the windows system. I can easily access from ubuntu to one of my "tight secure" ntfs partition. From Windows to access ext4 partitions I will try Ltools. Also nice to see it that web apps also do not have full system access, it is the biggest problem in windows, being IE6 worsen by IE7, both having more access to the system than a user !!

Printers : This seems to (still!) be the Aquilles heel of Linux, mostly because lack of support from manufacters. I contacted Epson to ask for support for at least one of my Epson printers and all I got a negative response, which I strongly protest. So the way is to sell my Epson printers (and sotp buying consumables) and go Brother that has some support.  
in the past, other printers made leave linux behind because of lack of support from OEM's, knowledge and time to learn, but now that is not the main attribut so...
Still In 9.10 it found a compatible printer driver that prints, yet the scanner lacks some of the features.

Graphics : Gimp is very powerful, and for movies there is almost everything (too a little pick at ubuntu studio). 

Games : It seems some games are being ported to linux, so that's good news so i can leave the "old windows xp game console" (hey it's better the xbox and it does not melt after a year !)
And playing freeciv makes me return to the old days ! 
If nvidia is on board what is the problem (and delay ) for harnessing it's gpu power ?

Keyboard and Mouse : All good and compatible. USB works like a charm, plug and unplug mouse and USB keyboard with not trouble. I even can use my full keyboard again as my model is listed !

Burning : Burns cds and dvds like a bushfire, without clogging the system !  

Conclusion : 
I have 80% pc power to use again; 
no crashes, freezzes or "the blues" (windows joke);
can use my whole memory (Me and my disks were seek of swapping !);
feel alot more secure in the internet (can even go to those "you have a virus sites");   
Multitasking is real ... not an advertising catch phrase !

---

### Post by jrweiss on 2009-11-30
> **jrweiss said:**
> Works fine:

Ubuntu 9.04
Lenovo T500 2081CTO laptop
4 GB PC3-8500
Intel C2D T9400 2.53 GHz
ATI Mobility Radeon 3650
Intel 5300AGN WiFi
Boot from Patriot XT 16 GB USB stick

Upgrade to Karmic Koala went without a hitch, too.

Only [non]issue is that the proprietary drivers for the ATI graphics still will not load.  Standard drivers work fine, though.

---

### Post by teward on 2009-11-30
[I][B][U]Laptop, running 9.04
[/U][/B][/I]
[I]Dell Latitude E6500 Laptop
Ubuntu 9.04 Jaunty Jackalope
Intel(R) Core(TM)2 Duo CPU T9550 @ 2.66GHz
RAM: 4GB, 2 DIMM (2GB x 2)
Intel A/G/N Wifi Card
Internal HDD: approx. 250GB
Video Card: nVidia Quadro NVS 160M 512MB

[/I]Everything works fine, 'cept for the desktop effects because I am forced to disable them by the programming software I use, which is incompatible with compiz.

---

### Post by OLDUSER on 2009-12-07
[B]Please Only List
1)Version Of Ubuntu 9.04 desktop x86 32 bit
2)Type Of Hardware[/B]
 
[B]Tower  Enermax Phoenix Midi-Tower, Black, Red LED.,eSATA,ATX, 25cm Side Fan (17db)
Power Supply  500Watt PowerSupply with 14cm FAN, ATX 2.2 ToughPower
Motherboard  Gigabyte EX58-UD3R, Intel X58 Express, DDR3,SATAII,1394,GLAN, Raid
CPU  Intel 4 Core i7-920 Nehalem, Quad-Core, 4.8GT/sec, 8MB, 45nm
Bloomfield, 2.66GHz, HT, SSE4.2, MMX
Memory  8182MB (8GB) DDR3-RAM, PC-10660, 1333MHz. (4x 2048MB)
Graphiccard  ATI R5770 (HD5770), 1024MB, HDTV-Out, 2xDVI, HDMI, GDDR5
Harddisc  1000GB (1x1000GB), SATA-II-300, 7200rpm/ 8.9ms/ 32MB
DVD-Recorder  24x DVDRW +/- R, +/-RW, LightScribe
Card-Reader  Apacer 22-in-1, USB 2.0
LAN-Card  
Gigabit LAN controllers 10/100/1000 MBit/s, Realtek 8111D
Special  External E-SATA Connector for External SATA Harddisc

3)Hardware Maker
4)Hardware Model[/B]

 
It's all good 
 
some problem with the installation of the graphiccard :D

---

### Post by OLDUSER on 2009-12-07
[B]Please Only List
1)Version Of Ubuntu 9.04 and 9.10 on same HD desktop x86 32 bit
2)Type Of Hardware[/B]
 
[B]Tower  Enermax Phoenix Midi-Tower, Black, Red LED.,eSATA,ATX, 25cm Side Fan (17db)
Power Supply  500Watt PowerSupply with 14cm FAN, ATX 2.2 ToughPower
Motherboard  Gigabyte EX58-UD3R, Intel X58 Express, DDR3,SATAII,1394,GLAN, Raid
CPU  Intel 4 Core i7-920 Nehalem, Quad-Core, 4.8GT/sec, 8MB, 45nm
Bloomfield, 2.66GHz, HT, SSE4.2, MMX
Memory  8182MB (8GB) DDR3-RAM, PC-10660, 1333MHz. (4x 2048MB)
Graphiccard  ATI R5770 (HD5770), 1024MB, HDTV-Out, 2xDVI, HDMI, GDDR5
Harddisc  1000GB (1x1000GB), SATA-II-300, 7200rpm/ 8.9ms/ 32MB
DVD-Recorder  24x DVDRW +/- R, +/-RW, LightScribe
Card-Reader  Apacer 22-in-1, USB 2.0
LAN-Card  
Gigabit LAN controllers 10/100/1000 MBit/s, Realtek 8111D
Special  External E-SATA Connector for External SATA Harddisc

3)Hardware Maker
4)Hardware Model[/B]

 
It's all good 
 
some problem with the installation of the graphiccard :D

---

### Post by steve19137 on 2009-12-07
I am running Ubuntu 9.10 from a Compaq Presario C551NR Notebook. It has a standard DVD-ROM drive, with CD-R/RW capabilities. It also has a built in Broadcom wireless card, but the version number escapes me. To make the wireless work properly, you must start with Ubuntu 8.10. This version has the drivers for the wireless card in the system already, and has the immediate ability to enable them after installation. If you go to 9.10 forst thing, you will be able to get the wireless drivers by using the update function in System --> Admin. --> Update Manager. This gives you the drivers, but when you enable them and restart, you discover that the network applet doesn't have the ability to connecto to a wireless network. So if you plan on having the latest and greatest version, start with 8.10. PM for more details if you want. Also, if you are planning on connecting to an Airport Extreme or Express, make sure that you obtain the HEX equivalent of you password, no matter the encryption. Otherwise the password will not register. Again, PM me for details.

---

### Post by Janeleaper on 2009-12-11
Ubuntu 9.10.

Logitech Webcam Pro 9000.

Works out of the box.

---

### Post by AntonJ on 2009-12-12
OS version: Ubuntu 9.10
Dell E6500 HW:
Only things is not working properly:
1) Fingerprint Reader
2) Nokia C-15 USB mobile broadband modem (internet stick)

---

### Post by mikeee99 on 2009-12-12
Sorry wrong forum

---

### Post by Carthorse on 2009-12-14
Ubuntu 9.10 (Dual boot, 32 bit and 64 bit)
Asrock N68-S M/B
On-board Intel/nvidia HD Audio
AMD Athlon64 x2 2.1GHz
DDR2 800Mhz 4Gb (2x2Gb: dual channel mode)
Sparkle Nvidia GS8400 512Mb PCIe
Generic OEM CD/DVD writer
Samsung SP1654 IDE HDD
O2 mobile broadband dongle
Generic (ie cheapie!) Keyboard and mouse, PS/2
Hyundai 19" widesceen lcd monitor @ 1440x900

All worked fine after clean installs.

---

### Post by arun181818 on 2009-12-15
Ubuntu 9.10

Palit **_[SIZE=2][COLOR=Red]Geforce 9400 GT[/COLOR][/SIZE]_** Super+ 1GB

Nvidia Proprietary drivers (version 185) installed from Hardware Drivers.

Compiz, Suspend and Hibernate all work like a charm.

Other system hardware:
Pentium D 820,
Motherboard with ATI Radeon Xpress200 Chipset,
1 GB system RAM

---

### Post by hfdragon on 2009-12-16
> **jrweiss said:**
> Works fine:

Ubuntu 9.04
Lenovo T500 2081CTO laptop
3 GB PC3-8500
Intel C2D T9400 2.53 GHz
ATI Mobility Radeon 3650
Intel 5300AGN WiFi
Boot from Patriot XT 16 GB USB stick
You don't have any problem with the 5300AGN wifi card ?
I have a few issues...

---

### Post by shortridge11 on 2009-12-16
Ubuntu 9.10
Laptop
Dell
Studio XPS 1340

Works great, applied recommended nVidia proprietary drivers with no problems.  Only issue is random wifi disconnect, running an Atheros card.

---

### Post by fivosz on 2009-12-16
Ubuntu 9.10 64bit

AMD Phenom II X4 955
MSI 785GM-E51
DDR3 1x2048 1333mhz
PixelView PlayTv Pro 2 (tv card)
Belkin F5D7001 Wireless G

Everything works perfect

---

### Post by kennethadammiller on 2009-12-17
Aspire 5920 (2 yrs old)
completely compatible except for one small caveat;
the touch buttons on the side don't work in ubuntu. ubuntu can tell when they are being used, but they are not used for the proper meanings they are given (play pause and stop do nothing, |<< and >>| scroll)

everything else works. the wireless, the touch pad, the keyboard. everything.

---

### Post by Kato4059 on 2009-12-17
This is for anyone that needs a cheap printer set-up. 
I have been successful with an Epson Colorstylus 740 in any 
Ubuntu ,since 8.04.
You just open CUPS and "add " printer,anl voila you can print. I wish 
that It was that easy for Multifunctions  to be enabled ,especially with 
the scanner side of them.
Kato4059

---

### Post by bubbabear on 2009-12-18
Ubuntu 9.04
Toshiba Satellite 1085-S402
Nvidia GeForce2 video card
 
96.43.14 and 96.43.13 video drivers.
 
While Ubuntu recognizes the video card and installs the default drivers, it gives you the option to install the 96.43.13 video drivers. When installing these drivers, you may get the computer to reboot properly in some cases, however in a few cases the screen was displaying a bright bar at the bottom of the screen. These drivers could be harmful to the computer as well as the screen in their default configuration and shouldn't be installed.

---

### Post by Rhythmdvl on 2009-12-18
I don't know if this is a good question for this forum/thread or it’d be better posted to Tom’s or Anandtech; please forgive me if this is this is in the wrong place. 

For absurdly unimportant and irrelevant reasons, I need to build a small Ubuntu file/web server — and I’m about to order in a couple hours. 

Requirements are absurdly small. There are only two or three of us in a home office (PCs and Macs), each working on simple documents and the occasional web page. Not a lot of traffic, and nothing more than file sharing and the occasional testing of a web page (all Internet-hosting is done off site; this machine won't ever go beyond the router). The rest of the network’s speed is Gigabit, so onboard LAN is important. I’ll be running it mostly headless, but onboard VGA will help setup and maintenance. I guess the only other thing to consider is that I’m going to be putting two 1.5 TB Seagate Barracuda drives in there in RAID 1. 

I have one machine now that I put together, based on an Asus P5KPL-CM. But it took just a bit of hoop-jumping to get it right (among other things, LAN drivers didn’t work out of the box). I can go through a fit of driver installs again, but I’m wondering if there is a simple and tested workhorse combination out there to make this as easy as possible (Linux noob, if that’s not clear). 

Thanks, 

Rhythm

---

### Post by joelw135 on 2009-12-18
I need a inexpensive Video card to fit a Dell E510 with an PCI Express 16 v1.0 slot. I want to use it in 9.10 Ubuntu. My ATI X300 SE freezes and has artifacts in 9.10 but works great in 9.04. What do you suggest for general purposes, not games.

---

### Post by terry@softreq.com on 2009-12-19
I've been using the Powercolor video cards (air cooled, no fan). 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814131144f](http://www.newegg.com/Product/Product.aspx?Item=N82E16814131144f)

It's PCIE 16 with 256 mb's of memory.  It has all three connectors, D-sub, DVI and HDMI! 

Runs cool, silent (no fan) and the graphics look good! 

I've done some moderate gaming and it holds up, so it will certainly handle desktop tasks and watching videos.

I'm using it right now, Ubuntu 9.10.

---

### Post by joelw135 on 2009-12-19
> **terry@softreq.com said:**
> I've been using the Powercolor video cards (air cooled, no fan). 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814131144f](http://www.newegg.com/Product/Product.aspx?Item=N82E16814131144f)

It's PCIE 16 with 256 mb's of memory.  It has all three connectors, D-sub, DVI and HDMI! 

Runs cool, silent (no fan) and the graphics look good! 

I've done some moderate gaming and it holds up, so it will certainly handle desktop tasks and watching videos.

I'm using it right now, Ubuntu 9.10.

Can you please be a little more specific as there are a few withe 256 mb memory, but different clock speeds. Thanks.

---

### Post by Carthorse on 2009-12-20
Trust basic wireless keyboard and mouse, Model 16593. Not the best quality kit (no LED's, media buttons) but it's working fine. Had to enable USB Legacy in BIOS (using old k/b) for it to work at grub/boot. No issues with Legacy USB (YET!). I'm now single booting into Ubuntu 9.10 x64 so it's not really an issue for me if I have to disable it at some point.

---

### Post by Romualdou on 2009-12-20
System : Laptop Samsung R522
Ubuntu : 9.10 first 64 bits, finally downgraded to 32 bits

I will look to complete this post regularly when I have more experience with this PC. 

Setup : with install CDROM, install quite straightforward, but I had to manually do the partition, the proposal was to remove completely the system. I wanted to keep a dual boot.

WLAN : could not get the Realtek 8192E integrated WIFI to work with 64bits. Issue seems to get a 64bits XP driver to use with ndiswrapper. 
After full reinstall of the 32bits version, network works fine with ndiswrapper. (Also not out of the box...)

Touchpad works fine, including the scroll side. 

Fn- keys : 
Sound on/off and volume ok
Brightness : nok, will have to figure out how to set them up. (Added brightness applet to the Panel, it works fine: Did not have time to try to map to Fn Keys)
Screen on/off : nok
Battery status : nok
Euro : nok (anyway, I have no clue what this key should be good for as AltGr + E work fines for &#8364; symbol)
Touchpad on/off : ok
VerNum : ok
Wifi on  off : nok - swithcing wifi on / off via software also have no impact on the wifi status led.
Energy / performance modus : nok

Video : ATI Radeon HD4650. 
Working ok, I guess with the fglrx driver from ubuntu. But no 3D, fglrxgears does not run. 
Cannot setup desktop effects, I guess this is also due to the fglrx driver. 
The proprietary driver option was not proposed first, but after internet connection, I can select it.
fglrx then works, with 1922 fps. Desktop effects are also available.

Webcam 
I tryed quickly with Cheese and the webcam works fine out of the box. No futher testing with skype or any similar application.
Fine means as fine as on Windows, as I find that the framerate of the cam is quite low...

USB
- Integrated card reader
- USB Memory stick
This works out of the box, but for some reason after a while running, newly plugged device will not be detected. It seems that if the computer stays on standby for a while, it will work again when coming back from idle. Strange.

---

### Post by dimas11 on 2009-12-21
ubuntu 9
hp photosmart 7550

---

### Post by jmate24 on 2009-12-21
Ubuntu 9.10

lenovo y510, just works, installed virtualbox from virtualbox.org
and updated graphics driver from launchpad using jaunty graphics how-to but changing it to karmic in the software sources.

1.86GHz Processor EM64T
160GB HDD (but upgraded to 400GB)
2GB RAM (but upgraded it to 4GB)
LAN and Modem Work (modem needs proprietary drivers)
Wi-Fi works
MMC MS MS pro SD SD pro xD works
Not Sure if Card reader works
fire wire works with installation of ffado-dbus and ffado-tools
VGA and TV out work
sound works
touch works Mute Play/Pause, Stop, FF, RV, orange volume and round orange switch. not sure if mixer buttons work.
all function buttons work
touchpad works though it does not lock when you type.
Video works with compiz with a little configuring.
usb works
Mic works

jmate24--:)

---

### Post by JimInLakeland on 2009-12-21
Ubuntu 9.10 Karmic Koala on a Dell Inspiron 530

[LIST]
[*]Intel Core 2 Quad Q6600 @ 2.40 Ghz
[*]4 GB RAM
[*]nVidia GeForce 8500 GT with 1GB vRAM
[*]Dell 1320c Color Laser Printer
[*]Microsoft Natural Ergonomic Keyboard 4000
[*]Logitech LX7 Wireless Mouse
[*]Logitech Precision Gamepad
[*]Saitek AV8R-01 Joystick
[*]Samsung SyncMaster 192N Monitor at 1280 x 1024
[/LIST]

---

### Post by iSephy on 2009-12-26
Ubuntu 9.10 Karmic Koala
USB Wireless Keyboard/Mouse (Integrated)
Microsoft
Microsoft Wireless MultiMedia Keyboard 1.1

---

### Post by jpchheda on 2009-12-26
Ubuntu 9.10 Karmic Koala on a HP DV9010TX


Plz help me find drivers for Mobile Intel 945GM chipset express family.

Also I am unable to use my Western Digital My passport essential 500Gb.

---

### Post by fanndian on 2009-12-30
[B]Please Only List
1)Version Of Ubuntu: 9.10
2)Type Of Hardware: notebook
3)Hardware Maker: lenovo
4)Hardware Model: t60p
[/B]

---

### Post by Richard9795 on 2009-12-31
Ubuntu 9.10 Karmic on a Gateway NV78:
What Works (Hardware) :
Video Card: Intel Corporation Mobile 4 Series (HD playback works fine)
Processor: Intel Core 2 Duo Processor T6600
Memory: 4GB DDR3
Touch Sensor Buttons (Vol. up, down, mute; Disable Touchpad and wireless) 2 don't work (Backup, and to assign a launcher)
Function Keys Work

As a matter of fact, everything works.

---

### Post by l-x-l on 2010-01-09
Ubuntu 9.10 Karmic running well on a Dell Inspiron E1705:

Audio: Card Intel 82801G (ICH7 Family) High Definition Audio Controller driver HDA Intel

CPU:   Dual core Intel Core2 T7200 (SMP)

GPU:  nVidia GeForce Go 7900 GS

Network:   Card-1 Broadcom BCM4401-B0 100Base-TX driver b44 v: 2.0
           Card-2 Intel PRO/Wireless 4965 AG or AGN [Kedron] Network Connection driver iwlagn v: 1.3.27k

Disks:     SAMSUNG HM160JI 160.0GB

---

### Post by ret3 on 2010-01-10
I have a NV7802u and can't get the SD card reader to work; did it "just work" for you, or is there a trick to it?

---

### Post by Sparky101 on 2010-01-14
Running Jaunty 9,04 in a Thinkpad T21. Works perfectly except the HP 400 Deskjet printer won't print, just sits there lights flashing. Driver set up is good. Print command is received, but nothing happens. Compatibility list says the 400 works with hplis.
What am I missing?

---

### Post by SilverBug on 2010-01-14
Hi,

I am using a Lenovo X60s laptop with Ubuntu 9.10 "out of the box" and every is working perfectly.

:D

---

### Post by milam on 2010-01-15
Ubuntu NBR 9.10 Karmic Koala

Acer Aspire One AO532h
Intel® Atom™ Processor N450 (1.66GHz, 512KB L2 cache, 667MHz FSB)
10.1" WSVGA Acer CrystalBrite™ LED-backlit Display
Mobile Intel® NM10 Express Chipset
Integrated Intel® Graphics Media Accelerator 3150
1024MB DDR2 667MHz Memory
160GB 5400RPM SATA Hard Drive

Everything pretty much worked out of the box off a clean Live CD install, with the following exceptions. Multi-gesture touchpad; pinch to zoom, two finger scrolling does not appear to work. Side scrolling, tap to click all work, have not attempted to get pinch to zoom working. Disable touchpad while typing, although enabled in the touchpad preferences, does not appear to work correctly. 

Wireless, using Atheros ath9k driver, while working was a bit flaky; poor signal strength, somewhat frequent disconnects/reconnects, having to resubmit WPA passkey, &c. Installing karmic back modules, as described elsewhere in these forums, corrected the issue. Signal strength now very good, no disconnects.

All Fn keys I have attempted to use work, including screen brightness, volume control, sleep, and mute. Suspend and resume on lid closing and opening works as intended.

---

### Post by coldraven on 2010-01-17
Ubuntu 9.10 64bit
Laptop
Compaq
6715b

All working out of the box except the fingerprint reader. It is not found with lshw, see:

[https://bugs.launchpad.net/ubuntu/+source/lshw/+bug/315921](https://bugs.launchpad.net/ubuntu/+source/lshw/+bug/315921)

I have not tried installing the LightScribe software.

---

### Post by Silent Warrior on 2010-01-18
**Ubuntu:** 9.10 Karmic/Mint 8 Helena
**Hardware:** Printer: Epson Stylus S20

Works out of the box, using CUPS.

(Maybe this is a no-brainer, but I searched the topic and found no reference to it.)

---

### Post by Appl3 on 2010-01-18
Hi, there is my pc specifications. Is it compatible for linux ubuntu OS?
 
it is a Compaq preasario SR1705UK, but i have added new hardware in it...
 
4GB of RAM
Nvidia GeForce 7900GTX
Intel Pentium D 330 3.00GHz two cores
Motherboard HP "Asterrope-GL8E"
Realtek HD audio (Azalia)
Preasario SR1705UK ports

---

### Post by manu2manu on 2010-01-19
hi this mani,
im faceing a problem with Ubuntu OS in MSI Motherboard 945GZM6 VER 5.0. THE problem is Installation is completed well and after installation the system is gets hang. kindly sugess me whether this board is compatible for ubuntu. the system configuration is 3.4Ghz Intel Processor, 512 MB RAM, 80 gb sata hdd. Kindly sugess me what to do
 
Regards
Mani
(email- [email]manik10_1981@yahoo.co.in[/email])

---

### Post by austinjl on 2010-01-23
I was pleasantly surprised with this purchase since I neglected to check out its compatibility beforehand. I am not the main user on this machine. So I don't have all the details.

Everything worked, but I haven't tried the HDMI output. There are only threes things that needed a little adjustment. The rest is straight out of the standard Karmic installation.

***08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)***
NetworkManager didn't like it at all. I switched to wicd, and it worked okay for a week, even though it was kind of slow for an undetermined reason. All of the sudden, it stopped working completely (suspending may be to blame). So I switched to MadWifi (v0.9.4), and it's been working perfectly.

***01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]***
The default install was usable, but I wanted full 3D. Switching to the restricted ATI drivers under System -> Admin -> Hardware Drivers worked fine.

***00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)***
Default installed worked fine, except the microphone stopped inputting after 10-20 seconds. I had to reboot to get it to work again. I did two things to fix this, and I am not sure if one would have done it without the other.
[LIST]
[*] First I installed the linux-backports-modules-alsa-2.6.31-17-generic package
[*] Second I commented out "options snd-hda-intel power_save=10 power_save_controller=N" in /etc/modprobe.d/alsa-base.conf
[/LIST]

---

### Post by trevorlewis on 2010-01-25
Release: 9.10
Hardware Type: Desktop
Manufacturer: Gateway
Model: GT5086b

Installed OK from Live CD.

---

### Post by MaindotC on 2010-01-25
The configuration in my signature works.  The only caveat is that I can't seem to get the onboard mic to work.  The workaround I have for this is I use the C-Media usb:
```

Bus 005 Device 002: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter

```
Audio and mic works great :D

---

### Post by jpowers1 on 2010-01-26
Shuttle XPC
Ubuntu 10.04
AMD Athlon 64 X2 4000+
2GB Ram
ATI Radeon X1550 512MB
ASUS DVD burner

It all works well except for the optical drive, but that was $25 in the first place;)

---

### Post by vivjo on 2010-01-28
:popcorn:
Acer Aspire 4710z  
1.86 Ghz 533 Mhz FSB (Pentium Dual Core)
1GB Ram(512 * 2) @667 Mhz
160GB HDD (hitachi)
BroadCom Bluetooth(2035)
Atheros Wifi
Ubuntu 9.10

BroadCom Ehternet Controller

All the keys are working fine expect bluetooth key as it generating two events ,however the switch is working fine

Regards
Viv

---

### Post by sbrattonuk on 2010-02-05
[B]1)Version Of Ubuntu   : Mythbuntu 9.10
2)Type Of Hardware : dual usb stick tv tuner 
3)Hardware Maker : Peak (Kworld copy)
4)Hardware Model dual tuner usb stick 399 model


USB ID :   1b80:e400


Needed to upgrade standard 9.10 Kernel to 2.6.32 using the ubuntu kernel  .deb files
& copy firmware  af9015.fw version 4.95  to /lib/firmware

kernel headers and image found in ubuntu kernel repos.
firmware found on linuxtv.org

Peak tuner is a copy of the Kworld U399 model

As I'm  inexperienced with ubuntu and mythtv it took me a lot of working out but I hope this helps someone

Steven
[/B]

---

### Post by Guanglin.Du on 2010-02-05
(1) Ubuntu Version: 9.10, Karmic
(2) Dell Dimension E521 (bought from Dell at the end of 2006)
(3) CPU: AMD 64 3200+ 1GMHz
(4) Display card: mother-board integrated nVidia GeForce 6150 LE
(5) Audio card: Sound Blaster Montogomery 3, also integrated
(6) Monitor: Dell E177FPc (17", with an analog interface only)
Works excellently after solving the display car driver problem (See below).

**Linux distributions used in history on this PC:**
1. Redflag Linux 5 & 6
2. Xubuntu 8.04, Xubuntu 8.10, Ubuntu 9.04
All worked fine.

**Problem after installing Ubuntu 9.10**: ”cannot display this video mode“ problem with Ubuntu 9.10
Problem Description:
After the basic installation and update (sudo apt-get update), from System -> Administration -> Hardware Drivers, there are 3 versions of the proprietary display card drivers: 96, 173, 185, among which version 185 is labeled "[Recommended]". However, using this driver will cause the ”cannot display this video mode“ problem. (There is also another line of text below ”cannot display this video mode“: "optimum resolution 1280x1024 60Hz".)

**Solution**:
Install version 96 of the display card driver. Both 173 and 185 will bring about the problem just above mentioned.
Use display card driver vesa to start X to modify X configuration with VI if the problem occurs.Only on X can I install version 76. Do not know how to install it under console. If you installed version driver version 173 or 185 and cannot start X, switch to the console mode (Ctrl + Alt + F1, or F2, or, ..., F6), edit /etc/X11/xorg.conf,

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    ...
EndSection

Comment out this line:
   # Driver         "nvidia"

Add a new line:
   Driver         "vesa"

(vesa is a pseudo-driver which makes it sure that X window starts correctly though the resolution is not high.)
[B]
Problem unsolved[/B]: A highly possible mother-board related defect with my PC
However, I'm sure my this PC has a mother-board related defect , which causes the system freeze once or twice a day, several days or one week. I've excluded the possible memory problem by replacing it with several other brand memory chips, but the problem remains all the way from Redflag Linux, Xubuntu and Ubuntu.

---

### Post by Silent Warrior on 2010-02-05
**Ubuntu:** 9.10 Karmic Koala/Mint 8 Helena
While not installed, 10.04 Lucid Lynx runs just fine from the LiveCD - there was no indications that anything would NOT work.
**Laptop:** Toshiba Satellite Pro L300-1CZ
**Specs:**
*CPU* - Intel Core2 Duo T3200 2GHz
*RAM* - Upgraded from 1 to 3 Gb, Samsung
*GPU* - Intel X4500 HD
*Sound* - Intel HD Audio controller (module used: snd-hda-intel)
*BIOS* - inSyde H2O 1.50
*Ethernet* - Wired: Realtek 8101SE & Wireless: Realtek 8187B

What works: Everything.
Untested: Standby/Hibernate (did NOT work with Mint 7, based on 9.04)

HOWEVER: Exercise caution with kernel updates. I wasn't too careful, installed just about every extra kernel-package (modules-backport, lbm-headers, modules-alsa-backports, etc) and found that wireless went down with kernel versions 2.6.31-15 through -17 - -14 and -19 works just fine. This seems to be related to either backported modules and/or libc-updates. (I'll update this post if I find out in more detail.)

---

### Post by Psumi on 2010-02-06
People should submit all their hardware to this website: [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

that way ubuntu.com can link to that website or this thread can and we then don't have to keep replying here.

---

### Post by jjjjeremy on 2010-02-20
Ubuntu 9.10
Bluetooth Dongle - USB
Unknown maker
Unknown model

I bought this bluetooth dongle on Ebay for less than three dollars from Hong Kong, and it words perfectly. I just wanted to post its compatibility, because I would have liked to had some assurance before I made the purchase. I'm attaching a picture to compare to ebay pictures. There are many sellers selling this unnamed product.

- jjjjeremy

---

### Post by wandalalakers on 2010-02-21
Kubuntu: 8.04
Laptop: Gateway M305CRV
Specs:
CPU - Intel Pentium 4 M GHz
RAM - 512mb
GPU - Intel 852MG
Sound - AC97
BIOS - Phoenix 38.01.07
Ethernet - Wired: Intel 82801DB Pro/100 VE
Note: Laptop would only restart when trying to shutdown.
This was fixed after bios 38.01.07 was installed.
I also initially installed a remastersys 8.04.4 image but screensavers never worked even though I had all the correct programs installed.
I had to install Kubuntu 8.04 from scratch in order to get the video and screensavers to work properly.

---

### Post by buzzmandt on 2010-02-21
**OS** kubuntu lucid development branch 64bit
**Laptop** Compaq CQ60-615DX Notebook
**CPU** Intel Celeron 2.2ghz
**Ram** 2Gig 
**GPU** Intel express series 4 mobile
**Sound** Intel Corporation 82801I (ICH9 Family) HD Audio Controller
**Wired Ethernet** Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E
**Wireless** Atheros Communications Inc. AR9285 Wireless Network

Everything "just works".

---

### Post by kyleabaker on 2010-02-24
1)Version Of Ubuntu
Ubuntu 10.04 x86_64

2)Type Of Hardware
Webcam and microphone (usb)

3)Hardware Maker
Microsoft

4)Hardware Model
LifeCam VX-1000

Details:
LifeCam VX-1000 video works out of the box in Ubuntu 10.04 x86_64, but the builtin mic is not functioning at all (and I'm unable to find a solution other than using a separate mic).

---

### Post by slevin_kelvera on 2010-02-24
First post, oh boy.  

Ubuntu 9.10 32 bit
Motherboard: Intel D945GCF
CPU: Intel Duo Core E2180 @ 2.00GHz
Ram: 3GB DIMM DDR2 Synchronous 667 MHz (1.5 ns)
Video: Nvidia  G96 [GeForce 9400 GT]
HDD: Seagate 1TB ST31000528AS ATA
Wireless: Zonenet [FONT=Arial][COLOR=#000000]ZEW1605 [/COLOR][/FONT][FONT=Arial]802.11g Wireless 54Mbps PCI Adapter[/FONT][FONT=Arial][COLOR=#000000]  [/COLOR][/FONT]
Monitor: Sony Bravia 26 inch KDL-26M4000 

I just now discovered my CPU was a 64 bit.  What's it been, 2 years since I got it?
No major issues on the software side, have compiz fusion installed and working nicely. Am dual-booting with Windows 7 Ultimate.

---

### Post by pizza-is-good on 2010-02-25
1) Ubuntu 9.10 Karmic Koala 32bit
2) Presentation Remote
3) Made by Keyspan
4) Presentation Remote Pro (**[B]PR-PRO3)**[/B]

Works flawlessly in Ubuntu, even if only certified for Windows and Mac.
The forward and backward buttons work with no problem. So does the volume up and down keys. F5 works as desired, as does the black screen button.
There is no problems with the mouse nor any of the mouse keys.

Also, as a little review
The remote is amazing. Powerful laser pointer, and amazing quality. Definitely recommend it.

---

### Post by pingu1 on 2010-03-01
1)Version Of Ubuntu
Ubuntu 9.10

2)Type Of Hardware
Wireless mouse (laser)

3)Hardware Maker
Logitech

4)Hardware Model
M 505

Details:
Works right out of the box. 
Just plug it in. Scroller works like a charm,
and the mouse has very good sensibility, and supposedly you can
use it on a glass table.... if the glass is a certain thickness.
Very pleased.

---

### Post by Trinity33 on 2010-03-03
[B][SIZE=1] 
OS                               Karmic Koala 9.10 86x32 

Processor                  Intel® Core™2 Quad Processor Q9000 - 2.0 GHz - 1066 MHz FSB - 6 MB L2 cache

DDR2                          4 GB
Graphics card           ATI Radeon™ HD 4850 with 512 MB dedicated video memory
Screen type              LCD widescreen
Screen resolution    1440 x 900 pixels
Screen size                17"
Screen features       16:9 format
Hard drive                  500 GB
Optical disk drive     DVD±RW
Memory card reader     Yes
USB                              3 x USB 2.0 ports 1 x USB/eSATA combo port
FireWire                      1 FireWire port
Modem/Ethernet      1 x RJ-45 Ethernet 1 x RJ-11 modem port
Wi-Fi                             Yes  Atheros 5007ag or Zydas 1211rw
Bluetooth                    Yes
Video interface          HDMI, VGA
Audio interface          Headphone and microphone ports
TV output                    HDMi socket

Sound                           Intel ACL1200 and ATI hd40x0 Hdmi Built-in 4 speakers and  subwoofer Realtek HD audio

Webcam                     Yes

After few tweaks (difficult to get something to work if u are new to Linux) every component inside this laptop is working perfect. {I tested also lucid and maybe cos is alpha was crashing a lot (high cpu usage, single application stealing whole ram, graphic problems, sound problems, bottom and top bar sometimes disappear, screen freeze etc)} thats why i will rather stay with karmic.[/SIZE]
[/B]

---

### Post by zeeshanhasan on 2010-03-05
Ubuntu 9.10 AMD64
Acer Ferrari One laptop
Works perfectly.

---

### Post by burner1 on 2010-03-06
ubuntu-9.10-netbook-remix-i386

Compaq mini 110c Netbook

Intel atom N270 - 1gig - 160g HDD

Everything but the wireless (broadcom) worked on install. I downloaded the proprietry driver for the wireless and that now works ok.

I installed via the live usb option, ran Gparted to repartition my hdd that had win 7 on already and then the install of Ubuntu for dual boot.

---

### Post by jackhe22 on 2010-03-10
All Of:
Compaq Presario R3000 (Laptop).

Wireless also working:
Belkin Wireless G Notebook Network Card. (G, 802.11g)

Sorry if that's a little vague but this was also on it:
Part # F5D7010

---

Ubuntu 9.10 (Wubi) No Updates Installed

---

### Post by AlexZaim on 2010-03-13
Toshiba T135 S1309 with 9.10 works fine!

There are some issues but they are fixable:
Brightness > 100% fixable
Wifi - works great! But some ppl say that on battery it tends to lessen the signal. That's fixable too, but have no 100% cure yet).
Mic - some said that they made it work. I can't.

---

### Post by paulnewall on 2010-03-13
Kodak ESP 5250 AiO printer.
There is a cups driver at
[http://sourceforge.net/projects/cupsdriverkodak/](http://sourceforge.net/projects/cupsdriverkodak/)
It has not been tested much, but its printing OK with ubuntu 9.10

---

### Post by rcayea on 2010-03-16
1)Version Of Ubuntu: 9.10

2)Type Of Hardware: 
1) Router
2) PCI-Express Wireless Adapter

3)Hardware Maker
1)Linksys
2)Asus

4)Hardware Model
1)Router WRT160N0
2) Wireless Adapter, PCE-N13 PCI-Express 

Everything works without any configuration on my part, except the standard password setup with the router and such. The Asus wireless adapter is AWESOME! I am downstairs from where the router is and I get 100% signal strength!

---

### Post by ManyuX95 on 2010-03-16
OS version: Ubuntu 9.10 karmic koala
Mobo Brand: ASUS
Model: P5KPL-AM SE
I think it is V1.0
Video Card: EVGA 9400 GT 1GB
HDD: Seagate 80 GB 7200 RPM
Processor: Intel Dual-Core E5200}

Everything came OOB, I just had to install the Nvidia drivers, only that. ;)
Hope this helps, and Im sorry if I added useless information

---

### Post by Chris Musampa on 2010-03-20
_Asus K70IO laptop_
Intel Core 2 Duo T6500 / 2.1 GHz
4 GB DDR2 SDRAM - 800 MHz
320 GB - 5400 rpm Hard Drive
DVD±RW (±R DL) / DVD-RAM
SD Memory Card, Memory Stick, MultiMediaCard
Display Type 17.3" TFT, Max Resolution 1600 x 900
Graphics NVIDIA GeForce GT 120M, Video Memory 1 GB
Sound card SRS Premium Sound, High Definition Audio, Altec Lansing speakers, Audio Input Microphone
Camera Type Integrated, Sensor Resolution	1.3 Megapixel
Data Link Protocol	Ethernet, Fast Ethernet, Gigabit Ethernet, IEEE 802.11b, IEEE 802.11g, IEEE 802.11n

Pretty much everything works out of the box with Kubuntu 9.10

Only thing I've noticed doesn't seem to work is the WIFI LED (the hotkey works to enable/disable, just the light always stays on).  
The camera is mounted upside down, I can't remember the fix but found it through a quick google.
The (Elantec) touchpad is incorrectly detected (as a Logitech mouse if I remember right) but all functions including 2 finger scrolling and 3 finger tap (for right click) work correctly.

All hotkeys work, hibernate/suspend/resume all work, Atheros wirless (haven't tested 'n' as I only have a 'g' router) is rock solid anywhere in my house.

I haven't tested the card reader or speaker out/mic in sockets.

---

### Post by Jirinovak on 2010-03-20
[FONT=Arial][SIZE=2][FONT=Arial][SIZE=2]Somebody gave me old Compaq Pentium3-500 GHz, with 256mb Ram, 10 GB hard drive. With help from friend we converted it into Ubuntu 8.04. It has been amazingly stable for almost 2 years, just doing updates. . I love it . . Even my wife loves it, . . . never ever a box with a message [SIZE=1]"you have committed illegal operation, your program will shut down".[/SIZE]
 
Then I converted for my fellow teacher Del Desktop with Intel 2.67 GHz (single core), 500 MB Ram. It works great on Ubuntu 8.04 as well . . :)
[/SIZE][/FONT]
[/SIZE][/FONT]

---

### Post by sixdrift on 2010-03-23
I bought the HP dv7-1245dx as a refurb (yes I know its reviews say it sucks) and I dual-booted it with Ubuntu 9.04 on it the first day I had it. Everything works out of the box with the exception of the 802.11 on/off button (software control works fine). This has been my 64-bit build machine for a few months now.

Specs:

HP dv7-1245dx
AMD Turion X2 Dual-Core Mobile RM-72 @ 2.1 GHz
4 GB RAM
300 GB Hard Drive
Radeon HD 3200 graphics
Realtek RTL8101E/RTK8102E fast ethernet
Atheros AR2425 802.11 wireless chipset

---

### Post by n1co on 2010-03-29
Hey  every1! this is my first post!!!!
So, i have a desktop pc with

ati - radeon 9550 - semi compatible - no 3d accelaration
ECS motherboard - socket 478 - p4s6a/dx+ - compatible.
creative - sound blaster se - semi compatible...(no microphone)

Thats it! :D

---

### Post by lizzibet on 2010-03-29
> **bodcod said:**
> 
Nvidia 6150 on board gpu on first install ran with visa driver

Bodcod


How'd you load a vesa driver?

---

### Post by cwilson85 on 2010-03-30
okay I'm new to the  forums.  

I have a laptop this is the specs...

Toshiba satellite l505d-s5965
aamd athlon dual core ql-65
3gb sd ram , 250gb hdd
15.6hd trubrite wide screen 
dvd super multi with flash label.. 

I dunno if either of the burners work,  but everything else seems to pan out
EXCEPT. well I guess I should put this.  
I'm a windows geek,  I've always been  keen on the windows fronteer,  my friend  recommened I try out ubuntu because I hate vista,  this came with vista, I put win 7 on it loved it until  it went  ungenuine,  so here I am I have ubuntu  9.10 

I put it on my acer netbook as well and it works great minus the sound.  

The sound and everything works on here except for my fn key fuctions,  but the  normal  functions work and my touch pad ... 

which  my touch pad is most important to me,  as I have kids, and find myself with in  many  play places and parks using wifi, i wanna be wireless, not have to carry a mouse with me.  

I was wondering if anyone knew how to  get the touch pad work,  or be able to  talk me threw it or what not,  I am willing  to  give out my messenger name, It ried to get on IRC but i can't find where to make a lgo in,  to get on irc,  so i gave that up i'm hopeing for help on here.  then I also  have one more issue lol 

my battery  life is like so much less than what it was before it's abrand new  battery i replaced it because  I figured it went bad it happenes,  and I know it's not the best battery out there but I use to get a good 3-4 hours on it  with just typeing  as i"m  writing a book,  and now i'm lucky to pull and hour if that out of the thing.  toshiba said it's a driver  however they do not support ubuntu  so they wont help me lmao  warrenty or not.  so ubuntu  u voided my warrenty lol but thats okay i still love you thus far! I'd love u more with  longer battery life and a touch pad, I could care less about the rest of  the  fn functions i can do those all threw your system  manually which is okay with me :)

---

### Post by kmrs75 on 2010-04-05
Graphtec Vinyl cutter - works great ubuntu 9.10

---

### Post by donovan1983 on 2010-04-15
Kubuntu 10.4 Beta 2
Motherboard
MSI
785GTM-E45

Sound and onboard ethernet work right away. Graphics fully usable in 2D mode right away (using default open-source driver), and installing the FGLRX driver brings fully-functional 3D acceleration for the integrated ATI Radeon HD 4200 chip. No glitches or issues at all that I have noticed. Hard to ask for a more painless board to use in Ubuntu.

Edit: there seems to be a bug in power management in the 2.6.32 kernels used in Lucid which prevents this machine from hibernating or suspending (it will hang on both) and will not allow the machine to power off when shutdown. Works fine from the Hardy live CD though.

---

### Post by Vega on 2010-04-15
ASUS PCE-N13 IEEE 802.11b/g/n PCI Express Wireless Adapter

Best 802.11 b/g/n wireless adapter you can use on Ubuntu/Mint/Fedora/and Arch with strong signal strength.

---

### Post by ReallNeurotiq on 2010-04-21
ATI 4850 Radeon - flawless
M-Audio 192 Delta - flawless

if i think of more i'll add to this.

---

### Post by northking on 2010-04-21
I am a newcomer to Ubuntu, so please bear with me. I know the following is a lot of data. Note the RAM, GPU, HiDef display, second hard drive, optical drives, and OS are not what shipped with the desktop. I initially installed a second hard drive, downloaded the Ubuntu v9.10 ISO, burned a CD, booted from the CD and installed Ubuntu on the second hard drive. The following are issues I had to resolve. I did not have to repeat these when I upgraded to v10.4 LTS beta2. 

1. Commercial DVDs would not play. I assume this is true for all new installs due to license issues. I followed the instructions in the Ubuntu Help Center (from the top toolbar) for playing DVDs and now both optical drives work.

2. No sound. I used System/Administration/Sound, tab Hardware to setup for my configuration. The STAC 92xx series has many options for analog and digital outputs, so of course setup depends on attached sound hardware.

3. The could not configure my dual monitors correctly. I used System/Administration/Hardware Drivers to find and install the Nvidia proprietary driver. This also installed System/Administration/NVIDIA X Server Settings, which worked. However, when I selected the button Save to X Configuration File I got a parsing error for the file /etc/X11/xorg.conf. Every time I logged in I had to reset the monitor configuration. I believed this was a write permission problem as it never asked for a password. With help from the forum I fixed it as follows:

 -Made a backup of the configuration file by pressing Alt+F2 and entering "sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup". I found out X is a capital letter the hard way.

 -Next Alt+F2 and entered "gksudo nvidia-settings" and  made my choices. In the left panel selected X Server Display Configuration, in the right panel selected the button Save to X Configuration File, which now worked since I had write permission for root. Voila! 

BOOTUP - GRUB Loading
 -UBUNTU - Ubuntu v10.4 LTS beta2 (default)
		GRUB v1.98
		Linux 2.6.32-21-generic
		GNOME v2.30.0
 -WINDOWS - Microsoft Windows 7 Premium 64-bit

COMPUTER - Desktop (Dell XPS 420)
 -CPU - Intel Core2 Quad, 3.2 GHz (Intel Q6600)
 -GPU - Nvidia GeForce 9600 GSO, 768 MB, PCI-E, v195 driver (XFX PV-T960-SDFH)
		Display, HiDef wide flat panel, DVI (Dell E248WFP)	
		Display, wide flat panel, DVI (Dell E207WFP) 
 -RAM - 8 GB DDR2, 800 MHz dual channel (four PC2-6400 DIMM)
 -DRIVE - 320 GB, SATA (Seagate ST3320620AS)
		/dev/sda1 System Reserved
		/dev/sda2 Windows
 -DRIVE - 250 GB, SATA (Seagate ST3250820AS)
		/dev/sdb1 Linux
		/dev/sdb2 Extended
		/dev/sdb5 Swap
 -OPTICAL - BD-RE DL/LightScribe, SATA (LG GGW-H20L)
 -OPTICAL - BD-ROM/DVD-RW DL, SATA (Pioneer BD-202)
 -AUDIO - HiDef (Sigmatel STAC 92xx)
		2 channel analog internal
		5.1 channel analog external 
 -NETWORK - Ethernet 10/100/1000 (Intel 82566DC-2)

---

### Post by mechanizedmedic on 2010-04-21
[SIZE=1]**Ubuntu 9.10**[/SIZE]
[SIZE=1]Biostar A770E3 v6.0[/SIZE]
[SIZE=1]AMD Athlon II X3 435 (OC'd to 3.2)[/SIZE]
[SIZE=1]Patriot DDR3 1333 (PN: [/SIZE][FONT=Verdana,Arial,Helvetica][SIZE=1]PDC32G1333ELK)[/SIZE][/FONT]
[SIZE=1][FONT=Verdana,Arial,Helvetica]Patriot PS-100 32GB SSD[/FONT][/SIZE]
[SIZE=1][FONT=Verdana,Arial,Helvetica]Asus DRW-24B1ST DVD Multi-Drive[/FONT][/SIZE]
[SIZE=1][FONT=Verdana,Arial,Helvetica]BFG GeForce 210 (nvidia driver works great!)[/FONT][/SIZE]
 
[SIZE=1][FONT=Verdana,Arial,Helvetica]Everything works as advertised. The CPU scaling was causing some lag so i disabled it. system boots in 17 seconds and reboots in 28! i had heard so many bad things about SSDs but now that i have one i'm never going back. i bought a cheapy one and it still kicks the crap out of any HDD. [/FONT][/SIZE]

---

### Post by Stray Wolf on 2010-04-21
-Computer-
Processor        : 4x AMD Phenom(tm) 9500 Quad-Core Processor
Memory        : 3090MB (974MB used)
Operating System        : Ubuntu 9.10
User Name        : XXXXXX (XXXXXX)
Date/Time        : Wed 21 Apr 2010 07:45:14 PM CDT
-Display-
Resolution        : 1024x768 pixels
OpenGL Renderer        : GeForce 8500 GT/PCI/SSE2
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA NVidia
-Input Devices-
 Power Button
 Power Button
 Macintosh mouse button emulation
 Microsft Microsoft Wireless Desktop Receiver 3.1
 Microsft Microsoft Wireless Desktop Receiver 3.1
 HDA Digital PCBeep
-Printers-
No printers found
-SCSI Disks-
ATA SAMSUNG HD320KJ
TSSTcorp CDDVDW TS-H653N
ATA SAMSUNG HD320KJ
Generic- Compact Flash
Generic- SM/xD-Picture
Generic- SD/MMC
Generic- MS/MS-Pro
WD 3200BEV External

The printer is recognized when it's on -  Epson Stylus CX7800.  It was instantly recognized and properly labelled.  I'm itching to use the TV Card but don't know what with or how. Same with lirc. Hell, I can't even get the am/fm working.  LMMS blows my mind!  It took a slight workaround to get it working but  I followed the lmms wiki's solution to gedit two lines to the right audio driver in verbatim and presto! digiKam is awesome out-of-the-box.  Especially, if you have a large volume of photos.  Now I just wish I could get those other items working...

---

### Post by jasonnur on 2010-04-28
Model NAV50 or 532h-2807. MFG Date: Feb. 2010. Wireless: Atheros AR5B95. 
Works very well. Webcam and wireless are no problem at all. 
Known Issues: 

[LIST]
[*]Touchpad scrolling doesn't work in the latest Beta; neither edge- nor two-finger scrolling. 
[*]Touchpad's "disable while typing" also doesn't work. But with a few days of practice it's not much trouble. 
[*]Microphone doesn't work out of the box, but setting PULSE_SERVER to localhost before running an application seems to fix it. I.e.: **/bin/sh -c "PULSE_SERVER=127.0.0.1 program-name"** will launch program-name with full microphone support (program-name can be gnome-sound-recorder, skype, etc.). 
[*]Card reader Not found in Ubuntu9.10 also cannot boot from SD at all. 
[LIST]
[*]This is a multifunction card slot. 
[/LIST]
Note:(In Windows 7:SD Card is listed as a Disk Drive(Combo-Drive) on ENE USB Mass Storage Controler 

[LIST]
[*]>drivers:C:\\Windows\system32\DRIVERS\disk.sys C:\\Windows\system32\drivers\partmgr.sys) 
[/LIST]
[*]ethernet port works well
[/LIST]

---

### Post by marten22 on 2010-04-30
Hi..,
I buy a personal computer of HCL. It is regular creating problem in every 10-15 days . one HCL  replace my complete pc recently . Every time it create a new problem . please help me..Why it have problem always... Thanks in advance....

---

### Post by xDarkicex on 2010-05-01
Ubuntu 10.04
CPU AMD turion x64 ML-40
GPU nvidia GS 7900 Go
RAM Patriot DDR
80GB fujitus 5400RPM
nforce4 chip set 
Touch pointer
Alienware
M9700

---

### Post by eckeroo on 2010-05-09
YO!

I found my wife's old Toshiba Satellite Pro 4280 laptop and then decided to get it going again. I installed the maximum amount of memory and loaded Xubuntu 10.04. 

The specs are:

Xubuntu 10.04

Toshiba Satellite Pro 4280
Intel PIII 500Mhz clock speed
100MHz bus speed
Memory: 320 MB PC100
Graphics: S3 Savage IX, 64 Bit AGP
Hard Disk: IDE, 6 GB 4200rpm Toshiba MK6014MAP

update**
Hard Disk: IDE, 40GB 5400rpm Hitachi HTS541640J9TAT00

Wireless Card: PCMCIA Edimax-7108PCG

I updated the bios to the latest available [2.70-TRAD] from Toshiba's web page.

And it works suprisingly well! The wireless card worked straight away with no mucking about. It took a while to confirm the actual laptop model number [4280] as there's a label at the bottom of screen that says "Satellite Pro 4200 series" - very confusing indeed.

It's got 1 usb port (v1.1), 24x CD player and a floppy disk drive. I would also like to replace the hard disk with something larger and faster as I've only got 1.8 GB space left free.

**update - hard disk now upgraded, see top of post :)

The playback on youtube is choppy [can a 500MHz processor anywhere provide decent frame-rate playback from youtube?] and it cannot switch itself off at the end of the shut-down process.

Except for the flash playback for youtube, this machine can almost do your typical web browsing. Any suggestions or further tweaks that may help?

---

### Post by DisgusTeen on 2010-05-09
Success!

Ubuntu 10.4

Home built with Asus P7P55D motherboard, with Itel i5 processor,6G RAM, two hard drives[FONT=Verdana]
[/FONT]WDC 3200AAKS (320Gb), WDC 15EADS (1.5Tb), ATI Sapphire 5750HD video card, a couple of DVD drives and what have you.[FONT=Verdana]

Install was easy, a couple of glitches HP LaserJet 1020 drivers installed but will not print...will post in appropriate forum. ATI card worked with Ubuntu drivers and with ATI driver.

Nice work gang!
[/FONT]

---

### Post by Jammanuser on 2010-05-10
> **frodon said:**
> 
[B]Please Only List
1)Version Of Ubuntu 
2)Type Of Hardware
3)Hardware Maker
4)Hardware Model[/B]


1) 8.10 (Intrepid Ibex) 64 bit and 9.10 (Karmic Koala) 32 bit
2) Laptop with built-in microphone, webcam, backlit keyboard, etc
3) Dell
4) Studio 1535

My built-in microphone works well in both versions of Ubuntu. My webcam works through a Flash recorder in Firefox, but I can't get it to work in Cheese in my 8.10 version, though it works fine in Cheese in Ubuntu 9.10.
As for my back-lit keyboard, I had problems with it in the past. I think I remember turning it on, and having the whole GUI of Ubuntu freeze up on me, though that was from a much earlier version of Grub and 8.10. I haven't tried that in a while though.
I had a few problems in the past getting various hardware to work in 8.10, but I think I eventually got mostly everything to work on this laptop. I really like ubuntu a lot, and look forward to using future versions of it. :)

Cheers.

-Jam Man

:guitar:

---

### Post by n.l.o on 2010-05-11
Ubuntu Lucid Lynx 10.04

Laptop hardware:
Intel Core i7-620M Processor ( 2.66GHz 1066MHz 3MB )
14.1" WXGA+ LED 1440x900
NVIDIA Quadro NVS 3100m 256MB
4 GB DDR3 SDRAM 1066MHz SODIMM
250GB 7200 rpm
DVD Rec. (DL)

Thinkpad
T410 model no. 2522

All standard hardware worked out of the box (installed nvidia restricted).

Shock protection worked with existing solutions.
Have not tried the fingerprint reader, card reader, display-port, eSATA port, the built in 3G broadband.

Edit  I: card reader working out of box
Edit II: eSATA works

Cheers.

---

### Post by Orographic on 2010-05-15
Antec 300 Case
Intel Core i3 540
4GB Corsair DDR3 1333 Ram
Logitech Deluxe 250 USB Desktop USB Mouse and Keyboard
Samsung dual layer burner, SATA
Seagate Barracuda SATA2 500GB 7200rpm
Antec 520W ATX Neo Eco PSU
Gigabyte GA-H55-USB3 motherboard

Lucid runs perfectly so far after a few days of use on this new machine.Only problem I had was Clonezilla was causing my monitor to produce an 'out of range' message after a restore of an image. This seems to have been fixed by using a DVI-D monitor cable instead of the older D-SUB.

---

### Post by Matt__ on 2010-05-16
[B]Ubuntu 10.04 lucid lynx

[/B][B]Fujitsu-Siemens Amilo 2727li

[/B][B]intel T1500 dual core 1.86gb
Atheros wireless
2Gb ram


[/B]runs lucid pretty much out of the box except for one thing...the wireless has a kill on boot command and cant be activated in linux (i Used .vbs in windows to automate it).
This can be cured easily and very simply using a screwdriver and small piece of masking tape to cover the kill signal pin.
see [U]>>>[here for instructions]("http://forum.ts.fujitsu.com/forum/viewtopic.php?t=34742")<<<

[/U]

---

### Post by martinwebster on 2010-05-17
**Ubuntu Version**: Ubuntu Network Edition (UNE) 10.04
**Type of Hardwar**e: Netbook - Intel® Atom™ Processor N450 (1.66 GHz, 512 KB L2 cache, 667 MHz FSB) / Intel® NM10 Express
**Hardware Maker**: HP
**Hardware Model**: HP Mini 5102 (VQ670EA)

This works out-of-the-box with UNE 10.04. Installation using usb-creator is necessary. Details at my weblog: [Installing Ubuntu Network Edition on an HP Mini 5102]("http://martinwebster.info/2010/05/01/ubuntu-hp-5102/").

Notes:

[LIST]
[*]Remove **quiet** option when first booting installer.
[*]A wired network connection is required to set-up the WLAN firmware (Broadcom.)
[*]WWW button does not work.
[*]Bluetooth detected but not tested.
[*]SD card reader works.
[*]External monitor works.
[/LIST]

---

### Post by Xnyper on 2010-05-20
Ubuntu Version: 10.04
Type of Hardware: Sound Card
Hardware Maker: Asus
Haedware Model: Xonar D2X PCI Express 7.1 Channel Audio Card

Output works out-of-the-box, Input not tested

Shows up as CMI8788 [Oxygen HD Audio] in "Sound Preferences" Just had to select 7.1 Surround and it was working.

Warning: The card will show up with or without the power plug inserted, but it will not make any noise unless you plug in that cable.  The plug is easy to miss.

---

### Post by dvwolfman on 2010-05-24
> **frodon said:**
> Welcome to the Hardware Compatibility List.

The purpose of this thread is for you, the user, to post what hardware/hardware combination works with Ubuntu for you. If you wish, you may post how the hardware works (configuration related), and the steps you took setting it up. These informations will help other users to choose new hardware and it will also help the UDSF archivers to update the Hardware Compatibility Guide.

Everyone is welcome to post here, as long as it is hardware related data. For help with hardware problems, please use the standard procedure of searching the forums, and starting your own thread for assistance if no answer is found.

**_Give detailed explanations when reporting compatible hardware._**

**Also Do not post any lspci outputs in this thread as they will be removed with out question.**

[B]Please Only List
1)Version Of Ubuntu 
2)Type Of Hardware
3)Hardware Maker
4)Hardware Model[/B]

[COLOR=Red]***NOTE* This thread is exclusively for the listing of compatible hardware. Any idle chatter or unrelated posts will be moved/removed accordingly. *NOTE***[/COLOR]

Thank you.

**PS: the old compatibilty list thread can be found here and will remain closed** :
[http://ubuntuforums.org/showthread.php?t=183664](http://ubuntuforums.org/showthread.php?t=183664)

is there a bash command that lists only that info that you mentioned?
I would like to post a positive hardware compatibility experience
Thx

---

### Post by movieman on 2010-05-28
1)10.04
2)Laptop
3)Toshiba
4)F60-00M

All the basic hardware works, though after installing from the install CD I had to get the kernel update before the wireless network would operate correctly. I haven't tried the microphone, but sound output, 3D card, LAN, wireless and webcam all work with the latest updates.

The only thing I know of that doesn't work is restarting: I have to shut down and then press the power button to power up, otherwise the screen goes black and nothing happens.

The computer did come with a MS-DOS partition table and four partitions, so I had to tell the system recovery tool to delete the French copy of the OS to free up a partition to install to.

---

### Post by dglnz on 2010-05-29
In reference to this posting for help [http://ubuntuforums.org/showthread.php?t=1483778](http://ubuntuforums.org/showthread.php?t=1483778)

Touchscreen serial.
IBM celeron 2.8ghz
1gig ram
15gig HD
Lucid-lynx 10.04LTS

I had put the WINXP HD back in so I could be sure that the ELO graphics driver would work.
WinXP showed the screen as being a intellitouch 2500S, with this info i sallied forth on another hard drive to try and get Linux to work as seen on some video's.

Out of the box 6.10LTS ELO graphics driver and easily found xorg.conf setting had the touch working (calibration was required but it worked).

I wanted to jump to a later kernel etc so installed Lucid-lynx.
As I believed that xorg.conf in /etc/X11 had been depreciated I googled for help but couldn't find anything.

All the gory details of what my experience is in the above url if you the read needs further help on this.

It's settings where in reference to ELO touchscreen systems and the model 2500S intellitouch.




**[SIZE="4"]What did I do?[/SIZE]** 

From the repositories install xserver-xorg-input-elographics.deb
in the folder /user/X11/Xorg.conf.d create a file xorg.conf and enter the lines below
> 
Section "InputDevice"
   Identifier "ELO Touchscreen"
   Driver "elographics"
   Option "Device" "/dev/ttyS0"
   Option "AlwaysCore"
   Option "screenNo" "1"
   Option "MinX" "4100"
   Option "MinY" "0"
   Option "MaxX" "0"
   Option "MaxY" "4100"
   Option "UntouchDelay" "5"
   Option "ReportDelay" "1"
EndSection

Section "ServerLayout"
   Identifier "Xorg configured"
   InputDevice "ELO Touchscreen"
EndSection


In **[SIZE="3"]/etc/udev/rules.d/[/SIZE]** I created this file **[SIZE="3"]69-touchscreen.rules[/SIZE]** with the text below.
> 
# Elo Touchscreen
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="04e7", ATTRS{idProduct}=="0020", SYMLINK+="input/evtouch_event"


[SIZE="4"]*[COLOR="Red"]This got the touch working now for calibration![/COLOR]*[/SIZE]

I found from Googling a program call touchcal, I downloaded it (source attached)

Logged out and from the login went to command line (note you must compile it first) and to run the calibration program ***./touchcal*** this being in the source file directory.

the resulting numbers I recorded and then rebooted.
Once back in (I am not as comfortable on the linux command line as some) X I edited the above xorg.conf file so the values where below
> 
Option "MinX" "4026"
   Option "MinY" "4026"
   Option "MaxX" "0"
   Option "MaxY" "-16"


This then got the calibration working for 1024x768 screen resolution.

Hope this helps someone else.

---

### Post by Vectorferret on 2010-06-07
> **Xnyper said:**
> Ubuntu Version: 10.04
Type of Hardware: Sound Card
Hardware Maker: Asus
Haedware Model: Xonar D2X PCI Express 7.1 Channel Audio Card

Output works out-of-the-box, Input not tested

Shows up as CMI8788 [Oxygen HD Audio] in "Sound Preferences" Just had to select 7.1 Surround and it was working.

Warning: The card will show up with or without the power plug inserted, but it will not make any noise unless you plug in that cable.  The plug is easy to miss.
I tested input on same card. Works perfectly, but volume recorded is low (may be my microphone) so you may want to boost it.

---

### Post by Kaner on 2010-06-07
Installed 10.04 on a Dell Studio XPS and dual booting with Windows 7. Everything works fine except the headphone jacks. Plug in the headphones and the speaker sound cuts out but no sound through the headphones. Sound through the speakers is fine though.I`ve googled around and this is a known issue, but so far there is no fix available.

---

### Post by RafaelBecerra on 2010-06-12
Ubuntu 10.04 LTS
Dell Latitude D830
Intel Core2 Duo T9300
Broadcom NetXtreme 57xx Gigabit Controller
Intel PRO/Wireless 3945ABG
NVIDIA Quadro NVS 140M
 
Installed Ubuntu on a usb harddisk, for testing purposes.
 
Every thing is working like a charm!!!

---

### Post by edpatterson on 2010-06-17
Ubuntu 10.04 LTS
HP Pavillion dv6000
Intel Centrino Duo T5200 @1.6Ghz
2.0 GiB Ram

Seemless install (upgrade from 9.?). Only issue was Netbeans would not work from the Repository. The package from Sun installed and ran without a hitch.

Well done!

---

### Post by RazTaz on 2010-06-18
1) Ubuntu Karmic, Ubuntu Lucid (extensively tested both versions)
2) Notebook 
3) MSI
4) MSI GX 720

Notes:
It worked out of the box. 

Tested devices, ports and interfaces: DVD-ROM, audio (external and internal), webcam, bluetooth, wireless, USB, Ethernet, VGA). 

Ports not tested
Firewire, e-SATA, HDMI (i suppose they work fine, only I didn't have any device to use with them)
Modem port (I had problems in the past with laptop MB integrated modem chipsets, particularly as they are usually win-modems and the drivers for them are either proprietary (see Connexant/Linuxant) or not available at all for Linux. In this case (MSI GX 720, I tried using the modem on a fixed telephone line using Efax but it didn't work and I gave up)

Bottom line:
The notebook works wonderfully with Ubuntu. 

Regards,
RazTaz

---

### Post by CWSmittenaar on 2010-06-19
**1a)Version Of Ubuntu **9.10 installed on USB for testing.  Worked great[B]
1b)Version Of Ubuntu[/B] 10.04 clean install to HDD, dual boot with fresh install of WinXP SP3
** 2)Type Of Hardware **Laptop
** 3)Hardware Maker **HP[B]
4)Hardware Model [/B]Pavillion dv8300 (ex177av)

Tested 9.10 for over a month on the USB stick (8GB) with persistence.
Running 10.04 since released.
Both had to install proprietary video drivers (Nvidea)

Formated both hard disks (2 120GB SATA) set 1st to Ext4 Ubuntu 10.04, 2nd set 2 partitions: 1st partition NTFS to Boot WinXP Media Center edition SP3, 2nd partition NTFS but shared data between Linux & Windows. Everything works great so far.

I have not tried burning CD/DVDs in Linux yet, or lightscribe. Also have not tried the TV tuner yet, as I don't have an input for it currently.  Some day maybe I'll test it.

I spend probably 95% of my time in Linux, and even use several windows programs via Wine, so I can continue with the familiar software till I get a chance to find and test Linux equivalents that I like.  So I only boot into Windows for very few tasks anymore.  Once I get those tasks converted I will remove the Windows from my machine forever!:grin:

Recently had over heating issues. But after reading several threads on these forums and installing some monitors on my task bar the over heat is a thing of the past. _**Linux and the Ubuntu forums, an unbeatable combination!**_:biggrin:

---

### Post by tommihl on 2010-06-19
10.04 Lucid Netbook Remix
HP Mini 5101 Laptop
Intel Atom CPU N280 1.66GHZ
1GiB RAM

Runs just fine out of the box. Theres 2 buttons(internet & EMail) which doesn't do anything but never put any effort to fix that. Everything else, including webcam and wifi works perfect.

---

### Post by d.ericsson on 2010-06-29
Except, this was supposed to go in the Hardware **In**compatibility list. Sorry for that.

---

### Post by stdb on 2010-07-03
Asus EEE PC 901 (netbook) works out-of-the-box on Ubuntu 10.04 Desktop x86.
Out-of-the box support since Ubuntu 9.10
Older versions of Ubuntu (<=9.04) may require some manual tinkering (especially kernel) after installation. See this resource for eeepc-patched kernels for those older versions of Ubuntu: [http://array.org/ubuntu/](http://array.org/ubuntu/)

---

### Post by pingu1 on 2010-07-07
HP CQ61-419 
[http://www.expert.no/product/product.aspx?identifier=126501](http://www.expert.no/product/product.aspx?identifier=126501)
 
Specs:
 
Processor: AMD Sempron prosessor M120
Memory size: 2048 MB
HDD: 250 GB
CD/DVD: Super Multi DVD +/- R/RW double-layer
Network: WLAN IEEE 802.11n; Fast Ethernet 10/100; WLAN IEEE 802.11b; WLAN IEEE 802.11g
Graphics: ATI Radeon HD4200 up to 1919 MB shared memory
USB ports: 3
HDMI: Yes
Memorycard-reader: Yes
Integrated webcam
Screen: 15.6''
Resolution: 1366 x 768
Weight: 2.96
 
 
Installed 10.04 yesterday.
Everything works so far. Desktop effects works fine (System->Appearence->Effects->Extra)
Also installed a proprietary driver for the graphics card from ATi.
 
NB! NOT TESTED YET:
-webcam
-HDMI
-Memory-card reader
 
The WLAN-indicator kept flashing (red/blue) constantly, but after 
update in update-manager, it just flashes when there is data being uploaded/downloaded.
 
Pleased.

---

### Post by NUboon2Age on 2010-07-09
Ubuntu Lucid Lynx 10.04
Xubuntu Jaunty Jackalope 9.04

Dell Inspiron 2200
Intel(R) Celeron(R) M processor 1.40GHz 
BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
 using bcmwl5 and ndiswrapper installed with ndisgtk/Windows Wireless Drivers
1.25 GB Ram

---

### Post by qepsilonp on 2010-07-09
ubuntu 10.04

Mouse incompatibility cherry xero works in windows 7 but stops my bois from starting up so every time i start up i have to remove the mouse then plug it back in once windows has started up but totally refuses to work in ubuntu 

there for im guessing its more a problem with the mouse than ubuuntu but it is annoying having to change mice when my old mouse doesn't like my mouse mat and will skip all over the desktop

don't really expect a fix because its not a highly popular mouse

---

### Post by krtica on 2010-07-11
1)Version Of Ubuntu: 8.04 - 10.04
2)Type Of Hardware: Laptop
3)Hardware Maker: Hewlett-Packard
4)Hardware Model: HP 550

Everything worked "out of box".

---

### Post by rolleander on 2010-07-13
e-machine T3642 stock
Amd Athlon64 4000+
(2.6GHz, 512KB L2 cache, 2000MHz system bus)
1024MB 667MHz DDR2 dual-channel memory (2 × 512MB)
250GB SATA II
16x DVD±R/RW Supermulti drive
NVIDIA GeForce® 6100 integrated graphics

Worked out of the box - fresh install of Ubuntu 10.04 (after wiping Vista) - 
Had to download proprietary driver from NVIDIA but was automatically prompted for that.

---

### Post by rolleander on 2010-07-13
Compaq Presario SR1913WM
original parts
2.2ghz AMD Athlon 64 3500+
NVIDIA GeForce 6150 LE integrated
512 MB 184 pin, DDR SDRAM
120gb sata hd

upgraded to 4gb ram before i installed ubuntu 8.04 but think it would have ran anyway
also have 2nd harddrive now where ubuntu is installed. WinXP on 1st drive
both hds are seagate 120gb a piece (2nd was pulled from an LG tv)

had to get proprietary graphics driver for NVIDIA and had a bunch of sound issues (garbled noises in speaker) don't remember exactly what I did to fix it, but i found the fix on these forums.

now upgraded to ubuntu 10.04 sound and everything else worked out-of-box

have upgraded graphics now GeForce 8400 gs - installed new NVIDIA driver

had to download lightscribe program to get lightscribe to work

can download here -
[http://lightscribe.com/downloadSection/linux/](http://lightscribe.com/downloadSection/linux/)

actually works better than my lightscribe software on my windows drive.

---

### Post by jen1963 on 2010-07-14
Lenovo G5555 running Lucid 10.04 64 bit.

You'll need the proprietary ATI drivers for the video but Jockey pulled those in without issue.

Webcam,wireless all worked 'out of the box'

:biggrin:

---

### Post by reg2117 on 2010-07-15
> **Orographic said:**
> Antec 300 Case
Intel Core i3 540
4GB Corsair DDR3 1333 Ram
Logitech Deluxe 250 USB Desktop USB Mouse and Keyboard
Samsung dual layer burner, SATA
Seagate Barracuda SATA2 500GB 7200rpm
Antec 520W ATX Neo Eco PSU
Gigabyte GA-H55-USB3 motherboard

Lucid runs perfectly so far after a few days of use on this new machine.Only problem I had was Clonezilla was causing my monitor to produce an 'out of range' message after a restore of an image. This seems to have been fixed by using a DVI-D monitor cable instead of the older D-SUB.

Is RAID supported for this motherboard? See [ [COLOR="Blue"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1295730&highlight=GIGABYTE+SATA2").

---

### Post by cfinc on 2010-07-18
HP Pavilion dv5
geforce 9600m gt working properly with driver 195 (buggy with 173)
hp quicktouch working
razer diamondback 3g working at 800 dpi (1800 dpi doesn't work)
hp photosmart 2610 and officejet J4580 working through usb and network
canon ix4000 working through usb
able to browse my nokia 6760 slide through usb connection
toshiba 320 gb (SMART says there is a problem with the temperature of airflow when running ubuntu)
sandisk cruzer micro 4gb working sometimes
two microphones work and webcam(low framerates)
overall pretty good compatibilty :)

---

### Post by n2dabloo on 2010-07-22
Please Only List
1)Version Of Ubuntu: 10.04
2)Type Of Hardware: Laptop
3)Hardware Maker: Asus
4)Hardware Model: G73jh-a3
Everything appears to be working fine out of the box.  This is the 4th latpop that I've put Ubuntu on and I must say it's the best experience so far.  Thanks Ubuntu :D

---

### Post by corrytonapple on 2010-07-26
With 10.04 my Toshiba l455 is perfect, except for fan control and function keys. Otherwise, I love it.

---

### Post by Jaydon H on 2010-07-29
Ubuntu 10.04 (Lucid)
Lenovo Thinkpad X200 Tablet:
Intel Core 2 Duo @ 1.87GHz and 1.88 GHz|2Gb DDR3 RAM|160Gb HDD|256Mb Graphics|Fingerprint Reader|Inbuilt Camera|Conexant HD Speakers

All of drivers work bar the Fingerprint reader, and the Mute and ThinkVantage buttons lack function. The middle button/scroll button has been changed to have a middle-click function. Other than that, everything else works.

---

### Post by desnaike on 2010-07-29
Ubuntu 10.04
Desktop HP p6510y
Ubuntu 10.04
laptop HP G61-429wm
All works out of the box.

---

### Post by Bill by the sea on 2010-08-01
I just set up a new workstation for home use. It uses usb wifi and a hardware raid 1. The netgear wg111v2 works with no modification just install and reboot and it comes up. The raid card is an Areca arc-1200, again it comes up with no problem and is transparent to Lucid Lynx.

 The workstation is home made with a Gigabyte motherboard and Seagate es drives.

I recommend both of these items.

---

### Post by jasi on 2010-08-03
The purpose of this thread is for you, the user, to post what hardware/hardware combination works with Ubuntu for you. If you wish, you may post how the hardware works (configuration related), and the steps you took setting it up. These informations will help other users to choose new hardware and it will also help the UDSF archivers to update the Hardware Compatibility Guide.

---

### Post by edwinbmiller on 2010-08-07
[B]Please Only List
1)Version Of Ubuntu = 10.04 LTS 
2)Type Of Hardware = motherboard
3)Hardware Maker = MSI
4)Hardware Model = 785GM-E51

worked except for igp hd4200 with older catalyst drivers had problems.
latest catalyst 10.7 drivers fixed problem
now everything works


[/B]

---

### Post by selittl on 2010-08-08
1.) 10.04 LTS
2.) net-top box
3.) Asus
4.) Eeebox PC EB1501

Everything worked out of the box.

---

### Post by mastablasta on 2010-08-13
1)Version Of Ubuntu = 10.04 LTS 
2)Type Of Hardware = motherboard
3)Hardware Maker = ASRock
4)Hardware Model = ASROCK 4CoreDual-SATA2 R2.0
 
 
Sound card has problems (ALSA needs to be upgraded, issues/bug with hda_intel module - errors in log file). Works on and off (may work for some time and then stop working) and only Analog Duplex. If Digital duplex sound is on, the mic is not working. Otherwise it works quite fast, but i suggest an inexpencive PCI sound card to be added in order to get propper sound with this Ubuntu release.

---

### Post by billwww on 2010-08-21
HP Pavilion dm3-2010us thin and light laptop
AMD Athlon II Neo Dual Core Processor K325
320 GB hard drive
4GB DDR3 SDRAM

Installed ubuntu 10.04 (64-bit) in dual-boot configuration with Windows 7 (64-bit Home Premium). I used the Windows partition editor to shrink the Windows partition and deleted the HPTOOLS partition (contents saved in Windows). Smallest size Windows would allow was about 150 GB. That left about the same amount of space for ubuntu. After that installation was straightforward.

I added a Logitech laser mouse and Samsung USB DVD drive (shared w/netbook).

Most everything works--minor problem with touch pad not turning off (seen in other HPs).

This is a nice and fast laptop--starts up and shuts down about twice as fast as Windows.

:D

---

### Post by ram0042 on 2010-08-23
1. Ubuntu 10.10 Alpha 3
2. Intel Celeron D 335 / 2.8 GHz, 256 MB, 1 x 80 GB - standard - ATA-100 - 7200 rpm, AC '97.
3. HP/Compaq
4. SR1411NX

Yes, this was very slow with Windows but not too fast with Ubuntu. There are no drivers for the integrated graphics so don't bother searching for them. I know they don't exist. The OS freezes and at around 30-50 min., it just shows some weird images and stays like that until you force to shut it down. It now has 1GB RAM and I took off the PCI modem and card reader to conserve more power and it also helped in Windows 7 to stop showing me the safely remove hardware dialog for the faulty drivers. The fan gets out of control when the PC is idle. Other than that, the system boots quite fast.

---

### Post by Tycho59 on 2010-08-24
IBM ThinkCenter

Ubuntu 10.04 Lucid Lynx
Pentium 4 @ 3.2 GHz
Integrated GPU 64mb shared from system
1GB of system ram
160GB
Optical Drive (DVD+_R-R/W - CD R-R/W)
TrendNet  Wifi card (802.11 b/g)

---

### Post by ShootEmUp on 2010-09-07
HP Pavilion 6730

Xubuntu 10.04 LTS
Intel Celeron @ 600Mhz
256mb RAM
40GB IDE Hard Drive
Standard PCI Ethernet Card

Had to use Alternate Install CD, But runs great (compared to XP on the same computer). Recommend using IceWM as Desktop Environment.

---

### Post by PGHammer on 2010-09-09
ASUS P5N-EM HDMI
Celeron DC E1200
3 GB DDR2-800 (2 GBx1/1 GBx1)
WDAC5000AAVS 500 GB primary/Maxtor 6LS200 200 GB secondary (both SATA)
Visiontek AMD HD5450 PCIe graphics card (512 MB GDDR3)
Creative Sound Blaster X-Fi XtremeGamer (PCI)
Microsoft Wireless Keyboard 6000 V.3 USB keyboard/Logitech V220 Cordless USB mouse
nVidia MCP73 gigabit Ethernet (primary)/SMC USB wireless-G Ethernet (secondary)
Windows 7 x64 Ultimate (primary)/Kubuntu 10.10 x64 Maverick Meerkat 20100908 daily (secondary)

Only problem is that closed-source AMD drivers do not work with Xorg 1.9 (known issue); I'm using open-source drivers from xorg-edgers PPA (very fast 2D).  All hardware is otherwise fully supported with full function.

---

### Post by Dragynn on 2010-09-10
Older computer:

Gigabyte K8NF-9 mobo
AMD64 Venice core 3200 @2.0 ghz
1 gig Patriot DDR-400
WD 100 gig HD
Nvidia 6200 turbo-cache running dual monitors on latest drivers from repository (260 series)
Samsung CD/DVD 
Dual boot XP Pro/Ubuntu 10.04 Lucid Lynx

Really zero problems installing or running, only had to apply workarounds for Avast install and getting the Plymouth boot splash to use alternate screen/splash pic. The Windoze partition is easily mounted and read by Ubuntu, and I can move files around and modify freely.



Only Issue: Foobar 2000 works in Wine, but it won't import my whole library (several formats involved) and the sound is fuzzy, very sad, would like to see Foobar make a linux version.

---

### Post by lutopium on 2010-09-17
Greetings... My first post!  I've checked numerous posts before buying an external hard drive and it seemed complicated.  Just wanted to tell you that I just bought a Seagate FreeAgent drive and it works fine.  Plug and Play.

---

### Post by mrsfixit on 2010-09-18
Dell Studio XPS 435MT

OS: Ubuntu 10.04 Lucid 64 bit
CPU: Intel core i7-920
6 GB's of DDR3 1066 RAM
640 GB Western Digital Blue HD
ATI Radeon 3650 256 MB video
Sony Optiarc DVD burner

I added: Samsung DVD Burner
I added: 1 TB Seagate HD

As for the rest of the motherboard specifics, chipset, sound, NIC and whatnot- I'm not sure as this is a pre-assembled machine.

Everything is working out of the box. I have had no issues at all. As for the ATI Radeon, I thought I would have a problem, but so far I've had none. I am using the open source driver, I have not tried to install the proprietary one.

I also am using an HP Officejet 6500 all-in-one usb printer, which is working well. This did NOT work OOB. I had to install CUPS, and pretty much much everything that said "HPLIP" that I could find in synaptic. After that it's all good.

The printer is also working great with my 2 Karmic 9.04 systems as well.

---

### Post by ItalOz on 2010-09-19
[COLOR="Blue"]Epson TX300F[/COLOR] inkjet printer scanner all in one
Installed on Ubuntu 9.10 64bit


I posted a [[COLOR="Red"]HOW TO here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1577669")

the printer prints... he he :P but as far as I have tried till now if you select monochrome printing from the options the printing goes out of scale.

also the scanner works after the installation of Iscan and now also Xsane picks out the scanner.

with Iscan I can use also the Automatic Document Feeder

---

### Post by adrenaline_rush on 2010-10-07
Hi,
 
I need to install Compiz and emerald to get the 3D Desktop. Could you please send me the link for hte same...and also the instructions on how to install the same
 
Thanks
 
 
 
> **skygazer said:**
> I have a vista home basic enabled laptop which was corrupted by the virtumonde virus and i couldnt get it to bootup. So i decided to install linux. I took a iso file of ubuntu 8.04 LTS to my friends XP machine and created a bootable Live USB using unetbootin. Install went perfectly, no hickups.This is my first linux install on a real computer and so far, i am amazed at how simple it is. Being from a windows background made me think i would have to deal with cryptic command lines and still not get anything working. But letme tell you, it all freaking works right out of the box. Here's my configuration
 
Compaq Presario V3702AU Laptop 
 
AMD Turion 64 X2, 1.9GHz
1 x 1GB, DDR2-667 Samsung
160 GB, 4200 rpm HDD Western Digital
Nvidia Geforce 7150M GS graphics card (287 MB shared RAM)
Nvidia MCP67M Chipset (Nforce 630M)
Integrated WLAN 802.11b/g Broadcom
Connexant HD Audio
SD Card Reader
Built In webcam 1.3 Mpixel
 
Installation took 15 minutes + 1.5 hrs to download/install updates. Then it prompted me to download and install propriotory drivers for wlan and gfx which i did and they work smooth. Then i installed compiz+emerald for 3d desktop.
 
I got the following hardware up and running out of box.
Audio, SD card reader, Webcam, Bluetooth, Volume up/down/mute buttons, Media player buttons play/pause/next/prev etc, Brightness up/down, hibernate button, inbuilt and external microphones, all led indicator lights. 
 
Yet to check out the following:
External monitor, PCI-express slot, firewire, s- video port, quick launch button, HDSOFT Data/Audio modem
 
I hope this helps other Compaq V3702X users out there who want to migrate to Linux. 
 
Regards,
Skygazer

---

### Post by optimisticyet on 2010-10-12
Ubuntu 10.04
USB external hard drive
Freecom
Mobile drive Classic II

This is a 250 GB external hard drive and works fine for me.

Out of the box, it has a single (primary) partition, formatted as FAT32. I used Gparted Live (version 0.6.2-2) to:

1) Shrink this original partition to 35 GB.

2) From the free space released, create an extended partition containing 4 (logical) partitions.

3) In each of these new partitions, created an ext4 file system.

4) Add a meaningful label for each partition, since Ubuntu will then use these labels for mount points when I plug in the external USB drive. For example, a new partition labelled "drama(mp3)" will be mounted at /media/drama(mp3). Otherwise, the partitions will have mount points using UUIDs.

---

### Post by krtica on 2010-10-18
1) Ubuntu 10.04 LTS Desktop i386
2) Tablet
3) Genius
4) G-Pen 340

Installation Guide:
[LIST]
[*][https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)
[*][http://allportal.net/posts/linux/6261910/Instalar-tableta-digitalizadora-en-UBUNTU-9_04-o-10_04.html](http://allportal.net/posts/linux/6261910/Instalar-tableta-digitalizadora-en-UBUNTU-9_04-o-10_04.html)
[/LIST]

---

### Post by optimisticyet on 2010-10-19
I have been using a **Microsoft Wireless Optical Mouse 2000** for the past 3 weeks without any problems:)

[LIST]
[*]My PC is running Ubuntu 10.04, and the mouse is reported by the Kernel as being "version 1.0".
[*]The mouse's transmitter connects to a USB port.
[*]Pointer sensitivity and acceleration adjust properly using the usual tool at System>Preferences>Mouse on the Gnome desktop.
[/LIST]

---

### Post by bear costume on 2010-10-27
**Thanks for the Compatibility Guide.**

---

### Post by bear costume on 2010-10-27
[B]Thanks for the Compatibility Guide list its really good
[/B]

---

### Post by annie25 on 2010-11-01
i have recently bought a dell mini laptop ..please suggest me which window is compatible with my laptop

---

### Post by arbos on 2010-11-09
What motherboard you use for Intel® CoreTM i5-760 2.8GHz, 8MB and Ubuntu ?

---

### Post by Nikola92 on 2010-11-13
Ubuntu version : 10.10
Computer: 
- Hard Drive: Western Digital 1TB
- Motherboad: Gigabyte H55M-S2H
- Processor: Intel i3-530 2.93 Ghz
- RAM: Kingston HyperX 4 GB DDR3 1600 MHz
- Graphic Card: NVidia Gainward GTX 260 1792MB

Everything works. I had to update graphic card driver for enabling Visual effects.

---

### Post by speedofdark on 2010-11-17
HP 3125 with ubuntu 10.10 everything works out of the box.

---

### Post by b3rylord on 2010-11-18
Compaq Presario C500 and a clean install of Ubuntu 10.10

Still fighting to understand how it all works but willing to learn.

Lexmark Z32 printer via USB prints SOME lines garbled from Open Office  but there seem to be so many different ways to print and I just cannot get a clear overview of them all (CUPS, lp, lpr, lprm, lpq, Red Hat, Ghostscript etc.) I tried the suggestion at [http://www.linux.com/learn/tutorials/262243-introduction-to-printing-in-linux](http://www.linux.com/learn/tutorials/262243-introduction-to-printing-in-linux) where it says to start cups type the following:
/etc/init.d/cups start

Response:-

deltaman@plimsoll:~$ /etc/init.d/cups start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service cups start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start cups
deltaman@plimsoll:~$ service cups start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.55" (uid=1000 pid=2506 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
deltaman@plimsoll:~$ 

So what did I do wrong....puzzled of Tonbridge.....

Lexmark have no linux drivers despite other Linux forums pointing to some for the Z600 which might be the one I want but they are seemingly not available when I have looked[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

The two lights on the printer flash after each print and then I have to hard boot the printer to do anything else with it. This does not happen on a windows machine with the same cable/printer.

Canon lide25 scanner will do a rudimentary scan but cannot be associated with a GUI seemingly.
Canon told me to go away, so I WILL go away to HP who have scanner  support for Linux.

Getting my Vodafone mobile connect dongle has taken some time to make work, and all is now ok apart from being unable to see how much of my 5GB limit I have used without calling and asking Vodfone!!!

WHilst highly delighted with Ubuntu for speed in general and many features too numerous to mention, I seem to be caught  in an upgrade loop similar to that experienced when moving from Windoze XP to Vista where I had to buy a scanner which would fit in with the OS rather than the other way around....

Fuji camera FJ-100 was recognised and catered for with no problems.

---

### Post by igotsanevo4g on 2010-11-22
I'd like to contribute to this list, but am unsure of how to get the exact make and details of my hardware, heres what i know/would like to know.

OS - 10.10
ram - 512 make?
processor - 2.5ghz intel pentium 4
Motherboard - no idea
Display - 32' Vizio xtreme tech HDTV
Graphics card - Whatever was built in..

It's a compaq presario.

Is there a terminal command to pull some of my hardware info? Id really like to know...

---

### Post by cascade9 on 2010-11-24
> **igotsanevo4g said:**
> Is there a terminal command to pull some of my hardware info? Id really like to know...

sudo lshw

That should get you pretty much everything.

---

### Post by peterthewolf on 2010-11-28
TP-LINK wireless modem router for ADSL TD-W8950ND.
By far the easiest router to install once isp user name entered it largely set itself up. The setup software is impressive.
And since it is one of the cheapest I have been delighted.
Amazon UK £25

---

### Post by HankB on 2010-12-09
> **jasi said:**
> The purpose of this thread is for you, the user, to post what hardware/hardware combination works with Ubuntu for you. If you wish, you may post how the hardware works (configuration related), and the steps you took setting it up. These informations will help other users to choose new hardware and it will also help the UDSF archivers to update the Hardware Compatibility Guide.

How about a link to the UDSF Hardware Compatibility Guide? I searched but could not find anything other than dead links dating back years.

Also... The particular search I'm involved in at the moment is desktop motherboards known to suspend/resume. If you're posting "everything works" please indicate if you've tried this and please give it a try!

many thanks,
hank

Edit: I found the UDSF:[https://wiki.ubuntu.com/UDSF](https://wiki.ubuntu.com/UDSF)

Searching for "hardware Compatibility Guide" gets me: 
> Your search query "hardware Compatibility Guide" didn't return any results. Please change some terms and refer to HelpOnSearching for more information.
Info (!) Consider performing a full-text search with your search terms. I did that and found lots of apparently obsolete references to laptop compatibility but no hint of an actual guide. :(

---

### Post by pygmyseahorse on 2011-01-01
I'm not covered by any embargo, and I bought these off a retail store... so

Intel Core i7 2600 @ 3.4GHz
MSI P67A-GD55 mainboard, Intel P67, Sata-6G. I used only the 3G ports, USB3 untested, no USB3 stuff lying around.
4GB of cheap Kingston DDR3 RAM
Intel 160GB G2 SSD
ATI 5770

Works fine, works well so far. Networking works as expected.

---

### Post by walt.smith1960 on 2011-01-01
Recent upgrade

Gigabyte MA785GA-US2H  
AMD AthlonII X2 240
Nvidia GeForce 8400GS
1 stick 2 GB crucial PC-6400 DRAM

Not a firebreathing gaming rig but it seems very stable and all the hardware seems to work properly.  It suspends and resumes reliably.  I had the Nvidia card and Nvidia has a good record with Ubuntu so I chose to not use the onboard ATI video.  This replaced a 6 year old Gigabyte board whose SATA ports were occasionally uncooperative.  I'll add a second identical stick of RAM soon so I can experiment with virtualization.  The MoBo has 4 DRAM slots which doesn't seem common on MicroATX boards.

---

### Post by seagullplayer77 on 2011-01-03
I picked up a [Lenovo H320-4041GU]("http://www.officedepot.com/a/products/328254/Lenovo-H320-4041-1GU-Desktop-Computer/") from Office Depot the other day, and I've been very impressed with it. Lots of features packed into a small, fast, powerful package. It's nice!

And what's even nicer is that installing Ubuntu Studio 10.10 (AMD64) went flawlessly. Sound and video "just worked" with a base install. The wireless card (Atheros AR928X, according to lspci) worked fine after I installed wicd. JACK worked without any tinkering, which was another major plus. Basically, everything works the way it's supposed to. I've been using the install for a few days and I haven't noticed any strange quirks or lacks of functionality.

Some things I haven't been able to test:

- The HDMI port
- The multi-card reader

I had a hard time finding anything useful on the Internet about this particular model of computer, so I figured I'd mention it here. In sum, the Lenovo H320 appears to run Ubuntu 10.10 quite reliably.

---

### Post by naina4beauty on 2011-01-05
Ubuntu version: 6.06
Type Of Hardware: USB Bluetooth Dongle
Hardware Maker: MSI
Hardware Model: BToes 2.0 EDR
Thanks and check

---

### Post by alienmindtrick on 2011-01-05
Ubuntu 10.10 Maverick Meerkat
Inkjet Printer
HP
Deskjet F2430

After switching from Windows Vista to Ubuntu 10.04 (now upgraded to 10.10 Maverick), I got the HPLIP Toolbox from the Ubuntu Software Center and actually got more functionality options for my printer than I had before with the HP OEM software, plus automatic updates through Synaptic Package Manager. Double plus ultra bonus!

---

### Post by boxcar451 on 2011-01-09
I also have an e machine. It's a T3504 pretty much stock from Best buy 5 years ago.
Desktop T3504
seagate 100gb hdd
2gb ram
nvidia ge force 8400 gs 512mb
cd rw drive+dvd rom.
I tried to install a newer hard drive but doesn't seem to be recognized. I downloaded Ubuntu 10.10 and thinking of wiping out my windows xp home edition and replace it with the Ubuntu. Thanks

---

### Post by [Snc] on 2011-01-10
My current configuration of my desktop is:
motherboard: Intel HD55HC
processor: Intel i5-750
ram: 8Gib (4*2Gib modules, type: OCZ3G1333LV2G)

i'm running Maverick 64bit and i cannot get the whole 8Gib of ram to be utilized (lshw can see all 8Gib, the system utilizes only 4Gib).

The problem is also present if i try to use only two ram modules in dual channel mode, then the system utilizes only 2Gib, unless i set them so, that the modules are in single channel mode, than the system utilizes 4Gib.

Conclusion - "dual channel" does not work, maybe the second channel cannot be used.

---

### Post by bilallucky on 2011-01-11
Laptop:
Dell Latitude D820
Ubuntu 7.10 - Gutsy
Gnome 2.20

Intel Core 2 Duo T7200
3 GB RAM
160 GB SATA Laptop Drive (multi-boot with XP Pro SP2)

nVidia GeForce 7400 (worked after download of driver)

Intel Pro 3945 Wireless -worked out of the box!
BroadCom BCM5752 Ethernet - Worked out of the box!

Intel 82801G Audio Controller - Alsa

---

### Post by seagullplayer77 on 2011-01-13
**Hardware:** Logitech MK320 Wireless Keyboard and Mouse combo

**OS:** Ubuntu Studio 10.10 (AMD64)

**Functionality:** Plug and play; works straight out of the box. Most of the hotkeys (volume up/down/mute, calculator, mail, sleep) work as well. A few of the hotkeys (Internet, lock screen) do not, but that's just a matter of configuration, I'm sure.

Overall, I was very impressed! A good product made excellent by the fact that it plays so nicely with Linux.

---

### Post by itlarson on 2011-01-16
Has it occurred to anyone that a hardware compatibility list in the form of 74 pages of forum postings is pretty much useless?  You can't even search it, because the results point to the entire thread, not the relevant posting.

---

### Post by HankB on 2011-01-16
> **itlarson said:**
> Has it occurred to anyone that a hardware compatibility list in the form of 74 pages of forum postings is pretty much useless?  You can't even search it, because the results point to the entire thread, not the relevant posting.

Please click "Search This Thread" above the first post on each page.

---

### Post by HappyLinux on 2011-01-18
Here's my complete system setup, and it all works out the box. Will list driver version where possible.

I've got Ubuntu 10.10 64bit installed on a dual-boot with Win7. As of posting, the kernel is 2.6.35-24-generic, with Gnome 2.32.0.

Asus P7P55 LX motherboard - so far just don't use any IDE drives as there's still Linux booting issues with the IDE controller for some reason.

Intel Core i5 760

4GB of memory being recognised as 3.9GiB. Not sure if that's actually 4GB as GiB is different to GB.

Samsung hard drive. Not sure what model, but it's a 1TB drive.

Creative 5.1 speakers. All speakers work fine through the sound testing, but haven't been able to test through any other means.

Samsung DVD Writer. Works fine reading disks, not tried writing to any yet.

Nvidia GeForce GTS450. Using 260.19.06 drivers which is the minimum version required for this card.

Samsung SynMaster 943 monitor. Yep, this works as well, even at higher resolutions than Win7 would allow.

Microsoft Natural Ergonic 4000. All the basic buttons work out the box. Not bothered about the extra features.

Logitech MX-400. Works perfectly out the box.

---

### Post by om8g on 2011-01-23
1)Version Of Ubuntu: Ubuntu 10.10 - 64 bit.
2)Type Of Hardware: Laptop
3)Hardware Maker: Acer
4)Hardware Model: 6920g

Everything is working out-of-box :D

---

### Post by mikeavison on 2011-02-06
Ubuntu 10.04 on laptop Axer Extensa 5220

This worked nearly straight out of the box. I installed it on the backup partition that Acer had created and the GRUB dual boot routine worked excellently.

Only the wireless network did not work straight away. The acer has a built in Broadcom wireless. To get it working I just plugged it in to a router and clicked from the menu in the top bar System> Administration> Hardware Drivers... and let Ubuntu search for drivers. It came up with some combination of a wrapper and a driver. I selected them both and it worked from then on.

The wireless connection did seem to drop out occasionally but that seemed do fix itself,possibly as a result of downloading updates.

The only thing that is wrong is that sometimes after going into sleep mode, it fails to wake and I have to force it off and reboot it. Not a big problem.

Mike

---

### Post by silverwolf636 on 2011-02-07
I am currently running Ubuntu 10.04 Lucid and am having fantastic results with it. 
I recently purchase an **IOGear Bluetooth USB Micro Adapter GBU421WM**. I plugged it in went to PREFERENCES -> BLUETOOTH and set it up so I could send pics from my phone to my computer. 
That was all I did and it works great. 
I don't get to help much on here but if I run into something that I can add, I'm doing it. 
Thank you Ubuntu for a fantastic OS: 10.04 Lucid.
--ray--

---

### Post by macstl on 2011-03-01
Im running ubuntu 10.10 on IBM laptop model t23. Everything works out of the box. Wifi, pcmia, usb, sound audio etc .
Great job!

---

### Post by John4582 on 2011-03-05
**Everything Working** with out loading additional Drivers (Just install Ubuntu plus Updates and go) Self built system so detail Hardware/OS's Listed below.

**Multi Boot 3 OS's**
 
**Operating Systems:**

[LIST]
[*]Microsoft Windows XP Media Center Edition/XP Pro/MCE 2005 OS Service Pack Service Pack 3 (All update applied)
[*] Microsoft Windows 7 Service Pack Service Pack 1 (All update applied)
[*] Linux Ubuntu 10.10
[/LIST]
  [B]CPU Processor: 
[/B]
[LIST]
[*]QuadCore AMD Phenom(tm) 9850, 2500 MHz (12.5 x 200) Max 3000 MHz (15 x 200)
[*]CPU Alias: Agena
[*]CPUID Revision:    00100F23h
[/LIST]
  **Memory - Max 16 GB 4 X 4096MB:**

[LIST]
[*]Installed 4096 MB
[LIST]
[*]DIMM1: Crucial Tech. CT25664AA800.M16FJ 2 GB DDR2-800 DDR2 SDRAM  (6-6-6-18 @ 400 MHz)
[*]DIMM2: Crucial Tech. CT25664AA800.M16FJ 2 GB DDR2-800 DDR2 SDRAM  (6-6-6-18 @ 400 MHz)
[/LIST]
 
[/LIST]
  **Motherboard:**
[LIST]
[*]MFG/Name: Gigabyte GA-MA785GM-US2H REV. 3.3
[*] Motherboard ID: 05/17/2010-RS785-SB710-7A66BG05C-00
[*] Motherboard Chipset: AMD K10
[*] BIOS Type/Date/Version: Award Modular (05/17/10) F11
[/LIST]
**Hard Drives:**

[LIST]
[*] All my internal HDDs are New Seagate LP Series (Green drives) SATA drives. Check Seagate product guide at the following Link: [http://www.seagate.com/staticfiles/s...100564361e.pdf]("http://www.seagate.com/staticfiles/support/disc/manuals/desktop/Barracuda%20LP/100564361e.pdf") for detail specs.
[*]To be exact the drive I installed Ubuntu on is a 1.5TB  ST31500541AS (7200.11) (Rev. E) 32MB Cashe SATA 3Gb/s. Also both my 1TB  drives are ST31000520AS and the specs are also in same .pdf file.
[/LIST]
  **Network Adapters: **

[LIST]
[*]       Realtek RTL8168/8111 PCI-E Gigabit Ethernet NIC (Intergrated)
[*]       Bluetooth Device (Personal Area Network-Logitech USB)
[/LIST]
  **Video MFG/Type/Memory/BIOS Date:**
[LIST]
[*] AMD/ATI ATI Radeon HD 4200  (700 MB Shared) 06/29/09
[/LIST]
**Optical Drives:**
[LIST]
[*]HL-DT-ST DVDRAM GH22NS50
[*]       HP DVD Writer 840b LightScribe
[/LIST]
**Audio Adapter: **
[LIST]
[*]Realtek ALC885/889A/890 @ ATI SB600 - High Definition Audio Controller 7:1 Channel
[LIST]
[*]**Note: I'm only using Two Speakers so can't verify the HD 7:1 Channel.**
[/LIST]
 
[/LIST]
 **Monitor: **
[LIST]
[*]SyncMaster **2233BW**/2233GW/2233BWPlus/2233GWPlus((Digital) [NoDB]  (H9LQ802761) )
[/LIST]
**Keyboard: **
[LIST]
[*]Dell HID USB Device
[/LIST]
**Mouse:**
[LIST]
[*] Logitech HID-compliant USB Unifying Performance MX Mouse
[LIST]
[*]**Note: Some functions are not working but all standard functions work with no problems.**
[/LIST]
 
[/LIST]
**Printer/Fax/Scanner/Copier:**
                    
[LIST]
[*] KONICA MINOLTA magicolor 1690MF
[LIST]
[*]**Note: I have not tried all functions yet but Printing via Network  and USB Connection both work.**
[/LIST]
 
[/LIST]
**Will update if/when anything changes.**

---

### Post by macibookg3 on 2011-03-28
Hi, Name is Jason

I have a Via Motherboard 

Computer ProcessorAMD Athlon(tm) XP 3000+ Memory961MB
Operating SystemUbuntu 10.10      
The X.Org Foundation 
 Audio AdapterVIA8237 - VIA 8237                 Operating System Version KernelLinux 2.6.35-28-generic (i686) Compiled#49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 C LibraryGNU C Library version 2.12.1 (stable) Default C CompilerGNU C Compiler version 4.4.5 (Ubuntu/Lin4.4.4-14ubuntu5)  DistributionUbuntu 10.10     Desktop EnvironmentGNOME 2.32.0
and I have the M-Audio Revolution 7.1 sound card.
Would like to know if any one has gotten it to work with Ubuntu 10.10.  If so please let me know and how they got it to work.  reply to this thread or aim me @ macibookg3

---

### Post by flarkit on 2011-03-31
1)Version Of Ubuntu: 10.10 64-bit
2)Type Of Hardware: Desktop PC (6-months old)
3)Hardware Maker: see below
4)Hardware Model: see below

Motherboard = MSI 890FX-GD70
CPU = AMD Phenom2 X4 965BE rev C
RAM = Corsair Vengeance DDR3-1600 (8-8-8-24)
Graphics = MSI N460GTX 1Gb Cyclone
HDD's = 3x 1Tb Seagate 7200.12
Sound = X-Fi XtremeAudio
DVDRW = LG GH22NS50

The setup runs perfectly well. Compiz, MP3 Audio, networking all work. Only attempted some Diablo2 under Wine, which was fine :P

Dual-booting with Win7 Ultimate 64-bit

---

### Post by Julitokenpo on 2011-04-03
Ubuntu 10.10.Maverick
Processor Intel P4, socket 478
motherboard Biostar P4PM900
Works really good, but it has not graphics acceleration, video card absolutely needed...

---

### Post by TheFool-AK on 2011-04-03
[FONT=Tahoma][SIZE=3]I have a Laptop - Dell D620 that was working great with Ubuntu 10.10 .  I upgraded to 11.04 yesterday.  my 802.11 wi-fi was working fine with 10.10, but is not working with 11.04 . Broadcom DW1390 minicard[/SIZE][/FONT].
[FONT=Tahoma][SIZE=3]
I also hate the gnome 3 interface, but i can work on that later.[/SIZE][/FONT]

---

### Post by race123 on 2011-04-16
I have a DELL D-600 laptop
1.6 
256 ram
ati raidion 9000
egridy os

where can i find compatible drivers

---

### Post by Antarctica32 on 2011-04-16
Ubuntu 10.04 
Desktop
Dell
Dimension 8300

That is with the P4 at 3GHz and the RAM at 2.5GB.
--------------------------------------
Ubuntu 10.04
Desktop
IBM
NetVista M21

I have installed on like 15 of these and I have encountered no problems ever.
--------------------------------------
ubuntu 10.04
Desktop
dell
dimension 4300

For some reason I was unable to install with a CD using the drives I found it with or with USB or with an external USB CD drive. I ended up having to plug in a more modern CD/DVD drive and it worked fine. The fact that the MOBO can only take 512 RAM is a real setback. If it wasn't for that it would be a lot better.
--------------------------------------
Ubuntu 10.04
desktop
dell
dimension 3000

don't think I had any problems with this one.
--------------------------------------
Ubuntu 10.04
desktop
hp
pavilion a630n

works fine with an install by USB
--------------------------------------
Ubuntu 10.04
desktop
Compaq
presario sr1200nx
--------------------------------------
ubuntu lucid
scanner/printer
HP
photosmart premium with ePrint wireless c310a

---

### Post by Antarctica32 on 2011-04-18
um.......
ok

---

### Post by YesWeCan on 2011-04-30
Just upgraded my mobo and uP.

Ubuntu 10.04 64 bit
ASRock P67 Extreme6
i5 2500K uP
Kingston HyperX DDR3 1600MHz RAM
4 disk RAID10 using sata3 ports
Nvidia 6600GT graphics card

Ubuntu was originally installed on the RAID array using my old Gigabyte/AMD mobo. After upgrading the mobo I reconnected the disks and it booted seamlessly. \\:D/

---

### Post by yyka on 2011-05-20
Hi, just want to share my sys info :)

_motherboard_: [COLOR="Red"]Gygabite EP45-UD3LR[/COLOR]
everything works without any problems with every linux that I've used ! 
suspend and hibernate (and recovery from..) is very good, no problems occured. used it with ubuntu since ubuntu 8.04 now with 11.04 (everything between :D) ; and tested  with various linux live cd, all worked.

_CPU_: [COLOR="Red"]INTEL CORE2DUO E8400[/COLOR] (3GHZ) -what to say, one of the best at that time (that is to say 2 years ago :) )

_ram_: [COLOR="Red"]4GO DDR2[/COLOR]

other:
_webcam_: [COLOR="Red"]logitec UVC[/COLOR] webcam 10&#8364; The cheapest ! works with everything (with flash too! for videoconference with service like tokbox or koowy.
Video quality is equal to as that we can have with windows. _*[COLOR="Magenta"]One rule to follow with webcam is to buy UVC standart ( universal video class ).[/COLOR]*_

[COLOR="Red"]apm [/COLOR]_multicard reader_ : of course works out/ob :) 

That's all folks ! bye

---

### Post by Rigved on 2011-06-06
This is my configuration that's been working properly for over a year now...

Version: Ubuntu 10.04 (with latest updates)
Motherboard: MSI P6N SLI V2
CPU: Intel Core 2 Duo E7300 @ 2.66 GHz
Memory: 2 x 2 GB Kingston (in Dual-channel mode)
Hard Disk: SATA II (Total=1.5 TB)
Graphics Card: NVIDIA 9600 GT
Sound card: Integrated MSI Sound Card

Everything works, including the front audio/microphone ports (which do not work in Windows even with the Realtek Audio Drivers).

---

### Post by oygle on 2011-06-06
I was looking for a suitable printer, either HP or Epson, and people on the Ubuntu forums advised to go with HP, as the drivers are open source and do work.

1)Version Of Ubuntu  -  11.04
2)Type Of Hardware  -  Printer
3)Hardware Maker  -  Hewlett-Packard  (HP)
4)Hardware Model - [HP Photosmart Premium e-All-in-One Printer - C310a (CN503A)]("http://h10010.www1.hp.com/wwpc/au/en/sm/WF06b/18972-18972-238444-410635-410635-4023238-4023242.html")

Grabbed hplip-gui from the archives, which is from [HP Linux Imaging and Printing]("http://hplipopensource.com/hplip-web/index.html") , and it all pretty much installed itself, very easy.

It works 100% , fantastic.

Thanks,

Oygle

---

### Post by Ichido on 2011-06-10
Just got a new Cirago External Hard Drive, USB, 320GB for $45.00 on-line from Newwegg.com (USA).

Model; EXTHD 320G|CIRAGO CST1320 R

Comes with Drive in case, Protective Carry Pouch, USB "Y" Cable and a Mini-Disc Not needed for Ubuntu.
Self powered through the USB.
Just plug in the USB and Drag & Drop Files/Folders and it works great:p

---

### Post by FrankCBarela on 2011-06-13
Laptop


Model: Toshiba Satellite 
Processor: Intel Pentium 4 HT 2.1GHz
RAM: 1GB
HDD: Hitachi 100GB 2.7"
DVD: NEC DVD+-RW DL Burner
Graphic: nVidia Go5200

---

### Post by cottfcfan on 2011-06-15
Desktop - HP G5370UK i3550
Runs Ubuntu 11.04 64 bit flawlessly.

The only tweak is to blacklist rt2800pci & rt2800lib in etc/modprobe.d/blacklist.conf, to make wireless work correctly.

---

### Post by Thomas_DEL on 2011-06-15
> **cottfcfan said:**
> Desktop - HP G5370UK i3550
Runs Ubuntu 11.04 64 bit flawlessly.

The only tweak is to blacklist rt2800pci & rt2800lib in etc/modprobe.d/blacklist.conf, to make wireless work correctly.
Thank you very helpful

---

### Post by Gs Dewd on 2011-06-30
Wanted to share my hardware profile for my Ubuntu system.

Version = Ubuntu 10.04 LTS
Mainboard = Epox KRAI-pro mb (via kt880 chipset)
CPU = Athlon xp 3200+
Memory = 2 gb Crucial PC3200 mem
Graphics Card = Visiontek Radeon x1550 XGE
Harddrive = ata133 bMaxtor 80 gb HDD
Optical Drive = Lite-on Cdrw

No issue with any of the on-board devices, (sound, nic, USB, etc)

For wireless net access I am using a Linksys wusb54gc USB WIFI adapter.

Also I did not have to play with any drivers everything has ran straight out of the box since I off loaded the Nvidia geforce fx 5700 I had in here. I dod have nothing but problems with that card under ubuntu. The ati card installed and has ran without a hitch.
System runs Ubuntu a good deal faster then it runs windows xp.

---

### Post by Rytron on 2011-07-09
My [COLOR="Indigo"]*Packard Bell IMedia 5064*[/COLOR] from 2003 works perfectly with Ubuntu 10.04 Lucid Lynx LTS.

---

### Post by trungvkvk on 2011-07-11
Laptop: Toshiba 
Model number: PSA70C RX100E
OS: Ubuntu 9.04 (has run 6.10, 6.06, 5.10)
CPU: Pentium® 4 supporting Hyper-Threading 3.20 GHz
Video: ATI 9100 IGP RS300M, 64MB-128MB shared memory
Screen: 15.4 inch wide (aka short) screen, 1280X800
Sound: ATI IXP AC97 / Realtek ACL202
Modem: ATI IXP AC97 Modem
Ethernet: Realtek RTL8101L
Wireless: Atheros AR5212 802.11abg
Firewire: Texas Instruments TSB43AB21
Cardbus: ENE Technology CB-710/2/4
RAM: 1.0Gb DDR
DVD/CD: Matsushita DVD-RAM UJ-820S, ATAPI CD/DVD-ROM 
HDD: Samsung HM120JC ATA 5400rpm (replaced original Toshiba)
Touchpad: AlpsPS/2 GlidePoint

---

### Post by optimisticyet on 2011-07-16
HP Pavilion t3560.uk (Desktop)
Pentium D 945 3.4GHz, 2GiB memory
Ubuntu 10.04 (Kernel 2.6.32-33-generic-pae; Gnome 2.30.2)

For about 3 months, I have been using an IronKey Personal S200, 2GB ([https://www.ironkey.com/files/datasheets/ironkey-personal-s200.pdf](https://www.ironkey.com/files/datasheets/ironkey-personal-s200.pdf)).

I found the behaviour rather more automatic than suggested by the instructions that came with my IronKey (IK).  Under Ubuntu 10.4 and 11.04, inserting the IK into a USB port automatically produces an entry in the **Places** menu and an **IronKey** icon on the desktop. If your system is configured to automatically open removable media when inserted, then you will also get a Nautilus window with a view of the IK's files.

This instance of the IK is an interim one, a partition that does not contain your secure files. To *unlock* the IK and reach your secure files, open the **linux** folder and then the **ironkey** file within that folder.  This prompts you for your IK password, and after supplying it, you will see your files in the secure partition of the IK. From here on, you can transfer material to and from the IK as you would for any other USB storage device.

When finished, right-click the IK icon on the desktop and select **safely remove drive**. This both *locks* the secure IK partition and then unmounts the IK.

As detailed in the manufacturer's description of the IronKey, the *on-board* applications do not work under Linux. This is not a serious loss for me, since when I've used the IK on the PCs of my local library, the only permitted web browsing is by using the Internet Explorer provided on their Windows XP platform.

Various other functions, such as initialising the IK and changing its password, you must do from a command shell. All this is well described in the IK user guide, but of course a simple graphical interface into these functions for Linux users would be nice: not everyone lives in a command shell.

---

### Post by trungvkvk on 2011-07-18
Hardware: IBM Thinkpad 
RAM: 2048 MB
Ubuntu Version: EDGY EFT

No problems with any services. Everything works out of the box.

---

### Post by DunZH on 2011-07-19
I just got a custom made system, a real cheap box with hopefully enough power.  So far its working great!

Here are the specs:

M4A88TD-M Asus mobo + Athlon II X4 640 with core unlocker, turboV EVO, and crossfireX support

3.0 Gighertz Quad Core
Socket AM3
Southbridge is 880G SB850
2 gigs of memory
Realtec ALC892 
Realtec 8111E

The 850 southbridge is important to avoid the buggy 7.1 or 7.5 southbridge from AMD. I got the best processor I could for the money. I do wish I had gotten a bit better processor, with better caching. This thing has 2.0 MB total cache :|

I had to clear out my alsa and sound settings, but finally the sound is fine.  I used the FGLRX graphics drivers cuz I am just using the on-board video, ATI Radeon HD 4250.  Yeah, the video sucks. Almost seemed like the video driver screwed up the sound, but its all good now. Oh, yeah, this is Natty 11.04.

And I had one weird bug, my time was wrong and the dialog would just crash when I tried to change it.  But that suddenly fixed itself perfectly...

---

### Post by Gs Dewd on 2011-07-25
I Want to update my specs.

Version = Ubuntu 11.04
Mainboard = Epox KRAI-pro mb (via kt880 chipset)
Cpu = Athlon xp 3200+
Memory = 2 gb Crucial PC3200 mem
Graphics Card = Visiontek Radeon x1550 XGE
Harddrive = Maxtor 80 gb ATA 133
Optical Drive = Lite-on Cdrw

No issue with any of the on-board devices, (sound, nic, USB, etc)

For wireless net access I am using a Linksys wusb54gc USB Wifi adapter.

And everything works right out of the box just as it did with the other releases I have used. Very pleased.:P

---

### Post by QsoftStudios on 2011-07-26
Ubuntu version: 10.04
Type Of Hardware: Keyboard
Hardware Maker: Razer
Hardware Model: Lycosa gaming keyboard

Works out of the box just plug it in and thare you go. Only issue I had is that the windows key will not take any key binding but I don't care since I never use it.

---

### Post by Trilogin on 2011-07-29
Ubuntu Version 11.04 Natty Narwhal

Motherboard: ASRock M3A770DE
                       VIA On-board Audio

Processor: AMD Athlon II X3 Rana @ 2.9GHz

RAM: 2x4Gb G.Skill Ripjaws X-Series, DDR3

HDD: Western Digital Scorpio Blue 500GB 
          Seagate Barracuda 7200RPM HDD W/ Win7 (Dual-Boot with GRUB loader)

Video Card: Sapphire Radeon HD 5400

Optical Drive: ASUS DVD-RW +- 

Logitech USB Mouse and Keyboard.

Works just fine =)

---

### Post by victor1234 on 2011-08-03
However, if you search using the model name - HP Compaq Business Desktop  dx2250 you may have more success finding compatible hardware for your  particular model.

---

### Post by kkrueger on 2011-08-09
[B]1)Version Of Ubuntu: Ubuntu 11.04
2)Type Of Hardware: Graphics Card
3)Hardware Maker: EVGA
4)Hardware Model: GTX 560 TI DS


It runs smoothly with slightly less performance than when playing windows games through wine which is expected. Everything else is smooth though.[/B]

---

### Post by Yoast on 2011-08-10
[B]1)Version Of Ubuntu: 11.04  (Standard Dual Boot/Grub alongside Win 7)
2)Type Of Hardware:  Laptop (P6200, 6Gb Ram, 640 Gb Hdd)
3)Hardware Maker:  Acer
4)Hardware Model:  Aspire 5742Z

[/B]

---

### Post by Gs Dewd on 2011-08-14
Ubuntu 11.04
Microsoft Comfort curve keyboard 2000

Works great and all keys function as they should. The web/home key I had to program to use Chrome, which is no biggie.

---

### Post by Gs Dewd on 2011-08-17
Well for kicks and giggles and also I got bored. I built another Ubuntu system out of some old hardware I had laying around.

Version = Ubuntu 10.04
Mainboard = Abit Kt7a v1.3 (via kt133a chipset)
Cpu = Athlon xp 2100+
Memory = 3x256 mb crucial pc133
Graphics Card = Gainward geforce fx 5700 ( waiting for this to act up)
Harddrive = Maxtor 80 gb ATA 133
Optical Drive = Sony cdrw, Lite on DVD
Sound card = Creative Audigy platinum
Using my Linksys wusb54gc USB Wifi adapter for net access.
Everything working great so far. Waiting for the Nvidia graphics card to start acting wonky as I have had no luck with Nvidia cards under Ubuntu. System is also pretty fast.

---

### Post by herdwick on 2011-08-18
1)Version Of Ubuntu - 11.10 alpha 64 bit daily build live CD
2)Type Of Hardware - AMD E-350 based small form factor desktop
3)Hardware Maker - Hewlett Packard
4)Hardware Model - HP Compaq CQ1020UK

Boots up fine, LAN sound & graphics work with default 2D unity desktop / Gnome 3.1.4

Linux ubuntu 3.0.0-8-generic #11-Ubuntu SMP Fri Aug 12 20:23:58 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by dangerboy77 on 2011-08-18
Forgive me if this is a hijack on a different thread but couldnt find anywhere fitting to start this thread as a new one-Please point me in the right direction as this is my first help plea on any forum ever. I need much help with display issues:
G/Card: Geforce4 440 Go 64 mb.  the screen is 3/4 the size of the monitor.   

How do i trouble shoot this issue.

This may be in the wrong thread completely.  I just couldnt find where to go........DONT MAKE ME BEG......PLEase PLEase

---

### Post by majid_karimi59 on 2011-08-18
[http://www.dinodirect.com/laptop-win7-multi-touch-screen-laptop-10-1-inch-n450-1gb-160gb-laptop-laptop-with-wifi-3g-gps-1-30-mega-pixels-10-1-inch-multi-touch-screen-laptop.html](http://www.dinodirect.com/laptop-win7-multi-touch-screen-laptop-10-1-inch-n450-1gb-160gb-laptop-laptop-with-wifi-3g-gps-1-30-mega-pixels-10-1-inch-multi-touch-screen-laptop.html)

i bought this but i like to have a Linux on it but specially windows 7 have too many crash on it specially win using Bluetooth 
mint 11 (Ubuntu 11.04 family) have too many problems about hardware drivers on it specially multi touch screen ability
and Bluetooth and wifi and ... hardware drivers ... 
please help

---

### Post by sleepingdragon on 2011-08-22
OS - Ubuntu 11.04, no special mods.

Medion E4600 DualCore2 Duo @ 2.4Ghz, 2Gb RAM and 500Gb Seagate and 500Gb W.Digital. 

Switched the ATi HD3450 card - (no hope) over to an Asus/nVidia EN210 Silent 512Mb DDR2 running on the 270.xx drivers.

Everything runs 100%, full-screen Flash video is smooth, higher settings possible in 3D games, plus all known desktop compositing modes.

Be warned though, the E4600 has a slightly odd motherboard - the PCI-e slot is next to the 20+4-pin socket, making it a close fit for any graphics card. Bigger cards with large fan arrangements may not fit. Graphics cards with double-height requirements will NOT fit. Since the nVidia 210 has no fan, but came with a double mount plate (don't ask me why), it took five minutes of creative fun with a hacksaw to make it fit - don't try this at home kids!

Also had an issue with the location of the drives being very close to the tower case. Removing the side panel snapped one of my SATA power plugs! Turns out it is part of the case panel runners that gets in the way of the SATA plugs. Again, five minutes with a hacksaw removed the offeding section.

Overall, performance is solid, and makes for a very stable Ubuntu box, but the weird hardware layout can put a few people off.

---

### Post by w1ll1am on 2011-08-22
Version-Ubuntu 10.04.3 LTS kernel 2.6.33 had to install for trim support

Hardware
MB- GIGABYTE GA-970A-UD3 AM3+ AMD 970 SATA 6Gb/s USB 3.0 ATX AMD
CPU- AMD Phenom II X4 955 Black Edition Deneb 3.2GHz
RAM- Corsair XMS 4GB kit 2x2GB DDR3 2000
SSD- OCZ agility 3 60GB / drive
HDD- Wester Digital 7200rpm 320GB /home drive
DVD-RW- lite-on drive
WebCam- HP HD-3100 with ( guvcview )
Bamboo/wacom pen tablet CTH-460
Graphics card- Zotac GeForce GT 440

What works and how I got it to
Everything on the MB works USB3.0
SSD runs quick 
graphics card works great downloaded nvidia driver from their site
bamboo tablet works sometimes had to install a ppa
overall the computer is super fast and runs great.

---

### Post by scottishbloke on 2011-08-25
OS Ubuntu 11.04 ( Natty )
Brand Packard Bell   
Model Packard Bell iMedia B2619uk Desktop PC   
Hard Drive Capacity 160GB  
Processor Type Intel Celeron E1500 Dual-Core  
Processor Speed 2.20GHz  
Ram memory 2GB  
Optical Drive Type DVD Rewriter  
Graphics card NVIDIA GeForce 7050 integrated graphics  
USB port 6  

All works perfectly:)

---

### Post by cfinc on 2011-08-29
OS Version: ubuntu 11.04 (unity not compatible with hardware but everything else works)
 
hardware
cpu: pentium 4 @1.6ghz
ram: 1gb hyundai electronics
gpu: Geforce2 MX 200, Geforce4 MX 4000 or Riva TNT2 M64 (tried all of them)
harddrive: 40gb seagate barracuda
mouse: microsoft optical wheel mouse
keyboard: logitech k120
motherboard: SiS 645
 
my USB 1.1 ports still work!!!

---

### Post by aykayross on 2011-09-03
OS = Ubuntu 11.04 
CPU = Intel Core i7 970 12 core
Motherboard = Asus R.O.G. Rampage III Formula
Graphics = Asus HD 6950 2GB
Memory = 24GB  (6 x Corsair 4 GB, DDR3-2000)
Primary Drive = Corsair 128GB SSD SATA-3
Hardware RAID = RocketRAID 2320
RAID array = 2TB RAID 10 (4 x WD 1TB, SATA-II)
PSU = Cooler Master Silent Pro Gold Series 1000 PSU
Tower = Cooler Master HAF Tower

Everything works except for the hardware raid array. This works in Windows 7 but not in 11.04.

---

### Post by chrissywissy on 2011-09-11
OS Ubuntu 11.04 (dual boot with W7 32 bit)
Desktop
Hewlett Packard s7510
AMD Turion ML-34 1.8 GHz and 1GB RAM
ATI Radeon Xpress 200
 
All seems to work including most peripherals - MS VX webcam and HP C5180 printer
 
The only exception so far is an encrypted data dongle from work which is recognised but won't unlock (yet)
 
My first try with Ubuntu so I'm well pleased - the promised speeed increase is obvious

---

### Post by royal.tarun on 2011-09-25
hi pals
this is my first post in the forum.
i'm not able to use UNITY
on my first boot, a dialog box said that you hardware does not support unity and blah blah blah.


My computer's configuration is as follows:

Intel  motherboard [dunno which version]
GPU: nVidia Geforce 8400 512MB
CPU: Intel dual core processor 2.7Ghz
TVS keyboad and Mouse
2.1 speakers
Samsung LCD monitor 18.5 inch
2GB RAM
320 GB hard Disk

i know that this hardware can easily support unity but its not.
please help me to solve my problem so that i can use unity.
thanx
tarun.

---

### Post by Johnny3 on 2011-10-04
1 year old PC
Asus M4A87TD EVO Bios 1202
AMD x4 955 black(oc to 3.4)
G Skill Ripjaws 4x2GB
Sapphire Radeon HD 5770
Monitor Asus VE276Q
Ever thing work well. But you can't use the additional driver or my monitor will blink. ATI has new drivers but 32 bit and don't feel like trying to force them. Not that good at it. IT looks fine to me.

Have a Canon iP4700 printer works ok. Have to force their drivers and I can't get 4 pictures on a letter size paper.
Hope this helps. using Ubuntu 11.04 64 bit.
Thanks and God Bless Johnny3

---

### Post by Gs Dewd on 2011-10-15
Version = Ubuntu 11.10
Mainboard = Epox KRAI-pro mb (via kt880 chipset)
Cpu = Athlon xp-m 2500+ @ 2.2 ghz (Athlon xp 3200+ speed)
Memory = 2 gb Crucial PC3200 mem
Graphics Card = Visiontek Radeon x1550 XGE
Harddrive = Maxtor 80 gb ATA 133
Optical Drive = Lite-on Cdrw

No issue with any of the on-board devices, (sound, nic, USB, etc)

For wireless net access I am using a Linksys wusb54gc USB Wifi adapter.

And everything works right out of the box just as it did with the other releases I have used. Only thing I had to do was enable open Gl. For some weird reason it wasn't automatically enabled. Very pleased so far. Now I have all my apps and programs installed that i had installed with 11.04 (used the packages backup and reinstall commands)All is well.

---

### Post by theoretical on 2011-11-01
Dell Inspiron 530

Version: Ubuntu 11.10
CPU: Intel Q6600 2.4GHz
Motherboard: Foxconn G33 (stock from Dell)
Memory: 2GB DDR2 800MHz RAM
Graphics Card: eVGA nVidia GT240 DDR3 512MB

Onboard sound and mic doesn't work. Video doesn't work unless you use onboard video and install nVidia drivers.

---

### Post by BuntuSeriously on 2011-11-03
1)Version Of Ubuntu: 11.10 Desktop-i386
2)Type Of Hardware: Printer
3)Hardware Maker: HP
4)Hardware Model: 6940

Perfectly supported --

---

### Post by captainentropy on 2011-11-08
1)Version Of Ubuntu = 10.04 (server + gdm)
2)Type Of Hardware = graphics card
3)Hardware Maker    = NVIDIA/PNY
4)Hardware Model    = 8400GS

verdict = NEVER worked. Many, many, many (wasted) hours trying to get it to work.

However,

1)Version Of Ubuntu = 11.04

verdict = works!

These are two identical cards on two similar Supermicro servers. I'm upgrading to 10.10 on the one server. I'll edit this to indicate whether I ever get it to work.

---

### Post by kensum on 2011-11-11
Ubuntu 11.10
both unity and gnome shell work fine:

1. Biostar Ta870u3+ motherboard
2. Gskill ripjaws 8gig memory
3. Anthlon x4 oc to 3.4ghz
4. Nvidia Geforce Gt 430 video card
 everything was picked up on boot of new board. Sound, mic work fine. No hardware issues to date.

---

### Post by peterthewolf on 2011-11-18
Edimax nano wifi adapter £9.99 from Amazon UK November 2011.

Works out of the box.

Xubuntu 11.04

Self build netbook with Intel D525MW atom motherboard

---

### Post by bobsageek on 2011-11-23
Acer X1930 small form factor desktop, Pentium G620, Intel HD2000 Graphics, 4GB DDR3, 1TB Seagate HDD, Samsung DVD +/-RW, UEFI BIOS. Works like a champ with 11.10 x64, installed from thumb drive been using as my main workstation for one week straight, all hardware functions as expected.

---

### Post by alzie on 2011-12-04
HP p7-1119
Processor Intel® Pentium® G620 2.6 GHz, DMI 5GT/s 
Chipset Intel H61
Memory 4 GB DDR3 

WUBI install of 10.10 went oddly but worked.  Used administrator mode.

I do not use on board WiFi but it detects all my neighbours' so I assume it should be working ;)

I'm not getting proper resolution on my monitor but it is an OLD Daewoo 17" monitor and has always been an issue getting resolution set properly.

All in all seems to be working well.

---

### Post by morningstar.fallen on 2011-12-10
Ubutu 11.10 amd64
GPU (Deskto graphics card) 
Sapphire[SIZE=1]
HD 5450 1GB DDR3 HDMI DVI VGA Out PCI-E Low Profile Graphics Card[/SIZE] (AMD CEDAR - Chip)

Works out of the box with stock ubuntu Gallium 0.4 driver. Do not install the proprietary ATI/AMD FGLRX driver as it decreases the chip's performance and badly affects other apps!

---

### Post by Johnny3 on 2011-12-12
Been working great for over a week on Ubuntu 11.10.
MB ASUS M5A99X EVO
CPU AMD Phenom II X6 1100T Black Edition Thuban
Memory G.SKILL F3-12800CL9D-8GBRL
Video Card PNY XLR8 VCGGTS2501LXPB GeForce GTS 250 1GB 256-bit(looks like they are not making this card anymore.Just got it to use until I can get a little more money)

The only problem is the BIOS time is of buy about 5 hr fast and X sensors don't work. But this is a new MB so it time it will get OK.
Thanks and God Bless Johnny3 65+++

---

### Post by StanleZ on 2011-12-17
Ubuntu / Xubuntu 11.10

Hardware:
intel Q6600 quad core cpu, asus mb P5N32E-SLI Plus, 2 GB Kingston DDR2 ram, nvidia gigabyte 9600 GTX 1GB DDR4, creative Audigy 2 ZS 7.1 + front panel, leadtek winfast PVR2000 TV card, seagate 750 GB sata II hard drive, LG DL DVD-RW combo writer, logitech usb 1200 dpi mouse + usb keyboard, racing wheel logitech G25 usb, 700 W power source.

All components run very smoothly and I´m happy.

---

### Post by Aaron-Mosela on 2011-12-17
I'm about to buy a 13" laptop to run Ubuntu 11.10 and for that sole purpose, ill be doing basic tasks such as web, office like stuff, programming and using hacking tools (This is **ONLY **for **educational **purposes as I will be studying Networks and Security next year and ill have a module is CEH) 

Will Ubuntu 11.10 run on:

Chipset; AMD Fusion Chipset with Integrated CPU/APU
Processor Support; AMD® Fusion Mobile Processor E350 (1.60GHz) 1MB Cache
Memory Type	4GB DDR-III 1333Mhz 
Hard Drive Type	1 x 9.5mm, 2.5” Intel 320 series SSD, SATA 3
Display & Graphics
Graphics	AMD Mobility Radeon™ 6310 - DirectX 11
Maximum Resolution	1366 X 768
 And if so, will it run well. 

I think this is the place to get fastest answer, hopefully someone knows off the top of there head. 

Many thanks to anyone who can help me.

---

### Post by BertN45 on 2011-12-17
Dell Inspiron 1521, AMD64x2, 1.8mHz, 2GB, HDD=320GB
Ubuntu 9.04-> 9.10-> 10.4 -> 10.10 -> 11.04 -> 11.10
Problems with Broadcom wifi, solved by using the open source drivers and removing the recommended company drivers.

Dell Lattitude CSX500XT, PIII, 500mHz, 384MB, HDD=40GB from 11/10/2000
Lubuntu 11.10
Sound driver issues with Xubuntu 11.10 not with Lubuntu, related to the sequence in which the sound and X video drivers are loaded. The sound chip seems to use a part of memory reserved for video.
Fine for FaceBook and YouTube 

Siemens Scovery 450, PII, 400mHz, 384MB, HDD=13GB
Ubuntu 10.04-> Ubuntu 10.10
Sound driver issue
Fine for FaceBook, too slow for YouTube
SOUND PATCH file content:
  # put this file in /etc/modprobe.d
  # add driver name snd-cs4232 to the file /etc/modules
  options snd-cs4232 isapnp=0 port=0x220 cport=0x0120 irq=11 dma1=1 dma2=3

HP Compaq d530SFF, P-IV, 3gHz multi-threaded, 1.5GB, HDD=250GB
Ubuntu 10.04-> Ubuntu 10.10-> Xubuntu 11.04
Did not work with Ubuntu 11.04 due to video problems with Unity.
Currently powersupply defect.

IWILL ZPC64 AMD Athlon 64 3300+, 512MB, HDD=40GB
Xubuntu 11.04
Power switch defect

ASUS eeePC 701, Celeron, 630mHz, 512MB, SDD=4GB without SWAP Partition. 
Used with an external 15" LCD screen and 40GB USB HDD.
Ubuntu 9.04 Netbook
Supports video. 
Given away.

---

### Post by SycloneMedia on 2011-12-29
My new super build: Everything is top-of-the-line, new and worked right out of the box!

Kubuntu 11.10 64bit

+ Case: ThermalTake Level 10 GT
+ Power Supply Unit: Cooler Master Silent Pro Gold 1000W
+ Processor / Cooler: Intel i7-3930k, Corsair Hydro H100
+ Motherboard: Asus P9X79 WS
+ RAM: 64GB GSkill Ripjaws Z-Series
+ SSD: 180GB Corsair Force GT Sata3
+ Hard Drives: Seagate Barracuda 3TB Sata3
+ Video Card: AMD/ATI FirePro V4900
+ UPS: CyberPower Pure Sinewave 1500VA/900W
+ Keyboard: Logitech K800 Wireless Slim Illuminated
+ Mouse: Logitech M570 Wireless Laser Trackball
+ Optical Drives: 2 x LG 12X 3D LightScribe Blu-ray Rewriter, 1 x Lite-On LightScribe DVD Rewriter
+ Printer: HP LaserJet 100 Color MFP M175NW networked off the E3000
+ Router: Cisco Linksys E3000
+ Webcam: Logitech HD Pro C910
+ Bluetooth receiver: MediaLink 3.0+HS Class 2 Model MUA-BA3
+ Monitors: 2 x Dell 23" U2312HM using dual DisplayPorts from the V4900 Firepro card.

Simply awesome.

:guitar:

---

### Post by sleepingdragon on 2011-12-30
LG E2211 21.5" Monitor

Connection type D-BUS (VGA).

Nice colours, resolution switchover from my older monitor was flawless (nVidia GT210). 

Works perfectly.

---

### Post by Fraoch on 2012-01-16
I'm not going to post all my hardware as it's old and out of production, but I will post something I got as a gift two days ago:

- Logitech MK520 wireless mouse/keyboard combo

It works just about perfectly* in Ubuntu Linux 11.10 32-bit.  No drivers to download, no configuration required, just plug and play.  And both the mouse and keyboard are quite nice.

Even the extra and multimedia keys on the top work almost perfectly.

* well 3 of the six multimedia keys should work but don't: the play, previous track and next track buttons.  They're trying to do something as a big "no" symbol comes up on the screen but I can't configure them.  I'll make a forum post but this issue is quite minor.

---

### Post by linfidel on 2012-02-01
> **Fraoch said:**
> 
* well 3 of the six multimedia keys should work but don't: the play, previous track and next track buttons.  They're trying to do something as a big "no" symbol comes up on the screen but I can't configure them.  I'll make a forum post but this issue is quite minor.
FWIW, I've gotten that on some music players, but not others.  For example, my multimedia keys don't work with VLC, but work fine with Banshee.

---

### Post by Ioana-Karina on 2012-02-03
Ubuntu 11.10 64-bit Unity
Motherboard: MSI G41M-P26
CPU: Intel Pentium Dual-Core E5700
Memory: 3 GB DDR3
Graphics: ATI Radeon HD 5450
Works perfectly.

---

### Post by CivilizationII on 2012-02-17
For Ubuntu 10.04.4 and Ubuntu 12.04 test

Motherboard: Gigabyte GA-P43-ES3G  release 1.1

Memory       : 12G (Micron + Kingmax)

HDD             : 4 various Western Digital SATA2

DVD             : Samsung SH-S223L

---

### Post by dave0109 on 2012-02-18
Xubuntu 11.10 Oneiric Ocelot

Motherboard: ASUS P8Z68-V Pro/Gen3  [1]
CPU: Intel Core i5 2500K 3.3GHz
RAM: Corsair Vengeance 4GB DDR3
Hard Disk: WD Caviar Blue 500GB SATA 6GB/s
Optical: Pioneer DV-RS19LBK DVD+/-RW DVD-RAM
Network: Addon 300Mb/s Wireless N PCI card  [2]
Printer: Canon Pixma ip4200

[1]
Audio was crackly for some applications, such as VLC and Skype.  The motherboard has a HDA Intel sounds card and after a couple of false starts, I got it working by setting the second position fix, as detailed in [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting).

[2]
Wireless did not work with Xubuntu's default driver, the Ralink rt2800pci.
After moving the machine to the router and hardwiring them together, I followed the instructions at [http://ubuntuforums.org/showpost.php?p=11624707&postcount=4](http://ubuntuforums.org/showpost.php?p=11624707&postcount=4), which worked.  Note that the source code linked in there, is a copy of the code available from the Ralink support site at [http://www.ralinktech.com/en/04_support/license.php?sn=5019](http://www.ralinktech.com/en/04_support/license.php?sn=5019).  The difference is that the config has been pre-modified, as per Ralink's suggestions.

---

### Post by Lee_Bo on 2012-02-22
Ubuntu 11.10 64 bit
Dell Optiplex 745 (4 gig ram)
ATI Radeon HD 2400 XT

Smooth install and operation.  Unity runs great.

---

### Post by Fraoch on 2012-03-06
My old WD Raptor hard drive was failing (it almost went completely a few days ago) and I wanted to upgrade to an SSD but my motherboard with its rather unique VIA SATA I controller couldn't handle a new SATA III device.  Yes, they're supposed to be backwards-compatible but this is the only controller that isn't.

So I got a new(ish) motherboard along with a new SSD.  I installed Ubuntu 11.10 on it, it's now running fine:

MSI G31TM-P21
Crucial M4 64 GB SSD

This works great as an OS drive, there's lots and lots of space - still about 55 GB free!  Incidentally it's also very very fast even on the SATA II controller on this board.  Splash screen to desktop...5 seconds.

I'm very pleased.

---

### Post by fmpconsult on 2012-04-09
Philips webcams have been nice with my Dell L520 with Ubuntu 10.10!

[LIST=1]
[*]**Version Of Ubuntu: **Ubuntu 10.10, with Macbuntu theme
[*]**Type Of Hardware: **webcam
[*]** Hardware Maker: **Philips
[*]** Hardware Model: **SPZ2000 and SPC900NC
[/LIST]
 Both has worked flawlessly out-of-the-box with Ubuntu 10.10, with Cheese, Skype and Flash +10. I only had to add the _env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so_ before the commands, but it was a single modification to the menu and it was all. I have used gstreamer-properties to test the cams, which also worked at once, no frills, from the first time (with the benefit of telling me they were V4L1/L2 compatible.)

Although I have tested those webcams with a Dell L520, they also worked fine with Brazillian local makers Positivo and Itautec, both with Ubuntu 10.04.

---

### Post by David Vincent-Jones on 2012-04-12
I have an HP Pavilion Model a6113w Product GC658AA-ABA that runs well with Ubuntu 11,10 32 bit.
Could this machine also run the current 64 bit O/S version?

---

### Post by MonkeyPaw on 2012-04-13
This was a huge pain, but I'm finally here on a Llano APU!

Version: 12.04 LTS AMD64 (beta 2)
CPU: AMD A8-3850
Mobo: ASUS F1A75-M LE

[How I did it thread.]("http://ubuntuforums.org/showthread.php?p=11842344#post11842344")

---

### Post by DunZH on 2012-04-21
Just put together two comps with the same specs, everything is running great on 10.04:

Mobo:                GIGABYTE GA-970A-UD3
CPU:                  AMD Phenom II X4 955 Black Edition Deneb
RAM:                 6 GB Kingston
Video Card:       GeForce GT 430

Downloaded the video driver direct from nvidia website, works great, downloaded the realtek driver from their site, was a piece of cake, clear audio.

At first I tried to install 11.10, and it did NOT install at all, the installation hung consistently at one point.  I don't know why, and I hope that I can install 12.04 later, after they get most of the bugs worked out of it. But thats not a big worry for me.

This is a fairly cheap system and very fast, I overloaded the RAM to be sure it would fly using the pae kernel.

---

### Post by motorcity909 on 2012-04-22
Xubuntu 11.10

Thought I'd add my new webcam to this list.  Own brand from Asda (Walmart).  

Princely sum of £7.95 for 1300k pixels and built in mono-microphone.

Video fine on Camorama webcam viewer

Video & Audio works fine in [http://meetings.io/](http://meetings.io/) and [http://tinychat.com/](http://tinychat.com/) 

Video fine on Google+ Hangouts but no audio - a quick Google reveals a number of users having same issue.

Haven't got Skype so not checked.

Also, all hardware in my sig below works fine.

Cheers
Dave :p

---

### Post by forbidden404 on 2012-04-28
Version: Ubuntu 12.04
Type of Hardware: Intel® Core™ i5-2430M CPU @ 2.40GHz × 4; DDR3 6GB, AMD RADEON 4670M; Intel HD Graphics 3000; 
Hardware maker: Dell;
Hardware model: Inspiron 15r

---

### Post by imac_89 on 2012-04-29
Version: Ubuntu 12.04 64-bit
Hardware: MB,             CPU,           GPU
Maker:    Gigabyte,       Intel,         nVidia (EVGA)
Model:    GA-Z68A-D3H-B3, Core i5 2500K, Geforce 560 Ti 448

---

### Post by Logan 1229 on 2012-04-29
Ubuntu 12.04

  Installed:

 "Creative I/O PCI Serial ATA Host Controller Card" 
  Model SA3114

to increase number of installed harddrives.  Worked instantly without requiring special drivers.

  Haven't tested the card's RAID ability as not required.

---

### Post by djb6 on 2012-05-13
Lubuntu 12.04 installed:

Medialink MWN-USB150N Wireless N Adaptor worked right out of the box.  Plugged it in, and it fired right up.

---

### Post by patrickceg on 2012-05-14
Please Only List
1) Ubuntu 12.04
2) Motherboard / GPU
3) Intel / nVidia (Dell)
4) DP67DE + Core i5 2500k overclocked / GeForce 7900 GS

This hardware worked straight out of the install. Also of note is that the motherboard's temperature and fan speed sensors all work as well with lm-sensors.

---

### Post by n2uad on 2012-05-23
[B]
1)12.04 Ubuntu
2)Intel DH77EB motherboard
3)[/B]** Intel i7-3770S CPU**
[B] 4)Gigabyte Nvidia GTX 550ti graphics card

Works Great!
Using allot of graphics crashed the system. The graphics card solved that problem.


[/B]

---

### Post by jmore9 on 2012-05-25
1 - Ubuntu 12.04LTS
2 - Motherboard
3 - MSI
4 - 848P Neo-V

Upgraded my motherboard from 1.8gig cpu to 3.2gig cpu.  Used the above board.  Installed it and had to make no changes to Ubuntu 12.04 LTS already installed.  Works as expected.

---

### Post by GreggC on 2012-05-27
Re: Desktop Hardware Compatibility List.
1 - Ubuntu 12.04LTS - 64bit
2 - Motherboard (dell studio XPS 435T)
3 - Intel(R) Core(TM) i7 CPU 920 @ 2.67GHz 1600.00MHz
4 - AMD Radeon HD 6870 (sapphire)

I had issues with the HD 6870 drivers
The system would hang on shutdown until latest driver from AMD was installed, 
After the last update, I could not boot into GUI until driver was removed and replaced with driver in Ubuntu repository.

Everything seems to be working well as of yesterday.

---

### Post by chrissywissy on 2012-05-30
OS Ubuntu 12.04 business remix (dual boot with W7 32 bit)
Desktop
Hewlett Packard s7510
AMD Turion ML-34 1.8 GHz and 1GB RAM
ATI Radeon Xpress 200

All seems to work including peripherals - MS VX webcam, HP C5180 printer and an encrypted data dongle from work which wouldn't unlock on 11.04

---

### Post by Fraoch on 2012-06-15
1)Version of Ubuntu: 12.04
2)Type of hardware: USB 3.0 - IDE/SATA hard drive adapter
3)Hardware maker: Vantec
4)Hardware model: CB-ISATAU3

At first I posted this in the incompatibility list since when I initially plug it in it does not work.  However after some extensive testing I can get it to work: plug the USB cable in, power up the drive, unplug and replug the USB cable.  After that it works fine provided the power is maintained.

Works all the time in USB 2.0 mode, in USB 3.0 this little rain dance is required.

---

### Post by martinr on 2012-06-16
1)Version Of Ubuntu: 12.04 LTS amd64
2)Type Of Hardware: Desktop (small form factor)
3)Hardware Maker: Acer
4)Hardware Model: Veriton X4610G

Note: install the Live CD with a non UEFI boot sequence (F12 during POST) or switch off UEFI boot devices in the BIOS.

---

### Post by jmore9 on 2012-06-18
1) Ubuntu - 12.04 lts
2) Pc dual core p4 3.2gig - Nvidia graphics
3) Samsung
4) ML 2525



1) Ubuntu - 12.04 lts
2) Pc dual core p4 3.2gig - Nvidia graphics
3) Cannon
4) N650U usb scanner

---

### Post by Rytron on 2012-06-18
> **jmore9 said:**
> 1) Ubuntu - 12.04 lts
2) Pc dual core p4 3.2gig - Nvidia graphics
3) Samsung
4) ML 2525

Are you saying the **Samsung ML 2525** is fully compatible with GNU/Linux or do you refer to the **Samsung ML-2525[COLOR="Red"]W[/COLOR]**?

---

### Post by thom_ on 2012-06-21
> **TerryMasters said:**
> Version: Ubuntu 12.04 64-bit
Manufacturer: Samsung
Model: Series 7 Chronos (Nike) NP700Z7C-S01
Specs: Intel i7-3615QM Ivy Bridge CPU, 8GB DDR3, Intel HD 4000/nVidia 650m 2GB Optimus GPU with HDMI and Mini DisplayPort, 1TB HDD, 1.3MP Integrated Webcam + Mic, Intel Advanced-N 6235 802.11 a/b/g/n WiFi + Bluetooth 4.0, USB 3.0


Everything seems to work out of the box with 2 minor exceptions:


1. The display is corrupted with graphical artifacts on boot - [http://i49.tinypic.com/4l4l6a.png](http://i49.tinypic.com/4l4l6a.png) - but resolves itself after switching resolutions then reverting back. Sometimes requires more than one attempt (have not tested Bumblebee).

2. The WiFi card stops working and is unable to recover after going into standby.


Hope this helps!

OS : Ubuntu 12.04
Maker : ASUS
Model : A43E-VX389D

Everything is just fine, but the monitor. As TerryMasters' prob, I often got my monitor be like this [http://i.imgur.com/HFksc.png]("http://i.imgur.com/HFksc.png") or [http://i.imgur.com/5wo55.png]("http://i.imgur.com/5wo55.png")

But it can be solved by maximizing the window, and revert it back (restore). If the error stay still, I just do maximize-restore till it's gone.

---

### Post by Bucky Ball on 2012-06-29
Compaq 610 laptop;
Ubuntu 10.04 LTS;
Logitech MK260 wireless keyboard/mouse combo.

Plugged the Logitech wireless keyboard/mouse combo USB dongle into the laptop and the keyboard and mouse were immediately recognised and operational, no drivers or tweaking required. They just worked 'out of the box'. ;)

---

### Post by Raphial Hebert on 2012-06-30
Ubuntu 8.04, 9.04, 9.10, 10.04, 10.10, 11.04, 11.10 (32Bit)
Ubuntu 10.10 (64Bit)
CPU: AMD Phenom II 550 3.5GHz Dual Core
Motherboard: ASUS M4A78-PLUS AM2, AM3, AM3+ (Crossfire Support)
GPU: EVGA Nvidia GeForce 8800 GTX 768MB @800MHz, PNY Nvidia GeForce 8400 GS 512MB @600MHz
RAM: 8GB DDR2 @1066MHz
HDD: SATA WD 650GB 7200 RM 32MB Cache (Detects my other 5 HDD with no problem)
WiFi: NETGEAR WPN111v3 (No longer in use)

I have had little to no problem with Ubuntu on this set up. I also have a small server setup:

Xubuntu 10.10, Ubuntu 10.10
CPU: Intel Pentium4 1.8GHz Single Core
Motherboard: Dell Dimension 2xxx series
GPU: PNY Nvidia GeForce 6100 LT 268MB @300MHz
RAM: 2GB DDR1
HDD: IDE WD 250GB 7200RPM 2MB Cache

---

### Post by Bucky Ball on 2012-06-30
@Raphial Hebert: Everything up to and including 10.10 (apart from 10.04 LTS) has reached end of life and no longer supported. 11.04 only lasts until October. Perhaps not great having a no longer supported release on a server. LTS releases are best and advised for server and production machines.  ;)

---

### Post by Raphial Hebert on 2012-07-02
> **Bucky Ball said:**
> @Raphial Hebert: Everything up to and including 10.10 (apart from 10.04 LTS) has reached end of life and no longer supported. 11.04 only lasts until October. Perhaps not great having a no longer supported release on a server. LTS releases are best and advised for server and production machines.  ;)

I am fully aware that these, below 11.04, are officially unsupported, but I really dislike Unity, and the Gnome desktop on these versions are completely different, making these distros really inconvenient for me, as well as a lot of others I've noticed.

---

### Post by EmmaS22 on 2012-07-05
Running Linux Ubuntu  12.04 (64bit) 

Specs: 
1.Intel Pentium Dual Core E5200,2x2.5Ghz
2.MB : Gigabyte G31M-ES2C
3. Kingmax ,ddr2, 4gb dual channel 
4.HDD Hitachi 250gb
5.Powercolor Radeon HD4850 PCIE,512mb,ddr3 

Running great:)  ;)

---

### Post by Dr_Muesli on 2012-07-10
> **Bucky Ball said:**
> Compaq 610 laptop;
Ubuntu 10.04 LTS;
Logitech MK260 wireless keyboard/mouse combo.

Plugged the Logitech wireless keyboard/mouse combo USB dongle into the laptop and the keyboard and mouse were immediately recognised and operational, no drivers or tweaking required. They just worked 'out of the box'. ;)

And the numeric-pad?  I also use 10.04 on a Packard Bell I5 desktop, but the numeric-pad just moves the cursor no matter if I press numlock on or off....:confused:
When I log in, the numeric-pad seems to generate the numbers well, but after login, the numeric-pad doesn't work except for moving the cursor.

Maybe someone has a bright idea what to do???

Erik

---

### Post by Bucky Ball on 2012-07-10
@Doctor_Muesli (who no doubt had a healthy breakfast! ;))

Never tried the numeric pad. I'll have a go later and let you know.

---

### Post by mmca on 2012-07-19
[B]
Ubuntu 12.04 (64bit)
CPU - intel core i5 2320 @3.0GHz
MotherBoard - Gigabyte H61N-USB3
Graphic AMD Radeon HD6770
[/B]

---

### Post by Icarus315 on 2012-07-27
WebCam Logitech c510

Tested in Ubuntu 12.04 64-bit.

Status: works fully.  Was having audio sync issues with Cheese but guvcview works absolutely fine with it.  Didn't trouble-shoot Cheese, perhaps the audio sync issue could be worked out there.

In gstreamer-properties it is detected and used as a Video4Linux2 device and I'm pretty sure the webcam just follows the UVC standard.

Both video and audio from the device are fine.

Installed Skype 4.0.0.8 64-bit from its official web site and both the webcam's video and audio worked correctly with no additional configuration on my part in a call to a Windows XP machine.

---

### Post by MarceloG on 2012-08-15
1)Version Of Ubuntu: 12.04 with Unity desktop (32bit) 
2)Type Of Hardware: Graphic Card
3)Hardware Maker: Nvidia
4)Hardware Model: GeForce 6200

Supports Unity 3D.

---

### Post by cowbell40 on 2012-08-20
Version: 12.04 LTS Precise Pangolin
Processor: Intel Ivy Bridge i7 3770k
Motherboard: ASUS Maximus V FORMULA Atx w/ Intel Z77 Chipset

Everything worked great right out of the box except for the Intel onboard graphics - they took a little convincing but now run great.

---

### Post by Random20210831 on 2012-08-23
OS: Ubuntu 12.04 LTS 64-bit
Type of hardware: Headphones
Hardware maker: SONY
Hardware model: MDR-CD370

All works perfectly.

OS: Ubuntu 11.10 64-bit
Type of hardware: Graphics card
Hardware maker: Nvidia
Hardware model: 6600

Supports Unity 3D, and work perfect.

---

### Post by Random20210831 on 2012-08-23
OS: Ubuntu 12.04 LTS 64-bit
Type of hardware: Wirelles Mice
Hardware maker: Genius
Hardware model: Ergo 9000

Work perfect, but not support special buttons, and special button for 3D view are moving back webpages or closing it.

---

### Post by martinr on 2012-10-05
1)Version Of Ubuntu: LUbuntu 10.04 LTS
2)Type Of Hardware: Desktop computer ATX
3)Hardware Maker: AOpen
4)Hardware Model: AX5T

Everything works except for APM nor ACPI power management.

---

### Post by mörgæs on 2012-10-12
Dell Optiplex gx150 (Intel Celeron 1 GHz, 512 MB memory, from 2001).

Everything works with Lubuntu 12.04 when using the alternate ISO.


First the [BIOS]("http://www.dell.com/support/drivers/us/en/19/DriverDetails?driverId=R89211") should be upgraded to A11.

During installation some combinations of [boot options]("https://help.ubuntu.com/community/BootOptions") are needed, for example *nolapic* and *acpi=off*. This is done from the F6-menu.

After installation: If you see a garbled screen after applying all updates and rebooting, the boot options can be replaced with 

```
GRUB_CMDLINE_LINUX="vga=791"
```

(more about VGA codes [here]("http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers")). Don't be afraid of editing the GRUB 2 configuration, it is no big deal.


The computer does not serve any useful purpose by today's standard. Installing was mostly done for the challenge of it.

---

### Post by Parker32 on 2012-10-15
Is there a Hardware Compatibility List for SLED somewhere? I think I saw
someone link it once but I can't find it. I'm specifically interested in
printers and scanners. (I.e. if someone buys [device] is it going to
work or cause me no end of grief.)

I found this 'NOVELL: Partner Product Guide: SUSE Linux Enterprise
Desktop' ([http://www.novell.com/partnerguide/section/676.html](http://www.novell.com/partnerguide/section/676.html)) but
that's not really any use since there's only one printer listed there.
(I guess hardware's only going to get YES certification if the
manufacture makes the effort to get it and most won't.)

I found this 'HCL:Scanners - openSUSE'
([http://en.opensuse.org/HCL:Scanners#Scanjet_3970c](http://en.opensuse.org/HCL:Scanners#Scanjet_3970c)) but it only refers
to openSUSE and is inevitably far from definitive.

---

### Post by dwb814 on 2012-11-03
Version Of Ubuntu: Ubuntu 12.04.1 desktop amd64 LTS
---------------------

Type Of Hardware: 3.5 Inches USB 2.0 4 PORT INT/EXT DUAL HUB BAY [Genesys Chipset]

Hardware Maker: Iocrest

Hardware Model: SD-U2HUB-4

Link to product image:
[http://www.amazon.com/gp/product/B001UJLZ36/ref=fb_lfb_prodpg_0](http://www.amazon.com/gp/product/B001UJLZ36/ref=fb_lfb_prodpg_0)
---------------------

You will need a Internal USB TYPE-A or you can run the cable through to the back ports. Also, you will need a floppy drive power connector. I also bought a: 
---------------------

Type Of Hardware: NEC 5 PORT USB 2.0 PCI CARD ADAPTER (4 external ports plus 1 shared internal port)

Hardware Maker: NEC

Hardware Model: UPC 844660002840

Link to product image:
[http://www.amazon.com/NEC-ADAPTER-external-shared-internal/dp/B004C4ZTFQ](http://www.amazon.com/NEC-ADAPTER-external-shared-internal/dp/B004C4ZTFQ)
---------------------

For more USB ports and to hook up the hub. Both work OUT-OF-THE-BOX. If you look around you can buy the whole setup for about $17.00 delivered.

---

### Post by dwb814 on 2012-11-03
Version Of Ubuntu: Ubuntu 12.04.1 desktop amd64 LTS
---------------------

Type Of Hardware: Motherboard

Hardware Maker: Asrock

Hardware Model: N68C-GS FX AM3+ NVIDIA GeForce 7025 / nForce 630a mATX

Supports AM3+ Processor, 8-Core CPU
Supports Dual Channel DDR3 1600 / DDR2 1066
Integrated NVIDIA® GeForce 7025 graphics, DX9.0 VGA, Pixel Shader 3.0
Gigabit LAN 10/100/1000 Mb/s
5.1 CH HD Audio (VIA® VT1705 Audio Codec)
Supports ASRock XFast RAM, XFast LAN, XFast USB Technologies
Supports ASRock Instant Boot, Instant Flash, OC DNA, APP Charger 

Link to product:
[http://www.asrock.com/mb/NVIDIA/N68C-GS%20FX/]("http://www.asrock.com/mb/NVIDIA/N68C-GS%20FX/")
---------------------

Type Of Hardware: Memory

Hardware Maker: Kingston

Hardware Model: 8GB (2 x 4GB) DDR3-1333MHz PC10666
---------------------

Type Of Hardware: Processor

Hardware Maker: AMD

Hardware Model: Sempron 140 2.7GHz Socket AM3 45W, Dual Core, 2.7GHz, 64-bit
---------------------

Note: I used the "additional hardware" in system settings to install the driver for the "NVIDIA GeForce 7025 / nForce 630a mATX" video card. I used the "NVIDIA accelerated graphics driver (post-release updates) (version current updates)


Other than that, no issues what-so-ever, installed the hardware, set the BIOS, installed Ubuntu, and I was done.

---

### Post by s9032g@comcast.net on 2012-11-03
Ubuntu 12.04  Dell mini 9

Edimax EW-7622UMn 802.11b/g/n (Realtec) wireless receiver is a USB plug in. Works like a charm. Strong signal Good backup for those times when a new Ubuntu release lacks wireless function w/o intervention.

---

### Post by NewAmercnClasic on 2012-11-12
Ubuntu 13.04 AMD64 (Daily Build)
Processor: Intel Core i7-3770K Ivy Bridge 3.5ghz (3.9ghz turbo) LGA 1155 77W Quad-core (w/ hyper threading)
Mobo: Asus Sabertooth Z77 LGA 1155 Intel Z77 HMDI Sata 6gb/s USB 3.0 ATX
PS: Corsair 650W
Ram: Corsair Vengeance 32GB (4x8gb) 240-pin DDR3 1600
HD: Seagate 1x500GB+1x2TB
Mouse: USB Microsoft (fold-able) Wireless
Keyboard: USB HP Elite Wireless
(Perfectly working hardware profile with stellar results)
VideoCard: Radeon HD 5700 (Proprietary drivers are NOT working well with unity OPENGL, however Open Server drivers work fine) and I will be looking for a Nvidia equivalent to solve this issue.

I also have a TrendNET wireless USB Ethernet dongle and USB bluetooth (which are running subpar, and have intermitten connection problems, bluetooth seems to be related to distance strength and human in-direct physical interference).

---

### Post by VooDooSyxx on 2012-11-15
Version: Ubuntu 12.04.1 LTS 64bit

Zotac Zbox Nano XS AD11
[http://www.zotac.com/index.php?page=shop.product_details&flypage=flypage_images-SRW.tpl&product_id=450&category_id=148&option=com_virtuemart&Itemid=100266&lang=en](http://www.zotac.com/index.php?page=shop.product_details&flypage=flypage_images-SRW.tpl&product_id=450&category_id=148&option=com_virtuemart&Itemid=100266&lang=en)

Processor:  AMD E-450 APU
Video: ATI Radeon HD 6320
Audio: ATI Radeon HD 6250/6310 HDMI
RAM: 1 x 8GB G.Skill SO-DIMM @1333Mhz (spec says 4GB max, but it  does support 8GB)
Storage: 120GB Mushkin mSATA SSD
Ethernet: Realtek RTL8111/8168B Gigabit Ethernet
Wifi: Realtek RTL8188CUS USB 802.11n

----
Monitor: Hanns-G HL248 24" @1920x1080
Keyboard / Mouse: Logitech K260 wireless combo

Everything works perfectly running Unity with full 3D acceleration and no issues. Used additional drivers to install the fglrx driver for the ATI integrated graphics. Also added the line below to /etc/pm/config.d/config to properly handle the usb wifi module when suspending. 

SUSPEND_MODULES=rtl8192cu

---

### Post by Psychobudgie on 2012-11-16
Version : Ubuntu 12.10 32bit

Processor : AMD FX-4100
MOBO : Asus M5A78L-M LX V2
Memory : Corsair 8GB (2x4GB) DDR3 XMS3 1600Mhz DIMM CL9 1.65V
Lite-On DVD RW/CD RW SATA Drive
Storage : Seagate 7200rpm SATA 320gb and External USB 2.0 320gb.
Video : Palit Nvidia GTX 650 1gb

Everything works as it should. No issues. Using Nvidia Experimental Drivers 3.10 via official repo.

---

### Post by 1204 on 2012-12-04
Version : Ubuntu 12.04 LTS 64bit

Processor : AMD A4-5300 (FM2) 3.4 GHz, TDP 65W
Video : AMD Radeon HD 7480D integrated
MOBO : Asus F2A55-M (FM2)
Memory : Kingston HyperX 8GB 1600MHz DDR3 CL9 XMP (2x4GB)
Lite-On DVD RW/CD RW SATA Drive
Storage : Seagate 7200rpm SATA 500gb

Works flawlessly, using [AMD Catalyst 12.10 drivers]("http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29"). I don't know if there should be, but no problems with UEFI bios either, it just booted right away to GRUB.

---

### Post by tlhIngan on 2013-01-04
Lubuntu 12.04
ASUS A7V8X-X motherboard
ATI Radeon 7500 (RV200 GPU) with 64 MB
AMD Athlon XP 2000+
2 GB system RAM

Had to use the alternate installer, and had to down grade to an older version of Adobe Flash (this old CPU doesn't support SSE2, Flash requires it starting with version 11.2)

---

### Post by tlhIngan on 2013-01-04
Lubuntu 12.10
Dell Dimension 3000
Intel Celeron 2.6 GHz
2 GB system RAM
Integrated Intel Extreme Graphics 2

Everything works fine as far as I can tell.

---

### Post by Calinou on 2013-01-06
Xubuntu 12.10
Intel i7-2600K -- 12GB RAM DDR3 -- NVIDIA 570GTX -- 2TB HDD

Runs fine, everything works, using the 304.51 NVIDIA proprietary driver. Nouveau works but is slower.

---

### Post by Laiquendi on 2013-01-18
Ubuntu 12.10 (and 12.04 earlier)

Typical tower, self-build mostly on Gigabyte pieces:
**CPU:** Intel Core i5-2310, 2.9GHz, 6MB;
**Motherboard:** GIGABYTE GA-Z68A-D3-B3;
**RAM:** Viper Xtreme Series Division 2, 2x4GB, DD3-1866MHz;
**HD:** WD Caviar Green, 1TB, 7200;
**Graphics:** Gigabyte GeForce GTX 460 1024 MB DDR5;

nVidia on proprietary driver 310.

_Works like a charm... :)_

---

### Post by dominictorreto87 on 2013-01-21
Ubuntu 12.10

SilentumPC Regnum Tower
CPU:Intel Corei7 3770k
Motherboard:Gigabyte DS3H-Z77-B3
Bios ver.F10f(before many problems)
Ram Memory: 4x4GB Kingston HyperX 1600MHz Blue
HD:OCZ Agility 3 120GB + Segate barracuda 2TB
Graphics:MSI Geforce GTX 560TI 1024MB DDR5

Nvidia on Nouveau works but sometimes during start shows errors and needs restart.

---

### Post by 1204 on 2013-01-24
> **1204 said:**
> Processor : AMD A4-5300 (FM2) 3.4 GHz, TDP 65W
Video : AMD Radeon HD 7480D integrated
MOBO : Asus F2A55-M (FM2)I got questions about this setup so let's put it here too. You can watch 1080p videos and also HD videos on Youtube, Vimeo etc. Remember to use AMD binary drivers and also VA-API (gpu video acceleration). 3.2 and 5.2: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

You can also play games fairly well like Minecraft, Legend of Grimrock etc. All I can say this A4 is very impressive to it's price. Very silent as well because of low power consumption.
------------------------------
Got questions about this via PM, so yes, it's better than you may easily think of. You also get nice gpu performance boost the faster ddr3 ram you use. Gaming perrformance for example Mafia 2, Driver, Skyrim (not my video, and this A4-4300(FM1) is slower than A4-5300 (FM2)): [http://www.youtube.com/watch?v=eGLeZOSvsNk](http://www.youtube.com/watch?v=eGLeZOSvsNk)

---

### Post by Bartender on 2013-02-17
HP dc7800 Convertible Mini-Tower Business PC

Ubuntu 12.04

I don't want to talk about the dc7800 so much as what I added to it.  I wanted to modernize the unit and make data transfers between HDD's more convenient.

Bought a [Kingwin KF-253]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817990016") from newegg.  It looks cool, and provides hot swap bays for big desktop HDD's and little notebook HDD's.  It also has two USB 3.0 ports.  

The dc7800 doesn't have any USB 3.0 capability.  So I bought a [Silverstone SST-ECO4-P]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815256004") at the same time as the Kingwin.  

I didn't really know if any of this was gonna work or not...

Your PC _has to be configured to AHCI_ in BIOS, or the Kingwin hot-swap bays won't work.  And you can't just change an existing install to AHCI from the old-school IDE emulation.  Your OS (Windows or Linux) has to be installed _after_ BIOS is set to AHCI.  

The Silverstone ECO4 needs a separate power supply, provided via Molex.  I had some Molex fan extenders laying around, so that was no big deal.

I don't have any USB 3.0 device, so I can't provide any USB 3.0 speed test results.  With the Kingwin USB cable connected to the Silverstone, the USB ports on the face of the Kingwin read USB 2.0 thumb drives.

Ubuntu picks up any 2.5" or 3.5" HDD inserted into the Kingwin.  A word of caution here - I nudge the HDD in as far as I can with a finger.  At first I just set the HDD in the opening and used the Kingwin's bay door to insert the HDD fully, but it felt like the door was gonna tear right off so I stopped doing that.

---

### Post by ghat on 2013-02-25
> **Bartender said:**
> HP dc7800 Convertible Mini-Tower Business PC

Ubuntu 12.04

The dc7800 doesn't have any USB 3.0 capability.  So I bought a [Silverstone SST-ECO4-P]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815256004") at the same time as the Kingwin.  



So does this card work with Ubuntu 12.04-LTS or not ? I have a rosewill card and it will not connect at USB 3.0 speeds, in oneiric. I am getting a new build ready which will have precise. I like the card because it has a header for most of the new cases you get with USB 3.0. If it works let me know..

G

---

### Post by fraktalek on 2013-02-27
Ubuntu: 12.10
uname -rvmpi: 3.5.0-25-generic #38-Ubuntu SMP Mon Feb 18 23:27:42 UTC 2013 x86_64 x86_64 x86_64
Type Of Hardware: USB DAC (digital to analog convertor)
Hardware Maker: Meridian 
Hardware Model: ***[Meridian Explorer]("http://www.meridian-audio.com/en/collections/products/explorer-1000/4/")***

Alsa version: 1.0.25

Works out of the box, you only need to fire up alsamixer and increase volume (Meridian Clock Selector, Meridian Clock Selector 1)

Don't know how to achieve a higher sampling rate, even if playing FLAC only the first LED light is on.

The same goes for Ubuntu 12.10 and Kernel 3.8.x of Ubuntu Raring

Meridian says Alsa version should be >= 1.0.23. I suspect it could play better than it does now for me. Or I need better headphones (have Shure SE315 and RHA MA450i)

EDIT: The Meridian website now says that Alsa has to only be >= 1.0.23 (it used to say >= 1.0.32)

---

### Post by jwaclawsky on 2013-03-05
I have Ubuntu 12.10 running on a ZBOX-ID80 with an Intel® Atom&#8482; CPU D2700 @ 2.13GHz dual core with hyperthreading. It has 2GB of memory and a 320 GiB hard drive. This is a basic system (there is NO keyboard, NO mouse and No display - I have accumulated a lot of mice and KBs and an extra display over the years due to the virus laden, slow Microsoft machines I had been buying so I had spares). The system I described costs me $300-$25 (rebate) = $275. It runs awesome and gives me a very small form factor PC that meets my needs. It fits nicely behind the display on my desk. I don't have to climb around under my desk and route cables. I simply can't recommend it enough. I just took the system out of the box and plugged in a CD RW drive with an Ubuntu 12.10 disk that I burned with my Dell mini 9 running Ubuntu 12.10 too. The ZBOX immediately found the 12.10 OS and installed without any issues. This is so much better than any windows machine (period!).

---

### Post by manhpv12 on 2013-03-05
According to Slashgear, in fact Microsoft has integrated hardware detection capabilities in Windows RT with a lot of other devices, from printers, scanners, mice, keyboards and other devices using the USB port.


And according to Microsoft, the number of hardware devices that the company has integrated the ability to identify the Windows RT up to 420 million devices.

---

### Post by Erik1984 on 2013-03-10
I recently bought myself a new desktop pre-installed with WIndows 8 that I've dual booted with Kubuntu 12.10 and now Ubuntu 12.10. 

**Components**
Main-board: MS-7798
Main-board firmware: MSI ClickBios II (UEFI)
Processor: Intel(R) Core(TM) i5-3550 CPU @ 3.30GHz
GPU (integrated): Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (HD2500)
Audio: 7 Series/C210 Series Chipset Family High Definition Audio Controller

**Added components**
USB wireless brand and type: Conceptronic C300RU Wireless N
USB wireless chipset: Ralink Technology, Corp. RT3072

**Compatibility**
_Kubuntu 12.10_
Graphical glitches on the desktop, disappear when changing rendering to Xrender in stead of OpenGL. Wireless works ootb. Installs fine.

_Ubuntu 12.04.2_
Live session works fine, Wireless ootb. Installer fails to install GRUB in separate /boot partition though.

_Ubuntu 12.10_
Perfect. Wireless works ootb and the GPU handles Unity fine. Installs and boots fine with separate /boot.

**My Installation Procedure**

[LIST=1]
[*]Use the disk management in Windows 8 to make room for Ubuntu (I took ~ 50 GB)
[*]Press <F11> at boot to pick a boot device, pick DVD drive.
[*]Create ext2 partition for /boot in empty space, I gave it 500 MB.
[*]Create swap area the size of your RAM
[*]Create ext4 partition for /root to take the remainign space
[*]**Install GRUB in the /boot partition, not MBR!**
[*]Finish installation and reboot to Windows.
[*]Install EasyBCD
[*]Add Ubuntu to the boot menu, point EasyBCD to the partition of /boot
[*]Reboot again and see if Ubuntu boots correctly.
[/LIST]

---

### Post by clearski on 2013-04-20
**OS:** Ubuntu 13.04 Raring (3.8.0-19-generic), workstation
([http://www.ubuntu.com](http://www.ubuntu.com))

**CPU:** Intel(R) Core(TM) i5-2500 CPU @ 3.30GHz
([http://ark.intel.com/products/52209/Intel-Core-i5-2500-Processor-(6M-Cache-3_30-GHz)](http://ark.intel.com/products/52209/Intel-Core-i5-2500-Processor-(6M-Cache-3_30-GHz))

**MB:** Asrock P67 Pro3
([http://www.asrock.com/mb/Intel/P67%20Pro3/?cat=Specifications](http://www.asrock.com/mb/Intel/P67%20Pro3/?cat=Specifications))

**Graphics:** ATI "Redwood XT" [Radeon HD 5670], 1GB, DDR5
([http://www.amd.com/us/products/desktop/graphics/ati-radeon-hd-5000/ati-radeon-hd-5670-overview/Pages/ati-radeon-hd-5670-overview.aspx](http://www.amd.com/us/products/desktop/graphics/ati-radeon-hd-5000/ati-radeon-hd-5670-overview/Pages/ati-radeon-hd-5670-overview.aspx))

**Case:** CoolerMaster HAF912
([http://www.coolermaster-usa.com/landing/haf912/home.php](http://www.coolermaster-usa.com/landing/haf912/home.php))

**Memory:** G.Skill 2x2 Gb DDR3 1333 MHz
([http://www.gskill.com/products.php?index=245](http://www.gskill.com/products.php?index=245))

**Wireless:** Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03)
(bought with a few dollars from Ebay, needs a miniPCI to PCI adapter)

**Ethernet:** Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI

**HDD:** Western Digital Caviar Green 500Gb

It just rocks!

---

### Post by worldwidejoe on 2013-05-26
Ubuntu 12.04
USB Wirelss Network Adapter
Netgear 
N300 USB Wireless adapter.  Other model identification listed on the box: WNA3100M

This worked out of the box on a fresh install of Ubuntu 12.04.  I did NOT install ndiswrapper.

---

### Post by koehn on 2013-05-29
Ubuntu 12.04.2 LTS
Gigabyte H61N-USB3 motherboard
Intel(R) Pentium(R) CPU G2120 @ 3.10GHz
8GB PC1333 RAM
Built-in video (HDMI), audio (HDMI), network (1000baseT)
OCZ-VERTEX PLUS 60GB SSD
Windows MCE-compatible USB infrared remote

Works well except the audio, which has a bit of static. I can only get the HDMI audio to work at all (with static) if I use the MythTV software mixer; everything else results in incomprehensible audio. If I could fix the audio it would be basically perfect for front-end work. The box itself is silent, you cannot even hear the fan from more than a few inches away. I know nothing of how audio works on Linux; any help would be appreciated. 

Would like to use the builtin Intel MPEG decoder too, but am using HQ OpenGL for blitting. Works fine.

---

### Post by Kevin S on 2013-06-13
OS: Lubuntu 13.04
PC: Dell Dimension 4300, Pentium II, 768MB RAM (upgraded from original 256)
Old system, shipped with Windows Me.  Lubuntu works great; now it's useful again.  (Have not yet tried WiFi or anything "fancy.")

---

### Post by mörgæs on 2013-06-26
First of all: This is old and slow hardware. By modern standards it is hardly useful, and some applications like Flash and Chromium are not available for PPC, so one should only install Buntu for the challenge of it.  

The hardware specifications are

```
snowball
    description: Computer
    product: iMac LCD 15"
    vendor: Copyright 1983-2001 Apple Computer, Inc. All Rights Reserved
    serial: [REMOVED]
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
       clock: 99MHz
       capabilities: powermac4_2 macrisc2 macrisc power_macintosh
     *-firmware
          product: OpenFirmware 3
          physical id: 0
          logical name: /proc/device-tree
          capabilities: bootinfo
     *-memory
          description: System memory
          physical id: 1
          size: 512MiB
        *-bank:0
             description: SDRAM
             product: PC100-222S
             physical id: 0
             version: 0000,00 00,00
             slot: DIMM0/J12
             size: 256MiB
        *-bank:1
             description: SDRAM
             product: PC100-222S
             physical id: 1
             version: 4141,09 66,02
             serial: [REMOVED]
             slot: DIMM1/J13
             size: 256MiB
     *-cpu
          description: CPU
          product: 7450, altivec supported
          physical id: 2
          bus info: cpu@0
          version: 2.1 (pvr 8000 0201)
          size: 700MHz
          clock: 99MHz
          capabilities: altivec performance-monitor
        *-cache:0
             description: L1 Cache
             physical id: 0
             size: 32KiB
        *-cache:1
             description: L2 Cache (unified)
             physical id: 1
             size: 256KiB
             clock: 700MHz (1.4ns)
     *-pci:0
          description: Host bridge
          product: UniNorth/Pangea AGP
          vendor: Apple Inc.
          physical id: 100
          bus info: pci@0000:00:0b.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-uninorth latency=16
          resources: irq:0
        *-display UNCLAIMED
             description: VGA compatible controller
             product: NV11 [GeForce2 MX/MX 400]
             vendor: NVIDIA Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: b2
             width: 32 bits
             clock: 66MHz
             capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
             configuration: latency=248 maxlatency=1 mingnt=5
             resources: memory:91000000-91ffffff memory:98000000-9fffffff memory:90000000-9000ffff
     *-pci:1
          description: Host bridge
          product: UniNorth/Pangea PCI
          vendor: Apple Inc.
          physical id: 101
          bus info: pci@0001:10:0b.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=16
        *-generic
             description: Unassigned class
             product: KeyLargo/Pangea Mac I/O
             vendor: Apple Inc.
             physical id: 17
             bus info: pci@0001:10:17.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=macio latency=16
             resources: irq:0 memory:80000000-8007ffff
        *-usb:0
             description: USB controller
             product: KeyLargo/Pangea USB
             vendor: Apple Inc.
             physical id: 18
             bus info: pci@0001:10:18.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=16 maxlatency=86 mingnt=3
             resources: irq:27 memory:80081000-80081fff
        *-usb:1
             description: USB controller
             product: KeyLargo/Pangea USB
             vendor: Apple Inc.
             physical id: 19
             bus info: pci@0001:10:19.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=16 maxlatency=86 mingnt=3
             resources: irq:28 memory:80080000-80080fff
     *-pci:2
          description: Host bridge
          product: UniNorth/Pangea Internal PCI
          vendor: Apple Inc.
          physical id: 102
          bus info: pci@0002:20:0b.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=16
        *-firewire
             description: FireWire (IEEE 1394)
             product: UniNorth/Pangea FireWire
             vendor: Apple Inc.
             physical id: e
             bus info: pci@0002:20:0e.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=16 maxlatency=24 mingnt=12
             resources: irq:40 memory:f5000000-f5000fff
        *-network
             description: Ethernet interface
             product: UniNorth/Pangea GMAC (Sun GEM)
             vendor: Apple Inc.
             physical id: f
             bus info: pci@0002:20:0f.0
             logical name: eth0
             version: 00
             serial: [REMOVED]
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sungem driverversion=1.0 duplex=full ip=[REMOVED] latency=16 link=yes maxlatency=64 mingnt=64 multicast=yes port=MII speed=100Mbit/s
             resources: irq:41 memory:f5200000-f53fffff memory:f5100000-f51fffff
     *-scsi
          physical id: 3
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD800BB-00JH
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 05.0
             serial: [REMOVED]
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:mac
             configuration: ansiversion=5
           *-volume:0
                description: Apple partition map
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                capacity: 31KiB
           *-volume:1
                description: Apple Bootstrap
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 974KiB
                capacity: 977KiB
                capabilities: bootable hfs initialized
                configuration: created=2013-06-25 07:28:23 filesystem=hfs label=bootstrap modified=2013-06-25 20:40:35 state=clean
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 73GiB
                capacity: 73GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-06-25 06:57:33 filesystem=ext4 lastmountpoint=/ modified=2013-06-25 07:28:59 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=1970-01-01 00:00:20 state=mounted
           *-volume:3
                description: Linux swap volume
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                version: 1
                serial: [REMOVED]
                size: 1450MiB
                capacity: 1450MiB
                capabilities: swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:4
                description: Apple Free
                physical id: 5
                bus info: scsi@0:0.0.0,5
                logical name: /dev/sda5
                capacity: 24KiB
        *-cdrom
             description: SCSI CD-ROM
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             capabilities: audio
             configuration: status=nodisc

```

When using a standard keyboard F12 opens the CD tray. Windows + Alt + o + f gives access to Open Firmware.

My iLamp needed a new CD drive. It takes a little while to [disassemble]("http://www.youtube.com/watch?v=TQ1Y76qfT14&#8206;") the unit, but it is doable. 

Download the 12.04 mini ISO for PPC and install from CD. Only a single-use CD worked, neither rewritables nor boot from USB did. Pressing c during power-on boots from CD.

The install works as usual except for some vivid colours, but one might need to enter the package mirror manually. 

When booting from hard drive some boot options are needed. Mine (sporting an Nvidia screen card) needed the command

```
Linux nouveau.modeset=0 
```
or
```
Linux nomodeset
```

at the yaboot prompt. Booting without options shows an interesting display of slowly fading colours and patterns. 

With the minimal system installed

```
sudo apt-get install xubuntu-desktop
```

brings rest of it (note to self: Lubuntu would probably have been a better choice than Xubuntu).

Now booting into the system (with the above-mentioned boot options) gives a barely usable desktop in Andy Warhol-ish colours. I didn't find a way to make the default Nouveau driver behave well, but switching to the older [nv driver]("http://ubuntuforums.org/showthread.php?t=2131644") did the trick. 

The system is stable, but it might freeze without warning for some time doing regular tasks. Just wait and then wait some more; it will come back to life. 

It's a good idea to add System Load Monitor or similar to the top bar to see how the workload is. When updates or another heavy task is going on just leave it for a while.

---

### Post by su:bhatta on 2013-07-11
Last Sunday did a box with these specifications:

1)Version Of Ubuntu : Ubuntu Studio 13.04 (AMD64)
2)Type Of Hardware : Mother Board & CPU
3)Hardware Maker : M/B ASUS & CPU AMD
4)Hardware Model: ASUS 88TM M/B & Phenom X2, 3.2 Ghz

---

### Post by red_starfox2 on 2013-08-17
[FONT=arial]Ubuntu 13.04
Hardware:
[/FONT]**[FONT=arial]P4 2,66GHz(FSB 400)[/FONT]**

786 MB PC2100(32 bit, single layer)
Gigabyte GA-85GXP main circuit board
160 GB HDD/7200rpm/8 MB cache/SATA II
Nvidia GeForce 7900GS/256bit/256MB DDR2/AGP 8X[FONT=arial]
[/FONT]
Works without any problems...just turn off unity's animation effects and tweak the graphic card for a bit more performance.
Very stable and smooth now!

---

### Post by rty2 on 2013-08-18
_Version of Ubuntu:_ Ubuntu 10.04.1 LTS, kernel 2.6.32-50-server
_Type of Hardware:_ Shuttle SN68SG2
_ CPU:_ AMD Athlon(tm) Processor LE-1640
_RAM:_ 2 GByte (2*1GB Corsair VS DDR-2 667)
_Graphics:_ Onboard graphics GeForce 7025 / nForce 630a (used for console only -- it's my server after all)
_Extensions:_ Sharkoon USB3.0 PCIe Host Controller Card

Concerning the many trouble reports, the USB3.0 card seems to be noteworthy. Detected out of the box (without device attached at boot time):
[INDENT][SIZE=1][FONT=courier new][    8.340305] xhci_hcd 0000:02:00.0: PCI INT A -> Link[APC6] -> GSI 16 (level, low) -> IRQ 16
[    8.340331] xhci_hcd 0000:02:00.0: setting latency timer to 64
[    8.340343] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    8.340412] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 5
[    8.345689] xhci_hcd 0000:02:00.0: irq 16, io mem 0xfdefe000
[    8.349121] usb usb5: config 1 interface 0 altsetting 0 endpoint 0x81 has no SuperSpeed companion descriptor
[    8.349194] usb usb5: configuration #1 chosen from 1 choice
[    8.349198] xHCI xhci_add_endpoint called for root hub
[    8.349200] xHCI xhci_check_bandwidth called for root hub
[    8.349225] hub 5-0:1.0: USB hub found
[    8.349233] hub 5-0:1.0: 4 ports detected[/FONT][/SIZE]
[/INDENT]

lspci: [SIZE=1][FONT=courier new]02:00.0 USB Controller: Renesas Technology Corp. Device 0015 (rev 02)[/FONT][/SIZE]
lsusb: [SIZE=1][FONT=courier new]Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub[/FONT][/SIZE]

Performance is not overwhelming but okay for me, with ext2 formatted *Toshiba Store.E Canvio* 2TB hdd:
[INDENT][SIZE=1][FONT=courier new]Timing cached reads:   2068 MB in  2.00 seconds = 1034.12 MB/sec
Timing buffered disk reads:  274 MB in  3.01 seconds =  90.96 MB/sec[/FONT][/SIZE]
[/INDENT]

Cheers!

---

### Post by paul_c2 on 2013-08-27
[B]Version Of Ubuntu : 12.04 LTS
Type Of Hardware : Core 2 Duo E4400 (2.00Ghz) / 4GB DDR2-800 / 500GB WD HD / ZOTAC GeForce 9300-ITX (onboard GF 9300 & WiFi unplugged)
Hardware Maker : Zotac
Hardware Model : GeForce 9300-ITX

[/B]Had a hard time making audio work through HDMI, turns out you have to unmute S/PDIF 1 in alsamixer.

EDIT : Oh! and suspend & Hibernate don't work, I just get a blank screen with a blinking promtp resulting in a forced restart.

---

### Post by mörgæs on 2013-08-31
HP dc7700: In order to boot from USB the BIOS must be upgraded from v01.10 to v01.15. After that everything works well with a 64 bit Xubuntu 13.04.

Some old threads in the forum talk about the need for boot options. No such need using 13.04 and v01.15.

---

### Post by mörgæs on 2013-09-25
In spite of the Trendnet TEW-703 not being mentioned on the [Linux compatibility list]("http://www.trendnet.com/support/os_compatibility.htm") it works out of the box with Xubuntu 13.04 using WPA encryption.

---

### Post by Donut50 on 2013-10-09
Acer Aspire x3470
Ubuntu 12.04 and 13.04 tested, both work perfectly, even when dual booted with windows 7.
Hardware:
AMD A6 3620 APU with AMD Radeon HD 6530d 512 mb ddr3
8Gb ddr3 RAM at 1333mhz
standard motherboard, case and power supply.
Everything works out of the box, wifi, ethernet and everything else.
Just install the AMD catalyst driver and it is an ubuntu pc that feels like it is preinstalled with it :)

---

### Post by Donut50 on 2013-10-09
only sleep option is a problem

---

### Post by Donut50 on 2013-10-22
amd radeon r9 290x 4gb gddr5 reference card.
16 gb ddr3 corsair dominator 1866mhz ram
evga studio motherboard
amd 1100t hex core at 3,6 ghz (amd phenom II)
ASUS pcie 240 gb ssd
Seagate platinum 4 terabyte hdd at 7200rpm
Corsair cx860 watt builder psu
Cooler master n500 case

Tested on ubuntu 13.04 and 13.10
No problems, just install the 13.10 beta drivers from amd and do glxinfo| grep render/ OpenGL and the hardware is fine.
It rocks with steam! :)

---

### Post by oneone on 2013-10-29
Hi, does the machine work running 13.10 (or 13.04, 12.04)?

I have a T510 (43494JG) with NVS3100M graphics that crashes using openGL on nouveau and the nvidia driver does not work at all.

---

### Post by DanglingPointer on 2013-10-29
> **Donut50 said:**
> amd radeon r9 290x 4gb gddr5 reference card.
16 gb ddr3 corsair dominator 2866mhz ram
evga studio motherboard
amd 1100t hex core at 3,6 ghz (amd phenom II)
ASUS pcie 240 gb ssd
Seagate platinum 12 terabyte hdd at 7200rpm
Corsair cx860 watt builder psu
Cooler master n500 case

Tested on ubuntu 13.04 and 13.10
No problems, just install the 13.10 beta drivers from amd and do glxinfo| grep render/ OpenGL and the hardware is fine.
It rocks with steam! :)

Hi Donut50,
So the minimum FGLRX driver is 13.10?  Do you know if it works with the non-beta driver from the ubuntu repository?

---

### Post by Donut50 on 2013-11-01
I currently have tested the system really far on ubuntu 13.10, on ubuntu it should work also, but i had some trouble with letting ubuntu detecing my hardware(the videocard mainly).
The prioritary drivers of AMD will give ubuntu the chance to let the card really stretch his legs.
The beta drivers are performing a little bit better on my feels (dem feels)

(sorry for the late responding time :) )

---

### Post by Claus7 on 2013-12-25
Hello,

Please Only List
1)Version Of Ubuntu - ubuntu maverick 10.10
2)Type Of Hardware - webcamera
3)Hardware Maker - crypto
4)Hardware Model - W003690- CRYPTO HD WEB CAMERA [TOUCH]

```
lsusb
```

> Bus 002 Device 005: ID 058f:3841 Alcor Micro Corp.

worked without any driver, just plugged it in
all resolutions (till HD) available
additional software with CD not checked (was not installed)

configurations of the webcam, while using skype, were made using this post:
[http://ubuntuforums.org/showthread.php?t=1310603&p=10598219#post10598219](http://ubuntuforums.org/showthread.php?t=1310603&p=10598219#post10598219)

with skype: ```
bash -c 'XLIB_SKIP_ARGB_VISUALS=1 skype'
``` just what I used with the previous camera in order to run skype

cheese is working ok

Regards! - Happy Holidays!

---

### Post by Rich53201 on 2013-12-27
1)Version Of Ubuntu [B]
     Lubuntu 13.10 for AMD 64
[/B]2)Type Of Hardware[B]
     AMD Athlon 64 3500+ / 2.2 GHz, ATI-Radeon Xpress 200 video (onboard, as provided)**, RAM upgraded to 2 Gb**
[/B]3)Hardware Maker[B]
     Emachines
[/B]4)Hardware Model
     [B] T6524

Would have tried Ubuntu 12.04.3 LTS, but the DVD reader is dead, and I was unable to solve bugs with thumb drive boot.  Lubuntu fits on a CD, so, it 'won'.
Dual boot with Windows XP is working fine.

Hibernate does not work.  Monitor shuts off, cpu/box does not.  I have to hard-reset it to get it out of this state.  I think this issue is reported/known for the AMD 64 version.

Edit 2014/04/23:  Automatic update to Lubuntu 14.04 went well.  I tried Hibernate.  It is now disabled, so it's an improvement over the previous version.
[/B]

---

### Post by Link_Family on 2013-12-30
I have been testing multiple platforms with the newest distribution of Ubuntu Linux and the best line of platforms is the Hewlett Packard line.

---

### Post by Twan_Slegers on 2014-01-23
ASUS P4P800-VM (BIOS works 100%)
Pentium 4 HT 3.0GHz (HT works good, a little bit on the slow side sometimes)
GeForce FX 5200 (using latest propetiary drivers, sometimes a little bit of graphics glitches)
1.5GB DDR RAM
20GB Matrox hard drive (not much space, so you can't dual-boot but it works fine)

And most if not all is well used original 2003 hardware.

---

### Post by mörgæs on 2014-01-24
Edit 2017-05-25: For Buntu 16.04 there is [another solution]("https://ubuntuforums.org/showthread.php?t=2355620").

= = = = = 
A lot of advice on Canon Pixmas exist, but the quality of said advice varies a lot.

Here's a guide for a **Pixma MP610** (and similar printers) running from a 64 bit Lubuntu 13.10.

Without USB cable attached: Reset the printer on the display.

Run ```
sudo apt-get update
``` and ```
sudo apt-get dist-upgrade
``` just to make sure that everything is up to speed. Reboot as needed.

After that 
```
sudo add-apt-repository ppa:michael-gruz/canon-trunk
sudo apt-get update
sudo apt-get install cnijfilter-mp610series
```

Now connect the USB cable. 

Go to System -> Printers 

Click 'add printer'. 

Wait a couple of minutes until you see MP610 in the window to the left.

Select the printer and proceed with next, next, next, finish.

Now printing should work and the same goes for Simple Scan, the built-in scanning application in Lubuntu.


Modified from the page 
[http://linuxg.net/how-to-install-drivers-for-canon-printers-pixma-mp-series-on-ubuntu-14-0413-1013-0412-1012-04-linux-mint-16151413-pear-os-87-and-elementary-os-0-2/](http://linuxg.net/how-to-install-drivers-for-canon-printers-pixma-mp-series-on-ubuntu-14-0413-1013-0412-1012-04-linux-mint-16151413-pear-os-87-and-elementary-os-0-2/)

---

### Post by leeper69 on 2014-02-14
Hi I am running ubuntu studio 13.10 on a gigabyte  ep45-ud3r mother board.
with a q9750 quad core cpu and 4 gig of corsair  system memory.
a pci express 2.0 zotec geforce gt630 gpu with 4 gig of memory.
a pci pchdtv 5500 tv card.
19"kds monitor.
usb 2.0  epson cx8400 printer/scanner.
sound blaster audigy 2 zs sound card.
built in intel sound card.
usb 2.0 card reader.
hp sata dvd reader.
sony sata dvd burner.
sony 3.5 floppy disk.
1tb 7200rpm segate hard drive. ( i have also run 3 80 gig 7200 rpm seagate hard drives at raid 5 untill all three of the drives faild me after about 4 years of use.)
this machine was built around linux compatable hardware but is on the falling edge behind the i3/i5/i7 processors and advancments in usb and sata data speeds.

---

### Post by linux4me on 2014-02-22
Ubuntu Version: 13.10
Type of Hardware: Wi-fi Adapter
Hardware Manufacturer: Rosewill
Model Number: RNX-N600UBE

It works out-of-the-box with Ubuntu 13.10. It has a nice long USB cord and the actual adapter sits nicely on a level (or nearly level) surface. This is more of a desktop wireless solution because I would prefer just a little dongle if I were using it for portability with a laptop, but for a desktop, especially maybe a tower you put on the floor, the USB cable and separate adapter would be ideal.

---

### Post by linux4me on 2014-02-22
Ubuntu Version: 13.10
Type of Hardware: Wireless Keyboard and Mouse
Hardware Manufacturer: Logitech
Model Number: MK120 Combo

These work out-of-the-box with Ubuntu 13.10.

---

### Post by linux4me on 2014-02-22
Ubuntu Version: 13.10
Type of Hardware: USB 3.0 SATA 3.0 HDD Docking Station
Hardware Manufacturer: Unitek
Model: Y-1072

This docking station works flawlessly with Ubuntu 13.10 via USB 3.0 with a couple of Western Digital 500 GB drives I have, but I have a 1 TB Western Digital drive that would not work with it via USB 3.0, though it would work via USB 2.0. I went through a bunch of troubleshooting, RMA'd the drive, and the replacement also failed to mount. I filed a bug report, then an upstream bug report, and still go no solution that would make the 1 TB drive mount. I got my hands on another external drive enclosure (an Icy Dock Blizzard, see below) and it works fine with the 1 TB drive, so I suspect it is a chipset issue with the Unitek.

---

### Post by linux4me on 2014-02-22
Ubuntu Version: 13.10
Type of Hardware: USB 3.0/eSATA External HDD Enclosure
Manufacturer: Icy Dock
Model Number: MB080U35-1SB

Works out-of-the box with Ubuntu 13.10 via USB 3.0. I haven't tried the eSATA connection. I've had issues with three other brands of HDD dock/external enclosures and USB 3.0 in Ubuntu 13.10, and this is the one that works best. I haven't had any problems with it.

---

### Post by linux4me on 2014-02-22
Ubuntu Version: 13.10
Type of Hardware: USB 3.0 External HDD Enclosure
Manufacturer: Rosewill
Model: RX35-AT-SU3

I've tried two of these, and neither one will reliably connect to Ubuntu 13.10 via USB 3.0. They occasionally connect, but it's not reliable at all. They do work via USB 2.0, but if you don't have a USB 2.0 connector on your machine you'll need to disable XHCI in your BIOS (if you can) to use the older EHCI controller at USB 2.0 speeds. It's a kludgy workaround at best, and who wants to pay for a USB 3.0 device to get only USB 2.0 speeds?

---

### Post by Johnny3 on 2014-03-18
This works with the Pixma ip4700 printer too. Just change mp610 to ip4700. With Ubuntu 14.04.
Thanks and God Bless Johnny333 67+++
Don't known much about the terminal. But good at copy and past.


> **mörgæs said:**
> A lot of advice on Canon Pixmas exist, but the quality of said advice varies a lot.

Here's a guide for a **Pixma MP610** (and similar printers) running from a 64 bit Lubuntu 13.10.

Without USB cable attached: Reset the printer on the display.

Run ```
sudo apt-get update
``` and ```
sudo apt-get dist-upgrade
``` just to make sure that everything is up to speed. Reboot as needed.

After that 
```
sudo add-apt-repository ppa:michael-gruz/canon-trunk
sudo apt-get update
sudo apt-get install cnijfilter-mp610series
```

Now connect the USB cable. 

Go to System -> Printers 

Click 'add printer'. 

Wait a couple of minutes until you see MP610 in the window to the left.

Select the printer and proceed with next, next, next, finish.

Now printing should work and the same goes for Simple Scan, the built-in scanning application in Lubuntu.


Modified from the page 
[http://linuxg.net/how-to-install-drivers-for-canon-printers-pixma-mp-series-on-ubuntu-14-0413-1013-0412-1012-04-linux-mint-16151413-pear-os-87-and-elementary-os-0-2/](http://linuxg.net/how-to-install-drivers-for-canon-printers-pixma-mp-series-on-ubuntu-14-0413-1013-0412-1012-04-linux-mint-16151413-pear-os-87-and-elementary-os-0-2/)

---

### Post by Donut50 on 2014-03-27
Nvidia geforce gtx 460 se 3gb edition
Íntel core I5 4430
12gb ram @ 1600mhz
Samsung 840 evo 120gb ssd
2 500gb 2,5 inch laptop hdd's
Asrock pro 3 z87 motherboard
460watt psu from coolermaster

works on ubuntu 12.04 and 13.10
only it will not shut off, it will reboot a couple seconds after you have shutted off the machine.

---

### Post by DogMatix on 2014-04-04
**Ubuntu:** Lubuntu 14.04
**Hardware:** 300Mbps Wireless N PCI Adapter
**Maker:** TP-Link
**Model:** TL- WN951N 

[LIST]
[*]This wireless card worked out of the box.
[*]It has an Atheros chipset and is using the Ath9K driver.
[*]It is fitted in a Dell Dimension 1100 desktop, (year 2004) Intel Celeron D 2.8Ghz
[/LIST]


**Note:**
I have used TP-Link wireless cards in several Linux computers and found, in my experience, they have good compatibility.

---

### Post by fred25 on 2014-04-05
Ubuntu 12.04 LTS
Desktop computer 2.8 GHz Pentium 4, 2 GB corsair memory, Gforce FX 5200 PCI, 
Dell
Dimension 2350
I installed Ubuntu 12.04  LTS and it worked no problems except the graphics weren't good and it was slow because of the shared memory.  I installed a Nvidia Geforce FX5200 video card, it installed automatically and works fine and the graphics were great and it ran faster.  Then I replaced the 2.2 GHz Celeron with a 2.8 GHz Pentium 4 now I have a computer that runs fast like a new machine.

---

### Post by tlhIngan on 2014-04-11
AMD QuadCore Phenom in an Asus M3N-HT Deluxe using the onboard graphics.
I had difficulties installing Ubuntu 12.04.4, the GUI wouldn't come on. After some poking around, it turns out that re-installing WITHOUT allowing the download of updates or 3rd-party things solved the issue.
After a successful login, I performed a complete system update and rebooted, and everything is still fine.
Prolly a 3rd-party driver that isn't really compatible with the hardware, or that wasn't setup properly, or whatever.
Hope this helps somebody somewhere some time.

---

### Post by lyubomirv on 2014-05-12
Ubuntu version: XUbuntu version 14.04
Type Of Hardware: Gamepad
Hardware Maker: Speedlink
Hardware Model: Strike FX Wireless (Model no. SL-4443-BK)

Works out of the box after charging and plugging in the USB receiver. May need installing the 'joystick' package and possibly 'jstest-gtk' too, for a visual check of operation. 'jstest-gtk' registers all axes and buttons correctly only if a LED (number 1, etc.) on the back of the controller is on. To turn it on/off, press the 'home' button on the gamepad.

---

### Post by Mike_Walsh on 2014-06-03
Thought I'd add my tuppence-worth (for what it's worth;*Groan...*)

Running a 10 yr old HP-Compaq Presario here. (SR1619UK, model EK335AA)

Just installed 14.04 'Trusty Tahr' (last night, in fact). Install was extremely straight-forward, and very quick: 22 mins in fact from start to finish, including wiping and reformatting. No problems WHATSOEVER. 

-------------------------------------------------------------------------------------------------------------------

[COLOR=#0000cd]CPU: AMD Athlon 64 3200+@2.0 GHz.[/COLOR]

**Update** (04/04/2015): Upgraded to [COLOR=#0000ff]Athlon 64 X2 3800+ dual-core@2.0 GHz[/COLOR]. Works perfectly on this board, with BIOS update to ensure dual-core support. Essentially two 3200+'s on the same die, the system is snappier, somewhat faster, and FAR more responsive.....and now multitasks even better than before. A worthwhile investment, for £7.90 off eBay.....and a couple of hours work.

[COLOR=#0000cd]MSI MS-7184 mother board[/COLOR]. Fellow Presario owners will know this as the 'Amethyst-M'. Due to the above-mentioned BIOS upgrade for the X2, the system now thinks it's an MS-7093..! #-o

[http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c00378480](http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c00378480)

.....ATI chipset; RS482- and SB400-based.

[COLOR=#0000cd]3GB DDR1 RAM from Micron[/COLOR] (2 x 1GB, 2 x512MB), running in dual-channel configuration.
On-board[COLOR=#0000cd] ATI Radeon Xpress 200[/COLOR] graphics chipset.
[COLOR=#0000cd]Western Digital Caviar 'Black' 160 GB[/COLOR] internal HDD, and [COLOR=#0000cd]Seagate Expansion 500 GB[/COLOR] external USB HDD.
**Update** (26/08/15) WD Caviar 'Black' (PATA) now replaced with [COLOR=#0000ff]WD Caviar 'Blue' 500GB[/COLOR] (SATA), due to the former developing lots of 'bad' sectors quite recently.....and it's over 10 yrs old, with a lot of hours 'on the clock'!
[COLOR=#0000cd]Dell E151 FPp 15" Plug'n'Play monitor[/COLOR] @ 1024x768 (donated by my brother, when he bought his iMac with 'Retina' display; cheers, John!)
[COLOR=#0000cd]Logitech K120 wired USB keyboard.[/COLOR]
[COLOR=#0000cd]Logitech Zone Touch T400 wireless mouse [/COLOR](this is brilliant, 'cos in Windows you need to install Logitech's Setpoint software to get the best out of the mouse; at 80 Mb+ it's NOT lightweight). It works perfectly "straight-out-of-the-box", even the sideways scrolling!
[COLOR=#0000ff]CoolerMaster B50 'single-rail' 500W PSU [/COLOR]recently (July '15) replaced the original generic 'silver box' PSU of 300W.

Normally use an Ethernet connection, but sometimes use wireless [COLOR=#0000cd]TP-Link WN-725N 'nano' wireless adapter[/COLOR], when I'm running my elderly Dell laptop on the 'net...wireless won't work with that, so RJ45 it is.Haven't even plugged this in yet, so haven't tried it. Will add update when I do..

**Update** (09/06/14); used this for the first time two nights ago; touch wood, no problems so far.


Generic Bluetooth packet dongle, which I use for file transfer between the two computers. This IS recognised, but again, I haven't yet tried it.

**Update** (18/06/14); used this last night, and paired it with the Dell laptop, which is running Lubuntu. Data packet transfer works well, in BOTH directions. Both computers are in fact using identical dongles, so I wouldn't have expected any problems...


[COLOR=#0000cd]Epson Stylus SX218 printer/scanner/all-in-one[/COLOR]. Just sorted out the driver for this. It's installed, but I can't try it at the mo, 'cos it's out of ink!!! Again, will add update when I've tried it.

**Update** (14/06/14) Printer working fine; built-in scanner is another matter ENTIRELY!! Will post update if & when sorted.

**Update** (23/07/14) Scanner now working A-OK, after installing separate filter and data packages from Epson's website (data package MUST be installed first).


**Update** (09/01/15) Added[COLOR=#0000cd] HP 2300 1080p webcam[/COLOR]. Picture works very well; haven't yet got the sound to behave itself...


**Update** (24/02/15) Added [COLOR=#0000cd]Transcend PCIe USB 3.0 adapter card[/COLOR]. This has **really **speeded up data transfer to the external Seagate, as it, too, is USB 3.0.

[COLOR=#ff0000]This system works perfectly.....despite being a 'Heinz 57'![/COLOR]

Hope this helps. ;)

---

### Post by lauri.t.kumpulaine on 2014-06-07
[http://www.intel.com/content/www/us/en/nuc/nuc-board-dn2820fykh.html?wapkw=dn2820fykh](http://www.intel.com/content/www/us/en/nuc/nuc-board-dn2820fykh.html?wapkw=dn2820fykh)
Mini PC - Intel® NUC Kit DN2820FYKH

Xubuntu 14.04
Everything hardware related works.

---

### Post by shag00 on 2014-06-23
I use a self built desktop and Ubuntu 14.04

Components:
Intel I5 CPU
Gigabyte Z87X UD5H
1 x Intel 320 series SSD (if i knew how fast Ubuntu was I would have opted for a HDD)
9 x Seagate ST4000DM000 4TB HDD
No Video card
Logitech wireless mouse, keyboard and Touchpad

All works well.

---

### Post by Axxon95 on 2014-07-25
Ubuntu 14.04
Dell Dimension 8300
NVIDIA FX 5200 GPU
Works flawlessly.

---

### Post by xSCCMx on 2014-07-29
1. Ubuntu 14.04 amd64
2. All-in-One with Touchscreen
WDC WD5000AAKS-55V0A0 Hard Drive (containing 500GB), Optiarc Bluray Drive
3) Sony Vaio VPCJ115FX
4) VPCJ115FX

---

### Post by ben107 on 2014-09-05
Ubuntu 14.04 64bit

motherboard: Gigabyte GA-970A-UD3P AM3+ AMD 970
CPU: AMD FX-6300 Vishera 6-Core 3.5GHz (4.1GHz Turbo) Socket AM3+ 95W Desktop Processor FD6300WMHKBOX
RAM: G.SKILL Ripjaws X Series 16GB (2 x 8GB) 240-Pin DDR3 SDRAM DDR3 1866 (PC3 14900) Desktop Memory Model F3-14900CL10D-16GBXL
power: Rosewill CAPSTONE-550-M 550W

I used an Ubuntu installer from a USB flash drive. It booted fine, but once Ubuntu started the installer failed with "no medium found." After some googling, I found I needed to enable IOMMU in the BIOS. Did that, was able to install Ubuntu (64 bit, 14.04), but networking wouldn't work. Also a lot of "IO_PAGE_FAULT" messages until I disabled the USB 3.0 controller in the BIOS. I tried flashing the latest BIOS (F2e beta, released 2014/09/01) but no change. I tried various combinations of IOMMU enabled/disabled and kernel options (iommu=soft, iommu=pt, amd_iommu=on) but could never get on the network. 


Final solution: Bought a cheap network card. F2e BIOS, IOMMU enabled, USB 3.0 disabled (may not be necessary if you're ok with kernel load errors), no kernel options.

---

### Post by mörgæs on 2014-09-18
Dell Dimension 9100, BIOS A03, Xubuntu 14.04.1: Everything works after a small modification.

The Dell came with 2 * 150 GiB hard disks in [fake-RAID]("http://skrypuch.com/raid/"). Before installing it's recommended to disable fake-RAID so the two disks are independent. 

After that one is free to install on the two drives separately or arranged in software RAID.

---

### Post by stevecaldwell2 on 2014-09-22
A few weeks ago, I was given a free HP Pavilion Elite HPE-112y PC with the following specs:

Processor -- AMD Phenom II X4 925
Memory -- 8 GB
Video graphics -- ATI Radeon HD4350
Sound/Audio -- Integrated Realtec ALC888S Audio
Networking -- LAN: Gigabit 10-Base-GT // 802.11 Wireless a/b/g/n PCI-Express x1 card
Hard drive -- 1 TB
CD/DVD disc drive -- SuperMulti DVD Burner with LightScribe Technology drive
Blu-ray Player

I wanted to check this hardware before refurbishing it as a Windows desktop PC.  I used Ubuntu 14.04.1 64 bit to evaluate this free cast-off hardware.  The Ubuntu install worked fine and I could confirm that the video card, sound card, and wireless card operated properly.

---

### Post by Irrationalis on 2015-01-02
Running an old iMac (2006) with Ubuntu 12.04.5 LTS:
Processor: Intel Core 2 Duo T5600  @ 1.83GHz
Memory: 2GB
Graphics: Intel GMA 950
Ethernet: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (Full Gigabit working with built in drivers, WOL even works :D)

Everything is running smoothly, Plex and CUPS are both working perfectly.

---

### Post by DennisFolsom on 2015-03-02
[FONT=Droid Sans]I have recently moved to an Acer AXC-605-UR2B, where I am running ubuntu 14.04 LTS 64-bit[/FONT]
 [FONT=Droid Sans]Processor: Intel® Core™ i5-4440 CPU @ 3.10GHz × 4 [/FONT] 
 [FONT=Droid Sans]Memory:  3.7 GiB (nominal 4 GiB)[/FONT]
 [FONT=Droid Sans]Graphics:  Intel® Haswell Desktop[/FONT]
 

 [FONT=Droid Sans]The UPC of this unit was:  8 87899 77823 0[/FONT]  I ordered it from Newegg.com.

 [FONT=Droid Sans]I purchased this particular PC because it ships with Windows 7 installed.  I am trying to wean myself off Windows, but still use it for some things.  I want nothing to do with Windows 8.[/FONT]

 [FONT=Droid Sans]This PC has a small case, but still includes an optical drive.  It came with a 1 TB hard drive installed.  Should I ever want more memory, there is a slot left for expansion.[/FONT]
 

 [FONT=Droid Sans]I had expected the PC to come with UEFI and a GPT partition table.  In preparation, I studied up on ubuntu dual-boot installs under UEFI.  To my surprise,  this PC was set up the old-fashioned way.  It boots Windows 7 in the old legacy BIOS mode, does not use Secure Boot (I believe that one is only on Windows 8 anyway), and has the MBR partitioning.  That made the ubuntu install easier than I anticipated.[/FONT]
 

 [FONT=Droid Sans]There were 3 partitions on the drive already.  Therefore, I had only 1 partition left to add (under MBR rules).  That meant I couldn't add a linux swap partition.  Using a procedure I found in the [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) , I created a 9 GB swap file in my Linux partition.[/FONT]
 

 [FONT=Droid Sans]So far, this PC is working very well.  I recommend it to anyone shopping for a new, small case desktop for ubuntu.[/FONT]

---

### Post by HDTimeshifter on 2015-07-16
> **Irrationalis said:**
> Running an old iMac (2006) with Ubuntu 12.04.5 LTS:
Processor: Intel Core 2 Duo T5600  @ 1.83GHz
Memory: 2GB
Graphics: Intel GMA 950
Ethernet: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (Full Gigabit working with built in drivers, WOL even works :D)

Everything is running smoothly, Plex and CUPS are both working perfectly.

There's no Laptop Hardware Compatibility List parallel thread to this one, so I'll post here.
I have an Acer Aspire 5630-6288 that I bought in 2006 which came with Vista and I upgraded to Windows 7. It runs like a dog, so I was thinking of wiping it and installing the latest Ubuntu desktop version (14.04). It is similar spec to your 2006 iMac. It has an Intel Core 2 Duo T5500 @ 1.66 GHz, 2 GB RAM, 160 MB Hard Drive, and Intel GMA 950 GPU. I hope it will run as well as your iMac.

---

### Post by Rytron on 2015-07-16
> **HDTimeshifter said:**
> There's no Laptop Hardware Compatibility List parallel thread to this one, so I'll post here.
I have an Acer Aspire 5630-6288 that I bought in 2006 which came with Vista and I upgraded to Windows 7. It runs like a dog, so I was thinking of wiping it and installing the latest Ubuntu desktop version (14.04). It is similar spec to your 2006 iMac. It has an Intel Core 2 Duo T5500 @ 1.66 GHz, 2 GB RAM, 160 MB Hard Drive, and Intel GMA 950 GPU. I hope it will run as well as your iMac.

Hi HDTimeshifter

There is one.

Laptop COMPATIBILITY List.: [http://ubuntuforums.org/showthread.php?t=1543006](http://ubuntuforums.org/showthread.php?t=1543006)

---

### Post by HDTimeshifter on 2015-07-17
> **Rytron said:**
> Laptop COMPATIBILITY List.: [http://ubuntuforums.org/showthread.php?t=1543006](http://ubuntuforums.org/showthread.php?t=1543006)

Thanks - don't know why a search on "laptop" didn't turn it up on the first results page as the last post was not that old. But I didn't find any Acers in that thread with specs similar to mine, so hoping I won't have problems since that iMac is spec'd so closely to my laptop.

---

### Post by Rytron on 2015-07-18
> **HDTimeshifter said:**
> Thanks ... 

You're welcome.

---

### Post by Kuro_Kitsune on 2015-08-23
Ubuntu 15.04

Alienware Alpha i3 base model 

cpu: 2.9 GHz Intel Core *i3*-4130T
ram: 4 GB
video card: NVIDIA Corporation GM107M [GeForce GTX 860M] (rev a2)

Everything Works smoothly installed Nvidia drivers without a problem only issue i had was wifi not working while bluetooth was enabled. however updating to newest kernel fixed this issue. Setup for anyone with an alpha was as plainless as it comes. Clean install, install nvidia drivers from ubuntu additional drivers reboot and done.

only feature that does not work is the hdmi in passthrough which only seems to work from the alpha ui in windows at the moment of this post. I wanted to add this on here since there wasn't much info on ubuntu running on the alpha when i got mine.

---

### Post by yoshii on 2015-12-26
Successful 32-bit Ubuntu Studio v14.04.3 LTS (long-term supported version, successful KXstudio repositories installed on top too):  

Computer:  HP ENVY 750-116; AMD ~3 GHz quad core; 12 GB RAM; ATI Radeon GPU
Monitor:  HP W2082a; 20 inch LED; sVGA
Keyboard:  Logitech K120 (Linux-compatible); USB
Mouse:  Logitech M100 (Linux-compatible); USB

Audio Interface:  Alesis M1Active 320 USB Monitors / Audio Interface; (USB Class Compliant; no drivers needed!)
MIDI Controller:  Alesis Q25; 25-Key synth action MIDI keyboard; (USB Class Compliant; no drivers needed!)

Approximately how success was attained (not an exact history but close)...

1) Plugged in all the hardware, including my audio gear (so it would be recognized by default!) and did NOT use the wifi keyboard and mouse that came with the computer.  
2) Powered on the computer and pressed ESC several times until the setup menu came up
3) Disabled Secure Boot in order to enable Legacy Mode in order to enable BIOS and hardware Boot Order Options; (several restarts required for settings to be implented via UEFI initital screen)
4) Enabled CD-ROM boot and booted up using the suggested key (I think it was F9 if I remember correctly) to select the CD-ROM instead of the SATA hard drive
5) Powered on using 32-bit Ubuntu Studio v14.04.3 LTS from DVD-R burned at 10x speed using K3B disc burner from an .ISO; chose the option to boot without installing;  boot up successful!
6) Formatted/erased the hard drive using gParted from the System menu:

First partition:  4 GB SWAP area; enabled swapon
Second partition:  960 GB formatted as ext3; (extra space reserved/left for other future optional linux os installs)

7) Rebooted from DVD-ROM using the Try Ubuntu Studio Without Installing menu choice.  
8) Clicked the Install Ubuntu Studio icon on the desktop to run the installation; chose to do "Something Else" instead of erasing the whole drive (default)
9) Performed the installation off-line without accessing the internet.  This was to prevent a documented corrupt install bug.  
10) Successfully rebooted into Ubuntu Studio with full hardware recognition and started configuring the sound mixer/volume controls; then continued configuring mouse and keyboard and all Ubuntu settings
11) Created folders and transferred my archived files from a previous installation from USB stick, starting with documentation files; installed the FireFox MAFF plugin so I could read my .MHT documentation
12) Entered my wifi log-in info and started updates and downloads and online installs.  I disabled Pre-Releases and UnSupported Ubuntu Sources to maintain stability.    
13) Continued configuration and setup and downloads and their configurations; updated the panels with launcher icons; set program associations for filetypes; edited my PulseAudio prefs to match my USB interface
14) Gradually implemented DAW performance optimizations such as ",noatime" in fstab (disable file access logging); disabled unneeded services
15) Installed current Wine and WineGecko following downloaded and internet documentation from WineHQ.com; re-downloaded updated WineGecko and moved it to the correct folder following WineHQ infos
16) Created a launcher for winecfg (Wine Configuration); (Wine stuff is located in "/opt" but it launches as normal; no need to remap launchers).  
17) Configured Wine
18) Installed, tested, and configured Windows programs
19) Created panel launchers for Windows programs
20) Installed the KX Studio repositories following the instructions on the KX Studio website; installed a few more programs off the internet; Checked installation integrity for mistakes (none really!); kept everything upgraded; I did NOT install any KX Studio repositories for Lucid since this is Trusty Tahr!  Removed the Lucid PPA entries from the Software Updater preferences.  
21) Installed backed up FireFox addons from previous installation and upgraded them to newer versions; backed up FireFox configuration with FEBE addon and some addon prefs exports
22) Finished configuring FireFox addons and preferences; backed up FireFox configuration again with FEBE and some addon prefs exports
23) Continued restoring old Reaper and EnergyXT projects from backups; fixed some buggy Image-Line FL Studio plugin/registry issues; upgraded FL Studio plugins   
24) Transferred my media library (FLACs, MP3s, and M4As) onto the hard drive via USB backup
25) Updated DeadBeef Portable with my media library folders and backed up DeadBeef

Started enjoying my setup!  
Everything is running as expected; no incompatibilities or crashes.  

The only thing that's a disappointment is FL Studio still doesn't run as well as I'd like.  
I think the problem is that it can only use one CPU core;  I don't think multicore support works for that.  

But 32-bit Windows EnergyXT v3 beta sees all the CPU cores and runs fine.  
And 32-bit Reaper v5.1 runs fine.  I had restored my previous configuration from backups, and tweaked it to match the new monitor size.  

Minor Issues:  There's not much documentation about the HP ENVY 750-116 (made for OfficeDepot) on the HP website.  You have to just look up ENVY 750 and find the closest info.   There are other versions of that computer with different CPU manufacturer (Intel instead of AMD).  

On first computer boot up, it showed a Windows 10 installation error from within Windows 10, it's default installed operating system.  
This is not a problem if you have a boot CD-ROM or DVD-ROM with gParted on it.  Just erase the entire hard drive and create a system partition with ext3 after you make your SWAP partition.  
The other advantage of this is LVM will not be installed, and the SWAP partition won't be within an extended partition.  

Because of the BIOS / UEFI steps described above, you can create an MBR partition table first, instead of a GPT one.  BIOS / Legacy Mode requires an MS-DOS MBR (master boot record).  gParted can do this.  
The downside is that MBR can only create a maximum of 4 partitions, including the SWAP one.  Just be aware of this and everything will be fine.  

Considerations...

The install went pretty OK with me because I have intermediate Linux experience.  I have installed Ubuntu Studio Linux in the past as well as other versions of Linux such as Puppy Linux, WattOS, and Lubuntu.  
[http://distrowatch.org](http://distrowatch.org) and this site were very helpful.  Also linuxaudio.org (?) or is it audiolinux.org (?) has some outdated but helpful info which is still valid on how to disable services on Ubuntu using .override files.  

When I chose the computer, I specifically avoided any computers with nVidia video/graphics hardware since it can be incompatible.  The HP ENVY model I have has an ATI Radeon video/graphics hardware and ATI hardware is usally well-supported on Linux distributions.  

I also chose to disable Bluetooth since it can interfere with DAW computer performance.  That's why I didn't use the provided wifi keyboard and mouse that came with the computer.  
I haven't even tried to install them at all.  I will probably sell them.  

At first I thought my monitor colors were off, but it turned out that the colors are more precise and exact than my old laptop's colors.  There is actually a wider range of colors on the new monitor, so I see colors I had never noticed before.  In particular, neon greenish-yellow is noticeable now within anything yellow.  Since not all digital cameras take accurate color photos, some of the older photos might look slightly wierd.  But newer camera photos done on a good camera without any aesthetic color filterings look alright.  

The monitor actually didn't require any configurations at all!  All of it's defaults are just fine.  

Summary:  2016 is looking like it will be a great year with this Ubuntu Studio DAW computer.  Starting January 1st Iwill no longer have direct internet access; it will be run entirely offline, and everything is running good without internet access.  So I am thankful that I got everthing installed, configured, and running.  The backups helped a lot.  

If you end up seeking this computer, you can get from BestBuy or OfficeMax or OfficeDepot.

---

### Post by Jonathan_Lowsley on 2016-02-23
[h=1]PNY NVIDIA Quadro K1200 - ( VCQK1200DP-PB) Video Card working on Ubuntu 15.10 Wily Werewolf[/h]
This card did not work right out of the box, I had to install nvidia-352 to get it to work. I have 3 screens (2K) attached via display port dp. With Nvidia-352 drivers randomly screens would start blinking on and off.  Maybe after an hour of uptime, every 5 seconds one would go totally blank for 1 second, and then come back. Over and over again. I upgraded the Nvidia driver to 358 and now everything works great for a few weeks now. I use compiz and lots of 3D graphics that work well now.

Kernel Linux 4.2.0-27-generic #32-Ubuntu SMP Fri Jan 22 04:49:08 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

dpkg -l | grep nvidia-358
ii  nvidia-358                                    358.16-0ubuntu0~gpu15.10.2                 amd64        NVIDIA binary driver - version 358.16

I had to install with alternate / minimal iso and after install before reboot select install openssh server.  After reboot, I had to ssh in and install the drivers. There's a newer version 361 but I have not tested it because 358 is working perfectly for me.

---

### Post by gunner5 on 2016-04-23
Hello there!
Ubuntu 16.04 LTS, HP, 14-d036la
Works perfectly except that is more warmer than windows and touchpad doesnt work pretty well.
Cheers!

---

### Post by james220 on 2016-04-27
I have Ubuntu 15.10 and I want to install an ATI Radeon HD 3450 video card.

Is it compatible?

James

---

### Post by ericoporto2008 on 2016-05-19
Ubuntu 16.04 LTS 64-bit
Linux 4.4.0-25-generic #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016

I5-6400, Gigabyte GA-Z170M-D3H, 16 GB  DDR4 3000 Corsair-Vengeance, SSD Samsung EVO 750 250GB, HDD WD 1TB,  Wireless PCI TP-LINK TL-WDN4800, Case Cooler Master N200 

Everything works, including the wireless card. Even after suspending.

Wireless card installation is as simple as powering off the computer, installing the card in the PCI E4X slot, and powering the computer on.

---

### Post by RichardET on 2016-06-30
Last week, I picked up an Inspiron 3655 (AMD processor & graphics) from Dell on sale for ~ $300, free shipping.  It came with Windows 10, but that's now gone!  I still have it set with secure-boot, running Ubuntu MATE 15.10;  Its great!  Very fast.  Its superior to an older Dell 660 with corei5 running Windows 10, which I also have;  I paid about $500 for that one two years ago, roughly.  

The 3655 has 8 GB of memory and a 1 TB drive, DVD and all important connectors, free mouse, keyboard.  Its a very good deal - I suggest it for anyone looking for a cheap Ubuntu desktop, perfect for the kid's dorm.

---

### Post by mail-2o on 2016-07-24
1) Xubuntu 16:04 64
2) MINIPC 2.90 1.45 GHZ Atom x5-Z8300 Quad Core, Cherry Trail CR, 
3) Sumvision
4) Cyclone Mini Micro Small Multi Media Desktop PC 2

Note, there seem to be several variants of these tiny PCs, using similar or the same motherboard. They are supplied with Win10 installed on the internal 32GB eMMC card. They have sufficient cooling, using static heatsinks, for Windows 10, which I assume uses some sort of CPU throttling to control temperature. They are **INSUFFICIENTLY** cooled for Ubuntu, in my experience, and overheating causes them to lock up. Maybe there is some CPU heat throttling option in Linux, but I'm not aware of it.

If like me, you really want this to work under Linux, have a great deal of time (I did one week), and don't mind adding a fan, you can end up with a very nice, tiny, cool running, power efficient quadcore desktop computer, running Linux, but before you do, do read my rather lengthy experience of this computer at:
[http://digitalanswers.info/2016/07/02/the-desktop/](http://digitalanswers.info/2016/07/02/the-desktop/)

It now plays videos, will carry out some heavy word processing tasks, and run BOINC at the same time, often the proverbial straw that breaks the camels back, on computers that are prone to overheating and has run continuously, for several days so far, in hot weather.

The chipset is not well supported in Linux. I've had to add an external USB sound dongle: neither blue-tooth nor WiFi work so far either, but it does have USB3. 

As more and more Chinese manufacturers are supplying these cheap desktop mini-PCs, I feel that exploring the deployment of Linux on them, is worth pursuing.
[IMG]http://digitalanswers.info/wp-content/uploads/2016/07/16l-cyclone-2-292x300.jpg[/IMG]

---

### Post by kyrithis on 2016-07-29
Ubuntu 16.04
Graphics Processing Unit
Nvidia/EVGA
GTX 660

Hardware is confirmed working out of the box. For best performance, installation of the newest Nvidia drivers is recommended but not required.

---

### Post by manish21thakur on 2016-08-23
**List of supported hardware**
1. Desktop (x86, AMD and Intel)
2. Servers/workstations
3. Laptops (ARM)
4. Laptops (Intel, x86)

**List of supported Hardware**
Desktops (AMD, Intel, x86)
1. Gigabyte GA-G41M-ES2L motherboard
2. Intel D510MO motherboard
3. ASUS KCMA-D8 motherboard
[B]
Servers/workstation (AMD, x86)[/B]
ASUS KFSN4-DRE motherboard
ASUS KGPE-D16 motherboard

---

### Post by backit on 2016-09-22
1)Version Of Ubuntu:  14.04
2)Type Of Hardware:   Ethernet to usb Adapter
3)Hardware Maker:  Rankie
4)Hardware Model:  R-1161-ADAPTER-USB3.0-RJ45-BK

Chip Realtek 8153
Works out of the box, just plug and enjoy :)

---

### Post by CD2000 on 2016-10-15
Ubuntu 16.04, 64bit LTS to install on SanDisk X400 SSD in new build with Asus Z170-Deluxe motherboard, i7-6700k, 32GB Ram.
Boots to install screen from Windows 7 DVD but won't boot in Ubuntu from USB. Able to access BIOS.

---

### Post by chewy9141 on 2016-12-06
Any Z170 ITX motherboards that would work well.

---

### Post by ppnman on 2017-01-04
system ubuntu 12.04 14.04 15.10 16.04 16.10
type of hardware:usb wifi adapter
hardware maker: TP-LINK
model : TL-WN728N
WORKS JUST FINE 
driver realtek RTL8188EUS :) ):P

---

### Post by zenerves on 2017-01-27
Hi there 

Happy to report that the [Acer Aspire R11 R3-131T full name R3-131T-C1VC  model no N15W15]("http://www.fnac.com/PC-Ultra-Portable-Acer-Aspire-R3-131T-C1VC-11-6/a8942595/w-4") 

is working just right with 16.10. No proprietary software needed, touchscreeen perfect, shortcut keys and rocker keys for volume works great. 
Keyboard is disconnected when in presentation/tablet/tent mode, that's cool.

Bluetooth OK with phone, with JBL loudspeaker but not with cheap mouse.
WiFi OK first try, both 2.4 and 5Ghz

Shortcut keys to brightness unbearably slow, sluggish, to the point you better keep a shortcut to the setting in your sidebar.

Tent Mode doesn't rotate the screen. Some other, less used shortcut keys untested as of now, will update.


For my use, and this install, I just wiped the drive, put the bios boot in Legacy, and installed from USB in one go. **Works for me**.

---

### Post by schyken on 2017-02-05
-Ubuntu 16.04.1 LTS
-Dell Alienware X51 R2 (Intel Core i5-4400, 16GB DDR3 @1866Mhz, 1TB SSHD(12GB SSD + 1TB HDD), Nvidia Geforce GTX 745)
-No special installation actions needed, however I recommend UEFI and *not* BIOS.

---

### Post by mippo9 on 2017-03-23
1)Version Of Ubuntu
16.10

2)Type Of Hardware
convertible PC 10.1"

3)Hardware Maker
HP - Intel

4)Hardware Model
[COLOR=#1155CC][FONT=Arial]_[HP x2 10-P008]("http://www8.hp.com/it/it/products/laptops/product-detail.html?oid=16129982#!tab=specs")_[/FONT][/COLOR]

Intel® Atom™ x5-Z8350
4GB SDRAM LPDDR3-1600  
64 GB eMMC
video  Intel® HD 400 (1280 x 800)
DTS Studio Sound
2 cameras; USB 3.1; USB 2.0C; HDMI; micro SD

Problems:
 sound card not recognized; multitouch not recognized; power management not working;

---

### Post by pete5 on 2017-03-30
Dell Dimension C521  (2 GHz Athlon 64, 1 GB DDR2, originally XP MCE)

Lubuntu 16.10 64 bit

works just fine

---

### Post by pete5 on 2017-03-31
Dell Optiplex GX280
2.53 GHz Celeron, 512M DDR2.

Lubuntu 16.10 32 bit

I threw in an extra 512M while installing. Runs fine with 512 afterwards. 

Lubuntu Seems faster than XP.

---

### Post by mclaren2 on 2017-05-10
Motherboard: GA-78LMT-S2PT
Motherboard Manufacturer: Gigabyte Technology Co.

CPU: AMD FX-6300
CPU Manufacturer: Advanced Micro Devices

GPU: NVidia Geforce GT 730
GPU Manufacturer: NVidia

---

### Post by sccman on 2017-06-16
1) **Version**: Lubuntu 17.04
2)** Type of Hardware**: Gaming Desktop
3, 4)  **Hardware Maker/Model**: CybertronPC GM1213B

I've found that with Linux can be a little finicky with the nVidia GPU cards. You'll need to set the Linux kernel parameter to "nomodeset" or you'll get a black screen when you boot. Also, the nVidia Geforce GTX 9xx series have problems with the nVidia Linux drivers, especially waking from suspend.

---

### Post by AnirudhVyas on 2017-06-22
Version: Ubuntu Desktop 17.04
Type of Hardware - programming environment, C, Rust, Go, Java, Scala and sometimes Assembly.
Hardware Maker - Maingear.

Precise configuration - 
[http://www.maingear.com/boutique/pc/viewconfig.asp?config=EMLFML](http://www.maingear.com/boutique/pc/viewconfig.asp?config=EMLFML)
I need to know if this configuration should work with 3 4k Monitors. I have a ton of source, I compile a lot of code from different languages and deploy and test locally. I do a lot of source merges, commit code etc. I test a lot of things that hog memory for some time, I am interested in tinkering with some GPU cores.

Leave windows shi...stuff out of this.

[TABLE="width: 500"]
[TR]
[TD="bgcolor: #cb0101, colspan: 2"]**Quantum SHIFT X299 (system-Quantum SHIFT-X299) $4,528.00**[/TD]
[/TR]
[TR]
[TD="bgcolor: #ffffff"]Chassis:[/TD]
[TD="bgcolor: #ffffff"]MAINGEAR SHIFT Chassis with Advanced Vertical Heat Dissipation[/TD]
[/TR]
[TR]
[TD="bgcolor: #cccccc"]Exterior Finish:[/TD]
[TD="bgcolor: #cccccc"]Brushed Black Aluminum[/TD]
[/TR]
[TR]
[TD="bgcolor: #ffffff"]Interior Finish:[/TD]
[TD="bgcolor: #ffffff"]Stock Black[/TD]
[TD][/TD]
[/TR]
[TR]
[TD="bgcolor: #cccccc"]Motherboard:[/TD]
[TD="bgcolor: #cccccc"]MSI X299A Raider[/TD]
[/TR]
[TR]
[TD="bgcolor: #ffffff"]Processor:[/TD]
[TD="bgcolor: #ffffff"]Intel® CoreT i7 7820X 8-core 3.6GHz/4.3GHz Turbo 11MB L3 Cache w/ HyperThreading[/TD]
[/TR]
[TR]
[TD="bgcolor: #cccccc"]Processor Cooling:[/TD]
[TD="bgcolor: #cccccc"]Coolermaster Hyper 212 EVO Advanced Air Cooler[/TD]
[/TR]
[TR]
[TD="bgcolor: #ffffff"]Enhanced Thermal Interface Material:[/TD]
[TD="bgcolor: #ffffff"]MAINGEAR EPIC T1000 Engineered Phase Change Thermal Interface Material[/TD]
[/TR]
[TR]
[TD="bgcolor: #cccccc"]MAINGEAR Redline Overclocking Service:[/TD]
[TD="bgcolor: #cccccc"]Intel® Turbo Boost Advanced Automatic Overclocking[/TD]
[/TR]
[TR]
[TD="bgcolor: #ffffff"]Memory:[/TD]
[TD="bgcolor: #ffffff"]32GB HyperX® PredatorT DDR4- 3000(4x8GB) [QUAD Channel][/TD]
[/TR]
[TR]
[TD="bgcolor: #cccccc"]Workstation Graphics Cards:[/TD]
[TD="bgcolor: #cccccc"]NVIDIA QUADRO K620 2GB DDR3[/TD]
[/TR]
[TR]
[TD="bgcolor: #ffffff"]Power Supply:[/TD]
[TD="bgcolor: #ffffff"]1200 Watt Corsair® Professional Digital Series AX1200i 80+ Platinum Certified Modular Power Supply ROHS[/TD]
[/TR]
[TR]
[TD="bgcolor: #cccccc"]Operating System Drive:[/TD]
[TD="bgcolor: #cccccc"][PCIe NVME SSD] 1.2TB Intel® 750 Series [2,400MB/s Sequential Reads] $300 off for a limited time! -[/TD]
[/TR]
[TR]
[TD="bgcolor: #ffffff"]Hard Drive Bay Two:[/TD]
[TD="bgcolor: #ffffff"]Pre-Wired SATA For Easy Upgrades[/TD]
[/TR]
[TR]
[TD="bgcolor: #cccccc"]Hard Drive Bay Three:[/TD]
[TD="bgcolor: #cccccc"]Pre-Wired SATA For Easy Upgrades[/TD]
[/TR]
[TR]
[TD="bgcolor: #ffffff"]Hard Drive Bay Four:[/TD]
[TD="bgcolor: #ffffff"]Pre-Wired SATA For Easy Upgrades[/TD]
[/TR]
[TR]
[TD="bgcolor: #cccccc"]Hard Drive Bay Five:[/TD]
[TD="bgcolor: #cccccc"]Pre-Wired SATA For Easy Upgrades[/TD]
[/TR]
[TR]
[TD="bgcolor: #ffffff"]Hard Drive Bay Six:[/TD]
[TD="bgcolor: #ffffff"]Pre-Wired SATA For Easy Upgrades[/TD]
[/TR]
[TR]
[TD="bgcolor: #cccccc"]Optical Drive One:[/TD]
[TD="bgcolor: #cccccc"]12X Asus® Blu-ray Burner External USB 2.[/TD]
[/TR]
[TR]
[TD="bgcolor: #ffffff"]Audio:[/TD]
[TD="bgcolor: #ffffff"]Asus® Xonar Essence STX 2.1-channel ONLY PCI-E [AUDIOPHILE][/TD]
[/TR]
[TR]
[TD="bgcolor: #cccccc"]Ethernet Adapter:[/TD]
[TD="bgcolor: #cccccc"]Dual On-board Gigabit Ethernet[/TD]
[/TR]
[TR]
[TD="bgcolor: #ffffff"]Wireless Network Adapter:[/TD]
[TD="bgcolor: #ffffff"]ASUS PCE-AC68 Dual-band PCI-E Wireless-AC1900[/TD]
[/TR]
[TR]
[TD="bgcolor: #cccccc"]Operating System:[/TD]
[TD="bgcolor: #cccccc"]Microsoft Windows 1 0 Home 64-bit[/TD]
[/TR]
[TR]
[TD="bgcolor: #ffffff"]Security Software:[/TD]
[TD="bgcolor: #ffffff"]Free 1 Year Subscription! McAfee AntiVirus Plus[/TD]
[/TR]
[TR]
[TD="bgcolor: #cccccc"]The Final Finesse:[/TD]
[TD="bgcolor: #cccccc"]Designed, Manufactured, and Supported in the USA - Flawless Craftsmanship and Wire Management[/TD]
[/TR]
[/TABLE]

---

### Post by him610 on 2017-06-23
OS Release:	Xubuntu 16.04-2
Mainboard:	AsRock H270M-ITX/AC
CPU:		Intel Pentium G4560
Ram:		Crucial 8GB Kit (4GBx2) DDR4-2133 
GFX:		Geforce GTX 760
SSD:		Samsung 840 250GB
HDD:		Seagate ST9750420AS 750GB
Network:	        Intel I219-V and I211
Wireless:	        Intel AC 3160
Case:		CoolerMaster Elite 130
PSU:		EVGA 550 B3
Optical Drive:	Lite-On DVD/CD RW

Intel AC 3160 module connected with wireless router before I even attached the antennae. All USB 2/3 ports work without issue. Have not attempted to connect with Bluetooth yet. Audio works from front panel connections.

---

### Post by roedesh on 2017-09-02
[SIZE=2][FONT=arial]**Ubuntu version**
Ubuntu 16.04.3 LTS

[B]Type of hardware
[/B]Barebones PC
CPU: [COLOR=#505050]4x Intel(R) Core(TM) i3-7100U CPU @ 2.40GHz
RAM: [/COLOR][COLOR=#505050]8059MB

[B]Hardware maker
[/B]Intel

**Hardware model**
Intel NUC7i3BNH

Everything runs smoothly![/COLOR][/FONT][/SIZE]

---

### Post by manover2 on 2017-11-11
Tested Ubuntu 16_04 on Dell Inspiron 15 3567 (Intel core i5): wifi didn't work (qualcomm atheros wifi card)!!

---

### Post by manover2 on 2017-11-11
Tested Ubuntu 16_04 on HP 450 G2 Intel core i7: it works fine out of the box.

---

### Post by djchandler on 2017-12-24
Gigabyte Brix Pro 5775 barebones kit.

Moved 16.04.03 to a [Gigabyte Brix Pro 5775]("https://www.gigabyte.us/Mini-PcBarebone/GB-BXi7-5775-rev-10"). As said in the reviews at [Newegg]("https://www.newegg.com/Product/Product.aspx?Item=N82E16856164036"), it makes a LOT of fan noise, but has been up now on this machine for about two weeks without a crash of any kind. ($249.99 US on Cyber Monday, paid for 3 day delivery, took 10 days) It has been rebooted due to kernel upgrade recently. Ran first time on a HD recovered from a laptop with a fried MB thanks to a cup of coffee. The original laptop had an Intel i7 with integrated gpu. Used the memory (Hynix PC3L) from the same HP laptop. Ran without making any changes on my part or difficulty with Linux or the Ubuntu distribution. It quit looking for the laptop's touchpad after the first reboot, which I did immediately after its first boot from the laptop HD (Toshiba 750 GB). Rebooted once since then, after the last kernel update.
[ATTACH=CONFIG]277920[/ATTACH]
Getting ready to give it a load with the [Ubuntu Folding Team]("https://wiki.ubuntu.com/FoldingAtHomeTeamUbuntu").

---

### Post by cca20102010 on 2018-02-01
i am trying to to install this printer follow the installation guides , and nothing works ,i am running ubuntu 16.04 on acer laptop 64bit i download the drivers from epson websites available for ubuntu 16.04 i installed it,and nothing i does not print ,it allow me to install it but as a generic printing ,does not use drivers install it ,make me choose the available on data base ,brand,model that is not available,it use generic but does not let do anything i cant print,please if anyone can help i will appreciate thank you

---

### Post by wyliecoyoteuk on 2018-07-16
Wacom Bamboo usb tablet.
Tablet detected but stylus does not work
Ubuntu 18.04

---

### Post by djdg on 2018-08-19
I have a JBL Everest 700 Bluetooth headphone and I'm looking for a compatible Bluetooth adapter so I can listen from my PC. I am using Ubuntu 18.04.1 LTS. Can anyone recommend me a good one that works? :)

---

### Post by linux4me on 2018-08-19
> **djdg said:**
> I have a JBL Everest 700 Bluetooth headphone and I'm looking for a compatible Bluetooth adapter so I can listen from my PC. I am using Ubuntu 18.04.1 LTS. Can anyone recommend me a good one that works? :)

I recently went through the same search. I'm using Ubuntu 18.04 as well, and the [Panda Bluetooth 4.0 USB Nano Adapter]("https://amazon.com/gp/product/B00BCU4TZE/") (can I put an Amazon link in here?) worked out-of-the-box for me with my Bluetooth headset. I have it plugged in one of the front USB 3.0 ports on my desktop, and I get about the 30-foot range they advertise, though it cuts out a bit if I am that far away and there is a wall in between me and the transmitter. I've never had any issues with it being recognized, no need for any extra driver with 18.04, and no problem pairing with my headphones. The really nice thing about 18.04 is that when the headphones are connected, they are automagically selected as the output device. When I turn them off, Ubuntu goes back to my default sound output device.

---

### Post by djdg on 2018-08-19
> **linux4me said:**
> I recently went through the same search. I'm using Ubuntu 18.04 as well, and the [Panda Bluetooth 4.0 USB Nano Adapter]("https://amazon.com/gp/product/B00BCU4TZE/") (can I put an Amazon link in here?) worked out-of-the-box for me with my Bluetooth headset. I have it plugged in one of the front USB 3.0 ports on my desktop, and I get about the 30-foot range they advertise, though it cuts out a bit if I am that far away and there is a wall in between me and the transmitter. I've never had any issues with it being recognized, no need for any extra driver with 18.04, and no problem pairing with my headphones. The really nice thing about 18.04 is that when the headphones are connected, they are automagically selected as the output device. When I turn them off, Ubuntu goes back to my default sound output device.

That's funny: I kept on searching after my request and found the Panda Adapter also! Your experience sounds good to me, so I think I will purchase this item also! Thanks for your answer :)

---

### Post by gpeguero on 2019-01-10
[COLOR=#000000]Ubuntu version 18.04LTS[/COLOR]
[COLOR=#000000]Motherboard : Gigabyte B450i Aorus Pro Wifi AM4 mini-ITX[/COLOR]
[COLOR=#000000]Processor : AMD Ryzen 5 2400G (APU)[/COLOR]
[COLOR=#000000]Ram : Corsair Dominator Platnium DDR4 2666[/COLOR]
[COLOR=#000000]SSD : Corsair FORCE Series MP300 240GB NVMe PCIe M.2 SSD

[/COLOR]I have been searching through the forum but have not found any post on a build using AMD Ryzen 5 2400g APU. Has anyone had experience with this platform and how it performs for light gaming?

Thank You in advance :)

---

### Post by mikasu on 2019-01-11
Ubuntu 18.04.1
Motherboard : Asus Crosshair Hero VI (Wifi-AC) X370
Processor : AMD Ryzen 5 1600
Graphics card : Sapphire Radeon RX 580 NITRO+ 8GB GDDR5
RAM : Corsair Vengeance LPX DDR4-2666 8GB (2x)
SSD : Kingston A400 120GB
HDD : 2TB Seagate Barracuda 7.2kRPM

The whole system is shared in a dual boot with Windows 10. Throughout my tests with it, no sound issues right after installation. No graphical issues, the GPU works great (to be expected, thanks AMD). Performs quite good in gaming, just need v-sync in Rocket League because the frame tearing makes the experience worse than it could be. The wifi card is working without any tweaking around. Though I didn't test HDA, only the motherboard audio ports.

---

### Post by whi2468 on 2019-02-14
Samsung Notebook 7 Spin (NP750QUA) Works only with version 18.10.

Keyboard lighting does not work. Must have kernel 4.18 or newer to work to boot Ubuntu.

---

### Post by tea for one on 2019-06-15
Intel NUC8i3BEH
2 x Crucial 4GB DDR4-2400 SODIMM (8GB total)
Sandisk Ultra II SSD- 2.5” 120GB
Logitech Wireless K270 Keyboard and M185 Mouse
Benq Monitor GL2250HM LED 22” 1920 x 1080 

[https://www.intel.com/content/www/us/en/products/boards-kits/nuc/kits/nuc8i3beh.html](https://www.intel.com/content/www/us/en/products/boards-kits/nuc/kits/nuc8i3beh.html)

Using Ubuntu 18.04 with Gnome DE

_All the following function fine:-_

All USB ports
Wired ethernet
Wireless
Graphics and sound via HDMI
Front panel headphone jack
Bluetooth
Micro SD card reader
(can also boot alternative OS from the card reader e.g. LibreELEC)
Charging via yellow USB port when powered off

_Untested_

Microphone 
M.2 drive

_M.2 drive now tested_

I purchased a 128Gb ADATA SU800 M.2 SSD Drive and I can report that it is recognised by Ubuntu 18.04 as a storage medium and also as a bootable drive.

---

### Post by P-I H on 2019-12-29
[B]Asus Rog Strix B450-F Gaming

[/B]Ubuntu Focal Fossa and Ubuntu 19.10

```
p-i@pi-System-Product-Name:~$ inxi -Fz
System:    Host: pi-System-Product-Name Kernel: 5.3.0-24-generic x86_64 bits: 64 Desktop: Gnome 3.34.1 
           Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: ASUSTeK model: ROG STRIX B450-F GAMING v: Rev 1.xx serial: <filter> UEFI: American Megatrends 
           v: 2704 date: 08/23/2019 
CPU:       Topology: 8-Core model: AMD Ryzen 7 1700 bits: 64 type: MT MCP L2 cache: 4096 KiB 
           Speed: 1380 MHz min/max: 1550/3750 MHz Core speeds (MHz): 1: 1375 2: 1375 3: 1374 4: 1374 5: 1375 6: 1375 7: 1375 
           8: 1372 9: 1373 10: 1372 11: 1374 12: 1375 13: 1375 14: 1375 15: 1371 16: 1370 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] Navi 10 [Radeon RX 5700 / 5700 XT] driver: amdgpu v: kernel 
           Display: x11 server: X.Org 1.20.5 driver: amdgpu tty: N/A 
           OpenGL: renderer: AMD NAVI10 (DRM 3.33.0 5.3.0-24-generic LLVM 9.0.0) v: 4.5 Mesa 19.2.4 
Audio:     Device-1: Advanced Micro Devices [AMD/ATI] Navi 10 HDMI Audio driver: snd_hda_intel 
           Device-2: Advanced Micro Devices [AMD] Family 17h HD Audio driver: snd_hda_intel 
           Sound Server: ALSA v: k5.3.0-24-generic 
Network:   Device-1: Intel I211 Gigabit Network driver: igb 
           IF: enp4s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 903.59 GiB used: 36.68 GiB (4.1%) 
           ID-1: /dev/nvme0n1 vendor: Kingston model: SA1000M8480G size: 447.13 GiB 
           ID-2: /dev/nvme1n1 vendor: Samsung model: SSD 960 EVO 250GB size: 232.89 GiB 
           ID-3: /dev/sda vendor: Samsung model: SSD 850 EVO 250GB size: 232.89 GiB 
           ID-4: /dev/sdb vendor: SanDisk model: Ultra II 240GB size: 223.57 GiB 
Partition: ID-1: / size: 227.74 GiB used: 36.67 GiB (16.1%) fs: ext4 dev: /dev/nvme1n1p2 
Sensors:   System Temperatures: cpu: 42.4 C mobo: 37.0 C gpu: amdgpu temp: 76 C 
           Fan Speeds (RPM): cpu: 553 case-1: 904 case-2: 823 case-3: 500 gpu: amdgpu fan: 0 
Info:      Processes: 420 Uptime: 17h 34m Memory: 15.57 GiB used: 5.22 GiB (33.5%) Shell: bash inxi: 3.0.37 
p-i@pi-System-Pro

```

Audio
Mounted the HD-audio connector incorrect. After remount had to set the Auto-Mut to Disabled i alsamixer. Now working with Analog Surround 5.1 Output

Sensors
Found information on this page
[https://github.com/electrified/asus-wmi-sensors](https://github.com/electrified/asus-wmi-sensors)
-Flashed BIOS to 2704. This Bios also support Ryzen 3000 CPU:s
-sudo apt-get install dkms
-sudo apt install git
-git clone [https://github.com/electrified/asus-wmi-sensors.git](https://github.com/electrified/asus-wmi-sensors.git)
-cd asus-wmi-sensors/
-sudo make dkms
-sudo nano /etc/rc.local with content:
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
modprobe asus-wmi-sensors
exit 0
Make /etc/rc.local exekverbar
-sudo chmod +x /etc/rc.local

Suspend
I made these changes in In BIOS, but perhaps only Set IOMMU to Disabled is necessary
-Set PSS Support to Enable
-Set USB power delivery in SoftOff to Disable
-Set Serial Port to OFF
-In AMD CBS Set Global C-state control to enable
-In AMD CBS Set Power Supply Idle Control to Low Current Idle
-In AMD CBS Set IOMMU to Disabled
Add "iommu=soft" in the line GRUB_CMDLINE_LINUX="" in /etc/default/grub

---

### Post by heroquestelf on 2020-04-24
I have just recently installed the Ubuntu MATE 20.04 LTS on a Dell Inspiron i3670 and I'm pleased to report that it's working flawlessly.
[B]
1)Version Of Ubuntu - Ubuntu MATE 20.04 LTS
2)Type Of Hardware - Desktop Computer
3)Hardware Maker - DELL
4)Hardware Model - i3670[/B]

---

### Post by Rytron on 2020-05-16
> **heroquestelf said:**
> I have just recently installed the Ubuntu MATE 20.04 LTS on a Dell Inspiron i3670 and I'm pleased to report that it's working flawlessly.
[B]
1)Version Of Ubuntu - Ubuntu MATE 20.04 LTS
2)Type Of Hardware - Desktop Computer
3)Hardware Maker - DELL
4)Hardware Model - i3670[/B]

Hi heroquestelf. Thanks, for the info. BTW - what the difference between the Dell Inspiron i3670 & Dell Inspiron 3670 desktops?

---

### Post by shabahanx on 2020-05-18
AMD Athlon 880K X4 @ 4.0/4.2GHz - ASUS Crossblade Ranger FM2+ - AMD Radeon R9 285 2GiB [amdgpu] - 16GiB RAM @ 2133MHz - Ubuntu 20.04 Focal :mrgreen:

```
dominusprogs@crossblade-athlon880k-linux:~$ inxi -Fz
System:    Kernel: 5.4.0-29-generic x86_64 bits: 64 Desktop: Gnome 3.36.1 Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: ASUSTeK model: CROSSBLADE RANGER v: Rev X.0x serial: <filter> UEFI: American Megatrends 
           v: 1803 date: 08/02/2017 
CPU:       Topology: Quad Core model: AMD Athlon X4 880K bits: 64 type: MCP L2 cache: 2048 KiB 
           Speed: 1699 MHz min/max: 1700/4000 MHz Core speeds (MHz): 1: 1699 2: 1699 3: 1699 4: 1700 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] Tonga PRO [Radeon R9 285/380] driver: amdgpu v: kernel 
           Display: x11 server: X.Org 1.20.8 driver: amdgpu,ati,fbdev,intel,modesetting,nouveau,radeon,vesa,vmware 
           resolution: 1920x1080~60Hz 
           OpenGL: renderer: AMD Radeon R9 200 Series (TONGA DRM 3.35.0 5.4.0-29-generic LLVM 9.0.1) v: 4.6 Mesa 20.0.4 
Audio:     Device-1: Advanced Micro Devices [AMD] FCH Azalia driver: snd_hda_intel 
           Device-2: Advanced Micro Devices [AMD/ATI] Tonga HDMI Audio [Radeon R9 285/380] driver: snd_hda_intel 
           Sound Server: ALSA v: k5.4.0-29-generic 
Network:   Device-1: Qualcomm Atheros AR9227 Wireless Network Adapter driver: ath9k 
           IF: wlp2s6 state: up mac: <filter> 
           Device-2: Intel I211 Gigabit Network driver: igb 
           IF: enp5s0 state: down mac: <filter> 
           IF-ID-1: vpn0 state: up speed: 10 Mbps duplex: full mac: N/A 
Drives:    Local Storage: total: 2.91 TiB used: 2.62 TiB (90.2%) 
           ID-1: /dev/sda type: USB vendor: Seagate model: Ultra Slim GD size: 931.51 GiB 
           ID-2: /dev/sdb vendor: Samsung model: SSD 850 PRO 128GB size: 119.24 GiB 
           ID-3: /dev/sdc vendor: Western Digital model: WD1002FAEX-00Z3A0 size: 931.51 GiB 
           ID-4: /dev/sdd vendor: Western Digital model: WD1002FAEX-00Z3A0 size: 931.51 GiB 
           ID-5: /dev/sde type: USB model: USB DISK 2.0 size: 7.27 GiB 
           ID-6: /dev/sdf type: USB vendor: A-Data model: USB Flash Drive size: 57.81 GiB 
RAID:      Device-1: md0 type: mdraid status: active raid: raid-0 report: N/A Components: online: sdc1~c0 sdd1~c1 
Partition: ID-1: / size: 98.70 GiB used: 17.24 GiB (17.5%) fs: btrfs dev: /dev/sdb4 
           ID-2: /boot size: 945.6 MiB used: 147.4 MiB (15.6%) fs: ext4 dev: /dev/sdb2 
           ID-3: /home size: 1.82 TiB used: 1.76 TiB (96.9%) fs: xfs dev: /dev/md0 
           ID-4: swap-1 size: 19.07 GiB used: 83.8 MiB (0.4%) fs: swap dev: /dev/sdb3 
Sensors:   System Temperatures: cpu: 41.0 C mobo: 34.0 C gpu: amdgpu temp: 59 C 
           Fan Speeds (RPM): fan-1: 363 fan-2: 1072 fan-3: 0 fan-4: 0 fan-5: 801 gpu: amdgpu fan: 1023 
Info:      Processes: 301 Uptime: 1d 20h 26m Memory: 15.58 GiB used: 5.30 GiB (34.0%) Shell: bash inxi: 3.0.38 

```

PS. I have a problem with raid in first boot because of mdadm is not being installed by default.

---

### Post by metacell on 2020-10-06
[B]1) Ubuntu v12.04, 14.04, 16.04, 18.04, 20.04
2) Motherboard
3) ASUS
4) P5E

[/B]Works out of the box. Have only had problems with Suspend mode -- screen stays black even after waking up. I've had problems with suspend mode on Windows 7 too on my setup, though.

---

### Post by wildman22 on 2020-10-20
Ubuntu studio 20.04
CPU              AMD 3900x
MB                MSI unity x570
HD                Corsair MP600 nvme 1 GB
Video card    NVIDIA Titan xp
keyboard      Kingston Hyperx mechanical keyboard.
Mouse          Logitech G403
monitor         Samsung 32in 1080 tv
Audio sent to a 7.2 Yamaha receiver sounds fine.  
all hardware recognized and running fine. Slight problem with mouse showing up as a Kingston mouse not Logitech.Caused by user error plugging  mouse into keyboard changed usb port runs fine.

---

### Post by tomas132 on 2020-12-13
Ubuntu 20.04 LTS ([COLOR=#000000][FONT=monospace]5.4.0-58-generic[/FONT][/COLOR])
CPU i5 650
GPU AMD RX550
MB GA-P55A-UD3R rev1 (LAN RTL8111D)
SSD Samsung 970 EVO Plus[FONT=monospace]
[/FONT]
Problem: Not detect network adapter after reboot, no data for pci line with network adapter in dmesg after reboot.
Reason: the default driver, r8169, initializes and works correctly with rtl8111d, but does not properly turn off rtl8111d.
Solution: exec "sudo apt install r8168-dkms" and shutdown computer (not reboot!)[FONT=monospace]
[/FONT]

---

### Post by ariful6557 on 2020-12-14
[COLOR=#000000]2.0 GHz Core 2 Duo T7200, 4Mb cache [/COLOR]

---

### Post by titanicband on 2022-03-25
Ubuntu 21.10
Laptop
Dell
XPS 15 7590

I had to disable the intel RST in bios before I could install.  Once I did that the installation was very smooth and painless.

---

### Post by djchandler on 2022-10-10
HP Pro Book 450G1
Runs Ubuntu 20.04 lts, 22.04 lts. They also can run Chrome OS Flex; haven't tried that yet. Unit came with Windows 7, Win 10 upgrade, then an inadvertent coffee spill; all hardware recovered but keyboard. Newer WD Blue 512GB SSD installed, Haswell core i7, 8 GB DDR3 low-voltage RAM.

Windows 10 installed UEFI secure boot; that will need to be disabled in the BIOS in order to boot from USB. I am not sure that's necessary for booting the DVD, but probably needs to be disabled anyway to install another OS on the local hard drive.

---

### Post by oygle on 2022-11-24
There is a list of all the Ubuntu certified desktops at [https://ubuntu.com/certified/desktops](https://ubuntu.com/certified/desktops)

---

### Post by Rytron on 2022-11-27
Cheers, oygle. :-)

---

### Post by tea for one on 2023-10-01
This thread has been starved of info. recently.
Therefore, I'll try the resuscitation procedure:-

In July 2023, GMKtec were offering substantial discounts on new Mini PCs
Order placed on 24 July direct with the supplier via their website.
[https://www.gmktec.com/](https://www.gmktec.com/)
The consignment arrived on 07 August (UK address)
All taxes, import duties, customs clearance and shipping door-to-door were included.

GMKtec Mini PC--NucBox K2
AMD Ryzen 7 7735HS with Radeon Graphics 
16GB DDR5 4800 Crucial
1TB M.2 NVMe PCIe 3.0 M.2 2280 
Ethernet: Realtek RTL8125 2.5GbE driver: r8169
Wireless: Media Tek [14c3:0608] driver: mt7921e
Bluetooth: MediaTek Wireless_Device type: USB driver: btusb
UEFI only
Windows 11 included

Using Ubuntu 22.04 with Gnome 42.9 and Wayland

_All the following function fine:-_

All USB ports
Wired ethernet
Wireless
Graphics and sound via HDMI
Front panel headphone jack
Bluetooth
Logitech K270 Wireless Mouse and Keyboard
Windows 11 Virtual Machine using Qemu/KVM

_Untested_

Microphone 

_Good features_

Very easy to change nvme disk or DDR5 ram. The lid is a clip-fit - no screwdriver required
Wireless card also accessible
No fan noise for 90% of the time, very little fan noise for the remaining 10%
USB-C on the front panel
Ubuntu 22.04 runs pretty quickly

_Disappointments_

One stick of 16GB ram rather than 2 x 8GB
UEFI firmware is limited 
Unable to deactivate internal disk via UEFI (but it only takes 90 seconds to remove it)
The PC manual is sparse - I had to search the internet to find the dedicated F7 key for both boot menu and UEFI Set Up

---

### Post by him610 on 2024-02-11
Recently came in to possession of AtopNuc MA90 mini desktop. It came with Ubuntu 20.04 installed which ran without any issues; however, I prefer Xubuntu. Having the latest Xubuntu 22.04.3 on a USB drive, I booted up and completely overwrote Ubuntu 20.04. Welcome home to XFCE.

The AMD Stony Ridge processor is not the fastest processor, but the integrated Radeon R5 graphics are about the sharpest I have yet seen. Just to let you know where I am coming from, all of my machines (4 + one chromebook) use integrated graphics. I removed and discarded two legacy nvidia GFX cards just last month.

---

### Post by humanuser1337 on 2024-06-09
Acer Travelmate Spin B3 runs 24.04 and previously 22.04. I use the KDE desktop and have also run Mint Cinnamon 21.3 on it. No issues. Sound and bluetooth work, wireless works, touch screen works, as does the touch-pad.
there is one thing that is a bit iffy though: in KDE due to the touch screen, the on-screen-keyboard is obstructing the entire login screen, I can only see the keys, not the login screen with user selection. I can type the pw and all goes smooth, and I can Esc from the keyboard and I see the login screen and user selection.

---

### Post by snowcrash1 on 2024-08-26
1) Ubuntu 24.04 LTS
2) CPU: dual core Intel Core2 Duo E8135 (-MCP-) speed/min/max: 2394/800/2400 MHz
Kernel: 6.8.0-41-generic x86_64 Up: 2h 18m Mem: 1.67/2.9 GiB (57.7%)
Storage: 465.76 GiB (10.5% used) Procs: 251 Shell: Bash inxi: 3.3.34
Network:
  Device-1: Broadcom BCM4321 802.11a/b/g/n driver: wl
  Device-2: Marvell 88E8058 PCI-E Gigabit Ethernet driver: sky2
Machine:
  Type: Desktop System: Apple product: iMac8,1 v: 1.0
    serial: <superuser required>
  Mobo: Apple model: Mac-F226BEC8 v: PVT serial: <superuser required>
    UEFI: Apple v: IM81.88Z.00C1.B00.0802091538 date: 02/09/08

3) Apple
4) iMac 8.1

After updating on LAN I was able to get video working and wifi working, but not before.  Umm problem on suspend... it's kinda funky after it wakes up with a snowy screen.  Other than, I'd say it was a smash trying to do it.  Everything recognized.  No solution at this time to fix suspend 8/28/24.  It was a nice day, my dog was happy before I sat down.  The crickets sound nice.  My biggest problem is getting some of the peripherials to work like my scanner and printer, which... you know... They're Always A Problem.  Definitely might install something else on it, seeing as I didn't really look around before.

---

### Post by falloutboy2 on 2024-08-26
[B]Ubuntu 24.04 Noble Numbat
Motherboard/CPU
SuperMicro AMD Epyc 7C13 / 7313P
H12SSLi
[/B]

---

### Post by falloutboy2 on 2024-08-26
Ubuntu 24.04 Noble Numbat
Video Card
MSI
Geforce RTX 4060 Ti

---

### Post by falloutboy2 on 2024-08-27
Ubuntu 24.04 Noble Numbat
USB Sound DAC ( stereo only )
Sennheiser
EPOS GSX 300

---

### Post by fonspatat on 2024-09-22
[B]Ubuntu 24.04.1 Lts
Intel core i7 x990
Msi X58-Pro-E
12GB DDR3 2000
Amd radeon 560 4GB

Runs way faster than windows 11 also better multi core usage.
My old pc got a second life with linux [/B]

---

