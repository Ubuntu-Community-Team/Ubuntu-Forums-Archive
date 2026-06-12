---
title: "NVIDIA drivers + screen lock-up bug"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by guyforget on 2005-04-08
This bug is well documented over at the [nvidia support forums]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14"). There is no clear fix, though some people have been successful with any number of random combinations of "fixes." Reading the threads at the [nvidia support forums]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14") has given me the best support so far in stablizing my system.  

The easiest fix for me was to simply go back to the standard vesa drivers by specifying them in my xorg.conf. I never had any screen lockous using these drivers but I didnt have any of the nice shit that my video card was purchased to do. Actually, I dont even have a nice video card as I dont do anything specifically video intensive; but theres principals involved here, and my hardware should friggin work. 

My situation: 

Mobo: Abit IS7-V2 / Intel 848P/ICH5 Chipsets
GFX:  GeForce MX 4000
NVIDIA Driver: 7174
Kernel: 2.6.10-5-686-smp
CPU: P4 3.0 HT
OS: Ubuntu 5.04 Hoary

X just locks. Hard. Mouse pointer still moves around the screen but all running apps are locked. Keyboard is locked. System is still functioning though. If I am moving large files from one drive to another (the crash happens most often when moving large files around different hdds) the files will continue to move. If audio is playing through BMP it will continue to play. I can ssh to the box and see that X is taking up 100% cpu and I can kill it from there. I can then restart X but it will usually lock the system up completely within a half hour. Its best to reset after the first crash it seems. There are mysterious lines in syslog:

```
kernel: NVRM: Xid: 1, Channel 00000000 Method 00000000 Data 00005500
```

This bug seems to be due to the nvidia drivers specifically, but is also reported using the "nv" drivers. It is not Ubuntu specific, but is xorg + nvidia drivers specific. 

Has anyone else had any luck resolving this issue on their system?

---

### Post by jery_wang2002 on 2005-04-08
Easy, you can still use nvidia drivers
you just need to disable 
#RenderAccel  "true"

Mine works this way, but slow with antialiasing on.

Ubuntu rocks. But the problem is somewhere else. And it may not be nvidia since it also happens to ATI card too according to some in nvforums.

[QUOTE=guyforget]This bug is well documented over at the [nvidia support forums]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14"). There is no clear fix, though some people have been successful with any number of random combinations of "fixes." Reading the threads at the [nvidia support forums]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14") has given me the best support so far in stablizing my system.  

The easiest fix for me was to simply go back to the standard vesa drivers by specifying them in my xorg.conf. I never had any screen lockous using these drivers but I didnt have any of the nice shit that my video card was purchased to do. Actually, I dont even have a nice video card as I dont do anything specifically video intensive; but theres principals involved here, and my hardware should friggin work. 

My situation: 

Mobo: Abit IS7-V2 / Intel 848P/ICH5 Chipsets
GFX:  GeForce MX 4000
NVIDIA Driver: 7174
Kernel: 2.6.10-5-686-smp
CPU: P4 3.0 HT
OS: Ubuntu 5.04 Hoary

X just locks. Hard. Mouse pointer still moves around the screen but all running apps are locked. Keyboard is locked. System is still functioning though. If I am moving large files from one drive to another (the crash happens most often when moving large files around different hdds) the files will continue to move. If audio is playing through BMP it will continue to play. I can ssh to the box and see that X is taking up 100% cpu and I can kill it from there. I can then restart X but it will usually lock the system up completely within a half hour. Its best to reset after the first crash it seems. There are mysterious lines in syslog:

```
kernel: NVRM: Xid: 1, Channel 00000000 Method 00000000 Data 00005500
```

This bug seems to be due to the nvidia drivers specifically, but is also reported using the "nv" drivers. It is not Ubuntu specific, but is xorg + nvidia drivers specific. 

Has anyone else had any luck resolving this issue on their system?[/QUOTE]

---

### Post by wolovids on 2005-04-08
[QUOTE=jery_wang2002]Easy, you can still use nvidia drivers
you just need to disable 
#RenderAccel  "true"

Mine works this way, but slow with antialiasing on.

Ubuntu rocks. But the problem is somewhere else. And it may not be nvidia since it also happens to ATI card too according to some in nvforums.[/QUOTE]I disabled RenderAccel in my xorg.conf file and I haven't experienced a lock up since.  Here's the 
[bug](https://bugzilla.ubuntu.com/show_bug.cgi?id=7183) in Ubuntu's bug tracking system relating to this.  

Turning off RenderAccel isn't the best fix because window resizing is ssssllllooowww.  Hopefully Nvidia will fix this soon and there will be an update for Hoary near.

---

### Post by jery_wang2002 on 2005-04-08
[QUOTE=wolovids]I disabled RenderAccel in my xorg.conf file and I haven't experienced a lock up since.  Here's the 
[bug](https://bugzilla.ubuntu.com/show_bug.cgi?id=7183) in Ubuntu's bug tracking system relating to this.  

Turning off RenderAccel isn't the best fix because window resizing is ssssllllooowww.  Hopefully Nvidia will fix this soon and there will be an update for Hoary near.[/QUOTE]

Yeah, ssssslllllooooooooooooooooooooowwwww when I use 1600x1200 res, esp with anti-aliasing on. There is no way I turn off anti-aliasing, after looking this nice smooth clear fonts, going back to non-antialiased is no option.

---

### Post by kuleali on 2005-04-09
I have the same problem hear with x freezing. I hate that. 

Is it possible to use xfree86 in hoary insted of xorg ?

---

### Post by Mindstab on 2005-04-22
what would be better is if they let us downgrade the nvidia kernel package to one that worked :/

---

### Post by capper308 on 2005-05-02
Hi there.  I am VERY new to Ubuntu.  This is my first post.  Can someone tell me how to downgrade my nvidia video drivers. I currently have 7xxx installed and I want 6111 installed.  The reason is that I am tring to play doom3 and mohaa and I keep getting and error that opengl cannot start.  I am using Ubunty Hoary 5.04  Thanks in advance

---

### Post by rosslaird on 2005-05-02
There are at least two bugs: one involves the mouse still working while the rest of the screen freezes. Disabling RenderAccel seems to work pretty well for most people in this situation (but by no means everyone).

The second bug (which I have) involves the entire x session crashing to a black screen. The only way to fix this is to downgrade the nvidia drivers to the 6 series (both bugs are with the 7 series only). Or by going back to "nv" in xorg.conf. Ouch! And it might  not work for everyone.

There seems to be no permanent resolution at the moment, but a host of folks have complained to nvidia, so I suppose they will respond eventually.

Ross

---

### Post by nocturn on 2005-05-03
[QUOTE=rosslaird]There are at least two bugs: one involves the mouse still working while the rest of the screen freezes. Disabling RenderAccel seems to work pretty well for most people in this situation (but by no means everyone).

The second bug (which I have) involves the entire x session crashing to a black screen. The only way to fix this is to downgrade the nvidia drivers to the 6 series (both bugs are with the 7 series only). Or by going back to "nv" in xorg.conf. Ouch! And it might  not work for everyone.

There seems to be no permanent resolution at the moment, but a host of folks have complained to nvidia, so I suppose they will respond eventually.

Ross[/QUOTE]

Actually, I mailed Nvidia and got a response the same day.  I'm hit with the 'screen freeze but mouse still moves' thingie.  I disabled RenderAccel as they suggested and so far it's going well.

I do hope they get arround to fixing it though (renderaccell really helped performance).

The strange thing is that I never had any problems with renderaccel on until Xorg and Nvidia 7174 (in Hoary).  So something must have changed to cause this.

---

### Post by Jvaldezjr on 2005-05-03
I'm having the same problem, and its only produced when I have the nvidia-glx package installed.  So I removed it.  Problem solved right?  No, cause now I cant play certain games that rely on glx to run.  :(

I'll try to reinstall the drivers, and change that option in the Xorg file and see where that goes.

---

### Post by flightcrank on 2005-05-03
i have the mosue move screen frezze bug, and turning off reder execl still dosn't fix the issue !

---

### Post by Jad on 2005-05-04
I have same problem, and its really annoying,
here is my xorg.conf
```

# XF86Config-4 (XFree86 X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the XF86Config-4 manual page.
# (Type "man XF86Config-4" at the shell prompt.)
#
# This file is automatically updated on xserver-xfree86 package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xfree86
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands as root:
#
#   cp /etc/X11/XF86Config-4 /etc/X11/XF86Config-4.custom
#   md5sum /etc/X11/XF86Config-4 >/var/lib/xfree86/XF86Config-4.md5sum
#   dpkg-reconfigure xserver-xfree86

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
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
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
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

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
 	Option          "NoLogo"
EndSection

Section "Monitor"
	Identifier	"500G"
	HorizSync	30-54
	VertRefresh	50-120
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Monitor		"500G"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```
cant find a solution, please advise

---

### Post by nocturn on 2005-05-04
It's an Nvidia bug, I suggest filing a bugreport.

That said, if you have GLX, you need to comment out GLCore and DRI (although this should not cause the lock-up).

For me, disabling renderaccel did the trick, but I see that you do not have it.

---

### Post by Jvaldezjr on 2005-05-04
From what I understand, RenderAccel is on by default when the drivers are installed, it's just not listed in the X.org file for some reason.  That's what I read on an earlier thread about NVidia crashes (sorry, I dont remember where).  So you have to include it in the file to disable it I believe.  I just dont know (understand) what part of the file you need to include that switch.

---

### Post by rosslaird on 2005-05-04
"Option"     "RenderAccel"    "false"

should do it (in the Device Section)

---

### Post by Jvaldezjr on 2005-05-04
[QUOTE=rosslaird]"Option"     "RenderAccel"    "false"

should do it (in the Device Section)[/QUOTE]
 Thanks we'll see if this solves it now....

---

### Post by sgbooth on 2005-05-08
This isn't a NVidia only specific bug.  I have a ATI radeon 7000 or something really cheap and it was locking frequently.  Its good now that RenderAccel is off.

sgb

---

### Post by zki on 2005-05-09
I had same problem with hanging X (with mouse cursor still alive).
I haven't thought about the RenderAccel option, but since I've come to Ubuntu from Gentoo (with which my A64 worked well) last month I thought that it will be good to throw everything I haven't used in Gentoo out from the system. And that everything was the 'powernowd' daemon.
I have not check the RenderAccel option influence on my machine, but without powernowd it's not hanging (and RenderAccel is, and was always set to "true")
*Sorry for my surely not grammatic english.*

---

### Post by kassetra on 2005-05-21
[QUOTE=nocturn]Actually, I mailed Nvidia and got a response the same day. I'm hit with the 'screen freeze but mouse still moves' thingie. I disabled RenderAccel as they suggested and so far it's going well.

I do hope they get arround to fixing it though (renderaccell really helped performance).

The strange thing is that I never had any problems with renderaccel on until Xorg and Nvidia 7174 (in Hoary). So something must have changed to cause this.[/QUOTE]

For anyone that tries the RenderAccel solution and it doesn't work:
Downgrade your nvidia-kernel-common and nvidia-kernel-source to the 7167 release (no need to downgrade the glx) - and it should stop having hard lockups.

The nVidia forums suggests that the release after 7174 should fix this issue with Xorg 6.8.1+

---

### Post by pointym5 on 2005-06-13
[QUOTE=kassetra]The nVidia forums suggests that the release after 7174 should fix this issue with Xorg 6.8.1+[/QUOTE]

Not for me they don't.

---

### Post by munkay on 2005-06-14
I managed to cause my X not to crash anymore with the screen freeze + mouse moves bug by downgrading my NVIDIA driver version to version 6629.

Here's some instructions if you need it:

To get the driver package, use this if you have wget:
```
wget http://download.nvidia.com/XFree86/Linux-x86/1.0-6629/NVIDIA-Linux-x86-1.0-6629-pkg1.run
```

Then you need the kernel-headers package for your version of kernel. To find out your version, type:
```
uname -r
```

Then get the package for your linux using apt:
```
sudo apt-get install linux-headers-`uname -r`
```

Now you need to shut down your display manager, I use gnome so to shut down the gdm i go to one of the terminals with Alt + Control + [1-6] and then typing:
```
sudo /etc/init.d/gdm stop
```

This will stop the gdm. Now you can install the nvidia package. Go to where you downloaded the package and type:
```
chmod +x NVIDIA-Linux-x86-1.0-6629-pkg1.run
./NVIDIA-Linux-x86-1.0-6629-pkg1.run
```

The installer will then compile the kernel module for your kernel with version 6629, and after it finishes, you can restart gdm by running:
```
sudo /etc/init.d/gdm start
```

Now enable xcompmgr with whatever settings you want. Hope it works for you, it seems to work for me find. I've managed to get shadows and transparency working without problems so far using **RenderAccel** enabled.

---

### Post by rosslaird on 2005-06-15
Well, I followed the above and now X is dead...

I have tried reconfiguring the server, tried a differnet kernel, tried reinstalling the module, all to no avail.

I think that part of the problem may be that every time I reboot, the Nvidia driver does this : "Creating NVIDIA TLS Links" and I believe it links the old driver incorrectly. But when I symbolically link the 6 series driver manually to the dynamic library, that doesn't work either. (The NVIDIA module does seem to load, however; it gets an "OK" beside it at bootup.)

X is dead. I think I may have mentioned this. And I can't check the log file because every time I try to start X my whole system hard locks.

Any ideas on where to go from here?

Later:

OK, small progress. I can get a sort-of gdm screen, which tells me that the version of the driver for X (6 series) is different than the version of the kernel module (7 series). However, I did run the 6 series installer on the correct kernel, and it completed without any errors.


Thanks.

Ross

---

### Post by ritger on 2005-06-15
I had exactly the same lockup bug. It become somewhat less common after disabling RenderAccel., but it would still lock up once a week (which is still too much). After trying nearly everything (kernel boot options, downgrading etc) is went into my BIOS to see if anything there was wrong. I found a small option called `APIC Support', set to 1.4. After disabling this and rebooting into my system i haven't had a lockup in two weeks. So i'm gonna try enabling RenderAccel again and see how it'll hold up. For now, disabling APIC seems to work just fine (no weird behavior from anything using interrupts, at least, not that i can tell). Using a GeForce 2MX with the default Hoary packages for nvidia and Xorg

---

### Post by munkay on 2005-06-15
[QUOTE=rosslaird]Well, I followed the above and now X is dead...

I have tried reconfiguring the server, tried a differnet kernel, tried reinstalling the module, all to no avail.

I think that part of the problem may be that every time I reboot, the Nvidia driver does this : "Creating NVIDIA TLS Links" and I believe it links the old driver incorrectly. But when I symbolically link the 6 series driver manually to the dynamic library, that doesn't work either. (The NVIDIA module does seem to load, however; it gets an "OK" beside it at bootup.)

X is dead. I think I may have mentioned this. And I can't check the log file because every time I try to start X my whole system hard locks.

Any ideas on where to go from here?

Later:

OK, small progress. I can get a sort-of gdm screen, which tells me that the version of the driver for X (6 series) is different than the version of the kernel module (7 series). However, I did run the 6 series installer on the correct kernel, and it completed without any errors.


Thanks.

Ross[/QUOTE]

Do you have the kernel-header module for your kernel version? Also, check the nvidia website ([http://www.nvidia.com](http://www.nvidia.com)) for info about the TLS links. I remember seeing a bit there about how to get around it. Also. You have to change a symbolic link for one of the .so files in /usr/X11R6/ (I think, or some directory like that) to automatically use the 6 series of module instead of 7 series. The installer should have promoted you to create this symlink. If not, I'll try to find out the files to link/unlink.

---

### Post by rosslaird on 2005-06-15
Thanks for the feedback.

[QUOTE=munkay]Do you have the kernel-header module for your kernel version?[/QUOTE]

Yup.

>  Also, check the nvidia website ([http://www.nvidia.com](http://www.nvidia.com)) for info about the TLS links. I remember seeing a bit there about how to get around it.

That's next.

> 
 Also. You have to change a symbolic link for one of the .so files in /usr/X11R6/ (I think, or some directory like that) to automatically use the 6 series of module instead of 7 series. The installer should have promoted you to create this symlink. 

It did. The symlink is in /usr/X11R6/lib, and I have manually adjusted it probably a dozen times by now. It no longer seems to get adjusted at bootup (now that in absolute frustration I have installed the latest 7664 version), but X still will not work with "nvidia" in my xorg.conf file. It will work, however, with "nv". Believe it or not, this is a major improvement, since I can now at least get some type of X session.

Update:

More progress:

I uninstalled the nvidia driver from [www.nvidia.com:](www.nvidia.com:)

sh NVIDIA-Linux-x86-1.0-7664-pkg1.run --uninstall

I purged these packages (using "aptitude purge ...")
nvidia-glx
nvidia-settings
linux-restricted-modules-k7

Then I reinstalled them using aptitude

I am now back using X with the nvidia driver -- or, I'm back to where I started before this whole mess...


Ross

---

### Post by Deathpickle on 2005-06-17
> I had exactly the same lockup bug. It become somewhat less common after disabling RenderAccel., but it would still lock up once a week (which is still too much). After trying nearly everything (kernel boot options, downgrading etc) is went into my BIOS to see if anything there was wrong. I found a small option called `APIC Support', set to 1.4. After disabling this and rebooting into my system i haven't had a lockup in two weeks. So i'm gonna try enabling RenderAccel again and see how it'll hold up. For now, disabling APIC seems to work just fine (no weird behavior from anything using interrupts, at least, not that i can tell). Using a GeForce 2MX with the default Hoary packages for nvidia and Xorg 

For what it's worth I was running like a champ using the new drivers full options ..... the works .... until I updated my BIOS (was over a year old) and then I started having these problems. I had some controller issues before hand and have replaced the board (haven't tried to enable 3D or anything yet) but your post now makes sense as to why it worked and then didn't.

A question for the rest .... those of us getting the black screen/lock up issues what chipsets do you have? Reason I ask is I see this is not only happening to Linux but Windows user's as well and it seems to be happening to the VIA chipsets.

---

### Post by senfunn on 2005-06-17
Iam pretty new to linux ... 

I have winchester(3000+), MSI neo4 platinum (nforce4 ultra) , nvidia 6600GT (there the problem comes) .. 

I get some flashy colorful screen after booting ubuntu (both live cd and from HDD) (both IA32 and amd64 versions )

could anyone tell me by procedure what are the steps to be done to get ubuntu running .

Iam determined to use ubuntu as for the caption and will try hard to do the same .

---

### Post by ritger on 2005-06-17
Well using RenderAccel again didn't work, it locked back up again (that's my fault though, nvidia does warn that it's an experimental function). For now it seems stable again, although i'm curious to find out what APIC is actually for (google wasn't too clear on that).

[QUOTE=Deathpickle]A question for the rest .... those of us getting the black screen/lock up issues what chipsets do you have? Reason I ask is I see this is not only happening to Linux but Windows user's as well and it seems to be happening to the VIA chipsets.[/QUOTE]Yup, i have an Abit-KD7 (i think) with a VIA KT400 chipset. I also have a problem on using Xv on the tv-out of the card. That always worked fine, until the driver hit 6.xxxx, at that point Xv displays a blue line and messes up the main display. Using Xshm gets around that, although playing a movie on the tv means a 30% cpu load (instead of the 8% with Xv). It's nothing critical, but it might be another symptom.

---

### Post by neighborlee on 2005-06-21
[QUOTE=munkay]I managed to cause my X not to crash anymore with the screen freeze + mouse moves bug by downgrading my NVIDIA driver version to version 6629.

Here's some instructions if you need it:

To get the driver package, use this if you have wget:
```
wget http://download.nvidia.com/XFree86/Linux-x86/1.0-6629/NVIDIA-Linux-x86-1.0-6629-pkg1.run
```

Then you need the kernel-headers package for your version of kernel. To find out your version, type:
```
uname -r
```

Then get the package for your linux using apt:
```
sudo apt-get install linux-headers-`uname -r`
```

Now you need to shut down your display manager, I use gnome so to shut down the gdm i go to one of the terminals with Alt + Control + [1-6] and then typing:
```
sudo /etc/init.d/gdm stop
```

This will stop the gdm. Now you can install the nvidia package. Go to where you downloaded the package and type:
```
chmod +x NVIDIA-Linux-x86-1.0-6629-pkg1.run
./NVIDIA-Linux-x86-1.0-6629-pkg1.run
```

The installer will then compile the kernel module for your kernel with version 6629, and after it finishes, you can restart gdm by running:
```
sudo /etc/init.d/gdm start
```

Now enable xcompmgr with whatever settings you want. Hope it works for you, it seems to work for me find. I've managed to get shadows and transparency working without problems so far using **RenderAccel** enabled.[/QUOTE]


I downgraded to 6629 and i'm stil getting lockups..

yesterday I tried to start: 'run as different user' dialogue from menu and before I could type in anything bam X locked on me..

I tried to 'restart' from ctrl-altF1 I think it was, and cupsd hung on trying to stop that service...

just an fyi in case it helps someone diagnose this mess

cheers
nl

---

### Post by m0ns00n on 2005-10-10
I think the Nvidia drivers are just buggy. In a way its not the ubuntu developers fault.. But it is aggrevating that the last working driver for the cards to and pre GeForce 4000 MX is 1.0.6111... It's very old now. Who knows why they can't make decent drivers, it's beyond me. Perhaps they should hire some better low level programmers.

Anyhow - I guess it's time to upgrade my hardware soon. I'm just a bit afraid of this happening again - ending up with an unsupported app. If you look at it another way, the Ubuntu developers are wrong to set a version on the nvidia drivers. Each version should have their own subversion with which patches they are given so that they could be upgraded - if somebody needed new drivers, they'd just specify the version they wanted. This way, I could still use the 1.0.6111 drivers and live with an accelerated desktop..

---

### Post by tseliot on 2005-10-10
[QUOTE=m0ns00n]Who knows why they can't make decent drivers, it's beyond me. Perhaps they should hire some better low level programmers.[/QUOTE]
It's obvious that Nvidia uses most of its resources for its Windows drivers (its main market).

---

### Post by pHr34kY on 2007-02-03
I'm getting the same problem. I disabled 'RenderAccel' and this seemed to improve the stability. However one I switch on XGL/Beryl the lockups start to come back.

I'm using a GeForce3 Ti200 (NV20)... So this bug still exists in the nvidia-glx-legacy package.

Oh, and the S$&#@ down at Nvidia decided to move the NV20 from the nvidia-glx package to nvidia-glx-legacy, so after a dist-upgrade the damn video stopped working and it took me a week (seriously!) to figure it out!

Anyway, I feel there's an improvement with RenderAccel disabled, but it's not a 100% effective fix. Or maybe I should stop thrashing my little GeForce 3 every chance I get :)

---

### Post by syberdave on 2007-03-09
I have a NVIDIA Go 6500 on my laptop.

Fluxbox without RenderAccel = Stable
Fluxbox with RenderAccel = Stable
Beryl with RenderAccel = Screen freeze
Beryl without RenderAccel = Stable


I've noticed that when I'm in screen-freeze mode, all the clicks are as if the ALT button was held down. However, the keyboard is unresponsive.

---

### Post by db0 on 2007-03-13
> **rosslaird said:**
> "Option"     "RenderAccel"    "false"

should do it (in the Device Section)

Sorry for being unnecessarily dumb but I put this on the xorg.conf in the device section and X would not start. I removed the quotes around Option and X started but I did not see any difference in the window rendering and the system still freezes (In my case it's a hard freeze. No mouse move, nothing running. Sometime the music from amarok continues playing until the current song ends, sometimes not)
Am I putting the option correctly?

```

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Driver         "nvidia"
    Option	   "RenderAccel" "false"
EndSection

```

---

### Post by varchar255 on 2007-07-09
I used to have this problem pretty often and I tried the RenderAccel which seemed to help. However, X will still sometimes freeze when the screensaver is running. It doesn't happen every time though but when it does, I can't Ctrl+Alt+Backspace or anything else, I must reboot.

---

### Post by brettryan on 2007-07-28
Hi guys, I'm having the same sort of problem, except my machine just completely freezes without warning and I have to hit the reset button, trying to ssh or ping the machine realises that the host has completely locked up.

On occasion the system would act slow prior to this but I'm not really sure, the system is usually not under any stress.

Here is some suspicious activity in kern.log, but I'm not sure the system gets time to actually write anything most times.

[ 2378.334301] NVRM: Xid (0003:00): 26, Ch 000001ff M 00001ffc D ffffffff intr ffffffff
[ 2378.465921] NVRM: Xid (0003:00): 1, Ch 000001ff M 00001ffc D ffffffff intr ffffffff
[ 2387.450943] NVRM: Xid (0003:00): 16, Head 00000000 Count 00071908
[ 2395.440482] NVRM: Xid (0003:00): 16, Head 00000000 Count 00071909
[ 2403.430042] NVRM: Xid (0003:00): 16, Head 00000000 Count 0007190a
[ 2408.423540] NVRM: Xid (0003:00): 8, Channel 00000000
[ 2421.406559] NVRM: Xid (0003:00): 16, Head 00000000 Count 00071aec
[ 2424.402658] NVRM: Xid (0003:00): 8, Channel 0000001e
[ 2689.266497] NVRM: RmInitAdapter failed! (0x12:0x2b:1569)
[ 2689.266509] NVRM: rm_init_adapter(0) failed
[ 2695.379266] NVRM: RmInitAdapter failed! (0x12:0x2b:1569)
[ 2695.379279] NVRM: rm_init_adapter(0) failed
[ 2701.463836] NVRM: RmInitAdapter failed! (0x12:0x2b:1569)
[ 2701.463850] NVRM: rm_init_adapter(0) failed

Hardware: configuration:
Motherboard: Asus A8N-VM CSM with AMD 6800+ X2
RAM: ubuntu mem test revealed 1GB of my ram could be causing problems so now only using 1GB
Graphics: Nvidia 7300 512MB
Graphics Driver: NVIDIA-Linux-x86_64-100.14.11
Kernel: 2.6.20-16-generic

Apart from that my system doesn't have much else in it.

-Brett.

---

### Post by hackeron on 2007-11-09
Similar problem here, X freezes (ctrl+alt+backspace does nothing) - I also tried to ssh and killall -9 Xorg - Xorg cannot be killed and carries on consuming 100% cpu.

This is what I see in dmesg:

[   52.804000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
[54257.404000] spurious 8259A interrupt: IRQ15.
[65995.616000] NVRM: Xid (0005:00): 26, Ch 000001ff M 00001ffc D ffffffff intr ffffffff
[65995.660000] NVRM: Xid (0005:00): 1, Ch 000001ff M 00001ffc D ffffffff intr ffffffff
[65995.708000] NVRM: Xid (0005:00): 6, PE01ff 1ffc ffffffff 00000000 00000000 00024040
[65995.764000] NVRM: Xid (0005:00): 6, PE0000 040c 00efedea 00000000 00000000 00024040
[65995.884000] NVRM: Xid (0005:00): 6, PE0000 040c 00efedea 00000000 00000000 00024040

Didn't have this happening with older versions of the nvidia drivers :(

---

