---
title: "Satelite 4090CDS success"
date: 2004-11-04
forum: Hardware &amp; Laptops
---

### Post by jwenting on 2004-11-04
This is the first time I've gotten any Linux to run on this machine without trouble, congrats on that. 
Installation took a few hours (slow CD and CPU  :-( ) but everything works fine after just one small tweak to the videosettings.
[http://www.superaje.com/~andreas/4070cds-xf86config-4.txt](http://www.superaje.com/~andreas/4070cds-xf86config-4.txt) cures a problem with the refresh rate of the screen, just taken the following sections and updated the generated file accordingly:
Section "Device"
	Identifier	"Trident 9525"
	Driver		"trident"
	BusID		"PCI:00:04:0"
	VideoRam	2048           # this line to be added
	Option		"noaccel"   # this line to be added
EndSection

Section "Monitor"
	Identifier	"Toshiba LCD"
	HorizSync	31.5-53.7    # this line different!
	VertRefresh	60	# this line different!
	Option		"DPMS"
EndSection

Now if only I can get rid of the "NT_ACCESS_DENIED" error when  trying to print to the HP970Cxi on my main computer all will be well  [-o< 

I won't hear "just install Linux on the main machine" as that's simply not an option.
I do customer support and beta testing for Microsoft Flight sim addons which obviously require a Windows machine to work  :mrgreen: as well as some Windows development (Delphi, C++) and building websites requiring testing them in IE.

I'm not religiously for or against anything, for me Linux is a way to keep alive the Unix skills I need at work more than anything (and to play around with Unix development as well, coding is a disease I'll probably never be cured of).

---

### Post by mip on 2004-11-10
[QUOTE=jwenting]This is the first time I've gotten any Linux to run on this machine without trouble, congrats on that. 
Installation took a few hours (slow CD and CPU  :-( ) but everything works fine after just one small tweak to the videosettings..[/QUOTE]

Which method of installation did you use? I have one of these laptops but I've had problems installing ubuntu on it.

---

### Post by mip on 2004-11-11
I've managed to get Ubuntu installed but I'm having some problems with X. I have a fuzzy bar across the bottom of the screen. I have tried making the changes suggested to xf86config-4 but to no avail. Is there anything else I have to do apart from making the changes to the file?

---

### Post by jcordone on 2006-11-04
What I have had to do in the past is to use the "vesa" server.  There is no acceleration that way, but you get rid of the corrupt band across the bottom of the screen.

The change that you have to make is in the "Device" section, and is as follows...

Original Line:
Driver "trident"

Replacement Line:
Driver "vesa"

The rest remains the same.

---

