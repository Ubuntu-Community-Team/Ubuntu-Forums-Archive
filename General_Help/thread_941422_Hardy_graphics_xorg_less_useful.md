---
title: "Hardy graphics xorg less useful?"
date: 2008-10-08
forum: General Help
---

### Post by bazzer on 2008-10-08
Hi
Bit of a rant really - xorg now doesn't control the graphics options and I don't know what does. The screen resolution can't be controlled reliably neither can the refresh rate. I think the gui control is funky and helpful for a lot of people but I'd like to know how I can affect the settings when Xorg fails. Is there a conf file I've not found yet?

Specifically, I've got a machine with onboard VIA graphics and Xorg fails with 'No screens found'. I've installed xserver-xorg-video-openchrome but the xorg.conf doesn't mention a graphics driver at all...

---

### Post by cybrid on 2008-10-08
Well I'm no expert at this but, I think you could default the driver in xorg.conf to vesa until you find out the name of the driver you must use. As far as I know everything you might need to configure X.org is in the xorg.conf file.

---

### Post by porchrat on 2008-10-08
why don't you just use "system" --> "Preferences" ---> "Screen Resolution"?

---

### Post by bazzer on 2008-10-08
> **porchrat said:**
> why don't you just use "system" --> "Preferences" ---> "Screen Resolution"? Well I'll assume you're referring to my rant there - have you tried that? It just doesn't work. Xorg will pick it's own resolution and you're stuck with it. I've several screens and have tried selecting 1280x1024, 1024x768, 800x600 and so on, but it just doesn't work. Surely there should be a conf file somewhere where you would be able to set it?!


But, I think I've found out what's wrong, the VIA driver doesn't present a screen to xorg. I've added Driver = "vesa" in the 'Devices' section and Xorg will load with this...

---

### Post by caleb12 on 2008-10-08
I believe... available modules (drivers) are in /usr/lib/xorg/modules/drivers, it should be as simple as editing xorg.conf adding a device section for the video adapter and defining the driver module to use... Something like this:

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "radeon"
EndSection

Screen resolution can also be defined in xorg.conf - most of those GUI utilities are just editing this file for you anyways... mine as well do it yourself. My screen section looks like this:

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth     24
   SubSection "Display"
        Depth       24
        Modes       "1440x900"
   EndSubSection
EndSection

Hope that helps... Also almost all your problems will be detailed in /var/log/Xorg.0.log & any changes made to xorg.conf requires the Xserver to be restarted... so, log out.Mind you, if there is a config error in xorg.conf that the Xserver doesn't like it will fail after you log out, be prepared to login to a command prompt and edit xorg.conf manually. This will almost definitely occur if you attempt to use the wrong module...

Your last post came through while I was writing this, so I thought I would add a bit... The default screen is usually defined in the ServerLayout section:

Section "ServerLayout"
        Identifier      "Default"
        Screen      0   "Default Screen"
        InputDevice     "Configured Keyboard"   "SendCoreEvents"
        InputDevice     "VX Nano"               "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection


You could define mutliple screens here as well, and then later in the Screen Section define the resolution for that screen...

---

