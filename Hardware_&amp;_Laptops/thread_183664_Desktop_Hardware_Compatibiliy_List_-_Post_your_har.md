---
title: "Desktop Hardware Compatibiliy List - Post your hardware here"
date: 2006-05-28
forum: Hardware &amp; Laptops
---

### Post by frodon on 2006-05-28
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

[COLOR="navy"]**The UDSF documentation team will catalog information posted here:**[/COLOR]

Thank you.

---

### Post by starfire1983 on 2006-06-02
Gateway 7322GZ:

Intel 855GM (has d-sub out for second monitor; dual head config not working)
Intel Pentium 4 Mobile (Still having slight ACPI/cpu scaling problems)
Broadcom 54 b/g wireless adapter (not in use but does work after ndiswrapper drivers installed. Using NetworkManager)
Belkin 54G PCMCIA card (F5D7010 rev5000; it just worked, no problems except status lights aren't powered on under Dapper. Using NetworkManager)
Synaptics Touchpad (disabled; use xserver-xorg-input-synaptics instead of xserver-xorg-synaptics)
Wacom Graphire3 Tablet (mouse wheel directions are reversed; -very- slight inconvenience)
MicroInovations Wireless Laser Mouse (no problems; need to get comeplete mousewheel and thumb buttons working)
AC'97 Audio (works wonderful)
LCD Screen (working at full resolution of 1280x800; do sudo dpkg-reconfigure xserver-xorg)
Logitech USB Headset (worked after a restart)

Not working:
KDS Avitron CRT Monitor - Dual head configuration is weird. Needs work and I can't figure it out.

---

### Post by chinaski on 2006-06-02
Asus K8V-MX

AMD Sempron Processor 2600+

S3 Unichrome Pro VGA Adapter

AC97 Audio Controller

Ethernet VT6102 [Rhine-II]

Philips 107E6 CRT Monitor

USB mouse Logitech Cordless CLICK! Plus (only the two buttons and wheel work without manual configuration, which I did not attempted to yet)

Scanner HP Scanjet 3400C

everything works fine with no settings needed

p.s. sorry for my english...

---

### Post by aysiu on 2006-06-02
eMachines T3065 with an NVidia GeForce4 MX graphics card and an AMD Athlon XP processor.

eMachines eTower 766id Intel Celeron processor.

Lacie 160 GB external hard drive.

Sandisk 256 MB MP3 player.

Logitech optical mouse (regular).
Logitech optical mouse (with scroll ball).

KDS Avitron 17" monitor.
ViewSonic VG150 15" monitor.

*Everything* works without any tweaking, *except* the max screen resolution on the Avitron. Breezy detects 1024x768. Dapper detects 640x400. If you add the proper HorizSync and VertRefresh values, it's all fixed.

Otherwise, CD drives, internet, media card reader... everything works straightaway.

---

### Post by virtual_void on 2006-06-04
I've installed Dapper on several systems so far. Description is 
<Ubuntu CD installed>:
<System description>

Kubuntu i386 desktop:
Laptop Dell Inspiron 510m with ipw2200 wireless and 1400x1050 display.
All components works (except maybe the modem that I have never used), the wireless works out of the box, need to install the "915resolution" package in order to enable the 1400x1050 mode (will use 1280x1024 otherwise). the wireless worked in 5.10, but was a bit unstable, it is now totally stable.

PPC server:
Mac Mini 1.4 GHz PPC with wireless and bluetooth, everything works except the wireless network card. Did not test the desktop features very much though (only for about 1 hour using the live CD): I'm using this machine for testing software on PowerPC at work, so I log into to i via SSH (and the system installed is the Ubuntu PPC server CD). Oh, one thing came up: the live CD did not allowed me to run above 1280x1024 resolution even though the Mac mini was hooked up to a 1600x1200 capable LCD screen via DVI.

Kubuntu i386 desktop:
AMD Athlon 64 3000+ (socket 754), ATI Radeon 9800 Pro, SB Audigy, VIA K8T800 AGP moderboard. Everthing works BUT the configure step selects the wrong driver for the graphics card, it selects "ati" instead of "radeon" (or possibly "fglrx"). This result in system hang when trying to start X. It is easy to fix, just change the Driver from "ati" to "radeon". The x86_64 installer CD for kubuntu seems to have the same problem, had to run in X safe mode (i.e. using the "vesa" driver) in order to install the system.

Kubuntu x86_64(SMP) desktop:
AMD Athlon X2 3800+ (socket 939), ATI Radeon VE 7000 PCI, ASUS A8N-SLI (nForce4), 1 skge PCI gbit network cards. Everything works (this is my office work station).

Ubuntu i386(SMP) server:
Pentium 4 HT 2.6GHz, ATI Radeon 7200, Builtin realtek 100Mbit network card, Intel e1000 PCI network card. Have not checked that the gfx card works since I upgraded this machine from Ubuntu 5.10 over SSH, but the card is detected at boot and no errors are reported.

All systems are pretty standard, but I was nice to see that the laptop work perfectly.

---

### Post by bigkahoona on 2006-06-04
Ok, different approach here. I use 3 different workstations and 3 laptops and thus going through every system seems a bit tiresome (I am a lazy git! :mrgreen: ), so I thought I'd "specialize" in PCMCIA WLAN cards.
Especially for non-geeks it is often difficult to identify them by their specs.
Things like "Hey, my AXYPL-S5244262 with Prism 34A-0347.22.as chipset worked ok once I tweaked /weirdmodules/dwrt4qrrzqbloooooop-23.765.0001.04.conf!" aren't really helpful to most newbies (including me!) and so I decided to simply start identifying the ones that do and those that don't with an identifiable image, as many people buy these things at ebay or online shops, but most of the time only the compatible Windows systems are listed. This hopefully helps identifying compatible cards from their image.

Ok, here goes:

**1) _Craptastic No Name WLAN Card:_ - [COLOR="Red"]NO GO![/COLOR]**

[IMG]http://gavajda.de/chinacrap.jpg[/IMG]

Don't bother. It doesn't work. It's not even recognized by the system as a PCMCIA/networking device. Not even the status light comes on.

**2) _No Name WLAN Card (Atheros or Prism chipset?)_ - [COLOR="Red"]WORKS![/COLOR]**

[IMG]http://gavajda.de/noname.jpg[/IMG]

This one is not recognized during install as an available networking device (status light comes on though) and thus DD 6.06 installer defaults to eth0.
After install go to your systems config and it will be there as "ra0". Adjust the settings to fit your WLAN setup, activate it, check "activate at system startup" and be a happy camper.
This card is budget at under 20&#8364; on ebay including shipping (I think I paid 17-18&#8364;).

**3) _D-Link DWL-G630_ - [COLOR="Red"]WORKS, but limited[/COLOR]**

[IMG]http://gavajda.de/dlink.jpg[/IMG]

This one has an Atheros chipset and is recognized by the DD 6.06 installer, BUT(!) **_do not choose it as the primary network interface during install!_** It caused my system to crap out on me three times during install! Somehow it doesn't allow itself to be configured over DHCP at this stage and manually configuring it then doesn't help either and you will end up with no network connectivity during install and (at least with me) it caused the install to freeze at some point.
If you choose eth0 as the primary network interface everything works fine during install. Afterwards this card will appear as "ath0" and can be configured just like the previous card.

[EDIT] [COLOR="Red"]This one won't automatically connect on boot-up! You have to start the Wireless Assistant every time after booting to connect![/COLOR]

**4) _JAHT JWN-5108P_ - [COLOR="Red"]WORKS! (++)[/COLOR]**

[IMG]http://gavajda.de/jaht.jpg[/IMG]

This is my favorite. There isn't a whole lot to be said, except that it sports an Atheros chipset and works out of the box and can be chosen as primary networking device during install. It comes at around 30&#8364; at eBay (eBay Germany that is for me) including shipping.

---

### Post by ahaslam on 2006-06-04
**Packard Bell EasyNote E6100 (laptop)**

Processor: Mobile AMD Sempron(tm) Processor 2600+ 	
Memory: 450 MB
Display: Via Unichrome Pro K8M800
Sound: VT8233/A/8235/8237 AC97
Ethernet: VT6102 [Rhine-II]

**All works perfectly 'out of the box' - no extra settings required in Dapper. **
*Total nightmare in Breezy though, could never get DRI enabled.*

Tony :)

---

### Post by wickwire on 2006-06-04
_Fujitsu-Siemens Amilo L7310W Laptop_

Works With Dapper 6.06:

---

### Post by swamytk on 2006-06-05
I have HP Compaq nx6120 Laptop. I have installed Ubuntu Dapper Drake 6.10. It is really terriffic. Most of the hardware are working perfectly. But following are worth noted:
1. 6-in1 MMC/SD Card Reader not test (no support so far)
2. Built-in modem not tested.

Note: Suspend/Hibernate works perfectly.

Regards
T.KaruppuSwamy

---

### Post by Frank Golden on 2006-06-05
Acer Aspire as5672WLMi notebook 

ATi Radeon x1400 after install had to use wiki
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) to update drivers to allow 3-D and native resolution (1280x800)

external USB sound card Creative Soundblaster Audigy 2 NX (automatically
detected and configured). Chose to blacklist my on board sound to prevent conflicts with
XMMS, on boot up with both cards available XMMS output plugin (Alsa) would need to be reset to the default sound card (Audigy 2).
By having my internal sound card blacklisted there is only one card available, so XMMS can't become confused.

Broadcom Netlink (TM) Gigabit Ethernet worked out of box.

Wi-Fi works out of box. Intel(R) PRO/Wireless 3945ABG

Logitech G-7 mouse works out of box.

All external storage devices auto mount and work out of box.

Matshita DVD-RAM UJ-845S optical drive works out of box.
Using Easy Ubuntu installed all codecs etc to allow DVD movie playback.

My computer is a Core Duo machine and after install, synaptic update to 
686 smp kernel seems to enable all powernowd features.

HP PhotoSmart 7760 works out of box.

Machine uses SATA HDD so HD designators in fdisk -l ,fstab and GRub are sd(x) rather than hd(x).

---

### Post by frodon on 2006-06-05
I installed dapper on my new computer last week end and all just works out of the box.
Here are the specs:

**Motherboard** : Asus A8N-E
**Prosc **: AMD Athlon 64 3700+
**Ram** :  Corsair 2 x 1 Go DDR PC3200 CAS 2 in dual channel
**Graphic card** : XFX GeForce 7600 GT Edition XXX
**Hdd** :  Maxtor DiamondMax 10 S-ATA/II - 300Go

---

### Post by D_block on 2006-06-07
hi, well, AMD Sempron 2800+, 512 DDR/400 Kingston, GeCube 9600XT 128/128,Hdd WD 80GB ATA, ASUS A7n8x-x nForce2, 500W power, hercules MUSE 5.1 DVD, Ethernet Lan, swap partition 2GB,

---

### Post by entangled on 2006-06-07
Intel Mac Mini Core Solo.
512MB, 1.5GHz
Matshita Combo CD-W/DVD-R
60GB Seagate SATA
Atheros AR5006ESX wireless card with AR5424 chipset.
Intel HDA Sound.
Bluetooth (Agere Systems?).
USB & FW ports.

Dapper 6.0.6 works, except for Bluetooth (perhaps I don't know how...).
X windows (correct resolution and good speed), Windows networking, Printing to windows, CD writing, sound, USB, FW - all work.

---

### Post by jon_benge on 2006-06-07
I will just list some of the less common stuff that works in (k)ubuntu

Hauppauge Nova-T PCI Digital TV card + Remote Control
C-MEDIA CMI8731 Sound Chip
Saitek P880 Dual Analog Controller
Belkin 4-Port USB PCI Card

---

### Post by spyke01 on 2006-06-07
heres my Homebrew that works
**Motherboard: **Abit IC7-G
**Processor:** Intel Celeron 1.6GHz(my old P4 3.0GHz worked before it fried)
**Hard Drive: **Western Digital 160GB IDE
**Graphics: **Geforce MX440
**CD-RW:** LG(will post more later)
**DVD-ROM: **LG(will post more later)

---

### Post by jakev383 on 2006-06-07
Dell E1505 Inspiron Laptop
Intel Centrino Duo 1.83 T2400 Processor
1G dual channel DDR (shared)
Intel 945GM Video Chipset
100G SATA HD
Intel 3945abg wireless card
15.4 Widescreen WSXGA (1680 x 1050) with TrueLife
24/10/24 CD Burner/DVD Reader

Installed Flight 6 and everything worked great, with the exception of the wireless card. Had to fiddle with that a little, and it occasionally will not associate with my AP (WEP64) when booted, and sometimes take 3-4 reboots to get working correctly (ifup/down doesn't cut it).
Had to manually edit the X11 config to get the widescreen resolution
All the media keys in the front work, as well as Fn-F2 to turn wireless on/off.
Dual-booting may have killed my "MediaDirect", but thats alright with me
Have not tried burning a CD with the drive yet, not the 5-in-1 combo card reader (reads almost everything EXCEPT CF, which my Canon uses....). Also have not tried the ExpressCard slot (no more PCMCIA guys, sorry!), due to fact that I cannot find any ExpressCard Cards that I need.
Hibernate works great. Have not had an unrecoverable "wake-up" yet.

---

### Post by entangled on 2006-06-09
One addition to my earlier post.
Bluetooth does work on the Intel Mac mini, but it is a bit manual; 
use 'hcitool scan' to find the device address then
use 'hidd --connect <device address>'.
Mouse and keyboard seem to work smoothly.
No good for boot inputs, but login might be OK if hidd will work in bootmisc.sh script.

---

### Post by jaymode on 2006-06-09
I have had dappper running on my Dell Inspiron 8600 since Flight 4 without any problems.

The computer is:
Pentium M 1.8ghz
1GB Ram
60 GB Hitachi 7200 Rpm HD
Geforce GO 5200
Intel Pro Wireless 2100
Broadcom ethernet adapter
on board audio/modem(AC 97 i think)

---

### Post by rekahsoft on 2006-06-12
I have ubuntu 6.06 dapper on my compaq R4000 series laptop. My laptop is an AMD 64 3400+ with a ATI Radeon 200M. I have yet to get the Radeon card working properly with the ATI propriatary drivers (some people have) because of a bug in the ATI driver. I got the wireless card (Broadcom BCM4318 [it doesn't work properly with bcm43xx-fwcutter]) working with ndiswrapper. I have not tried if the card reader workes but the PCMCIA slots work great although i am seeing some bugs using my Audigy 2 Laptop card.

---

### Post by chaosblue on 2006-06-12
Compaq Presario 700US - Everything works without tweaking
  - D-Link AirplusG DWL-G630: works using ndiswrapper with mrv8k51 driver for Win2K (in the Manual folder when you download the driver package from the D-Link site)

---

### Post by Topfs on 2006-06-13
Using Ubuntu 6.06 Dapper Drake LTS

Working:
MB:      Asus P5P800 intel i845PE chipset 
CPU:     Intel Pentium 4 530 
GPU:     Nvidia Geforce ti4200
Wifi:     D-Link DWL-G520                             [OK after tweaking]
Sound:  Creative Soundblaster Live Value
DVD:    Samsung SH-W163A SATA DVD Burner [OK after tweaking]

The MB is working flawlessly, haven't checked the onboard sound but it did not work with SuSE 10.0 a it stray a bit away from the std AC-97 codec
GPU, never had a problem.
The Wifi I had some troubles with connecting and WPA but I sorted it out with this guide: [http://www.ubuntuforums.org/showthread.php?t=125150](http://www.ubuntuforums.org/showthread.php?t=125150)
And an update to the absolute newest drivers:
```
svn checkout http://svn.madwifi.org/trunk madwifi
cd madwifi
make
sudo make install
```

The updated wifi drivers does not compile using i686 restricted drivers but without that new driver the i686 drivers works flawlessly.

My motherboard only boots with Sata + Pata when I use the DVD, has something to do with the ICH5 sata controller I think and it seems as the linux kernel have some problems with this setup, quickly resolved by booting the kernel with added IRQPOLL and it works

NonWorking:
Creative Soundblaster X-Fi (No drivers as of yet)

---

### Post by brimbleshoes on 2006-06-14
ASUS A8N VM CSM nVidia GF6150 430
AMD64 3000+
Printer: HP PSC 1315v -- print only so far.
Dell 1905fpv UltraSharp
TrendNet wireless with RealTek 8180 chipset
LAN uses ndiswrapper and GF 6100 64bit ndis driver (it really does work)

The LAN drivers are a little wierd.  On Ubuntu LiveCD LAN worked great.  After the install no LAN.  So I used ndiswrapper and the gf 6100 drivers (64bit) and it works! Hooray! ndiswrapper works great for more than just wlan.  I'd like to thank the community! Thanks!

---

### Post by chinaski on 2006-06-14
Dapper (LiveCD) works on my Asus A3A notebook

everything works fine, no manual tweaks needed to have a standard full working system

the wireless network adapter works without ndiswrapper

---

### Post by Milambar on 2006-06-16
Fujitsu-Siemens Amilo L6820

Everything worked 'out of the box', with the exception that the video was locked to 640x240 mode. I had to edit /etc/X11/xorg.conf and insert the following:

>         
        HorizSync        28-51
        VertRefresh     43-60


To the "Monitor" section before it'd work in 1024x760 mode.

---

### Post by hizaguchi on 2006-06-16
Dell Inspiron 4150
Intersil Prism internal wireless card
synaptics touchpad

Everything works out of the box except suspend to ram.  Kinda fixable by disabling acpi and then using ctrl-alt-F6 to switch away from X before suspending, then Fn-z on resume to stop the fan from wigging out.

---

### Post by RobertH on 2006-06-17
Toshiba Portege A200 - Dapper Drake

Everything exept the touchpad/keyboard and WPA work straight out of the box.

_Synaptics Touchpad_

the lines
```
modprobe -r psmouse
modprobe psmouse rate=40
```
must be added to /etc/rc.local
Then the symlinks 
**S99rc.local**
in the directories
[B]/etc/rc2.d
/etc/rc3.d
/etc/rc4.d
/etc/rc5.d[/B]
need to be renamed to
**S12rc.local**

What this does is it unloads the psmouse module and then reloads it with the correct number of polls per second (40). The links have to be renamed so that this happens before gdm starts because if this is done afterwards then X does not detect the driver properly and the touchpad loses much of its functionality.

_WPA_
To get WPA to work I had to add the lines
```
wpa-driver wext
wpa-ssid **network name**
wpa-key-mgmt WPA-PSK
wpa-psk **the psk generated by the comand wpa_passphrase**
```
to the eth1 entry in
**/etc/network/interfaces**

To generate the psk use the command
**wpa_passphrase (network name) (WPA Passphrase)**
Don't use brackets when you enter the command.

Then I had to remove the line
**auto eth1**
in
**/etc/network/interfaces**
and add the line
**ifup eth1**
to **/etc/rc.local**
This is just because the auto activating feature didn't work.

_Other Stuff_
I haven't tried to configure Suspend but it did not work the first time i tried it.

---

### Post by bk452 on 2006-06-17
I have a Lexar Jumpdrive Sport and it works with Ubuntu, OS X and XP.

---

### Post by kleedrac on 2006-06-17
Acer Aspire 3623WXCi works perfectly!  Even the scroll box on the trackpad works great!

---

### Post by bomanizer on 2006-06-19
_Acer Aspire 3610_

Everything works out-of-the box, except:

- Bluetooth, I haven't tried solving that.
- Video acceleration, same thing.
- Wi-fi, fw-cutter did the trick.

I think the laptop is running a bit hotter and slower (video) than with XP, but then again, no video acceleration...

---

### Post by MetaMorfoziS on 2006-06-19
Hi all!
This config works fine, except the sound, but i don't know where is the problem [not 100% it's a supporting problem] My ic's driver is built in, so it's supported...
But rarely after boot, it isn't gets sound, after i play the kmix for a 10-20sec it's going to work:)

---

### Post by ponkarthik on 2006-06-19
Dell Inspiron 6400

Intel Centrino Duo  - 1.83 MHz
ATI Radeon x1300
Intel 3945 WIFI - worked out of the box
RICOH card reader - out of the box - worked for SD card not for pro duo
Blue tooth - came built in with the dell - The enhanced data rate doesnt seem to work. otherwise works well

---

### Post by penguintutor on 2006-06-21
I had a problem installing Ubuntu on a system with a Nvidia GeForce FX5600 Graphics Card.

When I tried booting off the Desktop CD I just got a blank screen, as it appeared to detect my graphics card incorrectly. I tried different screen resolutions as my first thought was that maybe it was driving my screen beyond it's capability, but it turns out it was a driver issue.

I used the Alternative Install CD to install using the text based installer (I actually like the text based installer, it's easy to use, and at least it works regardless of the graphics card). Then after booting into Ubuntu (again blank screen), CTRL-ALT-BACKSPACE to get to a shell login prompt and then perform the following steps:

To get the Nvidia drivers the restricted sources need to be enabled for apt. These are contained in the /etc/apt/sources.list file which has to be edited as root (using sudo). Without a graphical screen this has to be done using vi 

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
sudo vi /etc/apt/sources.list

```


#deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper universe
(gb will be replaced with your own country code), and then delete the # at the beginning of the line.
Save and exit

Now refresh the list of packages using
```

sudo apt-get update

```

It is now possible to install the nvidia packages using the following commands:
```

sudo apt-get install nvidia-glx nvidia-kernel-common

```

Then run:
```

sudo nvidia-glx-config enable

```

I then rebooted:
```

sudo reboot

```

and I was then able to see the graphical logon, and X is working fine. 

I have provided more details on my [Linux blog](http://www.penguintutor.com/news.php):
[LIST]
[*][Installing Ubuntu 6.06 (Dapper Drake) with Nvidia Graphics Card - blank screen during install / Live CD]("http://www.penguintutor.com/blog/viewblog.php?blog=217")
[/LIST]

---

### Post by azc on 2006-06-22
HP Deskjet 5740 - OK

Good day,

I have just received my new HP Deskjet 5740 to use with Ubuntu.
It was automatically detected, and setup in just a few minutes.
Printing quality is excellent.

Note: The USB 2.0 printer cable is not included.

Best regards.

---

### Post by oolunchbox on 2006-06-30
Asus A8N-SLI Premium Motherboard

AMD Athlon 64 4800+ X2

2GB PC3200 RAM

LeadTek Winfast GeForce 7800GTX-TDH 256MB (Dual DVI outs working with 
TwinView on 2 17" LCDs)

WD 74GB SATA Raptor

2X WD 200GB SATA HDD

Lite-On DVD-Rom

Lite-On DVD+/- Double LAyer DVD Burner (havent tested the double layer burning yet)

Canon Pixma IP3000 working with Turboprint (It did cost $30 but the results are well worth it if you're serious about sticking with Linux and you want great quality printing)

Logitech G5 Laser Mouse (I've yet to get the 'back' button to work)

Logitech G15 Gaming Keyboard (I've messed with [g15lcd]("http://waug.at/g15lcd/") but I've had no success)

All hardware works great, the videocard needed some work on the xorg.conf to get twinview working properly but plays Counter Strike: Source / Half-Life 2 like a champ.  The main reason I switched to Kubuntu was because Windows XP wouldn't play with my Raptor nice, Breezy picked it right up and I installed with no problems, I've sicne upgraded to Dapper without issue.  I've had to do some configuring here and there but I'm by no means an expert.  If anyoen has any questions please feel free to ask and I'll see if I can help.

---

### Post by ubuntu_demon on 2006-07-09
Here's a hardware compatibility website for Linux. It's not Ubuntu specific.

I found it on the digg :
[http://digg.com/linux_unix/Linux_Hardware_Compatibility_Database_Launches](http://digg.com/linux_unix/Linux_Hardware_Compatibility_Database_Launches)

Here's the website :
[http://www.phoronix.com/lch/](http://www.phoronix.com/lch/)

---

### Post by hellmet on 2006-07-09
Cool Thread!!

Here is my Config..nothing out of the ordinary!!

Intel 915GAV Mobo
2.8GHZ
Some ABC-XYZ mouse(U won't know the company)
Samsung KBD
Seagate 80GB HDD

NO Vid cards
512MB ram

D-Link Via Rhine 520TX NIC

Philips 17" Monitor.

and well no dual boot!!

---

### Post by IoCaster on 2006-07-13
MSI K8N Neo4 Platinum
AMD 64 X2 4400+
Sapphire GeForce 7800GTX
Dell 2405FPW
Audigy 2 Platinum
HP-dvd640 DL DVD/RW
Generic DVD-ROM Drive
PATA 120GB HDD
PATA 160GB HDD
SATA 250GB HDD
Linksys WRT54G router as 10/100 switch
Chilibox CB160W - NAS/Server/Router/Wireless
HP Photosmart 3310 AIO Printer w/wireless 

Dual booting WinXP Pro + Ubuntu

All of the above working just fine with Ubuntu 6.06 - XGL+Compiz.
It took a bit of configuring, but nothing too difficult.

---

### Post by Pretzal on 2006-07-14
Gday,

I have an Acer Aspire 1200x Laptop installed with Dapper Drake 6.06 and had no trouble at all installing my D-LINK DWL-G630. Dapper Drake was installed with the card present in the PCMCIA slot and the only changes I made to get it working were to change from DHCP to static IP and enter my ISPs DNS server numbers and hey presto it works. The chipset is atheros and the hardware version is D. Hope this helps...

---

### Post by gratefultux on 2006-07-14
Well, nothing special in my computer :( 
600Mhz Pentium III
PCI GeForce4 MX440
Creative Sound Blaster 16 PCI (worked no problem in Breezy, took a while to configure in Dapper)
Texas Instruments PCI Cardbus Controller (PCI -> PCMCIA)
Enterasys RoamAbout 802.11 DS
Seagate 20GB Harddrive
Western Digital 80GB Harddrive
Sony 16x DVD drive

---

### Post by pepolez on 2006-07-15
**nibbler (Ubuntu Dapper 2.6.15-26-k7 - Full graphical install):**
Description:
AMD Semperson 2400+ CPU (1664MHz)
MSI KM4AM-L motherboard
nVidia GeForce 6600GT graphics card (using non-free xorg modules)
VIA VT6102 (Rhine 2) onboard ethernet
Realtek 8139 PCI ethernet card
Western Digital 80gb IDE HDD (WD800JB-00FMA0)
FUJITSU 40gb laptop HDD connected via Myson Century 'Fast 3.5" external storage' USB interface
TDE systems 21 in 1 card reader
LG HL-DT-ST DVDRAM GSA-4163B dvd burner
LG HL-DT-ST DVD-ROM GDR-8161B dvd reader
Phison Electornics Corp. 256MB USB flash drive
Cypress Semiconductor Corp USB 2.0 'TetraHub' (CY7C65640) (external powered USB hub)
Genesys Logic Inc. USB 2.0 hub [ednet] (internal powered USB hub)
Wacom Graphire 2 USB tablet (movement is relative (like a mouse) rather then absolute (like a tablet))
VIA 8237 AC97 onboard sound
Maxtor 104 key US keyboard (PS/2)
A4tech 'big thumb' scrollwheel optical mouse (PS/2)
eRacer programmable robot (detected correctly, but no programs to use with it)

**testbox (Ubuntu Breezy 2.6.12-10-386 - Non-graphical server install):**
description:
Intel P2 200MHz CPU
Trident Microsystems TGUI 9440 PCI video card
Realtek 8029 PCI ethernet card
Unknown HDD - 20gb (suspected wd or seagate?)

perhaps not the best systems in the world, but they do their jobs :)

---

### Post by Helix. on 2006-07-15
Compaq Presario 2200
40gb HD (regular...not SATA or etc)


Touchpad-Works (out of the box)
LAN-Works (out of the box)
Wireless Mouse- Works (out of the box)
4-Port USB Hub-Works (out of the box)
Volume buttons on side of laptop-Works (out of the box)
External Floppy Drive-Works (out of the box)
CDRW/DVD Combo dirve- Works (out of the box)
Compatibility with FTP-Works perfectly(out of the box), in fact, IE didnt even allow me to type a password in!
Broadcom Wireless card-Works

As you see...most of my stuff worked out of the box, besides my wireless card (had to configure) and my all-in-one, which has not worked for dapper and hoary.

---

### Post by Dinerty on 2006-07-18
Dell Laptop Inspiron 9300

Inspiron 9300 Pentium M Processor 760 (2.0 GHz, 2 MB L2 cache, 533 MHz FSB)
i9X00 17.0" WUXGA(1920 x 1200) LCD Gloss17" UltraSharp Wide Screen WUXGA (1920 x 1200) Display with 
TrueLife
1GB, DDR2, 533MHZ [2X512MB DIMMS]
80GB 7200rpm ATA/100 HDD80GB (7,200rpm) IDE Hard Drive
8XDVD+/-RWDriveFixed Internal 8X DVD+/-RW Drive NEC 6600
256MB NVIDIA GeForce 6800 Go graphics card, PCI-Express x16256MB NVIDIA GeForce 6800 Go graphics
Internal V.92 Modem Adapter UK
Intel Pro/Wireless 2200 802.11b/g

Had to install drivers for my graphics card from here: [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by fatsheep on 2006-07-19
AMD 64 3000+ Venice
1 GB Patriot Memory
XFX Nvidia 6600 GT
DFI Infinity Motherboard (onboard sound)
NEC DVD-RW
Realtek NIC

No hardware problems so far, didn't even need to install any sound drivers either. :mrgreen:

---

### Post by paulmilliken on 2006-07-19
Epson Stylus C45 works perfectly under Dapper.  Go to System, administration, printing and add printer.  Ubuntu autodetects the make and model of the printer without a problem.

---

### Post by hotani on 2006-07-25
**Motherboard**:Gigabyte GA-M55plus-S3G Socket AM2 NVIDIA GeForce 6100 ATX AMD Motherboard
**CPU**: AMD 3800+ X2 socket AM2
**RAM**: 2GB Corsair RAM
**HD**: 2x250GB Samsung SATA (RAID-1)
**GPU**: eVGA 256-P2-N553-AX Geforce 7600GT 256MB GDDR3 PCI Express x16 Video Card

It all worked out of the box(es). Even have sound from the MB.

Oh, that MB says it supports all kinds of RAID configurations but that is only if you are running windows. Once I figured out Ubuntu wasn't going to see the RAID set up with the MB, I re-did it with linux using the alternate install disk. 

I also set up a PATA LVM array with a 300GB and 120GB for movies and TV shows.

---

### Post by reacocard on 2006-07-27
HP dv4000 Laptop

1.7 ghz Pentium M
1 GB RAM
CD-RW/DVD-ROM
Intel i915 integrated graphics
Intel 2200 b/g wi-fi

Everything worked out of the box. Even the included remote for controling video/audio playback worked, albeit not with all media players (totem, rhythmbox and exaile are the ones I know work. gxine and xine do not). 

Logitech mx310 USB mouse

Side buttons don't work by default. a quick edit to its section of my xorg.conf fixed that. here's what it looks like now:

```
Section "InputDevice"
	Identifier	"Logitech USB Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option          "Buttons"               "7"
	Option          "ButtonMapping"         "1 2 3 6 7"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection
```

---

### Post by e_james on 2006-07-27
Shuttle XPC ST20G5
Motherboard - FT20
Processor - Athlon 64 3200
Ram - 2 x 512MB
on-board - video (ATI Radeon Xpress 200), audio, Broadcom Gigabit ethernet, USB 2, 1394

Currently installed
250GB Samsung IDE HDD (partitioned for multi-boot Windows / Linux, currently only using ubuntu 6.06-386)
Multi-format DVD+-R/RW, DVD-RAM
3.5in. floppy drive

1 x PCI slot used by Hauppauge TV card (Win TV FM PCI)
1 x PCI Express slot free

This is still a work in progress but so far, at about the 4th attempt, ubuntu 6.06 (386) is now installed. I needed to use boot options "noapic nolapic acpi=off". I also updated the bios to the latest available with no noticeable advantage. 

N.B. PS/2 keyboard and mouse recommended for install purposes. A USB mouse can cause boot failures and the USB keyboard only works correctly if starting from complete power off.

After successful boot up and login, I experimented a little and then, when I tried to make system changes, my password was rejected. At this time I can no longer login and I can't boot up in recovery mode. I will post a question in one of the help forums and edit this post if I have useful info to add.

---

### Post by Enverex on 2006-07-27
Asus A8N-E
AMD Athlon64 X2 3800+ (Toledo)
LITE-ON DVDRW SHM-165P6S
nVidia GeForce 7800GT
Sound Blaster Audigy (the original)
Microsoft Intellimouse Optical (1.0a)
HP LaserJet 4100
Maxtor 160GB SATA hard drive
Hitachi 250GB SATA hard drive
RealTek 8139 Network card
OmniVision OV511 WebCam
Saitek X52 Flight Control System (but only as a basic joystick and the screen + extra features don't work).

---

### Post by jakonj on 2006-07-31
AMD Athlon XP 2200+ (tb B)
Asus a7v8x-x
3x256Mb Kinston
Abit Siluro GeForce 4 Ti 4200 (64mb)
40Gb maxtor Diamond max 8
LG DVD-ROM GDR8163b
Sony CD-RW CRX230ED
Sound blaster Live! 24 bit
Rockwell HCF 56k with Riptide sound chip
HP LaserJet 6L
Logitech Quick cam express
Samsung SyncMaster 151b

everything worked out of the box except:

Geforce 4 Ti ( problem and solution: [http://www.ubuntuforums.org/showthread.php?goto=newpost&t=225840](http://www.ubuntuforums.org/showthread.php?goto=newpost&t=225840) )

An my monitor is supporting 60Hz, 70, 72 and 75 hz for refreshing the screen but ubuntu is dettecting only 75!

also i need to download driver for my modem from linuxant ;)

---

### Post by BobSongs on 2006-08-01
**Brother MFC 210C Multi Function Center**. Drivers are available. Tutorial available in this forum.

**Canon PowerShot A540 (AiAF)**. Worked the moment it was connected. However the AVI files appear to have distortion in the audio. When the same files were transferred to my Windows XP partition the sound was fine.

---

### Post by inkapyrite on 2006-08-02
ubuntu version: dapper 6.06 Ubuntu 64bit
motherboard: Asus a8n32sli deluxe
cpu: AMD Athlon 3500+
gpu: Pixelview nvidia 7900GTX
monitor: Viewsonic 20" VX2025wm LCD

ubuntu recognised all the onboard peripherals like audio, the gigabit lan on the motherboard. nvidia drivers worked fine too. But the monitor needed minor tweaking in xorg.conf, due to different refresh rates. see 

 [http://www.ubuntuforums.org/showthread.php?t=221313&page=2](http://www.ubuntuforums.org/showthread.php?t=221313&page=2)

for my post about it.

---

### Post by lasal on 2006-08-14
Ubuntu 2.6.15-26-K7

Abit KV7 KT400
AthlonXP 1700 @1.6
1024MB RAM
GeforceFX 5200
Zygas Wireless(b)(ZD1201)
Winfast TV Card 
Chaintech Envy24 (HT-S)
WD 80GB ATA100
Maxtor 40GB ATA133
LiteOn DVD-RW+-
Canon i350 (works w/Turboprint drivers)
XG Flat 17" CRT

No Problems, will be upgrading in a few months and I'll repost.

---

### Post by heffo_j on 2006-08-19
My Laptop is an Aopen 1547. 

Comments:
[LIST]
[*]Most things worked with Dapper, including the Anteros D-Link DWL G650 card. I can't understand how to get WPA/WEP working so I'm waiting for a later release to present a user friendly set up (the ethernet connection works well).
[/LIST]
[LIST]
[*]The internal modem should work (it used to under other distros).
[/LIST]
[LIST]
[*]Sound is good.
[/LIST]
[LIST]
[*]Mouse USB Labtec Optical Mouse is good.
[/LIST]
[LIST]
[*]The touch pad works.
[/LIST]
[LIST]Fan works well.
[/LIST]
[LIST]
[*]Battery "low power" is detected. Also screen dims when on batteries.
[/LIST]
[LIST]
[*]Lid closure shuts down the screen and logs out the user; a password is required to get back in. I'm not sure this is full hiberation or not.
[/LIST]

The following don't work:

[LIST]
[*]The Ird doen't work nor the SDA card reader.
[/LIST]
[LIST]
[*]My Pocket PC to connect/synchroise with Dapper (or Breezy or any of the distros that I know of) despite there being a Palm Pilot program.
[/LIST]
[LIST]
[*]The latest 3D graphics don't work yet either. I'm not clever enough to get it going.
[/LIST]
Otherwise all else seems to be okay. (Just wish I knew how to program so I could contribute).

Regards
John

---

### Post by mojoman on 2006-08-22
I run a Toshiba Satellite 1800-504 with the following:

CPU:	  Intel Celeron 1000
RAM:	  PC100 SDRAM, 256 MG
VGA:	  Trident Cyber ALADDiN-T (Cyber Blade XP) (Uses 16 MB of the 256)
Chipset:  ALI M1644T/M1535 (ALADDiN -T)
HDD_Int:  Ali M1535 14 GB
Sound:	  ALI M1535 (AK4543)

Everything works out of the box except the videocard. No matter how I try, I can't get the damn thing to work. :mad: I runs ok for normal usage but playing DVD or watching DivX/Xvid is impossible.

Also, DVD and USB works nice but I haven't tried the IrDa, floppy and TV-OUT (what would I watch? I can't get the damn video to work! :mad: )

Also, I use a CNet wireless PC-card which also works out of the box.

Apart from the video, I'm really satisfied and overall I'm impressed with the hardware support :D 

/Mojoman

---

### Post by beameup on 2006-08-24
See my Sig.

I used the LIVECD installer for Dapper and it didn't pick up my nvidia card. Not a big deal for me, just went to synaptic and installed the drivers.
I had used the Install CD for Breezy when I first started with Ubuntu and it loaded the nvidia drivers.

I have one of those 7 bay card readers on here and Dapper sees them OK

When I recently added a 160GB slave drive, I had to manually config it.

I have 2 more machines with dapper loaded on them. An Acer Travelmate TM4502 and a Wintergreen 1 GHZ Celeron. I'l add specs when I'm home.

---

### Post by jubilee33 on 2006-08-30
I strugged for a long time in Mandriva 2006 to get my wireless card to work but failed miserably but in Ubuntu every piece of the hardware just worked out of the box.  No tweaking at all.  I have a Dell Inspiron 600m.  

The DVD playback and USB...everything is great.  I am trying to get another laptop to work.  If I succeed, I will post that one's specs too.  Thanks for all the great tips on this forum.

---

### Post by chipace on 2006-09-02
My setup:
ASUS M2NPV-VM (nvidia 6150+430)
Athlon X2 3800 (AM2) (overclock to 2.1GHz)
Kingston valueram ddr2 667 512MBx2(KVR667D2N5K2/1G)
Maxtor PATA 250GB
NEC DVD Burner (ND-2510A)
USB keyboard and mouse
Dell 2001FP LCD monitor (dvi)

Results:
(1) Needed to use an external ethernet card to download the updates needed to get rid of it.
(2) All drivers working (have not checked firewire)
(3) Cool-n-quiet works flawlessly
(4) XGL is slow
(5) Suspend and hibernate non-functional (I believe the suspend problem is the nforce ide kernel bug... and the patch won't make it into the kernel tree for a while).
(6) Used xbindkeys to map keyboard volume control for ALSA
(7) I was only able to get GoogleEarth to run properly with XGL and Compiz.

Opinion:
Ubuntu runs like a champ... boots quick, good HD and network performance. The AMD64 kernel and binaries are fast! DVD playback and media decoding is excellent. I really would like to get suspend2ram working and easier control for enabling hardware OpenGL for GoogleEarth.

---

### Post by Shortgeek on 2006-09-03
D-Link G520 Works great out of the box.

---

### Post by hoosemon61 on 2006-09-04
post moved to correct thread

---

### Post by Belyel on 2006-09-05
Acer Travelmate 8200 working devices:
[LIST]
[*]Core Duo T2500
[*]15.4" widescreen 1650x1080 display
[*]120GB SATA hdd
[*]2GB ram
[*]ATI x1600 mobility w/256 + 256 shared video
[*]5 in 1 memory card reader
[*]DVD +/-R +/-RW CD R/RW combo drive
[*]802.11a/b/g WLAN (Intel® PRO/Wireless 3945ABG)
[*]gigabit LAN
[*]Bluetooth® 2.0 + EDR (enhanced data rate) wireless PAN 
[/LIST]

Untested devices:
[LIST]
[*]Dual-monitor/S-video out
[*]V.92 modem
[*]IEEE 1394 (firewire)
[*]IR
[*]PCMCIA
[*]ExpressPC/34 cards
[/LIST]

Working peripherals:
[LIST]
[*] Motorola PEBL (using moto4lin)
[*] Creative ZEN Micro (using gnomad2)
[*] Olympus P500 natively supported as a drive
[*] Maxtor 300GB external hdd
[*] All the USB pen-drives I have
[/LIST]

Only one thing remains unworking that I have tested and tried to get working: the built-in webcam.  I have it on good authority that the webcam will be supported in the future using v4l2 and the spca5xx successor.

---

### Post by davidebee on 2006-09-10
Laptop : Samsung X15 AZERTY keyboard:
Dapper Drake : 

Very happy with results, don't need modem, have no memory stick and no firewire device (Ricoh Co)
David E Bee

---

### Post by JAwuku on 2006-09-12
Netgear FA120 USB2.0 Ethernet Adapter works without problems on installation, but does not work with the Ubuntu live cd.

---

### Post by Bartender on 2006-09-15
Olympus SP500-UZ

The Olympus was recognized by Dapper just fine.  I used the same procedure as Olympus described for Windows - Camera off, with the dial on top clicked to the "Output" setting, plug in the USB cable, turn the Olympus on.  The screen on back lights up, make sure the "PC" setting on the menu is highlited, and click "OK" on the back of camera.  Camera came up on the Desktop as "USB device" something or other.  Images were easy to download.  I don't remember the details but it was simple.

---

### Post by ShamusPatt on 2006-09-16
I have Dapper Drake running on my laptop:

Compaq Presario 9120CA
AMD Athlon XP-M 18.GHz
40G Fujitsu drive
D-Link DWL-G630 wireless PCMCIA (Atheros chip)

I'm dual-booting with Windows XP Home. GPart wouldn't resize it at first. I had to use ntfsfix to get the original partitioning "corrected" by Windows XP first, even though I had just freshly restored the system from the rescue CDs. It seems the rescue CDs leave the hard drive in a workable but invalid state. 

The second issue I ran into was memory. The laptop was bought with 256M, which is minimum for Ubuntu. However, 64M was going to video RAM as it's shared so effectively it had only 192M. I was able to reduce that to 8M in the BIOS leaving 248M but it was still painfully slow. Throwing another 512M stick in made things much better.

After that, the install went off without a hitch.

---

### Post by maduranga on 2006-09-20
Nvidia Gforce FX 5200
Philips 107S5
WIDCOM Bluetooth - need configuration with gnome-bluetooth and bluez-utils
Aopen DVD-RW

---

### Post by Echo35 on 2006-09-20
Intel Core 2 Duo 2.4 GHZ Processor
GSkill 2 GB RAM
nVidia 7950 GTX2
Western Digital Caviar 250 GB SATA Hard Drive
Lite On SATA DVD-ROM
ECS nVidia Motherboard (Unsure of the model at the moment)
Linksys WMP54G Wireless Card
Sound Blaster Audigy Sound Card
 
It's a custom built rig, so there's a bunch of other random things in it, but it all works very well with Ubuntu. Oh, and my 19" Panasonic Widescreen LCD monitor works well also. As do the Creative inspire 7900 speakers.

---

### Post by Johan! on 2006-09-20
Server:
Asus TUA 266 Motherboard
Celeron 1 GHz (Coppermine)
Geforce 4 MX440 (AGP)
Realtek RTL8139 Network Card

Booting GRUB takes 2 minutes, after that everything works fast.



Main PC:
Asus A8N-E
AMD A64 3500+
nVidia 6600GT (PCIe)
Sound Blaster Audigy
Promise Ultra100 TX2

Scanner: Canon LiDE60
Printer: Canon Pixma iP4000

Everything works fine

Laptop:
Acer Aspire 5024 WLMi

X works, after tweaking xorg.conf
Card reader doesn't work
Wireless: Too difficult to configure. (I read somewhere that it works)

---

### Post by ShadowRage on 2006-09-21
Ubuntu Dapper: 64 bit

-ASRock 939Dual-SATA2, 512 mb Single Channel RAM, 939 AMD64 K8 3200+ @ 2 ghz with Cool 'n' Quiet technology.
-Cpu throttling works fine.
-Sensors are installed, though I know all are not working, I hear there are bugs with this.
-SATA: Works.
-SATA 2: (Jmicron ASIC) Works with newest Dapper kernels, the default kernel (as in, the one that's installed without updates on a fresh install) wont support it.

-Western Digital 80GB SATA HDD (3.0 gbp/s): Works fine, as it should.

-Onboard Realtek sound (Intel ICH actually): works, needs some work when it comes to software mixing, had to do some searching on getting a .asoundrc that mostly works. real surround sound is possible, but dont plan on doing any sound mixing in surround mode, it's buggy, also, you need to hack up the intel ICH definition files to get proper surround, and it isnt perfect. (for ICH5) (maybe this can be researched for the next release..?)

-Nvidia Geforce MX 4000 - Works fine with free driver and with the nvidia driver, having issues with color getting messed up with Xvideo when totem plays certain files. or whenever I run totem.

Hauppauge Wintv pvr 150: Doesn't work with the stock system. I had to compile my own modules for this to work, and get the latest CVS for XawTV (which I have a repository for, at least for 64 bit users) so I can watch TV with it, vlc works, but with vlc, it's more or less hackery. Still cant find a decent v4l2 radio tuner. Might also look into the latest zapping releases as future ref for the ubuntu devs.
Onboard networking using a Realtek PHY: works great.
DVD drive: works great
CDRW: has worked fine, is starting to have problems, not linux related though, it's just ancient. got it in '01 and it's done its fair share of burning.

Genius Wizardpen Tablet: Made a package for it in my repository, needed to do some modifications and hackery to get it to work as a package. (for the X driver anyway) I havent experienced any other issues with it in dapper.
STV680 based webcamera: colors are messed up, have to unclick the color correction fix in Camorama. Minor problem, just sucks in other apps that use the camera that dont offer a "fix" but I think this is a problem with the stv680 driver or an issue with the camera I have.


Kodak EasyShare CD33: Works great, no problems.

Microtek 815C monitor: Only issues are the the monitor itself, such as trying to adjust the screen frantically when it turns on, or switches modes. Otherwise, it displays fine, cant complain, got it for free :)

that about covers it.

As a side note, I wish I had waited and gotten the successor of the mobo I have, which is basically the same, but with some little fixes, such as hotswapping.

---

### Post by SticknClutch on 2006-09-21
Ubuntu Dapper 64bit

Asus M2NSLI - Deluxe
3Ware 9590SE PCI-E Raid Controller
Nvidia Geforce 6800GT
On board everything

Works perfectly. Everything was detected at install.

Raid performance is a bit low. Probably haven't tweaked it right yet.

---

### Post by armware on 2006-09-21
running dapper on an HP Pavilion dv8230us. 
the install was a bit bumpy at first. i had to install ubuntu 5.10, then dist-upgrade to dapper. i'm pretty sure it was the sata drives messing with it.

the list:
intel core duo 1.67ghz-ish
worked, worked better after manual install of 686-SMP kernel

1gb ram
ummm, yeah. that worked just fine

dvdrw
cd's and dvd's burn fine

2x80gb sata hd
sata screwed with 6.06 install disk, 5.10 worked

nvidia gefore go7400, 512mb
worked, used apt-get for binary drivers

intel 3945abg
worked, compiled latest drivers anyways

trackpad/keyboard including media keys
worked. the two 'quickplay' buttons didn't do anything, but the volume up/down/mute buttons work, even the calculator button pulls up the calculator. sweet. this laptop has a big screen, so they put a numeric pad on it. that works too.

screen
installed at the screen's native res (1440x900), works great.

haven't had a usb device plugged into it yet that didn't work (2 mice, digital camera, printer)

the only things not working after install was
  -Digital Media Reader by Texas Instruments. not a biggy, but it would be nice to use.
  -3D Video support, but that's a given. one command got the nVidia drivers going for me
  -dual monitor support, though i haven't messed with it too much

---

### Post by rengolin on 2006-09-21
MSI P4N EX SLI NVidia chipset
Pentium D 805 Dual-Core
Corsair memory
Leadtek NVidia PX6600 PCI-E 128
Netgear WG311v3 54mbps 802.11g Wireless PCI (using ndiswrapper)
SATA Seagate Barracuda 7200 80G

Apart from the wireless that I had to use ndisw (anyway, quite simple) the rest was completelly painless, plug & play.

---

### Post by vinodmenon on 2006-09-23
How did you dual boot your system? My details for my laptop are below.

I have a Dell Inspiron 510m laptop and would like to install the latest "Dapper Drake" version of Linux along with my windows running together. My current specs for the laptop are as follows:

Features/Specs: Pentium M 1.6GHz; 512MB RAM; 15in screen; 64MB shared Intel Extreme Graphics 2; 60GB hard drive; DVD-RW/CD-RW

Is there any way anyone could assist me with the installation procedures for having a dual-boot system on this laptop? Any guides or website? I believe that i have to recreate the partitions in order to have the dual-boot work properly. Currently my laptop has been reset to factory conditions ie like brand new when i got it delivered with Windows OS etc. I have just installed Partition Magic after ghosting the hard disk.

Hoping to resolve this matter asap.
-- 
Regards,
Vinod Menon

---

### Post by Vorticon on 2006-09-28
CPU : AMD Athlon XP 3500+ 64 Bits
MOBO: Asus a8n sli deluxe (With Realtek AC97' sound on it)
GFX : Asus EN7600GT PCI-e
RAM : Very old and unknown infeneon RAM (i should upgrade), 1028 MB
HD1 : Maxtor 75250R0 250 GB
HD2 : Maxtor 6Y120P0 120 GB
CDRW: Artec WRR-52Z
DVD : LG DVD-ROM DRD-8160B

And uhm, yeah that was about it. Just a logitec keyboard and a standard dell usb optical mouse.

Installing went perfect. I had to find out the partition thingies though being a complete linux n00b :cool:
I must say I really like ubuntu :)

---

### Post by trburkholder on 2006-10-01
ASUS A8V E SE Socket 939 Motherboard
AMD Athlon64 3200+ 
on board Marvell 88E8053 Gigabit Ethernet (Rev 19)
on board VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
1 GB RAM

Leadtek PX6600GT TDH Geforce 6600GT 128MB

Kubuntu 6.06.1 386 alternate, 6.06.1 amd64 alternate crashed during install.

Kubuntu 6.06 386 desktop DVD installed, audio, video, network all function but really unstable.

Tried upgrading the kernel from 2.6.15-23-386 to 2.6.15-27-386 and installing nvidia-glx 1.0.8762+2.6.15.11-5 binary driver, but that made things worse.  I went back to the nv driver and the 2.6.15-23-386 kernel.

Two fixes have stabilized the system to usable form.  

[LIST=1]
[*]edited /boot/grub/menu.lst lines to pass noapic and nolapic to kernel.

[INDENT]defoptions=quiet nosplash noapic nolapic
[/INDENT]

[*]commented out (#) lines in /etc/X11/xorg.conf that have to do with tablet PC devices as below:
[INDENT]
#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

and in the ServerLayout Section

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
#       InputDevice     "stylus" "SendCoreEvents"
#       InputDevice     "cursor" "SendCoreEvents"
#       InputDevice     "eraser" "SendCoreEvents"
EndSection
[/INDENT] 
[/LIST]

I would like to try the binary driver again, but it's not crucial.

---

### Post by brephophagist on 2006-10-06
Areca ARC-1160 16-port SATA RAID6 card.  Works like a dream, multiple volumes setup in the bios show up as multiple SCSI disks.  If this one works, most of the PCI-X / PCIe cards should as well, though I have yet to try an ARC-1260.  more soon.

---

### Post by DarkN00b on 2006-10-06
HP Pavilion ze2000 Everything worked "out of the box" except the Intel 82852/855GME video chipset and my Zyxel B-220 usb wireless adapter.  Tweaking fixed that however.

---

### Post by motstudios on 2006-10-08
my rig:
Xubuntu Dapper
430MHz AMD K6-2
390MB RAM
20GB IDE Hard Drive
Belkin Wireless G PCI card based on atheros chipset
USB 2.0 4-port PCI Card
Nvidia PCI Graphics card
Lexmark z25 Printer ([http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-Z25](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-Z25))

Also want to note that a Digital camera I have works as a mass storage device on ubuntu but needs drivers on windows despite the fact that the company says the camera doesn't need drivers (score one for linux)

---

### Post by nothingxs on 2006-10-09
Ubuntu Dapper (6.06 LTS, x86)

Running perfectly on an IBM Thinkpad A21m Model 2628. Installed straight out of the box with only minor problems: the DVD-ROM drive had some problems reading a CD-R (I'm new to Linux, so god forbid I know how to fix them myself -- for now) when mounting, I'm not sure if this is exclusive to just the CD-R I tried to read at the time. Also needed some tweaking for ALSA to not flip out over my sound card on some applications (MIDI sequencer not starting properly it seems). This may have just been an oversight on my part.

> - Intel Pentium III 800MHz (w/SpeedStep)
- 256MB RAM (2x 128mb DIMMs)
- 14.1" TFT LCD, 1024x768 Native Resolution
- 10/100 Ethernet
- 56k Modem
- Integrated Floppy Drive
- 2x PCMCIA Slots
- Serial, Parallel, PS/2, and VGA-Out Ports
- 1x USB (apparently 2.0!)
- Audio In-Out
- Li-Ion Battery

Using a 100GB (!) Toshiba hard drive from a laptop that died. Will do sudo lshw sometime tomorrow for information on the thing itself. Also, installing a PCMCIA Netgear WG511 802.11g wireless card, and will report on that to. Post will be edited to reflect that. :-k 

Will also edit to expand upon it when it's been upgraded to 512MB RAM (the maximum for this kind of computer).

---

### Post by xyz on 2006-10-09
Toshiba Satellite A40 PSA40E-0DEWN-S4 Works fine (XP Home-Dapper); I had to change my 2-year old HD to an 80G; I have yet to test/connect wireless; Samsung Aluminum USB 2.0/IEEE 1394 80G-external HD

---

### Post by DOD1951 on 2006-10-09
AMD ATHLON XP 2100+ via mainboard
There has been nothing in the way of hardware that I have thrown at Ubuntu Dapper 6.06 that has not worked. USB Thumb Drives, Digital Camera Cards, Ipod. The only thing that it has a problem with is me :)

---

### Post by catanzag on 2006-10-09
I've a Toshiba Satellite 2410-303 with dual boot WindowsXp SP2 + Ubuntu 6.06 Dapper which works almost really, really good; only a few tweaks needed
[LIST]nvidia-glx works only with 686 kernel, 386 kernel hang and I needed nvidia-glx-legacy; xorg.conf configurated according with latest nvidia dapper [guide]("https://help.ubuntu.com/community/Latest_Nvidia_Dapper") (thanks tseliot!!) for fixing the black line on the border
[/LIST]
[LIST]sudo +s /usr/bin/cpufreq-governor to enable cpufreq-applet scaling
[/LIST]
[LIST]slmodem compiled from source
[/LIST]
[LIST]xsane works at first time, but I had to download the firmware for the scanner
[/LIST]

also working
Firewire LG DVD+RW
Firewire Maxtor 160GB HD (with lot of partitions...)
Epson Photo Scanner 1670


btw, I added to kernel args *vga=792* in /boot/grub/menu.lst for 1024x768 resolution on boot

---

### Post by Fitzcarraldo on 2006-10-10
Gateway Solo 9300 notebook PC
288 Mb RAM
Belkin Cardbus Ethernet card
USB wheeled mouse (originally from an Acer Ferrari 3000 notebook PC)
ubuntu 6.06 LTS Dapper Drake


Everything works and ubuntu flies. Connected to a home network and Internet via RJ-45 socket on an ADSL router. Prints to remote printer connected to a networked tower PC running Windows XP Home. Also has access to a shared folder on the Windows PC to copy files to and from the PCs (or open them in the shared folder on the Windows XP PC).

I dowloaded all the video and audio codecs using Automatix, and can thus play MP3, WMA and WMV too. Video and audio on YouTube are slightly out of synch but otherwise OK. The volume control up/down push-buttons don't work, but I can use the ubuntu volume slider control instead.

---

### Post by landotter on 2006-10-11
Dell Latitude CPX j 750

Everything works  perfectly from a straight install.  Dapper with 256mb runs very smoothly. Suspend  and Hibernate  are flawless. Battery indicator is accurate. Perfect lappie for Ubuntu. Got  mine for $200 with a wifi card. :D

---

### Post by Unterseeboot_234 on 2006-10-11
Motherboard:A7V133
Vendor: ASUSTeK Computer INC.
Cpu: AMD Athlon(TM) XP 1500+
Display: 300/305 PCI/AGP VGA Display Adapter
Vendor: Silicon Integrated Systems 

================
 No install problems, ubuntu 6.06. Teenie sound on SoundBlaster Live! audio card, but it works. Have not tweeked that card except for pkg install of GNOME ALSA Mixer which gave a marginal improvement on the volume and added one SoundBlaster option button.

Cheap video card. Cost me $25, yet has outlived the $200 cards that fried easily and I threw away. Linux tells me I have 1024x768. Cannot adjust any other resolution. Haven't tweeked. Looks good. Hurts the eyes after a while. The desktop monitor displaying Linux is comparable to 800x600 from the WIN partition. That is, the WIN OS seems to give me a larger desktop.

But, I hardly fire up WIN any more. I'm thinking of an upgrade to 64-bit AMD machine with a PCIe video card ... running ubuntu. Can't find exactly that computer in this hardware list. I will post if I do upgrade.

---

### Post by big z on 2006-10-12
mobo: aopen ax34
Cpu: p3 733
Ram:256 
video card: nvidia quadro4 nvs 220 agp
hard drives: 1 20gb and one 80 gb one
every thing work  but for some resone my video card is agp 2x not 4x like its should be

---

### Post by gvgerman on 2006-10-12
Dell Latitude D600
Logitech V200 USB Wireless Mouse
LaCie 80G USB drive
Broadcom BCM4306 internal wireless network interface
Broadcom wired network interface

1. Had wireless network issues after install.  To get the wireless network interface to operate, used the steps contained in this forum note [How to: Broadcom Wireless Cards]("http://www.ubuntuforums.org/showpost.php?p=1071920&postcount=1")
2. Have not tried to get 7-button USB wireless mouse to work with all button features; left button, right button, & scroll work with no tweaks.  Mouse also can be hot installed w/o problems.
3. Dapper Drake is installed on the USB drive and PC boots from the USB drive after bios settings change: CD drive #1, USB #2, internal hard-drive #3.
4. Had to reformat USB drive from 80G Fat32 to 30G Fat32 to leave approx. 50G "empty" for Dapper Drake to install.  Dapper Drake Live CD would not resize the Fat32 partition and would not install on the USB drive w/o the empty space.
5. Had to install codecs for mp3's to play in Rythmbox. Used Easy Ubuntu. No problems.
6. Have not ripped w/ Sound Juicer yet, but did need to establish Lame -alt preset configuration manually to allow for mp3 conversion.
7. Was able to import Windows Thunderbird email and Windows Sunbird calendars using Evolution and its' Help Guide.

---

### Post by Thingymebob on 2006-10-13
Acer Aspire 1350 - Model No ZP1 - (Edgy Eft 6.10)
Athlon(M) XP2600+

Internal Modem not tested
ethernet working
usb working
pcmcia working

Everything else Appears to work fine from a clean install. Unplug everything before installing and Ubuntu Correctly Detects everything.

Left a USB mouse plugged in and couldn't get touchpad to work, installed without mouse and touchpad works fine. Then plugged in mouse.

Add the following to /etc/X11/xorg.conf to get user switching to work:

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"via"
	BusID		"PCI:1:0:0"
	VideoRam	64000
	Option		"UseFBDev"		"true"
	**[COLOR="Red"]Option		"VBEModes"		"true"[/COLOR]**
EndSection
```
Hot Keys:

fn+F1       (Help)                   Working
fn+F2       (Setup)                  Not Working
fn+F3       (Power Management Mode)  Not Working
fn+F4       (Sleep)                  Not Working
fn+F5       (Display Toggle)         Not Tested
fn+F6       (Screen Blank)           Working
fn+F7       (Touchpad Toggle)        Not Tested
fn+F8       (Mute)                   Working
fn+CurUp/Dn (Vol +/-)                Working
fn+CurL/R   (Bright +/-)             Not Working

Launch Keys
Web Working
Email Working
Bluetooth N/A
802.11 N/A
P1/P2 Not Tested

Lower status lights not working

---

### Post by willca on 2006-10-13
HP Pavilion dv5224nr

AMD Turion 64 ML-37

ATI Radeon Xpress 200M

Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Realtek RTL-8139/8139C/8139C+ (rev 10)

ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)


Running Dapper 6.06 with everything mostly running out of the box except for the wireless nic which I had to use ndiswrapper for this.

---

### Post by UCeivissenc on 2006-10-15
Hi

I've got a Hp dv5000 core duo, where don't work

I- a 82801G (ICH7) high definition audio sound card, (everything works ok except capture function) it didn't work with dapper.

II- and  TDT Freecom DVB-T USB Stick, USB 2.0, it worked with dapper according to [http://tabernadelcalvo.blogspot.com/2006/09/ubuntu-y-tdt.html](http://tabernadelcalvo.blogspot.com/2006/09/ubuntu-y-tdt.html)

---

### Post by dandaman32 on 2006-10-16
Everything except the modem works on my laptop, an **Acer TravelMate 230**. I posted a guide on how to get suspending to work at [this blog entry](http://blogs.fuhrykitchentable.no-ip.org/danfuhry/2006/10/15/linux-on-the-laptop-finally/).

(edit) The modem is an Agere Systems AC'97, one of the most notorious WinModems, so it's unlikely that I will ever get it working. It's not a problem for me because I have DSL, but if you have dial-up and a TM230 then avoid Linux or get a LAN and set up another box that can do Internet Connection Sharing.

-dandaman32

---

### Post by gn2 on 2006-10-16
Audiotrak Optoplay USB soundcard works in Ubuntu 6.06 on Dell Optiplex GX110 SFF

---

### Post by wikwam on 2006-10-18
hercules wireless adapter model no.: hwgusb2-54

not working...not detected...what do i do? :(

---

### Post by Jim March on 2006-10-18
Kyocera KR1 external EVDO router.

My "EVDO" PCMCIA modem, Kyocera KPC650 under Verizon wouldn't work under Dapper.  This is a $60/month mostly-unlimited wireless "low grade broadband" (in urban areas anyways) modem based on cellular tech.  If you can get a Verizon cell signal at all, you'll get at least good dialup speeds ("Nationalaccess").

EVDO modems are very weird critters indeed.  They have some characteristics of dial-up modems but "aren't".

There is a lot of info out there on getting these to work in Ubuntu but...it sometimes just doesn't work.

My solution: buy a Kyocera/D-Link "KR1" EVDO router.  This is an external box that has it's own PCMCIA slot for the KPC650 or other PCMCIA EVDO modem, and turns that into straight Ethernet, WiFi or both.  $250  but it's worth it - you can share your connection with multiple PCs/Macs/Linux/etc. boxes without any added drivers other than basic Ethernet/DHCP.

The best source of info on these:

[http://www.evdoforums.com/viewforum.php?f=17](http://www.evdoforums.com/viewforum.php?f=17)

A few people have had problems but...for most (who don't run VPN at least) it's plug'n'play.

[http://booster-antenna.com/index.php?main_page=product_info&cPath=35&products_id=99](http://booster-antenna.com/index.php?main_page=product_info&cPath=35&products_id=99)

The Top Global 6000 is supposedly even better:

[http://booster-antenna.com/index.php?main_page=product_info&cPath=35&products_id=123](http://booster-antenna.com/index.php?main_page=product_info&cPath=35&products_id=123)

...but that Godawful pyramid shape means no shlepping it around in the laptop bag.  Bzzzt.

As a bonus, any of these routers move that very high powered cell signal away from your..."reproductive organs".  With the amount of time I'm online, I could practically feel my nuts mutate.

I have no connection to that company other than being a satisfied customer.  I do recommend them; for one thing, with every KR1 they include a CD they built with three different firmware revisions and instructions on how to upgrade/downgrade and recover from mid-firmware-upload crashes.  That CD worked just fine for me under Dapper and Firefox.

---

### Post by nyinge on 2006-10-19
IBM Thinkpad X30 w/ Linksys WPC54G wifi NIC
-everything working flawlessly w/ ndiswrapper.
--but GUI not so snappy as I was expecting though.

---

### Post by rjz35 on 2006-10-19
Dell D610 latitude done by a linux newbee.

Works most out of the box, except for,

ATI x300 driver, was a mess to setup.
read and write on ntfs drive [dual boot still]
P4-M cpufreqd setup was horrible, i still not got the undervolting working. the frequency thing works
synce with my MDA vario not up completly yet.
screwed up suspend/hibernate big time, don't know where i stand to be honest.
Wireless works,modem dailup works, AT&T that is.
Printing and scanning over ethernet works.
Samba sharing works, all harware buttons work.
Temperature in linux  [cpu = around 41 Degrees Celcius/800mhz and 62 at 1600Mhz] is still too high compared to Winblows [35/50]

Besides al the above, i really like linux thanks to ubuntu and this great forum.

Although i would do when i setup a new system the following.
make a different partition for /home.
choose a faster filesystem: [http://linuxgazette.net/122/piszcz.html](http://linuxgazette.net/122/piszcz.html)

---

### Post by Scheater5 on 2006-10-19
Dell Inspiron 9300.  All the hardware worked out of the box.  Had to get a wrapper for the driver for the built in wireless card.

---

### Post by loboson on 2006-10-19
I installed dapper on my computers today and almost all just works out of the box.

*Computer 1 specs:*
**Model:** Travelmate 3002WTMi
**CPU:** Intel Pentium M740
**Ram:** Kingston 2 x 1 Go DDR2 in dual channel = 2Gb
**Graphic card:** Intel GMA 900
**HDD:** Toshiba - 100Gb

Things that needed / need a 2dn look:
[LIST]
[*]Suspend (just black screen and reboot after wakeup)[EDIT: worked after a reboot :neutral: ]
[*]Wifi w/ Network Manager. Needed some sort of tweakings..
[*]Widescreen (1280x800). Installed '915resolution'
[*]Synaptics touchpad. Doesn't work very good. No scrolling. Detected a 'Generic mouse'
[/LIST]

*Computer 2 specs:*
**Model:** Travelmate 4500 (migrated to Kubuntu, just testing flavors :rolleyes: )
**Ram:** 715 Mb

Things that needed / need a 2dn look:
[LIST]
[*]Wifi w/ Network Manager. Needed some sort of tweakings..
[/LIST]
Things that worked that haven't on the other:
[*]Suspend 
[*]Synaptics touchpad.

I'm still revamping this dual-boot system. Looking forward to update this list. Will be very interesting if I could run XP virtually. That way this would be my main OS.:cool: 

Good job!:KS :KS:KS :KS :KS

---

### Post by no_mayl on 2006-10-20
Compaq Evo N200
P3 700MHz
192MB
wireless: AirLink, 802.11g CardBus PC Card.

xubuntu 6.06
No tweaks, no hacks, easy brainless install.


$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82440MX Host Bridge (rev 01)
0000:00:00.1 Multimedia audio controller: Intel Corporation 82440MX AC'97 Audio Controller
0000:00:02.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M (rev 64)
0000:00:07.0 ISA bridge: Intel Corporation 82440MX ISA Bridge (rev 01)
0000:00:07.1 IDE interface: Intel Corporation 82440MX EIDE Controller
0000:00:07.2 USB Controller: Intel Corporation 82440MX USB Universal Host Controller
0000:00:07.3 Bridge: Intel Corporation 82440MX Power Management Controller
0000:00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
0000:01:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface


After downloading win32codecs and xine-extracodecs, I'm able to watch AVI files with xfmedia (with only 20% cpu usage).

acpi, c-states (c1, c2,c3), cpu throttling, battery metter: all good
suspend/resume: ko on resume.

me: :D

---

### Post by frogotronic on 2006-10-20
Dell Inspiron 8100 laptop

PIII 1 Ghz Intel CPU

40 GB HDD Hitachi

512 MB RAM

Toshiba DVD/CD Combo drive

nVIDIA GeforceGo 16 MB GPU

Microsoft MN-720 Wireless PCMCIA card

****Almost Everything works in Dapper Drake; even using Twinview to clone my screen via the VGA output for PowerPoint (using Crossover Office) Presentations*****


[B]What Doesn't work:

SLEEP; HIBERNATE; STANDBY[/B]

---

### Post by arkangel on 2006-10-20
**EPSON STYLUS D78  works** out of the BOX it uses the D68 
gutenprint driver :)

---

### Post by willca on 2006-10-20
HP Pavilion dv5224nr

AMD 64 Turion ML-37
ATI Radeon Xpress 200M
Broadcom 4318 Airport WLAN
Realtek 8139 Ethernet
DVD-RW
ATI Technologies Inc IXP SB400 AC'97 Audio Controller


Works off the bat for almost all, except had to do ndiswrapper for my stinking Broadcom.

Cheers
-W

---

### Post by galamud on 2006-10-21
Toshiba Satellite A105-S4094

Everything except memory card reader works perfectly out of the box.  Haven't tested modem.

The following script makes SD card reading work using the card reader.  Haven't tried any other types of cards.

# Remove SDHCI and MMC modules, if they are installed.
        modprobe -r sdhci
        modprobe -r mmc_block
# Change what interface is enabled.
        setpci -s 07:06.2 4c.b=02
# Load the SD and MMC modules again.
        modprobe sdhci || exit 1
        modprobe mmc_block || exit 1
        exit 0

I put this script in /etc/init.d as "fixsdcardreader" and then used update-rc.d to make it load at all appropriate runlevels.

---

### Post by rowol on 2006-10-23
Shuttle SS30G2

I bought one of those shiny new Shuttle SS30G2 SE's from Newegg a few weeks ago.

Yes, you can get Ubuntu Edgy EFT Beta 6.10 to run on it.
No, it's not easy.

I was disappointed that I didn't get any real help when I posted to the forums earlier.

The main problems are that the onboard SATA II controller is not recognized by the kernel, and the onboard ethernet controller is recognized but doesn't work with the included kernel driver.

To fix the problem, first I had to get the source for the same kernel that's on the install CD from [www.launchpad.com](www.launchpad.com) (?) I then had to patch the drivers/scsi/ahci.c driver...   and not with an official patch either, the manual changes I made came from a posting I found on the internet from some guy at Sis, referring to a different kernel version.

Then I discovered the ethernet controller didn't really work either (ping worked, but ftp and telnet didn't, the MAC address in ifconfig was wrong, etc) and later I found a sis190.c driver on Sis's website.   This driver was for kernel versions 2.6.9 or higher (the Edgy I used was 2.6.17.10 I think)   I'm not sure why the kernel people are using the one they are in 2.6.17 kernel, but replacing it with the one from Sis's website made the ethernet card work (oh yeah, did I mention I had to edit the driver source a little to make it compile too?  =)

I don't know if the onboard video controller works or not (there is driver source for it on the sis website also.)   I was using a Chaintech GeForce 6200 (nVidia) PCI-X card, so I never really tried the onboard controller with Linux.

Once I got the SATA 2 and NIC drivers working, I had to get them onto the install CD, which forced me to remaster the install CD with the new drivers and a new initrd.   Despite what the one guy that replied to my post thought (yes, I do appreciate that he was trying to help) you CAN replace the initrd.gz and drivers on the install CD and if you do it right it won't break the install.   There are some instructions for remastering the install CD on the Ubuntu Wiki, although the section that deals with changing drivers has at least one major mistake in it that I eventually discovered.

If anyone else bought one of these particular Shuttle machines from NewEgg, they really are pretty nice at a reasonable price... and if you drop me an email, I will send you two Open Office documents that detail the steps I did to build both drivers and remaster the install CD.   Or if after reading that you're too lazy or too intimidated to try it or hey, you just want to save like a day or so worth of work, I'll happily burn you a copy of mine for $20.

---

### Post by jlangston on 2006-10-23
Asus A6000 Entertainment Notebook on Edgy RC

Install perfect!!!
Everything works great but have not checked if the card reader or 1.3 megapix camera works yet.

Core Duo
PRO/Wireless 3945ABG Network
82801G (ICH7 Family) High Definition
Nvidia Geoforce 7300

---

### Post by wylie348 on 2006-10-23
After alot of work, things are looking pretty good on my tablet.
Totally wiped out windows... Clean Ubuntu!

Working:
Tablet with rotation and function buttons (thanks to external patch)
Sound (only through headphones)
Wireless ethernet (Have not tried built-in ethernet, but recognized)
acpi seems to work, but had to acpi=off to get Edgy to install
Edgy did not want to install with too many (>4) partitions on hard disk
SD slot works

Not Working:
Cannot determine how to measure temperature - LM-Sensors does not appear to work even with latest driver
Speaker sounds not working (But headphones do)

Overall very happy with performance so far under Edgy - hope it does not break!

:D

---

### Post by arunabh on 2006-10-24
Model No.
HP Pavillion dv5118TX Notebook PC (EV899PA)

Series
HP Pavillion dv5100 Series

Processor
Intel Core Duo Processor T2300 with Intel Centrino Duo Mobile Technology (1.66GHz, 2MB L2 cache, 667MHz FSB)
82801G (ICH7 Family) SMBus Controller
SMP support not configured yet.

Intel 945 PM Express Chipset

Dual boot -- Ubuntu 6.06 LTS - the Dapper Drake ,Windows XP sp2

System memory  1GB (1 x 1GB) DDR2 SDRAM (667 MHz)

Graphics - nVIDIA go Geforce 7400 [512 mb shared]

Hard drive  100GB (5400 rpm)

Optical drive Dual Layer DVD+RW/+R  

Integrated Bluetooth HP Module, Integrated 802.11 b/g
Network 10/100 LAN Ethernet integrated

Display
15.4 -inch WXGA High-Definition BrightView Widescreen Display
[1280 x 800]

Audio
3D Sound Blaster Pro compatible sound 16 bit intergrated

---

### Post by tigerfox on 2006-10-24
I've got Sony Vaio VGN-SZ28GP/C and everything works fine except for the ff:

1) Plugging in a headset would mute speaker and no sound coming out the headset. (I dual boot to windows and headset working fine)
2) Finger Print Sensor device not working.  Guess it's not yet part of the sony-pi.
3) No driver for NVidia Gefore GO 7400.
4) S1 and S2 buttons not working.
5) Unable to use any projector as VGA output not working.

---

### Post by Julius on 2006-10-24
Toshiba Satellite M40-145 (bought in Spain)

Pentium M processor 1.86Ghz
80GB Hard disk
1GB RAM
ATI Mobility Radeon X300
Intel PRO/Set Wireless 2200

Everything (sound included) works right out of the box. I'm yet to try the card reader, and the cardbus, but I dont have any of those to try on.

But it works like a charm  here :)

---

### Post by Tankard on 2006-10-24
**game/desktop box;**

Asus A7N8X board
nForce 2 chipset (with eth0)
AMD Sempron 2800+
1 gig kingston ram
SB Live! Value
Radeon 9800 Pro 128mb
WD Caviar 40gb system drive (dual boot win2000)
Seagate Raptor SATA drive (games on win2k, accessible in ubuntu)
WD Caviar 80gb external

**server box;**

VIA KM4AM-V
KM400A + 8237 Pro chipset (RAID, eth0)
AMD Athlon 1700+
756mb ram
Seagate Barracuda 10gb sys drive
WD Caviar SATA 250gb storage (still working on getting it recognized :P )
Radeon 9200 SE 64mb

---

### Post by MrBbDD_OK on 2006-10-24
Toshiba Satellite A105-S4074
Core Duo Processor T2050
1.5 GB RAM
120 GB HD

Has Windows XP Media Center Edition and U6.06. dual booting via 3rd party boot manager.

What else?:(

---

### Post by piotrwoj on 2006-10-25
In Edgy work fine with madwifi-ng GN-WIAG-02 on single chipset ath 5005 GS. Kismet work!!! :)))) Mac adress may be changed... Ifconfig ath0 hw ether xx:xx....xx
-------------------------------------------------------
[DRZWI]("http://www.drzwi-warszawa.pl/")

---

### Post by nowhere.elysium on 2006-10-26
Ok... I use a Dell Inspiron 6000... *ducks*
I'm sure that most people have heard the horror stories associated with this machine, but Ubuntu's been a real boon for me: it works. Straight out of the box.
The version of the machine that I got was this:
1680*1050 TFT monitor,
ATI Radeon M300 graphics card,
512MB RAM (When I remember, I'm gonna upgrade this)
Dual-Layer DVD-ReWriter - NEC 6650A
80GB SATA Hard Disk - I don't remember the exact flavour
Intel ProWireless 2200 card
Broadcom 4400 Wired Ethernet card
Ricoh CardBus SD Card Reader (also hosts the FireWire port, for some reason)
Synaptics Touchpad

I think that's about it: it's all I can remember at this point, certainly, and I can't be bothered to start chopping up dmesg output right now, so there.
The only thing that does play sillybuggers at any point is the Synaptics touchpad - the horizontal scrolling doesn't work without some serious xorg.conf alterations. Oh, and the WiFi LED still doesn't work. Because it's something that really would change my life, I'm sure ;)  .

---

### Post by eran- on 2006-10-27
My hardware list:

MSI P965 Neo-F
Intel Core 2 Duo E6400 Boxed
Club3D nVidia GeForce 7950GT 512mg
Corsair Twin Kit 2 x 512MB DDR2
LG DVD-RW -drive
Logitech Internet Navigation Keyboard
Logitech MX518
Seagate Barracuda 250GB S-ATA (not connected to RAID)
Videoseven LCD-TFT 19" 12ms 1280*1024

(and I've got [problems]("http://www.ubuntuforums.org/showthread.php?p=1671096#post1671096") with this hardware...)

---

### Post by Yumi on 2006-10-27
Wireless LAN Card

EagleTec ET-WB2400 54Mbps Wireless LAN Card PCMCIA CardBus (32bit)

Works with Edgy Desktop out of the box.

Michael

---

### Post by mblinux on 2006-10-28
Motherboard: ASROCK P4i65G
Proc: Pentium4 2.8GHz FSB 533 Northwood
1x512 DDR333 Kingston Memory
1x256 DDR266 memory
1x80GB Western Digital HDD
1x160GB Maxtor HDD
Video: PNY GeForce 6200 256MB
Audio: Onboard C-media 9761A 5.1
DVD-rec: Pioneer DVR-111D

Works perfectly with Kubuntu Dapper, I'll try soon Edgy.

---

### Post by machoo02 on 2006-10-28
I have a Thinkpad R52 (1849-4WU):
Proc: Pentium M 750 (1.86GHz)
RAM: 1.5GB DDR2
Optical: DVD+/-RW, Matsushita, I think...don't remember off the top of my head, and not on my laptop now.
Video: ATI Mobility X300 (64MB)
HDD: 80 GB
LAN: Broadcom NetXtreme Gigabit ethernet
WLAN: Intel PRO 2915 a/b/g

Everthing has worked great out of the box with both Dapper and Edgy.  Currently dual booting with WinXP, but that problem will soon be solved when I move it over to VMWare.

---

### Post by didobuntu on 2006-10-28
My hardware,
 Asus laptop W2Jc
processor, Core Duo T2500 (2GHz).
graphic card, ATI Mobility Radeon X1600 (256Mb dedicated), Beryl/Xgl works like a charm.
screen, 17 inch WSXGA (resolution 1680x1050)
Intergrated Bluetooth (runs well under Drapper, less well under Edgy).
Wifi: Intel Pro Wireless 3945, runs well under Drapper and Edgy.
Touchpad: can be easily activated/desactivated modifying xorg.conf.

There is a Built-in DVB-T TV Tuner card .. I never tried to use it under Linux (I know it would be unsuccessful)

Sound Card : hda-intel, chip Realtek ALC882: This never ran, since I bought the laptop. I never heard any sound under Linux ..  tried alsa 1.0.10, 1.0.11, 1.0.12, 1.0.13 ... no way ... This renders the Asus W2Jc not Linux friendly and all the good features above are reduced to nough.

Idea: I should put it on a waste basket soon.

---

### Post by Wesseli on 2006-10-28
Dell Latitude D510 (laptop)
Logitech MX1000 (wireless mouse)
TW-EA510 ADSL Modem Router (wlan modem)

Worked out of the box in dapper and now on edgy. I use wireless connection to internet, flawless connection and quickly for noobie...

---

### Post by mblinux on 2006-10-29
Acer Travelmate 240 (in reality it's a 244 although it's marked on the plastic as 240). I expanded the memory: it had 256MB ram now it has 256+512.
Everything works ok with Ubuntu 6.10 Edgy. Dual boot system WinXP Home SP2 + Ubuntu 6.10.

---

### Post by pfx on 2006-10-29
Dapper Drake works fully with Acer Aspire 3618AWLMi (Now listed as 3618AWXMi), including wireless, touchpad, function keys, easy-launch buttons, except for the extra Euro and Dollar symbols near arrow keys, and the button for wireless does not light up (it still works)

---

### Post by adolfotregosa on 2006-10-30
Edgy and laptop acer 169x

Have to add to monitor section on xorg Option "MonitorLayout" "LVDS, AUTO". If not i allways get a black/standby monitor on X start :(

Card reader works with this driver (v0.6) [http://developer.berlios.de/projects/tifmxx](http://developer.berlios.de/projects/tifmxx)

ati x700 - fglrx and xgl

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
[http://wiki.cchtml.com/index.php/XGL-Ubuntu](http://wiki.cchtml.com/index.php/XGL-Ubuntu)

everything else works - except in shitdows my battery lasts more ... cpu at 800mhz and aticonfig --set-powerstate=1

---

### Post by Vega on 2006-10-30
Toshiba M105

everything works perfectly. Just need fn key commands for screen brightness control and volume. 

Intel Core Duo 1.6Ghz (with centrino mobile technology)
512 MB DDR2 RAM
Intel GMA 950
80GB 5400 SATA Drive
RealTek HD Audio

And another piece of hardware that is compatible is:

ATi X1600XT 256MB GDDR3
(I was suprised it worked at full resolution 1600 by 1200)

---

### Post by meyrd on 2006-10-30
Asus P5WD2 Premium MB
em64t 3ghz proc
4gb ddr2 667mhz kingston ram
intel ich7r southbridge for sata support 4x
silicon image 3132 sata controller 1 internal 1 external
(2)gigabit lan controllers 1 intel pcix 1 marvell
realtek alc882d hd audio controller
ti 1394 controller
maxtor 250gb sata drives 3x
sony dru-820
ati radeon x1300 pcix
viewsonic vx924
belkin soho kvm 4 port switch w/usb-ps2

All works great right from install with 64 bit dapper.:cool:

---

### Post by voided3 on 2006-10-31
I plan to install Ubuntu on two of my computers at home over xmas break, but I have it running currently on:

-Soyo SY-K7VTA-B mobo
-AMD Athlon XP-M 1800+ @ 1463mhz with OCed FSB (board was made before the Athlon XPs came out...it's known in BIOS as "Unknown CPU typ"...haha)
-1.0 gig SDRAM
-ATI Radeon 9250 (haven't tried dual monitors with it yet though, and I had to go through a bit of searching to get the driver working right as many ATI users have found)
-HP f50 15" LCD @ 1024x768 on DVI
-Dynex surround sound card (ICE Ensemble mixer)
-VIA USB 2.0/Firewire card
-Maxtor Diamond Max 160 gig HDD
-WD Extreme 320 gig USB/Firewire external drive
-Linksys ethernet adapter

This system is probably seen by some as a bit of a relic being 4 years old now, but I got Windows XP to run on a 200mhz Compaq from '96 so I know the meaning of slow and this definetely isn't it!! Plus I plan to put Ubuntu on a 450mhz K6-III equipped system, but i'll post how that works when it does.

---

### Post by Scheater5 on 2006-10-31
I previously posted that everything worked "out of the box" with Dapper on my Dell Inspiron 9300 except wireless, that I got working with a wrapper.  Upgraded to Edgy about two days ago, and everything, including wireless, worked out of the box, minus some playing with the screen resolution.

---

### Post by maprx on 2006-11-02
Panasonic digital camera FZ7.  This camera is seen by Ubuntu  but will not connect either as a usb storage device or camera.  This is using  digikam or gtkam.  The camera did work with mandriva 2006 and mepis 6:-?

---

### Post by keltren on 2006-11-02
Motherboard: Asus P5LD2 SE (Rev.2.03)
Ram: 2x 1GB Samsung DDR2-400
CPU: Core 2 Duo E6300
GPU: Geforce 7800GTX 256MB
HD: Maxtor 200GB Sata HD
CD: Samsung Sata DVD-Recorder

Everything works perfectly although the built-in soundcard requires this fix:
```

sudo touch /etc/modprobe.d/sound

then edit the file (with "sudo nano -w /etc/modprobe.d/sound" or your favourite text editor) and add this line to it, save and reboot (or reload the module):

options snd-hda-intel position_fix=1 model=3stack

then:
sudo update-modules

```
Got the fix from this thread: [http://ubuntuforums.org/showthread.php?p=1627031#post1627031](http://ubuntuforums.org/showthread.php?p=1627031#post1627031)

Only problem is that gnome use the "headphone" channel as master which doesn't do anything (it should be the "Front" channel), the mixer still works fine, but the multimedia keys on my keyboard only control the useless  "headphone" channel and there doesn't seem an easy way to change this...

---

### Post by daou on 2006-11-03
Fujitsu-Siemens Amilo Si 1520-23

Installed with Edgy. Doesn't boot unless given the "noapic" command for the kernel. Had to install 915resolution to get 1280x800 res. No luck on  returning from hibernate or suspend yet (perhaps related no the noapic?). But other than that, works like a charm.

WLan, LAN, sound, power-management, etc. works right away after the installation. No complaints. And Beryl works great too.

---

### Post by bruma on 2006-11-04
HP Compaq nx8220 installs and works perfectly.

WLAN on/off switch button is working, but blue light indicator is never turned on.

Beryl is also working, but very unstable, often crashes...

Didn't try IRDA and bluetooth.

---

### Post by decoyjim on 2006-11-04
**_Gateway MX3215 Laptop_**
- *S3 Unichrome Pro* Video (works with openChrome driver from svn)  You will need to set up svn to get the latest openChrome driver, then change "vesa" to "via" in xorg.conf.
- *VIA Audio*
    ***To make this work, disable "External Amplifier"
       from alsamixer
- *VIA Rhine* LAN connection (works out of box)
- *Internal Modem* might work, never tried it.
- Synapitics Touchpad works out of the box.
- Everything else works out of the box except....

- *Broadcom 54g* Wirless miniPCI card
This was predictably the time consumer.  It CAN work perfectly with Network Manager, but the order of steps must be exact...
1. Add the line "blacklist bcm43xx" to /etc/modprobe.d/modules
2. Reboot
3. apt-get ndiswrapper (with all repos activated)
4. Under ndiswrapper, Install the bcml5a.inf driver (forget where to get it) with ndiswrapper.
5. depmod -a
6. modprobe ndiswrapper
7. add "ndiswrapper" to /etc/modules
8. iwlist eth1 scan
9. Now, before continuing to join an SSID, apt-get install network-manager
10. Reboot
11. When logged in, you'll be able to use NetworkManager to join your AP with WEP if necessary.

---

### Post by FurryNemesis on 2006-11-04
LG GSA-2164D External USB-2 Super Multi DVD Rewriter.

Works out of the box with Gnome CD/DVD tools. :D

---

### Post by pitkali on 2006-11-05
Hi,

I have Lenovo/IBM ThinkPad T60 with Ati Radeon X1300, 14" display (1400x1050), 1024 MB of RAM, Intel PRO wireless ipw3945 and combo optical drive. Both Dapper and Edgy works supporting all the hardware, but:

* radeon driver from dapper didn't work. I had to use either vesa or fglrx, but AFAIR with vesa suspend doesn't work. I didn't try radeon driver under Edgy.
* Suspend doesn't work with default ati drivers available in Edgy. I had to get newer version from ati page.
* If anybody doesn't know yet - when using ati driver you should disable the Composite extension of xorg server.
* under Edgy I noticed that using other cpufreq governor that userspace (ondemand or conservative) makes suspend not working (or not consistent, i.e. sometimes it works and sometimes it doesn't).

Regards,

---

### Post by dhughes on 2006-11-05
Compaq Armada E500

Hard Drive 20GB Hitachi DK23CA-20
Pentium III @ 850MHz 32/256 cache
256MB SDRAM
CD/DVD ROM read only, no write
Floppy

Some of the lspci output:

Multimedia audio ESS Technology ES1978 Maestro 2E rev 10
Ethernet Intel 82557/8/9 Ethernet Pro 100 rev 09
ATI Technologies Inc Rage Mobility P/M AGP 2x rev 64
CardBus bridge Texas Instruments PCI1225 rev 01
PCI bridge Intel 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge rev 03
Host bridge Intel 440BX/ZX/DX - 82443BX/ZX/DX Host bridge rev 03
IDE Interface Intel 82371AB/EB/MB PIIX4 IDE rev 01


Note:
Ubuntu 6.06 works, Ubuntu 6.10 fails (both have Ethernet issues)

---

### Post by openaddict on 2006-11-08
So far, everything is working correctly.  I haven't tested the wireless NIC yet, but it was recognized and the correct kernel modules were loaded.

Dell XPS M170 Laptop
Intel 915GM Chipset
Intel Pentium M 2.26Ghz CPU
2GB 533MHz DDR RAM
Intel 2915A/B/G Pro Wireless Card
Broadcom NetXtreme BCM5705M_2 Gigabit Ethernet Adapter
Intel 802801 (ICH6 Family) AC'97 Audio Controller
Intel 802801 (ICH6 Family) AC'97 Modem Controller
NEC ND-6650A DVD+-RW Drive
Fujitsu MHV2120A 120GB SATA Hard Drive
Alps GlidePoint Touchpad
nVidia GeForce GO 7800GTX PCI Express Video Adapter
17" 1920x1200 Laptop LCD Display

All USB ports are working correctly and my external Logitech USB Trackball works perfectly.

No hardware problems at this time.

---

### Post by beemer on 2006-11-09
[Biostar TForce 6100]("http://www.newegg.com/Product/Product.asp?Item=N82E16813138027")

Video, Sound, Networking all worked with Live CD (Kubuntu 6.10) and install.  Nvidia-glx installed w/o issue and works fine.

---

### Post by Obor on 2006-11-09
Dell SmartPC 250N (laptop)
2.4GHz Intel Pentium 4
512 MB 3.3-V SODIMM DDR RAM 
ATI Rage Mobility -M6, 32MB DDR Graphics
Active-matrix TFT display 1400x1050 SXGA
IBM Travelstar HDD
240cpi Touch pad
Microsoft basic optical mouse with scroll wheel
HP Deskjet 3820 printer

with Kubuntu 6.06 - everything worked straight from the box, shut down, restart works fine. Didn't try hibernate/suspend.

---

### Post by rax_m on 2006-11-10
Ubuntu Edgy 6.10
Laptop
Toshiba
P100-429

Initially I thought that the fans weren't working, but it just seems to come on a lot less frequently than Windows. If I could only get lm-sensors working..

---

### Post by Compaq Armada 7800 on 2006-11-12
feels pretty darn good to have this setup working again:

1) Ubuntu 6.10 ; 2.6.17-10-generic kernel
2) Compaq Armada 7800
3) Pentium 2; 224 ram; DVD drive; Belkin wireless 802.11g, F5D7050; S3 video driver
4) all this worked out of the box, i still have no ESS1879 audio driver. working

---

### Post by mgmiller on 2006-11-12
I'm running Dapper.  I just switched out by old PS2 keyboard for a new Saitek Eclipse II USB.  All the standard keys worked out of the box (make sure you have "Generic 104-key PC" keyboard selected in Keyboard preferences layouts.  The only thing I had to do to get all the multimedia keys working was to run System > Preferences > Keyboard Shortcuts and then for each of the multimedia keys click it once while highlighting the appropriate function.  It took longer to type this than to do the whole thing.  Right now, my keyboard and desk are illuminated a nice red color from the keyboard.  Nice tactile feel to the keys also.  :-D

---

### Post by zibletop on 2006-11-14
Hi,

I'm running Ubuntu Edgy on a Sony Vaio PCG FX705. The full report is [here]("http://zibletop.free.fr/pub/Linux_Ubuntu_Edgy_On_Sony_Vaio_PCG_FX705.html")

---

### Post by kishd on 2006-11-14
IBM Thinkpad T20
Ubuntu 6.10

Install with alternate cd and add 
Option "DMAMode" "None"
Option "BusType"  "PCI"

to xorg.conf via recovery console.

Add acpi=force to kernel options in grub for hibernate and suspend support.

Everything works including on screen display of volume changes.

---

### Post by civilian on 2006-11-18
Ubuntu 6.10

Hp Pavillion dv5163cl

- Intel Centrino duo (not sure if i'm actually supporting both cores, but everything works fine so i don't ask questions)
- Nvidia Geforce 7400 Go (works great)
- Intel integrated wireless (works off the bat!)
- Nothing else that i know of that i could've got problems with

---

### Post by fnf on 2006-11-18
Acer Aspire 5583WXMi (the 5580 family)

[LIST]
[*]Intel Centrino Duo Core (cpufreq enabled and worked)
[*]Intel 82801G High Definition Audio Controller
[*]NVidia GeForce Go 7300 (worked with the nv driver, but frequently /crashed/ if I dared to try nvidia-glx)
[*]Marvell PCI-E Ethernet controller 88E8038
[*]Intel Wireless 3945ABG
[/LIST]

Except the issue with nvidia-glx, all of them worked out of the box.

---

### Post by DirkRaeder on 2006-11-18
Fujitsu-Siemens Computer Lifebook E 8110
[LIST]
[*]Intel Core Duo T2400
[*]2x512 MB DDR2-667 RAM
[*]Chipset: Intel 945 GM; ICH 7-M
[*]Marvell 88E8055 GBit-LAN
[*]WLAN: Intel PRO Wireless 3945 ABG
[*]SD-Card-Reader
[*]DVD-Reader/Writer
[/LIST]

Not tested yet:
[LIST]
[*] Bluetooth
[*] SmartCard-Reader
[/LIST]

Except Bluetooth and the SmartCard-Reader, which I didn't test yet, everything worked pretty much out of the box. The only thing I had to "repair" was the resolution of X11, but that was done by installing 915-resolution.

Regards Dirk

---

### Post by Smirre on 2006-11-18
**Mainboard:** Asus P4P800 Deluxe i865PE socket 478 mainboard
**CPU:** Intel Pentium4 - 2.8 GHz @ 3.5 GHz (Northwood, 512KB L2)
**HDD:** 2x120GB Western Digital P-ATA 100, 1x250GB Western Digital S-ATA 150
**RAM:** 2x1024 GEiL PC3200 Value memory CL2.5 
**GFX:** Aopen Aeolus GeForce 6800GT 256MB GDDR3
**Sound:** Creative Soundblaster Live! 5.1
**Network:** Built-in 3Com Gigabit LOM
**DVD-ROM:** AOpen 16x DVD player
**DVD-RW:** Plextor PX708A 8x DVD burner

Works with Ubuntu 6.06 Dapper Drake. S-ATA drive shuts down when rebooting from Linux (though not when rebooting from Windows). Spins back up at POST screen. Been unable to solve that small quirk.

---

### Post by unbuntu kid on 2006-11-18
Compaq Presario V5204NR
wifi requires Linuxant, Ndiswrapper will not work
requires 915resolution package for correct screen resolution
Battery meter somehow shares itself w/ windows!
Nice little trick: instead of turning off an os to switch it, just hibernate it!  This is very helpful w/ windows as it takes forever to login.
I recomend keeping windows as a stable OS as this laptop does not ork great w/ wifi

---

### Post by RobNyc on 2006-11-20
**Mainboard:** Asus P4P800E Deluxe i865PE socket 478 mainboard
**CPU:** Intel Pentium4 - 3.0ghz (Prescott, 1024KB L2)
**HDD:** 160GB Western Digital WD1600JB-22GVA0 ATA 
**RAM:** 2x512 SuperTalent PC3200 dual-channel 
**GFX:** Sapphire Radeon x1600 PRO 512mb AGP 
**Sound:** Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio
**Network:** Built-in Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet **Network2:**Intel Corporation 82557/8/9 [Ethernet Pro 100] 
**DVD-RW:** NEC ND-3520A, 48xPlayer ATAPI

---

### Post by Flak Magnet on 2006-11-22
Almost everything works perfectly right out of the box after loading Edgy.

Details at:

[www.flakmagnet.com/m115.html]("http://www.flakmagnet.com/m115.html")

Highlights of what works:
Pentium Centrino DuoCore 1.6 GHZ - Speed stepping works.
80GB SATA HDD
Intel Graphics
14.1 1280x800 wide-aspect.
Intel LAN
Intel 3945 WLAN
Multi-mode DVD Burner
Hibernation - Kills the sound until full reboot though... wierd.

Lowlights of what doesn't work:
5-in-1 Flash memory card reader.
Suspend - Keyboard doesn't work on resume.
Quantum kanooder valve-based time bifurcater circuit - The sales guy SWORE it had one, but it isn't recognized for some reason.  ;) 

Check my page for details.

--Tim

---

### Post by trondhuso on 2006-11-24
Ubuntu is running on this hardware:
Compaq Evo Notebook N160 - PIII-M 1.13 GHz - 14.1" TFT
Processor Intel Pentium III-M 1.13 GHz 
Cache Memory 512 KB - L2 cache - Advanced Transfer Cache 
RAM 512 MB (installed) / 1 GB (max) - SDRAM - 133 MHz 
Hard Drive 30 GB
Optical Storage CD-RW / DVD-ROM combo - plug-in module
Display 14.1" TFT active matrix 1024 x 768 ( XGA ) - 24-bit (16.7 million colors)
Video:
Supported Display Graphics - VGA (640x480), XGA (1024x768), SVGA (800x600), SXGA (1280x1024) 
Max Resolution (external) - 1280 x 1024 / 24-bit (16.7 million colors) 
Graphics Processor / Vendor - ATI Mobility Radeon - AGP 4x 
Video Memory - DDR SDRAM - 8 MB 
Graphics Controller ATI Mobility Radeon - 8 MB 

Audio Output Sound card
Telecom Fax / modem - Mini PCI - 56 Kbps 
Interfaces - 1 x parallel - IEEE 1284 (EPP/ECP) - 25 pin D-Sub (DB-25) ¦ 1 x display / video - VGA - 15 pin HD D-Sub (HD-15) ¦ 1 x display / video - S-video output - 4 pin mini-DIN ¦ 1 x headphones - output - mini-phone stereo 3.5 mm ¦ 1 x microphone - input - mini-phone mono 3.5 mm ¦ 1 x network - Ethernet 10Base-T/100Base-TX - RJ-45 ¦ 1 x modem - phone line - RJ-11 ¦ 2 x USB - 4 pin USB Type A ¦ 1 x docking / port replicator ¦ 1 x IEEE 1394 (FireWire) 

Also with a 3Com OfficeConect (3CRWE154G72) wireless card.

I have not tried the fax/modem and do not know if it works. If someone has a how to on how to set this up, please let me know.

One thing that doesn't work is the battery meeter. 

Ubuntu-version 6.06

-t-

---

### Post by chinese_ys on 2006-11-30
Acer Aspire 5602

Intel core Duo 1.66Ghz

15.4" WXGA CrystalBrite LCD(16ms)

Intel Graphic Media Accelerator 950GM

AC97 Audio Controller

Realtek RTL8193 Ethernet NIC

Intel ipw3945

everything works fine with a few settings

---

### Post by dubrict on 2006-12-01
Self-built tower

Edgy 6.10 - 64bit
Asus A8N-SLI-Deluxe motherboard - nForce4 AMD Chipset
  Works great, only problem I've had is that usually if I hard-reboot, the USB keyboard doesn't work at all until linux is almost finished booting up.  You would think it was a bios problem, but I never had it happen before switching to linux.  Happens in all distros I've tried though.

SoundBlaster Audigy2 ZS
  Autoconfigured fine, but I don't know how much of it's sound-processing power is being put to use.  Onboard audio was disabled in the bios.

Leadtek Winfast2K Video capture card - bt878 chipset
  This has been the big problem.  I've tried and tried to get this thing working.  I've read every forum and tried every guide to get it to work, but the closest I've gotten to having it work was displaying one channel with exceptionally poor quality and static audio.  Everywhere I look though, people insist that this chipset and even this specific card work flawlessly out-of-the-box.  I don't know what gives.  It works in windows.

19" Flat-panel monitor that gets detected as named "CMO CMC 19" in most distros.  It supports 75hz refresh rate at 1280x1024, but I haven't been able to set it above 60 in ubuntu.

HP Deskjet 3645 - Gets detected as a 3740, but that's close enough and it works.

I have 2 geforce 6600GT's, but ubuntu only detects one of them when configuring xorg.  I have to load xorg.conf and add another device section with it's BusID.  (Well, I don't really have to because xorg finds it on boot.  But if I want to set any options for it, it needs to be there in the file)
Everything else works perfectly.

---

### Post by Rinzwind on 2006-12-03
Dell Inspiron 9300 and an own-built desktop PC (Gifabyte 4G4A+ mainboard).

Sitecom CN-531 Wireless Bluetooth Headset with the included USB-dongle working perfectly on both machine.

I used most parts of these 2 wiki-pages:
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)
[https://help.ubuntu.com/community/BluetoothAudio](https://help.ubuntu.com/community/BluetoothAudio)

and some swearing and headaches :)

---

### Post by amgeex on 2006-12-03
1)Version Of Ubuntu: Edgy 6.10
2)Type Of Hardware: LCD Flat Panel Monitor
3)Hardware Maker: Samsung
4)Hardware Model: SyncMaster 940BW

NOTES: Works like a charm with DVI-I connection, haven't tested it with VGA connection, but I assume it should work equally well. No problems whatsoever, Ubuntu detected it automatically. :mrgreen:

---

### Post by Sponge34 on 2006-12-04
1)Version Of Ubuntu - Edgy Eft
2)Type Of Hardware - Laptop, Intel Wireless, nVidia GForce4 4200
3)Hardware Maker - Dell
4)Hardware Model - Insiron 8500

Headaches: The wireless card comes up as eth1 which causes some problems...

---

### Post by PartisanEntity on 2006-12-05
1)Version Of Ubuntu - **Dapper (6.06)**
2)Type Of Hardware - **Laptop, Broadcom 4306 wifi, nVidia GForce Go 6200, Turion processor.**
3)Hardware Maker - **Asu**s
4)Hardware Model - **Asus A6K**

No problems. All hardware supported and working including SD card reader, synaptics touchpad, buttons for: mail, browser & touchpad-lock.

Installed drivers for the wireless card using ndiswrapper. Used wpa-supplicant and network-manager to use wireless internet.

---

### Post by alek66 on 2006-12-05
HI!!! this is my gear!!!


SYSTEM INFORMATION
 - Operating system type -> [Linux]
 - Distribution release -> [testing/unstable]
 - Kernel version -> [2.6.17-10-generic]
 - Kernel build time and date -> [#2 SMP Fri Oct 13 15:34:39 UTC 2006]
 - Computer hostname -> [Darkstar]
 - Computer domainname -> [(none)]

Some program versions
 - GNOME version installed -> [2.16.1 - Ubuntu (2006-10-02)]
 - GCC version installed -> [4.1.2 - x86_64-linux-gnu ]
 - Xorg version installed -> [7.1.1]

Uptime
 - System running -> [0 days 1 h 27 min]


CPU INFORMATION
 - Vendor identification -> [AuthenticAMD]
 - Model name -> [AMD Athlon(tm) 64 Processor 3000+]
 - Raw frequency -> [800.000 MHz]
 - Cache size -> [1024 KB]
 - Model number -> [4]
 - Family number -> [15]
 - Stepping -> [10]
 - BogoMIPS -> [1602.47]


MEMORY INFORMATION
 - Total memory - RAM -> [510 Mb]
 - Swap memory -> [1494 Mb]


IDE INFORMATION
Primary Master (hda) - disk
 - Model name -> [IC25N060ATMR04-0]
 - Capacity -> [58.6051 Gb  (actual - 55.8902 Gb)]
 - Cache -> [7.69922 Mb]

Primary Slave (hdb) - unknown
 - Model name -> [unknown]
 - Capacity -> [unknown]
 - Cache -> [unknown]

Secondary Master (hdc) - cdrom
 - Model name -> [TSSTcorpCD/DVDW TS-L532A]
 - Capacity -> [8.03193 Gb  (actual - 7.65984 Gb)]
 - Cache -> [unknown]

Secondary Slave (hdd) - unknown
 - Model name -> [unknown]
 - Capacity -> [unknown]
 - Cache -> [unknown]


HARDWARE INFORMATION
Motherboard chipset
 - Host Bridge -> [echnologies, Inc. K8M800 Host Bridge ]
 - PCI Bridge -> []
 - ISA Bridge -> []

IDE interface
 - String -> [echnologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) ]

VGA controller
 - Graphic card -> [a Corporation NV36 [GeForce FX Go5700] (rev a1) ]

Sound card/s
 - Card #1 -> [echnologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50) ]

Ethernet card/s
 - Card #1 -> [ys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01) ]
 - Card #2 -> [ek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10) ]


OTHER INFORMATION
Sound card
 - Model name -> [ VIA8233 - VIA 8235]
 - Details -> [ VIA 8235 with VIA1612A at 0x1400, irq 201]

Nvidia Graphic card
 - Model name -> [GeForce FX Go5700]
 - AGP rate -> [8x]
 - Faste writes -> [Disabled]
 - SBA -> [Enabled]
 - Driver details -> [NVIDIA Linux x86_64 Kernel Module  1.0-8776  Mon Oct 16 21:53:43 ]
 - Screen resolution -> [1024x768]

Input devices
 - Device #1 -> ["AT Translated Set 2 keyboard"]
 - Device #2 -> ["PC Speaker"]
 - Device #3 -> ["SynPS/2 Synaptics TouchPad"]

---

### Post by John.Michael.Kane on 2006-12-06
This thread is being temporarily locked while the information is transfered to the udsf database.

---

### Post by Oceola on 2007-01-01
Memorex 512Mb and 2 Gb Mini Travel Drives (Flash) both work with Ubuntu Breezy. Since both Breezy and Dapper use Pmount 0.9.6-1 my guess is they should work through to Edgy.
Both have a compatibility statement which includes Linux 2.4 kernel. Saw some older ones which had 2.3 kernel on them.
Best Buy has a sale on and the 512s are $10 US.

Will lock up the system if too much is attempted to be transferred at once but this seems to be relational to memory not the system software. They also open the CD, just leave it open. It will show a drop down menu which includes "eject", tried it and it closes the CD icon shown in Nautilus but also effects the Flash drive.

Both work OK and the files transferred still operate fully and install properly so nothing is added.
Both come with some out of date programs. Thunderbird, Migo and Usafe, not all are Linux builds.

---

### Post by peterthewolf on 2007-01-04
I have a tv card that works on edgy using kaffiene
It is a VideoMate DVB-T200 and is a straight forward install following the LinuxTV Install DVB instructions, the only exception being that after following the instructions you must put the saa7134.dvb into /etc/modules before rebooting.

I would have put this in the document guide but I think that by the time I learnt to do that TV will have been superceded.

---

### Post by bugboy on 2007-01-09
MS-6863 version 2.1
[more detail here]("http://www.msicomputer.com/product/detail_spec/product_detail.asp?model=VIA_PLE_133_5a_Lan")
running a p3 633mhz and also tried a 933mhz processor

256mb SDRAM 133mhz

Ultra ATA/133 CONTROLLER
[more detail here]("http://www.avlab.com.tw/ultra/1006_0086_000d.htm")
On the chip it says its chip number ite8211af
On ubuntu its saying its chip number ite8212 which is a raid controller.

Ubuntu server edition 6.06.

---

### Post by agamotto on 2007-01-20
Here is my entry for the HCL:

MSI mPC 51PV barebones SFF lunchbox computer

This lunchbox SFF barebones computer is made by MSI International, and includes the motherboard, a CPU cooler, case.

Specs:

Not sure what exact motherboard, but it supports Sempron 64, Athlon 64 & X2 in socket AM2 (940)

FSB 533/667 Mhz
Nvidia C51PV Northbridge
Nvidia MCP51 Southbridge
DDRII memory (2 slots) 2GB max 240pin 1.8v
CIS8201 Ethernet Lan port 10/100/1000
VIA VT 6307 IEEE 1394 (Firewire) up to 400Mbps
Realtek ALC880 7.1 channel Flexible audio Azalia 1.0 spec
1 IDE port Ultra DMA 66/100/133
1 SATAII port up to 300MB/s
7-in-1 media card reader
Nvidia NB (GeForce 6150 equivalent) on-board video with DVI, VGA, S-Video, Composite outputs  Can be set to use up to 256MB of system ram
260W full-range power supply
1PCI Express x16 slot
1PCI slot
1PCI Mini slot

I intalled this with the Windsor Athlon 64x2 65w processor, 1GB of DDR2 667 memory, along with a WD Caviar SATAII hd.  Ubuntu Dapper and Edgy 64 bit installed flawlessly on this machine, with no need to 'configure' anything.  Just put in the install cd, follow the prompts and go!

Very quiet system - when first turned on, the fans run at full speed for the first 30 seconds or so, then quiet down.

---

### Post by latinoguy on 2007-01-26
Acer notebook 1642 works very well, the only problem tha i had found is that the battery drain very fast, dont knwo why.

---

### Post by jgcamp99 on 2007-02-04
Dell L400 seems to be functioning quite well.

I had no cdrom, usb or floppy to boot from, so I used the PXE Network boot installation over the internet. It's tme consuming so I did it in the middle of the night and I'm quite pleased with the results. Edgy Eft replaces Windows 2000 Pro.

Everything seems to be working, ACPI that I read others having issues with don't seem to effect my install or experience with this notebook. Fan rarely comes on, then again it runs cool.

---

