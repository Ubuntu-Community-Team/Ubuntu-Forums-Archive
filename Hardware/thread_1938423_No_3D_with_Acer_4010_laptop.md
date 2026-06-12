---
title: "No 3D with Acer 4010 laptop"
date: 2012-03-09
forum: Hardware
---

### Post by acidblue on 2012-03-09
I have an Acer 4010 laptop with a intel 82852/855GM video card.
I cannot get compiz to run, even though i passed the 'compbiz test' in the 'system testing' although It did say I was using the 'vesa' driver.

How do I change from using the vesa driver to the actual driver for my card?
Do I need to compile the driver?
It's an older card so I assume the driver is included with Ubuntu but I don't really know.
Any insight would be helpful.

Using Ubuntu 10.10.

Here is the output of the Compiz-Check script
```

Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) y
```

The script checks for a driver but doesn't find one.
Looks like I need a driver for this chipset.
Does anyone know if one exists?

---

### Post by gordintoronto on 2012-03-09
Run System, Administration, Additional Drivers. If nothing shows up, you may be out of luck.

You could also try Google.

---

### Post by acidblue on 2012-03-10
I've tried this:
sudo add-apt-repository ppa:glasen/intel-driver
sudo apt-get update
sudo apt-get install xserver-xorg-video-intel

Then I had to make an xorg.conf file.
[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

But after a reboot I got a black screen, I could see the mouse pointer but nothing else.
So after some linux voodoo I got rid of the xorg.conf file and now I'm back to using the vesa driver.

However after rechecking the xorg.conf file I don't think this is right:
```
Section "Device"
        Identifier      "Configured Video Device"

```
Shouldn't the 'identifier' be something else?

---

### Post by gordintoronto on 2012-03-10
Mine says:

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

---

