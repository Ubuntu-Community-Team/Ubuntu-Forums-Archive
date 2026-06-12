---
title: "Sound problems after upgrading from 8.04 to 8.10"
date: 2009-03-07
forum: Hardware
---

### Post by adam_ski on 2009-03-07
I've just upgraded from 8.04 to 8.10. The volume was working fine in 8.04, but since the upgrade it's dead. When clicking on the volume control icon that appears in the top right hand corner I get the message

> No volume control GStreamer plugins and/or devices found.

and
> The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plug-ins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu

When I go to the sounds menu (System > Preferences > Sound) & click on the test for music & movies I get the error message

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not get/set settings from/on resource.

Using some of the info on [this thread](http://ubuntuforums.org/showthread.php?t=205449) I *think* Ubuntu has lost the configuration for the sound card because typing ```
aplay -l
```into the terminal comes up with ```
aplay: device_list:215: no soundcards found...
```

My sound card is whatever was shipped with the laptop (Toshiba Satellite Pro). I tried to check out the sound card from the Windows part of the machine & got the following information, which hopefully is the sound card:

Conexant AC-Link Audio
Driver Provided: Conexant
Driver Date: 14/10/2004
Driver Version: 6.13.10.8355
Location: PCI bus 0, device 31, function 5

However, I couldn't find anything that looked seemed to match that sound card on the [ALSA project website](http://www.alsa-project.org/main/index.php/Main_Page).

I have also tried reinstalling the ALSA drivers by first removing them ```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
``` and then reinstalling them using ```
sudo apt-get install linux-sound-base alsa-base alsa-utils
``` but that didn't help and I'm running out of ideas as to what to do.  Any hints?

---

