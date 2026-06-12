---
title: "Dead Laptop display - Want to force external monitor use"
date: 2008-03-25
forum: Hardware &amp; Laptops
---

### Post by flyboy771 on 2008-03-25
I'm trying to resurrect an old Dell Inspiron laptop.  The main panel is dead.  It lights up and displays something I know is related to whatever its input is, but there's no way to read what it says or make any sense of it.  In any case, I want to convert it to basically a compact desktop computer, in essence, a laptop that HAS NO main panel, only an external monitor.

So I boot from the LiveCD, attempting to install Ubuntu 8.04 Beta (I'll be repeating this later when the stable version is released), and the external monitor works fine until "Loading Gnome" then goes blank.  The GUI works... sort of, on the main panel.  I know because I am at least occasionally able to make out a word or two of text and recognizable graphics (like a yellow triangle exclamation point icon with some sort of message referencing the time zone or clock settings).  But literally, that's all I can see, and it only lasts for a few seconds before the picture fades into digital noise.  Not enough to get thru an installation routine, at any rate.  I can hit CTRL+ALT+F1 to bring up the command line, but I have no idea what to do from there.

The under-workings of Linux are pretty alien to me, as I'm the kind of user that likes the new user-friendly GUI's and increasing ability to just install and use.

I need two things:

1.  Force the GUI to the external monitor (might need to force the resolution and refresh rate to 1280x1024x60Hz) long enough to install the OS and boot it successfully.

2.  Configure something, once it's installed, to default to the external monitor every time, without user intervention.  I'm setting this up for my sister's son who really needs it to "Just Work".  Ubuntu is a perfect OS for him, because all he needs is a word processor and basic Internet, not to mention it's free.  I could use an older version of Ubuntu if necessary, I just figured I'd start with the latest and greatest as a baseline.

Thanks in advance!

All the system specs I know:
Dell Inspiron 8000
Intel PIII 1Ghz
512MB RAM
DVD-ROM drive
16MB ATI Mobility M4 graphics
Unknown chipset
3Com mini-PCI combo v.90 modem and 10/100 Ethernet

---

### Post by flyboy771 on 2008-03-26
Okay, so I got the LiveCD to boot with what I believe is the graphics on the external monitor, unfortunately, it's using a default mode that my monitor (and my HDTV, and two other monitors in the house) isn't capable of supporting.

I tried:

sudo nano /etc/x11/xorg.conf

but only come up with a blank file.  Is there another location where I can tweak the refresh rate (or set a different default on startup) besides that (apparently missing, at least in the LiveCD session) file?

---

### Post by Whiffle on 2008-03-26
should be 

/etc/X11/xorg.conf

case sensitive...

Also, some laptops have a button on the keyboard that switch the outputs around, i have an old compaq that does that.

---

### Post by tgalati4 on 2008-03-26
Normally there is a setting in the BIOS to activate the native display or the external display or both.  You need to find someone with a similar laptop so that you can walk through the BIOS blindly and try to select the external display.  

Once selected in BIOS, they you should be able to use a standard VGA monitor to perform your install.

---

### Post by flyboy771 on 2008-03-26
Thanks for the heads up on the case sensitive.  Since that post, the panel strangely started working again when I tried an OEM pre-install.  I'm not sure if that had anything to do with it or not, as I was just trying to find some setting that wouldn't cause the external LCD panel to complain "Out of scan range.  Invalid Mode"

I haven't actually had a need to manually edit the xorg.conf file yet, because the panel started working (sort of... the back light doesn't work, but if I hold a really bright flashlight just right, I can read about one square inch at a time of screen space)

I can access the BIOS just fine, since the BIOS and all text based command line interfaces (ie, CTRL+ALT+1..12) display perfectly fine on the external monitor.  This particular BIOS does not have any sort of display override.

The key combination, Fn+F8 in this case, that toggles between LCD, CRT (external) and Both works in some environments, and not others.  For instance it seems to work just fine when in the BIOS, but within Gnome (where it's really needed) it doesn't seem to do anything.

For a while I actually managed to get a dual monitor setup going.  It appeared to only work sporadically, so I experimented with leaving the system in different states when Gnome loaded, because during the Ubuntu splash screen (with the orange progress bar) segment of boot, my Fn+F8 key worked to switch display modes.  Unfortunately after several attempts and mostly "Ubuntu is running in reduced graphics mode, do you want to reconfigure?" messages, I couldn't get any multi-monitor setup to work again.  In other words, I couldn't reproduce what I had before.

I still have not been successful (even accidentally) in getting ONLY the external monitor to work at it's proper resolution.  If I pre-set the display selector (with the keyboard, during the first stage of booting) to use only the external monitor, it keeps coming up with "Cannot detect displays.  Running in reduced graphics mode" or something to that effect.  It doesn't seem to want to preserve the settings when in external only mode.

---

