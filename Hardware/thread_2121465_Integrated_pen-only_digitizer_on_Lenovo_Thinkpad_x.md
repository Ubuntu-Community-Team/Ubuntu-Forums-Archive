---
title: "Integrated pen-only digitizer on Lenovo Thinkpad x61t."
date: 2013-03-02
forum: Hardware
---

### Post by bogamol on 2013-03-02
Problem getting the integrated pen-only digitizer to work on my Lenovo Thinkpad x61t. Using Debian 6 Squeeze.

Initially, I thought that this issue was related to [this](XXXXX) thread [(here's where I started)](XXXXX), but according to Favux, there is no problem with the serial wacom drivers with respect to my particular hardware...??All integrated digitizers on serial wacom laptops, or just mine??...Per Favux, ISDV4 doesn't need a kernel module.

Here is a rundown of the conversation...

$ xinput list shows:

.&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
.&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
.&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=10	[slave  pointer  (2)]
.&#9116;   &#8627; Macintosh mouse button emulation        	id=12	[slave  pointer  (2)]
.&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
.    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
.    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
.    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
.    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
.    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
.    &#8627; ThinkPad Extra Buttons                  	id=11	[slave  keyboard (3)]
.    &#8627; ACPI Virtual Keyboard Device            	id=13	[slave  keyboard (3)]
    
$ uname -a shows:
Linux heartOfGold-debian 2.6.32-5-amd64 #1 SMP Mon Feb 25 00:26:11 UTC 2013 x86_64 GNU/Linux

$ lspci shows:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
05:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
05:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
05:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)

I was alarmed that I didn't see anything listed here that looks like a serial anything, let alone a digitizer.

$ lshal | grep WAC shows:

.udi = '/org/freedesktop/Hal/devices/pnp_WACf004'
.  info.udi = '/org/freedesktop/Hal/devices/pnp_WACf004'  (string)
.  pnp.id = 'WACf004'  (string)
.udi = '/org/freedesktop/Hal/devices/pnp_WACf004_serial_platform_0'
.  info.parent = '/org/freedesktop/Hal/devices/pnp_WACf004'  (string)
.  info.udi = '/org/freedesktop/Hal/devices/pnp_WACf004_serial_platform_0'  (string)
.  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_WACf004'  (string)

lshal at least indicated to me that the computer is recognizing that the digitizer exists, so this is heartening. Favux said that the issue is probably a X drivers configuration issue.

Favux asked my Xorg version number. 
If Xorg =< 1.7 then HAL ***
If Xorg >= 1.8 then xorg.conf.d

$ Xorg -version

.X.Org X Server 1.7.7
.Release Date: 2010-05-04
.X Protocol Version 11, Revision 0
.Build Operating System: Linux 3.0.0-1-amd64 x86_64 Debian
.Current Operating System: Linux heartOfGold-debian 2.6.32-5-amd64 #1 SMP Mon Feb 25 00:26:11 UTC 2013 x86_64
.Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-5-amd64 root=UUID=63284c28-92c7-45ac-9002-5691a017d224 ro quiet
.Build Date: 29 October 2011  06:58:14PM
.xorg-server 2:1.7.7-14 (Julien Cristau <jcristau@debian.org>) 
.Current version of pixman: 0.16.4

Favux mentioned that we would probably be dealing with problems in fdi files. Below is the contents of what I think is the most relevant fdi file in /usr/share/hal/fdi/policy/

nano /usr/share/hal/fdi/policy/10osvendor/10-tabletPCs.fdi
.<?xml version="1.0" encoding="UTF-8"?>
.
.<deviceinfo version="0.2">
.
.  <device>
.    <!-- to get the device up we need to set the baud_rate correct -->
.    <match key="pnp.id" contains="FPI2004">
.      <merge key="input.device.set" type="string">/dev/ttyS0</merge>
.      <merge key="pnp.serial.baud_base" type="int">38400</merge>
.    </match>
.
.    <!-- add addon if need special ttySx settings -->
.    <match key="input.device.set" exists="true">
.      <append key="info.callouts.add" type="strlist">hal-system-setserial</append>	
.    </match>
.
.    <!-- handle USB tablets -->
.    <match key="usb_device.vendor_id" int="0x56a">
.      <!-- WACOM Tablets -->
.      <match key="usb_device.product_id" int_outof="0x90;0x93;0x9a">
.	<!-- TabletPCs with USB Wacom Tablets -->
.        <match key="/org/freedesktop/Hal/devices/computer:system.formfactor" compare_ne="laptop">
.	  <!-- set the correct formfactor if not already laptop -->
.	  <merge key="/org/freedesktop/Hal/devices/computer:system.formfactor" type="string">laptop</merge>
.	</match>
.	<!-- set the correct subtype -->
.	<merge key="/org/freedesktop/Hal/devices/computer:system.formfactor.subtype" type="string">tabletpc</merge>
.     </match>
.    </match>
.
.  </device>
.
.</deviceinfo>

$ ls [...]/10osvendor/
10-cpufreq.fdi
10-dockstation.fdi
10-imac-backlight.fdi
10-input-policy.fdi
10-laptop-panel-mgmt-policy.fdi
10-leds.fdi
10-power-mgmt-policy.fdi
10-rfkill-switch.fdi
10-tabletPCs.fdi
10-usbcsr-mice.fdi
15-storage-luks.fdi
20-storage-methods.fdi
25-ntfs-3g-policy.fdi
30-wol.fdi
debian-storage-policy-ignore-fixed-crypto-drives.fdi


$ ls [...]/20thirdparty/
There is nothing in there.

---

### Post by bogamol on 2013-03-02
For whatever reason, the forum wont let me edit my post. The thread I thought was relevant to my problem is [here](http://ubuntuforums.org/showthread.php?t=1780154). 

[Here](http://ubuntuforums.org/showthread.php?t=1780154&page=51) is where I started posting.

---

### Post by bogamol on 2013-03-02
For whatever reason, the forum wont let me edit my post. The thread I thought was relevant to my problem is [here](http://ubuntuforums.org/showthread.php?t=1780154). 

[Here](http://ubuntuforums.org/showthread.php?t=1780154&page=51) is where I started posting.

---

### Post by Favux on 2013-03-02
The serial Plug and Play ID for the X61t's Wacom digitizer is WACf004.  That is a keyword that can be used for the match.

The serial digitizer should be showing up in **xinput list** as something like "Serial Wacom Tablet stylus".  And for the eraser instead of stylus then eraser would be appended.  Don't know if you have touch.  That should happen out of the box as long as the xorg-xserver-input-wacom package is installed.

Sorry, my mistake.  X Server is 1.7 = HAL for Distros except Debian/Ubuntu.  With Lucid 10.04 Ubuntu calls it X Server 1.7 but it isn't.  It is hybrid of 1.7 and 1.8.  But they got the hybrid from Debian.  Basically they were so eager to dump HAL they grabbed the xorg.conf.d stuff from 1.8 and grafted it on 1.7.  I'm just not sure which Debian release has the hybrid, if it still has it, or if they ever actually used it.  But since you have same 2.6.32 kernel as Lucid I'm thinking its the same.

Does look like HAL might still be functional, which it wouldn't be in Lucid, but lets see if xorg.conf.d is being  used.  The standard locations for the .conf files are:
Distro - /usr/share/X11/xorg.conf.d
User custom - /etc/X11/xorg.conf.d

However the hybrid X Server has only one location and it is not standard:  /usr/lib/X11/xorg.conf.d/10-wacom.conf  So look for a wacom.conf and if you find it post it.  If you compiled xf86-input-wacom it would not add the wacom.conf because of the non-standard location.  And by the way if you tried to add the custom directory /etc/X11/xorg.conf.d you'd break X.

Is not being able to edit until you have a certain number of posts one of their anti-spam measures?

---

### Post by bogamol on 2013-03-02
$ ls /usr/share/X11/ 
reveals xorg.conf.d.

$ls /etc/X11/
reveals some other stuff but not xorg.conf.d

$ ls /usr/lib/X11/
reveals some other stuff but not xorg.conf.d

I do not have touch. It is strictly the digitizer version. So no fingerprints on my screen, just giant paisley palm prints. :P

I hope that no post editing is not an anti-spam method because what was intended to be 2 posts became 5. Anti-spam failure :KS

---

### Post by bogamol on 2013-03-02
For clarity
# apt-get install xserver-xorg-input-wacom
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-input-wacom is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Favux on 2013-03-02
Hmm, 1.7 but with xorg.conf.d in the correct location.  But I'm betting it's the hybrid given xorg.conf.d is present.

What release of Debian is this?
```
cat /etc/issue
```

Did you find a wacom.conf in /usr/share/X11/xorg.conf.d?  If so what number does it have for a prefix and what are the contents?

What version of xf86-input-wacom?
```
xsetwacom -V
```

---

### Post by bogamol on 2013-03-02
$ xsetwacom -V
0.10.5


$ cat /etc/issue
Debian GNU/Linux 6.0 \n \l

---

### Post by Favux on 2013-03-02
Wow, 0.10.5.  That's like the first xf86-input-wacom after the fork from linuxwacom.  So updating your xf86-input-wacom should definitely be a consideration.

But the main thing is the wacom.conf in xorg.conf.d.  Is it there and what's in it?

---

### Post by bogamol on 2013-03-02
Re: 10.5 Apparently it is the bog standard for Debian Squeeze. It looks like Wheezy will be up to 15.XX. I'll look into updating that. I didn't even think of old drivers, I started out using Fedora Core and then Gentoo(burned out a MB with all the compiling once) and Arch, so bleeding edge everywhere. This never even occurred to me. 

Oh yeah, I was supposed to list that wasn't I.

$ ls
10-evdev.conf  20-wacom.conf  50-synaptics.conf

$ nano 20-wacom.conf
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection



Funny, I didn't think this was an N-Trig setup...

---

### Post by Favux on 2013-03-02
Currently N-trig, Waltop, and Hanwang use xf86-input-wacom code for their stylus.  The new KYE tablets can too.

Try adding below the current ISDV4 snippet (above the N-Trig one) this snippet.
```
Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
        Option "ForceDevice" "ISDV4"
EndSection
```
The **Option "ForceDevice" "ISDV4"** goes away quickly as Peter gets to work cleaning up the xf86-input-wacom code after the fork and makes all his changes to the wcmISDV4.c code.

---

### Post by bogamol on 2013-03-03
No effect if I try to draw on the screen. I tested the device in Win7 and it works there. I also checked the boot log for errors related to the input devices but nothing listed.

Here's the xinput list after your modification to the conf file.

$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=11	[slave  keyboard (3)]
    &#8627; ACPI Virtual Keyboard Device            	id=13	[slave  keyboard (3)]

Here's how I changed the wacom.conf

$ nano /usr/share/X11/xorg.conf.d/20-wacom.conf
Section "InputClass"
        Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#       MatchProduct "Wacom|WALTOP|WACOM"
        MatchProduct "Wacom|WACOM"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class"
        MatchProduct "Serial Wacom Tablet"
        Driver "wacom"
        Option "ForceDevice" "ISDV4"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
        Option "ForceDevice" "ISDV4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
        Identifier "Wacom N-Trig class"
        MatchProduct "HID 1b96:0001"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection

---

### Post by Favux on 2013-03-04
Good.  Since it works in Windows we know it isn't the hardware and that's important to know.

So the digitizer isn't initializing.  Why?  You may be able to obtain some information from Xorg.0.log in /var/log if the wacom.conf is making a match to the Wacom X driver.  Should be some errors.

Let's check with xxd if we are getting anything over the serial port and also find out which serial port it is on.  To determine available serial ports:
```
ls /dev/ttyS*
```
xxd (hidrawX hexdump) will exit for devices not listed, otherwise CTRL and C to quit.  Run through each device listed by "ls /dev/ttyS*" eg. ttyS0, ttyS1, etc.  Bring the pen to the screen and move it around.  You know you have the right ttyS* when you see a reaction with an output of characters.  That's the ttyS* you want to specify in say your xorg.conf.
```
xxd /dev/ttyS0
```
Sometimes to initialize it we have had to configure the digitizer in the xorg.conf.  Don't know why.  It is also possible something in your current xorg.conf, if present, is over riding the wacom.conf file.  Anything on Wacom in /etc/X11/xorg.conf?

I don't know if Squeeze comes with setserial installed and if that version autoconfigures the port or whether you would still have to do it manually.  As I recall in Lucid it was pre-installed and autoconfigured.  Since Squeeze appears to be the Debian equivalent setserial likely isn't the problem.

With some newer releases the Distros, in what I consider a misguided premature move, tried to switch to the ISDV4 serio kernel driver.  Since a script they had didn't invoke inputattach like intended it had the effect of disabling a bunch of tablet PCs that would have worked out of the box if they hadn't messed with things.  Doubt this applies to Squeeze.  See:
[http://forums.linuxmint.com/viewtopic.php?f=42&t=96247&p=550402](http://forums.linuxmint.com/viewtopic.php?f=42&t=96247&p=550402)
[http://forums.linuxmint.com/viewtopic.php?f=59&t=96183&p=550382](http://forums.linuxmint.com/viewtopic.php?f=59&t=96183&p=550382)

A more likely possibility is you need a udev rule for serial ISDV4 devices.  Check in /lib/udev/rules.d/ for 69-xserver-xorg-input-wacom.rules or the Debian equivalent.  Although mainly for usb tablets there should be a few lines for serial devices either at the beginning or end.  Or possible the serial stuff is in a separate rule file in Debian.  This wiki page will give you and idea of what to look for:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Fixed_device_files_with_udev](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Fixed_device_files_with_udev)  I can give you what Ubuntu uses if you needed, since they likely got it from Debian.  They never responded to my Launchpad bug on the upated serial rules you'll see on the wiki page.

---

### Post by bogamol on 2013-03-04
#xxd /dev/ttyS0 provided hexidecimal output for both the pen and eraser sides of my stylus. Nothing for any of the others.

There is no file /etc/X11/xorg.conf

There is no file /lib/udev/rules.d/40-inputattach.rules
inputattach is a bad command or file name.

I'm pretty sure, that if I create one with Xorg -configure and copy it into /etc/X11/xorg.conf it will break X. Since last time I did that...it broke X and I had to batter my way to the CLI and delete xorg.conf :oops:

Here is the udev Rules file in lib/udev/rules.d
I bolded what I think is the salient point...

# udev rules for wacom tablets.
# These rules were compiled for the Debian GNU/Linux distribution,
# but others may, and indeed are encouraged to, use them also.
#
# Should you do so, PLEASE CO-ORDINATE ANY CHANGES OR ADDITIONS
# of new devices with Ron <ron@debian.org> so that we can try
# to present users with a standard set of device nodes which
# they can rely on across the board.

# Catch the serial tablets and tell X that's what they are
[b]ACTION=="add|change", SUBSYSTEM=="pnp", ATTR{id}=="WACf*", 	\
	ENV{NAME}="Serial Wacom Tablet",			\
	ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1"

ACTION=="add|change", SUBSYSTEM=="pnp", ATTR{id}=="FUJ*",	\
	ENV{NAME}="Serial Wacom Tablet",			\
	ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1"


KERNEL!="event[0-9]*", GOTO="wacom_end" [/b]

# Port specific link for users of multiple tablets of the same type.
# The ID_PATH variable is set by the "path_id" script in an earlier rule file.
ATTRS{idVendor}=="056a", ENV{ID_PATH}=="?*", SYMLINK="input/by-path/$env{ID_PATH}-wacom"

# Multiple interface support for stylus and touch devices.
DRIVERS=="wacom", ATTRS{bInterfaceNumber}=="00", ENV{WACOM_TYPE}="stylus"
DRIVERS=="wacom", ATTRS{bInterfaceNumber}=="01", ENV{WACOM_TYPE}="touch"

# Type-named links for multiple tablets.  If you want to use multiple
# tablets of the _same_ type, you will probably need to use the links
# from /dev/input/by-path to identify which is plugged into what usb
# port.  For different tablet types though, just pick your links from
# the list below.
#
# We override SYMLINK for tabletpc devices because the by-path link
# is not required with such devices, there will only ever be one.
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0000", SYMLINK+="input/tablet-penpartner"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0003", SYMLINK+="input/tablet-cintiq_partner"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0010", SYMLINK+="input/tablet-graphire"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0011", SYMLINK+="input/tablet-graphire2-4x5"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0012", SYMLINK+="input/tablet-graphire2-5x7"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0013", SYMLINK+="input/tablet-graphire3"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0014", SYMLINK+="input/tablet-graphire3-6x8"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0015", SYMLINK+="input/tablet-graphire4-4x5"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0016", SYMLINK+="input/tablet-graphire4-6x8"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0017", SYMLINK+="input/tablet-bamboofun-4x5"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0018", SYMLINK+="input/tablet-bamboofun-6x8"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0019", SYMLINK+="input/tablet-bamboo1-medium"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0020", SYMLINK+="input/tablet-intuos-4x5"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0021", SYMLINK+="input/tablet-intuos-6x8"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0022", SYMLINK+="input/tablet-intuos-9x12"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0023", SYMLINK+="input/tablet-intuos-12x12"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0024", SYMLINK+="input/tablet-intuos-12x18"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0030", SYMLINK+="input/tablet-pl400"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0031", SYMLINK+="input/tablet-pl500"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0032", SYMLINK+="input/tablet-pl600"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0033", SYMLINK+="input/tablet-pl600sx"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0034", SYMLINK+="input/tablet-pl550"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0035", SYMLINK+="input/tablet-pl800"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0037", SYMLINK+="input/tablet-pl700"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0038", SYMLINK+="input/tablet-pl510"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0039", SYMLINK+="input/tablet-dtu710"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="003f", SYMLINK+="input/tablet-cintiq21ux"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0041", SYMLINK+="input/tablet-intuos2-4x5"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0042", SYMLINK+="input/tablet-intuos2-6x8"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0043", SYMLINK+="input/tablet-intuos2-9x12"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0044", SYMLINK+="input/tablet-intuos2-12x12"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0045", SYMLINK+="input/tablet-intuos2-12x18"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0047", SYMLINK+="input/tablet-intuos2-6x8a"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0060", SYMLINK+="input/tablet-volito"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0061", SYMLINK+="input/tablet-penstation2"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0062", SYMLINK+="input/tablet-volito2-4x5"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0063", SYMLINK+="input/tablet-volito2-2x3"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0064", SYMLINK+="input/tablet-penpartner2"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0065", SYMLINK+="input/tablet-bamboo"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0069", SYMLINK+="input/tablet-bamboo1"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0081", SYMLINK+="input/tablet-graphire_bt-6x8"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0090",  SYMLINK="input/tablet-tpc90"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0093",  SYMLINK="input/tablet-tpc93-$env{WACOM_TYPE}"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="009a",  SYMLINK="input/tablet-tpc9a-$env{WACOM_TYPE}"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="00b0", SYMLINK+="input/tablet-intuos3-4x5"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="00b1", SYMLINK+="input/tablet-intuos3-6x8"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="00b2", SYMLINK+="input/tablet-intuos3-9x12"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="00b3", SYMLINK+="input/tablet-intuos3-12x12"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="00b4", SYMLINK+="input/tablet-intuos3-12x19"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="00b5", SYMLINK+="input/tablet-intuos3-6x11"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="00b7", SYMLINK+="input/tablet-intuos3-4x6"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="00b8", SYMLINK+="input/tablet-intuos4-4x6"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="00b9", SYMLINK+="input/tablet-intuos4-6x9"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="00ba", SYMLINK+="input/tablet-intuos4-8x13"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="00bb", SYMLINK+="input/tablet-intuos4-12x19"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="00c0", SYMLINK+="input/tablet-dtf521"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="00c4", SYMLINK+="input/tablet-dtf720"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="00c5", SYMLINK+="input/tablet-cintiq20wsx"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="00c6", SYMLINK+="input/tablet-cintiq12wx"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="00c7", ENV{WACOM_TYPE}!="touch", SYMLINK+="input/tablet-dtu1931"

# Convenience links for the common case of a single tablet.  We could do just this:
#ATTRS{idVendor}=="056a", SYMLINK+="input/wacom-$env{WACOM_TYPE}"
# but for legacy reasons, we keep the input/wacom link as the generic stylus device.
ATTRS{idVendor}=="056a", ENV{WACOM_TYPE}!="touch", SYMLINK+="input/wacom"
ATTRS{idVendor}=="056a", ENV{WACOM_TYPE}=="touch", SYMLINK+="input/wacom-touch"

# Check and repossess the device if a module other than the wacom one
# is already bound to it.
#
# We probably don't need this one in the Real World anymore ...
# See the old wacom-tools package if we actually do need to resurrect the
# check_driver script for this again.
#ATTRS{idVendor}=="056a", ACTION=="add", RUN+="check_driver wacom $devpath $env{ID_BUS}"

LABEL="wacom_end"

---

### Post by Favux on 2013-03-04
OK, so the digitizer is working and is on ttyS0.  And setserial is not a problem.

You have the udev serial rule so that isn't the problem.

So now we want to look at Xorg.0.log in /var/log and see what that tells us.

You can use xorg.conf.  Breaking X was likely a video section or ServerLayout problem.  But yeah for sure we could break X a few times getting it set up.  Unless you have a old working xorg.conf for your X61t?  I might have a copy somewhere.

The way it works is what runs last controls.  And how it sort of goes is the system starts to read xorg.conf and then switches to xorg.conf.d.  The Distro location for xorg.conf.d runs first and then the user custom location.  And once it finishes xorg.conf.d it then actually runs xorg.conf.  So xorg.conf always controls and can over ride anything in xorg.conf.d.  The Xorg dev.s have guaranteed you will still be able to use xorg.conf.  There just is usually no reason to on a modern system except for the Nvidia proprietary drivers.

I'm still thinking there is no reason to try a Wacom .fdi file.  Although you have .fdi files I'm guessing HAL isn't actually active since you have xorg.conf.d.

---

### Post by bogamol on 2013-03-04
I do not have a functioning xorg.conf However, if I did Xorg -configure and delete the Video section, would that work? Hmm. Armed with ctrl-C to crush the ncurses error, I might get... I shall soldier on!

Also, I didn't see a ttyS0 or Wacom or wac or tablet or anything referenced in xorg.0.log

$ mousepad /var/log/xorg.0.log

X.Org X Server 1.7.7
Release Date: 2010-05-04
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.0.0-1-amd64 x86_64 Debian
Current Operating System: Linux heartOfGold-debian 2.6.32-5-amd64 #1 SMP Mon Feb 25 00:26:11 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-5-amd64 root=UUID=63284c28-92c7-45ac-9002-5691a017d224 ro quiet
Build Date: 29 October 2011  06:58:14PM
xorg-server 2:1.7.7-14 (Julien Cristau <jcristau@debian.org>) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar  4 12:54:01 2013
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7c8a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:2a02:17aa:20b5 Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller rev 12, Mem @ 0xf8000000/1048576, 0xe0000000/268435456, I/O @ 0x00001800/8
(--) PCI: (0:0:2:1) 8086:2a03:17aa:20b5 Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller rev 12, Mem @ 0xf8100000/1048576
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension SELinux
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 2.13.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6.901, module version = 0.4.2
	ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
(--) intel(0): Chipset: "965GM"
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): video overlay key set to 0x101fe
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): Output LVDS1 has no monitor section
(II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: LEN  Model: 4002  Serial#: 0
(II) intel(0): Year: 2006  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 25  vert.: 18
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: StandBy Suspend Off
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.572 redY: 0.332   greenX: 0.308 greenY: 0.536
(II) intel(0): blueX: 0.149 blueY: 0.157   whiteX: 0.305 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 66.8 MHz   Image Size:  245 x 184 mm
(II) intel(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1382 h_border: 0
(II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) intel(0): Unknown vendor-specific block f
(II) intel(0):  HV121X03-100
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff0030ae024000000000
(II) intel(0): 	0010010380191278ea8d5192554e8926
(II) intel(0): 	284e5421080001010101010101010101
(II) intel(0): 	0101010101011b1a0066410026301888
(II) intel(0): 	3600f5b8000000180000001000000000
(II) intel(0): 	000000000000000000000000000f0061
(II) intel(0): 	433c00000013020009e50000000000fe
(II) intel(0): 	0048563132315830332d3130300a007e
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
(II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1024x768"x60.0   66.83  1024 1048 1184 1382  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output LVDS1 connected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS1 using initial mode 1024x768
(II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(II) intel(0): Kernel page flipping support detected, enabling
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.7, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): [DRI2] Setup complete
(II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(II)         put_image
(II)         get_image
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(==) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder enabled
(II) intel(0): Set up textured video
(II) intel(0): Set up overlay video
(II) intel(0): [XvMC] i965_xvmc driver initialized.
(II) intel(0): direct rendering: DRI2 Enabled
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
SELinux: Disabled on system, not enabling in X server
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 270 x 203
(II) config/udev: Adding input device Power Button (/dev/input/event5)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6.901, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event5"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Video Bus (/dev/input/event8)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event8"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Lid Switch (/dev/input/event3)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event4)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event4"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event9)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event1)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event7)
(**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
(**) TPPS/2 IBM TrackPoint: always reports core events
(**) TPPS/2 IBM TrackPoint: Device: "/dev/input/event7"
(II) TPPS/2 IBM TrackPoint: Found 3 mouse buttons
(II) TPPS/2 IBM TrackPoint: Found relative axes
(II) TPPS/2 IBM TrackPoint: Found x and y relative axes
(II) TPPS/2 IBM TrackPoint: Configuring as mouse
(**) TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
(**) TPPS/2 IBM TrackPoint: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE)
(II) TPPS/2 IBM TrackPoint: initialized for relative axes.
(II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device PC Speaker (/dev/input/event2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event6)
(**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
(**) ThinkPad Extra Buttons: always reports core events
(**) ThinkPad Extra Buttons: Device: "/dev/input/event6"
(II) ThinkPad Extra Buttons: Found keys
(II) ThinkPad Extra Buttons: Configuring as keyboard
(II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event0)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device ACPI Virtual Keyboard Device (/dev/input/event10)
(**) ACPI Virtual Keyboard Device: Applying InputClass "evdev keyboard catchall"
(**) ACPI Virtual Keyboard Device: always reports core events
(**) ACPI Virtual Keyboard Device: Device: "/dev/input/event10"
(II) ACPI Virtual Keyboard Device: Found keys
(II) ACPI Virtual Keyboard Device: Configuring as keyboard
(II) XINPUT: Adding extended input device "ACPI Virtual Keyboard Device" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"

---

### Post by bogamol on 2013-03-04
Erp, Xorg -configure fatal error. Presumably because I tried to do it from gnome-terminal. Forgot that I can't do that except if X is not running.

---

### Post by Favux on 2013-03-04
That puzzles me.  There should be a match and we should see something with the keywords Wacom or ttyS0 in Xorg.0.log.

Do you get output when we try to query udev admin info?
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)
```
If so what is it?

Maybe we should change the match in the two snippets to this?
```
Section "InputClass"
Identifier "Wacom serial class"
#MatchProduct "Serial Wacom Tablet"
MatchDevicePath "/dev/ttyS0"
Driver "wacom"
Option "ForceDevice" "ISDV4"
EndSection

Section "InputClass"
Identifier "Wacom serial class identifiers"
#MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
Driver "wacom"
Option "ForceDevice" "ISDV4"
EndSection
```

---

### Post by bogamol on 2013-03-04
# udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pnp0/00:0a/tty/ttyS0':
    KERNEL=="ttyS0"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pnp0/00:0a':
    KERNELS=="00:0a"
    SUBSYSTEMS=="pnp"
    DRIVERS=="serial"
    ATTRS{id}=="WACf004"

  looking at parent device '/devices/pnp0':
    KERNELS=="pnp0"
    SUBSYSTEMS==""
    DRIVERS==""

---

### Post by bogamol on 2013-03-04
I notice in 20-wacom.conf that it says Driver "wacom"

lsmod | grep wacom doesn't list anything. Is it built directly into the kernel? That seems an odd way to do it...

---

### Post by bogamol on 2013-03-04
Tried changing the snippets. Lost Keyboard and Mouse. Still no Digitizer.

---

### Post by Favux on 2013-03-04
No, most of the Distros have wacom.ko as a seperate kernel module.  Although you can make it a built in at kernel build time if you wanted using the build in switch.  But remember you don't care because wacom.ko is a usb driver.
> Tried changing the snippets. Lost Keyboard and Mouse. Still no Digitizer. 
Now that is a bit of a puzzle.  I can accept the keyboard is a serial device but I do not recall the X61t sharing the keyboard and the digitizer on the same serial port.  Since the keyboard wants the evdev driver and the digitizer won't work on that...  But your Xorg.0.log didn't show any serial device on ttyS.  I don't see anything using a serial port.  And if the keyboard is serial it should be there.  Now by mouse do you mean the pointer stick or the trackpad?  If you've attached a serial mouse to the X61t that may be the problem.  In that case unplug that and reboot.

From the udevadm info. try using
```
MatchProduct "WACf004"
```
for the match.

Edit:  I guess you could also try:
```
MatchPnPID "WACf004"
```
Not sure that was available in your early version of xorg.conf.d.

---

### Post by bogamol on 2013-03-04
Mouse was imprecise. Sorry. I meant the trackpoint. The little red knobby guy on the middle of the keyboard.

This is what the snippets looked like when I disabled my computer.
Section "InputClass"
	Identifier "Wacom serial class"
	#MatchProduct "Serial Wacom Tablet"
	MatchDevicePath "/dev/ttyS0"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
        Option "ForceDevice" "ISDV4"

They are fixed back to this:
Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	#MatchDevicePath "/dev/ttyS0"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
**        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"**
        Driver "wacom"
        Option "ForceDevice" "ISDV4"

Do you want me to replace the bolded line with this?
MatchProduct "WACf004"

---

### Post by Favux on 2013-03-04
No.  Comment out the other matches and only use that match, as in:
```
Section "InputClass"
Identifier "Wacom serial class"
#MatchProduct "Serial Wacom Tablet"
#MatchDevicePath "/dev/ttyS0"
MatchProduct "WACf004"
Driver "wacom"
Option "ForceDevice" "ISDV4"
EndSection

Section "InputClass"
Identifier "Wacom serial class identifiers"
#MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
Driver "wacom"
Option "ForceDevice" "ISDV4"
EndSection
```

---

### Post by Favux on 2013-03-04
Oops.  Boy am I dense.  I just realized what was causing the confusion for you earlier.  There are two drivers called **wacom**.

In the kernel **wacom** refers to the usb kernel driver wacom.ko.

In X (xorg.conf.d or xorg.conf) **wacom** refers to the X driver wacom_drv.so.  That one is used by both the serial and the usb tablets.

Sorry.  :redface:

---

### Post by bogamol on 2013-03-04
So that borked the keyboard and the touchpoint too.  Why would 20-wacom.conf effect keyboard and touchpoint.

Xorg might be my kryptonite....that and printers.

---

### Post by Favux on 2013-03-04
> **bogamol said:**
> So that borked the keyboard and the touchpoint too.  Why would 20-wacom.conf effect keyboard and touchpoint.
At first blush it really doesn't seem like that should be happening.  That may be telling us something important.  We need to think about this.

If we are getting a valid match in xorg.conf.d wacom.conf something should be showing in Xorg.0.log.  You seem to have serial packets coming in from the digitizer (the stylus) over ttyS0.  Hard to see how matching to ttyS0 wouldn't work given that.  So what would stop the Wacom X driver at least attempting to initialize the digitizer?  Only thing I'm coming up with is if the Wacom X driver wasn't actually there.  Maybe try reinstalling the package?

If it is the hybrid X Server why is it using the standard location?  We never figured that out.  Maybe that's the problem?  We should be using the non-standard location?  Trying that may well break X.  What other .conf files are in your current xorg.conf.d?

---

### Post by bogamol on 2013-03-04
$ ls /usr/share/X11/xorg.conf.d
10-evdev.conf  20-wacom.conf  50-synaptics.conf

$ cat /usr/share/X11/xorg.conf.d/10-evdev.conf
#
# Catch-all evdev loader for udev-based systems
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

Section "InputClass"
        Identifier "evdev pointer catchall"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev keyboard catchall"
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev tablet catchall"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Do I even need synaptics? Per the [think wiki](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint) the Trackpoint is an evdev device, not synaptics. Other than whatever USB mouse I might plug in and the digitizer there are no other pointers on this laptop.

$ cat /usr/share/X11/xorg.conf.d/50-synaptics.conf
Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
EndSection

Here's 20-wacom.conf again. Check out the bolded comment.
It says WALTOP is getting dumped into evdev. So when I modify this file, I bet that's borking the keyboard and touchpoint with it.

Kernel problem? 

$ cat /usr/share/X11/xorg.conf.d/20*.conf
Section "InputClass"
	Identifier "Wacom class"
[b]# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"[/b]
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	#MatchDevicePath "/dev/ttyS0"
	#MatchProduct "WACf004"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
        Option "ForceDevice" "ISDV4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

---

### Post by Favux on 2013-03-05
Well that shoots down that idea.  If you have the evdev and synaptic .confs in that location then it is probably the correct xorg.conf.d location for your system and not something created by mistake.

Did you try reinstalling the Wacom X driver package with Synaptic Package Manager?  Debian has Synaptic Package Manager, doesn't it?

Other than that I'm sort of stalled.  The only other ideas I have I've already mentioned.  Trying to configure the tablet through xorg.conf might do something.  Not sure what if anything updating xf86-input-wacom would gain you.

Here's an xorg.conf I have.  It is similar to the other one I have except this one has touch.  You don't have touch correct?  So you'd want to remove the touch section and touch line in "ServerLayout".
```
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/ttyS0"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"
	Option		"Button2"	"3"
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/ttyS0"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"
EndSection

Section "InputDevice"
	Identifier	"touch"
	Driver		"wacom"
	Option		"Device"	"/dev/ttyS0"
	Option		"Type"		"touch"
	Option		"ForceDevice"	"ISDV4"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"stylus"	"SendCoreEvents"
	InputDevice	"eraser"	"SendCoreEvents"
	InputDevice	"touch"		"SendCoreEvents"
EndSection
```
Since the udev rule file you showed didn't seem to have the wacom symlink for serial tablet PCs, "/dev/input/wacom", I used "/dev/ttyS0".

---

### Post by bogamol on 2013-03-05
the xorg.conf file, placed in /etc/X11 has solved this issue. Hooray!!!!

You, sir, are a :guitar: :KS .

---

### Post by Favux on 2013-03-05
Outstanding!  :D

Could you post the output of **xinput list** now with the digitizer working?  While it may not tell us anything I'd love to get a handle on why the matches in xorg.conf.d weren't working.

---

### Post by bogamol on 2013-03-06
$ xinput list
[b]&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; stylus                                  	id=6	[slave  pointer  (2)]
&#9116;   &#8627; eraser                                  	id=7	[slave  pointer  (2)][/b]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=9	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=13	[slave  keyboard (3)]
    &#8627; ACPI Virtual Keyboard Device            	id=15	[slave  keyboard (3)]

---

### Post by Favux on 2013-03-06
Thanks.  lol  It's been so long since I've looked at a xorg.conf setup I forgot **xinput list** will show the section identifiers like stylus and eraser.  So that didn't get us anywhere.

How else can we find the name I wonder?  Don't think:
```
cat /proc/bus/input/devices
```
will work.  Don't know where ttyS0 shows up in /proc.

In the Wacom udev rules you showed the serial rule claimed the name would be **ENV{NAME}="Serial Wacom Tablet"**.  But why then didn't we get a match in xorg.conf.d?  Unfortunately the udevadm attributes walk didn't list the name.

I guess we just chalk it up to an issue with an early version of xorg.conf.d handling naming through a udev rule?

---

### Post by bogamol on 2013-03-06
$ cat /proc/bus/input/devices
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab54
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=402000000 83803078f900d001 feffffdfffefffff ffffffffffffffff
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
U: Uniq=
H: Handlers=event2 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=17aa Product=5054 Version=4101
N: Name="ThinkPad Extra Buttons"
P: Phys=thinkpad_acpi/input0
S: Sysfs=/devices/platform/thinkpad_acpi/input/input6
U: Uniq=
H: Handlers=kbd event6 rfkill 
B: EV=33
B: KEY=18840000 0 10000000000000 0 1501b00002004 8000000001104000 e000000000000 0
B: MSC=10
B: SW=a

I: Bus=0011 Vendor=0002 Product=000a Version=0000
N: Name="TPPS/2 IBM TrackPoint"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input7
U: Uniq=
H: Handlers=mouse1 event7 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: EV=3
B: KEY=3f000b00000000 0 0 0

I: Bus=0001 Vendor=11d4 Product=1984 Version=0001
N: Name="HDA Digital PCBeep"
P: Phys=card0/codec#0/beep0
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/input/input9
U: Uniq=
H: Handlers=kbd event9 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=0000 Product=0000 Version=0004
N: Name="ACPI Virtual Keyboard Device"
P: Phys=
S: Sysfs=/devices/virtual/input/input10
U: Uniq=
H: Handlers=kbd event10 rfkill 
B: EV=3
B: KEY=ffffffffffffffff ffffffffffffffff ffffffffffffffff ffffffffffffffff


The digitizer works because the singularity wants me to stop fiddling around with the settings. :)

---

