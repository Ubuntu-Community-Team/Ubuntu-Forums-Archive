---
title: "xorg.conf for Sapphire ATI and Samsung 24''"
date: 2008-06-29
forum: Hardware
---

### Post by Oceanic on 2008-06-29
Kubuntu 7.4 (yes I know but mission critical)

Video Card : Sapphire ATI X1600 Pro 512MB  (RADEON?)

TFT : Samsung SyncMaster T240, optimal 1920x1200 60Hz

Characters very blurry and stuck in wrong 1600x1200.
Log (see below) suggest VESA has something to do with it, so the entry Driver is perhaps wrong?

Can you help - what should it say?

THNX

Ps. Commandline shy after ruining many systems
Pps. Hsync, Verticalrefresh etc is correct.
Ppps. generieke beeldscherm = generic screen


**My xorg.conf excerp:**


Section "Device"
	Identifier	"Generieke videokaart"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generieke beeldscherm"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection


Section "Screen"
        Identifier      "Default Screen"
        Device          "Generieke videokaart"
        Monitor         "Generieke beeldscherm"
        DefaultDepth    24
        SubSection "Display"
        Modes           "1920x1200" "1600x1200" "1280x1024" "1280x690" "1024x768" "800x600"
        EndSubSection
EndSection




**My Xorg.0.log excerp:**


(II) VESA(0): Total Memory: 256 64KB banks (16384kB)
(II) VESA(0): Generieke beeldscherm: Using hsync range of 30.00-81.00 kHz
(II) VESA(0): Generieke beeldscherm: Using vrefresh range of 56.00-75.00 Hz
(II) VESA(0): Not using mode "1920x1200" (no mode of this name)
(II) VESA(0): Not using mode "1280x690" (no mode of this name)
(II) VESA(0): Not using built-in mode "1400x1050" (no mode of this name)
(--) VESA(0): Virtual size is 1600x1200 (pitch 1600)
(**) VESA(0): *Built-in mode "1600x1200"
(**) VESA(0): *Built-in mode "1280x1024"
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0):  Built-in mode "1280x1024"
(**) VESA(0):  Built-in mode "1280x1024"
(**) VESA(0):  Built-in mode "1152x864"
(**) VESA(0):  Built-in mode "1024x768"
(**) VESA(0):  Built-in mode "800x600"
(**) VESA(0):  Built-in mode "640x480"
(**) VESA(0):  Built-in mode "640x480"
(**) VESA(0):  Built-in mode "720x400"
(**) VESA(0): Display dimensions: (520, 320) mm
(**) VESA(0): DPI set to (78, 95)
(II) VESA(0): Attempting to use 60Hz refresh for mode "1600x1200" (176)
(II) VESA(0): Attempting to use 75Hz refresh for mode "1280x1024" (11b)
(II) VESA(0): Attempting to use 75Hz refresh for mode "1024x768" (118)
(II) VESA(0): Attempting to use 72Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 75Hz refresh for mode "1280x1024" (166)
(II) VESA(0): Attempting to use 75Hz refresh for mode "1280x1024" (124)
(II) VESA(0): Attempting to use 75Hz refresh for mode "1152x864" (156)
(II) VESA(0): Attempting to use 75Hz refresh for mode "1024x768" (123)
(II) VESA(0): Attempting to use 72Hz refresh for mode "800x600" (122)
(II) VESA(0): Attempting to use 73Hz refresh for mode "640x480" (112)
(II) VESA(0): Attempting to use 73Hz refresh for mode "640x480" (121)
(II) VESA(0): Attempting to use 70Hz refresh for mode "720x400" (136)
(**) VESA(0): Using "Shadow Framebuffer"

---

### Post by Oceanic on 2008-06-30
:KS  ¿ Anyone ? :KS

---

### Post by steefjeqv on 2008-06-30
Hi,

This should work.

First, backup your xorg.conf using terminal.

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup


Then install the radeonhd driver (in terminal) :

sudo apt-get install xserver-xorg-video-radeonhd


Now edit your original xorg.conf using terminal :

sudo kate /etc/X11/xorg.conf

Make sure to change the driver from "vesa" to "radeonhd".
Save and close your xorg.conf file.

Now use ctrl-alt-backspace to restart your Xserver.

That's it.

Greetings,
Steven

---

### Post by Oceanic on 2008-06-30
Hooray, thank you very much.

Hartelijk dank voor je gedetailleerde uitleg.
Will try it right away.

Cheers

---

### Post by steefjeqv on 2008-06-30
Don't mention it.

Graag gedaan !

Going off to work now, but please let me know if everything went well.

Greetings,
Steven

---

### Post by Oceanic on 2008-07-01
Thanks, however
Radeonhd is not to be found in any repositories for Feisty

Should I go for a fglrx driver instead?
What would be the complete syntax?

sudo apt-get install ???????-fglrx

I suppose in the xorg.conf change
"vesa" to "fglrx"

Groetjes, Greetz

---

### Post by steefjeqv on 2008-07-02
Hi,

1.You can activate the fglrx driver through :

Systeem > Beheer > Hardware Drivers

Note : I tried this last week on my Hardy system with a ATI X550 graphics card and ended up with a black screen.

If this should happen (hopefully not):) :

Press ctr-alt-F1

This should open your terminal. Login and edit your xorg.conf.

sudo nano /etc/X11/xorg.conf

Check if the Driver says "fglrx".

Press ctrl-o to save and ctrl-x to quit.

To restart, just type : sudo reboot

If it doesn't work edit your xorg.conf back to "vesa", this should restore your Desktop.

Greetings,
Steven

---

### Post by Oceanic on 2008-07-23
Hoi Steven,

Spend all night trying to get the fglrx driver to work
yet to no avail.
Loads of black screens, but command-line proof friend of mine was there to place the old xorg.conf back each time (we also tried other drivers as well)

Solution now will be to update to 8.04 in a couple of weeks, since the live-cd shows a beautiful clear screen (so the hardware isn't the problem :-) in the right resolution.

Again thanks for your time - hartelijk dank !

Groetjes,

Oceanic

---

### Post by steefjeqv on 2008-07-23
Hi,

Upgrading to Hardy will do the trick.

One more thing you can try (I just thought of this) is using the packages of "Intrepid", the upcoming version of Unbuntu.

These drivers are already packaged for use in Ubuntu, so you should be able to install by "double click" and removing them through Synaptic manager.

[http://packages.ubuntu.com/intrepid/xserver-xorg-video-radeonhd]("http://packages.ubuntu.com/intrepid/xserver-xorg-video-radeonhd")

[http://packages.ubuntu.com/intrepid/xserver-xorg-video-ati]("http://packages.ubuntu.com/intrepid/xserver-xorg-video-ati")

When you install either one of them, make sure your xorg.conf uses the correct driver. Change "vesa" into "ati" or "radeonhd", according to the driver you've installed.

Greetings,
Steven

---

### Post by Oceanic on 2008-07-29
Will definitely give that a go, Steven !

Ai - I must be the slowest reply in this entire forum :)

Cheers

---

### Post by Oceanic on 2008-12-02
Thank you all !
Eventually solved the issue by upgrading to Intrepid - here the screen+GPU works brilliantly :-)
Cheers):P

---

