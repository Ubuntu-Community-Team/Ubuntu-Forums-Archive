---
title: "Desktop Hardware Incompatibility List."
date: 2007-02-14
forum: Hardware
---

### Post by frodon on 2007-02-14
[B]Welcome To The Desktop Hardware Incompatibility List.
[/B]
The purpose of this thread is for you, the user, to post what hardware/hardware combination don't work with your desktop Ubuntu install. 

If you see an old warning regarding a particular piece of hardware, bear in mind that the problem might be solved in the present release of Ubuntu.

Everyone is welcome to post here, as long as it is hardware related data. For help with hardware problems, please use the standard procedure of searching the forums, and starting your own thread for assistance if no answer is found.

**_Give detailed explanations when reporting incompatible hardware including the version of ubuntu you use._**

**Also Do not post any lspci outputs in this thread as they will be removed with out question.**

[B]Please Only List
1)Type Of Hardware
2)Hardware Maker
3)Hardware Model
4)Known Issue[/B]

[COLOR=Red]***NOTE* This thread is exclusively for the listing of incompatible hardware. Any idle chatter or unrelated posts will be moved/removed accordingly. *NOTE***[/COLOR]

Thank you.

**PS: the old incompatibilty list thread can be found here and will remain closed** :
[http://ubuntuforums.org/showthread.php?t=207916](http://ubuntuforums.org/showthread.php?t=207916)

---

### Post by Mad Malc on 2007-02-15
Graphics Card
PNY Technologies
Nvidia 7600GS 8xAGP
Gives an error message on TFT display of 'Incorrect input'
Gives an error message on CRT Display of 'Out of Range' 'V: 92:6KHz H:45.8Hz'
When booting into X
Using Dapper Drake 6.06, solution is to upgrade to 6.10 edgy

---

### Post by mottalli on 2007-02-17
HP 500 Laptop

Touchpad (Synaptic) doesn't work by default, tried on Edgy and Feiesty, none of them worked.
After applying the fix mentioned here:
[http://ubuntuforums.org/showthread.php?p=2069870](http://ubuntuforums.org/showthread.php?p=2069870)
the touchpad works, but Ubuntu stops detecting my WiFi card (eth1 dissapears from the system, but eth0 and the modem work fine).

---

### Post by mjrclark on 2007-02-19
Emachines 370 PC
motherboard/cpu? (celeron 1.8ghz)
Fan does not power up.
like so; [http://www.mail-archive.com/linux-acpi@vger.kernel.org/msg04204.html](http://www.mail-archive.com/linux-acpi@vger.kernel.org/msg04204.html)
[http://ubuntuforums.org/showthread.php?t=364386](http://ubuntuforums.org/showthread.php?t=364386)

---

### Post by Amedee on 2007-02-20
Logitech Bluetooth Desktop MX5000 (combination keyboard&mouse) is partially incompatible.
It will work in legacy HID mode, but then all other bluetooth functionality (pairing with bluetooth phone) is disabled.
You can get the dongle in HCI mode, but then the keyboard and mouse stop working.
It is impossible to use keyboard&mouse and at the same time use any other bluetooth devices.

More info in [https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/32415](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/32415)

---

### Post by TwistesdTexan on 2007-02-20
Dapper and Edgy incompatability with Rosewill Wireless keyboard and a Logitec Trackman Wheel mouse. Works fine with Breezy. Takes a long time to reinstall. Breezy - Dapper - Edgy.

---

### Post by rfdeshon on 2007-02-22
ENE CB-712/4 (rev 10) 5-in-1 card reader
None of the cards I have tried show up nor do i see any system events when they are inserted.

Wireless Card
In Dapper showed up as Broadcom 4319
In Edgy shows up as Broadcom Corporation Dell Wireless 1470 Dual Band WLAN (even thought my laptop is from Lenovo and does not use Dell parts)
It kind of works using the BCM43xx drivers with the wl_apsta.o firmware package however it will ocasionally cause X to lock up solid and I often have to disconnect and reconnect to networks because it will randomly stop communicating.

---

### Post by mulperi on 2007-02-23
Motherboard Asus Commando, 0803 BIOS with SATA (AHCI) enabled.

Live CD boots into GUI from IDE CD-drive but further installation is not possible because no HDs are detected. I suspect this has something to do with lacking ICH8R support in kernel.

EDIT: Feisty daily build 31.3.2007 is now able to install itself with kernel 2.6.20-13 on my SATA drives. Big thanks to all active developers!

---

### Post by zeusx64 on 2007-03-04
PCI sound card
Voyera Turtle Beach
Montego II
Ubuntu 6.10 Edgy Eft 
Not recognized or functioning.

---

### Post by nwadams on 2007-03-07
amd xp 64 3000+
msi rs480 motherboard
geforce 7600 gs
1gb ram

no usb at all, not even power, they work fine in windows so i know its' a problem with linux, and i'm a complete newbie so i need help...thanks

---

### Post by mättu on 2007-03-16
laptop compaq evo n800v

dapper xubuntu

acpi: fan never turns off completely. It states "ok" but is in "active(1)".
(Workaround: make machine work until fan turn to "full noise speed" ;-), then kill the process, wait -> fan turns off)

palm-sync with gnome-pilot does not work reliably. In the forums it was reported to be a kernel-bug with some versions (can't remember exact details)

No 3d rendering. I believe the graphics card is not correctly detected. It should be an ati mobility 7500 (hardware-specs from compaq), ubuntu detects 8500. I think there is no accelerated driver for 7500?

backlight adjustment does not work as soon as x is started. (?!)

No dvd-playing on external monitor (black window)

minor issue: 
loudspeaker-keys are not recognized

All in all a very pleasant experience!

:m)

---

### Post by DAaaMan64 on 2007-03-27
Gateway M675

BCM4309 wifi card only works with ndiswrapper and windows driver.  

Sound malfunctions and can only be acquired via using the mic plugin instead.

As if the laptop isn't loud enough, it gets louder.

Battery gage and function(fn) buttons don't work at all other than the screen darken ing and lightening one.

---

### Post by HokkaidoHillbilly on 2007-04-15
** 1)Type Of Hardware: Built-in Webcam/Mic on Dell XPS M1210**[B]
2)Hardware Maker: Logitech[/B]
[B] 3)Hardware Model: Logitech Quick-Cam for Dell Notebooks
4)Known Issue: built-in mic refuses to function even after adding [/B]```
options snd-hda-intel model=ref
```** to /etc/modprobe.d/alsa-base.**

---

### Post by HokkaidoHillbilly on 2007-04-15
[B] 1)Type Of Hardware: Dell XPS M1210
2)Hardware Maker: Dell
3)Hardware Model: XPS M1210
4)Known Issues: 
[/B][INDENT][B]a) Computer does not automatically go into standby mode when lid is closed, i.e. fn+esc (Stand by) must be pressed first.  If computer is left in stand by mode more than 1 hour, will not wake from stand by and must be powered down and rebooted.

b) Screen brightness selection causes GDM restart.  When fn+up/down cursor is pressed, GDM immediately halts and restarts.
[/B][/INDENT]

---

### Post by farfoosh2007 on 2007-04-16
Dell Inspiron 6400
Wireless card not recognized

---

### Post by svennils on 2007-04-17
On the same laptop, under edgy, the loudspeaker-volume-keys are recognized. By the way, these are generating normal keyboard scan codes(never got around to set them up under slackware). Panel brightness and fan control dont work under edgy either. 

Sven. 

> **mättu said:**
> laptop compaq evo n800v

dapper xubuntu

acpi: fan never turns off completely. It states "ok" but is in "active(1)".
(Workaround: make machine work until fan turn to "full noise speed" ;-), then kill the process, wait -> fan turns off)

palm-sync with gnome-pilot does not work reliably. In the forums it was reported to be a kernel-bug with some versions (can't remember exact details)

No 3d rendering. I believe the graphics card is not correctly detected. It should be an ati mobility 7500 (hardware-specs from compaq), ubuntu detects 8500. I think there is no accelerated driver for 7500?

backlight adjustment does not work as soon as x is started. (?!)

No dvd-playing on external monitor (black window)

minor issue: 
loudspeaker-keys are not recognized

All in all a very pleasant experience!

:m)

---

### Post by mkincheloe on 2007-04-18
All IRTOUCHSYSTEMS' infrared touch screens.

[http://www.irtouchusa.com/download.htm](http://www.irtouchusa.com/download.htm)

Specifically model K15.

---

### Post by ElQuia on 2007-04-19
ASUS MOTHERBOARD M2N4-SLI

- MP-BIOS bug: 8254 timer not connected to IO-APIC.
- Kernel Panic - not syncing: IO-APIC + timer doesn´t work!. 
- HARDWARE ERROR. CPU0: Machine Check Exception. TSC 539c47cf42 ADDR 5bcf78. This is not a software problem. Kernel panic - not syncing: Machine Check
- Contact your hardware vendor.

---

### Post by pross on 2007-04-20
asus m2n4-sli
nvidia 7900gs x2 sli

boot from CD produces 'Kernel Panic - not syncing: IO-APIC + timer doesn´t work!'

adding noapic at bootime allows you to boot but no audio and no SATA.. nv driver is loaded but results in a black screen i had to ALT+F1 then edit xorg.conf and change the driver to vesa and restart X

after installing i added 'enable_8524_timer pci=biosirq' at bootime...now everything works :)

---

### Post by CrAzYoNi on 2007-04-20
MSI Megabook L740 laptop:

1)Type Of Hardware: Wireless card.
2)Hardware Maker: Ralink
3)Hardware Model: Unknown
4)Known Issue: I  can't find this card in the lspci output but i do find it in "Device manager"
* look at the screenshoot.
I can see my wireless network on the system via networkmanager applet but I can't connect to it, no matther what are the security options - even if none!!

p.s on windows it working. I never succeed to run it over ubuntu.

---

### Post by benoflinux on 2007-04-20
ATI HDTV Wonder

---

### Post by yarimahdi on 2007-04-22
labtop : vaio b100b02
soundcard : sound max untegrated digital audio
manufactureer : Analog Devices.Inc.


hint : ubuntu 7.04 shows that it finds the sound cart prpbably and i can increase/decrese volume but i no sound listen!

---

### Post by teutori on 2007-04-22
Joystick: Saitek X45. All axis work but buttons are messed up. Joystick worked in Edgy (kernel 2.6.17-11) but not in Feisty (kernel 2.6.20-15).

Tested with Kubuntu 7.04.

---

### Post by Neuralgia on 2007-04-22
ATI TV Wonder 650

lspci:  04:00.0 Multimedia controller: ATI Technologies Inc Unknown Device 4d50

Didn't work on Dapper, Edgy or Feisty.

TvTime displays: No video source, No signal, cpia2: Invalid argument, Cannot open device /dev/video0.

---

### Post by blamecanada on 2007-04-24
ATI Theater 550 Pro

No Linux Driver (that I could find)

---

### Post by the12cook on 2007-04-24
doesnt like my ati pci radeon9250 at all! wont boot from disc so cant install mandriva had no problem but ihave ubuntu on the laptop and prefer it. got the alternate instal for slow comps ( mine isnt) but unclear how to dual boot do i need to delete mandriva first? I want ubuntu where it is.

---

### Post by Scortech on 2007-04-24
Installing Ubuntu 7.04 works ok but when I restart computer and hit return on the first line of the ubuntu list my screen goes black and nothing more happens...

I have heard this is because ubuntu 7.04 have no support for my video card:-(
And I am also a first time user or should I say want to use ubuntu..

My system is:
Mainboard: A8N32-SLI Deluxe
CPU : AMD X2 4600+ 2.4Ghz
System Ram: 2GB Dual Kit
Graphics Card: 8800 GTX

I hope there will be out of the box support for 8800 GTX soon because I really
wanna test out ubuntu...

Thank you

---

### Post by alexjhill on 2007-04-25
I get a Driver warning about my 

Nvidia FX 5400 mobile card :(  

tho i have not had much trouble with it yet. i never had any issue sunder 6.10

---

### Post by Bjorkam Rodas on 2007-04-25
Hi

Completely new to Linux and (K)ubuntu.
On my laptop IBM T40, I have been able to run the LiveCD 7.04 - though it felt very slow.
But when installing, the boot would always hang before getting to the login screen using 7.04

I run 6.06 successfully, though the graphics feel slow.

---

### Post by RealG187 on 2007-04-25
Lexmark X3350.

I tired in Edgy

[http://ubuntuforums.org/showthread.php?t=390815&highlight=x3350](http://ubuntuforums.org/showthread.php?t=390815&highlight=x3350)
[http://ubuntuforums.org/showthread.php?t=390815&highlight=x3350](http://ubuntuforums.org/showthread.php?t=390815&highlight=x3350)

---

### Post by droko on 2007-04-29
PCI sound card
Voyera Turtle Beach
Santa Cruz
Ubuntu 7.04 Feisty Fawn
No Sound. 

- I try to unmuted all channel (including external amplifier).
- With "lspci -v", I can see my card listed.
- When I boot in Windows XP, the card work fine.

This soundcard was working in ubuntu 6.06. I didn't upgrade but make a fresh installation.

---

### Post by RichardM33 on 2007-05-02
The Diamond GL 1 AGP video card does not work. The 6.06 LTS Live CD will not boot with the card present. This is an older (circa 1999) video card so maybe not a issue for anyone else. (BTW, I plugged in another AGP video card and install completed -- no problems.)

Also, the Xsane Scanner support does not include the Nikon Coolscan V ED (aka 50 ED).

---

### Post by majuri1 on 2007-05-02
Logitech
DiNovo Bluetooth keyboard, MX1000 Bluetooth Mouse
USB Adpater

No response at all

ubuntu 7.04 Feisty Fawn

The system boots fine
Asus AR832-MVP Deluxe
AMD Athlon64 3700
Readeon X1800GTO

---

### Post by pintree3 on 2007-05-02
to the moderators of this thread. Please note, that by definition, this thread is not a list. I think it would be a great idea if an actual list were created at the very top (1st) of the thread so that a reader can in fact see the list of incompatible hardware discovered. This newly created and upated list should be alphabeticized and also, we the reader can assume, that the builders of ubuntu have in fact checked if the hardware given is in fact problematic. As it is now we have to go through page after page, both because there is no order and because it is not really a list but a place with different names of imcompatibilities.
Thank you for reading me.

---

### Post by xeocub on 2007-05-03
[B]1)DVD-R/W Drive
2)Sony
3)AW-Q170A-B2 BK
4) 
Not even recognized in Ubuntu (works fine in w2k). 
Just doesn't show up, can't mount or anything obviously

[/B]

---

### Post by roger_rf on 2007-05-05
1) Laptop
2) LG Electronics
3) LE50-5LTP1
4) Two issues in Kubuntu Feisty Fawn:
- Sound does not work;
- At any moment, USB mouse or internal ethernet network card may stop working. If this happens, the system won't be able to shutdown properly, and the only way to turn it off is by pressing and holding the power button for a few seconds.

Technical details:
[http://br.lge.com/md/product/prodcategorylist.do?actType=detail&currPage=1&categoryId=1000000088&parentCategoryId=0000000403&categoryLevel=4&productId=1100000433](http://br.lge.com/md/product/prodcategorylist.do?actType=detail&currPage=1&categoryId=1000000088&parentCategoryId=0000000403&categoryLevel=4&productId=1100000433)

---

### Post by erealz on 2007-05-06
1)webcam
2)microsoft
3)vx 1000
4very very dark quality pic in ekiga?...cant see unless the sun was like next to me or somthing:lolflag:

---

### Post by Toet on 2007-05-06
> **Scortech said:**
> Installing Ubuntu 7.04 works ok but when I restart computer and hit return on the first line of the ubuntu list my screen goes black and nothing more happens...

I have heard this is because ubuntu 7.04 have no support for my video card:-(
And I am also a first time user or should I say want to use ubuntu..

My system is:
Mainboard: A8N32-SLI Deluxe
CPU : AMD X2 4600+ 2.4Ghz
System Ram: 2GB Dual Kit
Graphics Card: 8800 GTX

I hope there will be out of the box support for 8800 GTX soon because I really
wanna test out ubuntu...

Thank you

Same here with a 8500 GT. There is a workaround, installing the beta drivers from NVIDIA site and then starting in recovery mode. Changing driver in xorg.conf to nv, startx and the exit it again, change xorg.conf back to nvidia and start gdm.

But I'll wait until it hits the repos and use my onboard till then.

---

### Post by rkarren on 2007-05-06
1) Wifi card
2) Intersil
3) Prisim 2.5 wavelan chipset
4) edgy or fiesty ubuntu not recognizing card. worked for the first 2 weeks of having edgy, then stopped. never worked for fiesty.

---

### Post by zero-Q on 2007-05-07
ich8 intel raid controller for raid0(dmraid doesnt work and after livecd boot, raid hdd apear as offline in bios raid screen at next boot)

---

### Post by cjae on 2007-05-07
Plextor 716A DVD+-R/WFirmware 1.10 Apr.9/07 (Windows Install) 

uname -r
2.6.20-15-generic


xubuntu 7.04 


[https://bugs.launchpad.net/bugs/27316](https://bugs.launchpad.net/bugs/27316)

Please forgive me if this is not right.

---

### Post by thommango on 2007-05-14
Dell SX260 - Virtual video memory seems to be a problem.  There's a lot of fixes for similar problems, but none seem to work for this box (in my experience).

---

### Post by zeus_ex_machina on 2007-05-17
ASRock 775 VM800 Motherboard

Under Ubuntu Feisty cannot recognize onboard video card. No drivers found online. Otherwise works pretty good.

---

### Post by earobinson on 2007-05-17
Wow thats a really good idea!

---

### Post by suchawato on 2007-05-17
Sony Vaio PCG-954A
Pentium III 695.6 MHz
254 M Ram
Chipset: Intel i815

Ubuntu 6 and 7 will not install at all.
forced installations result in a Snowcrash.
Will not boot beyond "loading standard PCI Resources" 
Install program will not load at all in normal mode.
*Forced Installation means: typing, "quiet splash noapi=off irqpoll" in the 'Alternate' CD menu Command line.(which results in a snowcrash on initial boot)
Identical problems with Zenwalk.
And very similar with openSUSE.

Live CD will not install at all.
Editing the boot kernel with the above command line does not work.
Adjusting the Bios settings does not work.

---

### Post by Daniele86 on 2007-05-23
Hello Everything,

I have a Fujitsu Siemens Amilo M1451G laptop with an Intel Realtek ALC880 soundcard. I have installed Ubuntu Feisty 7.04 with 2.6.20 kernel but suond doesn't work.I have an X on volume control  and if I click on i have this errore message:
No G-Stream plugin or dispositive of volume regolation.
Can I have your help?

---

### Post by luctor on 2007-05-24
-

---

### Post by regomodo on 2007-05-25
> **RichardM33 said:**
> 
Also, the Xsane Scanner support does not include the Nikon Coolscan V ED (aka 50 ED).

That's not true. Mine worked with no configuration. However, it won't work with the IR light for detecting dust. It just spits errors out

Epson 4180 scanner doesn't work though.

> **Daniele86 said:**
> Hello Everything,

I have a Fujitsu Siemens Amilo M1451G laptop with an Intel Realtek ALC880 soundcard. I have installed Ubuntu Feisty 7.04 with 2.6.20 kernel but suond doesn't work.I have an X on volume control  and if I click on i have this errore message:
No G-Stream plugin or dispositive of volume regolation.
Can I have your help?

This isn't the correct place for help i believe. It's a list. Make a new post

---

### Post by mastaphoo on 2007-05-26
EVGA GeForce 8800 640MB GFX card seems to be incompatible. Installed at first, but i tried to install the nVidia drivers (i think) and now i get "Failed to start X server"

---

### Post by lutosdemayo on 2007-05-28
Card reader on my HP nx6120 laptop doesn't seem to work. It somehow tries to read because it is lighting up but nothing ever shows up.

---

### Post by PintOfBitter on 2007-05-30
IBM Aptiva 245 (Mfg 1999) PS2 mouse is inop in 7.04.  6.06 works.

---

### Post by fsando on 2007-06-01
Hardware: asus notebook M2000N (anno 2004), centrino 'core solo' 1.3 ghz 500mb ram 40 gb hd. (bios: v0208 date: 03/08/04)

Tried the following CDs:

xubuntu 7.04 desktop, xubuntu 7.04 alternate:
The boot screen shows as expected. After starting the install (both standard install and safe graphics mode) it appears to initiate the install process (some green text and some dots at top edge of the screen) then screens turns black with a blinking dash in top left corner and nothing happens.

ubnutu 7.04 desktop:
The boot screen shows as expected. After starting the install (both standard install and safe graphics mode) it appears to initiate the install process (as above) then (with the menu still visible) it stops reporting in green text at top of screen "invalid or corrupt kernel image". When selecting one of the menus it reports "Could not find kernel image".

ubuntu 7.04 alternate
The boot screen shows as expected. After starting the installation the screen blinks a few times and it reboots (returning to the boot screen).

Installed Xubuntu 6.10 without a hitch, then upgraded to xubuntu 7.04 with kernel 2.6.20-16, which resulted in the laptop constantly rebooting (without any user interaction).

So the conclusion is that this laptop does not work with feisty!

---

### Post by sirius11 on 2007-06-09
use to be able to install ubuntu with the 7900gt video card,  upgraded for the 8800 gts  , can't install ubuntu anymore.  Blank screen .

---

### Post by JupiterMike on 2007-06-11
Using Fiesty Fawn and Dell printer model 725.  Can't detect printer or driver.

---

### Post by azdragon on 2007-06-11
I can not get my Epson Stylus C59 printer to work correctly.    I am using the driver for the C50 printer, it works perfect for black but other colors are offset and simply do not display correctly.   This is a VERY popular printer in most of the third world, millions have been sold, the same target market as Ubuntu, so it would be very important to get this driver working for everyone,    I think that only slight modifications from the C50 driver would be needed to get this working.   I tried at it for 2 hours but I have no clue what I am doing so it did not get better.

Please someone fix this.

---

### Post by matheuu on 2007-06-14
TOSHIBA A200 SATELLITE 2007
INTEL HDA SOUND CARD - detected but not working!!
SUCKS BIG TIME!

---

### Post by Tom Mann on 2007-06-14
720k Floppies! I can't port my Amiga ADF files to PC using 720k Cross-DOS formatted disks :(

---

### Post by nithrandil on 2007-06-16
MemoryStick Drive Reader, doesnt work in my laptop, Sony Vaio A130B its ligth is permanently on.. and when I introduce a Memory stick it doesnt mount, nor anything; when i review I think it is reconiced as MMC/SD Host Adapter... but my laptop doesnt have that.

---

### Post by hotani on 2007-06-23
**1)Type Of Hardware:** Laptop
**2)Hardware Maker:** Dell
**3)Hardware Model:** Latitude D531
**4)Known Issues:**
a- ATI video card, no video. Possible to get it going by installing fglrx-driver at command line after install
b- ATI sound card, no sound. No fix yet.
c- suspend does not work. Cannot bring computer back after suspend, have to hard boot.
d- hybernate hangs machine with a blank screen and flashing cursor in top left corner. Hard boot required.
e- compositing will not work with fglrx driver

(As a general rule of thumb, avoid this and any hardware that has any ATI components!)

---

### Post by dannyv on 2007-06-24
1)Audio/sound card

2&3)HDA Digital X-Mystique 7.1 Gold

4)Sound freezes after a while on Firefox and all system sounds. Have to wait more than an hour to reboot to make it work. And repeats after a while again.

---

### Post by totti10it on 2007-06-24
1)Type Of Hardware : SATELLITE CARD  ( pci card)
2)Hardware Maker    :TWINHAN vision plus ( red color with normal -old- tuner ) 
3)Hardware Model     : 1020 A
4)Known Issue           :  when the cars is connected no linux distro. can boot i tried several distros livecd's     and normal  but none of them  could ever boot .each distro is stopped at a step of detection of hardware.when i removed the card all distros could boot normally live cd's worked well and normal distros's i could install  well ..so pls wht is the solution.. i'm windows user and i want to swich to linux but i'm still beginner and  i can't do without my sat. card and it's impossible each time i need to use linux i 'll remove the card from pci slot

thanx everybody and waiting 4 ur help

---

### Post by gdp77 on 2007-06-29
1)Type Of Hardware : **Motherboard**
2)Hardware Maker : **Gigabyte**
3)Hardware Model : **P35-DS3**
4)Known Issue : **Ubuntu 7.04 (64 bit) installs, but network doesn't work**

---

### Post by SRParda on 2007-07-02
1)Type Of Hardware : Integrated network card.
2)Hardware Maker : Intel
3)Hardware Model : **[COLOR="Blue"]Intel® 82566DC Gigabit Ethernet Controller[/COLOR]** integrated into **DP35DP**
4)Known Issue : Ubuntu 7.04 (64 bit) installs, but network card is not installed

---

### Post by 3enith on 2007-07-08
ASUS
P5WD2 premium mainboard
with realtek azalia 882 sound

---

### Post by davidsrsb on 2007-07-09
ASUS
M2N-E SLI mainboard
C-Media 6501 usb sound is not supported by alsa 1.0.13 and the Ubuntu kernel

---

### Post by newbie2 on 2007-07-11
using feisty...
is it possible to add my keyboard to the 'Keyboard Preferences > Layouts > Keyboard model - list ?

it's this model --> Gateway 2000 Programmable Anykey Keyboard PS/2
[IMG]http://i10.ebayimg.com/05/i/000/a9/45/ad23_1.JPG[/IMG]
[http://cgi.ebay.com/Gateway-2000-Programmable-Anykey-Keyboard-PS-2-Vintage_W0QQitemZ280132435381QQcmdZViewItem](http://cgi.ebay.com/Gateway-2000-Programmable-Anykey-Keyboard-PS-2-Vintage_W0QQitemZ280132435381QQcmdZViewItem)
:mrgreen:

---

### Post by Pucpuc on 2007-07-13
I can install it as VESA, but i still cant get it working correctly
enabling desktop effects or sometimes ServerX

1)Ubuntu 7.04
2)Graphic Card
3)Winfast
4)PX 7600GT 256 mb

---

### Post by Namzy on 2007-07-13
-Laptop
-Acer
-TravelMate 2428AWXCi
-Ubuntu 7.04 will not install or even load from CD. Gets past the ubuntu loading page and brings up the fawn coloured background and then comes up with an error starting gnome desktop (sorry it's not precise, I don't really feel like trying it again right now, maybe when I have free time I'll get you the exact error message)

---

### Post by online14230 on 2007-07-17
Lexmark X1180 - driver available is for Z605, which onlygets the printer working. Sane not detecting scanner.

---

### Post by big9er5 on 2007-07-17
this is what im getting its a problem with my cpu of which is an amd athlon 2400, a little old hat but planning to upgrade soon

*starting powernowd...
/ect/rc2.d/s20powernowd: 156: cannot create /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor :directory does not exist
                                                                             * cpu scaling not supported



any help here would be great as  i am a complete linux vergin....
thanks

---

### Post by big9er5 on 2007-07-17
forgot to add does other thing after that happens
then
214.779632] bug: soft lock up dected on cpu#0!

---

### Post by tower_ on 2007-07-18
Laptop:

HP Compaq 6710b

unable to install feisty 7.04 from live-cd 
/bin/sh: can't access tty; job control turned off
(initramfs)

no support from vendor

---

### Post by igorgue on 2007-07-18
Laptop:

HP Pavilion dv2550se Verve(just in BestBuy)

unable to install feisty 7.04 from live-cd
/bin/sh: can't access tty; job control turned off
(initramfs)

no support from vendor

It sent you to a busybox shell

---

### Post by kornelix on 2007-07-23
The Intel D975XBX2 motherboard has a new chip for the sensor bus that is not supported by lm-sensors. Therefore you cannot get CPU temperature or any other sensor information.

The prior Intel product, the D975XBX, works fine with lm-sensors.

---

### Post by frdr09 on 2007-07-24
AMD Athlon 64 X2 3800 Brisbane
Epox MF570 SLI
2x512 MB RAM DDR2 533
80 GB SATA Seagate Barracuda

I cannot install ubuntu feisty fawn these words came out from the screen

[37.623837].. MP-BIOS Bug: 8254 Timer not connected to I/O-APIC
[37.802644]  Kernel Panic-not Syncing: to APIC + Timer Does'nt work 
Boot with APIC = debug and send a report.  Then try booting with the noapic option
[37.802693]


Could someone help me please.  I really want to install Ubuntu Feisty

---

### Post by mrcanard on 2007-07-24
Abit AN9 32X nVidia 590
AMD64 2x 5200+
MSI NX7300GT PCI-E / SLI
512x4 DDR2 667
SATA LiteOn DVD
SATA HDD

It´s my fault I should have read the available documentation better.
But I really thought Ubuntu would install on anything.

---

### Post by bdk9246 on 2007-07-25
(nvidia GeForce 8 series) 
WinFAST PX8600 GTS 256mb, 
Ubuntu 7.04

Not found.

---

### Post by CalvinK on 2007-07-25
Toshiba Satellite A200 (laptop).

[LIST]
[*]Bios bug. Hibernation doesn't work.
[*]Problem with ACPI (no solution found presently: DSCT reconf not available)
[*]Chicony webcam not recognized and no available driver. Unusable presently but I found a message in the french wiki which said that Ekiga (videoconf) works well on it and it did !!. This software has the correct driver.There must be a solution but I dont know it.
[*]No sound with Feisty Fawn (works with Edgy Eft). Intel Sound card not recognized. Works with a little line in /etc/modprobe.d/alsa-base : 
*options snd-hda-intel model=3stack-660*. 
One can replace 3stack-660 by 3stack.
. cf [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto). However no shut down of the speakers when you plug the headphones. The headphone is not recognized (cf alsamixer)
[/LIST]

Bon courage. :confused:

---

### Post by october3rd on 2007-07-28
I use Ubuntu 7.04.
On the first 2 days everything is working okay and neat in 1028 x 768 px resolution.
Today, on startup the screen appeared in 640 x 480.
I went to the System > Preferences > Desktop Resolution, clicked on the drop down menu. 
But there's no other option there but 640 x 480.
What do you think might go wrong?
I use dual OS. WinXP (genuine) and Ubuntu 7.04 (from Canonical).
I don't use any third party VGA card, just one on board with the Intel chipset.

My computer specs:
IBM Thinkcenter E54.
Intel Pentium 4 3.4GHz.
Intel Chipset (Intel Graphic Accelerator -onboard)
512MB RAM. (1GB RAM soon).

Please respond a.s.a.p..
Thanks in advance..

---

### Post by bmartin on 2007-07-28
Acer Aspire 5050-3785 on Feisty Fawn

ACPI .dat file is buggy; ACPI doesn't work properly; battery meter in Metacity indicates that computer is always running on AC.

Sound card (shows up as HDA ATI SB) not detected; solved by adding file /etc/modprobe.d/sound with the following contents (requires reboot):
```
alias snd-card-0 snd-hda-intel
options snd-hda-intel index=0 probe_mask=3 position_fix=3
```

ENE Technology Inc ENE PCI Memory Stick Card Reader Controller: This doesn't work and I don't know how to fix it. It seems like it might be bound to /dev/hda; however, even when a card is inserted, the **sudo mount** command indicates that no mountable media is present.

WiFi chipset (shows up as Atheros Unknown device 001c (rev 01) -- shows up as a 5007EG in Windows) not detected; solved by adding **blacklist ath_pci** to **/etc/modprobe.d/blacklist** (requires restart) and compiling new ndiswrapper (1.47) for use with appropriate Win XP drivers (net5211.inf, ar5211.sys). The card is unsupported by the ath_pci module set.

---

### Post by punya on 2007-08-01
Compaq Presario 2100US
Linksys WPC11 v3 PCMCIA card
Xubuntu Feisty Fawn 7.04 release

Installation from Alternate CD hangs if the card is in. If I take the card out, installation succeeds and the OS starts up as expected, but then hangs the moment I put the card in again.

Note: the Ubuntu wiki lists this card as supported. It also works on Windows XP professional on the same computer.

---

### Post by zenit123 on 2007-08-01
Maybe not the right place to post but my Canon Multifunctional printer MF4150 does not work or no drivers available.

cheers

---

### Post by simlu on 2007-08-03
SoundCard: HDA Intel
Chipset: SigmaTel STAC9200
Issues: Input and Mic don't work (No sound)

[IMG]http://img.photobucket.com/albums/v190/siml0808/snapshot1.jpg[/IMG]

---

### Post by tashmooclam on 2007-08-04
Dell Vostro 1500. 
Not compatible with ubuntu 7.04 PC. Not compatible with ubuntu 7.04 64 bit version. 
This is likely related to the hard drive as far as I can gather.

---

### Post by rong889 on 2007-08-05
Ibm T42 With ATI Random 9600

---

### Post by Aslan64 on 2007-08-10
**Acer Aspire 5580**

1) the built in Cam doesn't work 
2) the  resolution doesn't support the wide screen in the laptop ( 1280*800)
    even when i installed my nVidia 7300 driver.
3) there was a lil problem with the speakers in the beginning  ( the sound card was fine )
   the solution was to turn the surround sys on .
4) the touch pad works ( but no up-down , left-right arrow )


Ubuntu 7.04

---

### Post by guy.murray on 2007-08-10
Just got a brand new Dell inspiron 1720. Won't even run Ubuntu as a live CD, just drops you into busybox after telling me it can't access tty; job control turned off.

Curiously, this machine is of very similar spec to one they sell in the USA with Ubuntu preinstalled which is why I chose it!

Guy

---

### Post by midgetporn on 2007-08-11
Laptop
Acer 
Aspire 5100-3959
- Built-in microphone doesn't work
- Card reader doesn't work


> **HokkaidoHillbilly said:**
> 
[INDENT][B]a) Computer does not automatically go into standby mode when lid is closed, i.e. fn+esc (Stand by) must be pressed first.  If computer is left in stand by mode more than 1 hour, will not wake from stand by and must be powered down and rebooted.

[/B][/INDENT]

Unfortunately, I have the same problem :[

---

### Post by LudovicusRex on 2007-08-12
Salut Frodon, 

Je vois que tu es français et de Nantes en plus (j'ai fait une partie de mes études à Nantes, ville très agréable au demeurant!), cela tombe bien, cela va me faciliter la tâche... je suis un français expatrié aux USA et je viens d'acheter un tout nouveau laptop DELL. 
 Je n'arrive pas à installer Ubuntu feitsy 7.04 même avec les explications que j'ai pu trouver sur le forum. 

 Voici la configuration de mon DELL VOSTRO 1500:
Intel Core duo T5470 1.6GHh 800 Mhz FSB 2M L2 cache 7ZWPDF1
128MB NVIDIA GeForce 8400M GS
160G 5400 RPM SATA Hard Drive
Integrated 10/100 Network Cardand Modem
Integrated High Definition Audio 2.0
Intel 3945 WLAN (802.11a/g) Mini Card
Integrated 2.0 mega pixel webcam 1500

 P.S Sais tu si la prochaine version de Ubuntu sera capable de tourner sur ce type de PC. J'aimerai vraiment installer Ubuntu qui marchait très bien sur mon ancien PC. MERCI

---

### Post by bibas on 2007-08-17
Graphics card
ATI
Raedon xpress 200
Fiesty

---

### Post by lagitup on 2007-08-19
I just installed ubuntu and my x-fi is not recognizing.  I switched my speakers to the soundMAX output and it works (but compared to the x-fi soundMAX is just ugly >.<)

athlon 5200
asus m2n-sli deluxe nforce 570sli w/soundMAX intergrated sound
evga 8800gts640
creative x-fi xtremegamer
fiesty

---

### Post by s3a on 2007-08-21
I've tried using the following hardware on _Ubuntu 6.06 LTS and 7.04_ to no avail:

-Amigo AMI-CA52/CW52+ P9006-02 (chipset is Conexant HSFi CX11252-11)

-Conexant Modem [PT-FM3623 ESS 2838 Chipset V.92 56K Internal PCI Modem]:
Modem Card Model No.: FM-3623-1
Modem Chipset: ESS 2838

---

### Post by Jooky1138 on 2007-08-21
I am running ubuntu 7.04

1) Bluetooth USB adapter
2) Rocketfish
3) Model number RF-BTDGLE
4) Not recongized by HCI tools.  No linux drivers or support avaible from Rocketfish

---

### Post by Ken Milburn on 2007-08-21
Following a soundcard replacement. - no sound with 7.04 - OK with winXP

Soundcard is Sound Blaster X-Fi Xtreme Audio  (fairly new model)
Ubuntu reports it as Sound Blaster Audigy LS

Creative Labs says no Linux driver available.

---

### Post by a9909 on 2007-08-23
Motherboard: MSI P35 Neo
CPU: Intel Core 2 Quad 2.4ghz
RAM: Kingston DDR2 PC6400
Video: NX8400G8-TD256E PCI-e (unsure of the exact name, but it's also made by MSI)

When attempting to run the graphical installer, I get:

/bin/sh: can't access tty; job control turned off
(initramfs) 

And then it drops to a BusyBox shell. Two other people in this thread have had this same problem, albeit with laptops. Any ideas on how to fix it?

EDIT:
I've isolated what was causing my problem, and serenityUK on the Freenode Ubuntu channel provided me with a work-around. By looking at /casper.log I was able to determine that the installer simply couldn't see the Live FileSystem on the CD, because the IDE-based CD/DVD drive wasn't detected by the OS, even though the SATA hard drive was. serenityUK told me about the boot option "generic.all_generic_ide=1", which I applied to the "Safe Graphics" boot option to get things rolling.

---

### Post by CalvinK on 2007-08-24
laptopToshiba A200/1DR : CD/DVD not compatible with last kernel 2.6.22.9 generic. Inpredictable behavior when reading and writing CD/DVD

---

### Post by carlo bolzonello on 2007-08-28
hi all,

HP Compaq nc8430
ATI Mobility Radeon x1600 graphics card

Problem relates to Graphics chipset, you get a X-Server error during install

---

### Post by iliketoprogram on 2007-08-31
tribe 5 + dell inspiron e1505

using the install (liveboot) cd (don't have it actually installed yet)

some issue with resolutions;  kdm won't start until I modify xorg.conf, adding resolution "1680x1050";  i can also copy my feisty xorg.conf (changing driver from fglrx to vesa), and this will allow kdm to start (my feisty xorg.conf has the high res screens too)

it will then start, but X does not seem to recognize my touchpad.  It works fine in feisty, but i can't get a mouse to work in gusty unless I actually attach a ps2 mouse.. 

i can reproduce this, so I can get whatever data would be helpful :)  currently running feisty for desktop on the same machine

---

### Post by CyberCod on 2007-09-01
USB irda dongle
MosChip Semiconductor
ID 9710:7780 MosChip Semiconductor
does not make /dev entry in Feisty

Full details [here]("http://ubuntuforums.org/showthread.php?t=540563")

---

### Post by B0rsuk on 2007-09-02
Motherboard **Asus P5K SE** Intel P35 chipset
Seagate 250 GB Barracuda 7200 16MB SataII
DVD-+R/RW LG GSA-H54LBB LightScribe 
..

I tried installing Kubuntu 7.04 Feisty on it. The install stops with a message about some kind of input/output error and fd0 . Disabling floppy in BIOS fixed this one.
Then it gets stuck in the BusyBox with a message:
/bin/sh: can't access tty; job control turned off
(initramfs)

The problem is most likely the Asus motherboard. Do me a favor and don't buy from Asus.

---

### Post by WIREHEAD on 2007-09-02
HighPoint RocketRaid 1520 PCI  SATA card .

Kernal panick !
( Dapper , Feisty , Gutsy , Knoppix , GeexBox , all no boot )

Works in W*****Ws XP

Overclocked Athlon in Shuttle Spacewalker MOBO.

---

### Post by pdlethbridge on 2007-09-02
my usb canon n1220u scanner does not run in feisty, it did in dapper

---

### Post by rwmcgwier on 2007-09-03
Deleted content.

---

### Post by karvec on 2007-09-04
Ummm...  On an ACER 5630-6288 laptop, Orbicam, the built-in webcam is the only thing I can't seem to get to work.  PM me if you're running the same thing and have accomplished it, I'd love to know.

ALSO!!  An old AMD K-6 333 MHz proc w/ 256 megs of RAM and unsure of motherboard, but had to do with acpi settings...

---

### Post by {A}Poly on 2007-09-04
I get the 

/bin/sh: can't acess tty: job control turned off

I get that....


160GB 7200RPM Seagate sATA Hard drive
LG R+W DVD/CD drive
Intel Core 2 duo E4400 with fan (2GHz i think)
MSI G33M motherboard (supports intel core 2 duo and core 2 quad)
built in graphics card & surround sound
1GB 800MHz DDR2 Kingston RAM Desktop Memory

theres the details

PLEASE HELP

---

### Post by glupee on 2007-09-06
Leadtek Winfast PVR3000
Chipset Conexant CX23416 + NEC D64015AGM   Hardware Interface 32-bit PCI 2.3 bus mastering compatibility

This card appears in the device manager, but doesn't work with any software, NONE.
Probably needs drivers.. probably will sell it and get a new one, but would be nice if it was solved.

EDIT: Added spacing for neetness :D

---

### Post by tizzlebaco93 on 2007-09-06
Does anyone know about this mobo?
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2945301&Sku=MBM-MSNV-3800](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2945301&Sku=MBM-MSNV-3800)
I have 1 gb of ram that is ddr so i'm good on ram.
Does anyone know if you have to have a hd to use live cd?[http://ubuntuforums.org/images/icons/icon5.gif](http://ubuntuforums.org/images/icons/icon5.gif)
Question

---

### Post by karvec on 2007-09-06
tizzlebaco93:  no, you do not need a hard drive to use the live cd.  that's one of the benefits of live cds...  however, you won't be able to install it, and any changes you make will not be saved.  this will always be the case until you install it onto a physical hard drive.

---

### Post by Jubalgunn on 2007-09-08
DELL XPS210

I cannot install any version of Ubuntu

Report ata2 errors and install fails.

---

### Post by lswest on 2007-09-08
Graphics Card
Nvidia Geforce Go 7150 with dedicated memory of 64MB and shared up to 559MB
in an HP DV6545EG  (xserver crashes when the liveCD starts, crashes after install with alternate CD too)

also, Broadcom wireless card in the same laptop isnt recognized correctly, but can probably be corrected with ndiswrapper

---

### Post by gladstone on 2007-09-17
1) Soundcard (PCMCIA)
2) EMU
3) 1616m
4) If the card is left in at powerup, Ubuntu doesn't boot. If it's inserted after Ubuntu has booted (and at desktop), Ubuntu freezes completely

---

### Post by josephpmh on 2007-09-17
1)Type Of Hardware : All-in-one Printer
2)Hardware Maker : Kodak
3)Hardware Model : 5500
4)Known Issue : no driver

---

### Post by tomers on 2007-09-22
This monitot is an 1280x1024 monitor, and is detected as 1024x768 monitor, with no possible option to set is to 1280x1024.
I had to change monitor type to LCD 1280x1024 and restart X-Server in order to make it work.

I would like to add it to the list of monitors available under the manufacturers list - please let me know how I can do it myself, so I can add additional monitors to the list.

Is there a limit on the number of models the list can contain? I mean, submitting any posible monitor model available will make the list hugh...

Anyway, the specification for the LG L1900R LCD monitor available here:
[http://www.lge.com/products/model/detail/l1900r.jhtml](http://www.lge.com/products/model/detail/l1900r.jhtml)

Thanks,
Tomer

---

### Post by PumpAction on 2007-09-27
1) Motherboard
2) Asus
3) M2N32-SLI WS PRO
4) No driver support for the onboard Marvell SATA (88SE6145) Controller. None of my three disks connected to that controller is detected. Controller must be disabled in bios for ANY OS to be installed from a CD/DVD. Feisty can be installed from usb-stick with controller turned on.

---

### Post by abhishekjaiswal on 2007-09-28
> **lswest said:**
> Graphics Card
Nvidia Geforce Go 7150 with dedicated memory of 64MB and shared up to 559MB
in an HP DV6545EG  (xserver crashes when the liveCD starts, crashes after install with alternate CD too)

also, Broadcom wireless card in the same laptop isnt recognized correctly, but can probably be corrected with ndiswrapper


Hi 

I am having HP Pavilion dv6545eg  and facing some problems
Please contact me at [email]abhishek.a.jaiswal@gmail.com[/email]

Thanlks
Abhishke

---

### Post by arif_moin on 2007-10-04
)Type Of Hardware
-USB bluetooth hub. 

2)Hardware Maker
-Billionton

3)Hardware Model
-FCC ID: NLF-UBTCR3C2S

4)Known Issue

Ubuntu won't detect hardware.

---

### Post by nabeelfa on 2007-10-04
-Toshiba Satellite M100-180 
-Display card is not working:
ATI Mobility Radeon X1400 
-Dial up Modem not working

---

### Post by night_eulen on 2007-10-04
Graphic Card ATI Radeon HD 2600 Pro (Mobility???) on ACER Travelmate 5720G-602G35
Trouble finding the screen with FGLRX driver or ATI propietary

---

### Post by integralcv on 2007-10-05
VAIO VGN-TZ11MN_N 

After instalation, doesn't work wireles and suspend system. After actualization functions are resolved.

Doesn't work:
WEBCAM motion eye Driver windows xp sony visual comunication vgn-vcc7 
SD read media
MemoryStick of Sony

All rest it perfect.

I read that SD and MemoryStick are resolved in Ubuntu 7.10 in ten days.

---

### Post by ed-koala on 2007-10-10
Printer

Lexmark

Z730

Paper feeds slowly thru the printer, and nothing is printed.  Page stops halfway thru feeding.  Needs driver for this printer.

---

### Post by DM was on fire! on 2007-10-11
**Type Of Hardware**: Graphics/video card
**Hardware Maker**: ATI Radeon
**Hardware Model**: 7000
**Known Issue**: Causes computer lock downs and application crashes. Fix is most likely to manually install ATI drivers.

---

### Post by funky_D on 2007-10-15
1)Laptop
2)Asus
3)X50V
4)Booting Inconsistency (sometimes it boots, but mostly (98%) it doesn't, some ACPI Errors, freezing while working in console and booting)

---

### Post by talsemgeest on 2007-10-19
Graphics Card
Ati Radeon x1250 Inbuilt
No compatible driver for acceleration with gutsy

---

### Post by willemijns on 2007-10-19
ubuntu 7.10 gusty
ATI RADEON XPRESS 200 series,
no probleme with 7.04 / i'm trying to detect a low graphic mode which works well ;)

---

### Post by xanmoo on 2007-10-19
GPU; touchpad;wifi

Acer 1362LMI laptop

VIA unichrome K8M800; 
synaptics touchpad;  
INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)

3D applications using textures freeze the computer;
cursor driven by touchpad becomes blocked every 1 or 2 minutes (hit any key to deblock);
wifi not out of the box

---

### Post by sbennettgso on 2007-10-20
[UPDATED]

This appears to be an issue with the r8180 driver.  Using ndiswrapper and the W98 drivers for the RTL8180 chipset from RealTek, this seems to work fine.

------------------------------------------------------------------------------------------------------------------------------------

IBM Thinkpad A22p
Linksys WPC11 v4

I'm installing Xubuntu this time around.  When the card associates with the wireless network, the computer hangs.  I notice the scroll lock indicator and the caps lock indicator begin flashing when this happens.  I have to restart the computer.

This card worked fine under Feisty.

---

### Post by dr_cerebro on 2007-10-22
Acer Aspire 5050-4872

Ubuntu hates this machine...

Madwifi drivers do not work in this machine... but you can enable wireless with ndiswrapper, installing acer_acpi first.

Battery just is not recognized... and there is no way to make it be recognized.

---

### Post by wcm on 2007-10-22
Version : Ubuntu 7.10
Sound card : Audiotrak Prodigy HD2
Manufacturer : [http://www.audiotrak.net/products/prodigyhd2/](http://www.audiotrak.net/products/prodigyhd2/)
Found this from google, not sure if it will help.

[http://www.mailinglistarchive.com/freebsd-multimedia@freebsd.org/msg01107.html](http://www.mailinglistarchive.com/freebsd-multimedia@freebsd.org/msg01107.html)

---

### Post by enstardavid on 2007-10-22
Hi,

USB Camera on desktop

intel pc camera pro

Was working fine in Feisty - upgraded to GG Ubuntu 7.1 and Ekiga now reports:

"Your driver doesn't seem to support any of the color formats supported by Ekiga.
 Please check your kernel driver documentation in order to determine which Palette is supported"

Best wishes,

David

---

### Post by suchawato on 2007-10-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/154773](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/154773) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Its a PCG-954A
Pentium 3 processor. 695.6 MHz
254 megs of ram
chipset: intel i815

7.10 installed using acpi=off in the safe grafics installation.
The live session loaded, but not withthe correct screen size.
It made a little "box" in the center of the display that was the "screen" while the rest of it was black.
it still displayed, though it did not resize the install windows, and hid the buttons on the bottom of the install menus so that I had to use keyboard navigation blindly in order to install it.
Upon reboot, the display was black, exactly like the 7.04 problem.
Using the grub menu to boot in safe settings, I could see the initial loading text, and then:
black! in flickered once or twice before this and then Black.

There is a bug reported on this matter.
-Stu

---

### Post by Nilks on 2007-10-29
Wireless
Atheros
AR5008X (AR5416/5133)

I have tried with ndiswrapper and a lot of different drivers. I have tried with wifi-radar and wicd. I tried madwifi. All with no working result.

---

### Post by chrislind2 on 2007-10-29
Compaq EVO n600c
Pentium III 1.2mhz  1 gig of memory
Ubuntu 7.10
Netgear WG511 v2 wireless card, will not function

---

### Post by marcello100 on 2007-10-30
Sound card
Realtek alc 268
Sound card recognised on 6.10,but not working:no sound. Installed the newest drivers from realtek's website and alsa didn't find sound card.

---

### Post by couzin2000 on 2007-11-01
Creative X-Fi Elite Pro (no drivers, I checked)
Nvidia-powered Gigabyte 7300 GR graphics card, with VGA (works), DVI (works), and TV-out (cannot get it to work properly -- need VGA clone output)

Everything else works for me!

---

### Post by Exegete on 2007-11-01
C Media PCI sound card - CMI8738-MC6- works only sporadically - seems to be in conflict with VIA 8237 chipset, which Gutsy seems to prefer over the sound card.

---

### Post by pmoseley on 2007-11-02
Dell Inspiron 8600 with gusty.

Error just before bootscreen is supposed to appear. Workaround: install feisty then upgrade rather than doing a fresh gusty install.

---

### Post by mojtaba on 2007-11-03
HI,

I just Migrated from open SuSE  to Ubuntu it is really amazing  this is my Notebook specification:


HP PAVILION DV 6599EE ( 6500 ) 

- Intel Core 2 Due 2.00 GHZ.       
- nVidia GeForce 8400 GS  256 RAM.
- intel hda Realteck
- WIRELESS INTEL pro 3945 abg
- 2 GB OF RAM.
- HDD 160 GB.
- Blue tooth.
- Authen tech Finger Print.
- DVD RW LS.
- HP Web Cam.
- HDMI Interface.


I didn't test the Hp web cam & Finger print  yet but all:

Sound 
DISPLAY
BLUETOOTH
Wireless Net work card..


Working fine ...

---

### Post by zyg0t3 on 2007-11-03
Acer Aspire 5100-5674 
Ubuntu 7.10 32 bit

AMD athlon 64x2 1.7, 1 GB DDR2, 15.4 WXGA, Broadcom 802.11b/g WIFI, ATI Radeon Xpress 110, Orbicam integrated webcam

Unresolved Issues:
Orbicam - does not work.
SD card - does not auto-detect if it is in slot before bootup.

Resolved Issues (Post-Installation):
Broadcom WIFI - Restricted firmware drivers would not work on 64 bit gutsy, could not find compatible ndiswrapper drivers either. Had to downgrade to 32 bit gutsy, found working ndiswrapper drivers.

---

### Post by BluE_2ooth on 2007-11-04
Im  a  newbie  to  Ubuntu,  however  I  must  say  as  an  OS,  it  stands  above  the   rest.   I  really  enjoy  it,  however,  my  problem  is  with  this  device: -PCI Devices-

  Multimedia audio controller		: Ensoniq ES1371 [AudioPCI-97] 

  I  realize  my  sound  card  may  not  be  completely  supported..   This  is  A VERY  old  machine  : )  ..     I  had  an   issue  upon  installation  with  my  ETH device  ,  but  I  resolved  it  by  rolling back  the  device  driver  in  the  stupid  Windows partition.  ( Need it     
  for  school work, unfortunately)  SO..   Is  there  any  way  to  manually  edit  the  configuration  of  the  device  so  I  can  get  some  sound?  Its  my  one  and  only  issue  with   Ubuntu 7.10  thus  far..   Any  help  is  greatly  appreciated,  I  AM  new,  and  till  then,  I'll  keep  reading!

---

### Post by FEXOR on 2007-11-04
nVidia Riva TNT2 M64
Gutsy

Working: Standart drivers without GLX support

Not working:
Installing NVIDIA-Linux-x86-1.0-7184-pkg1.run for GLX support since config.h changed to autoconf.h

This is the newest (while old) GLX supporting driver for this graphic card.

Correct me if I'm wrong!

More detailed information:
[http://ubuntuforums.org/showpost.php?p=3704522&postcount=1459]("http://ubuntuforums.org/showpost.php?p=3704522&postcount=1459")

THX

---

### Post by 73man on 2007-11-05
Kingston Data Traveller 1GB model - no mounting even with a 'sudo mount'

---

### Post by razedk on 2007-11-05
My nVidia FX5700 doesn't work with Ubuntu 7.10.

See this link for more info - [http://ubuntuforums.org/showthread.php?t=580217](http://ubuntuforums.org/showthread.php?t=580217)

---

### Post by killatoffa on 2007-11-05
ATI Radeon HD 2600 pro
I tried using the Restricted Drivers tool and downloading and installing the driver from the AMD web site. the catalyst control center allows me to have my two monitors working but with alot of tearing & i can't run compiz fusion!!! also, in screens & resolution, it doesn't see my two monitors (dvi) which is dell 2405fpw & acer al2216w.
has anyone got this video card running ubuntu 7.10 gutsy gibbon with two LCD's at maximum resolution and full compiz fusion?

---

### Post by ARhere on 2007-11-05
1.  PROMISE RAID 5 Controller, PCI32/64 bit internal Card.
2.  [Promise Tech.]("http://www.promise.com/")
3.  [SX4000 ]("http://www.promise.com/product/product_detail_eng.asp?segment=RAID%20HBAs&product_id=94")(*and many others of the same type/family*)
4.  Great Raid/HDD controllers but little to no Linux support.  Drivers for the SX4000 are only for [Red Hat 9]("http://www.promise.com/support/download/download2_eng.asp?productId=94&category=driver&os=3&go=GO") and [SuSE]("http://www.promise.com/support/download/download2_eng.asp?productId=94&category=driver&os=1&go=GO").  Plus, binaries are only available on a floppy image.  **Most** of the [driver code]("http://www.promise.com/support/download/download2_eng.asp?productId=94&category=driver&os=4&go=GO") is open source though.

Using Ubuntu Desktop 7.10

---

### Post by auisce on 2007-11-06
**Toshiba A100 Satelite Pro:**
Feisty: sound card doesn't work at all and the ATI graphics are a joke but are ok for 2D with all effects TURNED OFF (including rounded corners of windows) .
[COLOR="Red"]there's a fix for all this: [http://ubuntuforums.org/showthread.php?t=361236&page=3](http://ubuntuforums.org/showthread.php?t=361236&page=3) [/COLOR]

**PNY Nvidia Geforce 7600 GT 256Mb X8 AGP**: couldn't get hardware 3D or OpenGl in Feisty OR Windows; card was returned to supplier.

**Saphire ATI Radeon X1650 pro 512Mb X8 AGP**: 
  Feisty:
   have hardware 3d (only with propriatary driver), games/GL works etc but bad performance and Compiz... doesn't work. The new EVE-Online native Linux client does work but when I undock it crashes.
 Gutsy:
  I tried I really did but had to go back to Feisty when I discovered that I had to use the default Ubuntu driver which doesn't work very well with this card because the propriatary drivers from both the repository and the AMD website kills X.

**BFG Nvidia 7600 GS 512Mb X8 AGP (factory over-clocked)**
BRILLIANT. Everything works flawlessly with no more effort than clicking on the "restricted drivers" icon on the top right and enabling the Nvidia driver. I know this shouldn't technically be here But just to let people know it's not all doom and gloom, I put it in.

---

### Post by darkmage77 on 2007-11-09
> **marcello100 said:**
> Sound card
Realtek alc 268
Sound card recognised on 6.10,but not working:no sound. Installed the newest drivers from realtek's website and alsa didn't find sound card.

Similar problem:
CreativeLabs Soundblaster Audigy (the first one)

Worked just fine pre 7.10, now shows as installed but will not function. Until sound gets repaired, will not use Ubuntu. It was going to be my only OS until this happened, too.

---

### Post by mpm on 2007-11-09
Logitec cordless EX110 keyboard/mouse package. (not listed specifically as a keyboard)
Volume button changes meter on screen but no actual volume change.
Internet navigation buttons do not work (exit/back).

---

### Post by supaplex on 2007-11-10
Motherboard MSI 945GCM5-V2. 
Malfunction network adapter. 
Checked on Ubuntu 7.04 and 7.10. 
TCP stack is malfunctioning, both in integrated controller, and external PCI cards. 
Ping and traceroute is OK,  but telnet, ssh, ftp etc - does not working.

---

### Post by jointstereotype on 2007-11-10
Under Ubuntu 7.10 (gutsy) on an Acer Aspire 5100-5674 laptop:

Built-in ENE flash memory card reader (CB-712/4) gives I/O errors when copying from (but not to) 2gb SD (secure digital) cards. Mounts / unmounts / reads / writes fine with smaller SD cards.

---

### Post by supaplex on 2007-11-10
> 
Under Ubuntu 7.10 (gutsy) on an Acer Aspire 5100-5674 laptop:

Built-in ENE flash memory card reader (CB-712/4) gives I/O errors when copying from (but not to) 2gb SD (secure digital) cards. Mounts / unmounts / reads / writes fine with smaller SD cards.
__________________
Specs: Acer Aspire 5100-5674, AMD Athlon 64 X2, 1gb RAM, 160gb SATA hard drive, ATI Radeon Xpress 1100 onboard graphics, Realtek HD onboard audio, Broadcom wireless, ENE flash card reader (CB-712/4) 


May be defected flash card. Try another.

---

### Post by ferd on 2007-11-13
Canon D1250 U2F

---

### Post by rickbeton on 2007-11-14
1)Type Of Hardware
  Widescreen LCD monitor

2)Hardware Maker
  Samsung Monitor with ATI graphics card

3)Hardware Model
  Samsung Syncmaster 2032BW with ATI Radeon HD2400 Pro

4)Known Issue
  Widescreen modes not available. The basic Vesa display driver is selected automatically during installation but it seems not to allow widescreen.  I've tried and failed to install a 'radeon' or 'fglrx' driver - they fail to start with the HD2400/2032BW combination.

Rick

---

### Post by rickbeton on 2007-11-15
Radeon HD2400 with Samsung 2032BW
  -- problem now solved - see Hardware Compatibility List

---

### Post by JulesBl on 2007-11-16
Hardware ATI Radeon x1300
Maker ATI
Drivers Restricted drivers
OS Gutsy-Gibon 7.10
Cant get it to drive the second output as anything other than a duplicate monitor. When I go to screen and graphics preferences there are two screen ones and the selection for the secondary screen is greyed out. When I do  xrandr -q I get this

julianb@julianb-desktop-main:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1600 x 1200
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      75.0*    70.0     60.0  
   1152x864       75.0     70.0     60.0  
   1024x768       75.0     72.0     70.0     60.0  
   832x624        74.0  
   800x600        75.0     72.0     70.0     60.0     56.0     47.0  
   640x480        75.0     72.0     60.0  
   1280x720       60.0  
   720x480        60.0  
   640x432        60.0  
   640x400        75.0     60.0  
   512x384        75.0     60.0  
   400x300        75.0     60.0  
   320x240        75.0     60.0  
   320x200        75.0     60.0  
   1600x1200      75.0  

Its like the second monitor does not exist

---

### Post by dpodo on 2007-11-16
Runing Ubuntu 7.10 x64 on Lenovo 3000 V100 (Intel chip set)



 no fax it seems that modem driver is missing and i've had touble finding one.
 vmware does not work - 1.04 and 2.0 betta tested - on 1.04 had serious problems with networking, and with 2.0 - well try it yourself.
 blue tooth has problems - same device that i used with vista now cannot be used - ericsson t630 to have web access by connecting it with bluetooth and use gprs
 embedded web camera does not work - couple of softwares did not dedect it.
 finger print reader does not work.
 card reader dors not work?
	
	in addition there is no support from lenovo for any linux destribution with this machine.
	

	I went back to windows vista(not that im happy about it)

---

### Post by synt on 2007-11-20
* Version Of Ubuntu
7.10

* Type Of Hardware
Samsung Monitor with ATI graphics card

* Hardware Maker / Model
Samsung Syncmaster 757NF with ATI Radeon 9800 Pro

* Issue 
My Monitor is not supported, i can's see him in the monitor list, can't put refresh rate higher than 85 hz (i need 100hz,and yes in windows all works perfect) That's the only reason i don't use ubuntu for the moment. tried everything.

---

### Post by loquela on 2007-11-20
I'm having problems trying to run v7.10 on a couple of configurations:

1. IBM Thinkpad R30 laptop

getting a string of errors on boot like [618.124000] Buffer I/O error on device fd0, logical block 0 then presented with BusyBox v1.1.3 shell

2. ACPI x86 based PC with
    RADION XPRESS 200 Series graphics
    
Get the loading screen but eventually screen just goes blank and seems to disconnect

Could someone please point me in the right direction to learn how to get linux installed on these (old) machines?

Many thanks

---

### Post by stoodleysnow on 2007-11-21
Try a different monitor. worked for me with a similar setup.:)

---

### Post by indoril on 2007-11-23
**Type Of Hardware:** Motherboard
**Hardware Maker:** Albatron
**Hardware Model:** PX865 PE PRO II
**Known Issue:** On board sound card isn' t recognized. There is no sound at all. (Ubuntu Gutsy & Feisty)

---

### Post by CarlosAtaide on 2007-11-23
Hi everyone!

I've been using Ubuntu for some time now and have been really happy with it! But I can't install Gutsy. Every variant of the 7.10 Ubuntu I can't install it.

ACPI: DMI BIOS year==0, assuming ACPI-capable machine

This is the error displayed, and after that the Live CD won't do anything. It looks like it's loading but after some time, it starts to display some errors. I have tried with:
Ubuntu 7.10
Xubuntu 7.10
Fluxbuntu 7.10
gOS (based on Ubuntu 7.10)

I have once attempted to do a roundabout of this by upgrading to 7.10 with the Internet updates, but the result is the same. The installer was successful, but I wouldn't start Ubuntu.
However, If in the GRUB boot options I'd choose the earlier version of Ubuntu (Feisty) then it would start normally with no problems.

On Edgy, and Feisty I have never encountered any problems of this sort. Can anyone help me with this?

I have already disabled ACPI in the BIOS but it made no difference.


Pentium III (Katmai) 550Mhz
MBoard: VT82c

---

### Post by Killer Cop on 2007-12-02
> **CarlosAtaide said:**
> Hi everyone!

I've been using Ubuntu for some time now and have been really happy with it! But I can't install Gutsy. Every variant of the 7.10 Ubuntu I can't install it.

ACPI: DMI BIOS year==0, assuming ACPI-capable machine

This is the error displayed, and after that the Live CD won't do anything. It looks like it's loading but after some time, it starts to display some errors. I have tried with:
Ubuntu 7.10
Xubuntu 7.10
Fluxbuntu 7.10
gOS (based on Ubuntu 7.10)

I have once attempted to do a roundabout of this by upgrading to 7.10 with the Internet updates, but the result is the same. The installer was successful, but I wouldn't start Ubuntu.
However, If in the GRUB boot options I'd choose the earlier version of Ubuntu (Feisty) then it would start normally with no problems.

On Edgy, and Feisty I have never encountered any problems of this sort. Can anyone help me with this?

I have already disabled ACPI in the BIOS but it made no difference.


Pentium III (Katmai) 550Mhz
MBoard: VT82c

You know you have a Pentium III CPU right? How old is your computer? I know I'm not that techy with Ubuntu yet, but I know even the most ressource efficient OS's need some power under the hood... :)

---

### Post by phinn on 2007-12-03
-Lenovo Thinkpad T60 running 7.10 with all current updates as of this post.
   (Intel Core 2 Duo 2GHz, 2GB RAM, ATI X1400 graphics, etc)
- Installed ATI's restricted driver for Compiz-Fusion (this could be the issue)

Issue #1
 Will not come out of Standby.  Just get a black screen with a curser blinking

Issue #2
 Will not come out of Hibernate.  Same thing.

Issue #3
 Cannot dim/brighten the screen with the hardware keyboard controls.  It doesn't work when its plugged in OR when its unplugged. This even worked in Feisty.

Issue #4
 Cannot use the middle mouse button to scroll through documents (such as Firefox)
 This is resolved by adding the following two lines to xorg.conf under "Section InputDevice":
              Option  "EmulateWheel"  "true"
              Option  "EmulateWheelButton"  "2"

EDIT: I reverted back to the non-ati drivers and it fixed issue #1 and #2 but not #3.

---

### Post by JayFunGee on 2007-12-03
Toshiba Tecra A4
Intel(R) Pentium(R) M processor 2.13GHz
800.000 MHz
2MB cache
1.5GB RAM
80 GB HDD
Matchita DVD-RAM

Initially installed Feisty.
Most things worked, accept graphics accelerator, modem, memory card reader. Machine stated real quick and response times were good.
Cannot switch between users, hibernate or suspend.

Now running Gutsy.
Only the card reader does not work - have not tried to fix that yet ...
Start-up is REALLY really slow, but once it is going all seems OK.
Cannot hibernate or suspend.

---

### Post by dbcalo on 2007-12-05
> **CarlosAtaide said:**
> Hi everyone!

I've been using Ubuntu for some time now and have been really happy with it! But I can't install Gutsy. Every variant of the 7.10 Ubuntu I can't install it.

ACPI: DMI BIOS year==0, assuming ACPI-capable machine

This is the error displayed, and after that the Live CD won't do anything. It looks like it's loading but after some time, it starts to display some errors. I have tried with:
Ubuntu 7.10
Xubuntu 7.10
Fluxbuntu 7.10
gOS (based on Ubuntu 7.10)

I have once attempted to do a roundabout of this by upgrading to 7.10 with the Internet updates, but the result is the same. The installer was successful, but I wouldn't start Ubuntu.
However, If in the GRUB boot options I'd choose the earlier version of Ubuntu (Feisty) then it would start normally with no problems.

On Edgy, and Feisty I have never encountered any problems of this sort. Can anyone help me with this?

I have already disabled ACPI in the BIOS but it made no difference.


Pentium III (Katmai) 550Mhz
MBoard: VT82c

i think it has something to do with the newer kernel in 7.10. i have no idea what though.

> **Killer Cop said:**
> You know you have a Pentium III CPU right? How old is your computer? I know I'm not that techy with Ubuntu yet, but I know even the most ressource efficient OS's need some power under the hood... :)

i have a dfi nforce 4 ultra-d board with a amd 64 x2 4200 and im getting that error. so age has nothing to do with it.

---

### Post by Vanon on 2007-12-05
pentium d 3.2ghz@3.5 ghz
asrock 4coredual-sata2
X1950pro 512mb AGP
2gb ram ddr2

can't use any visual effects for the desktop, everything becomes choppy:frown:

---

### Post by CarlosAtaide on 2007-12-06
**This post could be related to an Ubuntu bug filed at**: [http://bugs.launchpad.net/ubuntu/+bug/164779](http://bugs.launchpad.net/ubuntu/+bug/164779) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**This post could be related to an Ubuntu bug filed at**: [http://bugs.launchpad.net/ubuntu/+bug/164779](http://bugs.launchpad.net/ubuntu/+bug/164779) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **Killer Cop said:**
> You know you have a Pentium III CPU right? How old is your computer? I know I'm not that techy with Ubuntu yet, but I know even the most ressource efficient OS's need some power under the hood... :)

My computer is very old! Pentium III says it all, but still I can run Ubuntu + Gnome + Desktop widgets  just fine. Or I can just run Fluxbox without any eye candy and get out all the power under the hood. 
My problem isn't that, my problem is this bug with the linux kernel 2.6.22 that won't boot in my pc. Sadly, no fix for it yet  =/

---

### Post by liquidfunk on 2007-12-06
Linksys Ralink WUSB54GR USB Wireless Card
Rt73 Based
Quite tempermental, work for an hour, then stop. Requires you to unplug the card, then plug it back it for it to carry on working.

 Gutsy Gibbon.

---

### Post by QvasiModo on 2007-12-09
Using the Ubuntu Feisty live cd.

**Type Of Hardware:**
LCD monitor

**Hardware Maker:**
[http://www.lge.com/](http://www.lge.com/)

**Hardware Model:**
LG L1900R

**Known Issue:**
The image placement is incorrect. Specifically, the left side of the desktop is trimmed and I see a black vertical bar at the right side. In Windows this would be corrected with the proprietary software but LG doesn't seem to have a Linux version of it. :(

Here are the monitor specs:
[http://www.lge.com/products/model/detail/l1900r.jhtml](http://www.lge.com/products/model/detail/l1900r.jhtml)

Note this didn't happen to me with an old ubuntu 5.04 live cd I had lying around. Strange!

---

### Post by newbie2 on 2007-12-16
hp 6715b laptop :

[http://h18000.www1.hp.com/products/quickspecs/12686_na/12686_na.HTML](http://h18000.www1.hp.com/products/quickspecs/12686_na/12686_na.HTML)

gutsy has problems with : wireless/fingerprint sensor/graphically/bios/ etc.....
:sad:

---

### Post by dnvikram on 2007-12-24
Having issues with the below in Gutsy Gibbon on My Dell Inspiron 1420N

1)Having issues getting Gutsy detect the integrated bluetooth module.
2)Sound recording is not possible as the microphone has issues ,which Dell site also mentioned and the status of this issue on the Launchpad is still PENDING.

---

### Post by Blake Morgan on 2007-12-28
I am in the process of building an HTPC, and was attempting to use the LinuxMCE, which is based on Kubuntu 7.4. The core of this system is an Asus M2A-VM HDMI motherboard with an AMD Athlon X2 4400+ 64bit CPU and 2 gig DDR2 RAM. All of the Ubuntu variants listed below are referring to AMD 64bit CPU compatible versions.

The initial attempt to load the LinuxMCE distribution got hung on the point where live CD gets to "loading/booting/something at /etc/rc.local and the system just hangs. I also tried Mythbuntu with the same result and Ubuntu 7.10, straight (no weird MCE stuff); same problem. I also tried loading several other OSs such as Fedora 8, DSL-Linux, and straight up Debian Sarge. Nothing would install from any of those either. 

The shipped BIOS version was 0502, and I flashed the latest BIOS, 1603, and repeated the same sequence of operating systems as above. None of the Ubuntu variants would take, and all of them hung at the same spot: loading /etc/rc.local. I did eventually get Fedora Core 8 installed without a single hiccup. 

I have installed all of these OS (barring the MCEs) at one time and currently run most of them on various machines in my house, including an openMosix based cluster in my basement (recodes mps to flac like and renders vid like crazy). I have never had this much trouble installing an operating system on a piece of hardware EVER. It is doubly sad, because of all these systems, I enjoy using the Gutsy Gibbon machine over all the rest. Run away from this board as if a horde of pirates was at your stern. (It does run Fedora 8 hella fast though, but the frustration is not worth it.)

---

### Post by azexian on 2007-12-29
My PNY Nvidia 7300gs gives a very low fps on glxgears, *and games* there are scattered threads across the web about this issue, I have a thread here: [http://ubuntuforums.org/showthread.php?t=651674&page=2](http://ubuntuforums.org/showthread.php?t=651674&page=2) my average fps is about 1500 in glxgears

---

### Post by nerderello on 2007-12-30
1)Type Of Hardware
2)Hardware Maker
3)Hardware Model
4)Known Issue

1) Video Card
2) Radeon
3) Radeon 9600
4) If you use the restricted ATI driver this works fine until you change the resolution and then (no matter what you do, even return the resolution to what it was) you get lock up / re-boots after a number of minutes use. Disabling the restricted driver allows stable use of this AGP video card.

---

### Post by Kip_Cathey on 2007-12-30
Toshiba A75
MP-BIOS bug: 8254 timer not connected to IO-APIC.  If you wait for timeout, seems to work fine.
Atheros Wireless AR5212/AR5213 cannot connect to any secured network, even with restricted driver.  Also, randomly connects/disconnects unless roaming mode is enabled.  Only solution is unsecured wifi.
Also, unit randomly disconnects from AC adapter when it gets warm, screen flashes, and it says it is now on battery, but this isn't a problem with the jack.  Seems as though unit doesn't like my lap.  Only fix is to unplug, then plug back in.  Does it even when lid is closed and no open proceses.

But it did fix my usb controller problem windows kept harping on about.  Bonus there I suppose.

All this is from Gutsy.

---

### Post by por100pre1 on 2008-01-01
[B]1)Hardware: Wireless Desktop PCI Adapter
2)Maker: D-Link
3)Model: DWA-542
4)Issue: Lack of drivers[/B]

The culprit here is the **Atheros 5416 Chipset (Atheros 5008 Series)**. The windows drivers can't be used with ndiswrapper, they cause a kernel crash. the madwifi project is working in a solution to this but there is not a stable driver yet. Here's a previous post about Atheros 5008 series chipsets.

> **Nilks said:**
> Wireless
Atheros
AR5008X (AR5416/5133)

I have tried with ndiswrapper and a lot of different drivers. I have tried with wifi-radar and wicd. I tried madwifi. All with no working result.

---

### Post by mdoube on 2008-01-01
Sony Vaio SZ650NC Notebook

webcam not working (though there is a driver to compile elsewhere, r5u870, it needs to be updated for compatibility with linux 2.6.24): Ricoh / Sony Visual Communication Camera VGN-VCC7
nVidia 8400M GS not going on boot (up to Hardy alpha-2)
Smart battery identified as 2 batteries (new issue in linux 2.6.24)
dual display adapter config (Intel GM965 / nVidia 8400M GS) not accounted for
wlan Led not going (intel are putting this in a new verison of iwl4965 hopefully)
suspend and hibernate are flaky (suspend better at the moment)
fingerprint scanner not going: UPEK TouchChip fingerprint coprocessor
hybrid hard disk nvcache functionality not active

I've got a laptoptestingteam page here, which links through to several launchpad bug reports: 
[https://wiki.ubuntu.com/LaptopTestingTeam/SonyVaioVGN-SZ650N](https://wiki.ubuntu.com/LaptopTestingTeam/SonyVaioVGN-SZ650N)

---

### Post by syahya on 2008-01-05
Laptop

SAMSUNG R40 

in 7.10, Video display is corrupted :confused:

It was fine with 6.XX

---

### Post by JC Cheloven on 2008-01-06
Hardware: Toshiba laptop
Model: A50 (centrino 1.6MHz)
Ubuntu version: 7.10 (Gutsy)

Issue: Error messages at startup. 
"cannot allocate resource region 4 of device 0000:00:1d.0" 
"cannot allocate resource region 4 of device 0000:00:1d.1" 
"cannot allocate resource region 4 of device 0000:00:1d.2" 
  --> Note. The option "pci=routeirq" in grub, didn't help with this issue.

Issue: ACPI error (seen executing "dmesg | less").
"ACPI: looking for DSDT in initframfs...error, file /DSDT not found"

Issue (maybe related to the previous ones):
Unable to sleep/hibernate. Often unable to shutdown properly (system hangs up).

-->Note. Despite of these, Ubuntu 7.10 is fairly usable on a Toshiba A50 laptop. 
_____________________________

---

### Post by tompratt0 on 2008-01-12
in the case of gutsy the whole nc8000 system

it wouldn't even start

just gave me a whole heap of errors

---

### Post by bravemosquito on 2008-01-13
AMD Sempron 3200+ s. AM2
AsRock ALive NF7G-HDReady
used nVidia 7050 integrated video
used ALC888 integrated audio
used nVidia 10/100/1000 integrated LAN controller
HDDs: 250GB 16mb cache Maxtor PATA, 320GB 16mb cache Seagate SATAII, 500GB 32mb cache Seagate SATAII
Ubuntu 7.10

Yesterday I started the U for a maintenance... Just updated it and got a lot of problems:

- sound is choppy :shock: (before update all was ok)
- my additional and primary LAN controller stops workin' - SureCOM EP-320X-R 10/100 :shock: (before update all was ok). I can't remember the error msg but it was somethin like "cannot find device... trying to detect through BIOS" or similar...
- needed to remove NFS-common utils and some kde related packages to ensure fast boot. For information before that the boot time was fine but this doesn't go long enough - the reboot or two before updating I've got a slow one :confused:

---

### Post by aaaantoine on 2008-01-15
Hmm, I don't see a laptop hardware incompatibility list, otherwise I'd transplant the contents of this post.

**Hardware:** Acer Aspire 5050-5554 Notebook
**Operating System:** Ubuntu 7.10 AMD64

**Issues:**
1. Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
 - Does not work out of the box; requires firmware installation.  Installation requires firmware file on hand or a wired network connection.

2. Microdia OrbiCam (USB device 0c45:6260)
 - No known driver support

3. Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
 - Laptop speakers are mapped to the "Surround" channel.
 - Microphone does not work.
 - Laptop speakers do not mute when headphones are plugged in.

4. VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
 - Ubuntu 7.10 restricted drivers require the additional installation of the package xserver-xgl if you want to enable desktop effects.

General
 - The custom Euro and Dollar keys above the directional keys do not function.
 - Suspend and Hibernate both fail.  I do not know what hardware to attribute this to.

---

### Post by ripperzane on 2008-01-15
ATI Radeon HD 2400 (512M RAM on Graphics Card)
AGP 8x

ATI Forums gives a guide (which I am on 3rd install attempt). 
Restricted Driver Manager says i dont need a driver (uses Vesa)
Tried lastest ATI*.run from site and nogo on both custom distro install and automatic
Tried envy for the freak of it,
even tried 
"sudo apt-get install xorg-fglrx"
or something close...
still stuck in Vesa.
using #glxinfo | grep direct 
reports the good old mesa_inderect, no direct rendering.
oh well

---

### Post by nsgoh on 2008-01-16
HP server.

HP Netserver LC2000
HP Netserver E800

Both also hving problem running liveCD.

---

### Post by trebormills on 2008-01-17
MSI motherboard: P6NGM 
intel dual core CPU
DDr2 ram
PATA hdu and dvdrw

7.1 64bit editon
All seems to work ok until you try sound which is not detected/installed (realtek chip??) and also video (71xx chip with 630i??) which does not get detected as nvidia correctly and as such has no 2d/3d fancy features as using basic vesa. Propriatory drivers installer pops up but does not actually install nv or nvidia correctly as still runs in low gfx mode with no fancy features. Did reinstall and tried envy ... does not solve video issue. No problems with lan or drive access. Have not tested USB yet so may or may not work. Seems newer drivers needed from nvidia for nforce aspect. In hardware many many bits show up as unspoorted/unknown. System however does run and updates as per normal, not usuable as main system until sound, video resolved

---

### Post by andrebrait on 2008-01-23
ABIT Radeon 9600XT

Will give the "Black" Screen of death if not using vesa drivers. Both ati and fglrx result the same error.

---

### Post by LostMagix on 2008-01-29
Ubuntu 7.10 (gutsy)

USB Wireless RocketFish 2,4G Laser Mouse

the side scroll doesn't want to work.

---

### Post by the_analyzer on 2008-02-02
Laptop Acer Extensa 5210

The headphones wont work.

---

### Post by Sabot on 2008-02-08
Abit
NF-M2SV Motherboard
(Realtek ALC662 rev 1)
Mic Port Does Not Work
(Works in Vista and with Newer ALSA Driver from Source)

---

### Post by holmestp on 2008-02-08
Printer incompatibility with Fiesty Fawn, Ubuntu 7.10

HP Business Inkjet 1100 (worked fine on Ubuntu 7.04)
   recognizes but does not print to.
HP Officejet 6310
   recognizes but does not print to.
both ink jet printers.

Have a HP laserjet 1300 too, and that works fine with 7.10.

---

### Post by bethnesbitt on 2008-02-08
I've tried everything out there from ndis wrapper to the atheros chipset linux driver, nothing on my new EDUP Wireless Adapter PCI 2.4ghz

---

### Post by Sabot on 2008-02-08
Abit
NF-M2SV Motherboard
(Realtek ALC662 rev 1)
Mic Port Does Not Work
(Works in Vista and with Newer ALSA Driver from Source)

---

### Post by tdm on 2008-02-09
I cannot access the internet with any program but i can access other computers on my network.

Toshiba Satellite A50
1.5GHz Intel Pentium M processor
1GB DDR RAM
Intel PRO/100 VE Network Connection :confused:
Intel PRO/Wireless 2200BG Network Connection
Intel 855GM Graphics Chip

I **was** using Ubuntu 7.10
Linux Mint 4.0 which is based on Ubuntu 7.10 accesses the net with Firefox but nothing else.
Interesting Point: Ubuntu 7.04 **_DOES_** go on the internet perfectly!!!
Testing release - Ubuntu 8.04 Alpha4 **_DOES_** go on the internet
Any release before 7.04 doesn't go on the internet. I've tried every release except for Warty which I doubt will work.
 :confused: :confused:

---

### Post by tdm on 2008-02-09
> **tdm said:**
> I cannot access the internet with any program but i can access other computers on my network.

Toshiba Satellite A50
1.5GHz Intel Pentium M processor
1GB DDR RAM
Intel PRO/100 VE Network Connection :confused:
Intel PRO/Wireless 2200BG Network Connection
Intel 855GM Graphics Chip

I **was** using Ubuntu 7.10
Linux Mint 4.0 which is based on Ubuntu 7.10 accesses the net with Firefox but nothing else.
Interesting Point: Ubuntu 7.04 **_DOES_** go on the internet perfectly!!!
Testing release - Ubuntu 8.04 Alpha4 **_DOES_** go on the internet
Any release before 7.04 doesn't go on the internet. I've tried every release except for Warty which I doubt will work.
 :confused: :confused:

I have fixed the problem!!!!!!!!! :) :) :)
I opened forefox, went to about:config, Typed ipv in the filter and then i double-clicked network.dns.disableIPv6

:lolflag:

---

### Post by joshdudeha on 2008-02-13
Speedtouch 330 ADSL USB Modem
After toying around and finding firmware-it finally worked.
But, would be nice if this driver was already included in the beginning.
Sometimes doesnt connect and have to do a hard re-boot.

Ubuntu 7.10
had the same trouble with Dapper

---

### Post by andrewjoy on 2008-02-14
Scanner
Canon LiDE 80
Not detected / not supported by SANE
Ubuntu 7.10

---

### Post by Redrazor39 on 2008-03-01
Sony Vaio VGN-SZ430N

Built-in MotionEye webcam is not recognized
Memory Stick Pro Duo reader is not recognized (haven't tried the all-in-one card reader yet, but that only does Memory Stick Pros)
Fingerprint reader may or may not work, I have not been able to find software for it
*Edit*: Suspend doesn't work, either. This is very important to me because I use sleep on Vista A LOT and with ubuntu it just blacks the screen, the lights flash, and then nothing happens. To get it open again, I have to reset the entire system. I might as well shut it down! 

These problems are EXTREMELY important to me because I use all of these things VERY OFTEN on my Vista partition and I was hoping to do the same with ubuntu, along with ubuntu's other benefits.


Idk if this is supposed to happen, but ubuntu takes up to a full minute to start up, and this is a pretty nice laptop. Ubuntu should be up and running in 30 seconds or less! I think macs can do that, Ubuntu should be the magic that allows this to happen on almost any hardware

Also, this laptop is less than a year old. When can I expect my laptop hardware to be fully supported?

---

### Post by carl.alv on 2008-03-05
Toshiba Satellite A215-S7472
Ubuntu Gutsy 7.10

Atheros wifi: Installed it using the information in this post [http://ubuntuforums.org/showthread.php?t=606040&highlight=atheros+ar5418](http://ubuntuforums.org/showthread.php?t=606040&highlight=atheros+ar5418) . Works fine.

ATI mobility radeon HD2400: Installed it using the info in this post [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Installation](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Installation) . At first seemed to work, (using the manual procedure), it even had some funny visual effects, openGL did not worked right however (openGL using applications appear all broken and pixeled). After some reboots the cool visual effects were gone altogether, was not able to get them back even though I reinstalled the drivers.

Chicony webcam: did not work.

No microphone.

Sound seems to work right.

Resuming, some important aspects of the ubuntu gutsy installation (wifi and video acceleration) on this machine seem to degrade over time, even if at first they seem to work right, I have double boot with vista, but I don't know if this is supposed to affect the ubuntu installation,

Edit: 64 bit ubuntu version. I reinstalled mesa and now OpenGL works fine now, FPS are not high but at least it works.

---

### Post by ManiDhillon on 2008-03-08
I have Xubuntu 6.06.1 [Dapper Drake] installed on an IBM Thinkpad 600E having 300MHz Intel P2, 192 MB RAM and 6.4 GB HDD.
The builtin track point works perfectly but the PS/2 mouse doesn't work at all.
That same mouse used to work on Zenwalk, Ubuntu 7.10.
Can anyone please help.

---

### Post by Warmask on 2008-03-10
1) ATI Radeon HD 2600XT PCIe x16
2) Manufactured by PowerColor
3) Radeon HD 2600 XT
4) After installation of 7.10, after selecting Ubuntu from the boot menu, screen turns black and hangs.

---

### Post by brainstuff on 2008-03-10
My machine is running Ubuntu 7.10 64bit on AMD X2, 2Gb RAM, LG L204WT widescreen monitor over DVI, 1680x1050 native

Problem is AGP Sapphire x1950 Pro - getting black screen after login if I use any driver other than Vesa

---

### Post by finny388 on 2008-03-16
1)Video Card
2)ATI
3)Radeon 8500
4)Cannot adjust from 1024x768 @ 60Hz. Very frustrating. Too old.

I tried everything

See my attempts to get it working [here]("http://ubuntuforums.org/showthread.php?t=689868")

---

### Post by Redrazor39 on 2008-03-16
Just a thought, is anybody actually reading this or doing anything? What's going on?


I hope my hardware issues are fixed with hardy, as do most people with problems like this.

```
sudo make my hardware work

ERROR: access denied

sudo make my hardware work *please*

Ubuntu 8.04 Hardy Heron is available. Upgrade now? [Y/n]

y

blah blah blah code and weird symbols blah blahblah
 blah blah code and weird symbols 
blah blahblah blah blah code and weird symbols blah
 blahblah blah blah code and 
weird symbols b
lah blahblah blah blah code and weird symbols blah
 blahblah blah blah code and weird symbols blah
 blahblah blah blah code and weird symbols blah blahblah blah
 blah code and weird symbols blah blahblah blah blah code
 and weird symbols blah blahblah blah blah code and weird symbols bla
h blahblah blah blah code and weird symbols blah
 blahblah blah blah code and weird symbols blah blahblah 
blah blah code and weird symbols blah
 blahblah blah blah code and w
eird symbols blah blahblah blah blah
 code and weird symbols blah blahblah blah blah code and weird sy
bols blah blahblah blah blah code and weird symbols blah blahblah
 blah blah code and weird symbols blah blahblah
 blah blah code and weird symbols blah blahblah blah blah code
 and weird symbols blah blahblah blah blah
 code and weird symbols blah blah


*ding*


Your hardware is now 100% supported.


sudo thanks!
```


If only it were that easy :(

---

### Post by yasin_ecir on 2008-03-17
I have got my ACER 5102 laptop. my motherboard integrated graphical card ATI Radeon Xpress 1100 cannot be recognized and acer orbicam 0.3 megapixel webcam doesnt work. webcam is seen like plugged in USB in windows, but it is not external. it is also integrated in laptop. and my ENE 5 in 1 card reader is not seen.

---

### Post by theJagger on 2008-03-19
hp e800 netserver will start to boot if you hit F6 at the boot menu to get more opions and remove the -- and  add>  noacpi nolacpi acpi=off this gets you further along. THOUGH so far i have not had a successful install.

---

### Post by marine63 on 2008-03-26
x2gen mw19r 19 inch lcd monitor
after loading monitor turns black and the light turns blue to red on monitor...
used ubuntu 7.10 alternative 
and update ubuntu (using another monitor) to 8.04 thru update manager and used restricted drivers 
and yet have not fixed my problem.

---

### Post by teabag_46 on 2008-03-31
Built in wifi in my Amilo pro 2040
AGK graphics tablet


Neither of these work in my laptop, using ubuntu 7.10

---

### Post by vivalant on 2008-03-31
> **aaaantoine said:**
> Hmm, I don't see a laptop hardware incompatibility list, otherwise I'd transplant the contents of this post.

**Hardware:** Acer Aspire 5050-5554 Notebook
**Operating System:** Ubuntu 7.10 AMD64

**Issues:**
1. Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
 - Does not work out of the box; requires firmware installation.  Installation requires firmware file on hand or a wired network connection.

2. Microdia OrbiCam (USB device 0c45:6260)
 - No known driver support



The Microdia driver is available at [http://www.linux-projects.org](http://www.linux-projects.org) It's closed source :(

---

### Post by 1oldman on 2008-03-31
Ubuntu will not install on my new Compaq Presario F730US with an AMD64 AthlonX2 and nvidia graphics chipset.:confused:

---

### Post by Regenpak on 2008-04-04
Intel has this nice little "Via killer" Mini-ITX board, called D201GLY2. I installed 8.04 beta, but the graphics adapter is not really cooperating. In its initial resolution (1200*900 or something, I could not make it out) the display was cut up in narrow vertical stripes. Mouse pointer OK. Setting it to 1024*768 solved that but anything higher is marred by static (fine patterning and stripes) across the display. Of course Intel does not provide any Linux drivers and there seem to be no "restricted" drivers. Maybe the chipset is just too new. I'll play with it a bit more, I was able to get a nice image with Knoppix 5.0.1 and I'm sure Billy Gatez' Quality Product will install just fine. Performance as such of this board seems pretty decent, certainly the 1.2 GHz Celeron CPU (passive cooling!) is much faster than my Via Epia C3 at 800 MHz.

Edit: [This thread](http://ubuntuforums.org/showthread.php?t=463077) provides a solution. Have yet to try it, but it looks promising.

---

### Post by Linux_freek on 2008-04-04
HELLO ! 
My hardware is :
Ubuntu version:7.10 Amd64
Intel 945 GNT chipset 
Moniter:19 " widescreen samsung SyncMaster 920nw
Problem is :
Although ubuntu has a driver for my video card but it is not working fine. :(
 Widescreen mode is not supported.
2. When i set the highest resoulution mode i.e. 1440x900 screen shrinks to half of the width . and in ubuntu "screens and resoultion" dialog box shows 1440x900 is set @56hz.
3.Working Resoultion modes 1280x1024 @ 60hz 1024x768 @75hz. 
3. Even lower widescreen modes are not set.

And BTW hard ware if fine as all the available modes work fine with WinXp

Thanks. please reply.

---

### Post by mike_f on 2008-04-06
My Canon 3000F scanner is detected by sane-fine-scanner but is not supported. I manually added it to the genesys and canon630u config files, still no joy. :(

---

### Post by MDMS on 2008-04-08
My hardware is:  (old) IBM Thinkpad Laptop model 380Z
Xubuntu version 7.10 (or also with Beta 8.04)

The problems are:
--> No sound other than speaker 'beep'.  The sound chip is on the EISA bus; haven't been able to successfully recognize the chipset using the normal sound configuration tools.
--> This laptop does not have a built-in Ethernet interface but the infrared port is (erroneously?) bound to an Ethernet device 'irda0'
--> During initial installation process, the USB to Ethernet adapter (with ASIX chipset) is not found at all.  However, the correct linux driver seems to be assigned to the ASIX chipset and the Ethernet 'link' LED is on.  (I've tried automatic configuration with Network GUI, manual configuration and both static and dynamic IP schemes.)
--> I have not been able to get any Ethernet functionality to work at all.  Exact same setup _does_ work with MS Windows 95 and MS Windows ME OS.

---

### Post by dbp876 on 2008-04-08
I could not get Ubuntu 7.10 or 8.04 (beta) both 64-bit,  to install with the SLI bridge on the video cards, once I removed the SLI bridge it installed fine with both versions. I have not tried to put the bridge back on since I have gotten the OS to install with the correct nvidia drivers.  


OS: Ubuntu 8.04 beta (dual boot XP)
Motherboard: evga 780 sli
Processor: intel core 2 quad kentsfeild 2.4ghz
Ram: crucial ballistix tracer 2 (4 gigs)
video card: XFX 8800GT (x 2 without sli bride)
cdrom: HP DVD 1040
HDD: WD 500GB 7200 rpm sata 3.0Gb/s

---

### Post by vvvladut on 2008-04-11
Flatbed scanner
Canon Canoscan 8400F
Doesn't work at all, is not detected by XSane
Ubuntu Gutsy

---

### Post by wribeiro on 2008-04-17
Ubuntu 8.04 Beta - running in live mode
HP Pavilon dv6636 Turion X2 1.9 64 Dual-Core Processor, 2GB memory

Problem: Graphics card NVIDIA GeForce Go 7150 (UMA) is not recognized correctly and only works on 800x600 resolution.

Windows information about the hardware: 
- Adapter type: NVIDIA MCP67M 
- Chip type: GeForce 7150M / nForce 630M

---

### Post by colinet on 2008-04-17
1)Type Of Hardware: Mini Server -
2)Hardware Maker:  Home built - 256 MB Ram - 500GB HD, storage - 4GB Compact flash via and                 IDE converter for the OS.

3)Hardware Model:  Epia Mini ITX M1000 Nehemiah 

4)Known Issue:  
                           Tried loading  Ubuntu 7.10-Server - It loaded up and all looked good until I booted for the first time then I got a message saying that the kernel wasn't compatible with the processor.

                           Tried loading Ubuntu 6.06.2-Server - Again it loaded up fine and on booting for the first time it went through to to booting kernel and then just froze!  No messages at all.

It looks as though both Server variants are incompatible with the EPIA mini ITX boards.  A pity as they would have made a great combination as a NAS.

---

### Post by falkTX on 2008-04-18
> **Linux_freek said:**
> HELLO ! 
My hardware is :
Ubuntu version:7.10 Amd64
Intel 945 GNT chipset 
Moniter:19 " widescreen samsung SyncMaster 920nw
Problem is :
Although ubuntu has a driver for my video card but it is not working fine. :(
 Widescreen mode is not supported.
2. When i set the highest resoulution mode i.e. 1440x900 screen shrinks to half of the width . and in ubuntu "screens and resoultion" dialog box shows 1440x900 is set @56hz.
3.Working Resoultion modes 1280x1024 @ 60hz 1024x768 @75hz. 
3. Even lower widescreen modes are not set.

And BTW hard ware if fine as all the available modes work fine with WinXp

Thanks. please reply.

I got the same problem some time ago. It can be fixed by changing the refresh rate.

I had this:
1280x800 @ 59Hz - The real resolution was 1024x768, shrinked (like yours)
then I changed to:
1280x800 @ 60Hz - Perfect!

I still don't understand why it happens, but it works that way..

---

### Post by lunaluna on 2008-04-21
hi 
i have an ati mobility x700
everything seems to be ok but when i try to enable desktop effects it gives me:
with  the free driver:... cannot be enabled
on restricted one:  the composite extention could not be loaded
some help?

---

### Post by eln0k0fl on 2008-04-23
Motherboard?
ASUS
AN32 SLI Deluxe
Ubuntu-8.04-beta-desktop-amd64.iso hangs on install at Busybox V1.1.3. Checksums OK and tried ACPI=0 switch. Gutsy installs OK. Have dual 7800 GTX's.

---

### Post by screwballl on 2008-04-23
ATI Radeon (Sapphire) X1950GT PCI Express
Basic VGA options available on all variants of Ubuntu but no driver will load, and hardware accelleration is disabled.
Max resolution allowed is 1024x768, antyhing higher scrambles everything once X is loaded. Tested on 6.06, 7.04, 7.10, 8.04Beta desktop and server variants, Gnome and KDE... plus various other linux distros.
ATI/AMD website does have a driver for X1900 but not X1950 (they are different cores thus need different drivers)

---

### Post by Soledge on 2008-04-23
Graphics Card
manufacturer: Intel
Model: Intel Corporation 82810E DC-133 (CGC) chipset controller (rev 03)

Issue:  I am Currently running Ubuntu 7.10 Gusty with a screen resolution of 800X600, my original install of Edgy worked with many other resolutions to make my desktop screen larger and give me more room to see my windows and work. 

I am requesting support for my graphics card or any drivers that i may require that could possibly be provided. if not by the newest release, then by individual files.

with 800X600 i simply cannot operate as efficiently as i would otherwise. So far i have found nothing on this particular hardware issue. Hopefully the new release of Hardy will correct this issue. if not however, i still need it resolved.
*EDIT: i found the issue, its my Compaq MV540 monitor that does not work well with 7.10 nor 8.04 (my graphics card sucks) but i need a fix for this.


Thanks:

Sol

---

### Post by epitaph123 on 2008-04-24
Acer Aspire 5050, 2.0ghz, AMDturion64 MK-36, 1gb Ram, Integrated Motherboard Ati Radeon Express 1100



Ubuntu-8.04-beta-desktop-amd64.iso
ubuntu-8.04-desktop-i386.iso



Both i386 & x64 Architecture came to this same error



Booted from cd, selected install ubuntu, but it never got to the desktop to be able to install, hangs on Busybox.

(initramfs) [73.717013] 8139cp 0000:08:02.0: This (id 10ec:8139 rev10) is not an 8139c+ compatible chip

---

### Post by nukedathlonman on 2008-04-24
Acer Aspire 5002WLMi laptop running Hardy 8.04

Only current major problem: internal Broadcom wireless adapter does work with current b43 driver in 2.6.24-16-Generic kernel.  HOWEVER the current b43 driver is like the previous bcm43xx driver n which it generates ton's of APIC errors (about 1 every 2 seconds approximately).  This over time bogs down the system and eventually causes a hard crash regardless of system load.

The wireless does work 100% flawlessly with the old 2.6.22-14-Generic Kernel and ndiswrapper in Hardy (temp work around I'm using for the time being).  While ndiswrapper does load under 2.6.16-Generic Kernel, ndiswrapper will not load the actual WinDoze Broadcom driver (debugging).


Oddities: Touchpad also stopped working after upgrade to Hardy, but suddenly started working perfectly after running Windoze.  USB used to stall during transfers with Kodak cameras unless a self powered hub was used (Drapper, Fiesty & Gusty) - no longer the case with Hardy.  Everything else (from ACPI hibernate/sleep modes right down to the internal data/fax modem) works 100% flawlessly (SiS video adapter drivers needed to be tweaked slightly).

---

### Post by gwoodard on 2008-04-26
1)Video card/optical mouse
2)ATi/Microsoft
3)Radeon HD 2400 Pro AGP/Intellimouse Blue
4)only can get certain resolutions/cursor LAGS

Oh, my other hardware as follows:
2.4 Ghz Intel HT Pentium 4 processor, 1 GB ram, other than that look at my signiture...

---

### Post by rsawoseyin on 2008-04-27
Averatec AV2100 series laptop

---

### Post by cagedrefrain on 2008-04-28
ATI Remote Wonder -- worked under the last rev of Ubuntu...:(

---

### Post by -=Viper=- on 2008-04-28
Any ATI x200 card.  can not log into ubuntu.  xserver crashes i think
solution here:
[http://ubuntuforums.org/showthread.php?t=765465&page=4](http://ubuntuforums.org/showthread.php?t=765465&page=4)

> **Peter09 said:**
> try using envyng, its in the repositories or you can download by

```
sudo apt-get install envyng-gtk
```
and you may need
```
sudo apt-get install envyng-core
```

once these are installed 

```
envyng -t
```

and ask it to install the ATI driver.

PC

---

### Post by -=Viper=- on 2008-04-28
Any ATI x200 card.  can not log into ubuntu 8.04.  xserver crashes i think
solution here:
[http://ubuntuforums.org/showthread.php?t=765465&page=4](http://ubuntuforums.org/showthread.php?t=765465&page=4)

Log into Failsafe GNOME and follow instructions below

> **Peter09 said:**
> try using envyng, its in the repositories or you can download by

```
sudo apt-get install envyng-gtk
```
and you may need
```
sudo apt-get install envyng-core
```

once these are installed 

```
envyng -t
```

and ask it to install the ATI driver.

PC

---

### Post by Gamehunter on 2008-05-07
**Processor:** Intel Core 2 Duo E8400 3Ghz 
**Motherboard:** Intel DP35DP Original Motherboard
RAM: 2GB
**Graphics Card:** MSI nVIDIA GeFOrce 8800 GT 512MB PCI-Express *[No onboard VGA available]*
**Sound:** On Board (SigmaTel Codec)
**OS:** Ubuntu 8.04 Hardy Heron & Windows XP SP2
Monitor: CRT 17" Samsung

Issues: Graphics card is not recognized by Ubuntu. Enabling the nvidia "new" driver causes the screen to revert to 640x480. 

Xorg.conf detects it as generic Nvidia graphics card.
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:
"PCI device failed to allocate mem"----This message is seen if I edit Xorg.conf to correct screen resolution values. 
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:
"sudo dpkg-reconfigure xserver-xorg" does not configure or detect card properly. 
There are no options to set screen resolution and refresh rates or horizontal and vertical refresh frequencies of the monitor while running the above command in Hardy Heron.[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:



Manually editing xorg.conf crashes X on restart. 

3D acceleration is not properly working.



I had no issues on a previous system: Pentium 4 1.7GHz, Intel 845G Motherboard with GeForce 5700 AGP card running Ubuntu 7.10.

It used to work magnificently.[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:

---

### Post by harangdos on 2008-05-07
Asus motherboard m2a-vm series with ATI X1250 integrated griphics card... the graphics is the one that dont work

---

### Post by zorba_the_greek on 2008-05-07
Motherboard: MSI P965 F

I tried:
1) Ubuntu 6.06 LTS
2) Ubuntu 7.04 Feisty Fawn
3) Ubuntu 7.10 Gutsy Gibbon
4) Fedora 7
5) openSUSE 10.3 (could work, but with many problems)
6) Debian 4.0
7) Slackware (don't remember which one)
8) Vixta

nothing worked except for openSUSE 10.3

I also tried:
1) freeBSD 6.2 (worked with problems)
2) openBSD 4.1
3) trueBSD 0.9
4) dragonflyBSD 1.11
5) Solaris 10 OS

nothing worked except for freeBSD with problems

Conclusion: Don't buy this mobo, despite the fact that it's the best one with a P965 Chipset...

---

### Post by kpashok on 2008-05-08
[COLOR="Red"]I can't install ubuntu,kubuntu,edubuntu(6.06 LTS and 7.04) or any other linux like debian.
Configuration:
Core 2 Duo 6300
Intel G965RY
[/COLOR]

---

### Post by flowtron on 2008-05-08
On Feisty Fawn:
ALC662 - microphone remains silent, as yet no solution found.
I've tried compiling ALSA 1.0.16rc2 (including lib and utils (rc1 here, though)) myself but this only made it worse (read "no sound").

On Hardy Heron:
I was very happy when I tried the 8.04 (Hardy Heron) LiveCD and heard myself tapping the microphone .. now that I've had it installed for a couple of weeks and have been experimenting some more I'm sad to say : it still doesn't really work.
The ASRock/ALiveNF6 motherboard comes with 2 seperate jacks - front & back - for speakers and microphone ... I /can/ hear input coming through when jacked into either and having set the sound-settings appropriately.
But the quality is terrible and if I just try to use the audio-recorder to check capturing it only captures silence - yes, I've set the input to "Mic" (or "Mic Front") and have the channels un-muted and at full amp.
I've also tried running mumble (actually I did this first) .. but nobody could hear me ... it seems the microphone is still not configured properly :-/
Maybe some ~/.asoundrc stuff could help .. but sound-under-linux has never been easy for me to get to work .. and scourging the ALSA-site ([http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)) didn't really help at all.

---

### Post by jtappin on 2008-05-09
BusLogic Flashpoint SCSI adapters on 64-bit platforms

The BusLogic module loads but then fails to do anything because Flashpoint support is not enabled. (This CANNOT be rectified with a custom kernel as the code is not 64-bit clean -- and is unmaintained).

The same probably applies to big-endian platforms.

The card works just fine on 32-bit X86 architectures.

---

### Post by Pord on 2008-05-10
With hardy heron not with gutsy
1)Laptop
2)Acer
3)Aspire 2020
4)Doesnt recongnise graphics card acusing crashes when xserver starts making impossible to install from live cd and very unstable if at all usable from 7.10 upgrade. This is with opensource and fglrx drivers

---

### Post by makonis01 on 2008-05-10
1) laptop and external USB hard disc
2) Acer and Western Digital
3)Acer Aspire 5101 and WD My Book 500GB
4)I have this disc from my old windows, it has NTFS file system, but Ubuntu couldn`t mount the volume. It shows "unable to mount the volume WD".

---

### Post by Psychobudgie on 2008-05-11
1) Laptop
2) Hewlett Packard
3) 6032EA 
4) Broadcom Wireless doesn't work in Hardy. Worked in Feisty with ndiswrapper. No success with Hardy. USB ports do not work.

---

### Post by tad1073 on 2008-05-11
Ubuntu 8.04
Monitor
LG
Flatron L227WTG
Not in monitor list, doesn't go to powersave mode when idle. Using Generic Monitor in xorg.conf

---

### Post by free2useemail on 2008-05-12
A VIA Unicrome PRO IGP driver does not work. The Mouse has graphic issues displaying, and the special effects don't work any. Although Ubuntu 8.04 with KDE 3.5 works OK.

---

### Post by markbuntu on 2008-05-12
Radeon HD 3650 on Hardy 8.04

ATI proprietary driver implements 3D through mesa causing slow fps ~500-900. When using xserver-xgl to enable compiz fps slows to 90-150 making use impossible. Xv also has low fps. Xorg.0.log claims 2D acceleration is enabled but that is difficult to believe.

restricted driver from Ubuntu site crashes at will but has 2D acceleration to speed up crashing and other various random glitches

No 3D from any available driver.

All crash when running Firefox.

Put this card in the closet until some real drivers are implemented.

May, 23.2008
I take that back.Apparently there were some serious unfathomable problems with my previous installation because after a complete clean install this card works great with the restricted driver. Stable, no glitches. glxgears reporting fps around 5000. Compiz fusion fabulous.

---

### Post by Zer0Nin3r on 2008-05-12
1) Flatbed Scanner
2) Canon
3) Canoscan LiDE 90
4) Unsupported/Unrecognised
5) Ubuntu 8.04

---

### Post by Oxnigarth on 2008-05-13
.

---

### Post by dancer58 on 2008-05-13
I don't know if this is the right place but I have not had sound since I switched from Gutsy to Hardy. Here is a list of hardware:

linux 2.6.24-17
Ubuntu 8.04
mother board = Asus P5B
processor = Intel core 2 duo

--------------------------------------------------------------------------------------------

audio = Intel 82801H (on mother board)
   pci.product = '82801H (ICH8 Family) HD Audio Controller'

THIS IS FROM HWINFO:
31: PCI 1b.0: 0403 Audio device
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_8086_284b
  Unique ID: u1Nb.kURRCMIOEo3
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "ASUSTeK HD Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x284b "HD Audio Controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x81ec 
  Revision: 0x02
  Memory Range: 0xfebf8000-0xfebfbfff (rw,non-prefetchable)
  IRQ: 3 (no events)
  Module Alias: "pci:v00008086d0000284Bsv00001043sd000081ECbc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is not active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

Alsa.sh does not find a sound card

   !!Loaded ALSA module

   !!Soundcards recognised by ALSA
   --- no soundcards ---

   !!PCI Soundcards installed in the system
   00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family)  
       HD  Audio Controller (rev 02)

--------------------------------------------------------------------------------------------

Agere V.92 winmodem
video = nVidia G72 (GEForse 7300 LE)
2 hard drives
keyboard & mouse are USB
USB bluetooth BCM2045A

---

### Post by Tim Silver on 2008-05-14
Ricoh xd Card Disk Device (4in1)

Running Hardy Heron from external (USB) HDD on Dell Inspiron 9400 fitted with internal xD card reader. Had no luck with Dell - it would appear that there is no *nix driver for this device - at least, not available for download!

---

### Post by filip007 on 2008-05-14
Hi my first post ;)

LC Power ProLine 906S (very good cooling)
LC Power GP 550W
Intel DP35DP BIOS Update 0413
E6600
2GB DDR2 800Mhz
ATI HD3870
Other hardware standard...

My Report for Ubuntu 8.04 :KS

The sound only works when mixer is set to 100%.
Scanner don't work AGFA Snapscan e25... 

Xsane faild to open device
[http://slike.poglej.net/files/zz67pqc9f19v8a56v9jr.png]("http://slike.poglej.net/files/zz67pqc9f19v8a56v9jr.png")

---

### Post by &#1610;&#1587;&#1575;&#1585; &#1575;&#1604;&#1582;&#1601;&#1575;&#1580;&#1610; on 2008-05-15
hello and thank you 
i want drive for these device please
motherborad :gigabyte model :ga-8i865gme
graphic card :nivdia model; ge force4 5200
wireless card for the device below:
1- smcwpci-g  model no;99-012084-452
2- dlink dwl520g 

and thank you

---

### Post by vinchlet on 2008-05-15
1) Wireless WLAN lockup- chipset-ATI RS485MC/SB460
                         WLAN-MSI(RAL) MS-6877 802.11g Mini PCI
2) GQ (Frys brand)
3) NX-L515 Laptop (AMD Sempron 3200+)
4) Wireless locks up system , particularly when attempting network gui file transfer.  At lockup, the Numberpad lock light flashes
and all becomes locked; hard power boot is the only way to recover.

(NOTE)-USB Wireless dongle (AWL...standard) confirms the issue
as a malfunction of the onboard WLAN.

David Carter

---

### Post by Pakkanen on 2008-05-19
Using Ubuntu 8.04

Type of hardware: USB keyboard
Manufacturer: Logitech
Model: Y-BP62a
Issue: GDM freezes at random intervals. Recovery by restarting GDM.

---

### Post by sporkinum on 2008-05-21
> **brainstuff said:**
> My machine is running Ubuntu 7.10 64bit on AMD X2, 2Gb RAM, LG L204WT widescreen monitor over DVI, 1680x1050 native

Problem is AGP Sapphire x1950 Pro - getting black screen after login if I use any driver other than Vesa

Hardy heron, same card, different monitor, same problem. System only works with vesa driver.

Linux homer 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 05)
00:0a.1 Input device controller: Creative Labs SB Live! Game Port (rev 05)
00:0b.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 01)
00:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
01:00.0 VGA compatible controller: ATI Technologies Inc RV570 [Radeon X1950 Pro]
01:00.1 Display controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (secondary)

lsdev
Device            DMA   IRQ  I/O Ports
------------------------------------------------
0000:00:0a.0                 a000-a01f
0000:00:0a.1                 a400-a407
0000:00:0b.0                 a800-a81f
0000:00:0e.0                 b800-b87f
0000:00:10.0                 c000-c01f
0000:00:10.1                 c400-c41f
0000:00:10.2                 c800-c81f
0000:00:11.0                 4000-407f 5000-500f
0000:00:11.1                 0170-0177 01f0-01f7 0376-0376 03f6-03f6 cc00-cc0f
0000:01:00.0                   9000-90ff
acpi                      9
ACPI                             4000-4003     4004-4005     4008-400b     4010-4015     4020-4023
cascade             4
dma                          0080-008f
dma1                         0000-001f
dma2                         00c0-00df
e100                           a800-a81f
ehci_hcd:usb4            18
EMU10K1                  17    a000-a01f
emu10k1-gp                     a400-a407
eth0                     16
floppy              2     6  03f2-03f5 03f7-03f7
fpu                          00f0-00ff
i8042                  1 12
IO-APIC-edge            3 4
keyboard                     0060-006f
libata                14 15    0170-0177   01f0-01f7   0376-0376   03f6-03f6   cc00-cc0f
parport0                  7  0378-037a
PCI                          0cf8-0cff 9000-9fff
pic1                         0020-0021
pic2                         00a0-00a1
pnp                          0294-0297 04d0-04d1   4000-407f   5000-500f
rtc                       8  0070-0077
serial                       02f8-02ff 03f8-03ff
timer                     0
timer0                       0040-0043
timer1                       0050-0053
uhci_hcd                       c000-c01f   c400-c41f   c800-c81f
vga+                         03c0-03df
vt596_smbus                      5000-5007

---

### Post by shardtard on 2008-05-23
ati radeon hd 2400 pro
unbuntu 8.04
gotta use the generic vesa drivers

Shardtard

---

### Post by Sense on 2008-05-24
The motherboard Asus M3N78-EH works except for the onboard ehternet([https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/231162](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/231162)) and SATA([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/231159](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/231159)). I also couldn't get PCI ethernet cards to work, but they were very old and it could be their fault, but I'm not sure. When you try to boot your system with a SATA harddisk connected ata will get a 'qc timeout' and can't IDENTIFY it.

---

### Post by Hyper Tails on 2008-05-25
The only that doesen't work on my laptop is:
Atheros AR5007EG Wireless Network Adapter
I cannot get it working on my ubuntu 8.04 os But i can get it working on my vista home premium os (i used wubi)

My laptop is a acer Aspire 5715-4740

---

### Post by rekado on 2008-05-26
Haier A20 notebook
Intel T2370 @ 1.73GHz (Core Duo)
SiS M671 Mirage 3

[LIST=1]
[*]Ubuntu 8.04 64bit needed to be installed with options "noapic nolapic acpi=off vga=791", needs to be booted with "noapic acpi=off apm=power_off".
[*]OpenGL (3D) graphics driver unavailable (no Compiz)
[*]With self-compiled 2D driver from Chen Chao Yu at SiS (source under GPL license) videos don't play in full-screen, at boot-up the screen's brightness fades from faint to gleaming, showing a turquoise-grayish pale pattern with a cyan rectangle on the left bottom corner of the screen.
[*]CPU load spikes extremely high when doing nothing special but only moving windows.
[*]Sound is very soft; is normal when booting with pci=bios_irq but internet connection will fail and system will run very slowly with this option enabled.
[*]on boot-up, when attempting to reconfigure xserver and when executing displayconfig-gtk the following error occurs:```
FATAL: Error inserting battery (/lib/modules/2.6.24-16-generic/kernel/drivers/acpi/battery.ko): No such device
```
[/LIST]

---

### Post by sshlyk on 2008-05-29
Any Broadcom wireless (not supported by Vendor at all)

Any HP laptop based on AMD + NVidia + Broadcom wireless
(has glitchy ACPI, will not boot Ubuntu right out the box, needs some work around)

Guys, don't buy any hardware from Vendors who officially do not support Open Source.

---

### Post by sshlyk on 2008-05-29
> **Hyper Tails said:**
> The only that doesen't work on my laptop is:
Atheros AR5007EG Wireless Network Adapter
I cannot get it working on my ubuntu 8.04 os But i can get it working on my vista home premium os (i used wubi)

My laptop is a acer Aspire 5715-4740

Get Intel Wireless Card for $30 and replace it (it worked for me :) )

---

### Post by jackhe22 on 2008-05-30
Graphics Card
PNY Technologies
Nvidia 7600GS 8xAGP
Supported-Compiz Ready. (Only with Restricted/Proprietary Driver)

---

### Post by schmidtbag on 2008-06-01
1. AGP 4x Video card TV tuner combo
2. ATI
3. Radeon 7500 All-In-Wonder
4. No 3D or TV support of any kind no matter what you do

---

### Post by rjr1049 on 2008-06-04
1. Bluetooth Keyboard
2. Microsoft
3. Keyboard Elite for Bluetooth
4. It is impossible to connect this keyboard in 8.04. It is supported in 7.10.  This has been posted to the bug list wiki.

---

### Post by N3um0rin on 2008-06-14
Active XP-Pen tablet 

it only right clicks and the pointer wont move..i have a windows driver cd for it but the windows cd wont work and wine almost never works...can you guys make a driver for it..or tell me how to..=\

---

### Post by Mikamura on 2008-06-17
1. Mainboard + Graphic Card
2. ASRock + Nvidia / ATi
3. 775i65GV
4. Can only run in text mode with alternate disc install. When goes to graphic mode, screen goes blank like open the screen but not open the computer. Only happened when insert a graphic card into AGP slot, when use on board chipset, it can run normally.

---

### Post by lushden1988 on 2008-06-19
[img]http://i274.photobucket.com/albums/jj276/Shipcat/cpuz.jpg?t=1213886516[/img]

are my sound card and graphics card incompatible i have asked this in a new thread but have not heard anything back.

I am getting no sound through headphones, and i can't get the desktop effects to work or use my graphics card for anything


My laptop is a Hi-Grade VA250D

My motherboard is fic.

I have followed everything in this forum and now have lost sound completely i really need a step by step guide on what to do.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/184314](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/184314)

I am totaly *&#^$&@)!

Please someone help me im dual booting with Xp SP3

---

### Post by blackdalek on 2008-06-23
1)Type Of Hardware
Notebook running Ubuntu 8.04

2)Hardware Maker
Toshiba

3)Hardware Model
Tecra S1

4)Known Issue
Bluetooth not detected or working.
SD memory card reader not working.
TV-out not detected or working.
IRda port not working
Everything else appears to work.

---

### Post by ahbart on 2008-06-23
Card Reader delivered as part of a Medion pc model 8808. This card reader is part of the 5,25" front bay, including usb ports, audio, video and firewire. The card reader does not work at all!

1)Type Of Hardware
Card reader

2)Hardware Maker
C-Media

3)Hardware Model
CM-220
lsusb: ID 0d8c:5200 C-Media Electronics, Inc.

4)Known Issue
The card reader part does not work at all.

---

### Post by Trog on 2008-06-23
1. Router
2. Netgear
3. DG834G V2.0
4. DHCP will complete but the wired network will not work or will work intermittently after a reboot of the router. Works OK with IPV6 disabled on the desktop.

---

### Post by shonwein on 2008-06-30
Asus M2N-MX SE PLUS motherboard. 

nForce 430/Geforce 6150se . Just 640*480 resolution. No drivers fix yet this.

---

### Post by gamer625 on 2008-07-06
1.Gateway m-1625 laptop

2.AMD-Turion 62 X2 mobile technology TL-60

3.ATI-Radeon X1270

---

### Post by linuxnube on 2008-07-11
Running Hardy 8.04 on a Fujitsu T2010U.

Cannot get stylus working on the Wacom touchscreen.

Thanks.

---

### Post by Casper Hansen on 2008-07-16
Laptop:

Fujitsu-Siemens Amilo L1310G:

Ubuntu 8.04

Well, the CPU fan won't work so the system gets very hot and overheats. Also the graphic card (ATi Express 200 or something) is very lousy in Ubuntu.

---

### Post by Richard9795 on 2008-07-23
Dell Latitude C640
Intel Easy PC Camera
Camera shows every thing in a diffrent color in any app (eg. my face is green):confused:

---

### Post by Cyhawk on 2008-07-24
Version: Ubuntu 8.04 (all)
Name: x2Gen 19" Widescreen Monitor
Model: MW19R
Problem: According to a few posts, this monitor has a mistake in its table. It does not work at the native resolution of 1440x900 at anything other than 60hz refresh rate. Playing with xorg.conf will get it work with ONLY the nvidia drivers installed, however not correctly. (GDM (Blank until inside gnome), Videos (improperly scaled to 1024x768), Games (same as videos), anything requiring 3d acceleration will function improperly)

What's needed: Some sort of force resolution/refresh rate utility for both gnome and GDM =)

Windows has the same problem, until you change the refresh rate to 60hz, then it works perfectly fine.

---

### Post by cd\click!? on 2008-07-25
1)Type Of Hardware
motherboard

2)Hardware Maker
XFX

3)Hardware Model
 GeForce 8200

4)Known Issue
wont make it to the desktop from a live cd. loading bar appears does its job for a few then disappears. all other hardware worked on the previous motherboard, a gigabyte geforce 6100.

---

### Post by heiko_s on 2008-07-26
1)Type Of Hardware: Laptop
2)Hardware Maker: Dell
3)Hardware Model: Latitude D600
4)Known Issue: Ubuntu 8.04 Hardy - no out of box support for wireless router connection, no wired connection possible.

---

### Post by grss1982 on 2008-07-27
Ubuntu 8.04.1

1)Type Of Hardware: Motherboard
2)Hardware Maker: Inno3D
3)Hardware Model: SL7N73VM Link: [http://www.inno3d.com/products/motherboard/SL7N73VM.html](http://www.inno3d.com/products/motherboard/SL7N73VM.html)
4)Known Issue: Ubuntu can only detect the built-in sound (Realtek ALC883 HD Audio Codec), LAN (Marvell 88E8056 10/100/1000Mbps Ethernet Controller) & Video (GeForce 7050).  There are at least a dozen "Nvidia Corporation Unknown Device" readings when I use **lspci**.

BTW, the mobo is based on the **GeForce 7050 PV/nForce 630a** chipset.

---

### Post by video-video on 2008-08-01
You can also come to these websites to get more informations and you can be more familier with your mac.
:guitar::guitar::guitar:
[Mac DVD creator](http://www.dvdcreatorformac.com/index.htm),
[DVD Burner for Mac](http://www.dvdcreatorformac.com/dvd-burner-for-mac.htm), 
[DVD Ripper for Mac](http://www.dvdcreatorformac.com/dvd-ripper-for-mac.htm), 
[DVD Copy for Mac](http://www.dvdcreatorformac.com/dvd-copy-for-mac.htm),
[DVD Decryption for Mac](http://www.dvdcreatorformac.com/dvd-decryption-for-mac.htm), [DivX to DVD Converter for Mac](http://www.dvdcreatorformac.com/divx-to-dvd-for-mac.htm), 
[AVI to DVD Converter for Mac](http://www.dvdcreatorformac.com/avi-to-dvd-for-mac.htm), [DVD to iPod Converter for Mac](http://www.dvdcreatorformac.com/dvd-to-ipod-for-mac.htm).

---

### Post by dreadmeat on 2008-08-02
1)Type Of Hardware: CPU
2)Hardware Maker: intel
3)Hardware Model: 3.06Ghz HT pentium 4
4)Known Issue: xubuntu 8.04 very *unstable with hyper threading enabled, to the point of being unusable.
xubuntu 7.1 has no such issues that i observed.

i disabled hyper threading in my award bios and now my system works *very* well.


*thunar, firefox & epiphany freeze, xfce-session-logout can't be found, I/O error sr0 on reboot, unable to mount or burn cd/dvds reliably the list goes on...
but i will not.

---

### Post by soxs on 2008-08-02
REMOVED, useless..

---

### Post by ERName on 2008-08-06
1)Type Of Hardware: Laptop
2)Hardware Maker: Asus
3)Hardware Model: M50VM-A1 (probably -B1 as well because the hardware is identical except for the CPU speed)
4)Known Issue: Ubuntu i386 doesn't even install, x64 does BUT...

NO Compatibility (nothing works) for the following:
-Network Controller: Realtek, unknown model number
-Wifi Card: Some sources say Atheros AR928X, Vista identifies it as Intel 3945ABG. There is a sticker on the card itself that says Atheros, and the Vista drivers on the CD that Asus packaged with the computer lists itself as Atheros. (I'm inclined to believe that it's an Atheros AR928X)
-Sound: I believe it's Realtek integrated, but I'm not sure.
-Fingerprint Scanner: Unknown
-Webcam: Asus, unknown model

VERY LIMITED support for:
-Keyboard: Standard US key layout works, No hotkeys (somewhat expected)
-Touchpad/Mouse Buttons: "Media" and backlight functions are NOT available. The model of this touchpad is not known. Standard Mouse functions are available.
-Video: Nvidia 9600M GS... Standard drivers seem to work, but no advanced functions (higher than 800X600 resolutions) are available. No Desktop effects can be enabled, etc. (Video has never worked out of the box for me in Ubuntu).

Completely Working:
-Basic power functions (And that's IT!)

Summary: Asus M50VM-A1 (and -B1) do NOT come close to working out of the box. Without network support, nothing can be forced to work either.

Praying for: 8.10 to fix these problems (or at least the network issues!!)

UPDATE: The standard linux kernel that comes with 8.10 alpha 3 (I don't know the version number... 2.6.24?) fixes the wired network problem. However, installing a kernel update to the next version (2.6.25?) breaks it again.

---

### Post by hellknight_mnd on 2008-08-08
Hardware :- Printer
Model :- HP 1018 LaserJet
Problem :- Ubuntu or any Linux distro doesn't detects it accurately... i mean they show it but can't print.. the cure to this solution is download a 10 MB software from HP which then downloads more software when run. The print quality after running all these softwares is not that good!!

---

### Post by caf@omen.com on 2008-08-09
1)Type Of Hardware   Audio Card
2)Hardware Maker    Creative
3)Hardware Model     Audigy 2
4)Known Issue[/B]   The mixer "capture" tab is blank
except for a check box for mic gain.  One would expect to
see items such as "aux 2", "line", or even "mic" with
sliders.

Audio playback and volume control work as expected.
This is with the current 386 Ubuntu Studio with
all the install items selected.

Some other distros show the Audigy 2 inputs but Ubuntu Studio is the
only distro that seems to run xlinrad at 96000 capture rate.

The same 386 Studio and xlinrad work perfectly on an Intel
dg33bu motherboard at 96000 and 16 or 24 bits.

---

### Post by twinkel1961 on 2008-08-11
Laptop Acer Extensa 5220 type 201G08Mi Mfg Date: KS 080424

WLAN CARD:
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
  (needed manual workaround with ndiswrapper)

IRDA PORT:
nsc-ircc 'PnP Device (NSC6001)' /sys/devices/pnp0/00:0a

NO SOUND AFTER Hibernate and standby

---

### Post by DraconPern on 2008-08-11
Canon CanoScan LiDE 70.  Plug in. doesn't work.

---

### Post by liam j dyer on 2008-08-14
[http://www.rewards1.com/index.php?referrer_id=89832](http://www.rewards1.com/index.php?referrer_id=89832)

rewards1 is a website where you fill out surveys for points from 0-4 each point is worth $1 and you can spend the money on what ever you want like a..ps3,ps2,psp,nintendo wii,ds,dildo if you really wanted :lolflag:

[http://www.xtremetop100.com/in.php?site=1132252565](http://www.xtremetop100.com/in.php?site=1132252565)
if you used the first link and liked it or using it then vote for it at the second link thanks XD

please vistit them and help me thank you XD

^)(

---

### Post by liam j dyer on 2008-08-14
[http://www.rewards1.com/index.php?referrer_id=89832](http://www.rewards1.com/index.php?referrer_id=89832)

rewards1 is a website where you fill out surveys for points from 0-4 each point is worth $1 and you can spend the money on what ever you want like a..ps3,ps2,psp,nintendo wii,ds,dildo if you really wanted :lolflag:

[http://www.xtremetop100.com/in.php?site=1132252565](http://www.xtremetop100.com/in.php?site=1132252565)
if you used the first link and liked it or using it then vote for it at the second link thanks XD

please vistit them and help me thank you XD

^









[http://www.rewards1.com/index.php?referrer_id=89832](http://www.rewards1.com/index.php?referrer_id=89832)

rewards1 is a website where you fill out surveys for points from 0-4 each point is worth $1 and you can spend the money on what ever you want like a..ps3,ps2,psp,nintendo wii,ds,dildo if you really wanted :lolflag:

[http://www.xtremetop100.com/in.php?site=1132252565](http://www.xtremetop100.com/in.php?site=1132252565)
if you used the first link and liked it or using it then vote for it at the second link thanks XD

please vistit them and help me thank you XD

^













[http://www.rewards1.com/index.php?referrer_id=89832](http://www.rewards1.com/index.php?referrer_id=89832)

rewards1 is a website where you fill out surveys for points from 0-4 each point is worth $1 and you can spend the money on what ever you want like a..ps3,ps2,psp,nintendo wii,ds,dildo if you really wanted :lolflag:

[http://www.xtremetop100.com/in.php?site=1132252565](http://www.xtremetop100.com/in.php?site=1132252565)
if you used the first link and liked it or using it then vote for it at the second link thanks XD

please vistit them and help me thank you XD

^



















[http://www.rewards1.com/index.php?referrer_id=89832](http://www.rewards1.com/index.php?referrer_id=89832)

rewards1 is a website where you fill out surveys for points from 0-4 each point is worth $1 and you can spend the money on what ever you want like a..ps3,ps2,psp,nintendo wii,ds,dildo if you really wanted :lolflag:

[http://www.xtremetop100.com/in.php?site=1132252565](http://www.xtremetop100.com/in.php?site=1132252565)
if you used the first link and liked it or using it then vote for it at the second link thanks XD

please vistit them and help me thank you XD

^



















[http://www.rewards1.com/index.php?referrer_id=89832](http://www.rewards1.com/index.php?referrer_id=89832)

rewards1 is a website where you fill out surveys for points from 0-4 each point is worth $1 and you can spend the money on what ever you want like a..ps3,ps2,psp,nintendo wii,ds,dildo if you really wanted :lolflag:

[http://www.xtremetop100.com/in.php?site=1132252565](http://www.xtremetop100.com/in.php?site=1132252565)
if you used the first link and liked it or using it then vote for it at the second link thanks XD

please vistit them and help me thank you XD

^

---

### Post by Der_Idiot on 2008-08-16
1) Built in Gigabit Ethernet controller
2) Marvel
3) Yukon 88E8057
4) Upon install ubuntu installer cannot detect network adapter, and lspci detects it but lists it as 'unknown'.

This is on Gateway's new P-7811 series laptop.

---

### Post by Hyper Tails on 2008-08-17
Me webcam

U-cam ne878

doesen't show any picture on the computer........
which sucks :(

---

### Post by dornik on 2008-08-18
Type Of Hardware - Laptop Audio

Hardware Maker - Sigmatel

Hardware Model -  - SigmaTel STAC9752

Known Issue - No sound through either speaker or headphones.

Ubuntu Version - 8.04 Hardy

---

### Post by johnehowe on 2008-08-18
I receive a BusyBox error (Initramfs) when trying to run from CD or install 8.04. I know the hardware is good so it has to be an incompatibility issue.


The hardware is a Dell PowerEdge 600SC minitower (Small shop server hardware) However, I have been using it as a XP desktop workstation for a few years now.



Dell PowerEdge 600sc
2400 Mhz Intel Processor
533 Mhz Bus
L2 cache: 512
640 MB Ram

---

### Post by johnehowe on 2008-08-18
8.04 is incompatible with a Dell PowerEdge 600sc minitower server. Marketed by Dell as a small shop server. I have been using it as an XP Desktop for years, and was wanting to convert it to a Ubuntu WS, but no-go......

Dell PowerEdge 600sc
2400 Mhz Intel Processor
533 Mhz Bus
L2 Cache: 512

---

### Post by quack on 2008-09-07
1) Scanner
2) Canon
3) CanoScan LiDE 600F
4) Not detected & not supported in Ubuntu 8.04. Can be driven by a Windows guest OS in VirtualBox 1.6.6

---

### Post by hijk867 on 2008-09-19
&#19994;&#29983;&#20135;&#20445;&#38505;&#31665;&#30340;&#21378;&#23478;,&#21697;&#31181;&#40784;&#20840;&#27454;&#24335;&#26032;&#39062;,&#20854;&#20013;&#21253;&#25324;:&#22681;&#22721;&#24335;&#20445;&#38505;&#31665;,&#21333;&#38376;[&#20445;&#38505;&#31665;](http://www.qnn.com.cn),&#21452;&#38376;&#20445;&#38505;&#31665;,&#21488;&#24335;&#20445;&#38505;&#31665;,&#33853;&#22320;&#24335;&#20445;&#38505;&#31665;&#31561;.&#25552;&#20379;&#19987;&#21033;&#20445;&#38505;&#26588;,&#23478;&#29992;[&#20445;&#38505;&#26588;](http://www.qnn.com.cn),&#21830;&#29992;&#20445;&#38505;&#26588;,&#23486;&#39302;&#20445;&#38505;&#26588;,&#25351;&#32441;&#20445;&#38505;&#26588;&#31561;.&#32477;&#23545;&#24046;&#24322;&#21270;&#20135;&#21697;,&#21344;&#23613;&#24066;&#22330;&#20808;&#26426;&#19987;&#19994;&#29983;&#20135;&#22269;&#26631;,&#32654;&#26631;,&#24503;&#26631;&#27861;&#20848;,&#30899;&#38050;&#27861;&#20848;,&#19981;&#38152;&#38050;[&#27861;&#20848;](http://www.flange316.com),&#21512;&#37329;&#38050;&#27861;&#20848;,&#22823;&#23567;&#22836;,&#19977;&#36890;,&#31561;&#31995;&#21015;&#31649;&#36947;&#37197;&#20214;&#22269;&#38469;&#31649;&#27861;&#20848;&#26631;&#20934;&#20307;&#31995;: &#22269;&#38469;&#19978;&#31649;&#27861;&#20848;&#26631;&#20934;&#20027;&#35201;&#26377;&#20004;&#20010;&#20307;&#31995;,&#21363;&#20197;&#24503;&#22269;DIN(&#21253;&#25324;&#21407;&#33487;&#32852;)&#20026;&#20195;&#34920;&#30340;&#27431;&#27954;&#31649;&#27861;&#20848;&#20307;&#31995;&#21644;&#20197;&#32654;&#22269;ANSI...3,&#33521;&#22269;&#21644;&#27861;&#22269;&#31649;&#27861;&#20848;&#26631;&#20934;,&#20004;&#22269;&#21508;&#26377;&#20004;&#22871;&#31649;[&#27861;&#20848;&#26631;&#20934;](http://www.flange316.com)&#26631;&#20934; &#32508;&#19978;&#25152;&#36848;,&#22269;&#38469;&#19978;&#36890;&#30340;&#31649;&#27861;&#20848;&#26631;&#20934;&#21487;&#27010;&#25324;&#20026;&#20004;&#20010;&#19981;&#21516;&#30340;,&#19988;&#19981;&#33021;&#20114;&#25442;&#30340;&#25214;modern abstrac..&#22312;&#38463;&#37324;&#24052;&#24052;&#25214;&#26412;&#22320;[modern abstract art](http://ohpaintings.com)&#19978;&#30334;&#22995;&#32593;&#35775;&#38382;&#36890;&#29992;&#32593;&#22336;modern abstrac..&#26356;&#22810;modern abstrac..&#22312;&#24935;&#32874;&#65292;&#24555;&#26597;&#30475;&#30475;modern abstrac..&#23567;&#35828;&#22312;&#36215;&#28857;&#20013;&#25991;&#32593;

---

### Post by SomedoodIV on 2008-09-19
Hareware Type: sound card (PCI card)
Hardware manufacturer: Creative Technology
HW model: Fatil1ty X-FI pro series (PCI edition)
Problems: Card is not even seen or detected (or used, since i have no sound at all) by Ubuntu 8.04 HH, cannot even install Creative's Linux drivers, i get the error in the terminal "no supported hardware detected". Running 64x Ubuntu, tried both increments of the drivers (32x and 64x) with no success.

---

### Post by celem on 2008-09-21
I have loaded Ubuntu 8.04 on my Biostar TF8200 A2+, also Mint and a few others trying to get it to work correctly. Sabayon Linux works the best on this motherboard. Ubuntu and Mint share the same video problem, including Ubuntu Intrepid Ibex Alpha 6. If you load the proprietary drivers as prompted by the little pop-up icon you will trash the system, requiring a reload. It screws up X so that the screen is just bands of colors. If you load the patch directly from nVidia as directed by nVidia's instructions, you will also trash the video. If you load the patch directly from nVidia but using the instructions found in the forum (See: [http://tinyurl.com/5yf56h](http://tinyurl.com/5yf56h)), the graphics works perfectly until the first update from Ubuntu when the video will again be trashed. I gave up and loaded Sabayon which handles the video and almost everything else perfectly. I say almost because Sabayon and EVERY Linux distribution, including Ubuntu, fail to properaly handle the ALC888S audio with the nVidia chipset as implemented on the Biostar TF8200 A2+. The result with every distribution is audio with scratchy noises and reverberation. I had to disable the on board ALC888S and install a sound card.

---

### Post by nDrewPJ on 2008-09-28
Hareware Type: TV-tuner
Hardware manufacturer: AverMedia
HW model: AverTV Hybrid NanoExpress
Problems: The tuner is not detected, only listed with "lspci" on 2.6.27 kernel. The AverMedia programmers said that they won't even try to make liux drivers for it.

Could somebody say where I can post some kind of request for support of this device?

---

### Post by PGHammer on 2008-09-28
> **johnehowe said:**
> 8.04 is incompatible with a Dell PowerEdge 600sc minitower server. Marketed by Dell as a small shop server. I have been using it as an XP Desktop for years, and was wanting to convert it to a Ubuntu WS, but no-go......

Dell PowerEdge 600sc
2400 Mhz Intel Processor
533 Mhz Bus
L2 Cache: 512

Does this server have integrated (onboard) graphics?  It also (if it does not have onboard graphics) may require proprietary graphics for best performance (that is still an issue iwth some ATI/nV/Intel graphics chipsets).

---

### Post by pennybright on 2008-09-28
> **Richard9795 said:**
> Dell Latitude C640
Intel Easy PC Camera
Camera shows every thing in a diffrent color in any app (eg. my face is green):confused:

Happened to me too...Have you find the solution other than buy new camera?

---

### Post by shwick on 2008-10-18
1)Type Of Hardware - Motherboard
2)Hardware Maker -Gigabyte
3)Hardware Model - ep45-ds3
4)Known Issue - won't boot, can't install

This model won't work with kernel versions less than 2.6.25, Hardy uses 2.6.24, in Intrepid it should be 2.6.27 so Intrepid should run fine. There could be a way to start with custom boot options or messing with RAID, but i haven't tried that.

---

### Post by dharmabum4732 on 2008-10-18
1) Motherboard
2)Asus
3)P5E3 Premium WiFi-AP @n Edition
4)The integrated wireless and Raid don't work

Tried on both ubuntu 8.04 (x32 and x64) and 8.10 (x64)

---

### Post by ash05 on 2008-10-31
PCI sound card
Montego II
msi rs480 motherboard

[File sharing online,virtual file server storage,synchronize files offline]("http://www.nomadesk.com/")

---

### Post by yooden on 2008-10-31
Mainboard Intel DP35DP
CPU Intel E5200
NIC integrated Intel 82566DC
NIC Intel Pro 1000 PCI
GPU Gainward Bliss 9600GT
Plextor PX-716AL
Some cheapo DVD reader

Ibex amd64 installation freezes, live-CD option freezes upon reaching the Desktop.

FYI, I also tried two other options:
[LIST]
[*]Lenny amd64 installation fails because neither the opticals nor any NIC is found.
[*]FreeBSD 7.0 net install freezes during package download.
[/LIST]

The Gainward is actually my second choice, before that I tried a Matrox G550 DH. Neither me nor my (pretty knowledgeable) dealer could get the DP35DP/Matrox combo even to the boot screen.

---

### Post by TrendRat on 2008-11-01
Matrox AGP Parhelia 128 video card
Ubuntu 8.1

Worked fine under 8.04
I seem to be in an infinite loop once I upgraded to 8.10, can't get the video to display.

"Ubuntu is running in low graphics mode.  Your screen, graphics card and input device settings could not be detected correctly.  You will need to configure these yourself."

Click OK and get "What would you like to do?" choices are: 1)run in low graphics mode (which doesn't work when I select it, won't boot) 2) reconfigure graphics (which also does not work, as it just flashes the screen and wipes out my selection) and 3)Use your backed up configuration (result is same as 2 above).

My gawd, how tough is it to get a silly video card to work on a system that previously ran flawlessly?????

So the machine won't boot.  Can't restart, as it sometimes instructs me to do.  Only hard reboot works, after which the machine either hangs or throws me back into the infinite loop.

---

### Post by fifthconspiracy on 2008-11-04
Motherboard Incompatibility:

Asus P5Q-EM motherboard (Intel G45 chipset) on Intrepid 8.10

Sound does not work with an Nvidia Card in the PCI-E Slot, Remove the Nividia card and switch to on-board video and the sound works.

---

### Post by D.D.R. on 2008-11-05
Graphics Card
ASUS EAH3650 (ATI Radeon HD3650) - AGP 8x
Ubuntu v8.10 (intrepid)

When booting (after several screen flashes) I see a message saying the graphics card has failed to initialize. In order to get to the desktop I have to run in low-graphics mode.

---

### Post by ua6icab7 on 2008-11-06
Hot Promotion Storm of [WOW Gold](http://www.gold4power.com/) is Sweeping fiercely all around! Recently,we have tailored the unique World of Warcraft gold promotion for our valued customers.You could feel surprised that our [WoW gold](http://www.gold4power.com/) price are the cheapest on all the servers,especially on US server!Purchasing cheap WoW Gold from Gamelee.com is 100% safe; your account will not be suspended or banned for purchasing World of Warcraft Gold from us. Perfect Runescape Summoning! Recently we are offering the new skill of Runescape--Summoning.For all our valued Runescape Fans,it's no doubt that could be an unparalleled news.Do you want to miss this new skill?That can make you weather all the chanllenge and become the big cheese in Runescape!Plz trust us that our price is depend on the market,even cheaper than others,we will never set it random !Let's enjoy the hot storm you have never been to!

---

### Post by PGHammer on 2008-11-06
ASUS P4C800-E Deluxe (likely also applies to all other Intel 875P/ICH5R chipset-based motherboards with onboard Intel PRO/1000CT gigabit Ethernet) - due to a known quirk with the e1000g module (also effects the e1000 module in the Ubuntu 2.6.27-7-generic kernel used in 8.10), the onboard Intel gigabit Ethernet adapter must be disabled during installation or operation with Intrepid Ibex (this bug is *not* present in Hardy Heron; therefore, I must recommend that Hardy Heron users with this motherboard, or any motherboard with onboard Intel gigabit Ethernet to avoid upgrading to Intrepid Ibex (when clean-installing Intrepid Ibex, remember to turn the onboard Ethernet off).
However, I can also report that the freshly-minted (just today, in fact) Creative X-Fi Linux driver *does* work in Intrepid Ibex (in fact, I'm using it), so the X-Fi (all variants except XtremeAudio) can be removed from the Hardware Incompatibility List for Intrepid Ibex.

---

### Post by PGHammer on 2008-11-06
> **SomedoodIV said:**
> Hareware Type: sound card (PCI card)
Hardware manufacturer: Creative Technology
HW model: Fatil1ty X-FI pro series (PCI edition)
Problems: Card is not even seen or detected (or used, since i have no sound at all) by Ubuntu 8.04 HH, cannot even install Creative's Linux drivers, i get the error in the terminal "no supported hardware detected". Running 64x Ubuntu, tried both increments of the drivers (32x and 64x) with no success.

There are new drivers for this series of card (literally new; dated today), that work with at least 8.10 32-bit; I'm using them myself.

Download them from [http://support.creative.com](http://support.creative.com).  (They are a 32/64-bit unified driver set.)

---

### Post by PGHammer on 2008-11-06
> **yooden said:**
> Mainboard Intel DP35DP
CPU Intel E5200
NIC integrated Intel 82566DC
NIC Intel Pro 1000 PCI
GPU Gainward Bliss 9600GT
Plextor PX-716AL
Some cheapo DVD reader

Ibex amd64 installation freezes, live-CD option freezes upon reaching the Desktop.

FYI, I also tried two other options:
[LIST]
[*]Lenny amd64 installation fails because neither the opticals nor any NIC is found.
[*]FreeBSD 7.0 net install freezes during package download.
[/LIST]

The Gainward is actually my second choice, before that I tried a Matrox G550 DH. Neither me nor my (pretty knowledgeable) dealer could get the DP35DP/Matrox combo even to the boot screen.

This is part of a known issue with all versions of the Intel gigabit Ethernet controller (especially onboard gigabit);  however, it *only* affects Ubuntu 8.10 Intrepid Ibex; 8.04 (Hardy Heron) is not affected.  It's a kernel module-level bug that affects the 2.6.27 series of kernels with varying degrees of severity; unfortunately, Intrepid Ibex got hit the hardest, as no version of any Intel gigabit adapter or controller (either integrated or card-based) is usable.  Your options are really threefold:

1.  Disable/remove your Intel gigabit Ethernet and replace it with another Ethernet adapter.  (In my case, I went with a 3Com 3C905-TX.)

2. If running Hardy Heron, avoid upgrading to Intrepid Ibex.

3.  If an upgrade is in the cards, consider another distribution (such as openSuSE 11.0/11.1, which has patched their kernel against the issues I spoke of).

---

### Post by VictorR on 2008-11-07
Ubuntu Intrepid 8.10
USB ADSL modem SpeedTouch 330 rev.4.
The modem worked fine until I upgraded to Intrepid. It doesn't work at all with new  kernel 2.6.27. I can neither see USB devices with "lsusb" (it hangs), nor navigate to /dev/bus/usb folder (Nautilus hangs).
The  only solution I have found so far is to boot the kernel from Hardy (2.6.24).

---

### Post by j0nny55555 on 2008-11-08
Re: Desktop Hardware Incompatibility List.
1)Type Of Hardware - RAID Card
2)Hardware Maker - Promise
3)Hardware Model - SuperTrak EX8650 SATA/SAS
4)Known Issue - Installs, Boots, Yet after about 800 MBs to 1.5 GBs of data have been copied or the system has ran for about three days, the kernel panics.  Here is my typed version of the kernel panic.  There is a bit more to the message as shown by my "..." and it involves too many registers to try to type it all out, but if someone wanted me to, I'd be happy to take a photo with my digi and send it.

tty1 (screen - console)
```
Call Trace:
<IRQ>  [<ffffffff8815349d>]  :stex:stex_mu_intr+0xdd/0x500
...
Kernel panic - not syncing: Aiee, killing interrupt handler!
```
kern.log
```
Nov  7 23:18:32 mars kernel: [277144.326658] stex(0000:06:00.0): aborting command
Nov  7 23:18:32 mars kernel: [277144.326664] sd 8:0:0:1: [sdc] CDB: Write(10): 2a 00 09 13 f1 df 00 01 00 00
Nov  7 23:39:35 mars kernel: [278405.068848] stex(0000:06:00.0): aborting command
Nov  7 23:39:35 mars kernel: [278405.068856] sd 8:0:0:1: [sdc] CDB: Write(10): 2a 00 0e 01 38 87 00 01 00 00
Nov  8 01:36:02 mars kernel: [285380.651948] stex(0000:06:00.0): aborting command
Nov  8 01:36:02 mars kernel: [285380.651955] sd 8:0:0:1: [sdc] CDB: Write(10): 2a 00 09 67 46 ff 00 01 00 00
Nov  8 04:36:33 mars kernel: [296193.672356] stex(0000:06:00.0): aborting command
Nov  8 04:36:33 mars kernel: [296193.672363] sd 8:0:0:1: [sdc] CDB: Write(10): 2a 00 26 c3 85 cf 00 01 00 00
Nov  8 04:51:27 mars kernel: [297086.325160] stex(0000:06:00.0): aborting command
Nov  8 04:51:27 mars kernel: [297086.325167] sd 8:0:0:1: [sdc] CDB: Write(10): 2a 00 1f 31 a9 ef 00 01 00 00
```

---

### Post by sc0tt10 on 2008-11-08
Nvidia GeForce 6100 integrated graphics chip

when I tried to install 8.10 it installed ok but when it attempted to boot up after the splash screen the display just changes to a thin line on my 17' TFT Monitor, yet with 8.04 it works a treat.

---

### Post by 081103jk on 2008-11-10
&#26032;&#19968;&#20195;&#28070;&#26222;&#30005;&#35805;&#24405;&#38899;&#20202;&#26159;&#20197;&#36229;&#22823;&#35268;&#27169;&#26032;&#19968;&#20195;&#28070;&#26222;&#30005;&#35805;&#24405;&#38899;&#20202;&#26159;&#20197;&#36229;&#22823;&#35268;&#27169;&#35821;&#38899;&#22788;&#29702;&#22120;&#65292;&#38598;&#25104;&#30005;&#36335;&#20648;&#23384;&#22120;&#20026;&#20027;&#35201;&#20803;&#20214;&#26500;&#25104;&#30340;&#20840;&#25968;&#30721;&#30005;&#35805;&#24405;&#38899;&#20202;&#65292;[**&#30005;&#35805;&#24405;&#38899;&#35774;&#22791;**](http://www.googlejk.cn/dhlysb.htm)&#20855;&#26377;&#38450;&#23576;&#12289;&#38450;&#28526;&#12289;&#20351;&#29992;&#23551;&#21629;&#38271;&#31561;&#20248;&#28857;&#12290;&#20013;&#25991;&#23631;&#24149;&#28082;&#26230;&#26174;&#31034;&#65292;[**&#30005;&#35805;&#24405;&#38899;&#35774;&#22791;**](http://www.googlejk.cn/dhlysb.htm)&#21487;&#23454;&#29616;&#21452;&#24037;&#22810;&#36335;&#20449;&#21495;&#21516;&#26102;&#24405;&#38899;&#65292;&#24405;&#38899;&#26102;&#38388;&#38271;&#65292;[**&#30005;&#35805;&#24405;&#38899;&#35774;&#22791;**](http://www.googlejk.cn/dhlysb.htm)&#30701;&#21017;70&#23567;&#26102;&#65292;&#38271;&#21017;&#25968;&#21315;&#23567;&#26102;&#65292;[**&#30005;&#35805;&#24405;&#38899;&#35774;&#22791;**](http://www.googlejk.cn/dhlysb.htm)]&#20855;&#26377;&#25353;&#38190;&#25805;&#20316;&#12289;&#24555;&#36895;&#26597;&#35810;&#12289;&#24555;&#36895;&#25918;&#38899;&#12289;&#35760;&#24405;&#23436;&#25972;&#12289;&#26174;&#31034;&#20840;&#38754;&#65288;&#25918;&#38899;&#26102;&#65292;&#21516;&#27493;&#26174;&#31034;&#24405;&#38899;&#26102;&#30340;&#26631;&#20934;&#26102;&#38388;&#20449;&#24687;&#65289;&#12289;&#23494;&#30721;&#38145;&#23450;&#31561;&#29305;&#28857;&#12290;&#35813;&#24405;&#38899;&#20202;&#21487;&#24191;&#27867;&#24212;&#29992;&#25919;&#24220;&#12289;[**&#30005;&#35805;&#35821;&#38899;&#21345;**](http://www.googlejk.cn/dhyyk.htm)&#38081;&#36335;&#12289;&#20844;&#23433;&#12289;&#33322;&#31354;&#12289;&#27700;&#21033;&#31561;&#22330;&#25152;&#12290;&#65292;&#38598;&#25104;&#30005;&#36335;&#20648;&#23384;&#22120;&#20026;&#20027;&#35201;&#20803;&#20214;&#26500;&#25104;&#30340;&#20840;&#25968;&#30721;&#30005;&#35805;&#24405;&#38899;&#20202;&#65292;&#20855;&#26377;&#38450;&#23576;&#12289;&#38450;&#28526;&#12289;&#20351;&#29992;&#23551;&#21629;&#38271;&#31561;&#20248;&#28857;&#12290;&#20013;&#25991;&#23631;&#24149;&#28082;&#26230;&#26174;&#31034;&#21487;&#23454;&#29616;&#21452;&#24037;&#22810;&#36335;&#20449;&#21495;&#21516;&#26102;&#24405;&#38899;&#65292;&#24405;&#38899;&#26102;&#38388;&#38271;&#65292;&#30701;&#21017;70&#23567;&#26102;&#65292;&#38271;&#21017;&#25968;&#21315;&#23567;&#26102;&#65292;&#20855;&#26377;&#25353;&#38190;&#25805;&#20316;&#12289;&#24555;&#36895;&#26597;&#35810;&#12289;&#24555;&#36895;&#25918;&#38899;&#12289;&#35760;&#24405;&#23436;&#25972;&#12289;&#26174;&#31034;&#20840;&#38754;&#65288;&#25918;&#38899;&#26102;&#65292;&#21516;&#27493;&#26174;&#31034;&#24405;&#38899;&#26102;&#30340;&#26631;&#20934;&#26102;&#38388;&#20449;&#24687;&#65289;&#12289;&#23494;&#30721;&#38145;&#23450;&#31561;&#29305;&#28857;&#12290;&#35813;&#24405;&#38899;&#20202;&#21487;&#24191;&#27867;&#24212;&#29992;&#25919;&#24220;&#12289;&#38081;&#36335;&#12289;&#20844;&#23433;&#12289;&#33322;&#31354;&#12289;&#27700;&#21033;&#31561;&#22330;&#25152;&#12290;

---

### Post by 081105jk on 2008-11-16
[**&#28145;&#22323;google&#20248;&#21270;**](http://www.jkw.name/szgoogleyh.htm)&#22914;&#20170;&#65292;[**&#28145;&#22323;google&#20248;&#21270;**](http://www.jkw.name/szgoogleyh.htm)&#24050;&#25104;&#38271;&#25104;&#20026;&#20855;&#26377;&#22404;&#26029;&#20248;&#21183;&#30340;&#20840;&#29699;&#24615;&#65292;&#31639;&#19978;&#23427;&#20026;Yahoo&#21644;AOL&#25552;&#20379;&#30340;&#25628;&#32034;&#26381;&#21153;&#65292;Google&#30446;&#21069;&#30340;&#20840;&#29699;&#24066;&#22330;&#21344;&#26377;&#29575;&#24050;&#36229;&#36807;80%&#12290;&#31616;&#21333;&#30340;&#32467;&#35770;&#26159;&#65292;&#22914;&#26524;&#20320;&#30340;&#32593;&#31449;&#22312;Google&#19978;&#19981;&#33021;&#33719;&#24471;&#33391;&#22909;&#30340;&#25490;&#21517;&#65292;&#37027;&#20040;&#20320;&#30340;&#32593;&#32476;&#33829;&#38144;&#31574;&#30053;&#23601;&#31639;&#26159;&#22833;&#36133;&#12290; &#35201;&#24819;&#38024;&#23545;Google&#26469;&#20320;&#30340;&#32593;&#39029;&#21644;&#36827;&#34892;&#30456;&#24212;&#30340;&#25512;&#24191;&#24037;&#20316;&#65292;&#39318;&#20808;&#24471;&#20102;&#35299;[**&#28145;&#22323;google&#20248;&#21270;**](http://www.jkw.name/szgoogleyh.htm)&#26159;&#20197;&#20160;&#20040;&#35268;&#21017;&#26469;&#35780;&#20272;&#19968;&#20010;&#32593;&#31449;&#23545;&#20110;&#26576;&#20010;&#29305;&#23450;&#20851;&#38190;&#35789;&#30340;&#25490;&#21517;&#20540;&#30340;&#12290;&#24403;&#28982;&#65292;&#38500;&#20102;&#19978;&#28023;Google&#20248;&#21270;&#30340;&#24037;&#31243;&#24072;&#65292;&#27809;&#26377;&#35841;&#30495;&#27491;&#30693;&#36947;&#36825;&#20010;&#31192;&#23494;&#65292;&#20294;&#26159;&#26377;&#20851;&#30740;&#31350;&#34920;&#26126;&#65292;&#24433;&#21709;[**google&#25490;&#21517;**](http://www.jkw.name/googlepaiming.htm)&#30340;&#22240;&#32032;&#20027;&#35201;&#26377;&#22914;&#19979;&#19977;&#20010;&#26041;&#38754;&#65306;[**&#28145;&#22323;google&#20248;&#21270;**](http://www.jkw.name/szgoogleyh.htm)  [IMG]http://www.jingke.org/img/logo.gif[/IMG]

---

### Post by dhay on 2008-11-16
Hello

Recently I've acquired an Asus X50GL/F5GL. I tried to install ubuntu 8.10 but it tries to start running and stop in the middle of the live-session(leaving the screen in black). I tried to install ubuntu 7.04, 7.10 and 8.04. Now i'm running with 8,04 but I had to install it for 4 times and I did it with the dvd version at the end(it always fails saying that it couldn't read some blocks). 

When I had it installed I updated and it stop running. So I put the ubuntu cd and I ran it in text-mode and put the option "recover X". After that it runs another time. 

The main problem is that it doesn't recognise the wifi, neither the graphical chipset, nor the sound-card. It happens in all the distributions I tried(how ubuntu doesn't run I tried to install debian(sarge, etch...), knoppix, fedora,mandriva and centOS(all of them in the latest versions excepting knoppix that was the ver 5.3.1). Some of them like knoppix and debian broke when try to install the dvd driver(The same happens when I try to test the laptop with Hiren's boot, I can't do anything because none of the drivers included is able to manage the dvd device).

I sent the automatic Test of Hardware included in ubuntu 8.04, but I preffer to explain here what happens, because I suposse I will not be the unic with this problem(But if you know that somebody installed ubuntu 8.10 in a laptop like this , please, tell me and I will go fast to change it to the store(but I tested the memory, the hard disc(with two programs) and I did some global test with sisoft Sandra and it seems to run ok).

The web page of this laptop is:

[http://www.asus.com/products.aspx?l1=5&l2=24&l3=477&l4=0&model=2575&modelmenu=1](http://www.asus.com/products.aspx?l1=5&l2=24&l3=477&l4=0&model=2575&modelmenu=1)

Here the computer characteristics:

[http://www.asus.com/products.aspx?modelmenu=2&model=2575&l1=5&l2=24&l3=477&l4=0](http://www.asus.com/products.aspx?modelmenu=2&model=2575&l1=5&l2=24&l3=477&l4=0)

In my case is:

Pentium T3200 (2.0ghz dual core).
 
Thanks for your attention :)

dhay

---

### Post by graham_two_dot_oh on 2008-11-21
HP dc7900 desktop PC.  Ubuntu 8.10. Kernel 2.6.27-7-generic.

1 CPU runs at 100% reading /proc/kmsg.  Getting constant
warn_on_slowpath messages, useful looking stacktrace functions are: warn_on_slowpath, hrtimer_get_next_event, tick_notify.

Tried disabling 'run time power management' in the bios, didnt help.

Presumably /var/log/messages will fill the disc.

---

### Post by Scunizi on 2008-11-21
> **cd\click!? said:**
> 1)Type Of Hardware
motherboard

2)Hardware Maker
XFX

3)Hardware Model
 GeForce 8200

4)Known Issue
wont make it to the desktop from a live cd. loading bar appears does its job for a few then disappears. all other hardware worked on the previous motherboard, a gigabyte geforce 6100.

This board now works with the latest Intrepid kernel.  Nvidia graphics card is slow on screen redraws with the 177 driver.

---

### Post by pete25r on 2008-11-23
I've tried installing 8.10 (both CD and DVD)on an HP XE3 Omnibook laptop.
When booting to the CD everything works. I tried both default and then the failsafe install. Both times the install program functions correctly everything seems normal. After its all done and is rebooted, it looks like everything is fine. POST is normal, some text info, then it comes up with the pre-login screen colors, the start-up audio plays, the cursor changes from the pointer to the round one(screen goes black but still cursor), and thats where it stops. The round cursor stops its rotation and it just sits there, no hard drive light blinking or anything. The mouse will move the cursor. If I hit the power button there is some activity but it doesn't power down.

Video card in laptop is an Intel 82830, not sure how much ram it has.

---

### Post by stoian on 2008-11-25
For two years now my main o/s is Linux, but, alas, I cannot uninstall Wind0ze because I can't make my scanner work.

It is a scanner made by Canon, the model is: CanoScan N 340P.
It seems from the documentation I've read, that it should be supported, but XSANE starts scanning, and then it stops after one inch, and hangs there indefinitely. I have to kill the XSANE application.

I'm now using Ubuntu 8.04 Hardy Heron.

---

### Post by Scunizi on 2008-11-25
Stoian,  My Microteck Scanmaker 5950 is totally nonfunctional in Ubuntu or any other linux for that matter.   I run win2kpro in a vbox vm to give me access to it.  At least I don't have to reboot into my other partiton of winxp to use it..

---

### Post by valeriki on 2008-11-26
1)Type Of Hardware: Webcam
2)Hardware Maker:   Logitech
3)Hardware Model:   QuickCam Fusion
4)Known Issue:      Not detected by Ubuntu 8.10

---

### Post by miket3115 on 2008-11-26
Intel D945GTP board
Microsoft Lifecam 3000vx
Ubuntu 8.10 64

Can not get the microphone on this web cam or any microphone that I plug in to work.

---

### Post by TrendRat on 2008-12-03
Since I whined about 8.10 not running nicely with my Matrox Parhelia video card, I thought I should post this update.

I yanked the Matrox out, replaced it with an nVidia XFX GeForce 7600GS (about $80 mail order).  Wow.  The machine booted up by itself!!  I didn't have to baby it through the boot process - it actually worked, had the correct screen resolution and everything.  No more wild green and orange abstractions on the screen.  And then.....in a most user-friendly way.....it told me I needed to upgrade to the restricted nVidia drivers.  After I got back in my chair, I did have to look up a post on how to properly enable the drivers, but it was a piece of cake.

So thanks, nvidia and Ubuntu people.:KS  

And I sincerely wish a most hideous pox upon the Matrox company.:evil:

---

### Post by sahmed001 on 2008-12-04
Scanner
Canon
LiDE 100

lsusb shows that it is mounted but sane doesn't recognize it.

---

### Post by happyenduser on 2008-12-05
[COLOR=Red]1) Flatbed USB Scanner 
2) Canon 
3) CanoScan LiDE 90 
4) Unsupported/Unrecognized 
5) Ubuntu 8.04[/COLOR]

---

### Post by Jenske on 2008-12-08
Not recognised by Ubuntu 8.10: Iomega external hard disk on usb drive (Iomega Prestige 500 Gbyte).
It CAN be mounted, but only using fstab-adjustments (see elsewhere on this forum).

---

### Post by Matt-Del on 2008-12-10
description: VGA compatible controller
       product: 771/671 PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 10
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=0

Does not work because it does not support OpenGL

---

### Post by Truckerpunk on 2008-12-10
Soundblaster Live CT4830 with Ubuntu 8.10. Have really tried everything to make this work, but without luck. Don't go there!!!! Had a minor breakthrough where the ststem didn't freeze right after booting, but after minutes instead... Woohoo!! But it generally just makes your system freeze. I have no problem when removing the soundblaster Live card and using the onboard card(other than it doesn't support multiple audio playback at the same time :(). Well just have to miss out on multiple audio playback, won't go back to Windows. But really don't think you will ever get a stable Ubuntu-system with s Soundblaster Live-card... Sadly. Can anyone recommend a soundcard that they haven't had ANY trouble with while running Ubuntu? Would be sweet to get sound playback working perfectly.

---

### Post by pvossen on 2008-12-25
IBM Clone Computer pentium 4
nvidia chip
Gateway VX900 Monitor

Gateway VX900 monitor does is not configured correctly by
new monitor detection. Old xorg and display config worked
correctly. I have reverted back to 8.04 Hardy.

Two computers Intrepid is working with new monitors, older
monitors an issue. More work needs to be done to insure
older monitors work correctly, as many of us linux users 
manipulate a lot of devices.



> **frodon said:**
> [B]Welcome To The Desktop Hardware Incompatibility List.
[/B]
The purpose of this thread is for you, the user, to post what hardware/hardware combination don't work with your desktop Ubuntu install. 

Everyone is welcome to post here, as long as it is hardware related data. For help with hardware problems, please use the standard procedure of searching the forums, and starting your own thread for assistance if no answer is found.

**_Give detailed explanations when reporting incompatible hardware including the version of ubuntu you use._**

**Also Do not post any lspci outputs in this thread as they will be removed with out question.**

[B]Please Only List
1)Type Of Hardware
2)Hardware Maker
3)Hardware Model
4)Known Issue[/B]

[COLOR="Red"]***NOTE* This thread is exclusively for the listing of incompatible hardware. Any idle chatter or unrelated posts will be moved/removed accordingly. *NOTE***[/COLOR]

Thank you.

**PS: the old incompatibilty list thread can be found here and will remain closed** :
[http://ubuntuforums.org/showthread.php?t=207916](http://ubuntuforums.org/showthread.php?t=207916)

---

### Post by gabylastar on 2008-12-26
Hello,

I have a Notebook : 
Manufacturer : Fujitsu-Siemens
Model : Amilo Xi 1554

Configuration :
Intel Core 2 Duo T7200
Chipset : Intel ICH7-M
2GB Ram DDR2
Screen : 1920x1200
ATI Mobility Radeon X1900
Raid controller VIA VT6421
Sound card : Intel HDA ICH7-M (I think, it could also be a realtek ALC885...)
Wifi : Intel 3945a/b/g
Network card : Realteak RTL-8169 10/100/1000 

There is some problems with Ubuntu 8.04 (maybe not only this version, and probably not only Ubuntu...)
- My fake raid 0 doesn't permit any normal installation of ubuntu, whether you use the normal or alternate CD. You must be very lucky to install Ubuntu on it. I tried to follow some tutorials about it but every failed. Especially for the Grub step.

- There is no good driver for the Mobility X1900, so the 3D functionalities and all the effects are not available.

- The sound actually is coming from the internal speakers and line-out in same time !!

- The wheel to change the volume doesn't work at all.

- Any multimedia button doesn't work.

Otherwise it run smoothly.

---

### Post by RJARRRPCGP on 2008-12-26
> **Matt-Del said:**
> description: VGA compatible controller
       product: 771/671 PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 10
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=0

Does not work because it does not support OpenGL

PCIE? Then it's likely just a missing driver.

---

### Post by user_ex on 2008-12-29
1)Laptop
2)Toshiba
3)Satellite L305D-S5895
4)Never comes out of Suspend/Hibernate

The rest of the hardware works fine with some tweaks ([http://ubuntuforums.org/showthread.php?t=1024443&highlight=toshiba+l305d](http://ubuntuforums.org/showthread.php?t=1024443&highlight=toshiba+l305d)).

---

### Post by Tweenk on 2008-12-30
Pentagram USB Audio card P1311, ID from lsusb: 1130:f211 Tenx Technology, Inc. - sound playback works, but volume jumps between mute and very loud when changing master volume from 6% to 7%, and doesn't respond to any other changes in volume controls.

There are very similar cards (pendrive form factor) based on chips from different manufacturers - a second card of the same type I tried was based on 04f3:0a11 Elan Microelectronics Corp. chip and the volume control worked, but the settings on the low end of the scale were very coarse - 0-20% sounded the same, as well as 20-30%.

Tested on Ubuntu Intrepid.

---

### Post by Tweenk on 2008-12-30
> **gabylastar said:**
> 
- The sound actually is coming from the internal speakers and line-out in same time !!

Have you enabled headphone jack sense? IMO this should be enabled by default, because it causes no end of confusion.

---

### Post by Leo.F on 2009-01-02
SAS (Serial Attached SCSI) port on ASUS P6T Deluxe Motherboard (Core i7)

Fujitsu MBA3300 MBA3147RC 147GB 15000 RPM 16MB Cache SAS Hard Drive connected to the above SAS port

When installing Intrepid the drive is not recognized by the partitioner so it's not possible to install Ubuntu to that Drive. Have tried Live CD and Alternate CD installs to no avail.

This seems to be an issue with the Linux Kernel as described in this bug report:

[https://bugzilla.redhat.com/show_bug.cgi?id=474482](https://bugzilla.redhat.com/show_bug.cgi?id=474482)

And might have been fixed for the 2.6.28 release of the Kernel as per this post from the Linux Kernel Archive:

[http://lkml.indiana.edu/hypermail/linux/kernel/0812.2/02255.html](http://lkml.indiana.edu/hypermail/linux/kernel/0812.2/02255.html)

The above reports reference a Seagate Hard Drive, but since I'm also getting the same problem with a Fujitsu Drive, it must be the SAS port controller.

---

### Post by user11 on 2009-01-02
creative labs CT4750 sound card is DOA, with regards to Xubuntu (8.02.1/8.10) that is. Back to windows 98 for me.

Update

Scratch that, there was a faulty solder joint on the output jack. Touched it up this morning and works like a charm.

---

### Post by cprofitt on 2009-01-03
ASUS
Laptop
ASUS X83Vm-X1
Incompatible DVD drive, intermittent failures to boot up and shutdown

---

### Post by RealG187 on 2009-01-04
> **PrivateVoid said:**
> ASUS
Laptop
ASUS X83Vm-X1
Incompatible DVD drive, intermittent failures to boot up and shutdown

Can you report laptops here?

---

### Post by Joeb454 on 2009-01-04
> **RealG187 said:**
> Can you report laptops here?

Given this thread is in the Hardware & Laptops forum, I'm sure that would be fine.

At the end of the day, incompatible hardware is exactly what it says, and a more comprehensive list would be better.

---

### Post by jonhann on 2009-01-05
Dear All,

I have a Sony Vaio VGN TX-26GP.
Intel Pentium M Processor ULV 733 (1.10Ghz)
1 GB DDR2; Bluetooth; Wireless Lan.

My Problems:

1) Unable to operate the DVD/Cd Rom.

2) Unable to use Skype for video conferencing.(I guess the sound and video's drivers are in place.)

I'm not a technical guy for this so is there anyone out there can help ?

Very urgent~! Thank You

---

### Post by RealG187 on 2009-01-05
> **Joeb454 said:**
> Given this thread is in the Hardware & Laptops forum, I'm sure that would be fine.

At the end of the day, incompatible hardware is exactly what it says, and a more comprehensive list would be better.

Okay I was confused, the thread title says desktop, and by that I thought it meant "tower" computers, as in not laptops.

However, I learned that it meant desktop as in not server. As in any normal computer that uses the "Desktop Install" of Ubuntu, by desktop install it means not server.

So Desktop PCs and Laptops may be posted here as long as they aren't servers.

In that case I have something to report.

[http://ubuntuforums.org/showthread.php?t=766529&page=19](http://ubuntuforums.org/showthread.php?t=766529&page=19)
Okay my AtherOS AR5007 didn't work in Ubuntu. I got it working by taking [this tar file]("http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/"), extracting it. Then changing to the extracted folder and typing:

```
make
sudo make install
modprobe ath_pci
```
then restarting.

This was on 8.04 and 8.10.

By reporting this, is it possible that in 9.04 the AR5007 will work out of the box, like could they implement the driver I posted so it just works?

---

### Post by Ripose on 2009-01-07
**1)Type Of Hardware : **Mercury 141 Key Keyboard +scroll-wheel[B]
2)Hardware Maker : [/B]Mercury[B]
3)Hardware Model : [/B]Unknown[B]
4)Known Issue : [/B]Only the standard 101 keys function[B]
5) OS : [/B]Ubuntu 8.10
I have been unable to find ANY Linux drivers for this keyboard. :(

---

### Post by Dialog287 on 2009-01-08
[http://refoweb.net?p=40342]("http://refoweb.net?p=40342")

---

### Post by phamtieugiao on 2009-01-09
My laptop is NEC E6500.
Problem: Keyboard and touchpad. But external USB keyboard and mouse work fine.

---

### Post by user11 on 2009-01-11
On all Ubuntu versions:

Serial mice not working.

256-P1-N399-LX geforce 6200 video card. Card recognized and used, you can even install drivers, but it keeps booting into low graphics mode no matter what, and nvidea settings menu states that there is no driver in use.

Everything works fine in windows XP.

This was on a dell dimension xps d333 and on a compaq presario 5030, both with a pre 2000 bios.
Bios updated on both systems, still no luck.

Note: sound doesn't work either, but I haven't had the time to look up the chipsets.

---

### Post by galv on 2009-01-11
> **dhay said:**
> Hello

Recently I've acquired an Asus X50GL/F5GL. I tried to install ubuntu 8.10 but it tries to start running and stop in the middle of the live-session(leaving the screen in black). I tried to install ubuntu 7.04, 7.10 and 8.04. Now i'm running with 8,04 but I had to install it for 4 times and I did it with the dvd version at the end(it always fails saying that it couldn't read some blocks). 

When I had it installed I updated and it stop running. So I put the ubuntu cd and I ran it in text-mode and put the option "recover X". After that it runs another time. 

The main problem is that it doesn't recognise the wifi, neither the graphical chipset, nor the sound-card. It happens in all the distributions I tried(how ubuntu doesn't run I tried to install debian(sarge, etch...), knoppix, fedora,mandriva and centOS(all of them in the latest versions excepting knoppix that was the ver 5.3.1). Some of them like knoppix and debian broke when try to install the dvd driver(The same happens when I try to test the laptop with Hiren's boot, I can't do anything because none of the drivers included is able to manage the dvd device).

I sent the automatic Test of Hardware included in ubuntu 8.04, but I preffer to explain here what happens, because I suposse I will not be the unic with this problem(But if you know that somebody installed ubuntu 8.10 in a laptop like this , please, tell me and I will go fast to change it to the store(but I tested the memory, the hard disc(with two programs) and I did some global test with sisoft Sandra and it seems to run ok).

The web page of this laptop is:

[http://www.asus.com/products.aspx?l1=5&l2=24&l3=477&l4=0&model=2575&modelmenu=1](http://www.asus.com/products.aspx?l1=5&l2=24&l3=477&l4=0&model=2575&modelmenu=1)

Here the computer characteristics:

[http://www.asus.com/products.aspx?modelmenu=2&model=2575&l1=5&l2=24&l3=477&l4=0](http://www.asus.com/products.aspx?modelmenu=2&model=2575&l1=5&l2=24&l3=477&l4=0)

In my case is:

Pentium T3200 (2.0ghz dual core).
 
Thanks for your attention :)

dhay

I have that laptop, I've installed Linux Mint (Based on Ubuntu 8.10) and I can work with the laptop, but the brightness and battery are not working properly. Right now I'm hopping for some kernel update to fix this :/

---

### Post by grimanda on 2009-01-11
Hi..., Newbie here, i have try to search on the forum, but still don't now what to do.., i have ubuntu 8.10 (dual with vista)

1. 5-1 integrated Digital media reader is not working
2. HW maker : don't know how to check, but it's built in with Compaq CQ40-114AX, but from the list pci
JMicron Technologies, Inc. SD/MMC Host Controller
JMicron Technologies, Inc. Standard SD Host Controller
JMicron Technologies, Inc. MS Host Controller
JMicron Technologies, Inc. xD Host Controller

3. When i put my SD card IN, there is nothing happen, no blink2 at all from the led indicator showing that SD card is inserted. and there is no additional media showed in /media


Need your help how to deal with it


Best Regards,
Grimanda

---

### Post by Hydraah on 2009-01-16
Type: Laptop (specifically, sound, ALC883)
It's the LG P1 Express Dual.

The sound works only through headphones. While it sometimes works via the internal speakers, it will distort and crackle/fade out after a minute or less of sound playback.

Also, you need to change the model in /etc/modprobe.d/alsa-base to 6stack-dig to get any internal speaker sound to begin with.

---

### Post by user11 on 2009-01-18
SYBA SD-CM-UAUD71 USB Sound Adapter

For Xubuntu and Ubuntu 8.04.1 / 8.10. Device is recognized and the volume bar on screen adjusts accordingly when you press the buttons, but it's for the mic only (also the volume controller defaults to adjusting the mic).

No matter what though, I can't get any sound. Can't test the mic input because I don't have a mic.

[http://www.syba.com/Product/Info/Id/450](http://www.syba.com/Product/Info/Id/450)

---

### Post by jen1963 on 2009-01-18
Here's an odd one.
I have an ASUS M3N78 Pro MOBO with an AMD Phenom x4 CPU. The live version of Ubuntu 8.10 Intrepid works fine but after install the sound gets hosed saying incompatible hardware.
I know this MOBO works with Linux because OpenSuSE 11.1 works fine...

---

### Post by corsairgt on 2009-01-21
Corsair 8 GB Flash Voyager and 16 GB GT versions flash drives are NOT compatible with Ubuntu v8.10. I couldn't install Ubuntu on these drives. However, the older 4, 8 GB Flash Voyager batch # beginning with 080xxxxxx are compatible.

---

### Post by simormate on 2009-01-24
ubuntu 8.10
realtek alc262 sound card in a fujitsu-siemens esprimo mobile m9400 laptop
jack sense not working, had to change alsa-base (model=sony-assamd)to make it work

---

### Post by aetakoz on 2009-01-24
[LEFT]Laptob HP dv6000 

** cpu**:AMD Turion 64 X2 TL-52
 **ram**:2,5 GB

**graphiks**: NVIDIA GeForce Go 6150

i want to know if i am able to work with ubuntu !

[COLOR="Red"]**_thank you!_**[/COLOR]:)[/LEFT]

---

### Post by aidave on 2009-01-25
I have an Nvidia Nforce 730a motherboard by EVGA.

This thing is close to garbage when it comes to Linux support.
It barely works with Windows XP (leaves behind unknown hardware).

It would be great if it worked, but:

- The restricted NVIDIA driver causes sound problems and boot up failures
- The unrestricted driver sometimes works with sound, if it feels like it
- Onboard soundcard wont disable via BIOS
- Only boots graphics/usb if its "in the mood"

Basically the onboard sound is a major headache. 

I would not recommend this board at all, unless you want to waste all your time trying to get it to work and failing.

---

### Post by wpshooter on 2009-01-25
Has anyone experienced any problems when trying to **_BURN_** ISO images when using **Plextor** CD drives ?

I had a Plextor CD-RW model PX-W5224TA in one of my systems on which I was running Ubuntu/Hardy and every time I attempted to burn an ISO image of Ubuntu, either the burn would fail, I would get some type of error or if the burn completed successfully and then when I went to check the integrity of the CD ISO image, it would have some errors reported by the intregrity test that is found on the initial Ubuntu boot screen menu.  P.S. - I am very familar with the general rules as to how to successfully burn a Ubuntu ISO image, I have done numerious successful burns before on other machines.

Just as soon as I replaced the drive with a Sony CD-RW drive in this machine, I have so far burned both the live version and alternate version of Hardy with ZERO problems - I even used the very same CDs that I had used with the Plextor drive.

I am going to place the Plextor drive in another machine and see if the problems repeats themselves.  But I was just wondering, if there might perhaps be some incompatibility between Ubuntu and these Plextor drives ???

P.S. - I just tried another Plextor drive on another computer and again the Plextor drive would NOT successfully complete the burn & integrity check of the Ubuntu ISO image.  What happened this time was the the burn seems to go thru the burn process O.K. but when it got to the sumcheck function, it went to 25% complete and then just hung and instead of the counter that shows the estimated time remain on the sumcheck function counting DOWN, the estimated time remaining started to go UPWARDS/INCREASE.  Me thinks that Ubuntu does not like Plextor CD drives.

Thanks.

---

### Post by Alex Yeh on 2009-01-28
Thinkpad T42p

After the install, I get a boot error message saying that the linux kernel does not support my cpu.

---

### Post by george1984 on 2009-01-28
Corsair 8 Gb Flash Voyager

To confirm post by Corsairgt a few days ago...

I just purchased the above. Used Intrepid to install Hardy iso. All went well until end of boot, when cascading error messages appeared complaining of buffer I/O error on device fd0 logical block 0 : also fs ext3 not recognised. Had to pull the plug to stop it.

Now the Voyager (which was previously good) will not mount: is not recognised or acknowledged.

Tried to run gparted. says file is read only etc. Unsuccessful dealing with this so far.

Will try the software forum to see if there is a way around this, but with my limited experience this seems most likely a hardware problem.

---

### Post by frodon on 2009-01-29
I confirm this too, i just asked my reseller to give me an equivalent instead of the Corsair 8 Gb Flash Voyager.

This USB key is jus a pain in linux, the best is to stay far away from this product or to ask for a replacement if you just bought it.

---

### Post by mirhciulica on 2009-01-29
> **wpshooter said:**
> Has anyone experienced any problems when trying to **_BURN_** ISO images when using **Plextor** CD drives ?

I had a Plextor CD-RW model PX-W5224TA in one of my systems on which I was running Ubuntu/Hardy and every time I attempted to burn an ISO image of Ubuntu, either the burn would fail, I would get some type of error or if the burn completed successfully and then when I went to check the integrity of the CD ISO image, it would have some errors reported by the intregrity test that is found on the initial Ubuntu boot screen menu.  P.S. - I am very familar with the general rules as to how to successfully burn a Ubuntu ISO image, I have done numerious successful burns before on other machines.

Just as soon as I replaced the drive with a Sony CD-RW drive in this machine, I have so far burned both the live version and alternate version of Hardy with ZERO problems - I even used the very same CDs that I had used with the Plextor drive.

I am going to place the Plextor drive in another machine and see if the problems repeats themselves.  But I was just wondering, if there might perhaps be some incompatibility between Ubuntu and these Plextor drives ???

P.S. - I just tried another Plextor drive on another computer and again the Plextor drive would NOT successfully complete the burn & integrity check of the Ubuntu ISO image.  What happened this time was the the burn seems to go thru the burn process O.K. but when it got to the sumcheck function, it went to 25% complete and then just hung and instead of the counter that shows the estimated time remain on the sumcheck function counting DOWN, the estimated time remaining started to go UPWARDS/INCREASE.  Me thinks that Ubuntu does not like Plextor CD drives.

Thanks.

Same here. But it's a DVD-RW (PX-810SA) and every time I burn with Brasero I have errors. Give GnomeBaker or Nero a try;) I have no problems!

---

### Post by man_bash on 2009-01-29
Motherboard - partial incompatibility

Maker: DFI
model: DFI Infinity NF4X (AMD Socket 754, nForce4 chipset)
Problem: poor support for PCI-e, cannot get any PCI-e card to work with 3-d acceleration (tried nVidia 8800 GT and 8600 GTS). Both video cards work fine in 2-d mode.
Distributions: Feisty, Gutsy, Hardy, & Intrepid, both x86 and AMD64.

---

### Post by HappyMan on 2009-01-29
Dell inspiron b130 total falure no work
Sigmatel audio
Minipci broadcam

---

### Post by maxgt1 on 2009-01-31
Graphics adapter
Nvidia
Geforce 6150
The drivers don't install properly sometimes giving a blank desktop
And no one in this forum gives an easy to understand solution for noobs

---

### Post by gtopcu on 2009-02-04
Graphics Card - Intel
Mobile Intel 4 Series Express Chipset Family
Ubuntu Version 8.10

Stuck at 800*600 by default.

---

### Post by Ripose on 2009-02-05
Did you install the linux_restricted_modules for Nvidia?

---

### Post by feb3 on 2009-02-05
Ubuntu 8 - installed on Vista using wubi 2 days ago. Laptop is a Futitsu Seimens Amilo Li1818. No Network Manager in Ubuntu ?driver problem WLAN 802.11b/g Sis1634.
Internet connected via ethernet.

---

### Post by golusweet on 2009-02-05
Webcam,and Touchscreen

HP tx1003 AU

output of lsusb

Bus 002 Device 003: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 001 Device 005: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 001 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by vivichrist on 2009-02-06
I stupidly bought a XFX radeon HD4830 and I use hardy. thr combination of which is disastrous. vesa works fine but of cause that's not good enough to most people so jockey doesn't display restricted drivers and if I modify xorg.conf: driver "fglrx" xorg driver says it can't detect the hardware. so install ati9.1 driver following wiki instructions and I get as a result in X a screen full of buffer garbage. but works fine out of the box with intrepid but I (personally) need the RT kernel.

actually I fixed the install of 9.1ati drivers and now hardy is go! (problem the fglrx-rt-compat.patch file was put in the wrong place causing dkms to err)

---

### Post by harrykar on 2009-02-06
a)Type Of Hardware: Graphics Card
b)Hardware Maker: Hercules
c)Hardware Model: Hercules 3D Prophet 4000XT 64 MB PCI Video Card 
d)Known Issue: lack of driver of STG4000 [3D Prophet Kyro Series]

PS: I'm newbie here i have found a related thread like this one 

[http://ubuntuforums.org/showthread.php?t=216675&highlight=STG4000+](http://ubuntuforums.org/showthread.php?t=216675&highlight=STG4000+)[3D+Prophet+Kyro+Series]

but there i can't reply.I don't still know for what reason

Hello, harrykar You are browsing a READ only archive of the main support categories pre 4/21/2008. You will not be able to post or reply any threads in this section.

So i hope here is the right place and here im In Topic:)
Moreover after most googling i find that link 

[http://klt.sourceforge.net/](http://klt.sourceforge.net/)

I don't know if it comprises the drivers but i guess is worth trying it(when i'm not busy). It's really hard to find anything for this old card:(

---

### Post by gutharius on 2009-02-11
> **graham_two_dot_oh said:**
> HP dc7900 desktop PC.  Ubuntu 8.10. Kernel 2.6.27-7-generic.

1 CPU runs at 100% reading /proc/kmsg.  Getting constant
warn_on_slowpath messages, useful looking stacktrace functions are: warn_on_slowpath, hrtimer_get_next_event, tick_notify.

Tried disabling 'run time power management' in the bios, didnt help.

Presumably /var/log/messages will fill the disc.

Same for me here. HP DC7900 Kernel Panic - not syncing: Out of memeory and no killable processes...

Also getting the screen filled with "Killed" from top to bottom on the left side.

---

### Post by SMG_07 on 2009-02-16
ASUS M70SA
ATI RADEON 3650 1GB

the problem is that i had ubuntu and kubuntu and now im using the K and it seems that the only way to avoid my problem is to install 8.04 and upgrade via internet .. 

but not the problem is back cos i went to the recovery mode and did the whole thing again .. this is my proplem before this screen problem [http://ubuntuforums.org/showthread.php?t=1070251](http://ubuntuforums.org/showthread.php?t=1070251)

now when i boot every thing is working perfectly except for the screen it gives me these moving lines on the side 
[ATTACH]103559[/ATTACH]

and i also want to know how to remove kubuntu without the windows cd cos my laptop came with the windows inside
thanks

---

### Post by waketech66 on 2009-02-16
ubuntu 8.10
IBM web cam, here is the output
Bus 002 Device 002: ID 0545:8080 Xirlink, Inc. IBM C-It WebCam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04b3:310c IBM Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

is not recognized when installed in usb
no luck with cheese or camorama

---

### Post by spirit8 on 2009-02-16
hp dv6707us 
boot hangs and i have to press enter and maintain pressed to proceed.

it first stop at this point
[2.982311] chci_hcd 0000:00:02.1: irq 22, 10mem 0xf6489000

---

### Post by lfsrteixeira on 2009-02-18
The akasa internal card reader (Model No. AK-ICR-01E2) doesn't work on Ubuntu 8.10. Its integrated USB port works well.

---

### Post by Roadbloc on 2009-02-23
Compaq Presario 1700 Laptop/Notebook Battery not recognised

---

### Post by geekits on 2009-03-01
1)Type Of Hardware: Dell XPS M1210
2)Hardware Maker: Ricoh
3)Hardware Model: XPS M1210
4)Known Issues: 

Car reader 5 in 1 can read SD cards only after installing drivers.

---

### Post by fantom_feltpen on 2009-03-01
1)Type Of Hardware: Webcam 
2)Hardware Maker: Logitech 
3)Hardware Model: QuickCam Communicate MP 
4)Known Issue: lsusb shows "Logitech Device"... cant do anthing with it. cant use any video or audio programs and i have tried EVERYTHING. :confused:

---

### Post by Meelis on 2009-03-02
Video card
Ati (GIGABYTE)
HD-4670 (1Gb)
Driver or hardware = (ATI) issue with recordMyDesktop
[INDENT][[COLOR="Blue"]Video in Youtube[/COLOR]]("http://www.youtube.com/watch?v=cJg40Ad03sk")[/INDENT]

---

### Post by thomasyen on 2009-03-10
MSI 945GCM5 V2 mainboard (North Bridge: Intel 945GC, South Bridge: Intel ICH7)
Ubuntu Intrepid 32-bit, Linux kernel 2.6.27-11-generic

Issue: does not recover from Suspend or Hibernate

---

### Post by novellus on 2009-03-16
somebody can tell me where is a **[COLOR="Magenta"]quick synthetic liste of incompatible /compatible hw[/COLOR]** for ubuntu 6.06 6.10?
i mean a liste of specifical hardware and not pages and pages of posts.....

for hw i mean, expecially, modem, internet key and pc (packard bell models, for example...)

do i ask too much?

thanks

---

### Post by jithendra on 2009-03-16
Am using Compaque presario vt64000 model laptop.Its wireless card is not detecting.
in vista its driver is found to made by Broadcom 802.11 b/g wireless driver.pls help to work it properly.

---

### Post by Tootiecat on 2009-03-20
1)Type Of Hardware - Wireless Card
2)Hardware Maker - Dell
3)Hardware Model - Inspiron B130
4)Known Issue - Wireless Card is not recognized

:(

---

### Post by IfItMovesFunkIt on 2009-03-23
1)Laptop
2)Asus
3)A6000 (Dual Boot 8.10 & XP)

Backgounds Does not display correctly during install process or once completed, display appears to be set to the "wrong" Colour Depth/Resolution.

Removal of "Screens & Graphics" and introduction of a flawed automatic detection of Monitor/video card wil cause problems for ASUS A6000 users

I did do a screen dump to include in another posting but the supposed "Bad" picture actually displayed fine after it had been moved to a different PC

---

### Post by iridiumcao on 2009-03-23
1)Type Of Hardware: Voice card
2)Hardware Maker: (Dell Inspiron 1501)
3)Hardware Model: SigmaTel STAC9200 @ ATI SB600 - High Definition Audio Controller
4)Known Issue: cannot record voice

---

### Post by ponchojuan on 2009-04-09
CNF Cardport 24X PCMCIA CDROM

Does not recognize this CDROM with 8.10 and 9.04. Works fine on WinXP with gcdrom.sys, imapi.sys, redbook.sys, and storprop.DLL. Running on a Thinkpad 240 with 320MB.  PCMCIA Controller is a PCI1211.  The PCMCIA works fine with an RA61 wireless card.  Seems Yenta_Socket with pcmciautils implementation works with this RA61 card, but not the PCMCIA CRDOM.  The device is recognized as pcmcia0.0 but no subsystem device driver loads.  PRODID is recongnized but MANID=0000,0000 and FUNCID=255.

I understand this configuration worked with pcmcia-cs, but have not tried to go that route.

---

### Post by zaiboot on 2009-04-18
Hello everyone. I am trying to run Ubuntu 9.04. but it shows busy box. I have also tried, 8.10 ( does not work well, Video Card Issue), and 8.04 and does not work too well.

I have the following configuration:

MB: Asus M2A-VM ( [http://www.asus.es/products.aspx?l1=3&l2=101&l3=496&l4=0&model=1585&modelmenu=1]("http://www.asus.es/products.aspx?l1=3&l2=101&l3=496&l4=0&model=1585&modelmenu=1"))

RAM: 4GB
DVD.
Processor: AMD Athlon 64X 2 5600+ 2.90 GHz.

Mouse: USB Maxell Optical
Keyboard: Logitech Internet 350 Keyboard ( [http://www.logitech.com/index.cfm/business/products/keyboards/devices/586&cl=gb,en](http://www.logitech.com/index.cfm/business/products/keyboards/devices/586&cl=gb,en))
Monitor: AOC 917Sw. 

And this is cpu-Z Log:
```

-------------------------
  CPU-Z version 1.50
-------------------------

Processors Map
------------------------------------------------------------------------------------

Number of processors	1
Number of threads	2

Processor 0
    -- Core 0
        -- Thread 0
    -- Core 1
        -- Thread 0


Processors Information
------------------------------------------------------------------------------------

Processor 1 (ID = 0)
Number of cores		2 (max 2)
Number of threads	2 (max 2)
Name			AMD Athlon 64 X2 5600+
Codename		Brisbane
Specification		AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
Package			Socket AM2 (940)
CPUID			F.B.2
Extended CPUID		F.6B
Brand ID		4
Core Stepping		BH-G2
Technology		65 nm
Core Speed		2900.0 MHz (14.5 x 200.0 MHz)
HT Link speed		1000.0 MHz
Stock frequency		2900 MHz
Instructions sets	MMX (+), 3DNow! (+), SSE, SSE2, SSE3, x86-64
L1 Data cache		2 x 64 KBytes, 2-way set associative, 64-byte line size
L1 Instruction cache	2 x 64 KBytes, 2-way set associative, 64-byte line size
L2 cache		2 x 512 KBytes, 16-way set associative, 64-byte line size
FID/VID Control		yes
max FID			14.5x
max VID			1.400 V
Features		XD, VT
K8 Thermal sensor	yes
K8 Revision ID		6.0
Attached device		PCI device at bus 0, device 24, function 0
Attached device		PCI device at bus 0, device 24, function 1
Attached device		PCI device at bus 0, device 24, function 2
Attached device		PCI device at bus 0, device 24, function 3


Thread dumps
------------------------------------------------------------------------------------

CPU Thread 0
APIC ID			0
Topology		Processor ID 0, Core ID 0, Thread ID 0
Type			02002008h
Max CPUID level		00000001h
Max CPUID ext. level	80000018h

Function		eax		ebx		ecx		edx
0x00000000		0x00000001	0x68747541	0x444D4163	0x69746E65
0x00000001		0x00060FB2	0x00020800	0x00002001	0x178BFBFF
0x80000000		0x80000018	0x68747541	0x444D4163	0x69746E65
0x80000001		0x00060FB2	0x000008DF	0x0000011F	0xEBD3FBFF
0x80000002		0x20444D41	0x6C687441	0x74286E6F	0x3620296D
0x80000003		0x32582034	0x61754420	0x6F43206C	0x50206572
0x80000004		0x65636F72	0x726F7373	0x30363520	0x00002B30
0x80000005		0xFF08FF08	0xFF20FF20	0x40020140	0x40020140
0x80000006		0x00000000	0x42004200	0x02008140	0x00000000
0x80000007		0x00000000	0x00000000	0x00000000	0x0000007F
0x80000008		0x00003028	0x00000000	0x00000001	0x00000000
0x80000009		0x00000000	0x00000000	0x00000000	0x00000000
0x8000000A		0x00000001	0x00000040	0x00000000	0x00000002
0x8000000B		0x00000000	0x00000000	0x00000000	0x00000000
0x8000000C		0x00000000	0x00000000	0x00000000	0x00000000
0x8000000D		0x00000000	0x00000000	0x00000000	0x00000000
0x8000000E		0x00000000	0x00000000	0x00000000	0x00000000
0x8000000F		0x00000000	0x00000000	0x00000000	0x00000000
0x80000010		0x00000000	0x00000000	0x00000000	0x00000000
0x80000011		0x00000000	0x00000000	0x00000000	0x00000000
0x80000012		0x00000000	0x00000000	0x00000000	0x00000000
0x80000013		0x00000000	0x00000000	0x00000000	0x00000000
0x80000014		0x00000000	0x00000000	0x00000000	0x00000000
0x80000015		0x00000000	0x00000000	0x00000000	0x00000000
0x80000016		0x00000000	0x00000000	0x00000000	0x00000000
0x80000017		0x00000000	0x00000000	0x00000000	0x00000000
0x80000018		0x00000000	0x00000000	0x00000000	0x00000000

Cache descriptor	Level 1 I	64 KB	1 thread(s)	
Cache descriptor	Level 1 D	64 KB	1 thread(s)	
Cache descriptor	Level 2 U	512 KB	1 thread(s)	

MSR 0x0000001B		edx = 0x00000000	eax = 0xFEE00900
MSR 0xC001001E		edx = 0x00000000	eax = 0x00000060
MSR 0xC0010015		edx = 0x00000000	eax = 0x02000040
MSR 0xC0010042		edx = 0x31061208	eax = 0x06150215
MSR 0xC0010041		edx = 0x00000001	eax = 0x00000815

CPU Thread 1
APIC ID			1
Topology		Processor ID 0, Core ID 1, Thread ID 0
Type			02002008h
Max CPUID level		00000001h
Max CPUID ext. level	80000018h

Function		eax		ebx		ecx		edx
0x00000000		0x00000001	0x68747541	0x444D4163	0x69746E65
0x00000001		0x00060FB2	0x01020800	0x00002001	0x178BFBFF
0x80000000		0x80000018	0x68747541	0x444D4163	0x69746E65
0x80000001		0x00060FB2	0x000008DF	0x0000011F	0xEBD3FBFF
0x80000002		0x20444D41	0x6C687441	0x74286E6F	0x3620296D
0x80000003		0x32582034	0x61754420	0x6F43206C	0x50206572
0x80000004		0x65636F72	0x726F7373	0x30363520	0x00002B30
0x80000005		0xFF08FF08	0xFF20FF20	0x40020140	0x40020140
0x80000006		0x00000000	0x42004200	0x02008140	0x00000000
0x80000007		0x00000000	0x00000000	0x00000000	0x0000007F
0x80000008		0x00003028	0x00000000	0x00000001	0x00000000
0x80000009		0x00000000	0x00000000	0x00000000	0x00000000
0x8000000A		0x00000001	0x00000040	0x00000000	0x00000002
0x8000000B		0x00000000	0x00000000	0x00000000	0x00000000
0x8000000C		0x00000000	0x00000000	0x00000000	0x00000000
0x8000000D		0x00000000	0x00000000	0x00000000	0x00000000
0x8000000E		0x00000000	0x00000000	0x00000000	0x00000000
0x8000000F		0x00000000	0x00000000	0x00000000	0x00000000
0x80000010		0x00000000	0x00000000	0x00000000	0x00000000
0x80000011		0x00000000	0x00000000	0x00000000	0x00000000
0x80000012		0x00000000	0x00000000	0x00000000	0x00000000
0x80000013		0x00000000	0x00000000	0x00000000	0x00000000
0x80000014		0x00000000	0x00000000	0x00000000	0x00000000
0x80000015		0x00000000	0x00000000	0x00000000	0x00000000
0x80000016		0x00000000	0x00000000	0x00000000	0x00000000
0x80000017		0x00000000	0x00000000	0x00000000	0x00000000
0x80000018		0x00000000	0x00000000	0x00000000	0x00000000

Cache descriptor	Level 1 I	64 KB	1 thread(s)	
Cache descriptor	Level 1 D	64 KB	1 thread(s)	
Cache descriptor	Level 2 U	512 KB	1 thread(s)	

MSR 0x0000001B		edx = 0x00000000	eax = 0xFEE00800
MSR 0xC001001E		edx = 0x00000000	eax = 0x00000060
MSR 0xC0010015		edx = 0x00000000	eax = 0x02000040
MSR 0xC0010042		edx = 0x31061208	eax = 0x06150215
MSR 0xC0010041		edx = 0x00000001	eax = 0x00000815


Chipset
------------------------------------------------------------------------------

Northbridge		ATI RS690/RS690M rev. 00
Southbridge		ATI SB600 rev. 00
Memory Type		DDR2
Memory Size		4096 MBytes
Channels		Dual
Memory Frequency	362.5 MHz (CPU/8)
CAS#			6.0
RAS# to CAS#		6
RAS# Precharge		6
Cycle Time (tRAS)	18
Bank Cycle Time (tRC)	25
Command Rate		2T


Memory SPD
------------------------------------------------------------------------------

DIMM #1

General
Memory type		DDR2
Module format		Regular UDIMM
Manufacturer (ID)	Kingston (7F98000000000000)
Size			1024 MBytes
Max bandwidth		PC2-6400 (400 MHz)
Part number		99U5316-028.A00LF
Serial number		680D353A
Manufacturing date	Week 22/Year 08

Attributes
Number of banks		2
Data width		64 bits
Correction		None
Nominal Voltage		1.80 Volts
EPP			no
XMP			no

Timings table
Frequency (MHz)		266	333	400	
CAS#			4.0	5.0	6.0	
RAS# to CAS# delay	4	5	6	
RAS# Precharge		4	5	6	
TRAS			12	15	18	
TRC			16	20	24	

DIMM #2

General
Memory type		DDR2
Module format		Regular UDIMM
Manufacturer (ID)	Kingston (7F98000000000000)
Size			1024 MBytes
Max bandwidth		PC2-6400 (400 MHz)
Part number		99U5316-028.A00LF
Serial number		660ED704
Manufacturing date	Week 22/Year 08

Attributes
Number of banks		2
Data width		64 bits
Correction		None
Nominal Voltage		1.80 Volts
EPP			no
XMP			no

Timings table
Frequency (MHz)		266	333	400	
CAS#			4.0	5.0	6.0	
RAS# to CAS# delay	4	5	6	
RAS# Precharge		4	5	6	
TRAS			12	15	18	
TRC			16	20	24	

DIMM #3

General
Memory type		DDR2
Module format		Regular UDIMM
Manufacturer (ID)	Kingston (7F98000000000000)
Size			1024 MBytes
Max bandwidth		PC2-6400 (400 MHz)
Part number		99U5316-028.A00LF
Serial number		660ED604
Manufacturing date	Week 22/Year 08

Attributes
Number of banks		2
Data width		64 bits
Correction		None
Nominal Voltage		1.80 Volts
EPP			no
XMP			no

Timings table
Frequency (MHz)		266	333	400	
CAS#			4.0	5.0	6.0	
RAS# to CAS# delay	4	5	6	
RAS# Precharge		4	5	6	
TRAS			12	15	18	
TRC			16	20	24	

DIMM #4

General
Memory type		DDR2
Module format		Regular UDIMM
Manufacturer (ID)	Kingston (7F98000000000000)
Size			1024 MBytes
Max bandwidth		PC2-6400 (400 MHz)
Part number		99U5316-028.A00LF
Serial number		660ED804
Manufacturing date	Week 22/Year 08

Attributes
Number of banks		2
Data width		64 bits
Correction		None
Nominal Voltage		1.80 Volts
EPP			no
XMP			no

Timings table
Frequency (MHz)		266	333	400	
CAS#			4.0	5.0	6.0	
RAS# to CAS# delay	4	5	6	
RAS# Precharge		4	5	6	
TRAS			12	15	18	
TRC			16	20	24	

Dump Module #1
      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
00   80 08 08 0E 0A 61 40 00 05 25 40 00 82 08 00 00 
10   0C 04 70 01 02 00 03 30 45 3D 50 3C 1E 3C 2D 80 
20   17 25 05 12 3C 1E 1E 00 00 3C 69 80 14 1E 00 00 
30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 12 3C 
40   7F 98 00 00 00 00 00 00 05 39 39 55 35 33 31 36 
50   2D 30 32 38 2E 41 30 30 4C 46 00 00 00 08 1C 68 
60   0D 35 3A 00 00 00 00 00 00 00 00 00 00 00 00 00 
70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
F0   39 39 55 35 33 31 36 2D 30 32 38 2E 41 30 30 4C 


Dump Module #2
      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
00   80 08 08 0E 0A 61 40 00 05 25 40 00 82 08 00 00 
10   0C 04 70 01 02 00 03 30 45 3D 50 3C 1E 3C 2D 80 
20   17 25 05 12 3C 1E 1E 00 00 3C 69 80 14 1E 00 00 
30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 12 3C 
40   7F 98 00 00 00 00 00 00 05 39 39 55 35 33 31 36 
50   2D 30 32 38 2E 41 30 30 4C 46 00 00 00 08 1C 66 
60   0E D7 04 00 00 00 00 00 00 00 00 00 00 00 00 00 
70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
F0   39 39 55 35 33 31 36 2D 30 32 38 2E 41 30 30 4C 


Dump Module #3
      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
00   80 08 08 0E 0A 61 40 00 05 25 40 00 82 08 00 00 
10   0C 04 70 01 02 00 03 30 45 3D 50 3C 1E 3C 2D 80 
20   17 25 05 12 3C 1E 1E 00 00 3C 69 80 14 1E 00 00 
30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 12 3C 
40   7F 98 00 00 00 00 00 00 05 39 39 55 35 33 31 36 
50   2D 30 32 38 2E 41 30 30 4C 46 00 00 00 08 1C 66 
60   0E D6 04 00 00 00 00 00 00 00 00 00 00 00 00 00 
70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
F0   39 39 55 35 33 31 36 2D 30 32 38 2E 41 30 30 4C 


Dump Module #4
      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
00   80 08 08 0E 0A 61 40 00 05 25 40 00 82 08 00 00 
10   0C 04 70 01 02 00 03 30 45 3D 50 3C 1E 3C 2D 80 
20   17 25 05 12 3C 1E 1E 00 00 3C 69 80 14 1E 00 00 
30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 12 3C 
40   7F 98 00 00 00 00 00 00 05 39 39 55 35 33 31 36 
50   2D 30 32 38 2E 41 30 30 4C 46 00 00 00 08 1C 66 
60   0E D8 04 00 00 00 00 00 00 00 00 00 00 00 00 00 
70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
F0   39 39 55 35 33 31 36 2D 30 32 38 2E 41 30 30 4C 


Monitoring
------------------------------------------------------------------------------

Mainboard Model		M2A-VM (0x190 - 0x5345A0)

LPCIO
-----------------------------------------------------
Vendor			ITE
Model			IT8716
Vendor ID		0x90
Chip ID			0x8716
Revision ID		0x1
Config Mode I/O address	0x2E

Dump config mode register space, LDN = 0x4
      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
00   00 00 00 00 00 00 00 04 00 00 00 00 00 00 00 00 
10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
20   87 16 01 00 00 40 0E 00 42 80 00 00 1F 00 00 00 
30   01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
60   02 28 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
70   00 02 00 00 04 04 00 00 00 00 00 00 00 00 00 00 


Hardware monitor
-----------------------------------------------------

ITE IT87 hardware monitor

Voltage sensor 0	1.36 Volts [0x55] (CPU VCORE)
Voltage sensor 1	3.33 Volts [0xD0] (VIN1)
Voltage sensor 3	4.97 Volts [0xB9] (+5V)
Voltage sensor 4	12.10 Volts [0xBD] (+12V)
Voltage sensor 7	5.05 Volts [0xBC] (+5V VCCH)
Voltage sensor 8	3.22 Volts [0xC9] (VBAT)
Temperature sensor 0	42°C (107°F) [0x2A] (TMPIN0)
Temperature sensor 1	38°C (100°F) [0x26] (TMPIN1)
Temperature sensor 2	25°C (76°F) [0x19] (TMPIN2)
Fan sensor 0		3358 RPM [0xC9] (FANIN0)

Dump hardware monitor
LPC Register space, base address = 0x0228

      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
00   11 0A FF 07 00 00 00 00 00 80 40 09 17 C9 FF FF 
10   D0 D0 BF 30 D7 7F 80 82 00 FF FF 00 00 FF FF FF 
20   55 D0 00 B9 BD 00 00 BC C9 2A 26 19 CA 81 81 81 
30   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
40   FF FF FF FF FF FF 00 0D 2D FF FF FF FF FF FF FF 
50   FF 31 7F 7F 7F 50 F3 00 90 00 39 12 00 00 00 00 
60   00 32 7F 3C A0 00 FF FF 00 32 7F 3C A0 00 FF FF 
70   7F 7F 7F 00 00 00 FF FF FF FF FF FF FF FF FF FF 
80   FF FF 00 00 FD FF FF FF 00 00 FF C0 02 00 99 99 
90   7F 7F 7F 00 00 7F FF FF 7F 7F 7F 00 00 7F FF FF 
A0   00 00 00 00 00 00 00 FF FF FF FF FF FF FF FF FF 
B0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
C0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
D0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
E0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
F0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 



Hardware monitor
-----------------------------------------------------

AMD Athlon 64 X2 5600+ hardware monitor

Temperature sensor 0	20°C (67°F) [0x112] (Core #0)
Temperature sensor 1	13°C (54°F) [0xF6] (Core #1)

Dump hardware monitor



PCI Device List
------------------------------------------------------------------------------

Host Bridge
bus 0 (0x00), device 0 (0x00), function 0 (0x00)
Common header
	Vendor ID		0x1002
	Model ID		0x7910
	Revision ID		0x00
	PI			0x00
	SubClass		0x00
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x40
	Header			0x00
PCI header
	Subvendor ID		0x1043
	Subsystem ID		0x826D
	Int. Line		0x00
	Int. Pin		0x00
Capabilities
	HyperTransport Capability
		Offset			C4h
		Revision		1.05
		Interface type		Slave/Primary
		Link 0 width (in/out)	16 bits/16 bits
		Link 0 frequency	1000MHz
		Link 1 width (in/out)	8 bits/8 bits
		Link 1 frequency	200MHz
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 10 79 06 00 20 22 00 00 00 06 00 40 00 00 
	 10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 6D 82 
	 30   00 00 00 00 C4 00 00 00 00 00 00 00 00 00 00 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 42 20 05 00 
	 50   43 10 6D 82 FF 00 00 00 00 00 00 00 00 00 00 00 
	 60   5F 00 00 00 00 00 00 00 00 02 20 00 98 F8 01 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   40 43 00 00 95 00 00 03 20 01 10 00 03 26 00 00 
	 90   00 00 00 D8 40 C4 40 E4 00 D0 00 00 01 00 00 00 
	 A0   00 00 00 00 00 00 00 00 07 01 00 00 49 01 10 07 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 08 00 80 01 60 00 11 11 D0 00 00 00 
	 D0   25 06 65 00 02 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 90 00 00 00 F7 FF FE FF 
	 F0   00 00 00 00 00 80 80 00 00 00 00 00 00 00 00 00 


PCI to PCI Bridge
bus 0 (0x00), device 1 (0x01), function 0 (0x00)
Common header
	Vendor ID		0x1002
	Model ID		0x7912
	Revision ID		0x00
	PI			0x00
	SubClass		0x04
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x63
	Header			0x01
PCI header
	Primary bus		0x00
	Secondary bus		0x01
	Int. Line		0xFF
	Int. Pin		0x00
Capabilities
	HyperTransport Capability
		Offset			44h
		Interface type		MSI Mapping
	Subsystem Vendor Capability
		Offset		B0h
		Subsystem ID	0x7912
		Sub. Vendor ID	0x1002
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 12 79 07 00 30 02 00 00 04 06 00 63 01 00 
	 10   00 00 00 00 00 00 00 00 00 01 01 44 C1 C1 20 22 
	 20   A0 FD B0 FD 01 F0 F1 F7 00 00 00 00 00 00 00 00 
	 30   00 00 00 00 44 00 00 00 00 00 00 00 FF 00 0C 00 
	 40   00 00 00 00 08 B0 03 A8 00 00 00 00 02 10 12 79 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   0D 00 00 00 02 10 12 79 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


PCI to PCI Bridge
bus 0 (0x00), device 7 (0x07), function 0 (0x00)
Common header
	Vendor ID		0x1002
	Model ID		0x7917
	Revision ID		0x00
	PI			0x00
	SubClass		0x04
	BaseClass		0x06
	Cache Line		0x08
	Latency			0x00
	Header			0x01
PCI header
	Primary bus		0x00
	Secondary bus		0x02
	Int. Line		0xFF
	Int. Pin		0x00
Capabilities
	Power Management Capability
		Offset		50h
		Version		1.2
	PCI Express Capability
		Offset		58h
		Device type	Root Port of PCI-E Root Complex
		Port		4
		Version		1.0
		Physical slot	Integrated device
		Link width	1x (max 1x)
	Message Signalled Interrupts Capability
		Offset		80h
	Subsystem Vendor Capability
		Offset		B0h
		Subsystem ID	0x826D
		Sub. Vendor ID	0x1043
	HyperTransport Capability
		Offset			B8h
		Interface type		MSI Mapping
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 17 79 07 00 10 00 00 00 04 06 08 00 01 00 
	 10   00 00 00 00 00 00 00 00 00 02 02 00 D1 D1 00 00 
	 20   F0 FD F0 FD C1 FD C1 FD 00 00 00 00 00 00 00 00 
	 30   00 00 00 00 50 00 00 00 00 00 00 00 FF 00 04 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   01 58 03 C8 00 00 00 00 10 80 41 00 20 80 00 00 
	 60   10 08 00 00 11 0C 10 04 00 00 11 30 00 00 00 00 
	 70   C0 03 48 00 00 00 01 00 00 00 00 00 00 00 00 00 
	 80   05 B0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   0D B8 00 00 43 10 6D 82 08 00 03 A8 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   A5 00 00 00 10 0F 0B 0A 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


IDE Controller
bus 0 (0x00), device 18 (0x12), function 0 (0x00)
Common header
	Vendor ID		0x1002
	Model ID		0x4380
	Revision ID		0x00
	PI			0x8F
	SubClass		0x01
	BaseClass		0x01
	Cache Line		0x00
	Latency			0x40
	Header			0x00
PCI header
	Address 0 (port)	0x0000FC00
	Address 1 (port)	0x0000F800
	Address 2 (port)	0x0000F400
	Address 3 (port)	0x0000F000
	Address 4 (port)	0x0000EC00
	Address 5 (memory)	0xFE02F000
	Subvendor ID		0x1043
	Subsystem ID		0x81EF
	Int. Line		0x16
	Int. Pin		0x01
Capabilities
	Power Management Capability
		Offset		60h
		Version		1.1
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 80 43 07 00 30 02 00 8F 01 01 00 40 00 00 
	 10   01 FC 00 00 01 F8 00 00 01 F4 00 00 01 F0 00 00 
	 20   01 EC 00 00 00 F0 02 FE 00 00 00 00 43 10 EF 81 
	 30   00 00 00 00 60 00 00 00 00 00 00 00 16 01 00 00 
	 40   10 00 80 02 01 00 10 00 01 00 00 00 00 00 00 00 
	 50   05 00 84 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   01 00 22 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   12 00 10 00 0F 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 06 00 00 2C D5 00 B4 00 D5 00 B4 00 
	 90   D5 00 B4 00 D5 00 B4 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 78 00 00 00 00 00 00 00 78 00 00 
	 B0   00 00 00 00 00 78 00 00 00 00 00 00 00 78 00 00 
	 C0   00 20 00 00 80 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


USB Controller (OHCI)
bus 0 (0x00), device 19 (0x13), function 0 (0x00)
Common header
	Vendor ID		0x1002
	Model ID		0x4387
	Revision ID		0x00
	PI			0x10
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x08
	Latency			0x40
	Header			0x80
PCI header
	Address 0 (memory)	0xFE02E000
	Subvendor ID		0x1043
	Subsystem ID		0x81EF
	Int. Line		0x10
	Int. Pin		0x01
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 87 43 07 00 A0 02 00 10 03 0C 08 40 80 00 
	 10   00 E0 02 FE 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 EF 81 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 10 01 00 00 
	 40   80 1F 00 00 0A 84 B7 18 07 35 00 00 00 00 00 00 
	 50   00 8C 00 00 00 00 00 00 10 32 54 76 98 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 FF 00 00 80 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


USB Controller (OHCI)
bus 0 (0x00), device 19 (0x13), function 1 (0x01)
Common header
	Vendor ID		0x1002
	Model ID		0x4388
	Revision ID		0x00
	PI			0x10
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x08
	Latency			0x40
	Header			0x00
PCI header
	Address 0 (memory)	0xFE02D000
	Subvendor ID		0x1043
	Subsystem ID		0x81EF
	Int. Line		0x11
	Int. Pin		0x02
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 88 43 07 00 A0 02 00 10 03 0C 08 40 00 00 
	 10   00 D0 02 FE 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 EF 81 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 11 02 00 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


USB Controller (OHCI)
bus 0 (0x00), device 19 (0x13), function 2 (0x02)
Common header
	Vendor ID		0x1002
	Model ID		0x4389
	Revision ID		0x00
	PI			0x10
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x08
	Latency			0x40
	Header			0x00
PCI header
	Address 0 (memory)	0xFE02C000
	Subvendor ID		0x1043
	Subsystem ID		0x81EF
	Int. Line		0x12
	Int. Pin		0x03
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 89 43 07 00 A0 02 00 10 03 0C 08 40 00 00 
	 10   00 C0 02 FE 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 EF 81 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 12 03 00 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


USB Controller (OHCI)
bus 0 (0x00), device 19 (0x13), function 3 (0x03)
Common header
	Vendor ID		0x1002
	Model ID		0x438A
	Revision ID		0x00
	PI			0x10
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x08
	Latency			0x40
	Header			0x00
PCI header
	Address 0 (memory)	0xFE02B000
	Subvendor ID		0x1043
	Subsystem ID		0x81EF
	Int. Line		0x11
	Int. Pin		0x02
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 8A 43 07 00 A0 02 00 10 03 0C 08 40 00 00 
	 10   00 B0 02 FE 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 EF 81 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 11 02 00 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


USB Controller (OHCI)
bus 0 (0x00), device 19 (0x13), function 4 (0x04)
Common header
	Vendor ID		0x1002
	Model ID		0x438B
	Revision ID		0x00
	PI			0x10
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x08
	Latency			0x40
	Header			0x00
PCI header
	Address 0 (memory)	0xFE02A000
	Subvendor ID		0x1043
	Subsystem ID		0x81EF
	Int. Line		0x12
	Int. Pin		0x03
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 8B 43 07 00 A0 02 00 10 03 0C 08 40 00 00 
	 10   00 A0 02 FE 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 EF 81 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 12 03 00 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


USB 2.0 Controller (EHCI)
bus 0 (0x00), device 19 (0x13), function 5 (0x05)
Common header
	Vendor ID		0x1002
	Model ID		0x4386
	Revision ID		0x00
	PI			0x20
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x08
	Latency			0x40
	Header			0x00
PCI header
	Address 0 (memory)	0xFE029000
	Subvendor ID		0x1043
	Subsystem ID		0x81EF
	Int. Line		0x13
	Int. Pin		0x04
Capabilities
	Power Management Capability
		Offset		C0h
		Version		1.1
	Debug Port Capability
		Offset		E4h
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 86 43 07 00 B0 02 00 20 03 0C 08 40 00 00 
	 10   00 90 02 FE 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 EF 81 
	 30   00 00 00 00 C0 00 00 00 00 00 00 00 13 04 00 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   40 00 0E 00 01 00 00 00 00 00 00 00 00 00 00 00 
	 60   20 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   01 00 00 00 00 00 00 C0 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   01 E4 02 7E 00 00 40 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 0A 00 E0 20 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


SMBus Controller
bus 0 (0x00), device 20 (0x14), function 0 (0x00)
Common header
	Vendor ID		0x1002
	Model ID		0x4385
	Revision ID		0x14
	PI			0x00
	SubClass		0x05
	BaseClass		0x0C
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Address 0 (port)	0x00000B00
	Address 1 (port)	0xFFFFFFFC
	Subvendor ID		0x1043
	Subsystem ID		0x81EF
	Int. Line		0x00
	Int. Pin		0x00
Capabilities
	HyperTransport Capability
		Offset			B0h
		Interface type		MSI Mapping
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 85 43 03 04 30 02 14 00 05 0C 00 00 80 00 
	 10   01 0B 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 EF 81 
	 30   00 00 00 00 B0 00 00 00 00 00 00 00 00 00 00 00 
	 40   D4 39 00 04 00 00 00 00 0F FF 00 00 00 00 00 00 
	 50   F0 01 F0 08 F0 0F F0 07 11 0B F0 0F 00 00 00 00 
	 60   01 00 07 00 BF FF 9E 8F 3F 90 00 00 20 00 00 00 
	 70   00 01 00 00 08 00 C0 FE FF 6E 00 00 00 00 F0 0F 
	 80   F0 0A F0 0F 00 00 00 00 00 00 00 00 8C 00 00 80 
	 90   01 0B 00 00 F9 CE FF 00 00 00 00 00 00 00 00 00 
	 A0   00 00 FF FF FF FF F0 08 02 FD 02 02 16 7B 20 18 
	 B0   08 00 02 A8 00 00 00 00 00 00 00 00 F0 0F 08 1A 
	 C0   FF FF FF FF 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 01 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   D8 0C 00 00 00 00 44 00 00 00 00 00 AA 00 10 01 


IDE Controller
bus 0 (0x00), device 20 (0x14), function 1 (0x01)
Common header
	Vendor ID		0x1002
	Model ID		0x438C
	Revision ID		0x00
	PI			0x8A
	SubClass		0x01
	BaseClass		0x01
	Cache Line		0x00
	Latency			0x40
	Header			0x00
PCI header
	Address 4 (port)	0x0000E400
	Subvendor ID		0x1043
	Subsystem ID		0x81EF
	Int. Line		0xFF
	Int. Pin		0x01
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 8C 43 05 00 20 02 00 8A 01 01 00 40 00 00 
	 10   01 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
	 20   01 E4 00 00 00 00 00 00 00 00 00 00 43 10 EF 81 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 FF 01 00 00 
	 40   20 99 00 00 FF FF 00 00 00 00 40 00 00 00 00 00 
	 50   00 00 00 00 02 00 40 00 00 00 00 00 00 00 00 00 
	 60   00 00 40 00 10 2C 01 07 01 00 00 00 FF FF 0F 00 
	 70   05 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


Multimedia device
bus 0 (0x00), device 20 (0x14), function 2 (0x02)
Common header
	Vendor ID		0x1002
	Model ID		0x4383
	Revision ID		0x00
	PI			0x00
	SubClass		0x03
	BaseClass		0x04
	Cache Line		0x08
	Latency			0x40
	Header			0x00
PCI header
	Address 0 (memory)	0xFE020000
	Subvendor ID		0x1043
	Subsystem ID		0x8249
	Int. Line		0x10
	Int. Pin		0x01
Capabilities
	Power Management Capability
		Offset		50h
		Version		1.1
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 83 43 06 00 10 04 00 00 03 04 08 40 00 00 
	 10   04 00 02 FE 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 49 82 
	 30   00 00 00 00 50 00 00 00 00 00 00 00 10 01 00 00 
	 40   00 00 00 00 01 00 00 00 00 00 00 00 01 00 00 00 
	 50   01 00 42 C8 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   05 00 80 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


PCI to ISA Bridge
bus 0 (0x00), device 20 (0x14), function 3 (0x03)
Common header
	Vendor ID		0x1002
	Model ID		0x438D
	Revision ID		0x00
	PI			0x00
	SubClass		0x01
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Subvendor ID		0x1043
	Subsystem ID		0x81EF
	Int. Line		0x00
	Int. Pin		0x00
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 8D 43 0F 00 20 02 00 00 01 06 00 00 80 00 
	 10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 EF 81 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 40   04 00 00 00 FF FF FF FF 3F FF 42 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 20 02 00 00 0E 00 0F 00 B0 FF FF FF 
	 70   67 45 23 01 00 00 00 00 00 00 00 00 05 00 00 00 
	 80   08 00 03 A8 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


PCI to PCI Bridge
bus 0 (0x00), device 20 (0x14), function 4 (0x04)
Common header
	Vendor ID		0x1002
	Model ID		0x4384
	Revision ID		0x00
	PI			0x01
	SubClass		0x04
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x40
	Header			0x81
PCI header
	Primary bus		0x00
	Secondary bus		0x03
	Int. Line		0x00
	Int. Pin		0x00
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 84 43 27 00 A0 02 00 01 04 06 00 40 81 00 
	 10   00 00 00 00 00 00 00 00 00 03 03 40 F0 00 80 22 
	 20   F0 FF 00 00 F0 FF 00 00 00 00 00 00 00 00 00 00 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 04 00 
	 40   26 00 3C FF 00 00 00 00 0C 01 3F D1 00 00 00 00 
	 50   01 00 00 00 08 00 03 A8 00 00 00 00 85 00 FF FF 
	 60   CA 0E 17 00 BA 18 10 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 01 00 02 06 
	 E0   00 00 80 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


Host Bridge
bus 0 (0x00), device 24 (0x18), function 0 (0x00)
Common header
	Vendor ID		0x1022
	Model ID		0x1100
	Revision ID		0x00
	PI			0x00
	SubClass		0x00
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Subvendor ID		0x0000
	Subsystem ID		0x0000
	Int. Line		0x00
	Int. Pin		0x00
Capabilities
	HyperTransport Capability
		Offset			80h
		Revision		1.02
		Interface type		Host/Secondary
		Device number	0
		Link 0 width (in/out)	16 bits/16 bits
		Link 0 frequency	1000MHz
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   22 10 00 11 00 00 10 00 00 00 00 06 00 00 80 00 
	 10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 30   00 00 00 00 80 00 00 00 00 00 00 00 00 00 00 00 
	 40   01 01 01 00 01 01 01 00 01 01 01 00 01 01 01 00 
	 50   01 01 01 00 01 01 01 00 01 01 01 00 01 01 01 00 
	 60   00 00 01 00 E4 00 00 00 20 C8 2E 0F 0C 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   08 00 01 21 20 00 11 11 22 06 75 80 02 00 00 00 
	 90   78 01 70 01 00 00 03 00 07 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


Host Bridge
bus 0 (0x00), device 24 (0x18), function 1 (0x01)
Common header
	Vendor ID		0x1022
	Model ID		0x1101
	Revision ID		0x00
	PI			0x00
	SubClass		0x00
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Subvendor ID		0x0000
	Subsystem ID		0x0000
	Int. Line		0x00
	Int. Pin		0x00
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   22 10 01 11 00 00 00 00 00 00 00 06 00 00 80 00 
	 10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 40   03 00 00 00 00 00 1F 01 00 00 00 00 01 00 00 00 
	 50   00 00 00 00 02 00 00 00 00 00 00 00 03 00 00 00 
	 60   00 00 00 00 04 00 00 00 00 00 00 00 05 00 00 00 
	 70   00 00 00 00 06 00 00 00 00 00 00 00 07 00 00 00 
	 80   03 0A 00 00 00 0B 00 00 00 00 F0 00 80 FF F7 00 
	 90   03 00 E0 00 00 FF DF 00 00 14 21 04 B4 12 F4 CC 
	 A0   04 56 5B 38 80 E0 32 C2 03 00 F0 00 00 02 FE 00 
	 B0   03 00 E0 00 80 3F E0 00 00 00 00 00 00 00 00 00 
	 C0   13 B0 00 00 00 F0 00 00 30 E0 C3 00 00 F0 0F 00 
	 D0   10 50 28 00 10 30 8C 00 10 30 2F 01 13 10 03 00 
	 E0   03 00 00 03 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   01 20 00 E0 00 00 00 00 00 00 00 00 00 00 00 00 


Host Bridge
bus 0 (0x00), device 24 (0x18), function 2 (0x02)
Common header
	Vendor ID		0x1022
	Model ID		0x1102
	Revision ID		0x00
	PI			0x00
	SubClass		0x00
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Subvendor ID		0x0000
	Subsystem ID		0x0000
	Int. Line		0x00
	Int. Pin		0x00
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   22 10 02 11 00 00 00 00 00 00 00 06 00 00 80 00 
	 10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 40   01 00 00 00 01 01 00 00 01 02 00 00 01 03 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   E0 3C F8 00 E0 3C F8 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 46 00 00 00 00 00 00 00 
	 80   22 00 00 00 00 00 00 00 35 F3 7E 0C 20 13 92 00 
	 90   30 0C 01 00 5B 80 10 77 24 00 00 80 20 25 20 00 
	 A0   EF 02 00 0C 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   4C 23 85 59 B9 00 00 00 CE 7F 65 0E 81 12 06 18 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   0D 82 91 1C 10 E2 50 24 17 03 90 CE 23 07 24 EC 
	 E0   5B 86 91 CC 38 26 21 80 0D 9D 21 B2 89 06 04 4D 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


Host Bridge
bus 0 (0x00), device 24 (0x18), function 3 (0x03)
Common header
	Vendor ID		0x1022
	Model ID		0x1103
	Revision ID		0x00
	PI			0x00
	SubClass		0x00
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Subvendor ID		0x0000
	Subsystem ID		0x0000
	Int. Line		0x00
	Int. Pin		0x00
Capabilities
	Secure Device Capability
		Offset		F0h
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   22 10 03 11 00 00 10 00 00 00 00 06 00 00 80 00 
	 10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 30   00 00 00 00 F0 00 00 00 00 00 00 00 00 00 00 00 
	 40   FF 3B 04 00 40 00 10 0A 00 00 00 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 40 ED 2F FD 
	 60   4A 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   11 01 32 51 21 40 30 50 00 2A 00 08 1B 21 00 00 
	 80   00 00 07 23 13 21 13 21 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 10 00 00 00 00 3C 1F 01 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 01 A7 0D 00 00 00 60 0C 25 26 26 00 
	 E0   00 00 00 00 3E E0 40 00 19 17 00 00 00 00 00 00 
	 F0   0F 00 10 00 00 00 00 00 00 00 00 00 B2 0F 06 00 


VGA Controller
bus 1 (0x01), device 5 (0x05), function 0 (0x00)
Common header
	Vendor ID		0x1002
	Model ID		0x791E
	Revision ID		0x00
	PI			0x00
	SubClass		0x00
	BaseClass		0x03
	Cache Line		0x08
	Latency			0x40
	Header			0x00
PCI header
	Address 0 (memory)	0xF0000000
	Address 2 (memory)	0xFDBF0000
	Address 4 (port)	0x0000CC00
	Address 5 (memory)	0xFDA00000
	Subvendor ID		0x1043
	Subsystem ID		0x826D
	Int. Line		0x12
	Int. Pin		0x01
Capabilities
	Power Management Capability
		Offset		50h
		Version		1.1
	Message Signalled Interrupts Capability
		Offset		80h
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 1E 79 07 00 10 00 00 00 00 03 08 40 00 00 
	 10   0C 00 00 F0 00 00 00 00 04 00 BF FD 00 00 00 00 
	 20   01 CC 00 00 00 00 A0 FD 00 00 00 00 43 10 6D 82 
	 30   00 00 00 00 50 00 00 00 00 00 00 00 12 01 00 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 43 10 6D 82 
	 50   01 80 02 06 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   05 00 80 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


Ethernet Controller
bus 2 (0x02), device 0 (0x00), function 0 (0x00)
Common header
	Vendor ID		0x10EC
	Model ID		0x8168
	Revision ID		0x01
	PI			0x00
	SubClass		0x00
	BaseClass		0x02
	Cache Line		0x08
	Latency			0x00
	Header			0x00
PCI header
	Address 0 (port)	0x0000DC00
	Address 2 (memory)	0xFDFFF000
	Subvendor ID		0x1043
	Subsystem ID		0x81AA
	Int. Line		0x13
	Int. Pin		0x01
Capabilities
	Power Management Capability
		Offset		40h
		Version		1.1
	Virtual Product Data Capability
		Offset		48h
	Message Signalled Interrupts Capability
		Offset		50h
	PCI Express Capability
		Offset		60h
		Device type	PCI-E Endpoint Device
		Port		0
		Version		1.0
		Link width	1x (max 1x)
	Vendor Dependant Capability
		Offset		84h
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   EC 10 68 81 07 00 10 00 01 00 00 02 08 00 00 00 
	 10   01 DC 00 00 00 00 00 00 04 F0 FF FD 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 AA 81 
	 30   00 00 00 00 40 00 00 00 00 00 00 00 13 01 00 00 
	 40   01 48 C2 F7 00 00 00 00 03 50 00 00 00 00 00 00 
	 50   05 60 82 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   10 84 01 00 23 7F 00 00 10 58 10 00 11 F4 03 00 
	 70   00 00 11 10 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 09 00 4C 01 01 1C 02 00 FB FF FF 11 
	 90   08 30 00 00 F4 38 07 00 5D B1 00 00 CB 05 00 00 
	 A0   02 28 FF 01 00 00 00 00 00 08 00 00 03 00 03 00 
	 B0   00 40 00 00 FF 3F FF 3F FF FF 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


DMI
------------------------------------------------------------------------------

DMI BIOS
--------
	vendor		Phoenix Technologies, LTD
	version		ASUS M2A-VM ACPI BIOS Revision 1604
	date		12/19/2007


DMI System Information
----------------------
	manufacturer	System manufacturer
	product		System Product Name
	version		System Version
	serial		System Serial Number
	UUID		40DA6FB7-4F08DD11-AE51001F-C6B03D1B


DMI Baseboard
-------------
	vendor		ASUSTeK Computer INC.
	model		M2A-VM
	revision	1.XX
	serial		123456789000


DMI System Enclosure
--------------------
	manufacturer	Chassis Manufacture
	chassis type	Desktop
	chassis serial	EVAL


DMI Processor
-------------
	manufacturer	AMD
	model		AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
	clock speed	2900.0 MHz
	FSB speed	200.0 MHz
	multiplier	14.5x


DMI Memory Controller
---------------------
	correction	64-bit ECC
	Max module size	2048 MBytes


DMI Memory Module
-----------------
	designation	A0
	size		1024 MBytes (double bank)


DMI Memory Module
-----------------
	designation	A1
	size		1024 MBytes (double bank)


DMI Memory Module
-----------------
	designation	A2
	size		1024 MBytes (double bank)


DMI Memory Module
-----------------
	designation	A3
	size		1024 MBytes (double bank)


DMI Port Connector
------------------
	designation	PRI_IDE (internal)
	connector	On Board IDE


DMI Port Connector
------------------
	designation	FLOPPY (internal)
	port type	8251 FIFO Compatible
	connector	On Board Floppy


DMI Port Connector
------------------
	designation	COM1 (internal)
	port type	Serial Port 16450
	connector	9 Pin Dual Inline (pin 10 cut)
	connector	DB-9 male


DMI Port Connector
------------------
	designation	LPT1 (internal)
	port type	Parallel Port ECP/EPP
	connector	DB-25 female
	connector	DB-25 female


DMI Port Connector
------------------
	designation	PS/2 Keyboard (internal)
	port type	Keyboard Port
	connector	PS/2
	connector	PS/2


DMI Port Connector
------------------
	designation	PS/2 Mouse (internal)
	port type	Mouse Port
	connector	PS/2
	connector	PS/2


DMI Port Connector
------------------
	designation	USB1 (external)
	port type	USB


DMI Port Connector
------------------
	designation	USB2 (external)
	port type	USB


DMI Port Connector
------------------
	designation	USB3 (external)
	port type	USB


DMI Port Connector
------------------
	designation	USB4 (external)
	port type	USB


DMI Port Connector
------------------
	designation	USB5 (external)
	port type	USB


DMI Port Connector
------------------
	designation	USB6 (external)
	port type	USB


DMI Port Connector
------------------
	designation	USB7 (external)
	port type	USB


DMI Port Connector
------------------
	designation	USB8 (external)
	port type	USB


DMI Port Connector
------------------
	designation	USB9 (external)
	port type	USB


DMI Port Connector
------------------
	designation	USB10 (external)
	port type	USB


DMI Port Connector
------------------
	designation	VIDEO (external)
	port type	Video Port
	connector	DB-15 female


DMI Port Connector
------------------
	designation	LINE_IN (internal)
	designation	LINE_IN (external)
	port type	Audio Port


DMI Port Connector
------------------
	designation	LINE_OUT (internal)
	designation	LINE_OUT (external)
	port type	Audio Port
	connector	Mini Jack (headphones)


DMI Port Connector
------------------
	designation	MIC_IN (internal)
	designation	MIC_IN (external)
	port type	Audio Port
	connector	Mini Jack (headphones)


DMI Port Connector
------------------
	designation	CD_IN (internal)
	designation	CD_IN (external)
	port type	Audio Port
	connector	On Board Sound Input From CD-ROM


DMI Port Connector
------------------
	designation	SPDIF_OUT (internal)
	designation	SPDIF_OUT (external)
	port type	Audio Port


DMI Port Connector
------------------
	designation	FP_AUDIO (internal)
	designation	FP_AUDIO (external)
	port type	Audio Port


DMI Port Connector
------------------
	designation	LAN_1 (external)
	port type	Network Port
	connector	RJ-45


DMI Port Connector
------------------
	designation	SATA1 (internal)
	connector	On Board IDE


DMI Port Connector
------------------
	designation	SATA2 (internal)
	connector	On Board IDE


DMI Port Connector
------------------
	designation	SATA3 (internal)
	connector	On Board IDE


DMI Port Connector
------------------
	designation	SATA4 (internal)
	connector	On Board IDE


DMI Port Connector
------------------
	designation	CPU_FAN1 (internal)


DMI Extension Slot
------------------
	designation	PCI1
	type		PCI
	width		32 bits
	populated	no


DMI Extension Slot
------------------
	designation	PCI2
	type		PCI
	width		32 bits
	populated	no


DMI Extension Slot
------------------
	designation	PCIEX16
	type		A5
	populated	no


DMI Extension Slot
------------------
	designation	PCIEX1_1
	type		A5
	populated	no


DMI Physical Memory Array
-------------------------
	location	Motherboard
	usage		System Memory
	correction	None
	max capacity	8192 MBytes
	max# of devices	4


DMI Memory Device
-----------------
	designation	A0
	format		DIMM
	type		unknown
	total width	64 bits
	data width	64 bits
	size		1024 MBytes


DMI Memory Device
-----------------
	designation	A1
	format		DIMM
	type		unknown
	total width	64 bits
	data width	64 bits
	size		1024 MBytes


DMI Memory Device
-----------------
	designation	A2
	format		DIMM
	type		unknown
	total width	64 bits
	data width	64 bits
	size		1024 MBytes


DMI Memory Device
-----------------
	designation	A3
	format		DIMM
	type		unknown
	total width	64 bits
	data width	64 bits
	size		1024 MBytes

Resources
------------------------------------------------------------------------------

Port I/O Space, BA=0xFC00
Port I/O Space, BA=0xF800
Port I/O Space, BA=0xF400
Port I/O Space, BA=0xF000
Port I/O Space, BA=0xEC00
Memory I/O Space, BA=0x00000000FE02F000
Memory I/O Space, BA=0x00000000FE02E000
Memory I/O Space, BA=0x00000000FE02D000
Memory I/O Space, BA=0x00000000FE02C000
Memory I/O Space, BA=0x00000000FE02B000
Memory I/O Space, BA=0x00000000FE02A000
Memory I/O Space, BA=0x00000000FE029000
Port I/O Space, BA=0xB00
Port I/O Space, BA=0xFFFFFFFC
Port I/O Space, BA=0xE400
Memory I/O Space, BA=0x00000000FE020000
Memory I/O Space, BA=0x00000000F0000000
Memory I/O Space, BA=0x00000000FDBF0000
Port I/O Space, BA=0xCC00
Memory I/O Space, BA=0x00000000FDA00000
Port I/O Space, BA=0xDC00
Memory I/O Space, BA=0x00000000FDFFF000
Port I/O Space, BA=0x4008, size=0x4
Memory I/O Space, BA=0x00000000FEE00000, size=0x1000
Port I/O Space, BA=0x228
Port I/O Space, BA=0x2E
Port I/O Space, BA=0xCD0, size=0x100


```

And yes, unfortunatly I am running Windows.
Thanks to all of you, and keep all the good work. :wink: :wink:

---

### Post by am0_oma on 2009-04-21
sony vaio VGN-Z12MN

intel VGA- not work
nVidia 9300M GS VGA- not work

Headphone speaker do not work

Brightness keys not work

---

### Post by Kidney on 2009-04-23
Acer Aspire 6920G

I'm using Ubuntu 9.04
Three known issues - first is that i have no sound.Had no with previous edition of ubuntu ( 8.10 )

Second my laptop have CineDash Media Console.This is something like a remote control with touch sensors.This is not working properly.

Third - when i press bluetooth button the brightness icon  appears.Should be bluetooth.

---

### Post by webs37 on 2009-04-24
Compaq Presario CQ40-401AU

No Sound on ubuntu 7.10, 9.04-beta and 9.04 

hardware detect on 9.04: 
sudo lspci -v

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: Hewlett-Packard Company Device 30fe
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at 52500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
    Subsystem: ATI Technologies Inc RS780 Azalia controller
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at 52410000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

Detail spec:
Product Name 
Microprocessor AMD Turion X2 Mobile Processor RM-74  - 2x 2.2 GHz, 3600 MHz   Microprocessor Cache 1 MB L2 Cache   Memory 1024 MB DDRAM II   Memory Max Supports up to 2 GB DDR2 memory   Video Graphics ATI Radeon HD 3200 Graphics   Video Memory Video Memory with 256MB shared video memory   Hard Drive 250 GB SATA HDD (5400 rpm)   Multimedia Drive SuperMulti 8X DVD±R/RW with Double Layer Support   Display 14.1" Diagonal WXGA High-Definition BrightView Widescreen   Fax/Modem High speed 56K modem   Network Card Integrated 10/100BASE-T Ethernet LAN   Wireless Connectivity 802.11b/g WLAN   Webcam Webcam 1.3Mpx   Sound Altec Lansing® speakers   Keyboard 101 key compatible keyboard   Pointing Device Touch Pad with On/Off button and dedicated vertical Scroll Up/Down pad   Memory Card Device  5-in-1 integrated Digital Media Reader for Secure Digital cards, MultiMedia cards, Memory Stick, Memory Stick Pro, or xD Picture cards   External I/O ports 3 USB 2.0, HDMI, eSATA Combo, VGA, RJ-11, RJ-45, Expansion Port 3, 1 Headphone, 1 Microphone

---

### Post by zazuluree on 2009-04-28
PAUK10U
Targus Numeric Keypad with 2-port Hub
Incompatible with Ubuntu

---

### Post by WRISOFT.NET on 2009-04-30
abtop : vaio b100b02
soundcard : sound max untegrated digital audio
manufactureer : Analog Devices.Inc.


hint : ubuntu 7.04 shows that it finds the sound cart prpbably and i can increase/decrese volume but i no sound listen!

---

### Post by garythegoth on 2009-04-30
Laptop:Samsung R60+
Problem:Ubuntu 8.04 wont boot into X-Server.

Ive tried disabling apic and using Safe driver for graphics. It just wont work.

---

### Post by John Cheng on 2009-05-03
**[COLOR="DarkRed"]Sapphire X1550[/COLOR]** - Limited compatibility.
This is an nVidia video card with an RV505 chip.

With **Ubuntu 9.04**, running any OpenGL programs crashes Xorg or sometimes freezes the system. However, simply running Gnome with Compiz effects seems to be ok. However, the screen does blank randomly and QT-based applications shows bizzare artifacts. It has problems with both the open source and binary ATI drivers. It might be worth nothing that this card seemed to work fine with the open source driver under Ubuntu 8.10.

---

### Post by vivichrist on 2009-05-06
Teleman GSR-2100 DVB-S (satellite ethernet) too old and linuxtv crowd can't be bothered with it. but I have 50 of them.

---

### Post by andycc on 2009-05-06
Soundcard
Rocketfish 5.1 PCI Sound Card 
model number RC-51SDCD (Best Buy $25 replaced their dynex model at same price)
Running on Jaunty
This card gets automatically recognized as Creative Labs CA0106 Soundblaster
However, the snd-ca0106 driver does not do the job.
Whenever sound is supposed be present the speakers emit only white noise. Fiddling with the settings on alsamixer results in some some correction  - can actually hear music - or whatever - instead of just noise, but still very distorted.

---

### Post by denisbergeron on 2009-05-07
1)Type Of Hardware : bluetooth dongle
2)Hardware Maker   : IoGear
3)Hardware Model   : GBU 211
4)Known Issue      : Doesn't work with 9.04 64bits but with older version. Dongle detected, but none of the BT config manager can use it.

---

### Post by Amer Zuriekat on 2009-05-11
hi all,

I have problem with my mother board intel dp35dp and the cpu intel quad 6600 neither 32 bits or 64bits works

the previous version 8.04 32 bit was working perfectly :(

what should i do?!!

Regards
Amer

---

### Post by tomski on 2009-05-22
1)Type Of Hardware

USB WIRELESS MOUSE

2)Hardware Maker

LOGITECH

3)Hardware Model

LX8

4)Known Issue

my scroll wheel is now doing back and forward
if i tilt my scroll wheel it is ignored
left & right buttons are ok
as is middle button
my back and forward buttons are ignored

notes:
i think all i need is the correct imwheelrc or xmodmap config file statements to get it back to normal!
i am positive this issue was caused by the fact that XORG no longer reads input device statements as they are now handled by HAL 
BUT all on-line documentation only works with previous versions of ubuntu

---

### Post by Amer Zuriekat on 2009-05-22
> **Amer Zuriekat said:**
> hi all,

I have problem with my mother board intel dp35dp and the cpu intel quad 6600 neither 32 bits or 64bits works

the previous version 8.04 32 bit was working perfectly :(

what should i do?!!

Regards
Amer

Sorry everything worked fine the download iso was corrupted :(

Regards

---

### Post by man_bash on 2009-06-01
> **man_bash said:**
> Motherboard - partial incompatibility

Maker: DFI
model: DFI Infinity NF4X (AMD Socket 754, nForce4 chipset)
Problem: poor support for PCI-e, cannot get any PCI-e card to work with 3-d acceleration (tried nVidia 8800 GT and 8600 GTS). Both video cards work fine in 2-d mode.
Distributions: Feisty, Gutsy, Hardy, & Intrepid, both x86 and AMD64.

UPDATE

Installed Ubuntu 9.04 "Jaunty Jackaloupe", 64 bit on this box, and video card works fine in 3-D mode (nVidia 8600 GTS).

---

### Post by par129 on 2009-06-02
Anyone have any success or failures with Dell's all-in-on XPS One 20''? I'm looking for an all in one for basic uses and I've come across one for fairly cheap in my opinion. It has e4500 and intel x3100 intergrated graphic i think. I might attempt to upgrade some things, but known issues out there?

---

### Post by Lupy on 2009-06-03
Nvidia 8200m
Nvidia
8200m
The display is not aligned horizontally properly. This has become so annoying that I am unable to continue with Ubuntu until I find a solution.

---

### Post by angelxwind on 2009-06-11
Name: Intel 82865G Graphics Media Accelerator Extreme Graphics 2
Issue: Ubuntu 9.04 Jaunty Jackalope does not recognize the card after upgrading to 9.04

Solution: Downgrade to Ubuntu 7.10

---

### Post by mrdrprof on 2009-06-11
Graphics Card
Intel 82865G Integrated Graphics Controller
Using Ubuntu 9.04

A compiz-check states an error was detected; Software rasterizer in use.

---

### Post by mustaghattack on 2009-06-12
Using Ubuntu 9.04

Dell Studio 1537 with the following :
* Intel Core 2 Duo P8400 (2.26 Ghz)
* 3 GB 800 Mhz DDR2 Dual Channel
* 256 MB ATI Mobility Radeon HD 3450
* HDD : 250 GB Serial ATA (7200 RPM)
* Intel WiFi Link 5100
* Webcam 2 MPx

The following is a pain in the asss :
* Hard time to set up my external monitor (24'', 1920x1200). The open source driver is not usable (shitty display) and the ATI proprietary driver is clunky (the interface, "amd catalyst" is a nightmare). Of course HDMI is not working at all.

* The fan never stop : one of my temperature sensor is constantly between 55 and 65 Celsius, I guess that's the one on the graphic card. With the open source ati driver, the temperature goes even higher (> 70 Celsius !)

* Suspend doesn't work. I can see the computer going back to activity when it resumes, but the screen remain black (I guess that's again a pb with the graphic card). Note : this was working with Ubuntu 8.10

---

### Post by riskyayush on 2009-06-12
Toshiba Satellite L305-S5875

Known issues: 

1. 8.10: wifi does not work on initial installation.
Work around: Install MadWifi or switch to 9.04, wifi works like a charm on Jaunty.

2. Function keys do not work.

3. The laptop can not come out of a suspend.

4. Media key for opening a player does not work.

---

### Post by eugenia on 2009-06-14
Motherboard Gigabyte ga-ma78gm-s2h.

MB works fine with Ubuntu 8.10 but continues to restart as soon as I try to load the 9.04 live CD. Even removed the MB from the case, used a new power supply, nothing else connected other than a CD drive (no HDD, absolutely nothing else connected) tested the 2 Corsair RAM, swapped them around and then used them one at a time but the MB still rebooted shortly after starting to read the CD (which I used to install the OS on an older Foxconn K8M890M2MA-RS2 AM2 ALL in One)

Cannot understand as MB is stable with WinXP even when benchmarking (PC User Aust)

---

### Post by Sin@Sin-Sacrifice on 2009-06-15
XFX 750a sli´s nvidia chipset

Known issue (for me):

the nvidia drivers don´t like this chipset in any dist/flavor. I got it working in intrepid but very buggy when using docks and conky-esque software. If I use awn or any other dock I can´t open jpegs or any kind of text file without crashing x and sometimes the whole system. Haven´t tried the proprietary drivers yet though.

---

### Post by mrfotheringham on 2009-06-16
Nvidia Gforce 4 MX440 8X 64MB DDR TV (picked up on installation with NVIDIA accelerated graphics driver (version 96) tried to install and screen resolution went huge)

Canon ip1900

---

### Post by Aacron on 2009-06-22
Ubuntu 9.04
nVidia 550MCP on MSI K9N Neo-F
Sil0680 PCI-PATA card:

Does not recognise RAID stripe set.  Each drive listed separately (sdb sdc sdd, 3 drives)

Working in WinXPpro SP3 with correct drivers.

---

### Post by ktat on 2009-06-30
I'm using Jaunty Jackal - although I've also tried this printer/scanner with Hardy and Kosmic

Please Only List
1)printer/scanner
2)epson
3)tx100
4)was printing ok, then stopped (may be ink levels, but driver can't check these for me).  Never been able to scan, xsane reports that there are "no devices available" after searching.

---

### Post by plaknas on 2009-07-06
1. Laptop
2. Sony
3. Vaio VGN=TT16GN

4. No automatic override for headphone jack. Instead the alsa-base.conf file has to be modified to add a line towards the end that reads "options snd-hda-intel model=3stack-6ch". However, this change works in KMix only for one reboot after which the line needs to be deleted and then reboot and then add the line and reboot yet again. I have been trying to find a solution for this but no luck as of yet.

---

### Post by Leerten on 2009-07-06
Graphics Card
ATI
Raedon Xpress 200
No 3d Graphics running, no drivers by ubuntu.

---

### Post by mccagger on 2009-07-22
Karbon MP3 player
Ubuntu 8.04 (Hardy)
Does not mount correctly upon attaching hardware to USB
Must be mounted manually using $mount -t vfat /dev/sd* /mnt/usb
(* being the ID of the device in /dev)

---

### Post by black911 on 2009-07-22
Hi

I have a DVB Card Called Skystar usb 2

and am trying to Find driver for it

Plz any help ??!!??:confused::confused::confused::(:(:(:confused::confused:

I Use Ubuntu Juanty 9.04

Thanks all[-o<

---

### Post by tokoro on 2009-07-24
Hi i have an ATI Radeon 9550. It's an old card so they just decided that they will stop support for my video card. There are no proprietary drivers available for Ubuntu 9.04. It does work on Hardy Heron though

---

### Post by conradin on 2009-07-25
*-pci
                description: PCI bridge SCSI controller
                product: ABP-3925
                vendor: AdvanSys Advanced System Products
                (AdvanSys BIOS version2.9P)

Did not work when I tried it. I did not explore its failure any further than noting it did not work. This device does work in windows xp. There were no error messages.

---

### Post by hzandber on 2009-08-02
Scanner
Canon
D1250U2F
Not detected

---

### Post by hzandber on 2009-08-02
Printer
Canon
MF4350d
Detected, No driver available

---

### Post by stanca on 2009-08-05
No drivers in 64bit for my canon pixma ip 1300 printer.:(:confused:

---

### Post by damien22 on 2009-08-07
AMD dual core , radeon x1200 not working throwing me in the console!!!
why?

---

### Post by Insomniacno1 on 2009-08-09
IBM Thinkpad 770Z, Ubuntu 9.04 Desktop.

D-Link DWL-650+ does not work with WPA.

NEC PCMCIA USB 2.0 adapter (uPD720101) its not working with any devices, but can supply power to devices and is found when running lspci - but just not working.

JBJ

---

### Post by Hydraah on 2009-08-12
> **Hydraah said:**
> Type: Laptop (specifically, sound, ALC883)
It's the LG P1 Express Dual.

The sound works only through headphones. While it sometimes works via the internal speakers, it will distort and crackle/fade out after a minute or less of sound playback.

Also, you need to change the model in /etc/modprobe.d/alsa-base to 6stack-dig to get any internal speaker sound to begin with.

Hi all,

I managed to find a solution to this. I've only tested this fix under Ubuntu 9.04 and Archlinux so far, but it works!

In /etc/modprobe.d/alsa-base.conf add the following line to the end:

options snd-hda-intel model=laptop-eapd enable=1 index=0

I also have the latest ALSA installed (1.0.20 at this time), and kernel version 2.6.30 (kernel is to speed up the initial wireless connection, takes minutes to begin in 2.6.28!).

I hope this helps someone :)

---

### Post by bw1 on 2009-08-14
I had issues with an MSI g31m3 mothboard and got this reply from MSI:
"Dear Customer, MSI only supports on windows platform,..."

---

### Post by phil8715 on 2009-08-14
Laptop: Asus Eee PC701sd

Using Ubuntu 9.04

Hardware: Samsung YP-Q1 pmp

Issue: Ubuntu Os doesn't recognise the presence of the player plugged in via usb

Samsung stated that they don't support the LInux platform or Mac OS. Just Windows XP

It worked fine on Windows XP.

---

### Post by David Crockett on 2009-08-19
Gateway solo 9300 will not run with Ubuntu 9.04 but is fine with verion 8.10

Regards,
David

---

### Post by COOLDUDEGAMER on 2009-08-22
Creative Soundblaster 16 ISA.

It will not work in Ubuntu 9.X but will work in older versions.

---

### Post by Otustelija on 2009-08-26
Delete: Work thread

---

### Post by ggamauf on 2009-08-27
could the foll msg prevent my linux to recohnize my internet connection?
  - bios (1998) failed cutoff (2000)

---

### Post by djchandler on 2009-08-29
Probably not. Usually the only thing that is a problem due to failing bios cut-off date is ACPI support. 

How are you connecting to the internet?

---

### Post by SickBeast on 2009-08-30
Ubuntu 9.04 w/ all updates installed
Acer Travelmate 4000
Intel 855 chipset is not compatible with suspend/resume.

The system goes into suspend fine, but the screen does not come back on during resume.

This must affect thousands of systems!  Please fix it!  I'm willing to help!

---

### Post by Duncan_Macdonald on 2009-09-13
Radeon 4730 & ATI driver

If you have a Radeon 4730 do NOT select the fglrx driver - it dispays a message "Unsupported Hardware" and stops. The basic generic framebuffer driver does work (but NOT on a HDMI link :( )
The ATI website at the moment has no mention of the 4730 so it may be a while before a new driver that works is available from ATI.

---

### Post by josechapamendez on 2009-09-13
Toshiba M100 mousepad doesn't work...............

---

### Post by riddz on 2009-09-23
TV Tuner Card

Manufacturer: Frontech

Model No: jil- 0606 (BLACK)

Not recognized or No Driver for it to be installed & no software to run the TV Tuner app.

---

### Post by RadiatorNinjaen on 2009-09-23
USB DJ Console
Manufacturer: Hercules
Model: DJ Console RMX
Linux drivers are provided by Hercules and install fine with a standard kernel. However, this piece of hardware is made for live sound perfomances, making Ubuntu Studio with a real-time kernel the preferred distro for lower latency. However, the drivers apparently do not work with real-time kernels. As Hercules do not offer support for the driver, I post the problem here, hoping somebody can fix it from this side. The problem is described in detail here:
[http://ubuntuforums.org/showthread.php?t=1165372](http://ubuntuforums.org/showthread.php?t=1165372)

---

### Post by MP002 on 2009-09-23
Toshiba Qosmio X300-14V
Ubuntu 9.04

What does work out of the box:
- nvidia graphics card after installing restricted hardware
- touchpad
- built-in camera
- card reader (as a side note: BIOS does not allow to select it as a boot device)
- 2 out of 5 speakers but with dissapointingly low sound volume
- monitor brightness
- WLAN
- LAN
- DVD/CD
- USB
- VGA out
- hardware virtualization (I've learned it's extreamly hard to get information on this functionality in notebooks, so I've added it)
- FN keys

What does work AFTER installing and configuring additional software (takes a lot of time; I'm a total newbie in Linux but an expert programmer in Windows):
- all 5 speakers (I'm not sure for the sub though if it's working or not); it is posible also to add and configure a pre-amp slider in sound settings; it gets very loud after that with no sound distorsion of course
- fingerprint reader (but with such small sensor and such poor software the whole thing is quite useless)
- built-in microphone

What does NOT work:
- touch buttons above the keyboard
- IR (infrared) remote (PLEASE, fix this!)
- bluetooth
- hardware sensors (except the GPU temperature sensor)

What was not tested yet:
- HDMI out (I'm positive this should work)
- mic-in (I'm sure this should work)
- built-in modem (I feel this would not work)
- the second hard drive (I'm sure this should work just fine)

---

### Post by dargaud on 2009-09-24
Hercules Webcam Classic
Hercules Webcam Dualpix HD
Neither work, although some people seem to have managed to get the 1st one to work.

---

### Post by Dragokazov on 2009-09-26
Wireless mouse and touchpad on keyboard which comes with every hi-end Desktop All-in-one Sony PC (LV2SJ, LV1S, etc.)

---

### Post by hxleet on 2009-09-28
Brand--Saitek Eclipse keyboard
Model--PZ30AU
Interface--USB 2.0
Issue--Dosent allow for arrow keys to select in GRUB or any partition editors 
or UBCD or on a live session running from Ubuntu cd (at least not for me) could just be that its a usb board.

---

### Post by headmower on 2009-09-30
I have a Sakar model #91739 dualmode camera/webcam which uses a usb port that ubuntu 9.04 and 9.10 doesn't detect. This hardware works fine on Vista or 7. Is there any drivers avaliable for download  or should I try another webcam?

---

### Post by armandh on 2009-10-01
Intel® Desktop Board D201GLY2
[http://www.intel.com/support/motherboards/desktop/D201GLY2/](http://www.intel.com/support/motherboards/desktop/D201GLY2/)

SiS chipset video has tearing vertical lines

---

### Post by lirel on 2009-10-04
Notebook
HP Compaq nx6325

[LIST=1]
[*]Card Reader: XD-Cards don't work
[*]Additional buttons: presentation key(right to rfkill) doesn't create any events to xev
[*]ATI graphics card: S-Video output doesn't work
[*]Broadcom ABG wireless card: no 5ghz-band available, no packet injection
[*]display: brightness adjustment has only 8 of 10steps
[*]internal modem: no driver available
[*]RAM: only 3 out of 4GB available
[/LIST]
with Ubuntu Jaunty Kernel 2.6.28-15-generic

---

### Post by Mi*6d@# on 2009-10-16
Here comes my list.

[B]Ubuntu version: 9.10 Karmic Koala x86-64

[/B] _**LIST**_
**1) Joystick Genius Metalstrike FF** (detected, but unidentified as input device)

---

### Post by Gerald K. Sherman on 2009-10-16
I have an Asus M2N-E SLI motherboard. Linux is giving me an error message that the BIOS does not provide ACPI _PSS objects in a way that Linux understands & says to complain to the BIOS supplier.  I contacted Asus on this & they indicate that they don't support Linux & suggest I contact the Linux community for support.  I do have the system operating after a fashion, as part of the system was cannibalized from an old HP Pavilion that had a networking failure (I took the power supply, video card, & the complete disk drive system - both hard & optical).  Can anybody help me with this?  I am a real beginner to Linux, although I have 4 Linux boxes (2 desktops, a laptop, & a netbook).  This new system has an ATI Radeon Sapphire video card, 250 Gig in the hard, dual DVD drives (1 R/W & 1 RO) & 8 Gigs of DDR2-800 RAM.  The CPU is an Athlon 64X2 5600+ with the core running at 2.9 Gigs  I like the speed of this M/B but the BIOS problem is more than slightly annoying, as I can't switch applications from full-screen to a window, or move the windows around on the desktop.  Don't know if this is the correct place to put this request for help - if I am in the wrong place perhaps someone would be good enough to put this where it belongs.  Thanks.  Gerry, & you can reach me at [EMAIL="ve4gks@mts.net"]ve4gks@mts.net[/EMAIL]
Using version 9.o4 (Jaunty Jackalope)

---

### Post by Lewis Smith on 2009-10-16
Computer: Acer Aspire One D751h-52Bw
OS: Ubuntu 9.10 Karmic Koala (Beta)

Hardware: Speakers/Headphones
Vendor: Acer
Model: Unknown
Known Issue: Sound doesn't work.

Hardware: Screen
Vendor: Acer
Model: Unknown
Known Issue: Screen resolution is 1366x768, however Ubuntu only allows 1024x768.

Bug reports have been submitted for both of the above issues.

---

### Post by andydch on 2009-10-22
OS : Ubuntu Karmic Koala (9.10) - Testing

Hardware : VGA Chipset SIS Mirage 3 M672
Vendor : SIS
:(

---

### Post by aust77 on 2009-10-25
OS: Ubuntu 9.04 Jaunty Jackalope

Device: ACOMDATA storage device
Port usage: USB
Comments: Recognized immediately on Windows 7. Power is plugged in, USB is plugged in, device is turned on, nothing is recognized.

---

### Post by karma koma on 2009-10-29
panasonic toughbook cf-73
graphic: intel i915
net: huawei e510 umts+dvb-t
p4 centrino 1.75 1.5gb ram

ubuntu 9.04 well after installing experimental x.org driver from [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) :D except that no tv worked.

but now karmic koala does not even recognize the modem :(. how can that be?

---

### Post by priegog on 2009-10-31
1)Type Of Hardware: Tablet PC
2)Hardware Maker: Motion Computing
3)Hardware Model: M1300
4)Known Issue: It worked fine up until Intrepid; but it won't even boot with Jaunty or Karmic. 
[Here is the bug report for those interested]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/386272")

---

### Post by henryhmo on 2009-10-31
1)Type Of Hardware: 802.11n Wireless USB ADAPTER
2)Hardware Maker: ENCORE
3)Hardware Model: ENUWI-n
4)Known Issue: It works fine in 9.04 and previous ubuntu release with driver rt2870 from ralink.  But in Karmic, although it can display wireless networks and get through authenticity validation, it can never connect to both encrypted or unencrypted wireless network, by failing seemingly at Obtaining IP step (Indicated by WICD).  I try to re-install rt2870, but in 9.10 it always fails in compiling, even if I lower the gcc version to 4.3 or 4.2. 
Thanks for help!

---

### Post by zoris on 2009-11-01
Hi, disapointment----
No Karmic for me,
 it does not recognise my D-Link ADSL modem router  DSL-504T, I cannot get online at all with it and this unit is not a fossil.
Previous Ubuntu's all had no trouble until karmic.
It is a wired ADSL2 unit, and it is functioning fine in sidux with the latest 2.6.31 kernel, so guess Ubuntu dev's think everone is on wireless, but they are not.
Anyway they do not read this stuff.
So no hope I guess, so much for Karmic, for there is nothing wrong with the unit.
I'll be interested if anyone has any idea what is wrong in Karmic hardware detection.

Best
Zoris:(

---

### Post by Gardrot on 2009-11-01
Toshiba Tecra 8200 512Mb ram cpu 1Ghz
Trident Cyberblade videocard
Ubuntu 9.10 (w WinXp dual boot)

Screen resolution too small, it defaults to 800x600, but should be able to run at least 1400x1050
Creating a xorg.conf got the screen up to 1024x768 but still have a big black border around it :( 
WinXp fills out the whole screen w res at 1600x1280
I hope this wil get solved soon.

---

### Post by gordonngai on 2009-11-02
1)Type Of Hardware: All-in-one desktop
2)Hardware Maker: Acer
3)Hardware Model: EZ1601
4)Known Issue : It can run Ubuntu 9.10 live CD and can detect Wifi card automatically. However after installation with dual boot with XP, get error message when choose Ubuntu (initrd file to big). I have tried to install on USB flash drive. The USB drive installation can work in other computer but get error message with EZ1601.

---

### Post by CDR Services on 2009-11-03
Acer Aspire One 1.25 Gig ram 8 gig solid state drive ssd seems to have issues with Ext4 file system tryed regular install twice and partition manager crashed while trying to read newly created partition and corrupted the drive so badly i had to run a "0 fill" utility to reinstall any os! Third try did a custom partition and left it at Ext3 to get through the install but the boot time was horrible about 2.5 mins and very sluggish performance!  Gone back to 9.04 and everything is cool again.

---

### Post by nick88 on 2009-11-04
ati sapphire radeon pro 2600 agp
Black screen when installing ubuntu 9.10 at starup either by wubi either by cd install

---

### Post by kyleabaker on 2009-11-05
**Microsoft LifeCam VX-1000 doesn't work in Ubuntu 9.10 64-bit.** 32-bit may be working, but in 64-bit it doesn't get past the green screen and static even with the preload tricks.

---

### Post by DarthBrady on 2009-11-05
Ubuntu 9.10 32-bit intel Desktop Edition

All-in-One Printer/Scanner/Fax
Kodak / Kodak-Eastman
5500 AiO
Cannot install. Ubuntu can find the device, has no working 'driver' or ppd for the device.

---

### Post by zoris on 2009-11-06
The anonymity of ubuntu, the latest Karmic is hopeless, it is lost in space no answers on this one.
Borrowed a Billion modem, this worked, but still not impressed.
We are but little grains of sand here.
Installed kubuntu desktop, this did not help either, it only put some dud icons on gnome desktop that needed root privileges to configure them, and no root in ubuntu with gdm.
grrr
zoris:mad:




> **zoris said:**
> Hi, disapointment----
No Karmic for me,
 it does not recognise my D-Link ADSL modem router  DSL-504T, I cannot get online at all with it and this unit is not a fossil.
Previous Ubuntu's all had no trouble until karmic.
It is a wired ADSL2 unit, and it is functioning fine in sidux with the latest 2.6.31 kernel, so guess Ubuntu dev's think everone is on wireless, but they are not.
Anyway they do not read this stuff.
So no hope I guess, so much for Karmic, for there is nothing wrong with the unit.
I'll be interested if anyone has any idea what is wrong in Karmic hardware detection.

Best
Zoris:(

---

### Post by bobnoakridge on 2009-11-07
After upgrading to Karmic 9.10
Laptop.Compaq Presario 2710us.Not compatible with ATI Radeon Mobility M6.Screen shows nothing but lines.Compiz effects not working.If I install Xcompmgr the screen clears up but I get lines that completely obscure Gnome Do and the AWN dock.
Desktop.Using an ATI Radeon 9250 same issues as with laptop.No effects and unless I install Xcompmgr the screen is not viewable.I have tried clean installs with the same result.

---

### Post by the8thstar on 2009-11-07
> 1)Type Of Hardware
2)Hardware Maker
3)Hardware Model
4)Known Issue

I have two unsolved issues:

1. Webcam
2. **Microsoft**
3. **VX-6000**
4. Doesn't work at all with Skype in Ubuntu

1. Printer
2. **Canon**
3. **Pixma ip1500**
4. Doesn't work at all -- even with hacks that supposedly make it work

These two pieces of hardware are the reason I am forced to keep Windows for the moment. I believe the problems I mentioned are Linux/*NIX-wide, not just limited to Ubuntu.

---

### Post by mohdniyas on 2009-11-08
1. Webcam of make Frontech, E-cam(Olive) model no : jil 2222, not working in ubuntu 9.10

dmesg | less shows

usb 3-2: new full speed USB device using ohci_hcd and address 3
[ 6647.958164] usb 3-2: configuration #1 chosen from 1 choice
[ 6647.961058] gspca: probing 0c45:613c
[ 6647.982895] sonixj: Sonix chip id: 12
[ 6647.989082] gspca: probe ok

---

### Post by Xebec on 2009-11-08
0a:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8172] (rev 10)

Wi-Fi is not working in new Toshiba X505 laptop :(

---

### Post by duleep on 2009-11-08
I am using compaq cq40 laptop. now I try to use ubuntu 9.10 with my laptop.I can install the ubuntu to my laptop and grub also loaded. But when I try to load the ubuntu nothing will display and always courser blinking at the top of the screen. I bought my laptop in lastweek and i hv never install any ubuntu version to my laptop. please help what can i do for this problem?

---

### Post by helamsirrine on 2009-11-08
I think it is an LG DVD-Multi drive.
('HL-DT-ST' 'DVDRAM GH41N') 
32-bit Ubuntu 9.10 karmic
Acer Aspire X1301 AMD AthlonII x2 215

Problem occurs when writing to disc.
syslog message```
Nov  7 21:41:39 helam kernel: [ 3867.243796] sr 2:0:0:0: [sr0] Unhandled sense code
Nov  7 21:41:39 helam kernel: [ 3867.243804] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Nov  7 21:41:39 helam kernel: [ 3867.243813] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov  7 21:41:39 helam kernel: [ 3867.243823] sr 2:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Nov  7 21:41:39 helam kernel: [ 3867.243834] end_request: I/O error, dev sr0, sector 0
Nov  7 21:41:39 helam kernel: [ 3867.243844] Buffer I/O error on device sr0, logical block 0
```from k3b fault log```
[FONT=DejaVu Sans Mono]Waiting for reader process to fill input buffer ... input buffer ready.[/FONT]
 [FONT=DejaVu Sans Mono]Starting new track at sector: 0[/FONT]
 [FONT=DejaVu Sans Mono]Track 01:    0 of  690 MB written.[/FONT]
 [FONT=DejaVu Sans Mono]Track 01:    1 of  690 MB written (fifo 100%) [buf  96%]   3.7x.[/FONT]
 [FONT=DejaVu Sans Mono]Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error[/FONT]
 [FONT=DejaVu Sans Mono]CDB:  2A 00 00 00 02 4D 00 00 1F 00[/FONT]
 [FONT=DejaVu Sans Mono]status: 0x2 (CHECK CONDITION)[/FONT]
 [FONT=DejaVu Sans Mono]Sense Bytes: 70 00 05 00 00 00 00 0A 2A 30 02 80 21 02 00 00[/FONT]
 **[FONT=DejaVu Sans Mono]Sense Key: 0x5 Illegal Request, Segment 0[/FONT]**
 **[FONT=DejaVu Sans Mono]Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0[/FONT]**
 **[FONT=DejaVu Sans Mono]Sense flags: Blk 0 (not valid) [/FONT]**
 **[FONT=DejaVu Sans Mono]cmd finished after 0.002s timeout 40s[/FONT]**
 **[FONT=DejaVu Sans Mono]/usr/bin/wodim: The current problem looks like a buffer underrun.[/FONT]**
 **[FONT=DejaVu Sans Mono]/usr/bin/wodim: It looks like 'driveropts=burnfree' does not work for this drive.[/FONT]**
 **[FONT=DejaVu Sans Mono]/usr/bin/wodim: Please report.[/FONT]**
 **[FONT=DejaVu Sans Mono]/usr/bin/wodim: Make sure that you are root, enable DMA and check your HW/OS set up.[/FONT]**
 [FONT=DejaVu Sans Mono]write track data: error after 1206272 bytes[/FONT]
 [FONT=DejaVu Sans Mono]Writing  time:   11.764s[/FONT]
 [FONT=DejaVu Sans Mono]Average write speed 402.2x.[/FONT]
 [FONT=DejaVu Sans Mono]Min drive buffer fill was 96%[/FONT]
 [FONT=DejaVu Sans Mono]Fixating...[/FONT]
 [FONT=DejaVu Sans Mono]WARNING: Some drives don't like fixation in dummy mode[/FONT]**[FONT=DejaVu Sans Mono].[/FONT]**
 [FONT=DejaVu Sans Mono]Fixating time:   64.250s[/FONT]
 [FONT=DejaVu Sans Mono]/usr/bin/wodim: fifo had 211 puts and 20 gets.[/FONT]
 [FONT=DejaVu Sans Mono]/usr/bin/wodim: fifo was 0 times empty and 7 times full, min fill was 96%.[/FONT]
  [FONT=DejaVu Sans Mono]cdrecord command:[/FONT]
 [FONT=DejaVu Sans Mono]-----------------------[/FONT]
 [FONT=DejaVu Sans Mono]/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=4 -tao -dummy driveropts=burnfree -data -tsize=353688s -[/FONT]
```

---

### Post by conradin on 2009-11-08
via VT6421 PCI SATA Card
01:01.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
Subsystem: VIA Technologies, Inc. VT6421 IDE RAID Controller
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 32
Interrupt: pin A routed to IRQ 22
Region 0: I/O ports at d080 [size=16]
Region 1: I/O ports at d000 [size=16]
Region 2: I/O ports at df00 [size=16]
Region 3: I/O ports at de80 [size=16]
Region 4: I/O ports at de00 [size=32]
Region 5: I/O ports at dd00 [size=256]
Expansion ROM at ee200000 [disabled] [size=64K]
Capabilities: <access denied>
Kernel driver in use: sata_via
Kernel modules: sata_via

---

### Post by 1richard on 2009-11-09
I just bought a 320GB USB drive and 9.10 will not see it, Windoes sees it, but  from what I can find out on the internet, this drive needs a special driver.  Does anyone know where I can locate a driver, or how to get 9.10 to see the USB drive.  Thanks

---

### Post by NotWindowsXPagain50 on 2009-11-09
Using Ubuntu 9.04
**Sound Card: **Sigmatel STAC9200

No Sound from it, Ubuntu detects, Intel HDA

---

### Post by Kaner on 2009-11-11
Had Ubuntu 9.04 and have upgraded to 9.1 and am dual booting with Vista.

System Specs

E8400 Intel Core2Duo@3GHZ
Gigabyte MB
BFG GTX 280 1GB Vidcard
XFi Extreme Gamer Soundcard
WD 1TB HDD
4GB Crucial Ram

Both 9.04 and 9.1 work flawlessly with all of my hardware.

---

### Post by oldsoundguy on 2009-11-12
Add to the "do not use" list:

Sparkle Video card (PCI) even though it has an NVida GeForce 9500 chipset.  Will not boot because of an IO error. Tried it in two different computers with two different Linux builds.

---

### Post by tetris11 on 2009-11-15
Add to the 'works only on VESA' list:

Intel i830 graphic chipset (on Dell Inspiron 2600). (i810 and intel drivers dont work)

It did use to work about three years ago on Ubuntu 7.something, but I think it was using XFree86 drivers or something.

---

### Post by ????123856 on 2009-11-15
Via unicrome pro only works with opencrome, unless you download drivers and compile.

---

### Post by glenngds on 2009-11-19
HDTV tuner card
Avermedia
m780
PCI-Express

Not detected by Ubuntu 9.10 x86_64 and not usable.
Forced to keep Windows to be able to use this device.:(

---

### Post by glenngds on 2009-11-20
hardware: compaq presario vr6105nr
incompatible with KDE, video problem.
Font size is 10 to 20 times too big and if I try to open the KDE application menu the displays jumps out of sync horizontally.  Does not work with safe video mode or vesa
 video processor in this computer is Intel ICH7 and cannot put a video card in this computer because it is a laptop.

Gnome works just fine on this computer, but would prefer KDE.

---

### Post by Elijah on 2009-11-23
MSI CR400 laptop

Upgrading to 9.10 results to a flickering screen on bootup, get stuck with a blank prompt. 

It doesn't seem to work with 2.6.31-15 kernel

Sound is gone, it doesn't seem to detect it anymore.

---

### Post by molder on 2009-12-26
Only when in combination:
D-Link WDA-1320 Wireless G PCI card
ATI HDTV Wonder TV Tuner PCI card

Mythbuntu will not boot.

---

### Post by 2lagos on 2009-12-30
I get a message like, failed to load kernel windows has shut down any help?

---

### Post by javasaad on 2010-01-01
Laptop HP Pavillion DV5 1116em 
Core 2 Duo Don't work , 
i test all method but don't work
I hate this Laptop brand !!!!!!!!!!!!!!

---

### Post by trinnyg on 2010-01-04
Asus 904 HA - specs - Failed Video Resume Mode

Intel CPU & Chipset  	Intel® Atom N270 (Dothan)
 L1 Cache: 32 KB
 L2 Cache: 512 KB
Wireless Data Network 	WLAN: 802.11 b/g
Memory 	2GB (DDR2) 
Video Intel 945 Express Integrated Chipset
Hard Drive : Hitachi HTS543216L9A300 Travelstar
160 GB - 5400 rpm - 2.5" - Plug-in Module
1 x 7-pin Serial ATA/300 Serial ATA

Loaded Ubuntu 9.10 Full version KDE 4 does not recover from Sleep mode with the internal video reinitalizing.

---

### Post by Stormspace on 2010-01-04
TDK DVD drive. Fails during install on 9.10, no driver found.

---

### Post by jitendrasnv on 2010-01-06
HELLO !!!!

when ever i install a fresh copy of windows Xp then the sound driver for my mother board doesn't work and for every time i have to download a new sound driver.

can any one suggest me for this?

Thanks

---

### Post by mowersman on 2010-01-08
Net-lynx wp61r2 wireless card
ubuntu will not run from the live cd or run if installed. tried on two computers

---

### Post by bigbossVII on 2010-01-12
Acer Aspire 5515

Ubuntu 9.10

Acer Crystal Eye Webcam (intergrated) isnt even recognized
used a generic audio card driver instead of Realtek Audio driver ver. 6.0.1.5657
used a generic video card driver instead of ATI VGA Driver ver. 8.520.0.0 - cant access 3D graphics, could before switch

Wifi is ok

---

### Post by hendoc on 2010-01-12
I am running Ubuntu 8.10. I have a Cables unlimited USB to IDE adapter. It says it supports Windows and Mac, but, at only $22, I thought I'd give it a shot. Ubuntu does not see the Hd ( at least, it does not list it under "computer". Cables Unlimited, of course, has no drivers for Linux. Do I have to go back to dual booting?

---

### Post by hendoc on 2010-01-13
Set the jumper pin on the HD to "Master" and this issue is solved. Thank you.

---

### Post by user11 on 2010-01-14
Software: Ubuntu Karmic x86

Hardware: Floppy drive

Issue: Does not detect floppy diskette

---

### Post by viper250 on 2010-01-19
a lot of hardware is windows only and will not work with linux 
its better to check out the compatability list for the distro you plan to use and then change the hardware or search and locate drivers. 
submitting info such as manufacturer, chipset, ect can help developers write driver files

---

### Post by k64 on 2010-01-23
ATI TV Wonder 650 Tuner: No driver exists.

Linksys WUSB54GSC Wireless Network Adapter: Even NDISWrapper doesn't work.

---

### Post by thermal_dl on 2010-01-25
[B]Sony Vaio CW series Laptop,Intel i5, Nvidia 330m 512MB
1)Type Of Hardware - Video Card
2)Hardware Maker - Nvidia
3)Hardware Model - GeForce 330m - 512MB
4)Known Issue - When updating the drivers to the recommended 185.xxx drivers, the display monitor is not recognized and the screen becomes blank.
[/B]"For some reason, the current nvidia driver does not auto-detect that a display is attached to an internal digital port. Even if you force the driver to assume a display is attached, it is still unable to read the EDID information from the display. It is this information which tells the driver how to drive the display. Starting X yields just a blank screen."
See:  [http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22](http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22)

Also, someone recommended using the Phoenix EDID designer to fix this problem as they could not fix it with the softMCCS program.

I have not yet tried this solution yet.  Otherwise, Ubuntu 9.10 works without the updates.

---

### Post by uaebuntu on 2010-01-26
Broadcomm 5338 WiFi adaptor
Ubuntu 9.10
Dell Latitude E6400
Does not work with Open or Propriety drivers, blue indicator led did not light and no connection could be made, swapped with Intel WiFi card and all OK.

---

### Post by AmrH on 2010-01-27
Printer
Canon
I-SENSYS LBP3010B

No drivers for 64bit Linux; however, it works with the 32bit version.

---

### Post by shepherdpeter on 2010-01-31
Karmic Koala
Envision 1770 17" CRT Monitor
Does not recognize monitor, and System-Preferences-Display will not allow me to set the proper settings for the monitor.  Consequently, everything is too big on the monitor, and will not fit on the screen.

In previous editions of Ubuntu, in particular, Hardy Heron, I can't even get a display on the monitor - it goes immediately to command line when I boot it up.

---

### Post by seancameron on 2010-02-05
Intel Corei3 integrated graphics using 9.10 64 bit. Locks up as soon as any menu is displayed, half way through the "fade" effect.

Note that disabling Compiz resolves this issue. Apparently Ubuntu doesn't work very well with Intel's graphics solutions. Pretty poor.

---

### Post by dmasc on 2010-02-07
Sony VAIO VGC-LV1S wireless mouse (VGP-WMS3) and touchpad on keyboard (VGP-WKB9FR) aren't working under Ubuntu 9.10 Desktop (but keyboard itself does).

---

### Post by Mirko Scurk on 2010-02-18
Booting any version of ubuntu from live cd results in blank screen with message out of range for
 
ASUS monitor VH222D. 

One should create custom xorg.conf and add some options for monitor.

K8M890 mobo with integrated via chrome graphics paired with this monitor displays redraw mistakes with vesa driver and nothing with openchrome driver.

---

### Post by cnja on 2010-02-20
Ubuntu 9.10 64bit
Gateway NV52 series laptop

- Wireless (Atheros AR928X) was a hassle until d/l and install linux-backports - fixed issue.:p
- issue with sound, unable to record and then play back sound with out having to reboot     and jump through a couple of hoops :confused:

sound is detected as ATI Technologies RS780/Conexant....

---

### Post by dabl on 2010-02-21
> **user11 said:**
> 

Issue: Does not detect floppy diskette

```
sudo modprobe floppy
```

---

### Post by LinuxGold on 2010-02-23
1.) Laptop
2.) Gateway
3.) M685
4.) When not docked, Ubuntu 9.04 setup went fine, was able to boot into using 1440x900 resolution video.  But when I dock the laptop, the display became garbled, second monitor (attached to the docking station) is blank.

Video card is nVidia G70 GeForce Go 7600

---

### Post by Objekt on 2010-02-23
Probably old news, but:

1) printer
2) Canon
3) Multipass F60
4) Not supported under any Unix/Linux printing system (CUPS et al).  No .ppd driver exists.  This is a Winprinter, totally reliant on a Windows-only software package to work at all.  Therefore, no support under:
-Kubuntu 8.04, 8.10, 9.04, or 9.10
-Ubuntu 8.04.4, 9.04, or 9.10

---

### Post by quadproc on 2010-02-24
Canon i860 printer

This printer will not work with a print server such as the HP J2591A or the D-Link DP301P+; the printer just ignores the server even though the server and the computer communicate just fine through Ethernet.  Yet the printer does work when plugged into a parallel port in the computer.

Other printers do work with these print servers.

---

### Post by geoff123 on 2010-02-24
Lucid/Karmic

Samsung SyncMaster 245BW Monitor
It runs at the wrong default resolution as 1680x1050.  I always have to manually configure xorg.conf to make it use 1920x1200.  I blame the monitor for not being standards compliant and giving wrong EDID information to xorg.  Samsung is off my next monitor list - too much work.

---

### Post by jayant_id on 2010-03-03
_**Hardware**:_ 

- Motherboard  :          ASUS M2N-MX SE PLUS
- Processor      :          AMD Athlon LE 1620, 2.4 GHz
- Monitor         :          Viewsonic VA 1716w, Widescreen 17" LCD
- Graphics card:           NVIDIA GeForce 6150 SE
- RAM             :           2GB  
- BIOS             :          AMIBIOS  v0503

_**Base OS**_:
Windows XP SP3 Home Edition (32-bit)

_**Other**_:
Have installed monitor & NVidia driver CDs
Am trying to install Ubuntu 9.10(32 bit) via wubi (windows ubuntu installer)
Have also tried(without success) installation using CD.

_**Problem**_:
During installation I see ubuntu logo followed by LCD screen going blank with error 
"Out of Range".
_Note_: Ubuntu Installation is successful if I swap my LCD with my friend's CRT(Viewsonic VA 30)

Have tried troubleshooting by tweaking one or more of the following parameters:
- screen resolution (600 * 800)
- refresh rate (59/60/75 Hz)
- color qwality (32/16 bit)
No success.

Please help & let me know if anybody needs more information.

---

### Post by RealG187 on 2010-03-04
> **jayant_id said:**
> _**Hardware**:_ 

- Motherboard  :          ASUS M2N-MX SE PLUS
- Processor      :          AMD Athlon LE 1620, 2.4 GHz
- Monitor         :          Viewsonic VA 1716w, Widescreen 17" LCD
- Graphics card:           NVIDIA GeForce 6150 SE
- RAM             :           2GB  
- BIOS             :          AMIBIOS  v0503

_**Base OS**_:
Windows XP SP3 Home Edition (32-bit)

_**Other**_:
Have installed monitor & NVidia driver CDs
Am trying to install Ubuntu 9.10(32 bit) via wubi (windows ubuntu installer)
Have also tried(without success) installation using CD.

_**Problem**_:
During installation I see ubuntu logo followed by LCD screen going blank with error 
"Out of Range".
_Note_: Ubuntu Installation is successful if I swap my LCD with my friend's CRT(Viewsonic VA 30)

Have tried troubleshooting by tweaking one or more of the following parameters:
- screen resolution (600 * 800)
- refresh rate (59/60/75 Hz)
- color qwality (32/16 bit)
No success.

Please help & let me know if anybody needs more information.

I sometimes have it say out of range only on the boot screen, but once Ubuntu loads it's fine (usually if I use an installation made from a CRT monitor then switch to LCD)

---

### Post by N00b-un-2 on 2010-03-06
I just bought a new LITEON Blu-ray drive (model number iHOS 104-8 3) for my previously working HTPC and it is not detected in ANY linux distro I've tried (Ubuntu/Mythbuntu/Xubuntu/Kubuntu 9.10, 9.04, 8.10, and 8.04) and I tried the alternate install discs, as well as a few versions of Linux Mint and openSUSE.  I'm going to give SLED and Fedora a shot to see if that might help.  Typically, what happens is when I put in a disc and boot up, I get as far as loading the linux kernel and then I get a message saying that there is no medium with a live file system available, causing me to believe that there are no BD-ROM drivers for linux.  How can that be?

---

### Post by trorion on 2010-03-07
> **N00b-un-2 said:**
> I just bought a new LITEON Blu-ray drive (model number iHOS 104-8 3) for my previously working HTPC and it is not detected in ANY linux distro I've tried (Ubuntu/Mythbuntu/Xubuntu/Kubuntu 9.10, 9.04, 8.10, and 8.04) and I tried the alternate install discs, as well as a few versions of Linux Mint and openSUSE.  I'm going to give SLED and Fedora a shot to see if that might help.  Typically, what happens is when I put in a disc and boot up, I get as far as loading the linux kernel and then I get a message saying that there is no medium with a live file system available, causing me to believe that there are no BD-ROM drivers for linux.  How can that be?

if it's SATA bdrom then try moving it off your primary SATA array and switching the bios to IDE for your secondary array (mine for example has SATA 1, 2 and 3 on SATA1 and 4&5 on SATA2).  Worked for me with my LG BDrom.

---

### Post by nmr on 2010-03-19
Ubuntu 9.10
1GB RAM
Pentium 2,4 GHZ

Sound Blaster X-Fi Xtreme does not work
OnBoard Sound Card does not work

I have tried about 5 or 6 sets of instructions from this forum and others, and I still can't get sound on my PC using Ubuntu. Every single How to I have found does not work. And, yesterday, I had the help from a somewhat experienced Ubuntu user (though we were talking through IM, so he did not actually work with my PC), going again through the How to's posted here and elsewhere, for about 3 hours. And we both failed to bring sound to my Ubuntu installation. (we installed the open source beta driver by Creative Labs, and followed the steps in every different suggestion, one at a time).

Everything else seems to be working fine. Performance is great, twice as fast as it was with Windows Vista, just a few days ago. My PC is an old 2003 Pentium. And no one would tell my PC is 7 years old. It's incredibly fast now, with Karmic.

So, I am a complete noob. And I am loving Ubuntu. I read in some forum a user saying that the effort of tuning up Ubuntu was worth it, because in the process the user learns a lot about the OS. Well, that was the case for me. Yesterday I spent 3 hours trying to make the sound card work. I did not get it yet, but I learnt a lot about using the terminal, basic commands and about where things are in Ubuntu.

---

### Post by Anderson Brasil on 2010-03-26
I would like to report that the live CD of ubuntu 9.10 (as well as kubuntu 9.10 and the derivative work linux mint helena) don't work at my hardware: athlon x2 4600+, with motherboard asus m2n68-vm (a quick research at google, showed me a few users of the same motherboard with the same issue). After some time, the screen becomes a lot of vertical green lines and after a while, a completely weird collection of collorful spots. It may or may not be related to this issue, but I remember once trying to install the "resulinux" distribution at the same machine, and it was (incorrectly) detecting the onboard video as if it was ATI. 

The weirdest part is that kubuntu 9.04 CD worked perfectly fine with exactly the same hardware, which allowed me the workaround: install kubuntu 9.04 and then upgrade it to 9.10. Anyway, it sucks to need to use such indirect way. I hope that it is fixed soon.

Cheers,

Anderson Brasil.

---

### Post by exd7 on 2010-03-30
Hardware:
MSI A6200
Core i5-430M
Graphics are integrated in the processor itself, named Intel GMA HD

Problem:
I get no display whatsoever. Ubuntu 9.10 installs correctly, as far as I can tell, but I get no display. I hear the login screen sound, but nothing shows up.
My hunch is that, because the GPU is technically the CPU (somehow, not sure how that works, but that's what I believe the setup of i5's are), Ubuntu is not detecting a graphics device.
Any workarounds?

---

### Post by DOGBOT on 2010-03-31
Hi 
i have just started to get to know linux a bit of a novice really.
Just need to be pointed in right direction on makeing crossfire to work ,with two ati radeon hd2900 xt cards , the os i am useing is kermic koala , i seem to have one card working but system doesnt seem to recognise second adaptor can you help please.:)

---

### Post by galegUbu on 2010-03-31
acer aspire 5740-6025
Core i5
lucid lynx, beta 1 (10.04)

multi-touch pad does not work, 'two-finger scrolling' option is disabled in preferences >> mouse >> touchpad tab. Worked with original install of Windows 7.

---

### Post by nismo_2005 on 2010-04-01
geforce 8400gs

the card is black listed by compiz and has problems loading games.

os - ubuntu 9.10

---

### Post by aaronlopez9210 on 2010-04-01
Toshiba Satellite Laptop
Kubuntu 9.10
keyboard & touchpad worked before installation, and after it stopped working completely

---

### Post by carfreak on 2010-04-06
I used to work with Ubuntu 9.10 flawlessly =D>, untill I bought a canon scanner lide 100. 
So far, I can't get it to work under Ubuntu, but under Windows XP it works just fine, and that's why I switched "back" to windows.

I hope you find a solution for this issue, since "unfortunately" I'm a BIG FAN of UBUNTU, and now I'm using Win XP :(

---

### Post by 3177 on 2010-04-30
> **aaronlopez9210 said:**
> Toshiba Satellite Laptop
Kubuntu 9.10
keyboard & touchpad worked before installation, and after it stopped working completely

just had that problem too in ubuntu
it works though
i just had to reboot
weird

---

### Post by thekat on 2010-04-30
Dell latitude 
E6500 
OS: Netbook REmix Lucid 

- Stand by does not work (have not tried hibernation)
---  Stand by did work on Karmic 

Everything else on Lucid does work so far.. and no
I will not be going back to Karmic.. keep up the good work
Ubuntu Devs.. 

charles

---

### Post by noway on 2010-05-04
HP Pavilion zd7000 (more specifically zd7150ea)
NVIDIA GeForce FX Go5600

Tried to install with the following discs:
ubuntu-10.04-desktop-i386.iso
ubuntu-10.04-alternate-i386.iso

The laptop used to have 9.04 which worked just fine. Formatted the hard drive and did a clean install. 
With ubuntu-10.04-desktop-i386.iso it hangs at 89% when it says "looking for packages to remove".
With ubuntu-10.04-alternate-i386.iso it hangs at 82% during "Configuring software-center"

---

### Post by sbike on 2010-05-07
Something about ubuntu 10.04 breaks the CM8738 driver.  Either no audio at all comes out of earphones or stereo speakers, or sometimes you get the rear channels instead (which usually has no dialog).

---

### Post by dE_logics on 2010-05-12
Nvidia 6100 showing various problems like no standby, dmps features if starting manually (like suspend, off) does not work properly.

This problem cannot be solved...it's an nvidia binary problem.

---

### Post by eckeroo on 2010-05-12
OS: Lucid 10.04 (32 bit)
Processor: 1733MHz [2100] Athlon XP [palamino] processor
MB: ASUS A7M266, BIOS version [1008.02b]
Memory: 1Gb 266DDR PC2100
PCI USB 2.0 Card: PC Line VIA VT6212L chip set

doesn't work with:

Sansa clip 2GB (set to MSC mode and formated), firmware: V02.01.32F 
The Sansa clip will not mount on my USB 2.0 ports on the PCI USB 2.0 Card  but do mount on USB 1.1 ports on the motherboard.

My kingston 6GB USB memory stick does mount on the USB 2.0 ports

---

### Post by oldsoundguy on 2010-05-12
> **eckeroo said:**
> OS: Lucid 10.04 (32 bit)
Processor: 1733MHz [2100] Athlon XP [palamino] processor
MB: ASUS A7M266, BIOS version [1008.02b]
Memory: 1Gb 266DDR PC2100
PCI USB 2.0 Card: PC Line VIA VT6212L chip set

doesn't work with:

Sansa clip 2GB (set to MSC mode and formated), firmware: V02.01.32F 
The Sansa clip will not mount on my USB 2.0 ports on the PCI USB 2.0 Card  but do mount on USB 1.1 ports on the motherboard.

My kingston 6GB USB memory stick does mount on the USB 2.0 ports



Sounds more like a card problem than a device problem.

---

### Post by Toast2120 on 2010-05-13
My system
Athlon 4200
2 evga nvidia 8800 GTS 512, in SLI
2 GB RAM

My issues

9.10
Install went fine. Sound worked. Then I installed the nvidia 185 drivers.
After reboot saw the Ubuntu splash and then nothing, screen was out, connected but nothing. But sound works as I heard it beep.

My post is here
[http://ubuntuforums.org/showthread.php?p=9287433#post9287433](http://ubuntuforums.org/showthread.php?p=9287433#post9287433)

10.04
First install attempt was last week, didnt get to the installer, crashed

My error message is the same Installation Failed thats going around "The installer has encountered an unrecoverable error. A desktop session will be run so that you may investigate the problem or try installing again." 

Second attempt now it crashes but goes to a live boot, was considering to install it that way but avoided as I dont want to break Windows. Went back to 9.10 hoping it would be stable with nvidia drivers but that didnt work either.

Any solutions for either is fine by me.

---

### Post by 3177 on 2010-05-13
> **Toast2120 said:**
> 


Install went fine. Sound worked. Then I installed the nvidia 185 drivers.
After reboot saw the Ubuntu splash and then nothing, screen was out, connected but nothing. But sound works as I heard it beep.



reboot using the live disk and check your graphics drivers.
Ubuntu's been having trouble with Nvida cards lately
make sure you have the right driver for your card

---

### Post by Locke2053 on 2010-05-13
Belkin "Wireless N" USB wifi card using the RT2870 chipset.

Note that this card can be made to work by compiling your own drivers, but the Lucid kernel is misconfigured as shipped.

---

### Post by Toast2120 on 2010-05-13
> **3177 said:**
> reboot using the live disk and check your graphics drivers.
Ubuntu's been having trouble with Nvida cards lately
make sure you have the right driver for your card

Where do I check for the drivers, as in what folder? I know nvidia installs to separate locations. And how I do know? Will the drivers be specified?

---

### Post by agongpor on 2010-05-19
Laptop Axioo TVW 116

Graphic card
SiS M672/ SiS Mirage 3
Ubuntu 10.04

The highest resolution only 800 x 600 (4 : 3) instead of 1280 x 800 (16 : 9)

---

### Post by nanomiter on 2010-05-21
Toshiba Satellite R15-S829
Ubuntu 10.04
Ubuntu Netbook Edition 10.04
Neither will install, both hang prior to the splash screen

---

### Post by dndposey on 2010-05-21
Older Sony VIAO laptop (circa '00) doesn't recognize
Bluetooth USB adaptr.  Just upgraded to 10.04 from 9.1

---

### Post by 3177 on 2010-05-22
> **Toast2120 said:**
> Where do I check for the drivers, as in what folder? I know nvidia installs to separate locations. And how I do know? Will the drivers be specified?

sorry its been so long since I replied, As I myself do not have an Nvida card I do not know where they install.(you said they install elsewhere).  As I said before, I had just read a lot if stuff pertaining to ubuntu's lack of Nvida support.
There are a lot of other forums on your exact problem though. Search NVida on the forums. I doubt it will take you too much longer to get things working.(If you haven't already)
hope the best with Ubuntu for you.

---

### Post by cub on 2010-05-24
This is a combination of Sony Vaio laptop and Edirol UA-25EX external sound card

1)Type Of Hardware - Laptop
2)Hardware Maker - Sony
3)Hardware Model - Vaio VPCEB1S1E
4)Known Issue - Will not work with Edirol UA-25EX USB sound card in Advance Driver mode

1)Type Of Hardware - USB sound card
2)Hardware Maker - Edirol
3)Hardware Model - UA-25EX
4)Known Issue - It will not work with this specific Vaio and JACK in Advance Driver mode. Only "normal" mode in 16 bit and 44.1 kHz is possible.

This was tested on both 9.10 and 10.04. Same issue.

---

### Post by Dr.FrankenMod on 2010-05-30
System: HP DV8000 laptop
OS: Ubuntu 10.04 
Problem: On board Headphone jack does not work, Mute button does not work
Have not been able to find solution

---

### Post by CoolRabbit on 2010-05-30
In Brasil: 
Positivo Premium R430L - has a SiS 671 video card witch doesn't work out of the box (see below a fix) and a Realtek rtl8187b onboard wi-fi card that only works if it is 2-3 meters from router. 



Go to this post and the 671 SiS will work ...

[http://ubuntuforums.org/showthread.php?t=958967&page=38](http://ubuntuforums.org/showthread.php?t=958967&page=38)

---

### Post by Roly25 on 2010-06-04
Ubuntu Version: 10.04 Netbook Edition
Hardware: Advent 4213 Netbook (Sorry I don't know all the individual makes of the different components)

Everything seems to work out of the box.  I've not tried Bluetooth  or Wired Ethernet But Webcam works out of the box, Wifi works out of the box and 3G modem works out of the box.

Battery charge doesn't seem to hold in Hibernation and once it's started charging if you pull plug out it goes into Hibernation witch is a pain and if I can't work out how to solve it I'll probably end up going back to windows.

Roland

---

### Post by Old Newville on 2010-06-06
Dell All-In-One Printer 964 does not work.
Ubuntu detects the printer but there are no drivers available for it. Same goes for the built-in scanner and memory card reader.
Solution is to run Windows XP in VirtualBox and pull files across from Ubuntu for printing; or to scan documents or memory cards in Windows and save them to a USB stick for retrieval in Ubuntu.
I've had this problem with Lucid Lynx and Hardy Heron. My computer is a Dell Dimension 4600.

---

### Post by Macchi on 2010-06-06
Sony Vaio VGN-B1XB will not work out of the box with Ubuntu 10.04 LTS
due to problems with the latest kernel and graphics software on Intel integrated graphic chipsets 855 etc. As a workaround you may chose earlier kernel releases or search for other hacks through the forum.

---

### Post by Macchi on 2010-06-06
Asus EEEPC 900 and Asus EEPC 701 have several issues with Ubuntu 10.04, with limited functionality of the touchpad, microphone problems, critical limitations for the small screen resolutions (especially for the 701 that has 800x400), and power management problems while running these netbooks on battery.
Ubuntu is recommended only if you have the time and skills to apply a series of documented workaround to be found on the wiki and forum.

---

### Post by joaojotta on 2010-06-07
HP Pavilion dv1000
Intel(R) Pentium(R) M processor 1.60GHz
1GB+256MB RAM
82852/855GM Integrated Graphics Device

Wont's go past the splash screen:
Ubuntu 10.04
Ubuntu 10.04 Netbook Edition

Updating from 9.10 won't work either.

---

### Post by maxpain007 on 2010-06-16
I am using a compaq  Evo n610c . My hardisk is not showing in computer... and no other usb is detected as well!! and in the disk utility no hardisk is detected ..my worst experince with ubuntu 10.04 ..i am the unluckiest man on earth..i installed ubuntu 16 times and formatted 16 times in ONE DAY.....OEFF!!

---

### Post by dynamicshyam2006 on 2010-06-17
hi

i have intel Pentum ||| 800 EB MHZ (133*6.0) with 256 MB RAM.
i am  installing  Ubuntu 9.04 but this hardware is not supportable.

---

### Post by bertvv on 2010-06-17
On Ubuntu Lucid Lynx (10.04) 32 bit

1)Type Of Hardware: Graphics card
2)Hardware Maker: nVidia
3)Hardware Model: GeForce 330M (ID 10de:0a29)
4)Known Issue

Not supported by nouveau, nor by the proprietary nVidia drivers in the repository (version 185). You have to manually download the driver from the nVidia website and install it, after removing the drivers from the Ubuntu repository. You have to redo the installation after each kernel upgrade.

---

### Post by cascade9 on 2010-06-17
> **bertvv said:**
> On Ubuntu Lucid Lynx (10.04) 32 bit

1)Type Of Hardware: Graphics card
2)Hardware Maker: nVidia
3)Hardware Model: GeForce 330M (ID 10de:0a29)
4)Known Issue

Not supported by nouveau, nor by the proprietary nVidia drivers in the repository (version 185). You have to manually download the driver from the nVidia website and install it, after removing the drivers from the Ubuntu repository. You have to redo the installation after each kernel upgrade.

Change from nVidia 185 (which is old) to nvidia-current and that problem should be fixed. 

[http://packages.ubuntu.com/lucid/nvidia-current](http://packages.ubuntu.com/lucid/nvidia-current)

---

### Post by fendermon on 2010-06-17
Okay..I've got one..

Samsung Super Writemaster  SH-223 dvd..,  It won't work in any manner on my new Lucid or Mint installs. I had the odd circumstance of having bought two of them and installing in two separate machines, both running Lucid. Cds skipped horribly until they crashed out, data cds unreadable. 

Being a consummate distro hopper I fired the Samsung up in Debian (Antix) and Slackware (Salix) and, for the heck f it..Xp. 
Zero problems with those. I then swapped out the Samsung for a LG drive and booted up Lucid. I am listening to flawless cd play now as as I type this.

 -  Bill

---

### Post by d.ericsson on 2010-06-29
Ubuntu 10.04 LTS
HP Pavillion dv6-3006tx 15.6" laptop
Intel® Core™ i5-430M processor
4096MB DDR3 1066MHz (2 Dimm)
 802.11b&#8260;g&#8260;n WLAN 10&#8260;100 ethernet
ATI Mobility Radeon™ HD 5650 with 1GB

Failed to disable the Touchpad, which is big enough, and close enough to the keyboard, to constantly interfere with typing. Giving commands via synclient would inactivate it for at most 30 seconds. Uninstalling the xserver-xorg-input-synaptics package had no effect. Other approaches, similar to [these]("https://help.ubuntu.com/community/SynapticsTouchpad"), also failed.

---

### Post by nike234 on 2010-07-04
The Epson EPL-6100L Printer is recognized and installed fine but it doesn't print! Not even the test-page! It is the only Printer plugged into my computer. It works nice when plugged to my notebook with Win7.
Googled it, but didn't find a suitable answer.

-greetz Nike234

---

### Post by ScubaDrew on 2010-07-08
> **bethnesbitt said:**
> I've tried everything out there from ndis wrapper to the atheros chipset linux driver, nothing on my new EDUP Wireless Adapter PCI 2.4ghz

Same issue with edup 54m - worked on the version 9 ubuntu but not on the 10 release.

---

### Post by foresthill on 2010-07-08
> **d.ericsson said:**
> Ubuntu 10.04 LTS
HP Pavillion dv6-3006tx 15.6" laptop
Intel® Core™ i5-430M processor
4096MB DDR3 1066MHz (2 Dimm)
 802.11b&#8260;g&#8260;n WLAN 10&#8260;100 ethernet
ATI Mobility Radeon™ HD 5650 with 1GB

Failed to disable the Touchpad, which is big enough, and close enough to the keyboard, to constantly interfere with typing. Giving commands via synclient would inactivate it for at most 30 seconds. Uninstalling the xserver-xorg-input-synaptics package had no effect. Other approaches, similar to [these]("https://help.ubuntu.com/community/SynapticsTouchpad"), also failed.

I use this command to disable mine:

[PHP]xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 0


[/PHP]

---

### Post by HDTimeshifter on 2010-07-10
Ubuntu 10.0.4 LTS 64-bit
ASUS P5Q Pro motherboard

GE WK3803 PS/2 optical mouse won't work.  No cursor movement when I boot up with this mouse plugged in.  Anybody with this mouse able to get it to work?

---

### Post by nikitis on 2010-07-11
MadCatz Cyborg R.A.T. 7 Wired mouse.  Just released in June.  It appears to work out of the box except it doesn't fully.  I've tried this on two machines, one running Kubuntu and one running Ubuntu.  On both KDE and Gnome, After a few seconds of being logged in, I cannot drag a window, click on buttons, or even select windows to be on top.  I know it's not the mouse per se malfuctioning because in kde, I can still click on the "K" Start menu type button at the bottom right, but other buttons no longer work.  If I change modes on the mouse (Yes it has like 4 different modes as well as 4 DPI settings that you can change in hardware.)  Selection will work again but then a few seconds later the process repeats.  I did a tail -f /var/log/syslog and tail -f /var/log/messages, and there is nothing going on except for the plug in and out events.  Lots of people are going to want to buy this new mouse as it's a gaming enthusiasts dream mouse.  Would like a firmware driver written for this as I think with all of the extra's this mouse comes with that most mice do not have, it will need one to work fully.

Goes up to 5400 DPI!

---

### Post by BrunoSilva on 2010-07-12
LG GP08NU6B External Optical Drive
It's not recognized.
Doesn't mount CDs or DVDs.

$ lsusb
Bus 008 Device 009: ID 152e:2571 LG (HLDS)

---

### Post by cfinc on 2010-07-18
HP Pavillion dv5 touchpad
Works when the touchpad is on but when i turn off touchpad with a button so that i can use my mouse, the GNOME interface becomes unresponsive.
ubuntu 10.04

---

### Post by UptownRedLine on 2010-07-19
Custom built PC.


[LIST]
[*]Acer H233H Monitor
[*]Asus M4A78T-E Motherboard
[*]Atheros L1E On-Board NIC
[*]AMD Phenom II X4 965 Black Edition
[*]North Bridge AMD 790GX
[*]South Bridge SB750
[*]ATI Radeon HD 3300 built-in 128MB DDR3 1333
[*]VIA VT1708S 8 Channel On-Boar Audio
[*]2 DVD+RWs (HP 1270 & HP 1260)
[*]Western Digital Caviar (Green) WD5000AAVS
[*]External Seagate Free-Agent HDD
[/LIST]
Everything is working perfect. For the On-Board NIC, remember, you have to enable it in your BIOS for it to work!

---

### Post by thelethargarian on 2010-07-21
Laptop Computer
HP
G60-508us
Headphones jack does not mute speakers,
Touchpad button does not turn off touchpad,
fn+F6/F7 does not adjust screen brightness down/up

---

### Post by ansary on 2010-07-22
ATI Mobility Radeon HD 5470
Bluetooth 2.1+EDR

---

### Post by Hogberg on 2010-07-25
HP dv7-3199eo
1.
Sound in/out problems

5 Series/3400 Series Chipset High Definition Audio
Many people have problems. Different problems depending of what computer... 

2line from lspci. For me it can be a part of the problem.  
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
****
2. Battery indikator don't work. Showing battery is charing but isn't. Can't show right %. Boot with no power loading can make the indicator cord for some time.
****

---

### Post by edwinava1964 on 2010-07-26
Dear Ubuntu Communnity,

Acer Aspire M1800 (Desktop) with pre-installed NVIDIA® GeForce® 7050 and nForce® 620i,
Ubuntu 9.10 keyboard and mouse hang after successful installation. too bad, so tried ubuntu 10.04, worse this time,
after successful installation to the same partition (the other one is Windows 7 working fine), the screen is showing white snow and system hangs. Hope the next 
version has vast improvement for Acer Aspire users. 

By the way, the same cd that failed works perfectly fine on my Acer Aspire laptop (2920z)

Yours sincerely,
Ed

:popcorn:

---

### Post by corrytonapple on 2010-07-26
I have a Toshiba L455 with Ubuntu 10.04. The fan control with Ubuntu doesn't work, and none of the Function keys work.

---

### Post by oldsoundguy on 2010-07-26
To the moderators:
This thread has become increasingly long because some people can not read the opening title.
DESKTOP
not 
LAPTOP
Laptops are a different breed from good to trash, and it is the latter that seems to have filled this listing, which makes it impossible for a DESKTOP user to find that list of incompatible hardware!

---

### Post by corrytonapple on 2010-07-26
> **oldsoundguy said:**
> To the moderators:
This thread has become increasingly long because some people can not read the opening title.
DESKTOP
not 
LAPTOP
Laptops are a different breed from good to trash, and it is the latter that seems to have filled this listing, which makes it impossible for a DESKTOP user to find that list of incompatible hardware!
Please, point me to a Laptop Hardware Incompatibility List so I can "show" future buyers that this computer won't work in certain ways.
Thanks:)

---

### Post by citizencj on 2010-08-04
[B]Toshiba
Satellite
Model 1135

Built in Mouse pad does not work. Plugging a mouse into the USB port works, but not the built in mousepad. 
[/B]

---

### Post by citizencj on 2010-08-04
Please point me to a laptop incompatibility list so I also can add this laptop issue to the list.

However the description at the top of the web page does say
**Hardware & Laptops** Problems with hardware & laptops not being detected or supported during or after install.he description

---

### Post by corrytonapple on 2010-08-04
> **citizencj said:**
> Please point me to a laptop incompatibility list so I also can add this laptop issue to the list.

However the description at the top of the web page does say
**Hardware & Laptops** Problems with hardware & laptops not being detected or supported during or after install.he description
I got a mod to make one. Its a sticky on the Hardware and Laptops page.

---

### Post by firefreak on 2010-08-25
Logitech Dinovo Edge Keyboard is not detected by the 10.04 Ubuntu or Kubuntu.

Sucks. Since it's the only one i've got.

Can't login to my existing updated installation or even reinstall it.

Epic fail since everyone seems to suggest I type something at root terminal but I cant get to it without a keyboard.

---

### Post by Zer0Nin3r on 2010-08-26
> **Zer0Nin3r said:**
> 1) Flatbed Scanner
2) Canon
3) Canoscan LiDE 90
4) Unsupported/Unrecognised
5) Ubuntu 8.04

This scanner is still unsupported.  Running 10.04.

---

### Post by oldsoundguy on 2010-08-26
> **firefreak said:**
> Logitech Dinovo Edge Keyboard is not detected by the 10.04 Ubuntu or Kubuntu.

Sucks. Since it's the only one i've got.

Can't login to my existing updated installation or even reinstall it.

Epic fail since everyone seems to suggest I type something at root terminal but I cant get to it without a keyboard.

suggest you go to a local thrift store with $5.00 US in hand and pick up a spare key board.. ps2 connector so you can hard wire in.  Might behoove you to get a ps2 mouse as well.  Handy things to keep in the drawer for just such instances .. and for the time you dump your Jolt into your keyboard.

---

### Post by hendraorhnd on 2010-08-28
UBUNTU 10.04 kernel 2.6.32-24-generic
Used on Mini HP 110-3014TU

Type of hardware:
USB Modem IVIO 2000u (CDMA)

Hardware:
QUALCOMM MSM6050

Issue:
--> Modem not responding.

```

~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 003 Device 004: ID 8300:0402**
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b1eb Chicony Electronics Co., Ltd
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

# modprobe usbserial vendor=0x8300 product=0x0402
~$ wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0 S1 S2 S3
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.

Sorry, no modem was detected! Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at http://open.nit.ca/wiki/?WvDial

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

~$ dmesg | grep tty
[ 0.000000] console [tty0] enabled
[ 4041.444806] usb 3-1: generic converter now attached to ttyUSB0

~$ sudo nano /etc/wvdial.conf
[Dialer Defaults]
Modem = /dev/ttyUSB0
Modem Type = USB Modem
...
...
..

~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: AT
--> Sending: ATQ0
--> Re-Sending: AT
--> Modem not responding.

```

here's dmesg output:
```

**[  173.488174] usb 3-1: new full speed USB device using uhci_hcd and address 2**
[  173.706500] usb 3-1: configuration #1 chosen from 1 choice
[  219.162757] usbcore: registered new interface driver usbserial
[  219.165616] USB Serial support registered for generic
**[  219.166808] usbserial_generic 3-1:1.0: generic converter detected**
[  219.170261] usb 3-1: generic converter now attached to ttyUSB0
[  219.170376] usbcore: registered new interface driver usbserial_generic
[  219.170389] usbserial: USB Serial Driver core

```

**Question?**
refer to link: 
[http://www.qbik.ch/usb/devices/showdr.php?id=253](http://www.qbik.ch/usb/devices/showdr.php?id=253), this device doesn't registered.:(

as we can see from dmesg output above, its also read as uhci_hcd, but this USB modem doesn't have storage.:confused:

hope for suggest or guideline for solution...
thx:)

---

### Post by SOME1 on 2010-09-01
brother's printers - I am installing Ubuntu for many people in Israel (9.04, 9.10, 10.04), many of them have Brothers printers with scanners and usually none of them work out of the box. the installation from brother's website is not easy as install deb package and in some cases do not work on ubuntu 10.04.

---

### Post by ub-pir on 2010-09-01
Asus P4/PE HDD runs the Live CD of Lucid fine but full install fails as the HDD are not recognized and therefore no partition can be created. (SATA disk). The very same h/w runs Karmic with no problems.

BTW: It would be nice if these community reports could be compiled into a database that would allow users to know in advance if an install or upgrade is likely to fail.

---

### Post by PGHammer on 2010-09-09
> **oldsoundguy said:**
> suggest you go to a local thrift store with $5.00 US in hand and pick up a spare key board.. ps2 connector so you can hard wire in.  Might behoove you to get a ps2 mouse as well.  Handy things to keep in the drawer for just such instances .. and for the time you dump your Jolt into your keyboard.

Microsoft USB keyboards (wired and wireless) *are* still supported in 'buntu (all versions, up to and including Maverick Meerkat) - I mention this as the older Wireless Keyboards can be picked up at bargain prices (I have the Wireless Keyboard 6000 V.3) and use it with my multiboot setup (7 Ultimate x64/Maverick x64 20100908 daily).  Same applies to Microsoft (and Logitech) USB wireless mice (I have the V220 Cordless; despite the *Notebook* moniker, it works a treat for desktop duty).

---

### Post by PGHammer on 2010-09-09
> **ub-pir said:**
> Asus P4/PE HDD runs the Live CD of Lucid fine but full install fails as the HDD are not recognized and therefore no partition can be created. (SATA disk). The very same h/w runs Karmic with no problems.

BTW: It would be nice if these community reports could be compiled into a database that would allow users to know in advance if an install or upgrade is likely to fail.

The P4C800E Deluxe runs Lucid (and even Maverick) just fine; what chipset does that motherboard use?  It may well use a third-party SATA chipset.

---

### Post by oldsoundguy on 2010-09-09
> **PGHammer said:**
> Microsoft USB keyboards (wired and wireless) *are* still supported in 'buntu (all versions, up to and including Maverick Meerkat) - I mention this as the older Wireless Keyboards can be picked up at bargain prices (I have the Wireless Keyboard 6000 V.3) and use it with my multiboot setup (7 Ultimate x64/Maverick x64 20100908 daily).  Same applies to Microsoft (and Logitech) USB wireless mice (I have the V220 Cordless; despite the *Notebook* moniker, it works a treat for desktop duty).

You missed the point
I suggested getting a wired keyboard and mouse for EMERGENCIES.  Such as the poster mentioned .. keyboard no longer working .. It could be many issues including batteries, USB, whatever.  A hard wired keyboard/mouse bypasses those issues and allows for investigative testing.

---

### Post by vayira on 2010-09-09
Epson AcuLaser M1200

Can't find drivers for this model.

---

### Post by dawiese on 2010-09-16
1)Integrated Graphics Controller
2)Intel
3)852GME 
4)Video card crashes when starting most types of videos in either Totem or VLC.  Using i915modset=1 to boot clean. 

Toshiba Satellite A45-S120
Lucid

---

### Post by dawiese on 2010-09-20
> **dawiese said:**
> 1)Integrated Graphics Controller
2)Intel
3)852GME 
4)Video card crashes when starting most types of videos in either Totem or VLC.  Using i915modset=1 to boot clean. 

Toshiba Satellite A45-S120
Lucid

Update:
Installed "...restricted_codecs" from OMGUbuntu.  Installed Ubuntu Tweak.  Messed around with some Compriz settings (cool stuff btw).  And all of a sudden I had video! :P  Messed around with more Compriz stuff, then *POOF* gone.  BSOD!  Like taking candy from a baby. :cry:  And for the life of me, I can't remember what I did to gain it or lose it.

---

### Post by dawiese on 2010-09-22
> **dawiese said:**
> Update:
Installed "...restricted_codecs" from OMGUbuntu.  Installed Ubuntu Tweak.  Messed around with some Compriz settings (cool stuff btw).  And all of a sudden I had video!  Messed around with more Compriz stuff, then *POOF* gone.  BSOD!  Like taking candy from a baby.  And for the life of me, I can't remember what I did to gain it or lose it.

Update 2:
VESA is the only setting that allows Lucid to boot clean and play video (s---l---o---w---l---y), but now the laptop refuses to wake from suspend.  It will be interesting if Canonical claims a perfect 10 in October.

---

### Post by waperboy on 2010-09-29
1) Motherboard
2) Asus
3) P6T SE
4) With Asus EN8800GT card, any nVidia driver causes lockups in X. Replacing video card with nVidia GTX 460 (same driver) removes problem.
(Asus EN8800GT card worked flawlessly on motherboard Asus P5W DH Deluxe with Intel C2D E6600)

---

### Post by LiquidZero on 2010-09-30
[B]1)RangeBooster G USB 2.0 WiFi Adapter
2)D-Link
3)WUA-2340
4)Compatiblity issue -- not detected, no associated driver[/B]

I've been having trouble with this device in Windows, also.. But at least windows will detect this piece of hardware.  Ubuntu ignores it and will only allow a LAN connection, no wifi---this is only a matter on my desktop, not my notebook using THIS device only.

---

### Post by catlover2 on 2010-09-30
printer canon pixima pro 9000 mark ii.

detected but cant find drivers.

---

### Post by Tee.Gee on 2010-10-19
Correction
I have the same card. It comes with 1 PATA and 3 SATA ports. None of the SATA ports work (with 10.10) but the PATA port works just fine.

00:08.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
Subsystem: VIA Technologies, Inc. VT6421 IDE RAID Controller
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 32
Interrupt: pin A routed to IRQ 11
Region 0: I/O ports at b800 [size=16]
Region 1: I/O ports at b400 [size=16]
Region 2: I/O ports at b000 [size=16]
Region 3: I/O ports at a800 [size=16]
Region 4: I/O ports at a400 [size=32]
Region 5: I/O ports at a000 [size=256]
[virtual] Expansion ROM at 40020000 [disabled] [size=64K]
Capabilities: [e0] Power Management version 2
Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
Kernel driver in use: sata_via
Kernel modules: sata_via

> **conradin said:**
> via VT6421 PCI SATA Card
01:01.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
Subsystem: VIA Technologies, Inc. VT6421 IDE RAID Controller
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 32
Interrupt: pin A routed to IRQ 22
Region 0: I/O ports at d080 [size=16]
Region 1: I/O ports at d000 [size=16]
Region 2: I/O ports at df00 [size=16]
Region 3: I/O ports at de80 [size=16]
Region 4: I/O ports at de00 [size=32]
Region 5: I/O ports at dd00 [size=256]
Expansion ROM at ee200000 [disabled] [size=64K]
Capabilities: <access denied>
Kernel driver in use: sata_via
Kernel modules: sata_via

---

### Post by Jacko1 on 2010-11-24
1) Multifunction Printer (scanner + printer) 
2) Canon
3) MG5150
4) the device is detected but Ubuntu 10.10 cannot find drivers. The Ubuntu generic printer driver does not allow even simple text printing.

Unfortunately at the present date there are no linux drivers available from Canon.

Help is welcome!

Jacko1

---

### Post by Jazzmaster94 on 2010-11-26
1) Graphics Card
2) ATI (Specific to my exact card: Asus)
3) Radeon X1350Pro

This card will freeze the boot process, and display a blank white screen.  KMS has been identified as the root cause.
This issue was resolved under OpenSUSE 11.3 by changing the boot parameters to be permanently set to "nomodeset".  This can be resolved under Ubuntu, by booting with KMS disabled and permanently setting it using a command-line tool.

---

### Post by philosophers-stone on 2010-11-27
G41 express chipset
Intel corporation
kde application freezes in ubuntu
Kwin freezez the desktop when trying to launch
No game requiring pixel shadder runs under wine

---

### Post by kgarbutt on 2010-11-28
Please Only List
1)Laptop
2)ibuypower
3)Uniwell 257SA1
4)Keyboard doesn't work in 10.10 -- Maverick Meerkat
(keyboard = AT Translated Set 2 keyboard)


Thank you.

---

### Post by asifnaz on 2010-12-13
Sound card : CMI8738 (C-Media) does not work even it has driver in kernel

---

### Post by bilallucky on 2011-01-11
a lot of hardware is windows only and will not work with linux 
its better to check out the compatability list for the distro you plan  to use and then change the hardware or search and locate drivers. 
submitting info such as manufacturer, chipset, ect can help developers write driver files.

---

### Post by corrytonapple on 2011-01-11
> **bilallucky said:**
> a lot of hardware is windows only and will not work with linux 
its better to check out the compatibility list for the distro you plan  to use and then change the hardware or search and locate drivers. 
submitting info such as manufacturer, chipset, ect can help developers write driver files.
That is true, but *a lot* of hardware **is** supported by Linux and Ubuntu specifically.  What you point out in this thread is true, and we hope that the developers will be looking here.  Normally, it is best to report hardware bugs or whatever you hardware/Ubuntu working together issue is on Launchpad.
Just what I know....

---

### Post by QsoftStudios on 2011-01-11
Linksys AE1000 USB Wireless adapter no drivers for Linux, not detected it network manager. To fix use version 10.10 or 10.04 and follow these instructions.

[http://forums.fedoraforum.org/showthread.php?p=1353558](http://forums.fedoraforum.org/showthread.php?p=1353558)

---

### Post by ewr2san on 2011-01-11
> **BrunoSilva said:**
> LG GP08NU6B External Optical Drive
It's not recognized.
Doesn't mount CDs or DVDs.

$ lsusb
Bus 008 Device 009: ID 152e:2571 LG (HLDS)

Works in Ubuntu 10.10 2.6.35-23-generic

---

### Post by trolleybus on 2011-01-24
Dell Latitude E5410. Partial incompatibility.
Ubuntu 10.04. Cannot boot from live CD as screen goes blank with blinking cursor. Graphics is Intel GMA 5700 MHD. Tried to boot with nomodeset (or whatever the instructions said i googled for). After that i could hear the login sound but screen was still blank.

Ubuntu 10.10. Ricoh SD card reader didn't work. I had to modify /etc/modprobe.d/latitude-e5410-cardreader.conf file and add the 'options sdhci debug_quirks=0x40' at the end of the file. Even then I have to unload and load the sdhci_pci module manually after every computer restart to get SD card read.
Synaptics touchpad. Vertical and horizontal scrolling don't work, touchpad is recognized as PS/2 mouse.

---

### Post by superduperlinuxperson on 2011-01-24
The ethernet controller on vostro 1500 (10/100 Gigabit wireless controller) freezes your computer once plugged in :mad:

---

### Post by Rouward on 2011-01-24
Printer: Canon Pixma iP1300
Scanner: Canon LIDE 100

---

### Post by LynxUser on 2011-02-28
Scanner HP Scanjet G4010 under Ubuntu 10.04 (connected through the USB)!

---

### Post by oldsoundguy on 2011-02-28
> **LynxUser said:**
> Scanner HP Scanjet G4010 under Ubuntu 10.04 (connected through the USB)!

have you installed sane?
[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

Many scanners will not work out of the box without the above.  The scan portion of my multi units work great once those directions were followed.

---

### Post by KG4UJD on 2011-03-03
Toshiba A305-S6905 issues with fan laptop overheats... That is the only problem I have had..... Great o.s. though!!!

---

### Post by ceminino on 2011-03-24
Printer
Color laser printer
Epson Aculaser C1600
no linux drivers available.

---

### Post by kent021410 on 2011-03-24
hi im new in ubuntu and i install it in my laptop and  i have problem in my screen resolution im stack in 800x600 can i bgger my screen resolution please help .

kent@kent-laptop:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0 

this is the output when i type xrandr

tnx in advance

---

### Post by tomibraniste on 2011-03-27
1) Motherboard
2) Asus
3) P6T SE
4) With Asus EN8800GT card, any nVidia driver causes lockups in X. Replacing video card with nVidia GTX 460 (same driver) removes problem.
(Asus EN8800GT card worked flawlessly on motherboard Asus P5W DH Deluxe with Intel C2D E6600)

---

### Post by cookiefac3 on 2011-04-01
Today I reconsidered installing the new beta release (11.04-b1) after reading the major video card fixes on this distro.
Got the same results as i had with the previsious distributions science the 9.10 release, beeing unable to load the desktop environment and getting choppy graphics on boot time.
Using the integrated graphics i can access the gnome environment, and everything else works just fine. 

My configuration:

1)Palit Daytona - 8800GS (384mb/192bits)
2)Asrock Alivenf7g
3)Chipset - nvidia MCP67

---

### Post by Gaming4JC on 2011-04-20
Webcam: Black 5.0 MegaPixel USB 2.0 Digital Webcam with Mic
Website: [http://www.amazon.com/gp/product/B004HKAICY](http://www.amazon.com/gp/product/B004HKAICY)
```
Bus 001 Device 010: ID 090c:71b3 Feiya Technology Corp. 

```
Displays as black screen in Cheese, and Not working.
Tested fine in VirtualBox WinXP.

---

### Post by Habeouscorpus on 2011-04-23
Phone
Samsung
Samsung Gravity Model SGH-T469
The phone will not connect through the USB Cable. I have no idea about Bluetooth. The Phone says its connected, and charges, but you cannot access the memory card inside. Very inconvenient.

---

### Post by lewislytal on 2011-04-23
> **frodon said:**
> [B]Welcome To The Desktop Hardware Incompatibility List.
[/B]
The purpose of this thread is for you, the user, to post what hardware/hardware combination don't work with your desktop Ubuntu install. 

Everyone is welcome to post here, as long as it is hardware related data. For help with hardware problems, please use the standard procedure of searching the forums, and starting your own thread for assistance if no answer is found.

**_Give detailed explanations when reporting incompatible hardware including the version of ubuntu you use._**

**Also Do not post any lspci outputs in this thread as they will be removed with out question.**

[B]Please Only List
1)Type Of Hardware
2)Hardware Maker
3)Hardware Model
4)Known Issue[/B]

[COLOR=Red]***NOTE* This thread is exclusively for the listing of incompatible hardware. Any idle chatter or unrelated posts will be moved/removed accordingly. *NOTE***[/COLOR]

Thank you.

**PS: the old incompatibilty list thread can be found here and will remain closed** :
[http://ubuntuforums.org/showthread.php?t=207916](http://ubuntuforums.org/showthread.php?t=207916)
trident microsystems cyberblade graphics card. on ubuntu 10.10 I can only get 800x600 screen resulation.

---

### Post by MountainX on 2011-04-24
GA-P55-USB3 Locks up on inserting USB flash drive
-------------------------------------------------

If I insert then safely remove a USB flash memory drive, and repeat this a number of times in a row, my system will hard lock.

As far as I can tell it will happen with any USB flash drive. I have a total of 12 different ones I have tested with now. They are different brands, different sizes, different filesystems, etc.

I have replicated the problem with the following operating systems:
Ubuntu 10.10 64bit LiveCD
Linux Mint 10 LiveCD
OpenSuSE 11.3 KDE LiveDVD
Debian Edition Linux Mint (LMDE) LiveCD

It also happens on my installed system, Ubuntu 10.10.

All I have to do is repeatedly insert and remove a USB flash drive and sooner or later the system will hard lock.

When it locks, nothing is response. The mouse cursor freezes, CTRL-ALT-DEL doesn't do anything, no special keys have any effect, and nothing is written to the system log. In addition, there are no errors in the system log preceding the lock up.

No overclocking or any other special settings. The bios settings are all defaults.

Components:
Intel Core i5-750 Lynnfield 2.66GHz LGA 1156 95W Quad-Core Processor
GIGABYTE GA-P55-USB3 LGA 1156 Intel P55 USB 3.0 ATX Intel Motherboard
G.SKILL Ripjaws Series 4GB 240-Pin DDR3 SDRAM DDR3 1333 (PC3 10666) Desktop Memory  - 16 GB total
SeaSonic 650W Power Supply X650 Gold


My guess is that the Linux kernel doesn't get along with the USB on the Gigabyte motherboard... but the problem isn't resolved, so I really can't say.

---

### Post by BELLION on 2011-04-24
I have Samsung RV510 laptop with intel gma x4500 hd graphic chipset which is not working properly under the Ubuntu 10.10 latest version and 32 bit operating system I can not change the screen brightness...
Any help ?

---

### Post by Richardcavell on 2011-04-29
Hewlett-Packard Deskjet 2000 printer, brand new.  

I have a desktop PC that dualboots Ubuntu 10.04 and Windows 7.  When it is running Ubuntu on the metal, the printer will not print.  (Ubuntu thinks that it is printing but it doesn't actually print).  The printer works flawlessly when the PC boots into Windows 7.  The printer also works flawlessly from my Mac laptop running OS X. 

When running on Ubuntu 10.10 that is virtualized within Windows 7 using VirtualBox, I cannot get the printer to work whether I attempt to use it via USB filter or via virtualized network connection.

I have tried using different drivers with no success.  Bottom line is, it works out of the box with Windows and OS X, and doesn't work at all with Ubuntu.

Richard

---

### Post by enimga.linda on 2011-04-29
mouse touch pad
my laptop is Snoy EA35FG
the touchpad is Synaptics PS/2 Port Touch Pad
after installation, when I boot up ubuntu 10.10, the mouse does not move at all.
actually I have the same problem with backtrack as well...

---

### Post by japfin on 2011-04-30
[B]Please Only List
1)Type Of Hardware
2)Hardware Maker
3)Hardware Model
4)Known Issue[/B]
[COLOR=Red][/COLOR]
Graphics card
NVidia
GeForce FX 5200

11.04, default mode. Do not show top menu bar. Right mouse button shows option box for nanosecond, then disappear. All other boxes are flashing ON/OFF constantly, for example network connection notice in start up. Mouse works, keyboard does not.

Works perfectly in Ubuntu Classic mode. Reinstallation of NVidia drivers does not help.

---

### Post by SevenSeas on 2011-05-01
Motherboard:  ASRock H67M + Intel i5
CD/DVD drive: ASUS DRW-24B3ST

The CD/DVD drive is not found in Ubuntu 10.10 or Ubuntu 11.04.
However, it is detected correctly in Ubuntu 10.04.1 LTS.

---

### Post by t-mark on 2011-05-01
No touchpad, laptop is Toshiba Satellite L670

---

### Post by alexander750 on 2011-05-03
DVD+/-RW Drive
Toshiba Samsung Storage Technologies
TSST TS-H522B, firmware rev. TS12
Ubuntu 10.10

**Drive recognized erratically or not at all.** Disk Utility sometimes lists this as a standard hard drive (/dev/sdb), sometimes as a CD-ROM, sometimes as something else altogether (e.g., a USB mouse). Occasionally, it will even appear as a DVD-RW drive.

When the drive is recognized correctly, it works with all the relevant applications (e.g., Brasero, VLC, etc.)

The drive does allow booting with the Ubuntu 10.10 Live CD, other Linux flavors (e.g., Damn Small Linux), and Windows 2000. It will not boot with Kubuntu 10.04 or Ubuntu 8.04.

---

### Post by Martin_sensei on 2011-05-04
1)Soundcard
2)Creative Labs
3)SoundBlaster Audigy2 ZS
4)Sound extremely distorted using Skype 2.2 on Ubuntu 11.04 (works on Ubuntu 10.10)

---

### Post by alexander750 on 2011-05-05
Motherboard
AsusTeK Technologies Ltd.
Asus A7A266, Socket A, ALi M1647 chipset, AGP Pro 4X (w/o onboard sound)
Ubuntu 10.10

**Hardware sensors** (fans, temps, voltages) **do not work in GNOME.** I have not verified whether they work at the console. This may have been caused by a recent update of the lmsensors package; the sensors were known to work in Ubuntu 10.04. IIRC, they worked earlier in 10.10.

---

### Post by EmmGeeImage on 2011-05-11
TYPE:  15.4" Monitor/HDTV
MANUFACTURER: Coby / Coby Electronics Co., Ltd (USA/Canada)
MODEL: TFT1524

In Ubuntu 11.04:  Mis-reports the 15.4 inch screen size as 26", which does not give a proper resolution and aspect ratio, when on Ubuntu 11.04. Things look too skinny, or too wide... No middle ground.

In Ubuntu10.04 and below: Simply does not display Ubuntu after the splash screen. Therefore, you will not be able to log onto the Computer to use Ubuntu 10.04 and under.

---

### Post by mgurgelmga on 2011-05-24
External USB HDD Samsung S2 Portable 320Gb
Mount Manager identify that is something, but does not mount, even, dinamically.

Runing Ubuntu 11.04 on a VMware Fusion Machine, under MAC OS X 10.6.7

On Pure windows machine the driver is ok, and on a Windows XP Virtual machine is ok also.

---

### Post by red03golf on 2011-06-03
1)Type Of Hardware - Hard Drive,
2)Hardware Maker - Seagate
3)Hardware Model - Barracuda 7200.12 (500GB)
4)Known Issue - SATA II 3GB / Sec setting of hard drive leads to hard drive not being recognized in the BIOS of slightly older motherboards that were produced before support for SATA II was included.

My specific cases - Abit motherboards KV8-Pro & KV-85.

For these Seagate drives installing a jumper on the two pins furthest away from the SATA data connector reduces drive to 1.5GB / Sec and permits the hard drive to be seen in the BIOS and thus the operating system.

Check with the manufacturer of your hard drive and properly determine the correct jumper setting for your specific hard drive to reduce it to 1.5GB / Sec..

Not specific to Ubuntu but may still be helpful to many Ubuntu users that find that their hard drive is not recognized in the BIOS or operating system - either connected via SATA directly to the motherboard or via USB as an external - as it 'may' be the cause.

This issue may also be present on other hard drives from the same manufacturer, as well as other manufacturers, as it results from using hard drives that have a default data transfer setting of 3GB / Sec. which exceeds what is supported on specific older motherboards - yet has a jumper setting that permits hardware recognition through the addition of a jumper thus providing backward-compatibility to the older motherboards that only recognize the original SATA specification of 1.5GB / Sec.

---

### Post by red03golf on 2011-06-03
> **t-mark said:**
> No touchpad, laptop is Toshiba Satellite L670

I looked on the synaptics site and found this page:

[http://www.synaptics.com/support/consumer-tips](http://www.synaptics.com/support/consumer-tips)

at the bottom of the page it mentions that linux drivers are available at the two following sites:

[http://compass.com/synaptics/](http://compass.com/synaptics/)
or
[http://www.pdos.lcs.mit.edu/~cananian/Synaptics/](http://www.pdos.lcs.mit.edu/~cananian/Synaptics/)

Hopefully that will provide assistance to some.

[B]EDIT:
These links appear to be dead and useless now.
I'll try to find useful links to drivers and post them.[/B]

---

### Post by Tootler on 2011-06-07
Kodak ESP C310 AiO Printer.

It appears to set up but nothing goes to the printer. There is no driver support from Kodak. There are third party drivers on sourceforge but these are only partially functional - print only and this specific model is not supported.

---

### Post by Anwarshah on 2011-06-29
_ZTE AX226 Wimax Modem_

ZTE AX226 WiMAX Modem not working in ubuntu. Successfully ModeSwitched from device 19d2:bccd to 19d2:0172 Which is a modem.
But the modem isn't working in ubuntu.:(


________________________________________
Ubuntu 11.04,( dual booting Windows 7),
Lenovo 3000 Y410, 160GB Harddisk,
1 GB RAM, 2GHz Core2Duo

---

### Post by PeterBrun on 2011-06-29
Hi.... I am a new returner to Ubuntu, but I can't get my wireless running. It has been on a coupple of times but only for a short time. Then it gets off again.

In Linux the hardware is described as this: >>Bus 002 Device 004: ID 13d3:3247 IMC Networks 802.11 n/g/b Wireless LAN Adapter<<

In Windows it is called: >>AzureWave usb\vid_13d3&pid_3247<<

The driver used is rt2800usb

Is there anyone that have found a driver that works for this?

Peter Brun

---

### Post by kamakazi20012 on 2011-07-04
Hi,

First, I'm new to Ubuntu, but I have tried to learn Linux with past versions with no luck.  So far, I like Ubuntu on my laptop but want to make it mandatory on my old desktop.

Trying to install Ubuntu on it works fine and I can read everything it is doing.  Rebooting after an install, however, gives an "outdated hardware" message and then the video gets all messed up.  I would like to try and fix it, but I can't read anything on it to do anything.  

Hardware:
eMachine w3052
512 DDR RAM
GeForce 4
nForce 2 motherboard architecture

---

### Post by trungvkvk on 2011-07-18
Dell Inspiron 6400
Wireless card not recognized

---

### Post by crshbndct on 2011-08-09
AMD Athlon II x2 260
4 GB DDR3 1333mhz
Gigabyte GA-78LMT-S2P 
radeonhd 4350

when using open source or driver provided by "hardware drivers", video performance is terrible. i cannot watch movies, youtube, enable desktop effects, its just slow and choppy

glx gears freezes, and when it doesnt, it reports 800fps.

this problem exists with all radeon hd cards.
i tried a $1000 radeon 6990 in this system and it was only marginally better, but i still am using windows as i cant get it to scroll simple text only webpages without being choppy

---

### Post by wfbowen on 2011-08-11
Toshiba L775 laptop; AMD 64bit; 
[COLOR=#000000][FONT=Ubuntu][COLOR=#3c3c3c]Ubuntu 11.04 in classic mode[/COLOR][/FONT]
[FONT=Ubuntu][COLOR=#000000]Keyboard/internal mousepad don't boot about half time. Shutdown and/or suspend also problematic.[/COLOR][/FONT]
 
Edit:
I've moved this to the laptop thread.
 
[/COLOR]

---

### Post by Ollie13 on 2011-08-15
SiSM661MX **- **No backlight

---

### Post by bebopberg on 2011-08-17
Dell Dimension 9200
Asus Xonar Essence STX
Intel HD Audio
Natty 11.04

Intel HD Audio card doesn't work.  Various pertinent solutions tried to no avail.
Sound is intermittent at boot time w/ Asus Xonar. Not sure if this is MPD or hardware/driver issue.

---

### Post by Diachi on 2011-08-31
1) Onboard Graphics
2) Intel Corporation
3) Sysinfo says that i am using a "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev01)(prog-if 00[VGA controller]) 
4) What if the graphics driver ubuntu installed is not the right one like say for a Compaq Evo D510 SFF and it doesnt show a proprietary driver? Its an onboard not a graphics card but the "3d effects" are not working properly. I am having to run it in fallback mode, How do i get the "right driver for ubuntu?" i guess is my question. :D Please help.

---

### Post by bijur on 2011-10-20
Hi,

I guess my problem is a little trickier than usual.

I just can't use 3D Acceleration on my brand new PC.

My machine is an HP Omni 200 PC (model 5320br). (Core i3, Intel HD Graphics onboard Clarkdale chipset, with 2Gigs RAM, and 500Gb HardDisk)

Facts:
- If I boot (LiveCD or after installing) without the "nomodeset" kernel switch activated, the system goes black screen. I hear the sound, but nothing on video, not even the Ubuntu logo on startup.
- I've already tried all the possible configurations with a customized xorg.conf. Nothing works.
- after A LOT of debugging, I've ended up in the dmesg log, that says to me (just a snip of the relevant part):

[   10.140701] [drm] Initialized drm 1.1.0 20060810
[   10.166857] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   10.166858] [drm] Driver supports precise vblank timestamp query.
**[   10.199873] [drm] Cannot find any crtc or sizes - going 1024x768.**
[   10.630795] fbcon: inteldrmfb (fb0) is primary device
[   10.630878] fb0: inteldrmfb frame buffer device
[   10.630879] drm: registered panic notifier
[   10.633540] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
 
So, I've discovered that Ubuntu is not recognizing my video output. I've also tried forcing the detection (via the video=VGA-1:e switch in kernel), and that also didn't worked out.

At last, I've found this thread on another forum:
[http://forums.opensuse.org/english/get-technical-help-here/hardware/452160-intel-hd-graphics-intel-core-i3-suse-11-3-a-4.html](http://forums.opensuse.org/english/get-technical-help-here/hardware/452160-intel-hd-graphics-intel-core-i3-suse-11-3-a-4.html)

The guy has the same hardware as mine, mostly, so is not a specific Ubuntu problem.

I have no more hope :(
If anybody can help me please...

Att,
Daniel

---

### Post by paulnewall on 2011-10-21
Kodak esp C310 should now be able to print with c2esp21~rc1 at
[http://sourceforge.net/projects/cupsdriverkodak/files/](http://sourceforge.net/projects/cupsdriverkodak/files/)

---

### Post by azzid on 2011-10-25
Motherboard
Gigabyte
A75M-S2V

Shuts of monitor when switching to higher resolution, happens during installation.

I also tried installing ubuntu server (non-gui installer), installer works fine, but resolution change after grub showing (before even showing the login prompt) shuts of monitor aswell.

**EDIT:** boot option 'nomodeset' seems to sidestep the issue
**EDIT2:** no network during installation
**EDIT3:** really buggy networking and no x after install, unable too boot unless 'nomodeset'
**EDIT4:** the network issue: [http://ubuntuforums.org/showthread.php?t=1865436&highlight=8168B+realtek](http://ubuntuforums.org/showthread.php?t=1865436&highlight=8168B+realtek)

---

### Post by techlogik on 2011-11-16
HP Compaq 6000 Pro All In One Desktop
 
 
Specs:
 
Graphics Card Intel GMA X4500Intel(R) Q45/Q43 Express Chipset
 
 
Used Ubuntu 11.10 USB boot device, no video displayed, but sound was working.  After the initial kernel text screen on boot displayed, it appears to hit the graphics card detection, and it goes black.  Then shortly you will have sound like it is on the desktop working.

---

### Post by PayPaul on 2011-11-16
The Microsoft Comfort Mouse 3000 does not have any drivers for Ubuntu or Linux. The mouse works sometimes but often the cursor will drift down to the bottom of the screen and I have a tug of war with it to get it back in my control. The only reason I can possibly think is there is no real driver for it. Could this be the case and can I get one that matches it closely for Ubuntu 11.04?

---

### Post by joreg on 2011-12-02
> **Amedee said:**
> Logitech Bluetooth Desktop MX5000 (combination keyboard&mouse) is partially incompatible.
It will work in legacy HID mode, but then all other bluetooth functionality (pairing with bluetooth phone) is disabled.
You can get the dongle in HCI mode, but then the keyboard and mouse stop working.
It is impossible to use keyboard&mouse and at the same time use any other bluetooth devices.

More info in [https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/32415](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/32415)



Thank you

---

### Post by IMvVIP on 2011-12-08
Gigabyte UD5 AM3
AMD Ph II x6 1050T
8GB DDR3 
500GB
ATI 5770 (2 DVI port)
24" LED

Video problems.
load on Virtual install ok
After click install and reboot screen goes black.
Only Fedora have success install.
But Ubuntu, Linux Mint, Opensuse, Ubuntu.
all linux are not support DVI port i guess.
my max screen resolution go up to 1600x1200
my LED max is 1920x1200

even upgrade ATI driver for linux... nothing is changed...

---

### Post by harrystrent on 2011-12-31
Toshiba Satellite L775 with AMD 3400M APU. Under Ubuntu 11.04 the keyboard is not operative about 50% of the time. Sometimes it helped to turn laptop completely off and do a cold reboot. After upgrading to 11.10 the keyboard does not work at all.

---

### Post by Kadai on 2012-01-06
The video card on the HP TouchSmart 320-1022 is detected, but can't be used by any current Kubuntu LiveCD/USB, therefore needing you to set the "nomodeset" option in order to be able to see the screen during boot, but then X did not started properly when tried to use the live desktop.

Also, I was not able to install Kubuntu 11.10 either using Wubi or Classic install, on both cases the bootloader was not able to be installed (Maybe this is a Win7 faulty thing).

Before to be able to see the Live options, the next message is shown:
```

Error: "Prefix" is not set.

```After what I'm only shown 2 options: Start Kubuntu or Check the CD for deffects, despite the fact that on VirtualBox they show correctly, also on other computers.

And, when I try to start X (with startx on terminal) I got this output:
```

(EE) Failed to load module "fglrx" (Module does not exist, 0)
(II) [KMS] drm report modesetting isn't supported
(EE) RADEON(0): Chipset: "SUMO" (ChipID = 0x964a) requires KMS
(EE) Screen(s) found, but none have a usable configuration

```So far, those are all the problems I have.
The computer specs (brief):
AMD Radeon HD 6530D
USB, RJ45, PCIe, Card Reader
6gb ram
AMD Quad-Core A6-3600
 10/100/1000BASE-T / WiFi 802.11B/G/N

---

### Post by anushcbe on 2012-01-07
Dell WMI interface like cap touch switch that are available in DELL XPS L401X  is not functioning at all, or am not knowing how to enable the same to my desktop of UBUNTU 11.10 (AMD64 version) with unity theme.

Any suggestion how i can enable it?

---

### Post by cove19 on 2012-01-07
This thread is old but I'll give my monies worth.

Please Only List
1)Type Of Hardware
2)Hardware Maker
3)Hardware Model
4)Known Issue

1)Laptop 2ghz Intel 4, 1230mb RAM
2)Acer
3)Travelmate 530

4)LinuxMint LXDE 11 unstable after install. Couldn't, wouldn't put me on the environment/flavour I wanted. Couldn't get to terminal with alt+f2. Had to logout by pressing DEL + BREAK + CTRL + ALT and managing to get a dialogue to logout. I then managed to run Gnome classic and installed XFCE and this was ok but I don't prefer it.

Ubuntu 11.11 unity will not work, puts me on Gnome and I don't even think it was 11.10 in the end, I think it was 11.04.

Tried various other Distro's, Slax 6.1.2 runs as a live cd. LUbuntu 11.10 works fine fully installed.

I tried GeexBox (similar to XBMC) and it struggled to do that.

LUbuntu for me with Slax 6.1.2 as a backup. I may try Ubuntu 10.04 again.

---

### Post by cdoebbler on 2012-01-13
Desktop Hardware Incompatibility List.

1) Multifunction Printer (scanner + printer)
2) Canon
3) MG5150
4) The device is detected but Ubuntu 11.10 cannot find drivers. Both printer and scanner do not work.

---

### Post by anushcbe on 2012-01-13
> **cdoebbler said:**
> Desktop Hardware Incompatibility List.

1) Multifunction Printer (scanner + printer)
2) Canon
3) MG5150
4) The device is detected but Ubuntu 11.10 cannot find drivers. Both printer and scanner do not work.
I have an Imageclass MF4350d, which is an multi function printer this is working with UBUNTU 11.10 only if u install two supporting package from the cannon.

---

### Post by cmp1988 on 2012-02-03
1) Mouse
2) Razer
3) DeathAdder 3500 DPI (Model No. RZ01-0015, Infrared Gaming Mouse)
4) Sometimes this mouse is completely unresponsive, requiring a reboot or 2 to get it working again.   This is Ubuntu Oneric Ocelot (11.10), as well as any distro based on Ubuntu (Mint for example).

EDIT:  Forgot to mention that it's 64-bit Oneric Ocelot, and 64-bit Linux Mint.

---

### Post by anushcbe on 2012-02-04
> **cmp1988 said:**
> 1) Mouse
2) Razer
3) DeathAdder 3500 DPI (Model No. RZ01-0015, Infrared Gaming Mouse)
4) Sometimes this mouse is completely unresponsive, requiring a reboot or 2 to get it working again.   This is Ubuntu Oneric Ocelot (11.10), as well as any distro based on Ubuntu (Mint for example).

why this trouble kind of issues taking place is that kernel problem or something else am not able to understand it

---

### Post by anushcbe on 2012-02-27
Could Try Virtual BOX for it, which support different home OS. only you need the new Solaris OS to install in that, it will do.hope it helped you.

---

### Post by eiguike on 2012-02-29
1) USB Wireless Card
2) Kaiomy
3) Wa-150U
4) Ubuntu 11.10 can search wireless spot and find it, but can't connect. (with or without security like WPA/WPA2).

---

### Post by konradst on 2012-03-01
1)Printer
2)Canon
3)PIXMA MP250
4)not detecting (through official installer)/not installing/stops printing "unable to send data to printer" at 8-9% /flashing enabled/shared in printer monitor (through cups driver or cups installed official driver) - the behavior depends on solution attempt - it doesn't work in any way

---

### Post by konradst on 2012-03-01
1)USB device (pendrive)
2)VIA KT333 motherboard
3)USB 1.2 port, USB 1.2/2.0 devices
4)no sign of life

---

### Post by fjgaude on 2012-03-08
1)ASRock Z68 Motherboard
2)Intel i5-2405S CPU
3)Ubuntu 10.10 through 12.04
4)Suspends but will not Resume

Seems that many of the Sandy Bridge motherboards, not just ASRock, have issues with suspend/resume. The kernel's handling of ACPI needs updating.

UPDATE: Updated BIOS, 2.10, and now it resumes after suspend. The upgrade BIOS was really for Ivy Bridge CPUs, but something was done to work correctly with Sandy Bridge also. Hurray!

---

### Post by morismemo on 2012-03-14
1)Printer
2)Canon
3) Razer

---

### Post by asvestomix on 2012-03-24
Desktop Hardware Incompatibility List.

1) Printer
2) Canon
3) PIXMA (ip4700)
4) The device is detected but Ubuntu 11.10 cannot find drivers.
Impossible to make it work on 64 bit version

---

### Post by Jezzze on 2012-04-05
I would not recommend the **XFX Radeon HD 4850** graphics card when using Linux Ubuntu and Gnome. After installing the drivers for the card, it seems not able to handle resolutions over 1024x768, although it did in the past, so you would say it would be a version problem, although I did not look into that.

---

### Post by yardbird2012 on 2012-04-05
1)ASRock Z68 extreme 3 gen 3 Motherboard
2)Intel i5 2500k
3)Ubuntu 10.04 64bit
4)USB 3.0 problem, plug in flash drive to usb 3.0 port, which cause the computer dead.

since i do not have windows system, i can not test it there. since it's a brand new motherboard, there might be some chance it is defective. however, the motherboard works very well other than the usb 3.0.

---

### Post by Axxon95 on 2012-04-06
Board: Asus P8H61-M LE/CSM

UPDATE: This board works with later versions of Ubuntu.

---

### Post by Elzenbr8 on 2012-04-29
Ubuntu 12.04
Mainboard: MA790GP-UD4H

1) Display[INDENT]    GPU: Radeon HD4670
   LCD: LG M227W
   *) Screen resolution detected correctly, but shown wider.
   **)Proprietary driver fix this issue, but quality is poor.
[/INDENT]2) Printer[INDENT]Epson L200
*) Detected, but won't print. Print job proceeded and report done, but nothing have done.
[/INDENT]3) Storage[INDENT]    WDC20EARX (2.0TB)
   *) Not sure for incompatibility issue related to 12.04, could be not supported by 
    mainboard. Ubuntu said "softreset" 6/3/1.5 couple o times.[/INDENT]

---

### Post by Chris80RN on 2012-05-07
Diamond AMD Radeon HD 6450

Won't work at all, with any Linux OS, 
works well with Windows 7.

Ubuntu runs smootly without the card.

Tried nomodeset, installed drivers. Still not working.

Motherboard: Gateway RS780 (AM2)
Processor  : AMD Phenom X3 8400
RAM        : 6,00*Go Dual-Channel DDR2 @ 400 MHz

---

### Post by monsag on 2012-05-15
Manufacturer: Acer            
	Product Name: Aspire 4736Z    
	Version: V2.06
	Serial Number: LXP530C0980100F8411601
	UUID: 02957C1D-3AF9-F122-632D-705AB6403AA9

Perfect and happy with 10.04 
Disaster and sad with 12.04

Clean install of 12.04 - blank screen, nothing else to do, no where else to go.

---

### Post by MarkM1 on 2012-05-15
Desktop: HP Pavilion a220N (Mtr Bd: ASUS A7N8X-LA)
 CPU: AMD Athlon XP
 AGP: Nvidia GeForce 4 MX
 

 Perfectly ran Ubuntu up to and including 10.04 LTS (Live CDs)
 
Crash installing Ubuntu 12.04 LTS (Live CD)
 (was a clean install, freshly **repartitioned **& formatted HDD)
   
 ->> Crash &#8230; /usr/share/ubiquity/plugininstall.py
Package: Ubiquity 2.10.16
Plugin Install.py crashed With IO error ... Errno 32 <<--
 

 

 See thread &#8220;**12.04 Installation Crashes&#8221;  started by  aykoola**

---

### Post by abstractAlchemist on 2012-05-16
Motherboard: Asus Rampage IV Formula
CPU: Intel i7 3930K
GPU: EVGA Classified Nvidia Geforce 580GTX 3072 GB
RAM: Corsair Dominator 4GB modules ( 4 of them )
HDD:  2x Ocz Agility 3 SSDs 128GB

Freezes when attempting to install 12.04 in UEFI mode;  seems fine in legacy BIOS, but I want to install in UEFI mode.  Gets as far as first screen after the initial boot menu.

For the record, 11.10 installs cleanly and works like a charm, what I have normally come to expect from Ubuntu releases.

---

### Post by Regrets1015 on 2012-05-21
[FONT=Arial]1) Graphics Card
2)Nvidia
3)GeForce 6150SE nForce 430

4) Been getting errors since the 11.04 update that "Input Not Supported" after selecting Ubuntu when it gives me the option to boot up Vista or Ubuntu. 

I have a 20' LCD Acer monitor running at 1600 x 900 resolution @ 60 Hertz. 

I have to wait for the Moving message to go away (About 30 seconds) before it takes me to the login screen.

When I put in my password and log in the entire screen goes black and all I can see is the cursor. There it stay like that. 

This happened after I installed the Nvidia graphics accelerator and restarted like it told me to.

The other Ubuntu versions before Ubuntu 11.04 ran much faster and had no problems with my graphics or really bad processor (AMD Athlon 64 @ 1.6 GHz) 
[/FONT]

---

### Post by Ubun2to on 2012-05-21
1. USB VGA External Video Card
2. IOGear
3. GUC2015V
4. Won't work with both screens-boot screen shows up on second monitor, but then shows a picture of the boot screen after the login screen shows up.

---

### Post by cdoebbler on 2012-05-22
Update: 

Cannon 5150 seems to work out of the box with 12.04...have not tested scanner.

---

### Post by Fraoch on 2012-05-22
[removed, hardware now works]

---

### Post by roelforg on 2012-05-22
Note:

The Hercules RMX is listed as "incompatible", this isn't true anymore.
```
[FONT=monospace]
[/FONT]sudo add-apt-repository ppa:rojtberg/hdjmod 
sudo apt-get update 
sudo apt-get install hdjmod-dkms
sudo modprobe hdj_mod
sudo bash -c 'echo hdj_mod >> /etc/modules'
[FONT=monospace]
```

Will install it just fine.
Reboot and it should be recorgnised by the normal sound config as a surround card and by mixxx as the console.
Tested (and working) on ubuntu 11.10 32bit

[/FONT]

---

### Post by Baulageng on 2012-06-21
share experiences hardware Posted June 9, 3:45am Alexander Keller, Fedora Core Linux, Other Linux, Ubuntu Linux
Home | Ubuntu

Desktop Fast, secure stylishly simple, Ubuntu operating Certified software; Certified hardware; Component catalog
Find Hardware Specs (Details) on your Computer « Ubuntu Blog

disk list hard disks. It create html page hardware Blog Archive » What kind hardware Ubuntu computer ? Firefox 2 compatibility
Hardware by Acer - Fedora Core Linux Hardware Compatibility List

[http://www.tcbiodiesel./desktop/desktop-hardware-compatibility-list-archive-page-2-ubuntu-.html](http://www.tcbiodiesel./desktop/desktop-hardware-compatibility-list-archive-page-2-ubuntu-.html) Hardware Acer - Fedora Core Linux Hardware Compatibility List.
Ubuntu for you | Ubuntu

Ubuntu . Super-fast, easy free, An operating system computer work, running programs managing hardware.
Acer Aspire 5315 Notebook Pcs - Ubuntu Linux Hardware

[http://www.top10haircuts./desktop/desktop-hardware-compatibility-list-archive-ubuntu-forums.html](http://www.top10haircuts./desktop/desktop-hardware-compatibility-list-archive-ubuntu-forums.html) Mar 28, 2012 – Acer Aspire 5315 Notebook Pcs - Ubuntu Linux Hardware.
Idea #3575: "Online Ubuntu compatible - PC Hardware Store

Archive Manager 3- A mindset Think Ubuntu compatibility Line: Give list compatable hardware fits desktop users ubuntu
Ubuntu on Pentium 3 ? - Laptop Forums and Notebook Computer Discussion

News Archives Hardware, Software Accessories > Linux Compatibility Software: Ubuntu Pentium 3 ? HP Desktop Pentium 3 processor. Will Ubuntu
LINUX ON DESKTOP: Making your Ubuntu 7.10 Desktop look like MAC OS

---

### Post by stevecook on 2012-07-01
Canon LPB2900i printer not picked up by Ubuntu 12.04 LTS. When the drivers are installed, it still does not work without a bash script workaround. 

  There is a tutorial on the workaround here:

[http://ubuntuforums.org/showthread.php?t=2013437](http://ubuntuforums.org/showthread.php?t=2013437)

---

### Post by palimmo on 2012-07-06
1)Ubuntu 12.04 64bit,Ubuntu 10.04 32 bit
2)USB Keyboard Mini 
3)Hama
4)SL 640

It works occasionally and you need to plug/unplug several times.... 
When it works it is perfect (media keys too).

More info here:
[http://ubuntuforums.org/showthread.php?t=2018203](http://ubuntuforums.org/showthread.php?t=2018203)

---

### Post by stefan231 on 2012-09-01
OS: Ubuntu 12.04 LTS 64bit

[http://h10025.www1.hp.com/ewfrf/wc/p...roduct=5109961]("http://h10025.www1.hp.com/ewfrf/wc/product?cc=us&lc=en&dlc=en&product=5109961")
[Compaq Presario CQ5814 Desktop PC ]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02859370&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=5109961")

AMD E-350 (Zacate core)  
3 GB  DDR3-1333
Integrated graphics using AMD Radeon HD 6310
Realtek ALC662 CODEC
500 GB 7200 rpm HDD

Ubuntu installs very slow, but it does install when you get to the   desktop anything you try to open takes a few seconds to respond, Compiz    is using constantly 45-50% cpu and the systems is basically unusable   this 1.6ghz processor and integrated GPU cant seem to handle the load   making Ubuntu unstable and eventually freezes up.

---

### Post by sergio-bobillier on 2012-09-03
This PC has really bad issues with Ubuntu and with Linux in general. The PC comes with an Intel HD Graphics 2000. (Sandy/Ivy bridge). When Ubuntu boots on this machine the screen flickers heavily, you can still manage to see a few things on screen but working on it wold be crazy.

Here is a video of the issue:

[https://plus.google.com/u/0/117342201953354940968/posts/JHVJec9HhUJ](https://plus.google.com/u/0/117342201953354940968/posts/JHVJec9HhUJ)

I tried everything, to try and fix the issue but to no avail: I tied 32 and 64 bits version of Ubuntu, tried various PPAs including **glasen/intel-driver**, **xorg-edgers/ppa** and the proposed repositories for Ubuntu 12.04 but nothing.

I tried with ubuntu 12.10 Alpha 3 and problem still persists.

The only way to get an stable image on the screen is to boot with **nomodeset** which only allows 1024x768 resolution and that is really low and also is not the correct aspect ratio for the monitor.

I tried with OpenSUSE 12.1 but with it all I get is a black screen (I tried with 1024x768 and VESA video modes). I'm pretty sure that this PC is just incompatible with Linux. Don't buy an HP All in One PC if you want to run Linux.

---

### Post by jynyl on 2012-10-16
1. mini-ITX motherboard, integrated CPU & graphics
2. Intel
3. DN2800MT, Cedarview / Cedar Trail
4. hardware graphics acceleration not available to Linux

Tried Ubuntu 12.04, and 12.10 beta 2; runs X but without graphics acceleration
The Intel website has Linux drivers to download and case study instructions, but these don't work on Ubuntu 12.
[http://download.intel.com/support/motherboards/desktop/sb/enabling_hardware_accelerated_playback_ubuntu_12.pdf]("http://download.intel.com/support/motherboards/desktop/sb/enabling_hardware_accelerated_playback_ubuntu_12.pdf")

---

### Post by cdoebbler on 2012-10-16
1)Type Of Hardware: USB Wireless stick
2)Hardware Maker: Netgear
3)Hardware Model: A6200 (b/g/n/ac modem)
4)Known Issue: Not recognized by Ubuntu 12.04 LTS

Provided some basic diagnostic information with call for help in forum. USB does not even seem to be recognized when plugged in.

---

### Post by crnipauk on 2012-10-21
1.MB Gigabyte H61M-S2PV
2.Ati Reaedon HD 6570 PCI-E
3.CPU Intel G630

Why not work Ubuntu 64 bit 12.04 or 12.10??


What hardware is compatible with Ubuntu 12.xx 64 bit?



Thanks!!

---

### Post by cdoebbler on 2012-10-24
1)Type Of Hardware: USB Wifi Modem/Adapater/Extender 
2)Hardware Maker: Netgear
3)Hardware Model: A6200
4)Known Issue: Not being recognized by system

---

### Post by AirmanByrd on 2012-12-01
USB Keyboard 
Sharkoon Skiller Gaming Keyboard
Ubuntu 12.04
Ubuntu 12.10
And many other flavors of Linux to include a Gentoo build.

Works in CMOS and GRUB but as soon as it boots to Linux it stops.

---

### Post by Lightning Dragon on 2013-01-24
**Distros tried: ** Ubuntu, Kubuntu, Edbuntu, Xubuntu, Linux Mint, and Manjaro. (Problem)
**Graphics:** GeForce Sparkle 6600 LE 256mb GPU *with current driver 304.64* (Problem) 

[SIZE=1]Problem, currently, is the GPU. All available drivers are *supposed* to support the GPU series (Geforce 6 Series), however no distro I tested above works with the above GPU and the drivers, or even without the drivers installed. The problem is that you get a black screen after the GRUB, and hideous static screens on boot up.[/SIZE]

---

### Post by willyeverlearn on 2013-02-27
Good Morning,
I have been searching around, however effectively{8^)
Is there any plans to support Ubuntu on the s390 platform?
That could roughly be translated to say IBM mainframe IFL....

Thank you very much
Willy

---

### Post by mash107 on 2013-02-27
Keyboard & mice
Logitech
MX5500
Ubuntu 12.10

Only workaround is to install kernel 3.7.0 or later.
Naturally, makes installation very painful.

---

### Post by InformateIt on 2013-03-23
I have promlems with LG BE14NU40 and USB 3,
it works but it looks like a USB 1.1 connection,
the trnsfer spped is limited to 1500KiB/sec,
**very very slow**!

---

### Post by waltercool on 2013-03-25
1) Laptop
2) Samsung
3) np355v4c-s02
4) 
- Fn-keys are working faulty, screen bright isn't working, but fn keys seems to respond (just visual change, not bright change)
- mute/volUp/volDown faulty, if I just press one, indicators becomes crazy, volUp makes volume up to max, volDown makes volume down to min (and gui becomes not responsive until I move it to terminal from ctrl+alt+Fx)
- Settings fn key doesn't do nothing.
- Monitor fn key keeps pressing p and super? (I can see numbers on unity bar)
- Fan fn key appears to not work
- Wifi fn key do nothing.

Another issue, this Laptop is using A10 APU, but seems like isn't using full processor OR videocard as Windows does. On the same game, Windows seems to make the laptop very hot, but Linux don't, keeps on a normal temperature. 

No another issue. Thanks

Using: Ubuntu 13.04b, with Ubuntu 12.10 same problems. Using xorg-edgers ppa, because my videocard doesn't works other way on Ubuntu 12.10 (black screen if I'm not using nomodeset) and an unsupported chipset  message from AMD with 13.04b without xorg-edgers (I can't remove unsupported chipset without touch the binary, but with xorg-edgers I have a experimental chipset and could be removed with a key on /etc/amd)

---

### Post by pnarciso on 2013-03-27
There's no sound support for Sound Blaster Z sound card in Ubuntu 12.10 and 13.04. The card is recognized as CA0132 but it doesn't output any sound.

---

### Post by davidbaumann on 2013-04-29
ALFA AWUS036NHR

Uses RTL8192CU Module, which seems broken.

---

### Post by Jhon smith on 2013-04-30
msi rs487 motherboard
512mb ram
data cable is not work,

---

### Post by kmurray42 on 2013-05-08
I built a computer using the 
[B][SIZE=2]
GIGABYTE GA-990FXA-UD3 AM3+ AMD 990FX SATA 6Gb/s USB 3.0 ATX AMD Motherboard [/SIZE][http://www.gigabyte.com/products/product-page.aspx?pid=3894#sp](http://www.gigabyte.com/products/product-page.aspx?pid=3894#sp)[/B]


only 2 usb 2.0 ports worked and the ps2 keyboard/mouse port. The front facing usb ports and usb all 3.0 did not work

on board network card was recognized but would not work

[FONT=Arial][COLOR=#3d3d3d]Realtek RTL8111E chip[/COLOR][/FONT]

[FONT=Arial][COLOR=#3d3d3d]fyi ultimate linux which is ubuntu based seemed to work [/COLOR][/FONT][http://ultimateedition.info/](http://ultimateedition.info/)

I did not test any other ports/connectors.

Thanks

---

### Post by cdoebbler on 2013-05-09
Netgear USB modem A6200 a/c quality 
still does not work with Ubuntu 13.04 (Raring Ringtail) on my i7 3.5 Mhz 8 GB desktop 2.0/3.0 USB.

---

### Post by mmstick on 2013-05-22
1) Sound Card
2) Creative
3) Recon3D + Sound Blaster Z
4) No sound; detected by alsa but no sound.

I've tried: Ubuntu 12.04, 12.10, 13.04, 13.10; no luck

---

### Post by sunnycreatives on 2013-05-22
Canon iP6210D

I have downloaded Wine to see if that helps...but no...I can't print anything :(

---

### Post by ubuntaix on 2014-04-19
I now tried (X)Ubuntu 14.04 LTS on an older Hardware. There were rather few problems, but one drove me crazy:

It is not possible to install an up-to-date flashplayer plugin on webbrowsers (see here: [http://ubuntuforums.org/showthread.php?t=2199635](http://ubuntuforums.org/showthread.php?t=2199635)) with Linux on a CPU without sse2 or higher (in my case an Athlon XP 3000+). It is possible to use older plugins, but due to severe security risks this isn't recommended. 

Therefore I would suggest to assume those CPUs as incompatible with Linux (please criticize Adobe for the issue since they stopped updates).

---

### Post by madbyte on 2014-04-21
After years using Ubuntu, I can say the rtl8187 driver is one of the  worst. The WiFi connection becomes unstable if the signal is less than  50% and totally lost at 20% or less. And now, after the last upgrade to  14.04, if the router changes the tx channel sometimes the connection is  lost with this:

```

wlan0: deauthenticating from (MAC) local choice (reason=3)
wlan0: deauthenticated from (MAC) (Reason: 7)

```

I need to restart to connect again.

---

### Post by Madman1978 on 2014-04-30
Flatbed Scanner 
Cannon
CanoScan LiDE 70
Unbubtu 14.04

---

### Post by imrazor on 2014-05-01
> **pnarciso said:**
> There's no sound support for Sound Blaster Z sound card in Ubuntu 12.10 and 13.04. The card is recognized as CA0132 but it doesn't output any sound.

> **mmstick said:**
> 1) Sound Card
2) Creative
3) Recon3D + Sound Blaster Z
4) No sound; detected by alsa but no sound.

I've tried: Ubuntu 12.04, 12.10, 13.04, 13.10; no luck

Wrong...sort of. 64-bit Ubuntu is a bust. 32-bit Ubuntu 14.04 works, with some tinkering. First, you'll have to run alsamixer, hit F6 to change sound cards if necessary, then unmute main, PCM and surround and set the two volume levels to something sane. For some reason the card kept muting itself, but eventually started behaving. I'm using Kubuntu 14.04 32-bit, so I had to go to Phonon to disable all my other audio devices. You then get front panel audio ONLY. The headphone and analog 5.1 ports on the back get no output. Supposedly digital out works, but I don't have a digital receiver to test it on.

The thing is...it sounds absolutely AMAZING. Much better than the same hardware under Windows (32-bit or 64-bit), and it sounds darned good under Windows. Makes it worth crawling along with 1990s 32-bit technology. Someone needs to kick the 64-bit driver into shape, pronto.

---

### Post by redrumrogue on 2014-08-05
1.  Sound Card
2.  Asus
3.  Xonar Essence STX II
4.  not detected - not selectable in alsamixer or in Ubuntu sound settings GUI.  Device does show up in lspci -v output.  Works fine under windows 8.1 on same hardware, using drivers downloaded from Asus.

OS:  Ubuntu 14.04.1 64bit
Motherboard: Asus Sabertooth 990fx R2.0

***I have just built kernel 3.16.2 (running ubuntu 14.04) and this card is now supported - 09 September 2014 ***

---

### Post by lile001 on 2015-01-30
Epson WF7520 printer - possibly WF 7540 and other printers by Epson that are capable of 11X17
ANY Linux version - this is a generic problem with Epson Linux printer drivers

Epson has written a printer driver for linux that has worked very well for me on Ubuntu 12.04 and 14.04, however it includes no support for printing US B 11X17 sheets.  Other common US sizes are supported. I believe this would affect any Linux distro.  Epson uses the same printer driver to interface many (perhaps all) of thier printers under 'nux.

---

### Post by JavaMeister on 2015-07-04
HP LaserJet PRO MFP M225dw, 
installed with HPLIP 
on Ubuntu 14.04 
connected via wireless LAN - 
will not print multiple copies when COPIES set to more than one on the ctl-P print menu. It prints one copy and n-1 blank pages.

Multiple copies works fine from MSW 7 system.

Help or pointer to appropriate forum?

---

### Post by Geoffrey_Arndt on 2015-07-04
Probably the right forum (but wrong thread).   More folks would read in new to Ubuntu section or if you *open your own thread* in this hardware forum.    Having said that, it seems **_your printer is supported for Cloud Print_** . . . worth a try IMHO.

HP Cloudprint support:  [http://support.hp.com/us-en/document/c02814760#N2680](http://support.hp.com/us-en/document/c02814760#N2680)

---

### Post by ag17india on 2017-08-17
Issue :  RAM - 4GB in 2 DIMM slots,   only 2GB detected.   

Specs:  

Eveything else runs fine.  
Processor : AMD SEMPRON 145 (2.8GHz) 
GPU : Nvidia GT 610 HDD : 500GB 
Ram clock speed : 590 mhz
 PSU powers all components no power issues 450-500Watt PSU.
 BIOS - flashed for latest version i am to believe.  
*Re-insterted RAM sticks by removing them and reinserting. Still problem persists. No dust issues.
 *UBUNTU version 16.0.4 LTS (XENIAL)  
CPU and other Temperatures - 35-39 Degrees (Celcius) (Stable)  

should i try Ubuntu 17 (non LTS) or MINT?   Can this problem be solved?

i tired inserting a screenshot but apparently only takes url links....

---

### Post by ag17india on 2017-08-17
See attachment for screenshot.

---

### Post by vasa1 on 2017-08-17
@ag17india, if you want help please feel free to start a new thread with a title that describes the issue you want help with.

---

### Post by ag17india on 2017-08-18
@vasa1 

I am sorry i thought this is the thread to discuss hardware incompatibility issues for desktop for the latest ubuntu release. will start a new thread.

---

### Post by rbmorse on 2017-10-22
**EPSON flatbed scanners** requiring proprietary Epkowa plug-in software.  Although Epson/Epkowa provides the plug-in through their iScan package at no charge, the package will not install in Ubuntu 17.10 due to a dependency issue.  My attempts to back-level the packages (libusb, libsane) have resulted only in myriad other incompatibilities in the system. 

The iScan package installs properly in the 16.4 LTS release. Recommend users requiring the use of a scanner not upgrade to 17.10 at this time.

---

### Post by paulgbrandon on 2018-02-04
[B]Please Only List
1)Type Of Hardware

Motherboard - Asus Prime X-399A 
CPU - AMD 1950X
Memory - 16GB 
Memory - Samsung 960 EVO m.2


4)Known Issue - No Network - tried wifi and Ethernet

Tried - Ubuntu 16.04.3. LTS
            Ubuntu 17.10.1

Live works fine. Bug report when installing either to the SSD or to another USB Stick.

"Installer Crashed"  

Bug Report - can't send - No Network;)


[/B][SIZE=1]
[/SIZE]

---

### Post by droid2bsd88 on 2018-03-02
Firstly Dapper Drake is no longer  officially supported. The next release slated for LTS support ifrastructure is [18.10]("https://www.ubuntu.com/info/release-end-of-life") slated for release in  October of this year

---

### Post by deadflowr on 2018-03-02
> **droid2bsd88 said:**
> Firstly Dapper Drake is no longer  officially supported. The next release slated for LTS support ifrastructure is [18.10]("https://www.ubuntu.com/info/release-end-of-life") slated for release in  October of this year

Next LTS comes out in April, next month.
LTS always come out in April, even numbered years. (the lone exception being 6.06 which was suppose to come out in April but was delayed)
Anything else is a standard release and only gets 9 months support.

Not sure what the Dapper Drake references, though.
The OP, perhaps. This thread is now 10 years old, so...

---

### Post by eeshanmulye2 on 2018-03-13
I have HP pavilion wave. Everything works except the discrete graphics card which is the AMD r9 m470. All I get is Intel he graphics 530 what do I do.

---

### Post by hikikomoridev on 2018-07-12
Radeon Pro WX2100 doesn't seem to be supporting more than one monitor at the moment with the driver situation it seems.

---

### Post by flipper88cfl22 on 2018-07-14
Dell Precision  Tower 3420 Small Form Factor Work Station
AMD/ATI FirePro WS2100 Series professional Graphics working under 18.04 with the amdgpu-pro drivers directly from AMD/ATIs' UNIX driver site
Classic Buckling Spring Early to Mid 190's Ibm PS/2 Key Board
Hewlett Packard 27es IPS 1920x1080  hull HD monitor  
2 terabyte  HDD (Spinning rust'
16GB Non Error Correcting Code (ECC)DDR4 RAM
EPSON WF-2660 MFP
Generic Microsoft Intelimouse optical mouse

---

### Post by djchandler on 2018-08-21
> **deadflowr said:**
> Next LTS comes out in April, next month.
LTS always come out in April, even numbered years. (the lone exception being 6.06 which was suppose to come out in April but was delayed)
Anything else is a standard release and only gets 9 months support.

Not sure what the Dapper Drake references, though.
The OP, perhaps. This thread is now 10 years old, so...

Dapper Drake and 6.06 are the same--my first Ubuntu install. Somebody following up after 12 years?
;)

---

### Post by iiiears2 on 2018-11-17
1)Type Of Hardware

  HP z420 
  Xeon e5-1620 3.6ghz 
  8gb ram



Tried both from usb stick 
- Ubuntu 18.04 LTS
            - Ubuntu  18.10

Live Fails. Fans spin up to maximum, system halts before showing bios messages. Waiting 5mins changed nothing. 

"Installer Crashed"  

Bug Report - can't send - No Boot:wink:

---

### Post by wildmanne39 on 2018-11-17
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by rbmorse on 2019-07-09
Ubuntu 19.4  fails to boot on machines equipped with AMD Ryzen series 3000 CPU and motherboards based upon AMD x570 PCH due to incompatibility with systemd release > 237.   This is probably a temporary situation.  

Interim solution: use Ubuntu 18.04 (LTS).

---

### Post by tuhelolu on 2019-07-10
> **rbmorse said:**
> Ubuntu 19.4  fails to boot on machines equipped with AMD Ryzen series 3000 CPU and motherboards based upon AMD x570 PCH due to incompatibility with systemd release > 237.   This is probably a temporary situation.  

Interim solution: use Ubuntu 18.04 (LTS).


Just echoing this. I just got an X570 board & ryzen 3600 and 18.04 has no issues at all, but 19.04 install media fails to boot with 100s of systemd errors. Interestingly, 19.04 also fails to boot inside a Virtual Machine under Windows 10 (both Virtual Box & VMWare) with the exact same issue, basically showing this is cpu/chipset related.

Hopefully this won't be too hard to fix...

EDIT: this is the core issue. [https://linuxreviews.org/AMD_Ryzen_3000_series_CPUs_can%27t_do_Random_on_boot_causing_Boot_Failure_on_newer_Linux_distributions](https://linuxreviews.org/AMD_Ryzen_3000_series_CPUs_can%27t_do_Random_on_boot_causing_Boot_Failure_on_newer_Linux_distributions)

---

### Post by jims2321 on 2019-07-17
It appears to be an issue with 3000 AMD Ryzen series in general.  I have 3900x on a B450 and it will not install.  I reinstall a Ryzen 1400 or 2600 and it will work.

Interestingly  RHEL 7.x and 8.x will install..

---

### Post by cookiecruncher on 2020-06-03
AMD RX470 graphics card DVI outputs no usable audio.

My RX470 graphics card HDMI connector failed while repairing someones monitor and had to start using the DVI output connector with a DVI to HDMI adaptor. My monitor (Dell S2340) produces no usable audio on jack output. Tested both Ubuntu and Kubuntu.  Tested and works normally on Windows 10.

---

### Post by hk42 on 2020-10-21
I bought this device:
https://www.aliexpress.com/item/4000950516104.html?ug_edm_item_id=4000950516104&tracelog=rowan&rowan_id1=user_add_wishlist_remind_1_1_en_US_2020-10-20&rowan_msg_id=0086biz_add_wishlist:2001:e078af128ceb4c848e6f58b7c738bf81_548424$56051e5203d0437b99e29c1cf9835453&ck=in_edm_other
It is not clearly said that it uses a fan.
But as W10 users regret that there is no way to switch it off when booting Ubuntu it is off and there is no simple way to switch it on :-)
I made an hardware mod to quickly solve this problem but this is not for every body.
On the other hand this device has many advantages :
It is cheaper
It uses a micro sd card with nothing "out of the box"
It has an additional  USB type C port .
The box is bigger than my passive cooled BT3 pro.
So if you are prepared to do hardware mods on the cooling system
it is a good choice.
Also Bios menu  is very poor on this device but it allowed Ubuntu without problems.

---

### Post by olavGV§l2n£OA2xH on 2020-10-21
Type Of Hardware: External USB 2.0 Sound Card
Hardware Maker: TASCAM
Hardware Model: US-600
Known issue: Does not get recognized in Ubuntu 20.04 64-bit. USB led turns on on the device.
The following is the output of /var/log/syslog when plugging in the device.
```

Oct 21 21:25:13 calcolatore kernel: [ 1995.841353] usb 2-2: new high-speed USB device number 8 using xhci_hcd
Oct 21 21:25:13 calcolatore kernel: [ 1995.990681] usb 2-2: New USB device found, idVendor=0644, idProduct=8035, bcdDevice= 1.00
Oct 21 21:25:13 calcolatore kernel: [ 1995.990686] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Oct 21 21:25:13 calcolatore kernel: [ 1995.990690] usb 2-2: Product: US-600
Oct 21 21:25:13 calcolatore kernel: [ 1995.990693] usb 2-2: Manufacturer: TASCAM
Oct 21 21:25:13 calcolatore kernel: [ 1995.990696] usb 2-2: SerialNumber: no serial number
Oct 21 21:25:13 calcolatore mtp-probe: checking bus 2, device 8: "/sys/devices/pci0000:00/0000:00:14.0/usb2/2-2"
Oct 21 21:25:13 calcolatore mtp-probe: bus: 2, device: 8 was not an MTP device
Oct 21 21:25:13 calcolatore mtp-probe: checking bus 2, device 8: "/sys/devices/pci0000:00/0000:00:14.0/usb2/2-2"
Oct 21 21:25:13 calcolatore mtp-probe: bus: 2, device: 8 was not an MTP device

```
TASCAM does not currently provide a Linux driver for it (it's also a discontinued product, but it works great under Windows).

---

