---
title: "How to get ATI running FAST on Xorg"
date: 2007-08-02
forum: Hardware &amp; Laptops
---

### Post by Ryoushi19 on 2007-08-02
This tutorial is a very easy, and efficient way to get Xorg to run ATI cards faster than FGLRX ever could (granted FGLRX isn't stating much), and even faster than Xorg before these changes are done.

Step 1:  Set up your graphics Driver to Xorg ATI, if it isn't allready.
To do this, type this in the console:

> sudo gedit /etc/X11/xorg.conf

And then change the "Device" section to look something like this:

> Section "Device"
	Identifier	"Generic Video Card"
	Driver		"ati" ## the only important part is that this says "ati", as seen here.
	BusID		"PCI:1:0:0"
EndSection

Step 2:  Run glxgears and remember your frame rate, so that you can see how much improvement this change makes.  To run glxgears, type this into the console:

> glxgears

Step 3:  Open up synaptic and download "driconf".  After it's installed, run it in the console, by typing the following

> driconf

Step 4:Now that driconf is open, you'll notice one button which says "Enable Hyper Z to boost performance".  This is an ATI acceleration method, which has been continuously upgraded by ATI as they make their video cards.  Enable it by setting it to "yes".

Now that it's set to enable this, run glxgears again, and see if you notice any difference.  On my computer I saw a 300 fps boost!  ^.^

Note:  Yes I know this is in the wrong forum.  sorry, didn't read the subtitle.  Hopefully an admin wouldn't mind moving it.

---

