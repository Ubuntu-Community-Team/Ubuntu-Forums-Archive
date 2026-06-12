---
title: "NVidia Geforce 4 MX 4000 (Can't boot with it)"
date: 2008-03-09
forum: Hardware &amp; Laptops
---

### Post by jou770d on 2008-03-09
After using Gutsy for a while on my laptop I thought that it's time to install it on my Desktop (dual-boot, I need windows for my parents' use and certain programs).
However I wasn't able to boot from the live cd (it kept getting stuck during hardware recognition). I tried removing the mentioned card (NVidia Geforce 4 MX 4000) and used the built-in card instead, everything worked fine and I got Ubuntu installed.
I tried putting the card back in and booting into the now installed Ubuntu but I was unsuccessful because it froze again (if the place it freezes on is of importance tell me and I'll try doing it again to tell you).
All the "How To"s that I found concerning installing NVidia drivers mention that I should have the card installed during the process...
So what can I do in order to get the card working on Ubuntu?? I can't just keep removing it everytime I want to boot into Gutsy and put it back in when I'm using windows.

This are my device's specs if it's of any use:
Biostar 865GV Micro 775
Pentium 4 3.00GHz (2 CPUs)
512 RAM
Nvidia GeForce 4 MX 4000 / 128 RAM (rather old)
Creative SB Live! 5.1
Creative Modem Blaster
LifeView FlyTV Prime 34

I want to change that card but I would also need to change the mobo and probably the rams while I'm at it but I can't afford doing so at the time being.

---

### Post by jou770d on 2008-03-10
bump

---

### Post by jou770d on 2008-03-13
This is both a bump and an update.
I found out that I it wasn't necessary to remove the card in order to get gutsy to boot. I left it and connected the monitor to the other card and that worked.
So I installed the NVidida restricted drivers and restarted but that resulted in messing up my whole device:
Gnome didn't start up correctly so I used a teminal to restart planning to go online using windows to see if there's something I'm supposed to do. However I was no longer able to boot into windows. And the whole device was freezing sometimes even before reacinng grub's menu.
I managed to boot into ubuntu, uninstalled the drivers from the terminal and resotred my old xorg.conf. That seems to have fixed the freezing problems but I was still unable to reach windows. To fix that I had to repair my windows installation.

My next step is to try using Envy but before I'm doing that I'm backing up my important docs and files in case something went "wronger" than my first attempt.

Any ideas and comments are welcomed...

---

### Post by mgranet on 2008-03-13
Your video cards are both duking it out for control. You need to disable the onboard card in your BIOS. You may have to reconfigure your X configuration with ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by jou770d on 2008-03-13
Tried dissabling the onboard card already, it didn't work. (Neither before nor after installing the restricted drivers).
But about reconfiguring x, I should do that with the restricted drivers installed?? Right?

---

### Post by mgranet on 2008-03-13
Correct. If you have the restricted drivers installed, try doing a ```
sudo nvidia-xconfig
``` first.
Try that before the dpkg-reconfigure, and reboot. It might work, if not, then try the dpkg-reconfigure one. If that fails, we'll still be here :)

---

### Post by mgranet on 2008-03-13
Also, what drivers are you using? nvidia-glx, or nvidia-glx-new? The 4 series only work with nvidia-glx, not the glx-new

---

### Post by jou770d on 2008-03-14
Someone on an another board told me that he had installed Ubuntu with the same card as mine without any trouble whatsoever, he recommended updating my GART drivers but that didn't change a thing.
And I tried, once again, to install the restricted driver (and made sure that I wasn't mistakingly installing nvidia-glx-new instead of nvidia-glx) but it's still the same thing: using the geforce4 card I can't boot (I'll put where it freezes in the end of the post), and using the onboard card I boot to a messed up gnome (tried nvidia-xconfig and dpkg-reconfigure but obviously, since I was using the onboard card, they only corrected the settings for that card but didn't change anything concerning the geforce). I'm not sure if windows is messed up this time cause I haven't tried it, I'm more concerned about Ubuntu since any possible windows' problems can be fixed by repairing from the cd.
I still haven't tried Envy. I'm about to try it now but I'm starting to lose hope about getting this card to work.
However I do have an idea, but being a linux noob I'm not sure if it's not plain stupidity. What I'm thinking about is this: would it change anything if I used a system specific kernel instead of the generic one??

Here's where the booting process freezes when I'm using the geforce4 card.
```
[85.952058] [<c01260c8>] mmput+0x38/0xa0
[85.957437] [<c012b5ff>] do_exit+0x10f/ox810
[85.962805] [<c01323e9>] __dequeue_signal+0xd9/0x160
[85.968190] [<c01320ab>] recalc_sigpending+0xb/0x20
[85.973563] [<c012bd26>] do_group_exit+0x26/0x80
[85.978934] [<c0134368>] get_signal_to_deliver+0x298/0x410
[85.984329] [<c02f5b70>] do_page_fault+0x0/0x690
[85.989703] [<c01037d3>] do_notify_resume+0x93/0x720
[85.995097] [<c016ce38>] __handle_mm_fault_0x288/0xb00
[86.000525] [<c016ce38>] __handle_mm_fault_0x288/0xb00
[86.005914] [<c02f62a7>] atomic_notifer_call_chain+0x17/0x20
[86.011335] [<c02f5f63>] do_page_fault+0x3f3/0x690
[86.016768] [<c02f5b70>] do_page_fault+0x0/0x690
[86.022152] [<c010432e>] work_notifysig+0x13/0x25
[86.027529] =======================
[86.032857] Code: db e1 ff ff 90 b9 03 00 00 00 89 c9 8d b6 00 00 00 00 8b 04 24 83 c4 04 5b 5e 5f 5d c3 83 c4 04 89 d8 5b 5e 5f 5d e9 24 a4 04 00 <0f> 0b eb fe 8b 0d 34 e3 44 c0 e9 35 ff ff ff 90 8d 74 26 00 89
[86.044620] EIP: [<c011fbbc>] kmap_atomic_prot+0xbc/0xc0 SS:ESP 0068:dd69ddc4
[86.050444] Fixing recursive fault but reboot is needed!
[86.056274] BUG: scheduling while atomic: udevd/0x00000001/3911
[86.062047] [<c02f22fb>] shedule+0x4db/0x890
[86.067928] [<c012bc58>] dO-exit+0x768/0x810
[86.073758] [<c0105edf>] die+0x25f/0x260
[86.079565] [<c0106200>] do_invalid_op+0x0/0x90
[86.085357] [<c0106281>] do_invalid_op+0x81/0x90
[86.091095] [<c011fbbc>] kmap_atomic_prot+0xbc/0xc0
[86.096738] [<c02f43f2>] error_code+0x72/0x80
[86.102249] [<c011fbbc>] kmap_atomic_prot+0xbc/0xc0
[86.107795] [<c016b48c>] unmap_vmas+0x1ac/0x5d0
[86.113174] [<c0163591>] get_page_from_freelist+0x2c1/0x3a0
[86.118411] [<c012081a>] task_rq_lock+0x4a/0x80
[86.123455] [<c016f008>] exit_mmap+0x78/0xf0
[86.128408] [<c01260c8>] mmput+0x38/0xa0
[86.133329] [<c012b5ff>] do_exit+0x10f/ox810
[86.138228] [<c01323e9>] __dequeue_signal+0xd9/0x160
[86.143124] [<c013204b>] recalc_sigpending+0xb/0x20
[86.147956] [<c012bd26>] do_group_exit+0x26/0x80
[86.152758] [<c0134368>] get_signal_to_deliver+0x298/0x410
[86.157548] [<c02f5b70>] do_page_fault+0x0/0x690
[86.162249] [<c01037d3>] do_notify_resume+0x93/0x720
[86.166879] [<c016ce38>] __handle_mm_fault_0x288/0xb00
[86.171458] [<c016ce38>] __handle_mm_fault_0x288/0xb00
[86.175902] [<c02f62a7>] atomic_notifer_call_chain+0x17/0x20
[86.180292] [<c02f5f63>] do_page_fault+0x3f3/0x690
[86.184671] [<c02f5b70>] do_page_fault+0x0/0x690
[86.193289] [<c010432e>] work_notifysig+0x13/0x25
[86.193289] =======================
```
The last 5 lines are always the same but the ones before them change sometimes without me doing any changes.


Update:
Used Envy, installing it and getting it to work was a real pain in the neck, and nothing changed...
This is my very last idea: would it help if I manually configured the xorg.conf using the onboard card and rebooted using the geforce4 card??
And I made a trivial discovery, if I tried booting with the onboard card enabled with the monitor connected to the geforce4 card the device gets stuck in an infinite loop (but I couldn't read what was on the screen cause it was changing way too fast).
The only bright side for what I've tried today is that windows isn't messed up this time, don't know why but I'm glad that I don't have to wait for an hour to repair it..

---

### Post by mgranet on 2008-03-14
Can you post the text of your xorg.conf? Also, post the output of```
lspci
```.

---

### Post by jou770d on 2008-03-15
First off all I seem to have forgotten to thank you for you support! I really appreciate it.

Here's my xorg.conf (after installing the driver through Envy and allowing it to auto-configure the file), it doesn't seem right to me: (As I already made clear I was using the onboard card to get this file)
```
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

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82865G Integrated Graphics Controller"
	Driver		"nvidia"
	Busid		"PCI:0:2:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Controller"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1440x1440"	"1440x900"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

As for the lspci output here it is:

```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)
01:01.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
01:02.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
01:02.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
01:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:04.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)

```

As I don't know how to make one myself I'm currently looking around for a more appropriate xorg.conf to replace this one whilst waiting for your help..

---

### Post by mgranet on 2008-03-16
Wow. That's one screwed up xorg. This whole thing is odd. lspci is showing your 865G, which you stated you were running. However, you shouldn't be installing Nvidia drivers if you are running on the onboard(865G) card. However, if you disable the onboard, and try booting with the MX4000, the system freezes before it can even boot. This almost leads me to think 'card failure', but it works in Windows. Very odd, and very much above my head. I'll give it some thought, and get back to you if I can come up with anything more.

Let me ask you: Where,generally speaking, in the boot up process (from power-on to desktop) does the card freeze?

---

### Post by jou770d on 2008-03-16
The device freeze happens while the bar in the usplash is loading, when it's still about 1/5 full or maybe a bit less.
I've posted in the first page what I last see if I used recovery mode instead. And when I get home (currently posting from uni) I'll post the other version I sometimes get (as I said it changes sometimes). And I'll also check it there's any change in the card's fan or something.
I found many threads by people having the same problem but none with a solution... So I've practically surrendered. I'm going today to check the prices to see if I can manage a new card, a decent mobo and a 1gb ram stick. 
Anyway, thanks for trying to help.

---

### Post by peshwali on 2008-03-17
Hey, i am getting the exact same problem with a GeForce 5 FX card.  Works fine on Windows, but with Ubuntu 7.10 (alternate CD install), it will not work as the primary card.  

There were no errors in the installation.  I had been trying to make it work on a already installed installation, but I got the exact same kind of xorg.conf problems you have.  I then tried to install on a different hard drive, but same computer, and made the Nvidia card primary from the beginning and have had the same problem.

It locks on the boot, in both regular and recovery mode.   I tried taking out the "splash" option in Grub, but still no luck.  I cannot access a tty, so no luck doing any config changes.

Any thoughts anyone?

---

### Post by peshwali on 2008-03-17
I think I found a solution and it seems to work for me.  The solution is for a ASRock motherboard (which I have), but it may work with others.  This was in a post a year ago:

> **todoporron said:**
> Hi 

About a year ago, I had the same problem with an Asrock board with embeded graphics and my Nvidia card.

The solution:

Edit your /etc/modprobe.d/blacklist file:

```
sudo gedit /etc/modprobe.d/blacklist
```

and add the following line:
```
blacklist intel_agp
```

After that, you have to install your Nvidia drivers if you have not done it yet. 

On your BIOS setup, disable your onboard graphics and enable your Nvidia card. This should solve the problem .

So what I did:

1. enabled and used internal MB video card to get to ubuntu
2. followed instructions above
3. shutdown and restarted computer, but now I disabled internal video in BIOS (as mentioned above)
4. booted into Ubuntu, but there was no gui, so I did ctrl-alt-f1 to get to terminal
5. did the following from the command prompt (choosing Nvidia or nv as graphics card and did other necessary steps, which should be explained elsewhere):
```
sudo dpkg-reconfigure xserver-xorg
```
6. Rebooted system
7. Went to work setting up video as desired (i.e. envy, nvidia, ubuntu's nvidia driver, etc.)

I did this in my new setup and in my old setup and both work now!!

For your reference, here is the post in context:
[http://ubuntuforums.org/showpost.php?p=2392604&postcount=2]("http://ubuntuforums.org/showpost.php?p=2392604&postcount=2")

---

### Post by jou770d on 2008-03-17
Weird... I remember replying to your post by saying that I'll try this after my Spanish course. Must have been a problem with my connection,
Anyway, I did try it and it works!  I'm currently still editing the display settings.
Thanks! My English fails me in describing how grateful I am..

The only annoying side effect of this is that I seem to have lost the sound... Same thing happened on my laptop when I installed the restricted driver for my modem but I didn't look for a solution at the time cause I don't care about that modem and removing the driver gave me back my sound. However I remember seeing tons of threads about the subject I'm sure I'll find a solution.

---

