---
title: "Ubuntu, Nvidia 9800 gtx+, nvclock, and me.  Argh."
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by CombatLibrarian on 2009-08-14
Complete and utter newbie to Linux.

Setup went just fine, got the drivers installed for my card and all that.  And then, I hit my first big snag.

My video card is a 9800 gtx+.  It's a fine card, but with one rather unfortunate flaw in the drivers.  While it has a nifty cooler, especially for OEM, the drivers default it's speed to a paltry 35%, and don't bump it up until the temperature REALLY climbs.  In windows, I use RivaTuner to correct this, but there is no RivaTuner for linux.

A little bit of searching later, enter nvclock.

First, I attempted to install it simply from the package manager.  This seemed to go fine, but even when installing the gtk version I wasn't able to find any UI options.  I fell back to the basic version, and went from there.

The basic function to set fan speed simply does not work, and tells me adjusting the fan speed isn't supported on my card.  The message suggests setting option coolbits 1 in the xorg.conf.  I do this, and it opens up clock speed controls, but fan speed remains stubbornly unmoveable.  So I do a bit more digging, and I see the CV version.  I uninstall nvclock, go through the process of installing that, and now it tells me to set that coolbits option again...despite the fact that it's already there.

Am I completely barking up the wrong tree here?  Does anyone else have experience with this card and this system?

---

### Post by modmadmike on 2009-09-02
> **CombatLibrarian said:**
> Complete and utter newbie to Linux.

Setup went just fine, got the drivers installed for my card and all that.  And then, I hit my first big snag.

My video card is a 9800 gtx+.  It's a fine card, but with one rather unfortunate flaw in the drivers.  While it has a nifty cooler, especially for OEM, the drivers default it's speed to a paltry 35%, and don't bump it up until the temperature REALLY climbs.  In windows, I use RivaTuner to correct this, but there is no RivaTuner for linux.

A little bit of searching later, enter nvclock.

First, I attempted to install it simply from the package manager.  This seemed to go fine, but even when installing the gtk version I wasn't able to find any UI options.  I fell back to the basic version, and went from there.

The basic function to set fan speed simply does not work, and tells me adjusting the fan speed isn't supported on my card.  The message suggests setting option coolbits 1 in the xorg.conf.  I do this, and it opens up clock speed controls, but fan speed remains stubbornly unmoveable.  So I do a bit more digging, and I see the CV version.  I uninstall nvclock, go through the process of installing that, and now it tells me to set that coolbits option again...despite the fact that it's already there.

Am I completely barking up the wrong tree here?  Does anyone else have experience with this card and this system?

I have the same card but mine runs around 39 degres idle and 43 while running Unreal tournament with 16x antialsing 16x anasoptic filtering, texture sharpining and OpenGL set to High Quality. But before i switched cases it ran 70 degrees while running unreal tournament.

---

### Post by modmadmike on 2009-09-02
> **modmadmike said:**
> I have the same card but mine runs around 39 degres idle and 43 while running Unreal tournament with 16x antialsing 16x anasoptic filtering, texture sharpining and OpenGL set to High Quality. But before i switched cases it ran 70 degrees while running unreal tournament.

[http://linuxgamingtoday.wordpress.com/2008/01/30/how-to-overclock-nvidia-video-cards-in-linux/]("http://linuxgamingtoday.wordpress.com/2008/01/30/how-to-overclock-nvidia-video-cards-in-linux/")

by adding ```
    Option     "Coolbits" "1"
``` to your Device section of your /etc/X11/xorg.conf you will be able to Overclock your GPU in Nvidia X server settings.

---

### Post by czhen32 on 2010-07-08
My first post w00t! (ok sorry now that's out of my system...)

I've actually figured this one out finally, and I've been struggling with it since 9.04. There also aren't any easy found answers to this, so I figured I'd spread it around!

Coolbits "1" only opens up the over clock section in the nvidia x server settings.

Where as **Coolbits "4"** opens up the fan speed slider in the thermal settings under the Nvidia X server settings. (View attached picture)

I believe this is what you actually wanted CombatLibrarian, the only down side is having to reset this every time you boot up if you want this fan setting 24/7. Unless someone can come up with a fix for that? I'm average when it comes to Linux and can't do those things yet!

(Use the following steps to replacing "coolbits" "1" with "4")
(Also I'd replace nano with gedit) to make editing your xorg.conf easier, just remember to save and log in and out of Ubuntu afterwards to let the x server restart, allowing the changes you made to take place.
[http://linuxgamingtoday.wordpress.co...ards-in-linux/]("http://linuxgamingtoday.wordpress.com/2008/01/30/how-to-overclock-nvidia-video-cards-in-linux/")

---

### Post by Christopher on 2011-01-06
> **czhen32 said:**
> My first post w00t! (ok sorry now that's out of my system...)

I've actually figured this one out finally, and I've been struggling with it since 9.04. There also aren't any easy found answers to this, so I figured I'd spread it around!

Coolbits "1" only opens up the over clock section in the nvidia x server settings.

Where as **Coolbits "4"** opens up the fan speed slider in the thermal settings under the Nvidia X server settings. (View attached picture)

I believe this is what you actually wanted CombatLibrarian, the only down side is having to reset this every time you boot up if you want this fan setting 24/7. Unless someone can come up with a fix for that? I'm average when it comes to Linux and can't do those things yet!

(Use the following steps to replacing "coolbits" "1" with "4")
(Also I'd replace nano with gedit) to make editing your xorg.conf easier, just remember to save and log in and out of Ubuntu afterwards to let the x server restart, allowing the changes you made to take place.
[http://linuxgamingtoday.wordpress.co...ards-in-linux/]("http://linuxgamingtoday.wordpress.com/2008/01/30/how-to-overclock-nvidia-video-cards-in-linux/")



Sweet thank you very much!  :biggrin:

---

### Post by ridetheteapot on 2011-01-06
> When "1" (Bit 0) is set in the "Coolbits" option value, the nvidia-settings utility will contain a page labeled "Clock Frequencies" through which clock settings can be manipulated. On mobile GPUs, limited clock manipulation support is available when "1" is set in the "Coolbits" option value: clocks can be lowered relative to the default settings, but overclocking is not supported due to the thermal constraints of notebook designs.

When "2" (Bit 1) is set in the "Coolbits" option value, the NVIDIA driver will attempt to initialize SLI when using GPUs with different amounts of video memory.

When "4" (Bit 2) is set in the "Coolbits" option value, the nvidia-settings Thermal Monitor page will allow configuration of GPU fan speed, on graphics boards with programmable fan capability.

Setting coolbits to 5 would allow clock control & fan control - fyi

---

### Post by Christopher on 2011-01-06
> **ridetheteapot said:**
> Setting coolbits to 5 would allow clock control & fan control - fyi


Thank you very much. Would these settings work for SLI?

---

### Post by Christopher on 2011-01-07
I have the fan control on 1 of my Nvidia 8800 GTS 512's, but it won't show on the 2nd one, how do i get it to show up for the 2nd card? Thanks in advance.

---

