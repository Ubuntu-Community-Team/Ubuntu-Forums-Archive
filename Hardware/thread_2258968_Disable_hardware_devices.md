---
title: "Disable hardware devices"
date: 2014-12-31
forum: Hardware
---

### Post by Irrationalis on 2014-12-31
Hello all,
I am turning an old iMac (Ubuntu 12.04.5 LTS CLI only) that I have into a headless (ssh) Plex Media Server.
Because this machine will be running 24/7, I need to disable as much hardware (usb,firewire,display,audio,cd drive, etc) as I can (including the display drivers if possible) in order to save power. 


How can I disable these devices?

---

### Post by weatherman2 on 2014-12-31
The amount of real-world power you're likely to save by disabling stuff in software is negligible.  It seems from your other thread that you have gotten WOL to work anyway - that's certainly the way to go to reduce power use over time.

I've never put a Mac on a watt meter, but a typical Core 2 Duo PC would consume (at idle) only maybe 40W-60W depending on what hardware you have attached to it.  It seems you have an integrated video card too which means it will consume less.

You should make sure any hard drives attached will power down at idle after a certain period of idle time.  That will save maybe 3-4 watts.  But this may happen automatically anyway.

---

### Post by Irrationalis on 2014-12-31
Thanks for the input. So, theoretically speaking, for a non AIO pc, it would be more efficient to physically remove the devices rather than disable them?

Also, how could I set or check the status of the drive's power?

Edit: I would actually like to disable the display driver, but not for power reasons; the display is a little annoying when the room is dark.

---

### Post by weatherman2 on 2014-12-31
If a device can be completely disabled in software, then you would be able to save the same amount of power vs. removing it.  But I doubt the kinds of devices you'd be removing can be completely disabled in software.  (What would you remove, anyway, that you don't really need?)

You need some kind of display driver going to boot the OS.  This is an iMac with a built-in screen?  Otherwise, why do you need the screen on?  There may be tricks to blank the display.  If you are using it as a server but have a "desktop Ubuntu" OS installed, you can tell it to blank the screen after one minute fairly easily, in power settings.

---

### Post by Irrationalis on 2015-01-01
I don't have x server or any DE installed. How could I blank the screen from the command line?

---

### Post by tgalati4 on 2015-01-01
Mac's tend to draw more power than PC's of similar specifications because they use higher-performance bus chipsets and higher on-board graphics.  So, other than cutting traces on the motherboard for stuff that you don't want to power, your best bet is WoL and put a wake-up app on your phone or tablet or some WoL launchers on your laptops.

If you have a separate graphics card, then pull it out.  You should be able to boot a headless server without a graphics card--although with Mac hardware everything is difficult.

---

### Post by Irrationalis on 2015-01-02
Alright, I understand what I need to do power-wise, but what about the "screen-blanking" previously mentioned above?

> If you are using it as a server but have a "desktop Ubuntu" OS  installed, you can tell it to blank the screen after one minute fairly  easily, in power settings.

Is it possible to accomplish this from the command line without an x server or DE installed? I want to do this not for power reasons, but because it is annoying when the room is dark.

---

### Post by Yellow Pasque on 2015-01-03
I don't know much about Macs, but on my mobo, I can disable a lot of things in the BIOS (audio, firewire, USB, etc.). Whether that saves significant power I don't know..

---

### Post by Irrationalis on 2015-01-08
Alright, I understand what I need to do power-wise, but what about the "screen-blanking" previously mentioned above?

>  	 		 			 			 				If you are using it as a server but have a "desktop Ubuntu" OS   installed, you can tell it to blank the screen after one minute fairly   easily, in power settings. 			 		

 	
 


Is it possible to accomplish this from the command line without an  x server or DE installed? I want to do this not for power reasons, but  because it is annoying when the room is dark.

---

