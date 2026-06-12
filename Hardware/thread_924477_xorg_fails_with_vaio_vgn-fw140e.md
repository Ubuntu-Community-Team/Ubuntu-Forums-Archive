---
title: "xorg fails with vaio vgn-fw140e"
date: 2008-09-19
forum: Hardware
---

### Post by scottied on 2008-09-19
The Sony Vaio FW140e uses Centrino2 Montevina graphics, specifically Intel's gm45. Everything seems to be detected fine when Ubuntu 8.04 to Intrepid beta 6. 

Xorg fails to load correctly however. The screen is white with flowing gray blobs. When I examine xorg's log file, it correctly identifies the Intel gm45 graphics as well as the settings for my monitor. I even hear Ubuntu's gdm greeting sound.


Any recommendations? Would building intel drivers from git get me anywhere? Is this a known issue?

Thanks!

---

### Post by Crafty Kisses on 2008-09-19
Try this command to start the GDM:
```
sudo /etc/init.d/gdm start
```
If that doesn't work try the following command:
```
startx
```
Let's just see if you get different results with different things. If all else fails try reconfiguring X, you can do that by doing the following:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by tamagotono on 2008-09-19
Scottied,
  There is already a couple of discussions about this.  Please see the following:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=889323](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=889323)
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=903182](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=903182)


I am running the same laptop with the same results.  The only difference I can see is that I am running Kubuntu Intrepid Alpha 6.
You can use the VESA drive and get 1024x768 or keep the INTEL driver and use an external display.  I have tried the VGA port and it works fine with the Intel driver and I am going to get a DVI to HDMI cable to test that port out as well.
  Best of luck and lets keep everyone informed if we find any tricks or tips to get this problem fixed.
by the way, I did file a bug report on this.  It would help if you would confirm this bug and post your Xorg.0.log file too.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/268036](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/268036)

---

### Post by ponar on 2008-10-20
I have a Sony VGN-FW140E with the exact same issue. I've install the latest 8.10 Beta, compiled the latest intel drivers (2.4.2), updated the kernel, all to no avail.

It works great when I connect an external monitor to the VGA output of the laptop, but the built-in display refuses to work with anything other than vesa mode.

Has anyone got this thing to work yet?

---

### Post by goshock on 2008-10-22
I just got this laptop, and am new to ubuntu, but I found on the gentoo forums that it will work with:

# xf86-video-i810-2.4.2-r1
# mesa-7.2
# xorg-x11-7.4 

at least for 2D graphics.  I don't know when I'll get the time to tinker with this to see if works, but hopefully this will help someone.

---

### Post by ponar on 2008-10-22
That's great. I'll give it a try and let you know what I find. Could you send a link to the forum post you're referring to? Thanks!

---

### Post by smoosh on 2008-11-03
Any word on this?  Everything else works on my Sony, but it's kinda hard to use at 800 x 600....

---

### Post by slayerdme on 2008-11-04
You can get a higher resolution with the vesa driver. Just edit the /etc/X11/xorg.conf file correspondingly. (from terminal: gksudo gedit /etc/X11/xorg.conf)

here is mine (was, tried a few other stuff which did nothing new):
Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"Monitor"
	Driver		"vesa"
#	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync	30-75
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1600x900" "1440x900" "1280x1024" "1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x900" "1440x900" "1280x1024" "1280x800" "1024x768" "800x600"
	EndSubSection
EndSection


Btw..any progress? can't get the xf86-.. driver to work for me.. i tried the 2:2.5.0 xserver-xorg-video-intel driver but nothing new - same white screen slowly fading
Please anyone help? I am willing to give people full access to my computer in order for this issue to be fixed. (Remote desktop or something? Or maybe LA/Pasadena?)

---

### Post by smoosh on 2008-11-05
Thank you!

I had the vesa driver in there before, but for some reason, it only gave me 1024x768 for my first login, then defaulted to 800x600, but now it stays at 1024x768, which is waaaay better, for now.

---

### Post by dwestbrooks on 2008-11-11
Has anyone been able to figure this out yet?  I just bought the FW140E last week, and am having the same issue.  I can't even get Ubuntu 8.10 installed because I get white/black screen before the install disk boots up. On most forum topics related to this issue (FW140E and Intel GMA 4500m graphics chip), the topic has seemed to have died. Does that mean that there is a solution out there that I just haven't found? I'm really missing Ubuntu right now.:) Thanks for your help in advance.

---

### Post by smoosh on 2008-11-11
To install, hit f8 (?) during boot from the install disk, or whatever it says to hit for install options, then choose "failsafe mode".  This will install using low graphics.  Then, when it's installed, and you restart your computer, hit "esc" at the prompt, and choose "recovery mode".  Then edit your xorg.conf as suggested above in this thread.  Then reboot and you will have insanely amazing 1024x768 fuzzy graphics that show no hope of getting better!  Yaaaaah!   Hope that helps!

---

### Post by smoosh on 2008-11-12
Allright, permanent solution: Spend the loot to get a fw-139e (uses supported ATI graphics card), and sell the fw-140e.  That is what I'm doing because I can't stand the crappy resolution anymore.  Check the auction sites, you can get a 139e for under 900 bucks, and you should be able to sell the 140e for at least 800... worst case.  I got lucky and found one for cheaper because Win-doze wasn't installed, so I should break even...........

---

### Post by igknighted on 2008-11-12
The bug is being worked on by the intel devs right now (read the thread in the bug report on freedesktop.org).  I would hang on to the 140, because in the long run you will have a supported OSS driver that wont have support dropped in a couple years when ATI moves on to something new.

---

### Post by smoosh on 2008-11-12
Hmmm, I see your point, but it just doesn't look like it will be resolved anytime soon.  Every time (and it has been MANY times) I go to the bug page to see the progress it says the same thing, which is NEEDINFO under the keyword and doesn't appear to have changed at all in the last few weeks...  But, of course, as soon as my ATI machine arrives, the Intel bugs will probably magically dissappear.  I guess I'll keep them both for a spell and see if it gets worked out...

Thanks for the insight!

---

### Post by NotoriousMOK on 2008-11-12
> **Codename said:**
> Try this command to start the GDM:
```
sudo /etc/init.d/gdm start
```If that doesn't work try the following command:
```
startx
```Let's just see if you get different results with different things. If all else fails try reconfiguring X, you can do that by doing the following:
```
sudo dpkg-reconfigure xserver-xorg
```

The last part fixed this problem for me, though I don't recall answering any video related questions (mostly keyboard).  Got all my resolutions, and desktop effects are working good too -- thanks a bunch!

Sony Vaio VGN-NS135E (x3100 integrated video)

---

### Post by smoosh on 2008-11-12
What's the resolution on your screen?  I think the issue with the FW series is the 1600x900 screen, only used by Sony...

---

### Post by NotoriousMOK on 2008-11-12
ah, mine only goes to 1280x800, which is max for my card

---

### Post by dwestbrooks on 2008-11-13
I considered buying the Sony Vaio VGN-NS135E, but my last laptop had an ATI Xpress 200m card and had issues with it on any Linux distro I tried. I know it was just that card's compatibility, but it still scares me away from using any ATI card with Ubuntu. Hopefully they'll get this bug worked out soon. For now I'm stuck with fuzzy 1024x768 resolution on a nice 1600x900 screen. I'll keep telling myself it's great until then......if that happens.

---

### Post by smoosh on 2008-11-14
Well, got my fw-139e today, and the only thing that does not work is the screen brightness adjust!  The 1600x900 works great, wireless, etc.  I know it's better to wait for the open source Intel driver to get patched and glued back together, but dang, ya'll...  Just sayin.

---

### Post by smoosh on 2008-11-20
So... I hung on to the FW-140E to see if there would be any progress with the open source intel drivers, and it looks like a few people with know-how have gotten it working by adding "if (!on) return;" (with no quotes) to line 289 of xf86-video-intel-2.5.0/src/i830_lvds.c!  

If anybody knows how to compile a driver, this apparently works.  You download the 2.5.0 driver, add that one line of code, compile and install it.

Anybody that knows how to compile a driver feel like letting the rest of us in on it? I want to get this thing working so I can sell the FW-139E and not have a negative bank account...

If you want to check out the progress for yourself, here is the link - scroll most of the way down: [https://bugs.freedesktop.org/show_bug.cgi?id=17292](https://bugs.freedesktop.org/show_bug.cgi?id=17292)

---

### Post by JunCTionS on 2008-12-09
I just installed Intrepid Ibex on a VAIO VGNFW270.
The liveCD didn't load at first so I tried it in Safe Graphics Mode.
I've tried several things but none worked.
I wanted to know if I could have a look-see at your xorg.conf and your xrandr -q outputs (those of you that have a working 1600x900 monitor) so that I can copy the numbers there.
Thanks!

---

### Post by JunCTionS on 2008-12-12
I found help for my exact model (no this one) [on this thread]("http://ubuntuforums.org/showthread.php?t=996395").
I only had to install the new intel drivers which are patched.
In my case I used the 64bit version.

[daniel in launchpad]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/268615") was nice enough to compile them.
Here they are (the 64-bit version of the drivers): [http://launchpadlibrarian.net/203928...0driver.tar.gz](http://launchpadlibrarian.net/203928...0driver.tar.gz)
Just install the three files in there (they replace the old intel ones so no need to uninstall them) and then change "vesa" for "intel" and then restart the X Server (Close and save anything important then press "Alt+Ctrl+Backspace" which will also log you out or reboot).

If you have the 32bit version the procedure is the same (although binaries come with the code, so just install the .deb files) this is the fix: [http://launchpadlibrarian.net/19868825/intel%20driver%20fix.tar.gz]("http://launchpadlibrarian.net/19868825/intel%20driver%20fix.tar.gz")

Be aware that smoosh reported some problems with the fw-140e if I'm not mistaken.

---

### Post by smoosh on 2009-01-04
That was the computer I believe - the same thing happened when I re-installed windows.  I am just sticking with the fw-139e, I have had zero problems with it...

---

