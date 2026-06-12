---
title: "Enabling S-Video [Radeon 9600] on no-name laptop -- Gutsy"
date: 2007-11-09
forum: Hardware &amp; Laptops
---

### Post by GrantB on 2007-11-09
Hi, I'm trying to get S-Video working with my laptop, which has a Radeon 9600.  My laptop was bought from a Linux-only vendor (laclinux.com) a few years ago, so it's effectively no-name.  I'm using the fglrx proprietary drivers at the moment.  Just last night I upgraded from Edgy to Gutsy (probably not relevant to the problem).

**[COLOR="Red"]Details in this first post have changed.  See second post.[/COLOR]**

Problem One is that I'm not sure if my config even recognizes that S-Video is even there.  I have tried simply connecting the laptop & TV and hitting Fn-F4, which has zero effect.

I tried looking at System->Admin->Screens_&_Graphics, but there doesn't seem to be a way to configure a TV screen there.  I tried setting a generic card to 800x600 on the second monitor; when I hit "Test", the screen blanked and I couldn't get it back (blah - shouldn't it revert after some time?) and had to reboot.  I don't know where the screen contents went, but it wasn't to S-Video.

On the advice of _[COLOR="Blue"][this page]("http://www.joshgerdes.com/blog/2007/10/29/s-video-tv-out-with-ubuntu-710-on-dell-xps-m140-laptop/")[/COLOR]_, I tried
[FONT="Courier New"]xrandr --output LVDS --mode 800x600 --output TV --mode 800x600[/FONT]
but xrandr pretty much ignored the command.  Looked at the xrandr man page, but I'll admit that I don't really understand it (yet).

So now I think I need to edit xorg.conf, which I'm not looking forward to.  Can someone give me a push in the right direction?

(I've been using *nix for 10 years, but sysadmin stuff to me has always been a chore, not an adventure.)

I've pasted my xrandr and the relevant part of my xorg.conf below.

Thanks to any who can help.  (My DVD player just broke and I want to sub my laptop for it until Christmas!)

```
542 ~$ xrandr
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 1680 x 1050
default connected 1680x1050+0+0 0mm x 0mm
   1680x1050      60.0* 
   1280x800       60.0  
   1024x768       60.0  
   1400x1050      60.0  
   1280x1024      60.0  
   1152x864       60.0  
   848x480        60.0  
   800x600        60.0  
   720x576        60.0  
   720x480        60.0  
   640x480        60.0  
   640x400        60.0  
   640x350        60.0  
   512x384        60.0  
   400x300        60.0  
   320x240        60.0  
   320x200        60.0 
```

```

Section "Device"
	Identifier	"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Option		"UseFBDev"	"true"
EndSection

Section "Monitor"
	Identifier	"Laptop Monitor"
	Option		"DPMS"
	Horizsync	28-84
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Monitor		"Laptop Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1680x1050"	"1440x900"	"1280x800"	"1024x768"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1680x1050"	"1440x900"	"1280x800"	"1024x768"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1680x1050"	"1440x900"	"1280x800"	"1024x768"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1680x1050"	"1440x900"	"1280x800"	"1024x768"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1680x1050"	"1440x900"	"1280x800"	"1024x768"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1680x1050"	"1440x900"	"1280x800"	"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

```

---

### Post by GrantB on 2007-11-09
Made some progress after seeing this thread, which had similar issues.
[http://ubuntuforums.org/showthread.php?t=600091](http://ubuntuforums.org/showthread.php?t=600091)

I removed my xorg.conf (backed up) and rebooted, and my xrandr output looks much more appropriate.

```
516 ~$ xrandr
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 1680 x 1200
VGA-0 disconnected (normal left inverted right)
LVDS connected 1680x1050+0+0 (normal left inverted right) 0mm x 0mm
   1680x1050      61.1*+
   1280x800       60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right
```

I've tried these commands as directed by that thread:
```
xrandr --output S-video --set load_detection 1
xrandr --output S-video --set tv_standard ntsc
xrandr --output S-video --auto
```
but S-Video is still not working.

How do I get my machine to see S-video as connected?  It's not autodetecting when I plug the cable in.

Also, what's the relationship between xorg.conf and xrandr?  As I said earlier, I removed my xorg.conf to get my xrandr to work right, but now I lost my old xorg settings.  If I restore the old xorg.conf, will the xrandr revert to the old stupid state?

Thanks.

---

### Post by seanf on 2007-11-09
the xrandr stuff in my post worked with the open source driver, but according to your xorg.conf up there, you're using the proprietary fglrx driver.

have you tried the Catalyst GUI tool? It should be in the menu under (Applications > Accessories)

---

### Post by GrantB on 2007-11-09
I do not have Catalyst in my Ubuntu menus.  I cannot find a Linux download for it, only XP.  **[edit - never mind, I found it.  Needed to enable the prop. driver in the Ubuntu Restr Driver Mgr]**

I did, however, reinstall the ATI drivers from the ATI website.  I see no difference, except now my xrandr is "good" again and coexisting with my xorg.conf.

-Grant

---

### Post by GrantB on 2007-11-09
[deleted post. info was not right.]

---

### Post by GrantB on 2007-11-09
I've tried a bunch of things, only to end up right where I started.  Same xorg.conf and xrandr as I had in my first (not second) post.

If remove the xorg.conf, I get a decent xrandr.  The S-video still doesn't work, but at least the machine acts like it's there.  But I want my xorg.conf.

Catalyst doesn't do jack.  It just tells me there's only one screen configured.  Thanks, Catalyst!

Any ideas?

---

