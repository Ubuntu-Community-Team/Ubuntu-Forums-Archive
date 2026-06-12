---
title: "usb audio trouble"
date: 2006-11-17
forum: Hardware &amp; Laptops
---

### Post by vmueller on 2006-11-17
Can somebody help?  I'm running Ubuntu Edgy on a Dell Inspiron 710m laptop.  I've got a new usb audio device that won't play back.  Ubuntu recognizes it and loads it, with the LED lights on.  lsusb lists it as:

Bus 004 Device 005: ID 1130:f211 Tenx Technology, Inc. 

It shows up in the System>Preferences>Sound as USB Audio, along with my built-in sound card (Intel 82801DB-ICH4).  When I select the USB Audio for "Music and Movies" and "Sound Events," sound playback still happens through my built-in speakers.  I've tried restarting and everything, but Ubuntu still selects my built-in soundcard over the USB device.  Is there a way to force it to use the USB audio?  I can't disable the built-in sound card in my BIOS, there's no option to.

When I select "USB Audio" in the Sound Preferences dialogue box and click "Test" I get the following message:


audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not get/set settings from/on resource.


Can anyone help?

Thanks!

---

