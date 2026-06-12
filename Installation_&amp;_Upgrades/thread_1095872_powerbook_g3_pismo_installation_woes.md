---
title: "powerbook g3 pismo installation woes"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by mrjohnc on 2009-03-14
good afternoon

i am tearing my hair out over this. i'm trying to install 8.04 on a powerbook g3 pismo (500mhz, 256 ram) 

when i try to run the live cd the monitor goes out of sync, the screen is a party of moving diagonal lines. i've managed to get as far as using live vga=788 to get it to boot live 800x600. i start the installation but it freezes, i guess it doesn't like being 800x600. i'm fairly sure the hardware is ok because i got osx 10.4 working on it, which i can't use my wireless card on, stupid apple.

i tried the new 9.04 alpha and 8.10 with the non live install which installed ok but then when it had installed and it booted it went to stripy city again. i tried the ctrl,alt,- trick to get the resolution down but no dice. i guess it would be at the log in screen anyway.

it did the same when i tried to install fedora (which i don't really want, it was just to see) but was fine with ydl (don't want either). i guess it's a problem with the drivers thinking the screen can do higher resolution than it can, it can definately do 1024x768 but i just think the hz is wrong.

i've trawled google but can't find anyone with the same problem

any help would be super

thanks

---

### Post by thejmfc on 2009-03-14
Hey, I think I can help.  I just installed Debian Lenny on my Pismo (400 mhz, 512 ram) the other day, and had the same issue with xorg not self-configuring.  

I tried dpkg-reconfigure xserver-xorg, and that didn't do it.

I tried manually editing /etc/X11/xorg.conf file, but nothing I made up worked either.

So... Some Googling told me that lots of people had installed Ubuntu 5.10 without trouble back in the day.  Obviously it self-configured better.  With that in mind, I downloaded and burned the Breezy Badger PPC live cd, and booted it.  X worked fine, so I copied /etc/X11/xorg.conf from the live setup to my Debian setup.  That works fine.

I'll save you the trouble of downloading a whole other .iso image.  I just have to switch to Debian (can't seem to mount that partition from OS X yet), and I'll post my config file.

EDIT:  Here she is.
```
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
	Load	"extmod"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 (AGP)"
	Driver		"ati"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage Mobility M3 (AGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
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

It may not be the ideal, most optimized config, but it works.

Good luck.

---

### Post by mrjohnc on 2009-03-16
Thanks a lot

That is super, I shall give it a go. So is it possible to edit xorg.conf from outside the linux desktop? If not I'm going to try starting with 5.10 and then letting it update it's self, I wonder if it will work.

Thanks again, i'll keep you posted on developments

---

### Post by thejmfc on 2009-03-16
When you start your Ubuntu up and get to the corrupted X screen, you can drop to a prompt.  Two ways for sure that I know of to do this.  You can use some combination of <ctrl> <alt> and F1 or F2 (I forget which is actually correct, this didn't work on my Pismo, but a quick search should turn up the correct keystroke).  Alternately, you can restart X with <ctrl> <alt> <delete>.  Do that enough times in rapid succession, and it'll drop you to a prompt for two minutes before retrying again.  Less than ideal, but it is how I ended up editing my file.

Actually, in the end, I just mounted my HD from the live CD with this command:

```
mount -t ext3 /dev/hda11 /mnt
```

Of course, hda11 is my linux partition, yours may vary.  If you're double-booting OS X, that might be it though.

I think that if the first method of dropping to a CLI fails, running from the Live CD is still easier than installing an older version.  Alternately, there is at least one distro of the "Rescue" variety for PPC, which is a smaller download.  The one I have is strictly CLI, but that's all you need.  Just get the HD mounted, use Nano to edit /etc/X11/xorg.conf file.  Just remember that it must be edited as root, or you won't have the permissions to save over it.  Since you're running Ubuntu, you'll have to use "sudo nano /etc/X11/xorg.conf", and then enter the admin password, etc.

Sorry if I'm stating the obvious, but I don't know what your experience level is...

---

### Post by mrjohnc on 2009-03-16
Ok thanks

What an absolute ball ache, I tried updating but no dice so I just tried a clean install on the alternative installer and it crashed half way through. I'll give it a go, i'm a rank amateur with linux but a competent follower of typed instructions. I don't really want to have to type out that behemoth by hand. 

Is there no way of booting linux and specifying 800x600 once it's installed?

Sorry I'm so basic at this, thanks for holding my hand and speaking slowly and clearly.

---

### Post by thejmfc on 2009-03-17
Okay.  I realize now that I've made this harder than it needs to be, since you'd have to type it vs. cut and paste.  I'm a little fuzzy on your current state of events (whether or not you've still got current Ubuntu installed).  If you are at that point though, or can get back to it, here's what you do.  Don't worry about the whole file that I listed.  Modify only the part that you need to see a usable screen:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 (AGP)"
	Driver		"ati"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"true"
EndSection


```

Don't change the "Identifier", since that might be referenced elsewhere in the file, and you don't want to break that link.  If your default file is like mine, it will be called "configured video device" or something.  DO change the driver to "ati", and make sure the "Option "UseFBDev" "true"" line exists.  I would assume that the BusID location of my Pismo is the same as yours also.  

If you can just get that part changed to what I've got as described above, you should have a functioning (if less than ideal) desktop.  From that desktop, you can change the whole file to what I copied above, and get things working smoother and prettier.  

FWIW, you don't want to run 800x600.  I tried giving myself that option, and it didn't work.  1024x768 works fine though, and is infinitely more usable.

Don't feel too bad about your experience so far.  Linux can be something of a challenge on a laptop, or on a Mac.  Therefore, a Mac laptop would be among the more difficult installs to get working well, especially for a newcomer to Linux.  If you can get back to the point where you were at though, and just modify the "configured video device" section, I think you'll be on the right track.  

If all else fails, I know first-hand that Debian Lenny runs on a Pismo.  Debian is, of course, what Ubuntu is based on, so it is reasonably similar.  Ubuntu tends to be slightly more up to date, and has a reputation for self-configuring things better.  I suspect that reputation is more accurate on standard Intel hardware however.  Once set up though, the experience should be similar.  I've managed to get mine working with a Broadcom wireless card, working sound, working (mostly) suspend, etc.  I kind of hope you manage to get Ubuntu working though, since I am curious how the two really compare on the PPC as far as the details go.

EDIT:  If modifying the file as described above does not work, then the next thing I would modify in the file would be the "monitor" section, followed by "screen".  In the "screen" section, the only "mode" you really need is the "Depth 24, 1024x768".  Everything else would just be lower quality.  Don't worry about this stuff unless what I suggested changing first doesn't work though.  This is just backup info, for if that fails you.

---

### Post by MJMullinII on 2009-07-20
I don't know if you still need help, but I recently found a solution to a similar problem on my Pismo.

[http://ubuntuforums.org/showthread.php?t=1208335]("http://ubuntuforums.org/showthread.php?t=1208335")

---

### Post by Firepowerforfreedom on 2009-09-26
I've got the same problem with my Pismo and 8.04.1 Hardy. I'm wondering, 
1) can you change the xorg.conf before installation [on my Pismo, it wouldn't let me save the file; I don't have permission or something], and
2) how do I install Hardy without going through the graphic install process [and I can't find those four really important files everybody says are vital to a hd boot installation].

Don't worry about trying to convince me to stay Linux. I'm not the kind of guy who gives up on a good thing just because it's hard or it's not working [I went through three old Apple laptops before I finally struck gold with this Pismo]. I've used this LiveCD on my iMac G4, though I haven't installed Ubuntu on it since it's a shared computer that would be very difficult to back up. In Ubuntu, even though everyone says the CD should be really slow, the iMac runs faster than if it were running OS X 10.4.11 Tiger. And since I've noticed Tiger on old Macs runs faster than Vista and XP on new PCs, I'm guessing Ubuntu has got to be a speed demon of OSes. I'm just dying to try it, so help me out here!

---

