---
title: "Inspiron 7500 problems"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by Thomvis on 2005-04-22
Hi people!

I downloaded Ubuntu 5.04 yesterday and installed it right away. The installation process went well and i was very happy to discover installing Ubuntu wasn't very difficult.

Before I installed Ubuntu I tried the live cd. Everything was working fine: network, display etc. But now, whith ubuntu installed i can't start the x server! This is exactly the problem i was having with Fedora Core 3 (and so i switched to suse9.0, but i dont like that one). I tried some configurations and reconfigured the xorg-server with the tool named in xorg.conf.  But i'm not a linux hero so i can't solve it! :( Btw i'm using a Dell inspiron 7500.


I hope someone can help me! Thanks in advance,

Thomas

---

### Post by heimo on 2005-04-22
Useful information, you could post, is output of lspci, Monitor, Device and Screen parts of xorg.conf (see the thread below) and the whole /var/log/Xorg.0.log attached or linked (not inline, please).
 
Some information about configuring xorg.conf on this thread:
[http://www.ubuntuforums.org/showthread.php?t=21984]("http://www.ubuntuforums.org/showthread.php?t=21984")

---

### Post by Thomvis on 2005-04-22
ok, i will attatch the log files soon. Right now i'm reinstalling Ubuntu because the xserver worked for a very short time after the very first Ubuntu boot. And because i didn't see the boot process I restarted the pc using the gdm reboot button and after that.. i never saw x again! Maybe it 'll work after this install. I'll keep you informed..

---

### Post by Thomvis on 2005-04-24
I made some advances in one day:  At the moment i have X op and running using the vesa drivers but that's not satisfying: i can't use the resolution i want (1400x1024), it's stuck at 1280x1050 and that's quite ugly and out of proportion. And even if i delete all the resolution settings in the xorg.conf and enter 1400x1024 for every mode it still runs at 1280x1050; is this a driver maximum?

To double check if my hardware is compatible i ran the Ubuntu Live CD. And everything went above expectations! My resolution was 1400x1024 and the view was cristal clear. :) So i was happy and thought i found the right configuration. I copied the xorg.conf from the virtual filesystem made by the live cd to my own /etc/X11/xorg.conf. You can find the [xorg.conf file here](http://62.166.35.187/linux/xorg.conf).
But when i restarted the xserver with this configuration it didn't work! The screen went blank but didn't hang because i could login and hear sounds.
I dont' understand it :( I inspected the Xorg.0.log file but it was like Chinese to me ;) I hope one of you can understand the[Xorg.0.log file](http://62.166.35.187/linux/Xorg.0.log).


Thanks in advance!
Thomas

ps. excuse my english, i'm dutch and 17 years old

---

### Post by heimo on 2005-04-24
Hi!

I don't have experience installing Ati drivers, but here's a howto:
[http://www.ubuntuforums.org/showthread.php?t=22496]("http://www.ubuntuforums.org/showthread.php?t=22496")

I think using vesa driver means sticking to a list of predefined standard vesa video modes and to my knowledge 1400x1050 is not included. I assume you mean 1400x1050 as that's 4:3. (btw, that's the resolution I'm using on my old 19" CRT, with nv and nvidia drivers)

So, you'll need those ati drivers installed to get 1400x1050 resolution and 3D acceleration, which is what you most probably want to do.

 >  ps. excuse my english, i'm dutch and 17 years old 
If you had said you're from United Kingdom and work as English teacher, I would have believed. :) Your English is fine.

But your Xorg.0.log is invisible. ;)

---

### Post by Thomvis on 2005-04-24
[QUOTE=heimo]But your Xorg.0.log is invisible. ;)[/QUOTE]
I edited my post completely and added the Xorg.0.log (forgot it :whistle:)
I allready tried to install the ati drivers but that didn't work, the x server even wasn't able to start and crashed. But i will try again and post my experiences.
And yeah it's 1400x1050, oops :) it's good in the xorg.conf file so that can't be the problem. thank you!

---

### Post by heimo on 2005-04-24
This is a long shot, but I'd try commenting out couple lines in Monitor section (seems to detect those automaticly):
 ```

Section "Monitor"
		Identifier	  "Generic Monitor"
		Option		  "DPMS"
#		HorizSync	   30-75
#		VertRefresh	 50-85
EndSection

``` 

And editing Screen mode to:
 ```

Section "Screen"
		Identifier	  "Default Screen"
	 Device		 "ATI Technologies, Inc. Rage Mobility P/M (AGP)"
		Monitor		 "Generic Monitor"
		DefaultDepth	24
		SubSection "Display"
			 Depth		 24
			 Modes		 "Native panel mode"
		EndSubSection
EndSection

``` 

Why would I try this? Because this is what I found in the log file:

 ```

(**) ATI(0):  Default mode "1400x1050": 122.0 MHz, 64.9 kHz, 60.0 Hz
(II) ATI(0): Modeline "1400x1050"  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync
(**) ATI(0):  Built-in mode "**Native panel mode**": 107.9 MHz, 76.2 kHz, 72.4 Hz
(II) ATI(0): Modeline "**Native panel mode**"  107.86  1400 1400 1408 1416  1050 1050 1051 1052
(**) ATI(0):  Default mode "1280x1024": 157.5 MHz, 91.1 kHz, 85.0 Hz
(II) ATI(0): Modeline "1280x1024"  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync


```

Here's link to specification sheet of your laptop (mostly just for me when I come back to this thread, but maybe useful for others too):
[http://support.dell.com/support/edocs/systems/psyd/specs.htm](http://support.dell.com/support/edocs/systems/psyd/specs.htm)

---

### Post by Thomvis on 2005-04-24
thanks for your suggestions. But it still doesn't work. As far as i understand the 
[log file](http://62.166.35.187/linux/atilog.txt) it looks perfect: my lcd panel is detected and the right resolution is used; BUT i don't see a thing. The next thing i should try is if maybe the external monitor get some signals. I'll try and find a external monitor and post my findings.

edit: i've to go so i can't try your suggestions immediately. I'll be back in the evening so i can try some other options then or tomorrow. Thanks very much :)

---

### Post by heimo on 2005-04-24
Here's old thread on Warty forum about similar problem with Ati Rage mobility chipset:
[http://www.ubuntuforums.org/showthread.php?t=1382]("http://www.ubuntuforums.org/showthread.php?t=1382")

Also try 16-bit colordepth (change defaultdepth and subsection).

Yes, your config and log files look fine. Trying external monitor is a good idea. Remember to change signal output with Fn + F7 or F10 or where ever the monitor symbol (rectangle inside rectangle) on your laptop keyboard is.

EDIT: Run *lspci* and check that the line with your graphics card matches BusID in device section. It looks to be fine, but someone on this forum earlier reported inconsistency between Xorgs detection and [i]lspci.

[/i]Here is list of problems encountered by other Ubuntu / Inspiron users:
[i][http://www.ubuntulinux.org/wiki/HardwareSupportMachinesLaptopsDell](http://www.ubuntulinux.org/wiki/HardwareSupportMachinesLaptopsDell)

[/i]I don't know if your card is suppoted by fglrx driver, but here's howto:
[i][http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)

[/i]

---

### Post by Thomvis on 2005-04-24
Ahhh!! :D:D problem solved! Thank you very very much; ubuntu looks a lot nicer in the  right proportions ;)
This is what i did:
- added vga=791 tot the kernel argument in /boot/grub/menu.lst;
- limited the Vrefresh to 58-62

And now i have the ati drivers up and running at a 1400x1050 resolution :D
thank you very much and see you around!

Thomas

---

### Post by heimo on 2005-04-24
Great news!

So do you use ati or fglrx driver?

> 
thank you very much and see you around!  You too! :D

---

### Post by Thomvis on 2005-04-24
i use the ati driver wich came with ubuntu :)

---

### Post by heimo on 2005-04-24
[QUOTE=Thomvis]i use the ati driver wich came with ubuntu :)[/QUOTE]

Great! Thank you, this information can come handy to others in similar situation.

---

### Post by mmrobins on 2005-05-11
Thanks Thomvis, this helped me out a lot.  I installed Ubuntu 5.04 and it worked fine until I rebooted it, then it just came up with a black screen every time.  Adding vga=791 fixed it all though.  Thanks again!

---

