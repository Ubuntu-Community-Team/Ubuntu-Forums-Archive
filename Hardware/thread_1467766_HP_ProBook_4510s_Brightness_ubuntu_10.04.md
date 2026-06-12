---
title: "HP ProBook 4510s Brightness ubuntu 10.04"
date: 2010-05-01
forum: Hardware
---

### Post by bkbilly on 2010-05-01
I recently installed Ubuntu 10.04 and I can't change the brightness of my screen...
I tryied the combination fn+F7 or F8 but nothing!
I added to the panel the Brightness Applet and still nothing...
The applet shows me this message: Cannot get laptop panel brightness
when I had 9.04 It worked without any problem... :(
can you help?

---

### Post by dino99 on 2010-05-01
need to know the video card or chipset

---

### Post by bwad on 2010-05-01
Same problem with my HP Elitebook 8530w, Nvidia FX 770 chipset with proprietory drivers installed. Worked fine on ver 9. When attempting to change brightness, the brightness display panel pops up and sits at 50% and doesn't move.

---

### Post by pschroth on 2010-05-01
Here the same on a hp 6830s. I am able to change the display brightness directly in the /proc dir so I use an simple script to set my preferred brightness to 80%.

Video card is ATI Mobility Radeon HD 3430 with the ATI driver.

I hope there will be an solution for this bug.

Philip

---

### Post by bkbilly on 2010-05-01
> **dino99 said:**
> need to know the video card or chipset

This is my video card: ATI Radeon HD 4330

---

### Post by FalFire on 2010-05-01
I have a similar issue on my HP EliteBook 8530w with Ubuntu 10.04: 

When I hit the key combination to *increase* the brightness, the brightness indicator pops up and flashes, which normally indicates (on previous versions of Ubuntu) that it's already at it's max/min, which is true, because I can't get it off max. brightness. It does appear to work but it can't do anything because the brightness is already maxed out.

When I hit the key combination to *decrease* the brightness, the indicator also pops up, but doesn't do anything, it doesn't decrease the brightness and doesn't give any visual feedback except for popping up when hitting the key combo. 

Hitting the combination to disable/enable adjusting the brightness to the environment lighting does work normally.

So it appears that only decreasing it doesn't work. Everything worked fine on earlier versions on Ubuntu, but sometimes I had to install the newer binary nvidia drivers for it to work. It didn't work with the nvidia drivers that are automatically installed with 10.04, so I installed the latest binary driver (195.36.24) but it still doesn't work.
My graphics card is a "Quadro FX 770M/PCI/SSE2".

---

### Post by pschroth on 2010-05-01
Just uninstalled the FGLRX driver and now I am able to set the brightness via the gnome applet. Fn keys for brightness give a popup now but do not change the brighness.

With the FGLRX driver the brighness Fn keys do nothing. Just sometimes the screen flickers a bit.

Maybe this belongs to the same bug. The Fn mute key does nothing.

Philip

---

### Post by Dan0512 on 2010-05-01
I have an HP8530w and I'm also experiencig this problem. Pressing fn+f9 and fn+10 doesn't change brightness. Though when pressed, the brightness level indicator pops up at the right top of the screen.

I've found the following information while googling:

> Haha, I solved the Bug!

The ACPI key-scripts seem to echo 0-100 to the following location:
 /proc/acpi/video/GFX0/LCD/brightness

...but that is false! The graphics card on my compaq615 is mounted to /proc/acpi/video/IGFX

Enter this to get a description which kind of values are allowed by the driver:
cat /proc/acpi/video/IGFX/LCD/brightness

Create a test script and test it via sudo:

#!/bin/bash
echo 100 > /proc/acpi/video/IGFX/LCD/brightness

Now I've got my full backlight again =)
If you want to change the backlight of an external monitor, just...
ls -l /proc/acpi/video/IGFX
...to see the "available" Monitors (connectors) of your graphics card.

Cheers!
Chris

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/514477]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/514477")

I would like to test the solution, but I don't know where these "ACPI key-scripts" he's referring to are located. Help!

dan

---

### Post by bkbilly on 2010-05-01
That's very usefull to know but the only problem is that it's not easy...
I want to make the fn+f7 & fn+f8 to work...

My graphic card is mounted on the /proc/acpi/video/DGFX.
It must be diferent between graphic cards...

---

### Post by FalFire on 2010-05-02
Does anyone know which package is responsible for this so I can file a bug report? When using System->Preferences->Power Management to adjust the brightness it works perfectly fine.

---

### Post by pschroth on 2010-05-03
I think that is one of the problems to file a bugreport. There are many complaints about the acpi interface on different laptops. I read somewhere it is even possible a kernel bug.

---

### Post by gnothi on 2010-07-10
bkbilly, the fn-key problem that you describe here also appeared when I went from 64-bit Karmic to Lucid on my HP ProBook 4510s, which has an ATI Mobility Radeon HD-4330. The fn-key problem disappeared after I installed ATI Catalyst Display Driver version **10.6**, which I downloaded from the AMD support site.

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

---

### Post by bkbilly on 2010-07-10
Unfortunately it doesn't work...
Is there a chance that you did and something else beside installing ATI Catalyst Display Driver?

---

### Post by xantios on 2010-07-27
> **Dan0512 said:**
> I have an HP8530w and I'm also experiencig this problem. Pressing fn+f9 and fn+10 doesn't change brightness. Though when pressed, the brightness level indicator pops up at the right top of the screen.

I've found the following information while googling:



[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/514477]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/514477")

I would like to test the solution, but I don't know where these "ACPI key-scripts" he's referring to are located. Help!

dan

Thx for that quote, it really helped me to fix that annoying brightness problem. 

Sure it isn't the most beautiful solution ever,but i don't really care so much for as long as it works...

Though,i don't think it should be so much of a problem to fix this bug in a more neat way, or just implement this call into the acpi buttons.

Lets see if we can code around for a solution.

Edit:
```

#!/bin/bash
#
# -- Just a bit of hacking arround.
#

# -- Fist of,lets read the file.
currentvalueraw=`cat /proc/acpi/video/IGFX/LCD/brightness`

# -- We only want current value,so lets split.
currentvalue=${currentvalueraw#*current: }

# -- What are we going to do?
# -- Increment or Decrement..
if [ "$1" = "increment" ]; then
	newvalue=$((currentvalue+10))
	echo $newvalue
else
	# Asumption is mother of all ****ups, so lets **** things up.
	newvalue=$((currentvalue-10))
	echo $newvalue
fi

# Lets make **** happen.
echo $newvalue > /proc/acpi/video/IGFX/LCD/brightness

```

Just a piece of Bash i think should make it a bit more of a breeze to fix this.
Also,you can offcourse use the default Hotkey manager to use this script as a permanent fix.

Hope you can use this for some useful purposes!

(by the way: i used this for my Compaq 615)

---

