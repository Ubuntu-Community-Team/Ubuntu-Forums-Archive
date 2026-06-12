---
title: "Low Res... Please Help Noob!"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by devious_01 on 2009-04-04
Would someone please help me out.  I have read several articles and most of the noob papers out there today and still am no closer to figuring this out.  I just Installed Ubuntu 3 days ago and it always loads in low resolution.  I have an Ati Mach 64 Vid card and it seems to show up.  However, when i look in /etc/X11/xorg.conf it show no info at all other than the items are configured... eg: 

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


Please help me!?

Frustratedly yours

---

### Post by inobe on 2009-04-04
first and most important thing "run the system updates"

you can start these updates if you already haven't by clicking the red arrow next to network connection on top right corner...

if you never got such updates or a notification click applications> accessories> terminal..

in terminal type

```
sudo apt-get update
```

then hit enter.

when it's done post any errors here, if all is well close terminal and await the red update arrow.

click the arrow and install all updates.

when it's done you may need to reboot.

upon startup go to system> administration> hardware drivers.....

if there is a driver in there' activate it, if not let us know !

---

### Post by devious_01 on 2009-04-04
I did exactly what you said and there are no drivers listed here at all.


btw thank you very much for getting back to me so quickly

---

### Post by inobe on 2009-04-04
please include some information.

have you gotten all the updates.

have you made any changes that resulted in the low resolution.

what version of ubuntu is installed on your computer.

did you install ubuntu inside of windows or did you dual boot with windows.

what is the make and model of your computer.

---

### Post by Briandb1222 on 2009-04-04
Have the same issues heh...except I don't boot up in low res mode. I have a Gateway MX3228. Did what people told me I should do and to no avail. Talked to a repairman and he said that it is possible that the computer's drivers (not Ubuntu's drivers) are probably out-of-date. Though, according to others with the newer computers, they have no problems like this...or find an easy fix.

However people like us with older computers are going to have a lot of issues, due to compatibility. Perhaps Ubuntu's included drivers do not compat well with older drivers.

My specific problem is that my resolution is stuck at 1600x1200. If I change it to the correct settings (1024x767), I get horizontal lines or vertical, one of the other I don't remember. I tried editing xorg.conf but of, course there is no information reguarding my monitor in there as well...mine shows exactly what your's does. I added the Mode and VertRefresh and HorizSync in there, but didn't work.

Someone who also uses Ubuntu, suggested my graphics driver is missing. Possible, as Ubuntu is probably confused and doesn't know what my graphics driver is, and is taking a guess by what size it is by changing it to the highest resolution there is (as far as computer monitors go anyways). I'm attempting to find out how to get my graphics driver as we speak...if I find the solution I will post it.

---

### Post by devious_01 on 2009-04-04
I did the updates as soon as i was able to get to the gui/desktop apon install.  I did the install as a dual boot from windows and was unable to get to the gui (being a noob i didn't understand the cli is better).  So i installed again from the a direct boot up from the cd.  Once the install was completed (or so i thought) i rebooted and there was the dual boot set up.  From there it has always forced me into low res saying unable to detect screen(s).  Once i actually was able to use the gui, it prompted me to do an actual install from there.  Once i did that install i had the dual boot option again.  I selected ubuntu and again forced into low res.  It promted me to do updates. (so i did)  And here i am after a whole lot of reading.

I am running:  Ubuntu 8.10 - the Intrepid Ibex - released in October 2008.

My comp is custom made.  What exact spects are you after?


Thank you again.

---

### Post by inobe on 2009-04-04
> **Briandb1222 said:**
> 

Someone who also uses Ubuntu, suggested my graphics driver is missing. Possible, as Ubuntu is probably confused and doesn't know what my graphics driver is, and is taking a guess by what size it is by changing it to the highest resolution there is (as far as computer monitors go anyways). I'm attempting to find out how to get my graphics driver as we speak...if I find the solution I will post it.

please read this [http://ubuntuforums.org/showpost.php?p=7013830&postcount=8](http://ubuntuforums.org/showpost.php?p=7013830&postcount=8)

and this 

[http://ubuntuforums.org/showpost.php?p=7013795&postcount=7](http://ubuntuforums.org/showpost.php?p=7013795&postcount=7)

the documentation site

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

if you don't know what to do' please start your own topic in the correct forum, here [http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

your system specs [http://support.gateway.com/s/Mobile/Q106/MagicLC/1008831sp2.shtml](http://support.gateway.com/s/Mobile/Q106/MagicLC/1008831sp2.shtml)

---

### Post by inobe on 2009-04-04
> **devious_01 said:**
> 

My comp is custom made.  What exact spects are you after?


Thank you again.

i will try my best to help.

open terminal and type

```
lspci
```

copy and paste

hit enter and copy the output from terminal on your next post wrapped in code, example of code: #

---

### Post by inobe on 2009-04-04
i have to go, you will need to read the documentation for the ati card.

the best i can do with what i have 

[http://packages.ubuntu.com/intrepid/xserver-xorg-video-mach64](http://packages.ubuntu.com/intrepid/xserver-xorg-video-mach64)

---

### Post by devious_01 on 2009-04-04
As you requested... here is my lspci

sentra@Sentra:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8753 [P4X266 AGP] (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:08.0 VGA compatible controller: ATI Technologies Inc 215CT [Mach64 CT] (rev 09)
00:09.0 Communication controller: ESS Technology ES2838/2839 SuperLink Modem (rev 01)
00:0c.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 42)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)

---

### Post by inobe on 2009-04-04
in synaptic search for **mach64**

tell me what is listed after the search

---

### Post by devious_01 on 2009-04-04
i have 4 packages listed.... 3 are installed... one isn't

not installed: xserver-xorg-video-ati-dbg
intalled: xserver-xorg-video-mach64 | 6.8.0-1build2
          xserver-xorg-video-mach64 | 6.8.0-1build2
          xserver-xorg-video-ati | 1:6.9.0+git20081003.f9826a56-0ubunto2.1

---

### Post by inobe on 2009-04-04
the dbg is for debugging symbols, i am uncertain if that has a connection or not, let me review the docs.

---

### Post by Rumtscho on 2009-04-04
What happens when the xorg is loaded? 

You will find that info under /var/log/xorg.0.log. 

I am combating a similar problem now, but with a nVidia card. Looks like my monitor is sending wrong signals (EDID) to the card. Just search your log file for any lines starting with (WW) or (EE).

---

### Post by devious_01 on 2009-04-04
If i type:
gedit /var/log/xorg.0.log

there is nothing in that file... i just created it on the fly

---

### Post by devious_01 on 2009-04-04
under my system log view it has:

(WW) VESA(0): Unable to estimate virtual size
(WW) VESA(0): No valid modes left.  Trying less strict filter...

there are a ton of (II) 's too

---

### Post by devious_01 on 2009-04-04
here is the bottom portion of that Xorg.0.log file:

(II) VESA(0): Total Memory: 32 64KB banks (2048kB)
(II) VESA(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(WW) VESA(0): No valid modes left.  Trying less strict filter...
(II) VESA(0): Configured Monitor: Using hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(--) VESA(0): Virtual size is 800x600 (pitch 800)
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(==) VESA(0): DPI set to (96, 96)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"

(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 1.2
(II) VESA(0): VESA VBE Total Mem: 2048 kB
(II) VESA(0): VESA VBE OEM: ATI MACH64
(II) VESA(0): virtual address = 0xb787d000,
	physical address = 0xa0000, size = 65536
(II) VESA(0): VBESetVBEMode failed...Tried again without customized values.
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device ImPS/2 Generic Wheel Mouse
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event6"
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"

---

### Post by inobe on 2009-04-05
tried finding rock solid information except it's all outdated !

this for example: [http://www.bakarasse.de/mach64-howto.html](http://www.bakarasse.de/mach64-howto.html)

i seriously doubt that will work in 8.10 with the newer xserver.

my suggestion would be start a topic in multimedia and video forum, hopefully someone will spot this and be able to help you more efficiently .

---

### Post by devious_01 on 2009-04-05
I sincerely appreciate all the help you have tried to give me.  I will do as you requested.


Thanks

Devious_01

---

### Post by inobe on 2009-04-05
is this an agp or pci card ?

if it's pci card' that's probably why this is happening.

quite honestly' if you have an agp slot' a cheap nvidia card 6series and up would be worthy.

---

### Post by devious_01 on 2009-04-05
it is a pci... i have an agp (Ati Radeon x700 pro 256M) infront of me now.  But when that is installed i don't get to see the gui at all

---

### Post by inobe on 2009-04-05
you have a better chance with that agp card.

the opensource driver [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

the binary driver [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

also i haven't asked' but if you have onboard video you should disable it in the system bios before installing any add on cards.

as for the agp card' are we sure it functions/ works ?

---

### Post by devious_01 on 2009-04-05
it works awesome... if i exit out of Ubuntu and log into XP pro i have good graphics there.

---

### Post by inobe on 2009-04-05
i would like to add, since you get a black screen' restart again and hit escape when you see the grub count down and choose recovery mode, then choose xfix......... run threw it, that should get you to see a gui.

then we can go from there

example

[IMG]http://ramonecung.com/blog/uploads/2008/07/ubuntu-1.png[/IMG]

[IMG]http://www.psychocats.net/ubuntu/images/resetpassword02.png[/IMG]

[IMG]http://1.bp.blogspot.com/_LKra8AUL9bY/SRleYPWhWfI/AAAAAAAAALY/MetRjP9OxqU/s400/20081111149.jpg[/IMG]

only do these if you get the infamous black screen

---

### Post by devious_01 on 2009-04-05
so you want me to load my good vid card in and reboot?

 good = x700 pro agp 256M Ati?

---

### Post by inobe on 2009-04-05
yes unless you do not wish to proceed ?

it's your choice :)

---

### Post by devious_01 on 2009-04-05
> **inobe said:**
> yes unless you do not wish to proceed ?

it's your choice :)

I'm now chatting via BlackBerry ... I'm now sitting on a black cli that says Sentra login:  with a blinking cursor

---

### Post by devious_01 on 2009-04-05
I'm now chatting via BlackBerry ... I'm now sitting on a black cli that says Sentra login: with a blinking cursor

---

### Post by inobe on 2009-04-05
did you hit escape and enter recovery to select xfix ?

---

### Post by devious_01 on 2009-04-05
Yeppers ... I'll restart and do it again.  However it went exactly like the pictures

---

### Post by inobe on 2009-04-05
if it happens to throw you back in cli do

```
sudo dpkg-reconfigure xserver-xorg
```

then follow the prompts

---

### Post by devious_01 on 2009-04-05
Rebooted and still @ the same spot

---

### Post by inobe on 2009-04-05
> **inobe said:**
> if it happens to throw you back in cli do

```
sudo dpkg-reconfigure xserver-xorg
```

then follow the prompts

try that

---

### Post by devious_01 on 2009-04-05
I can type that in, but as soon as I hit enter it asks for a password.  If I enter my password, I get login incorrect and I'm positively sure its the right password as I just ussed it on the other graphics card

---

### Post by inobe on 2009-04-05
instead of selecting xfix go into root !

then run that command

example of the selections, notice "drop to root shell"

[IMG]http://1.bp.blogspot.com/_LKra8AUL9bY/SRleYPWhWfI/AAAAAAAAALY/MetRjP9OxqU/s400/20081111149.jpg[/IMG]

---

### Post by devious_01 on 2009-04-05
Its late and I'm exausted... I'll do a fresh install when I wake up and then look you up

---

### Post by inobe on 2009-04-05
ouch i was getting anxious :lol:


okay' i will see you tomorrow :guitar:

---

### Post by Thomper101 on 2009-04-05
Hi there

I've been following this thread because i had the same problem, but after following your instructions i can now get 1024x768,
thank you.

Now i have get the network card to work, but i'll start another thread for that.

---

### Post by inobe on 2009-04-05
glad some of the info helped you.

---

