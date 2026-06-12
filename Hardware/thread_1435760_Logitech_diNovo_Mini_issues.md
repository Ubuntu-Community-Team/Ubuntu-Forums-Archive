---
title: "Logitech diNovo Mini issues"
date: 2010-03-21
forum: Hardware
---

### Post by moodog on 2010-03-21
I picked one of these up on the weekend, and when it works, it works well.

I've got a couple of issues though. For some reason on booting, the dongle doesn't seem to be recognised - I need to pull the dongle out and put it back in again to get the keyboard to work.

I've also created an xmodmaprc file to modify some of the key mappings, but it doesn't seem to be processed on start up - however I think I've just found that I've named it wrong - if I name it /home/<username>/.Xmodmap it should get processed on mythbuntu login.

Also, I've read through a lot of other posts and wiki entries, specifically this one here:

[http://www.mythtv.org/wiki/Logitech_diNovo_Mini](http://www.mythtv.org/wiki/Logitech_diNovo_Mini)

which say that there are issues with getting all the keys to map. But most of these posts/wiki entries are quite old, and I'm wondering if anyone has got anywhere with them?

I've found using xev that when pressing the 3 leftmost media keys (vol down, vol up and mute), the keys don't output a useful scan code. However when pressing Fn <those 3 keys> they do output useful values. Is there any way to use these keys without having to hit Function?

Also, is the supplied dongle just using the standard wireless communication like most other wireless mice/keyboards (2.4ghz?)? If I was to get a bluetooth dongle, would communication be more reliable? I've read some conflicting reports - i.e. pre 8.10, bluetooth was better, but now bluetooth is worse.

---

### Post by efflandt on 2010-03-21
I have a diNovo keyboard/mousepad and it has worked immediately from the BIOS splash screen onward on any computer I tried (even for BIOS password) without having to do anything special at all in Windows or Linux, even when connected on the fly.  But everything is standard modules in Ubuntu 9.10 32 or 64-bit except for Broadcom STA on USB hard drives that are sometimes booted on a Dell laptop.  I was surprised that its volume control and mute worked in gnome automatically.  But I am not doing any key mappings and have no xorg.conf (maybe you have xorg.conf settings that interfere).

The dongle is Bluetooth, but secure HID, for keyboard/mouse only.  So it does not show up as a regular Bluetooth device (does not bring up the Bluetooth ap and is not visible in that) since it does not work for other Bluetooth applications.

So I am very pleased with how it works automatically.  I originally got it for when laptop is connected to HDTV and I can sit back in my easy chair with the lightweight keyboard/mousepad.

What are your BIOS (CMOS setup) settings related to USB?  I think mine are Auto, so they can automatically recognize legacy devices if present, or can boot from USB.

---

### Post by moodog on 2010-03-24
Acutally, I plugged the dongle into my other ubuntu 9.10 machine, and as you said, everything worked straight away. It appears that it's just some problem with Mythbuntu. re: bios settings, it's a bit hard for me to check as my plasma doesn't come on until the system has booted (past bios). I'll have to plug in another monitor to check. I think last time I was in there though, I decided I was a bit disappointed with the motherboard in that box, as it didn't support booting from a usb memory stick, so there may be some issues. Thanks for the info.

---

