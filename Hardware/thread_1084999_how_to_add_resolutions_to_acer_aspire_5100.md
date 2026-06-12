---
title: "how to add resolutions to acer aspire 5100?"
date: 2009-03-02
forum: Hardware
---

### Post by smilinggeek on 2009-03-02
I have an Acer Aspire 5100 running Ubuntu 8.10
Everything works fine right out of the box - wireless, screen, sound, etc. Heck, it even worked fine off the liveCD (which is why I chose Ubuntu, as it was the only distro that did so).

Problem:
It only offers 4 resolutions under System->Preferences->Screen Resolution

640x480, 800x600, 1024x768 and 1280x800.

I'd like to add more resolutions, since this monitor can handle more and what's available isn't adequate.

I've tried the following:
1)  sudo dpkg-reconfigure -phigh xserver-xorg
2)  booting to recovery and using xfix

Both just return after calling them, do not allow any user interaction, and both do absolutely nothing to my xorg.conf configuration file.

The xorg.conf file remains as follows:
-------------------- cut here ----------------------
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
------------------------ cut here --------------------

It seems that xorg.conf isn't used anymore to set resolutions? 

How can I add resolutions to my "Screen Resolutions" options on this laptop? Is there a tool, somewhere, that will allow me to add to the available resolutions?

Note: I have not installed the ATI/AMD proprietary FGLRX graphics driver using System->HardwareDrivers. Apart from the resolution issue, the graphics are working just fine for me without it.

---

### Post by smilinggeek on 2009-03-02
I've just tried ```
dpkg-reconfigure -plow xserver-xorg
``` and I finally get some interaction - for the keyboard. File /etc/X11/xorg.conf is still unchanged, and still no luck adding screen resolution choices to the menu.

Pointer to useful documentation (as in, RTFM) more than welcome.

---

### Post by smilinggeek on 2009-03-03
Perhaps someone can suggest a forum where the question doesn't get buried quite so quickly?  

I've done more research - nothing. Everyone says to use one of the two techniques I've tried above, neither of which actually allow me to change anything.

---

