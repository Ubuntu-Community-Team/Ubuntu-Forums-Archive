---
title: "VGA output limited to 640x800 on Vaio VGN series, Nvidia Geforce 7400"
date: 2008-09-17
forum: Hardware
---

### Post by Teppi on 2008-09-17
Hi all,

I recently installed Ubuntu Hardy Heron on my Vaio VGN-SZ400 which was originally shipped with Vista Business. Everything works right out of the box and by everything i mean almost everything for a functional notebook: keyboard, USB, bluetooth, wireless, laptop monitor, motherboard, dvd read/write, Fn volume/brightness control, etc. It runs quiet and cool, and i was amazed at the degree of reliability and hardware support of this linux system. 

The native laptop resolution is 1280 x 800. I have a 1440x900 external monitor connected and on windows vista, i was able to set up dual monitors with different resolutions (1440x900 forced) with the help of Powerstrip.

note that the laptop's graphic card is Nvidia Geforce 7400
now on ubuntu, i tried installing nvidia xserver settings and cloning my laptop screen to the 1440x900 external monitor. However, the VGA output would only go up to 640x800. 

So my question is:
My graphic card only supports up to 1280x800 res. 
How do i clone this to the external monitor with 1440x900 native resolution thru a VGA port? or simply just getting any resolution above 640x800?

Please help 
i've gone thru this ubuntu support page for graphic cards and resolution but the information was just massive to pin down to my problem, i was not sure which solution to try and which not to.

Many thanks!

---

### Post by overdrank on 2008-09-17
Hi and welcome, if you are unable to use nvidia-settings to change the resolution for the external monitor then you can try and use the command ```
gksu displayconfig-gtk
``` to setup the external monitor. If this fails then you may look at editing your xorg. If you like you can post your xorg here  and someone may be able to help.
Use the command ```
cat /etc/X11/xorg.conf
```

---

### Post by Teppi on 2008-09-17
Hey thanks for the welcome message :)

This is what i just did:

gksu displayconfig-gtk

When i employ a clone monitor of 800x600, my laptop screen resolution will stay at 800x600 or 640x800 depending on which generic external LCD screen settings i use. 

So i reseted the change, logged off and my laptop display was fine again.

On to the 2nd try:

Knowing my laptop display would be affected when i try cloning it,
this time i specifically chose settings for each display:

Generic Widescreen 1280x800 monitor for my laptop display
Generic Widescreen 1440x900 monitor for the external display
Clone output

I logged off and logged back on, both displays were at 800x600
I tried gksu displayconfig-gtk again to reset these changes
It wouldn't start
and i got this

> []
Traceback (most recent call last):  File "/usr/bin/displayconfig-gtk", line 75, in <module>
    app = DisplayConfig(options)
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 189, in __init__
    debug_scan_pci_filename=self.options.pcitable)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 394, in __init__
    self._finalizeInit()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 418, in _finalizeInit
    self.setLayout(gfxcard._getDetectedLayout())
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 972, in setLayout
    gfxcard.setLayout(XSetup.LAYOUT_CLONE)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1184, in setLayout
    screen._resyncResolution()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1861, in _resyncResolution
    self.gfx_card.setup.getPrimaryScreen()._resyncResolution()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1817, in _resyncResolution
    (preferred_width,preferred_height) = self.getAvailableResolutions()[-1]
IndexError: list index out of range



Please help.

---

### Post by overdrank on 2008-09-18
Ok if you still receive the error you may have to use the xfix option by booting into recovery mode. which is usually the second choice from the grub.

---

