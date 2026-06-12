---
title: "really slow everything. ubuntu 8.04 (im basically a complete begginer)"
date: 2008-08-24
forum: General Help
---

### Post by bennyturok on 2008-08-24
so basically what the title says... boot is slow. getting to the session login is moderately slow, going from the session to gnome is REALLY slow. and after that opening any applications is slow. working on the applications is slow. i cant really view any video or hear any music since it gets stuck, breaks up allot. same with viewing videos on youtube, youtube video like sites or playing any java/flash games (i was using vlc before the clean install i just did)

i just did a clean install in the morning and everything was already slow before installing anything.   and after installing all the updates it was still about the same speed (or so it feels like it).  it wasn't as slow with windows xp.  so this is pretty annoying. if i type the words sometimes it lags behind the letters when i type...

just to make it clear my previous install was even slower than it is right now.  i thought it might be fixed with a clean install...

my system is:
toshiba satellite a15
712 ram (i also tried operating it with only the 512 installed but it was the same thing)
p4m 2.2ghz
fan is working and i also use a cooling pad.
it has integrated graphics (32 megs i think)

i dont think it has to do with hardware problems but if it is help me find out so maybe i could change whatever is causing the problem.

ive found a couple of tips around saying that it might have to do with the networking software or something of that sort but nothing concrete or easily explained.

also ive found everything works a bit faster when i boot from system recovery instead of directly. i think its because everything its preloaded or just more ready to be loaded since it was checked...  but sincerely i have no idea....   

i basically need people patient enough to tell me: go to applications>accessories>terminal and then in quotes step by step explain: type "sudo apt-get bla bla" or stuff like those... if anyone thinks i can fix it from root i have no idea how to enter it other than restarting my computer and entering it through system recovery (done once because i had to change user pass witch i forgot. thankfully i found and easy enough guide to do that.)
***
the only things ive installed in this clean install is all the updates, flash, java and google toolbar.   i uninstalled all the games and the mp3 player that comes installed in ubuntu. (since i dont use them)

i want to install skype, vlc, amule, picasa and a bunch of firefox add-ons.  Uninstall: totem player (movie player)

Just saying in case it  helps or for tips around it...  i wont install any of those yet, since it would be useless with my system so slow.
i repeat. its been slow from the very start. since before i did anything.
***
well. ill wait for help. hope it comes. 
have fun helping me :) AND
thank you, Gracias, Arigato And Toda.  he he.

EDIT: something that might be worth mentioning, i installed ubuntu on another computer.  i took out the hard drive from this one and with a usb adapter i installed it in a pc.

---

### Post by bennyturok on 2008-08-25
also.  when from recovery i click fix packages. it says theirs not a folder and it dosent connect to the sources. but i guess thats not such a big deal.   i hope... 
unsuprisingly nobody has answered my previous help request.  dont ask me why im not suprised......
you guessed.....

well.. anyway. ill aprecciate any suggestiong or help.  thanks in advance for the great adventurer who adventures to help me...

---

### Post by bennyturok on 2008-08-25
wow.. its very slow... still cant watch any videos :(
and yea. i confirmed it again.  booting through recovery mode makes my machine a little faster when i use it. I guess that should be weird... i mean. what extra steps does recovery mode takes that normal boot dosent.... if any...   maybe more time....

well... meanwhile ill keep thanking the air until someone crazy enough comes to help me...  or excentric :P

---

### Post by -Zeus- on 2008-08-25
just so we're clear......... you have removed the live CD, correct??

---

### Post by forger on 2008-08-25
1) As Zeus said, are you sure that you **installed ubuntu** and you're not running it from the cd?
2) Did you install the drivers required? Try System > Administration > Hardware drivers
Make sure you have everything checked there
3) Did you install the codecs for the videos you're trying to watch?
a) **[COLOR="Red"]Close all your running programs![/COLOR]**
b) go to Applications > Accessories > Terminal and execute this command:
```
sudo apt-get install ubuntu-restricted-extras
```
c) When it's done installing, reboot and try watching the videos again

---

### Post by bennyturok on 2008-08-25
yes, ive never put it in. EVER.

this might be important.. since my cd drive dosent work very well i cant isntall ubuntu through my computer.  so what i have been doing is taking out the hard drive connecting it to a pc through a usb adapter and installing it through another computer.  maybe the configuration of that pc is what making my laptop be all ****** up.  can anyone tell me if theirs a way to check/fix this? 

thanks.
Edit:
1)im not that dumb. of course im not running from  the live cd.
2)im not trying to watch any videos from my computer right now. only online videos like in youtube or so.  and yes i installed flash.....  it does load,  but the video starts the sound goes much ahead from the video. video stays stuck...  and sometimes audio gets cut allot...  anyway. im certain this is not the problem. i know my way around playing videos. -.-
3)i checked the hardware drivers and it says their is no proprietary drivers.
im going to check the last one in a sec.

---

### Post by forger on 2008-08-25
Why not create a new user and try logging in and using the new username?
System > Administration > Users and Groups > unlock > add user

---

### Post by morbid_bean on 2008-08-25
That could be the problem...does it run slow on the pc you installed it on?

---

### Post by bennyturok on 2008-08-25
i wasnt able to get it running on the computer for uknown reasons...  i did put to boot from usb-hdd  but it didnt.   for some reason that computer didnt want to.   

right now i dont have any acces to it. i did the clean install on a borrowed computer.  

i knew my way around windows well. so i know how to manage around some things. i mean. installing the required stuff and drivers.  basic stuff like those i know. if my windows was all slow like this i could probablly fix it.  but im new to linux all together.   i changed because i feel linux is the future. so i really dont want to go back to windows because of a problem like this...

anyway. thanks for the help. hope it continious

---

### Post by -Zeus- on 2008-08-25
> **bennyturok said:**
> 1)im not that dumb. of course im not running from  the live cd.

You did bill yourself as a complete beginner... I'm just being safe :-P

---

### Post by bennyturok on 2008-08-25
to linux that is...  should i do what forger recommender about installing restricted extras?

oh, and about the username thing. i had done that in my previous install to see if it would go faster.  did not work.  dont see why it would work this time around.

---

### Post by WRDN on 2008-08-25
Try disabling the graphical effects, if not done so already. To do this, click System > Preferences > Appearance. Select the Visual Effects tab, and select "None".

---

### Post by venator260 on 2008-08-25
You say that you installed Ubuntu with another computer via usb and then stuck the hard drive into your computer? 

If so, go to a terminal and type: 

```
sudo dpkg-reconfigure xserver-xorg
```

Answer the questions and then restart.

This is what I had to do with my laptop after installing with a USB adapter, and it works just fine now, and it has less RAM and a slower processor than what you have.

---

### Post by bennyturok on 2008-08-25
well. after doing what venator told me to i got an error when turning on my computer.
> Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

if that isnt normal then how or should i reverse it. 
i dont think its any faster now. if anything its slower now. 

p.s. i had already disabled all the special effects. i did it the first moment i turned on the computer for the first time.....

---

### Post by bennyturok on 2008-08-25
*if by friday i havent been able to fix this problem i think ill go back to *windows...  windows 2000 should do everything i need at a descent speed.  dont *really want to since i have to find all the drivers to even be able to enter *internet through ethernet cable. but its seems  like a more viable option right *now. 
*
*anyway, theirs allot of geniuses around this forums so i hope i wont have to go to *that extreme..  
*
*if anything ill try ubuntu again in a year or so...  

p.s.  this is more of a bump for the forums than anything....

---

### Post by SammerHammer on 2008-08-25
Did you make a partition for swap space while installing?
Also, is there any application that you may have added to the Autostart menu, because that could also be a problem.

If nothing works, use Xubuntu instead.

sudo aptitude install xubuntu-desktop

After the download+installation is done, reboot, and at the login window, click session, then click Xfce

---

### Post by bennyturok on 2008-08-25
seriously dont feel like installing xubuntu...  this was a clean install.  from a wiped out hard drive... i just followed the guided mode..   and as i said i havent installed any applications yet.  other than flash openjdk google toolbar and 2 firefox addons that i installed after posting this.  

anyway. if by thursday nobody manages to help me out with this ill try xubuntu....

---

### Post by forger on 2008-08-25
Let's try to reverse it, execute these commands:
```

sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm restart

```
This should give you back your desktop, slow or not, it's with the default safe 'vesa' graphics driver.

Now, I need more information for your hardware and software in general
Reply with the FULL output of these commands:
```

lspci
lsusb
sudo lshw -short
sudo lshw -C display
sudo lshw -C disk
sudo lshw -C storage

```

Put it in [CODE] or [QUOTE] tags

---

### Post by bennyturok on 2008-08-25
lspci
> 00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)

lsusb
> Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 045e:00f0 Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000  

sudo lshw -short
>                                system         Satellite A15
/0                             bus            Portable PC
/0/0                           memory         128KiB BIOS
/0/4                           processor      Mobile Intel(R) Pentium(R) 4 - M C
/0/4/12                        memory         8KiB L1 cache
/0/4/13                        memory         512KiB L2 cache
/0/81                          memory         768MiB System Memory
/0/81/0                        memory         256MiB SODIMM SDRAM Synchronous
/0/81/1                        memory         512MiB SODIMM SDRAM Synchronous
/0/100                         bridge         82852/82855 GM/GME/PM/GMV Processo
/0/100/0.1                     system         82852/82855 GM/GME/PM/GMV Processo
/0/100/0.3                     system         82852/82855 GM/GME/PM/GMV Processo
/0/100/2                       display        82852/855GM Integrated Graphics De
/0/100/2.1                     display        82852/855GM Integrated Graphics De
/0/100/1d                      bus            82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-
/0/100/1d.7                    bus            82801DB/DBM (ICH4/ICH4-M) USB2 EHC
/0/100/1e                      bridge         82801 Mobile PCI Bridge
/0/100/1e/8        eth1        network        82801DB PRO/100 VE (MOB) Ethernet 
/0/100/1e/b                    bridge         ToPIC100 PCI to Cardbus Bridge wit
/0/100/1f                      bridge         82801DBM (ICH4-M) LPC Interface Br
/0/100/1f.1        scsi0       storage        82801DBM (ICH4-M) IDE Controller
/0/100/1f.1/0      /dev/sda    disk           40GB TOSHIBA MK4021GA
/0/100/1f.1/0/1    /dev/sda1   volume         35GiB EXT3 volume
/0/100/1f.1/0/2    /dev/sda2   volume         1451MiB Extended partition
/0/100/1f.1/0/2/5  /dev/sda5   volume         1451MiB Linux swap / Solaris parti
/0/100/1f.1/1      /dev/cdrom  disk           UJDA750 DVD/CDRW
/0/100/1f.5                    multimedia     82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-
/0/100/1f.6                    communication  82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-
/1                             power          LP643E

sudo lshw -C display
>  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0

sudo lshw -C disk
>   *-disk                  
       description: ATA Disk
       product: TOSHIBA MK4021GA
       vendor: Toshiba
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: GA22
       serial: 936N9618T
       size: 37GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000be771
  *-cdrom
       description: DVD reader
       product: UJDA750 DVD/CDRW
       vendor: MATSHITA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.51
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=open

sudo lshw -C storage
>   *-ide                   
       description: IDE interface
       product: 82801DBM (ICH4-M) IDE Controller
       vendor: Intel Corporation
       physical id: 1f.1
       bus info: pci@0000:00:1f.1
       logical name: scsi0
       logical name: scsi1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: ide bus_master emulated
       configuration: driver=ata_piix latency=0 module=ata_piix


there...  is it just me or the fact that it says 33mhz is not good.  

also. after doing the thing you told me to do first i still got an error... didnt copy it tho...   anyway. thats not important right now.

---

### Post by forger on 2008-08-25
OK thanks, do these commands now:
```
sudo apt-get update
sudo apt-get autoremove --purge
sudo apt-get autoclean
```

And post the output of these commands:
```
cat /etc/X11/xorg.conf
df -h
```

---

### Post by forger on 2008-08-25
To speed things up a bit, be sure to post what I asked on the previous post, and take a look at your xorg.conf

If you **do not see** a line like:
> Driver "intel"
..under section "device" in your xorg.conf, install displayconfig-gtk
```
sudo apt-get install displayconfig-gtk
gksu displayconfig-gtk
```

Choose your monitor and screen resolution, also choose the graphics card driver (driver's name is **intel**).
Press OK, and execute:
```
sudo /etc/init.d/gdm restart
```

Now post once more the output of
```
cat /etc/X11/xorg.conf
```

---

### Post by bennyturok on 2008-08-25
the error that comes up when i start ubuntu is 

> Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

but i dont think its giving me any problem.  but i might want to fix that once my computer is speedy. if ever...

---

### Post by bennyturok on 2008-08-25
here it is.  i dont think theirs anything abount intel driver... 
> benny@bennytc-lap:~$ cat /etc/X11/xorg.conf
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
	Option		"XkbLayout"	"sp"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
benny@bennytc-lap:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G  2.8G   32G   9% /
varrun                371M  100K  371M   1% /var/run
varlock               371M     0  371M   0% /var/lock
udev                  371M   52K  371M   1% /dev
devshm                371M   12K  371M   1% /dev/shm
lrm                   371M   39M  332M  11% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       36G  2.8G   32G   9% /home/benny/.gvfs


---

### Post by forger on 2008-08-25
Ok, you could try do this after the instructions in the previous two posts:
```
sudo aptitude reinstall xserver-xorg x11-xkb-utils libxkbfile1 x11-common xserver-xorg-video-intel debianutils ubuntu-desktop gdm gnome-panel gnome-system-tools gnome-utils alsa-base alsa-utils
```

Can you now do the rest of the commands? I'm eager to see the output

---

### Post by forger on 2008-08-25
> **bennyturok said:**
> i dont think theirs anything abount intel driver...
true, use displayconfig-gtk to add the driver (you can set it in the "graphics card" tab) and the monitor and screen resolution

---

### Post by bennyturok on 2008-08-25
i did what you told me to do in post 21. other than my resolution not being right theirs no change in speed...  or at least nothing noticeable.
> # xorg.conf (X.Org X Window System server configuration file)
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
	Option		"XkbLayout"	"sp"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"Intel 85x"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
	Vendorname	"Intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"Intel 85x"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	1
	Vendorname	"Intel"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection


---

### Post by forger on 2008-08-25
Weird, it says driver i810, are you sure you selected driver name "intel"?

Do these:
```

sudo aptitude reinstall x11-xkb-utils libxkbfile1 x11-common xserver-xorg-video-intel debianutils ubuntu-desktop gdm gnome-panel gnome-system-tools gnome-utils alsa-base alsa-utils
sudo sed -i -e 's/Driver "i810"/Driver "intel"/' -e 's/modeline "640x480@60" 25\.2 640 656 752 800 480 490 492 525 -vsync -hsync//' -e 's/Virtual 640 480//' -e 's/Modes "640x480@60"//' /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart

```
I hope this will fix the resolution problem and kbd error (and possibly speed?)

When you are saying it's slow, what do you mean? What do you see of these:
1) mouse pointer going slowly?
2) if you move a window it moves slowly, leaving "marks" all over the screen?
3) the programs load very slowly?
4) the videos you mentioned earlier are displayed "chopped up"?

Post the output of xorg.conf once more:
```
cat /etc/X11/xorg.conf
```

Can you also post the output of:
```
top -b -n 1
ps aux
```

---

### Post by bennyturok on 2008-08-25
after reinstalling everything i got this error:
> E: Couldn't configure pre-depend x11-common for x11-xkb-utils, probably a dependency cycle.
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      


if you meant to do > sudo apt-get install displayconfig-gtk
 i had already done that and it said it said the latest version was already installed or something like that.... 
when i select the intel driver it gives me allot of options...  

anyway. if you mean if i can do all the commands youve told me to do again ill do it.

---

### Post by bennyturok on 2008-08-25
and all of the above... thats what i mean by slow.

---

### Post by forger on 2008-08-25
> **bennyturok said:**
> 
when i select the intel driver it gives me allot of options...  


OK never mind the intel driver, let's stick with i810.
If you haven't already done it:
```
gksu gedit /etc/X11/xorg.conf
```
Locate the Driver "intel" line and make it "i810" and restart gdm

I also asked for two more command outputs:
```
top -b -n 1
ps aux
```

If I can't find anything here.. I'll probably be out of ideas :(

---

### Post by bennyturok on 2008-08-25
> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"sp"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes		"800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "screen2" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"Intel 5430"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	0
	Vendorname	"Intel"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "device" # 
	Identifier	"device2"
	Boardname	"Intel 85x"
	Busid		"PCI:0:2:1"
	Driver		"intel"
	Screen	0
	Vendorname	"Intel"
EndSection
Section "screen" # 
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor2"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

> top - 03:02:57 up 11 min,  2 users,  load average: 2.29, 2.20, 1.14
Tasks: 100 total,   1 running,  99 sleeping,   0 stopped,   0 zombie
Cpu(s): 55.9%us, 10.9%sy,  3.4%ni, 23.7%id,  5.4%wa,  0.2%hi,  0.3%si,  0.0%st
Mem:    758312k total,   482284k used,   276028k free,    14676k buffers
Swap:  1485972k total,        0k used,  1485972k free,   293792k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5861 benny     20   0  146m  55m  19m S 10.3  7.5   1:53.44 firefox            
 6000 benny     20   0  2304 1000  756 R  6.9  0.1   0:00.12 top                
 5437 root      20   0 36008  10m 6212 S  1.7  1.5   1:01.85 Xorg               
    1 root      20   0  2844 1692  544 S  0.0  0.2   0:01.26 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.28 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.18 kblockd/0          
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.12 kacpid             
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 kacpi_notify       
  118 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 kseriod            
  149 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
  150 root      20   0     0    0    0 S  0.0  0.0   0:00.16 pdflush            
  151 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0            
  192 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0              
 1462 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd      
 1465 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd              
 1486 root      15  -5     0    0    0 S  0.0  0.0   0:00.26 ata/0              
 1490 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux            
 1610 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0          
 1612 root      15  -5     0    0    0 S  0.0  0.0   0:00.58 scsi_eh_1          
 2392 root      15  -5     0    0    0 S  0.0  0.0   0:00.30 kjournald          
 2595 root      16  -4  2520 1040  380 S  0.0  0.1   0:00.64 udevd              
 2768 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused          
 2948 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 pccardd            
 4281 root      20   0  1716  512  440 S  0.0  0.1   0:00.00 getty              
 4282 root      20   0  1716  508  440 S  0.0  0.1   0:00.00 getty              
 4286 root      20   0  1716  512  440 S  0.0  0.1   0:00.00 getty              
 4287 root      20   0  1716  508  440 S  0.0  0.1   0:00.00 getty              
 4289 root      20   0  1716  508  440 S  0.0  0.1   0:00.00 getty              
 4397 root      24   4     0    0    0 S  0.0  0.0   0:05.18 ktoshkeyd          
 4466 root      20   0  2852 1780  692 S  0.0  0.2   0:00.18 acpid              
 4511 root      15  -5     0    0    0 S  0.0  0.0   0:01.60 kondemand/0        
 4572 syslog    20   0  1936  652  512 S  0.0  0.1   0:00.04 syslogd            
 4625 root      20   0  1872  536  444 S  0.0  0.1   0:00.04 dd                 
 4627 klog      20   0  3148 2052  424 S  0.0  0.3   0:00.14 klogd              
 4649 messageb  20   0  2828 1300  796 S  0.0  0.2   0:01.80 dbus-daemon        
 4665 root      20   0 12892 2100 1820 S  0.0  0.3   0:00.10 NetworkManager     
 4679 root      20   0  3536 1312 1120 S  0.0  0.2   0:00.00 NetworkManagerD    
 4692 root      20   0  4112 1104  904 S  0.0  0.1   0:00.00 system-tools-ba    
 4712 avahi     20   0  2760 1412 1208 S  0.0  0.2   0:00.12 avahi-daemon       
 4713 avahi     20   0  2760  464  288 S  0.0  0.1   0:00.00 avahi-daemon       
 4752 root      20   0  5920 2268 1696 S  0.0  0.3   0:00.02 cupsd              
 4818 root      20   0  2020  904  776 S  0.0  0.1   0:00.34 dhcdbd             
 4837 haldaemo  20   0  6180 4188 3568 S  0.0  0.6   0:01.68 hald               
 4840 root      20   0  7884 2388 1628 S  0.0  0.3   0:00.40 console-kit-dae    
 4902 root      20   0  3352 1160  976 S  0.0  0.2   0:00.10 hald-runner        
 4915 root      20   0  3416 1152 1004 S  0.0  0.2   0:00.02 hald-addon-inpu    
 4924 root      20   0  3428 1224 1072 S  0.0  0.2   0:00.02 hald-addon-cpuf    
 4925 haldaemo  20   0  2204  960  828 S  0.0  0.1   0:00.04 hald-addon-acpi    
 4946 root      20   0  3420 1140  988 S  0.0  0.2   0:00.74 hald-addon-stor    
 4985 root      20   0  3172 1236 1076 S  0.0  0.2   0:00.00 hcid               
 4991 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn          
 4992 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btdelconn          
 5003 root      20   0  3084 1288 1140 S  0.0  0.2   0:00.00 bluetoothd-serv    
 5007 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd           
 5012 root      20   0  3020 1088  956 S  0.0  0.1   0:00.00 bluetoothd-serv    
 5061 dhcp      20   0  2440 1180  868 S  0.0  0.2   0:00.00 dhclient           
 5104 daemon    20   0  1984  420  300 S  0.0  0.1   0:00.00 atd                
 5118 root      20   0  2104  888  712 S  0.0  0.1   0:00.00 cron               
 5199 root      20   0  1716  508  440 S  0.0  0.1   0:00.00 getty              
 5425 root      20   0 14060 1608  972 S  0.0  0.2   0:00.10 gdm                
 5426 root      20   0 14524 2988 2204 S  0.0  0.4   0:00.36 gdm                
 5475 benny     20   0  7108 4176 1900 S  0.0  0.6   0:05.72 gconfd-2           
 5477 benny     20   0 14340 2048 1656 S  0.0  0.3   0:00.15 gnome-keyring-d    
 5480 benny     20   0 28860 7500 6296 S  0.0  1.0   0:01.66 x-session-manag    
 5595 benny     20   0 23056 6796 4868 S  0.0  0.9   0:01.26 seahorse-agent     
 5599 benny     20   0  2692 1088  732 S  0.0  0.1   0:00.60 dbus-daemon        
 5600 benny     20   0 47196  17m  10m S  0.0  2.3   0:08.36 gnome-settings-    
 5608 benny     20   0 28472 5712 3268 S  0.0  0.8   0:01.77 pulseaudio         
 5611 benny     20   0  5776 2264 1848 S  0.0  0.3   0:00.14 gconf-helper       
 5622 benny     20   0 18160 9848 7004 S  0.0  1.3   0:04.92 metacity           
 5623 benny     20   0 68880  19m  12m S  0.0  2.7   0:16.36 gnome-panel        
 5625 benny     20   0 43404  14m  11m S  0.0  2.0   0:05.99 nautilus           
 5634 benny     20   0 15216 2548 1688 S  0.0  0.3   0:03.30 gnome-screensav    
 5636 benny     20   0 31928 3156 2432 S  0.0  0.4   0:02.22 bonobo-activati    
 5646 benny     20   0  5372 2096 1800 S  0.0  0.3   0:00.20 gvfsd              
 5651 benny     20   0 29048 1888 1500 S  0.0  0.2   0:00.06 gvfs-fuse-daemo    
 5656 benny     20   0 26328  13m 9032 S  0.0  1.8   0:03.44 update-notifier    
 5659 benny     20   0 62344  10m 8612 S  0.0  1.4   0:01.53 evolution-alarm    
 5661 benny     20   0 15216 5524 4680 S  0.0  0.7   0:00.54 tracker-applet     
 5664 benny     39  19 31504  10m 2284 S  0.0  1.4   0:00.88 trackerd           
 5668 benny     20   0 24272  11m 7164 S  0.0  1.6   0:02.56 python             
 5669 benny     20   0 25200  11m 8000 S  0.0  1.6   0:05.96 nm-applet          
 5674 benny     20   0 20672 4624 3424 S  0.0  0.6   0:00.22 gnome-volume-ma    
 5675 benny     20   0 23188 8276 6328 S  0.0  1.1   0:01.66 gnome-power-man    
 5688 benny     20   0 66928 6696 5340 S  0.0  0.9   0:00.83 evolution-data-    
 5701 benny     20   0 38944 9756 8104 S  0.0  1.3   0:01.17 evolution-excha    
 5712 benny     20   0  5372 2140 1844 S  0.0  0.3   0:00.12 gvfsd-burn         
 5827 benny     20   0 23316 9.9m 7524 S  0.0  1.3   0:02.32 trashapplet        
 5830 benny     20   0 13836 2604 2224 S  0.0  0.3   0:00.24 gvfsd-trash        
 5841 benny     20   0 44356  14m 9660 S  0.0  1.9   0:03.26 mixer_applet2      
 5844 benny     20   0 26044  12m 8548 S  0.0  1.7   0:02.64 fast-user-switc    
 5943 benny     20   0 74948  20m  10m S  0.0  2.7   0:08.06 gnome-terminal     
 5952 benny     20   0  2912  860  708 S  0.0  0.1   0:00.02 gnome-pty-helpe    
 5953 benny     20   0  5592 3004 1412 S  0.0  0.4   0:01.82 bash               
 5984 benny     20   0 23444  12m 7140 S  0.0  1.7   0:03.46 notification-da 
> USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.1  0.2   2844  1692 ?        Ss   02:51   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   02:51   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   02:51   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   02:51   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   02:51   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   02:51   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S<   02:51   0:00 [khelper]
root        41  0.0  0.0      0     0 ?        S<   02:51   0:00 [kblockd/0]
root        44  0.0  0.0      0     0 ?        S<   02:51   0:00 [kacpid]
root        45  0.0  0.0      0     0 ?        S<   02:51   0:00 [kacpi_notify]
root       118  0.0  0.0      0     0 ?        S<   02:51   0:00 [kseriod]
root       149  0.0  0.0      0     0 ?        S    02:51   0:00 [pdflush]
root       150  0.0  0.0      0     0 ?        S    02:51   0:00 [pdflush]
root       151  0.0  0.0      0     0 ?        S<   02:51   0:00 [kswapd0]
root       192  0.0  0.0      0     0 ?        S<   02:51   0:00 [aio/0]
root      1462  0.0  0.0      0     0 ?        S<   02:52   0:00 [ksuspend_usbd]
root      1465  0.0  0.0      0     0 ?        S<   02:52   0:00 [khubd]
root      1486  0.0  0.0      0     0 ?        S<   02:52   0:00 [ata/0]
root      1490  0.0  0.0      0     0 ?        S<   02:52   0:00 [ata_aux]
root      1610  0.0  0.0      0     0 ?        S<   02:52   0:00 [scsi_eh_0]
root      1612  0.0  0.0      0     0 ?        S<   02:52   0:00 [scsi_eh_1]
root      2392  0.0  0.0      0     0 ?        S<   02:52   0:00 [kjournald]
root      2595  0.0  0.1   2520  1040 ?        S<s  02:52   0:00 /sbin/udevd --d
root      2768  0.0  0.0      0     0 ?        S<   02:52   0:00 [kpsmoused]
root      2948  0.0  0.0      0     0 ?        S<   02:52   0:00 [pccardd]
root      4281  0.0  0.0   1716   512 tty4     Ss+  02:52   0:00 /sbin/getty 384
root      4282  0.0  0.0   1716   508 tty5     Ss+  02:52   0:00 /sbin/getty 384
root      4286  0.0  0.0   1716   512 tty2     Ss+  02:52   0:00 /sbin/getty 384
root      4287  0.0  0.0   1716   508 tty3     Ss+  02:52   0:00 /sbin/getty 384
root      4289  0.0  0.0   1716   508 tty6     Ss+  02:52   0:00 /sbin/getty 384
root      4397  0.8  0.0      0     0 ?        SN   02:52   0:05 [ktoshkeyd]
root      4466  0.0  0.2   2852  1780 ?        Ss   02:52   0:00 /usr/sbin/acpid
root      4511  0.2  0.0      0     0 ?        S<   02:52   0:01 [kondemand/0]
syslog    4572  0.0  0.0   1936   652 ?        Ss   02:52   0:00 /sbin/syslogd -
root      4625  0.0  0.0   1872   536 ?        S    02:52   0:00 /bin/dd bs 1 if
klog      4627  0.0  0.2   3148  2052 ?        Ss   02:52   0:00 /sbin/klogd -P
108       4649  0.2  0.1   2828  1300 ?        Ss   02:52   0:01 /usr/bin/dbus-d
root      4665  0.0  0.2  12892  2100 ?        Ssl  02:52   0:00 /usr/sbin/Netwo
root      4679  0.0  0.1   3536  1312 ?        Ss   02:52   0:00 /usr/sbin/Netwo
root      4692  0.0  0.1   4112  1104 ?        Ss   02:52   0:00 /usr/bin/system
avahi     4712  0.0  0.1   2760  1412 ?        Ss   02:52   0:00 avahi-daemon: r
avahi     4713  0.0  0.0   2760   464 ?        Ss   02:52   0:00 avahi-daemon: c
root      4752  0.0  0.2   5920  2268 ?        Ss   02:52   0:00 /usr/sbin/cupsd
root      4818  0.0  0.1   2020   904 ?        Ss   02:52   0:00 /usr/sbin/dhcdb
111       4837  0.2  0.5   6180  4188 ?        Ss   02:52   0:01 /usr/sbin/hald
root      4840  0.0  0.3   7884  2388 ?        Ssl  02:52   0:00 /usr/sbin/conso
root      4902  0.0  0.1   3352  1160 ?        S    02:52   0:00 hald-runner
root      4915  0.0  0.1   3416  1152 ?        S    02:52   0:00 hald-addon-inpu
root      4924  0.0  0.1   3428  1224 ?        S    02:52   0:00 /usr/lib/hal/ha
111       4925  0.0  0.1   2204   960 ?        S    02:52   0:00 hald-addon-acpi
root      4946  0.1  0.1   3420  1140 ?        S    02:52   0:00 hald-addon-stor
root      4985  0.0  0.1   3172  1236 ?        Ss   02:52   0:00 /usr/sbin/hcid
root      4991  0.0  0.0      0     0 ?        S<   02:52   0:00 [btaddconn]
root      4992  0.0  0.0      0     0 ?        S<   02:52   0:00 [btdelconn]
root      5003  0.0  0.1   3084  1288 ?        S    02:52   0:00 /usr/lib/blueto
root      5007  0.0  0.0      0     0 ?        S<   02:52   0:00 [krfcommd]
root      5012  0.0  0.1   3020  1088 ?        S    02:52   0:00 /usr/lib/blueto
dhcp      5061  0.0  0.1   2440  1180 ?        S    02:52   0:00 /sbin/dhclient
daemon    5104  0.0  0.0   1984   420 ?        Ss   02:52   0:00 /usr/sbin/atd
root      5118  0.0  0.1   2104   888 ?        Ss   02:52   0:00 /usr/sbin/cron
root      5199  0.0  0.0   1716   508 tty1     Ss+  02:52   0:00 /sbin/getty 384
root      5425  0.0  0.2  14060  1608 ?        Ss   02:56   0:00 /usr/sbin/gdm
root      5426  0.0  0.3  14524  2988 ?        S    02:56   0:00 /usr/sbin/gdm
root      5437 20.2  1.5  19884 11772 tty9     Rs+  02:56   1:38 /usr/bin/X :0 -
benny     5475  1.2  0.5   7108  4176 ?        S    02:57   0:05 /usr/lib/libgco
benny     5477  0.0  0.2  14340  2048 ?        S    02:57   0:00 /usr/bin/gnome-
benny     5480  0.3  0.9  28860  7500 ?        Ssl  02:57   0:01 x-session-manag
benny     5595  0.2  0.8  23056  6796 ?        Ss   02:57   0:01 /usr/bin/seahor
benny     5599  0.1  0.1   2692  1088 ?        Ss   02:57   0:00 dbus-daemon --f
benny     5600  1.9  2.2  47196 17420 ?        Sl   02:57   0:08 gnome-settings-
benny     5608  0.4  0.7  28472  5712 ?        Sl   02:57   0:01 /usr/bin/pulsea
benny     5611  0.0  0.2   5776  2264 ?        S    02:57   0:00 /usr/lib/pulsea
benny     5622  1.4  1.2  18160  9848 ?        S    02:57   0:06 /usr/bin/metaci
benny     5623  3.9  2.6  68880 20344 ?        S    02:57   0:16 gnome-panel --s
benny     5625  1.3  2.0  43404 15336 ?        S    02:57   0:06 nautilus --no-d
benny     5634  1.1  0.3  15216  2548 ?        Ss   02:57   0:04 gnome-screensav
benny     5636  0.5  0.4  31928  3156 ?        Ssl  02:57   0:02 /usr/lib/bonobo
benny     5646  0.0  0.2   5372  2096 ?        S    02:57   0:00 /usr/lib/gvfs/g
benny     5651  0.0  0.2  29048  1888 ?        Ssl  02:57   0:00 /usr/lib/gvfs//
benny     5656  0.8  1.8  26328 13796 ?        S    02:57   0:03 update-notifier
benny     5659  0.3  1.3  62344 10360 ?        Sl   02:57   0:01 /usr/lib/evolut
benny     5661  0.1  0.7  15216  5524 ?        S    02:57   0:00 tracker-applet
benny     5664  0.2  1.3  31504 10392 ?        SNl  02:57   0:00 trackerd
benny     5668  0.6  1.6  24272 12168 ?        S    02:57   0:02 python /usr/sha
benny     5669  1.5  1.5  25200 11808 ?        S    02:57   0:06 nm-applet --sm-
benny     5674  0.0  0.6  20672  4624 ?        Ss   02:57   0:00 /usr/lib/gnome-
benny     5675  0.4  1.0  23188  8276 ?        Ss   02:57   0:01 gnome-power-man
benny     5688  0.2  0.8  66928  6696 ?        Sl   02:57   0:00 /usr/lib/evolut
benny     5701  0.2  1.2  38944  9756 ?        Sl   02:57   0:01 /usr/lib/evolut
benny     5712  0.0  0.2   5372  2140 ?        S    02:57   0:00 /usr/lib/gvfs/g
benny     5827  0.6  1.3  23316 10124 ?        S    02:58   0:02 /usr/lib/gnome-
benny     5830  0.0  0.3  13836  2604 ?        S    02:58   0:00 /usr/lib/gvfs/g
benny     5841  0.8  1.9  44356 14692 ?        Sl   02:58   0:03 /usr/lib/gnome-
benny     5844  0.6  1.7  26044 13108 ?        S    02:58   0:02 /usr/lib/fast-u
benny     5861 39.8  7.4 150528 56668 ?        Sl   02:58   2:24 /usr/lib/firefo
benny     5943  5.2  2.7  75164 20912 ?        Sl   03:00   0:12 gnome-terminal
benny     5952  0.0  0.1   2912   860 ?        S    03:00   0:00 gnome-pty-helpe
benny     5953  0.8  0.3   5592  3004 pts/0    Ss   03:00   0:01 bash
benny     5984  2.2  1.7  23444 12960 ?        S    03:02   0:03 /usr/lib/notifi
benny     6025  0.0  0.1   2644  1004 pts/0    R+   03:04   0:00 ps aux


i think i might have ****** up at the time when you told me to select intel driver. i did click intel. but it said intel i810 or something like that.   their was nothing that was JUST "intel" 
it might be because im tired but it does seem a bit faster.  though i think the resolution is a bit lower than it should. but if my videos work i wont matter anymore to me. i just want my videos to work and to be able to check my mail quickly.  and messenger...  just basice stuff...   ill check a video in a sec and tell you how it went.

---

### Post by bennyturok on 2008-08-25
well... thanks for helping me out.  if anything ill check in tommorrow and maybe try whatever you suggest if anything to try and make it faster.   video still chopped up.  opening new tabs in ff is still a pain in the *** (slow) and i cant stand it.  i bet ubuntu works better at my computer back home.  or if i buy a new computer ill definetly try ubuntu on it.  i really want it to work smoothly. but it just dosent.  if anything i learned somethign from this and it might help other people out with their problems. unless i manage to work it out if you leave anything for tommorrow sorry for taking your time. 

maybe its because im tired and perhaps a bit hungry but i reached my limits of patience.

---

### Post by forger on 2008-08-26
Had to step out too :) I think the problem is with the driver
Ok, let's replace your xorg.conf - do:
```
sudo wget http://pastebin.ca/raw/1185084 -O/etc/X11/xorg.conf
sudo /etc/init.d/gdm restart
```
and then log in again, and give me the output of these commands:
```
sudo lshw -C display
cat /var/log/Xorg.0.log | grep -i "intel\|i810"
```

One more thing, check out your Xorg log, see if there's anything else there that could be useful:
```
gedit /var/log/Xorg.0.log
```

---

