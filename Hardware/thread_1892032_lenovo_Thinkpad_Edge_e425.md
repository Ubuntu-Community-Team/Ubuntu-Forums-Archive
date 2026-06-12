---
title: "lenovo Thinkpad Edge e425"
date: 2011-12-07
forum: Hardware
---

### Post by gcbzzzz on 2011-12-07
just a thread to dump information before I format to the hardware wikis

upgrades on this box:
- cpu
- HD display
- fingerprint reader

00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Complex
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9648
00:01.1 Audio device: ATI Technologies Inc Device 1714
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode]
00:12.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB Controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB Controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 13)
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:14.7 SD Host controller: Advanced Micro Devices [AMD] Hudson SD Flash Controller
00:15.0 PCI bridge: Advanced Micro Devices [AMD] Device 43a0
00:15.1 PCI bridge: Advanced Micro Devices [AMD] Device 43a1
00:15.2 PCI bridge: Advanced Micro Devices [AMD] Device 43a2
00:15.3 PCI bridge: Advanced Micro Devices [AMD] Device 43a3
00:16.0 USB Controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:16.2 USB Controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
04:00.0 System peripheral: Ricoh Co Ltd Device e823 (rev 04)
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

---

### Post by gcbzzzz on 2011-12-07
Booting from SD card. Impossible with the included reader. BIOS from 2011-09-27 can't boot from the included card reader via PCIe bus.

workaround: attach an external reader on a usb port. works fine.

---

### Post by gcbzzzz on 2011-12-07
Video card does not work with Live image.

on the boot menu, press tab and add "xforcevesa radeon.modeset=0" to boot in failsafe graphics mode. Also add "nosplash" for good measure. splash boot's good for nothing.

---

### Post by gcbzzzz on 2011-12-07
it came with partitions:
sda1 (boot?)
sda2 (windows 7)
sda3 (recovery)

using gparted you can reduce the size of sda2 and create sda4 in there. windows will continue to work without a problem.

but before actually installing grub, make a bootable CD with lenovo rescue software because after installing grub you will not be able to use the rescue partition. or so I read.

---

### Post by gcbzzzz on 2011-12-08
after installing the ati restricted drivers

```
sudo aticonfig --initial -f -v --adapter=all
```

this is because X will fail if configuration is missing from any device.

also, make sure your BIOS has both devices enabled, and in my case i left the "OS support detection" for the graphic device switching. don't know if that helps or hurt...

also, make sure you do not have nothing like radeon.modeset=0 or nomodeset on your grub kernel options.

---

### Post by gcbzzzz on 2011-12-08
fingerprint reader is UPEK, so it will not work with the pam module available today.

here's lsusb with nothing external attached to the box

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 5986:03b3 Acer, Inc 
Bus 004 Device 002: ID 147e:1002 Upek 

```

---

### Post by gcbzzzz on 2011-12-08
For the radeon graphics cards to work, i had to disable one bios setting about Auto detecting OS support for Switchable graphics

---

### Post by gcbzzzz on 2011-12-08
aticonfig generated this, i commented some sections trying to debug which was solved by changing the BIOS setting above and now i'm scare to put them back since it's working :)
will probably delve more into that when i need HDMI out...

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	#Screen         "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:0:1:0"
EndSection

#Section "Device"
#	Identifier  "aticonfig-Device[1]-0"
#	Driver      "fglrx"
#	BusID       "PCI:1:0:0"
#EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

#Section "Screen"
#	Identifier "aticonfig-Screen[1]-0"
#	Device     "aticonfig-Device[1]-0"
#	Monitor    "aticonfig-Monitor[1]-0"
#	DefaultDepth     24
#	SubSection "Display"
#		Viewport   0 0
#		Depth     24
#	EndSubSection
#EndSection

```

---

### Post by gcbzzzz on 2011-12-08
touchpad and clitmouse.

the clitmouse middle button works as:
- middle button, if clicked
- scroll toggle if hold. (hold middle button, not clitmouse is the scrollwheel, not mouse pointer)

i couldn't find setting for this behaviour, and i'm afraid it may be done in hardware... not sure yet.

touchpad has an awful multitouch sensibility. if you enable two finger scroll, your fingers have to be APART! never saw that on any other touchpad before. if your fingers are tuching (even if the contact area on the tip of them are apart) you get simple mouse movement. this is the same under the lenovo drivers in windows. but in linux it feels much more responsible for movement.

---

### Post by Antarctica32 on 2011-12-08
I was thinking about getting an edge when they first came out, but I figured they didn't seem as rugged. May I ask you how rugged it feels? I'm a HUGE fan of thinkpads and I would love to know. My granddad used to work for IBM back when they made the thinkpads. I have loved them ever since I found a T30 and put ubuntu on it. Do you think the new design of the edge is still thinkpad-ish? I have never actually seen an edge and would love to play with one. I'll probably find one someday at a store around here. thanks man.

---

### Post by gcbzzzz on 2011-12-09
> **Antarctica32 said:**
> I was thinking about getting an edge when they first came out, but I figured they didn't seem as rugged. May I ask you how rugged it feels? I'm a HUGE fan of thinkpads and I would love to know. My granddad used to work for IBM back when they made the thinkpads. I have loved them ever since I found a T30 and put ubuntu on it. Do you think the new design of the edge is still thinkpad-ish? I have never actually seen an edge and would love to play with one. I'll probably find one someday at a store around here. thanks man.

No. the edges are NOT thinkpads.

**the only thinkpads are the T series**. (i'd like to be wrong here)

the non-T are flimsy (my battery woobles a little in the slot) and all the nice details on the T (status leds under the screen, physical RF-kill switch, beveled arm-rest) are all gone

the edge have:
- no status led at all (event the charging led is on the SIDE. and there's no led to warn about low battery)
- RF-kill switch by fn-F9
- an edge on the arm rest that completely cuts your wrist bloodflow (worse thing so far. maybe that's why it's called edge)
- the most unresponsible touchpad (get's better on linux than on windows)
- finish on the plastic (entire body, keyboard, cover) shows my fingerprints more vividly then my phone screen! and it's not shiny, it's dull. i can't understand how this material can do that... but it does. to a point i will probably not even bother to configure my fingerprint reader because it would be a joke.
- does not boot via SD card reader

The things it have better: hdmi out. e-sata. monitor open/close without mechanical lock. ...those may be available now on the T series. AMD cpu with nice radon-mobile (this may be a two-edge sword in linux, as support is worse. and required a $100+ upgrade)

things that are personal:
- keyboard is BIG. keys feel a little wider than my T400 also 14". comparing now, the T400 has speakers on the side, this one on the bottom... so it uses the entire width for the keyboard... i rater small keyboards.
- touchpad is enourmous. again, i don't like :) but i guess i'm alone on this one. i use the ****-mouse exclusively and the touchpad only gets in the way.

I am seriously considering turning this one back. As i was really expecting something like the T400 i have at work. I mean, they are nice machines. But the turndown because of the high quality i was expecting, plus the linux compatibilities issues that do not happen on the T400 is giving me buyers remorse...

If you are still planning on buying, there's only two models that have the non-glare screen. do not overlook that.

Also, don't fall for the $100+ upgrade for HD lcd. I can tell that the direct viewing colors are WORSE. it's only ever a good choice if you are looking at weird angles at the screen. for regular usage, cheap non-HD screen has better image.

---

### Post by gcbzzzz on 2011-12-09
Update. i'm fed up with ubuntu. the unity retarded state is beyond this world.

and installing the gnome-fall-back-something package leaves everything broken! no compiz plugin will work. from window-move to Scale. nothing will work. you have to add new repositories and roll back compiz versions... you gotta be kidding me. 

I'm back to debian for good.

unity is still a toy WM. just like the [7000 i've seen appear an go]("http://www.gilesorr.com/wm/table.html") over the years. it's in no way ready to be force fed to a bunch of users. You can't even configure shortcuts keys for $deity-sake! I'm all about alternatives and improving. but breaking gnome for THAT is retarded.

---

### Post by gcbzzzz on 2011-12-09
botting debian 6.0.3 net install does not require any workaround. graphical mode works, but i proceeded with text install.

after install, must add "nomodeset" for grub entry.

after radeon driver install, add "nomodeset xforcevesa text" and boot into text mode to run aticonfig and have a proper xorg.conf


catalyst 11.11 does not work with this board ... back to start

---

### Post by gcbzzzz on 2011-12-10
great... debian-stable has glx with direct rendering out of the box... but no luck getting wifi working.

---

### Post by gcbzzzz on 2011-12-10
tried both mint linux ubuntu and debian editions.

neither would even boot in vesamode. so away with them.

i'm back with debian-test using kernel 3.1

---

### Post by Jesse2004 on 2012-01-27
> **gcbzzzz said:**
> great... debian-stable has glx with direct rendering out of the box... but no luck getting wifi working.

wifi works in debian-stable, with the kernel and firmware from squeeze-backports

---

### Post by gcbzzzz on 2012-01-27
> **Jesse2004 said:**
> wifi works in debian-stable, with the kernel and firmware from squeeze-backports

completely forgot about backports! will give it a try. thanks!

---

### Post by oxide23 on 2012-02-29
After trying ubuntu 11.10, 12.04, fedora core 16 all of which have problems 

12.04 : unstable unity interface, system runs in live mode, but panels "disappear" rendering system unusable. 

11:10: no video, installs, but then no video
11:10 alternate install: no video
fedora core 16 : no video in live mode

Anyway, Debian stable (6.0.3, squeeze) kind of seems to work...except for the wireless....

lspci | grep WiFi

06:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
 
I enabled the backports in /etc/apt/sources.list

deb [http://backports.debian.org/debian-backports](http://backports.debian.org/debian-backports) squeeze-backports main non-free

Then I did an apt-get update && apt-get install firmware-realtek

this seemed to install OK...

dpkg -L firmware-realtek (lots of stuff)
but nothing looks like a module...what, if anything does one do with these files?

lib/firmware/rtlwifi/rtl8192cfw.bin
/lib/firmware/rtlwifi/rtl8192defw.bin
/lib/firmware/rtlwifi/rtl8192cufw.bin
/lib/firmware/rtlwifi/rtl8192sefw.bin
/lib/firmware/rtlwifi/rtl8712u.bin

Now that it's all installed does anyone know how to make it work? I think there is still something missing. NetworkManager doesn't "see" it, and there are no entries in /etc/network/interfaces. Seems there should be a module to install or load or something in /etc/modprobe.d  

ifup wlan0 

Ignoring unknown interface wlan0=wlan0

no module gets loaded for it, is it manual and if so, what can I modprobe -a to get it loaded?  thank you

---

### Post by wnelson on 2012-02-29
This is for the RTL8188. There are others there also.

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

Walt

---

