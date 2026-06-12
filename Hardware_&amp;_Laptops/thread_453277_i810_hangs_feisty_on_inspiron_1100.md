---
title: "i810 hangs feisty on inspiron 1100"
date: 2007-05-24
forum: Hardware &amp; Laptops
---

### Post by Eil on 2007-05-24
Greetings,

I have a Dell Inspiron 1100 laptop with an Intel 845GL chipset. On every other Linux distribution that the machine has run, the i810 X driver has worked pretty much flawlessly on this laptop. However, after installing Feisty, I cannot get the i810 driver or the newer 'intel' driver to work.  I've been a Linux geek for 11 years now, so I've run into my fair share of X problems in the past, but this one has me truly stumped. 

When I specify 'i810' as the driver in xorg.conf and reboot the machine, X appears to start loading the login manager. It gets as far as showing the X cursor (with the spinner) and then the machine hangs. So then I boot into recovery mode and check the Xorg.0.log file and am presented with the following error messages:
```

Fatal server error:
lockup

(II) AIGLX: Suspending AIGLX clients for VT switch
Error in I830WaitLpRing(), now is 78528, start is 76527
pgetbl_ctl: 0x1ffe0001 pgetbl_err: 0x49
ipeir: 0 iphdr: 50300003
LP ring tail: 180 head: 144 len: 1f001 start 0
eir: 0 esr: 10 emr: ff7b
instdone: ffc1 instpm: 0
memmode: 0 instps: 24
hwstam: fffe ier: 82 imr: 53c iir: 0
space: 131004 wanted 131064

FatalError re-entered, aborting
lockup
```

The catch is that *sometimes* it doesn't do this. In these cases, X just works fine, I get normal 2D acceleration and everything is happy. But on the next startup or reboot, it freezes again.

One thing I tried was the Xorg 'intel' drivers. 'apt-get install xserver-xorg-video-intel' and change the driver to 'intel' in xorg.conf. This hangs the machine in much the same way, except it seems to happen quicker (no X cursor) and without the error messages pasted above for the i810 driver. I also tried commenting out the optional X modules (dri, dbe, glx, etc) on both drivers, and setting pci=noacpi on the kernel command line. Nothing helped.

I've Googled the problem for days now but am no closer to an answer. People have reported error messages similar to those described below, but only in the context of resuming their session after putting the laptop in suspend. This happens on boot and I haven't seen anyone else with the same identical problem. I'm thinking of filing a bug with the Ubuntu folks, but many people seem to have not had much luck with that.

---

### Post by Eil on 2007-05-31
So, nobody with any similar issues on their inspiron 1100 or similar Dell laptop?

---

### Post by Merrickk on 2007-06-04
I have the same lap and chipset, but it runs.  My issue is that I can't seem to get it to run in the correct resoulution.  It will only go up to 1024x768.  Looks like poop on the lcd.  I also tried the xorg driver, but alas am extremely new to linux and am very lost at this point.  When I force the 1280x1024 res into the conf file, it seems to ignore it.  I even tried removing all the other res options.

Wish I could help more, with some guidance i'd be happy to give you any info from my machine.

Merrickk

---

### Post by treue on 2007-06-05
I have a i845GV chipset and I can confirm the bug you present to the letter - sometimes (apparently phase-of-the-moon-dependent) xorg will lockup at startup - I have attached the relevant Xorg log file, but the relevant lines mirror yours, Eil:

Error in I830WaitLpRing(), now is 67469, start is 65468
pgetbl_ctl: 0x3ffe0001 pgetbl_err: 0x49
ipeir: 0 iphdr: 50300003
LP ring tail: a8 head: 144 len: 1f001 start 0
eir: 0 esr: 10 emr: ff7b
instdone: ffc1 instpm: 0
memmode: 0 instps: 424
hwstam: fffe ier: 82 imr: 53c iir: 0
space: 148 wanted 152
(II) I810(0): [drm] removed 1 reserved context for kernel
(II) I810(0): [drm] unmapping 8192 bytes of SAREA 0xf8c8d000 at 0xb7c51000

Fatal server error:
lockup

I'm rather linux experienced (post sysadm at ~1000 users system) but I'm at a loss with this one - It appears to be (x)ubuntu-specific, since other linux-dists have worked fine for me. I have
tried another driver (available from [http://www.fairlite.demon.co.uk/intel.html]("http://www.fairlite.demon.co.uk/intel.html")) since others with similar (though not exactly the same) problems had some succes with that, but alas, no luck.

running:
ASUS P4BP-MX (with intel i845GV chipset)
xubuntu 7.04 (feisty)
xorg 7.2.0
linux 2.6.20-15

have you (or someone else) had any luck so far?

/Frederik Treue

---

### Post by jdelagar on 2007-08-28
Hi !

I'm having the exact same problem.  Using a Toshiba Satellite 1005-S157 and Feisty 7.04.  Any hint?

Thanks...

---

### Post by OttifantSir on 2007-08-28
I saw treue reported having kernel 2.6.20-15. I haven't tried the intel driver on that kernel as I always do the update right after installing, and that gives me kernel -16. (I am a newb at this, so apologise in advance if this does anything worse). The resolution isn't right on an Inspiron 9400 (1024x768, not 1440x900), so I install the intel driver, reboot X (Ctrl-Alt-Backspace) and I have full resolution.

I haven't had it hang on boot on me like you have, but it MIGHT be a solution to upgrade the kernel if you haven't already done so, and you know it will break your installation.

---

### Post by linux-guy-from-mich on 2007-11-05
I installed gutsy on a Dell Inspiron 1100 laptop and am having the same problem.
I had no video on the desktop.  When I did ctrl-alt-f1 to get to the console, the letters were really big and I could not see what I was typing.
I have tried numerous solutions suggested on posts all over the internet and nothing seems to solve the problem.
I am able to limp along with a small 640x480 screen that is shrunk in the middle of the display.  To get that far, I did the following:

- Remove splash from the kernel line in /boot/grub/menu.lst
- Rename /etc/X11/xorg.conf to something else, preventing the server from finding it and using whatever defaults it wished.

To do these things, I had to boot using recovery mode.

---

### Post by brymux on 2007-11-30
> **Merrickk said:**
> I have the same lap and chipset, but it runs.  My issue is that I can't seem to get it to run in the correct resoulution.  It will only go up to 1024x768.  Looks like poop on the lcd.  I also tried the xorg driver, but alas am extremely new to linux and am very lost at this point.  When I force the 1280x1024 res into the conf file, it seems to ignore it.  I even tried removing all the other res options.

Wish I could help more, with some guidance i'd be happy to give you any info from my machine.

Merrickk

I have the same problem on my inspiron 1000,am using an HP f1905b monitor but no matter what I try can't get more than the 1024x768...
Is it because the built in screen can only go that high after updating the SiS and Microsoft drivers?
Or because Ubuntu keeps installing the 915 chipset driver?then says its the wrong one?
After reconfiguring Xserver several times all I have been able to accomplish is an 900x720 and some extra refresh rate options 65,70,75
On my HP media center with a Radion xvs600 pcie card and a 37" flat panel (going dvi-hdmi) I can't get any flaver of linux to display past the initial screens...which I don't understand because the boot option screens all show up fine.(sorry off track)
If any one figures out this screen resolution problem please let me know.:(

---

### Post by brymux on 2007-12-01
I don't have alot of luck even less experience  "makeing from binaries" but this page might help.
Could some one check it out and explaine it to me if this is on the right track?[http://www.winischhofer.eu/linuxsisvga.shtml]("http://www.winischhofer.eu/linuxsisvga.shtml")

---

### Post by BDNiner on 2007-12-01
I have the same problem on my 1100. If you press ESC on the grub screen and then select your kernel it should boot properly. I am looking for the post to fix this issue. Basically the boot screen takes up too much memory when starting ubuntu so when it comes time to load X the computer crashes. There is a text file that you can edit to remove the boot screen so that you see the output when booting instead of the ubuntu logo with the progress bar. That is the fix for this issue. When i upgraded to gutsy i accidentaly overwrote that file with a default one.

---

### Post by grege on 2007-12-01
I have the same issue in Gutsy. The simplest solution is to edit your grub menu and remove "splash". This bypasses the problem by forcing a text boot process.

/boot/grub/menu.lst

Scroll down towards the end to where it says  ## ## End Default Options ## ##

Then the third line starting with "kernel"  - at the end of the line remove the word "splash"

You will need to "sudo gedit /boot/grub/menu.lst"  to edit the file.

---

### Post by linux-guy-from-mich on 2007-12-02
I finally have the Dell Inspiron 1100 working fairly well with gutsy.
I still have the splash screen disabled in the grub configuration file.
This is what I am using in /etc/X11/xorg.conf:
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"Intel 810"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
	Vendorname	"Intel"
	Option		"XaaNoPixmapCache"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"Intel 810"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	1
	Vendorname	"Intel"
	Option		"XaaNoPixmapCache"
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

### Post by apos on 2008-01-16
I used to have the same problem with a Thinkpad R31 which has another intel chipset (i830M). I came to the same solution as you: using the "i810' driver and disable the splash screen. The full story can be read [HERE]("https://wiki.blue-it.org/Thinkpad_R31#Xorg").

Unfortunatly after a few days of normal bootup's, the error occurs again. Sometimes X just freezes at startup.

Sometimes the only way to reactivate X is, to first boot up the second linux (suse 10.3) on this notebook, activate a video in there and then reboot into ubuntu.

---

