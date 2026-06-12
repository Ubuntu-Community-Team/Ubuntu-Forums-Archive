---
title: "Acer Aspire 5024WLMi and Ubuntu 5.04"
date: 2005-07-06
forum: Hardware &amp; Laptops
---

### Post by daenney on 2005-07-06
Oke

I totally changed the beginning post...
For ppl on this forum who have the same laptop or other Aspire laptops from the 5000/5020/3000/3020 series here's a few things to get Ubuntu working.

1) Disable Legacy USB Support in BIOS (don't worry, this doesn't disable USB under Windows) to make the keyboard working during the install and onwards.
1*) Just to add some apps to ur system and update it a bit from the default configuration check: [http://ubuntuforums.org/showthread.php?t=23368](http://ubuntuforums.org/showthread.php?t=23368)
and check: [http://ubuntuforums.org/showthread.php?t=30147](http://ubuntuforums.org/showthread.php?t=30147)

2) The ATi X700 graphics card: [http://ubuntuforums.org/showthread.php?t=24557](http://ubuntuforums.org/showthread.php?t=24557)
3) Wlan: [http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)
and WPA: [http://ubuntuforums.org/showthread.php?t=31418](http://ubuntuforums.org/showthread.php?t=31418)

4) USB audio devices: [http://ubuntuforums.org/showthread.php?t=30891](http://ubuntuforums.org/showthread.php?t=30891)

5) index of how-to's: [http://ubuntuforums.org/showthread.php?t=31094](http://ubuntuforums.org/showthread.php?t=31094)

---

### Post by t3r0 on 2005-07-06
[QUOTE=daenney]Hey guys,

Finally have my laptop in, windows working just fine so I thought I'd opt to install Ubuntu on it, duh...
Well, not so duh to be honest.
I have both the x84 and the amd64 versions of Ubuntu 5.04 on CD so I decided to go immediatly for the amd64. I put in the cd, reboot the laptop and enter the install and there it immediately goes wrong... **the keyboartd doesn't work**.
Thats right, ur ead it well, the keyboard does not do anything and without the arrows, enter, back and escape keys I can't really install Ubuntu, can I?!

So I ejected the cd-rom and decided to go for the x86 version with good hope that that one will work just fine. Boy oh boy was I wrong....
The exact same thing happens, the laptops keyboard doesn't react during the install so there again I can't proceed with the install!!

So my question is, anybody a clue what is causing this and how to fix it?[/QUOTE]


Hi,

I've 5021WLMI and had the same problem.... solution is to press the "prtSc" key  \\:D/  ( same thing every time you boot )

Few more tips:
if your mouse doesnt work just do
```

$ rmmod psmouse
$ modprobe psmouse

``` 

and I had lot of problems with the 5.04 default kernel (2.6.8??), ( REALLY slow HD etc.. ) but the latest kernel 2.6.11-1 fixes most of the HD problems...

so far only thing that doesnt work in my case is the wireless lan... (most likely because of the kill switch)


Hope this helps...

- tero

---

### Post by gorrth on 2005-07-07
hey i have the same laptop.
for the keyboard problem just DISABLE usb legacy support in bios and it will work fine.

for the hdproblem you have to install the latest stable kernel because in uhhm i guess 2.6.10-5 the atixpi is supported but doesn't work, so you can't enable dma.

does anyone know how to get the wlan work ?
its an acer laptop where you have to enable wlan on the laptop itself. but it doesnt work.

---

### Post by daenney on 2005-07-08
[QUOTE=gorrth]hey i have the same laptop.
for the keyboard problem just DISABLE usb legacy support in bios and it will work fine.

for the hdproblem you have to install the latest stable kernel because in uhhm i guess 2.6.10-5 the atixpi is supported but doesn't work, so you can't enable dma.

does anyone know how to get the wlan work ?
its an acer laptop where you have to enable wlan on the laptop itself. but it doesnt work.[/QUOTE]
 Well i remember there was a thing u could download comparable to the Acer launchmanager but don't remember how that is called

---

### Post by gorrth on 2005-07-10
acerhk, i tried it.
so the 4 buttons right of the powerbutton work. but wlan und bluetooth don't.

---

### Post by GuyveR800 on 2005-07-12
I'm running Hoary 64 bit now. Some notes:

- I got CPU frequency scaling working by putting **powernow-k8** in /etc/modules.
- As said, kernel 2.6.11-1 from Universe fixes the DMA on the harddisk.
- I also use **noapic nolapic noapictimer** flags for the kernel, which fixes the too fast clock and also seems to improve touchpad behaviour.

Remaining problems:
- battery status report doesn't work. (might try sbs-linux) (actually I remember it working in earlier install attempts, I wonder what made it stop  :? )
- WLAN doesn't work yet. Installed recent 64 bit WLAN drivers downloaded from the Acer site with Ndiswrapper 1.2. See for installing the latest ndiswrapper for 64 bit from source: [http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)
But acerhk doesn't run on 64 bit (yet, I hope :? ), so that's where I'm stuck.
- 5-in-1 cardreader doesn't seem to be functioning... Any clues will be appreciated.

---

### Post by sarahtf on 2005-07-13
I've got an Aspire 3000. The wireless problem is that the wifi card is a Broadcom, but not the 4400 series supported by the kernel. You need to get the windows driver downloaded from Acer and install ndiswrapper. Very good howto on this in the wiki section.

Does anybody else have a "display weirdness event" such as vertical flashing lines on boot? I have to hit the power button a time or two before the display comes up right. Then I get colored lines while xorg is doing its init thing, but then gnome comes up just fine.    Didn't happen with windows, but I got rid of that quick !

Hope this helps somebody - I fought the wifi thing for days!

---

### Post by GuyveR800 on 2005-07-13
[QUOTE=sarahtf]The wireless problem is that the wifi card is a Broadcom, but not the 4400 series supported by the kernel. You need to get the windows driver downloaded from Acer and install ndiswrapper.[/QUOTE]
This is not the only problem, the other is to get the wifi card enabled, because it is locked and the on/off button-led (on the front) isn't recognised by Ubuntu. (just like any of the other special Acer buttons)

> Does anybody else have a "display weirdness event" such as vertical flashing lines on boot?No, I did have weirdness on shutdown once though, when Ubuntu switches to text-mode. Not like you describe, but lots of flashy/flowy 'your LCD might blow up at any second' type weirdness. This also happened once when I closed the lid halfway and it started switching on/off really quickly.

---

### Post by sarahtf on 2005-07-14
[QUOTE=GuyveR800]This is not the only problem, the other is to get the wifi card enabled, because it is locked and the on/off button-led (on the front) isn't recognised by Ubuntu. (just like any of the other special Acer buttons)

No, I did have weirdness on shutdown once though, when Ubuntu switches to text-mode. Not like you describe, but lots of flashy/flowy 'your LCD might blow up at any second' type weirdness. This also happened once when I closed the lid halfway and it started switching on/off really quickly.[/QUOTE]
 Oh boy. I didn't have the button-lock problem initially, but I do now! After reading your post I messed around with what I had thought was just a LED. My wifi is now dead in the water.

How did you get out of this?

---

### Post by GuyveR800 on 2005-07-14
[QUOTE=sarahtf]Oh boy. I didn't have the button-lock problem initially, but I do now! After reading your post I messed around with what I had thought was just a LED. My wifi is now dead in the water.

How did you get out of this?[/QUOTE]
If it ain't broke.....  ;-) 
Seriously, I haven't gotten out of it yet. It hadn't worked for me even before I knew it was a button.

Try this: [http://www.informatik.hu-berlin.de/~tauber/acerhk/](http://www.informatik.hu-berlin.de/~tauber/acerhk/) or [http://www.roessner-net.com/wlan_button/](http://www.roessner-net.com/wlan_button/)

---

### Post by Kuolio on 2005-07-17
Hullo!

Another Acer 5021 Owner reporting o/. I'm using 64bit flavored version of ubuntu, and i'm having massive problems in getting mobility radeon x700 to work. This might be due to the fact, that I have never before had to care much about configuring my videocard (former nVidia user). If there is someone of you guys using 64bit and have x700 drivers installed and working like a charm, I would realy apreciate if you would have time to make simplified installation directions like "step1. step2. etc".. you can leave details out of it, i would just need some advice on where to start and wich steps to take on the "Great Hacking Of The X700" adventure ;D

---

### Post by GuyveR800 on 2005-07-17
I just installed xorg-driver-fglrx with synaptic... No problems whatsoever.

---

### Post by bdaw on 2005-09-12
Hi...

Anyone successfully resolved battery status / hibernating (acpi) problems on this acer model?

---

### Post by bdaw on 2005-09-23
[QUOTE=bdaw]Hi...

Anyone successfully resolved battery status / hibernating (acpi) problems on this acer model?[/QUOTE]

Ok. dist-upgrade with breezy yeasterday and with kernel 2.6.12-9-amd64-k8 battery status works fine!
Hibernation still hangs....

---

### Post by Nostrau on 2005-09-27
Hey,

I've tried to install Ubuntu but I've got problems with the ATI card. I have the Acer 5024WLMI laptop, bought in Sweden if it makes any difference. I'm totally new to linux and I have no idea what to do now. I would really appreciate your help. I think I've got a linux curse or something. This is about the 5-6 time I try a linux distro and everytime something go wrong. At least this time I might not be alone ;) 

I've followed the ATI how-to linked to in this topic, but it still doesn't work. Thankfully I did make a backup of xorg.conf or I would have to reinstall for the 5th time I think. I've updated the OS and before I did I could use 1280x800, but now it is set on 1280x1024 and if I change I get several graphics bugs. 
When I rebooted the computer with the updated xorg.conf file GNOME didn't start. I got an error message that X is not setup correctly. I looked in the log file and the only thing I can see is wrong with my untrained eye, is this: "Fatal server error: No screens found". 

Apart from that the whole OS is running incredibly slow. It takes about 2.5 minutes from pressing the power button to the desktop screen. Since we have the same laptop and hardware, is this normal?

Here's my updated xorg.conf file after the how-to thread: 

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	 # Load "extmod" but omit DGA extension
  # (the DGA extension is broken in the fglrx driver)
  SubSection "extmod"
    Option "omit xfree86-dga"
  EndSubSection
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
	Driver		"fglrx"
# If X refuses to use the screen resolution you asked for,
# uncomment this; see "Bugs and Workarounds" for details.
  Option "NoDDC"
# === Video Overlay for the Xv extension ===
  Option "VideoOverlay" "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
  Option "OpenGLOverlay" "off"
# === Use internal AGP GART support? ===
# If OpenGL acceleration doesn't work, try using "yes" here
# and disable the kernel agpgart driver.
  Option "UseInternalAGPGART" "no"
	BusID		"PCI:1:0:0"

EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x854" "1280x800" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x854" "1280x800" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x854" "1280x800" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x854" "1280x800" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x854" "1280x800" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x854" "1280x800" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


---

### Post by bdaw on 2005-09-27
[QUOTE=Nostrau]Hey,

I've tried to install Ubuntu but I've got problems with the ATI card.[...]
Apart from that the whole OS is running incredibly slow. It takes about 2.5 minutes from pressing the power button to the desktop screen. Since we have the same laptop and hardware, is this normal?

Here's my updated xorg.conf file after the how-to thread:[/QUOTE]

Hi. I haven't played with installing proper ATI drivers yet but all works fine for me. (except wifi which I haven't tried yet too but according to forums should be ok)

First of all. You didn't mentioned this but you are using hoary right? It's not good as there are some problems with UDMA with kernel 2.6.10 - that's why it's so slow. Update to kernel 2.6.11 from Universe - it'll be ok then with speed..

Second thing that is wrong is that you probably have system clock running to fast. Use 
"no_timer_check" and "noapic" options for kernel in /boot/grub/menu.lst

You can switch to breeze -it's still unstable but very close to relase so should be ok.

search ubuntu forums and you will find more solutions. I don't know how well you know linux so if you have more simple problems just ask. I'm not a linux master but I was able to make my acer working fine so maybe I could help more.

Here is my "working" xorg.conf (but remember that I'm using breezy):

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"pl"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection



```

---

### Post by Nostrau on 2005-09-28
I updated to the 2.6.11 kernel and yeah you're right. It is a remarkable speed boost, for awhile. Cause now something isn't working. When I try booting with the .11 kernel the computer freezes before the desktop is fully booted. It began after I changed the menu.lst file, but still continues even when I've deleted the changes in menu.lst. Do you know what's wrong?

Edit: I forgot one thing worth knowing. I can still use the old .10 kernel so something is definately wrong with .11

And about breezer. How do I upgrade to that? I can't find it in the package manager. 

Thank you for the help :)

---

### Post by bdaw on 2005-09-28
Breazy is next distro version - it should be relased in october. It's still in preview version so it might be unstable (you're on your own risk upgrading...). But according to my expierience and many others on forums it's very stable right now and works nearly perfect.

To upgrade to breezy just
-edit /etc/apt/sources.list and replace 'hoary' with 'breezy'
sudo apt-get update
sudo apt-get dist-upgrade

The last will upgrade your whole system - it'll take a longer while and... will upgrade all packages and configuration so be carefull ;)

With latest kernel from breezy (2.6.12-9) you should have battery status working (don't work with 2.6.11). For working hibernation try 'noapic' in kernel params.

About grub. You can write 'noapic no_timer_check' to the end of
'#kotp' line in menu.lst - kernel update will use this options when updating the file.
If you're updating menu.lst manually it usefull to reload grub sometimes ;)
#sudo grub-install /dev/hda   
(for my acer 5024 works fine)

Hope this will help and you have your system still working..... ;)

---

### Post by bdaw on 2005-09-28
For enabling fglrx driver follow last posts in thread:
[http://ubuntuforums.org/showthread.php?p=375072#post375072](http://ubuntuforums.org/showthread.php?p=375072#post375072)

Works for me!

---

### Post by Nostrau on 2005-09-28
Great link. Thank you for providing that :) 

I have one question though. Did you get the same things as Kuolio for installing fglrx, except fglrx-config? I have in mind this line he wrote: "I have installed kernel-headers, kernel-restricted-modules, xorg-driver-fglrx and then ran fglrxconfig."

> Hope this will help and you have your system still working....

Yeah now it works great, though I haven't touched on the ati card thing yet. I did get some problems when I tried to update from hoary, but after a clean install it works wonders. :)

---

### Post by bdaw on 2005-09-28
[QUOTE=Nostrau] I have in mind this line he wrote: "I have installed kernel-headers, kernel-restricted-modules, xorg-driver-fglrx and then ran fglrxconfig."
[/QUOTE]

Yeah. You have to get this packages - especially xorg-driver-fglrx if you want to use it ;)

I haven't run fglrxconfig but just took related sections (modules, files, device, screen) from his attached config and copy/paste into mine xorg.conf. Try it. if you have problems I can attach you mine to - but it shouldn't be very complicated.

---

### Post by bdaw on 2005-09-30
I try to enable my wifi on 5024WLMi
ndiswrapper installed and wlan0 present - that is ok
But as I found it on the web wifi is not powered on 
```
bdaw@elk:~$ iwlist wlan0 scan
wlan0     No scan results
bdaw@elk:~$ iwlist wlan0 power
wlan0     Current mode:off
bdaw@elk:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:0E:9B:D3:EE:C3
inet6 addr: fe80::20e:9bff:fed3:eec3/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
Memory:c0204000-c0205fff
```
and should be started using [http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html](http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html)
And I have problem with it. There is some stupid problem and module is loaded on second time and than it's not working properly:
```
bdaw@elk:~$ sudo modprobe acer_acpi
Password:
FATAL: Error inserting acer_acpi (/lib/modules/2.6.12-9-amd64-k8/extra/acer_acpi.ko): No such device
bdaw@elk:~$ sudo modprobe acer_acpi
bdaw@elk:~$ sudo modprobe ndiswrapper
bdaw@elk:~$ dmesg |tail
[  114.810067] [fglrx] max   Inv = 0
[  114.810069] [fglrx] total Inv = 0
[  114.810071] [fglrx] total TIM = 0
[  114.810072] [fglrx] total FB  = 0
[  114.810074] [fglrx] total PCIe = 16384
[  116.830279] eth0: no IPv6 routers present
[  117.189666] wlan0: no IPv6 routers present
[  158.095548] acer_acpi: Acer Laptop ACPI Extras version 0.2
[  158.095883] acer_acpi: Unable to register driver, aborting.
[  158.651367] acer_acpi: Acer Laptop ACPI Extras version 0.2
bdaw@elk:~$ sudo echo "enabled : 1" > /proc/acpi/acer/wireless
bash: /proc/acpi/acer/wireless: Permission denied

```
any ideas? someone had similar problems? somene has wifi working well without such things?
I have:
```
bdaw@elk:~$ uname -r
2.6.12-9-amd64-k8

```
and I installed proper kernel headers package before making acer_acpi - install was without errors.
thanks in advance.

---

### Post by GuyveR800 on 2005-10-01
[QUOTE=bdaw]
```

bdaw@elk:~$ sudo echo "enabled : 1" > /proc/acpi/acer/wireless
bash: /proc/acpi/acer/wireless: Permission denied

```
any ideas? someone had similar problems? somene has wifi working well without such things?[/QUOTE]
First I had problems compiling on 64 bit breezy (it seems to need gcc3.4 specifically), then I got the same permission denied as you. Using 'sudo su' first to change to the root user seemed to fix that. Perhaps fakeroot works too, but I'm too n00b to know ;)

<edit: removed part about ndiswrapper from the respositories not working, because it does ^^;>

Let us know if you get it working :cool:

---

### Post by bdaw on 2005-10-01
yeah... I'm writing this post using WPA-PSK connection :D Moreover I did nothing besides of plugout the ethernet cable and power on the computer :)
So... two HOWTOs mentioned in the first post of this topic are really great and work properly. As accer user I have to do as follow to have it working:
I placed some really dumb scripts in /etc/init.d and /etc/rcS.d:
```

bdaw@elk:~$ cat /etc/init.d/acer-acpi
#!/bin/sh
rmmod ndiswrapper
rmmod ndiswrapper
modprobe acer_acpi
modprobe acer_acpi
echo "enabled : 1" > /proc/acpi/acer/wireless
bdaw@elk:~$ ls -alF /etc/rcS.d/ |grep acer
lrwxrwxrwx    1 root root   21 2005-10-01 10:42 S38acerwifi -> /etc/init.d/acer-acpi*

```
for the seccond do:
ln -s /etc/init.d/acer-acpi /etc/rcS.d/S38acerwifi
to have this link.
Next I have all things configured as in those two HOWTO's
and as mentioned there I have such /etc/network/interfaces:
```

bdaw@elk:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
iface eth0 inet dhcp
auto eth0
auto wlan0
iface wlan0 inet dhcp
pre-up /usr/sbin/wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

```
So.... with all of above... I plugout ethernet cable, have my AP working with WEP-pk configured and.... power on... and I'm connected :D
Most important is to turn wifi adapter on with acer_acpi. The script is really dumb. modprobe is run twice as there is some error at the firs time. I remove ndiswrapper to do it cleanly. When interfaces will be made up (you can do it manually by ifconfig wlan0 up - or ifupdown will do it) the ndiswrapper module will be loaded automatically (look at dmesg).
Hope this will help, and let you save some time. Rest is in those two really great howto's.

---

### Post by GuyveR800 on 2005-10-02
Thanks bdaw, I have wireless working now using your scripts. Just WEP tho, as WPA seems to be stuck during the handshake phase.

Let's hope Ubuntu 6.04 will have the acer_acpi built-in or at least in universe :)

---

### Post by kitsos on 2005-10-16
Many many thanks to everybody that contributed to this thread!

I've managed to get everything working on my acer 5021 with Breezy Badger. Writing this msg through my wireless connection :D 

Great release guys! Keep on with the good work! This release convinced me that the time has come to make the final trasition to pure linux and get rid of the windows tyrany!

---

