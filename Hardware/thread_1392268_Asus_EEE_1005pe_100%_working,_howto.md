---
title: "Asus EEE 1005pe 100% working, howto"
date: 2010-01-27
forum: Hardware
---

### Post by chadraytay on 2010-01-27
Here's how to get one of the new pineview chipset Asus EEE 1005pe systems running regular ubuntu.
Netbook still works like crap for some reason so don't bother trying the remix.

Use whatever installation method you want, have a usb mouse handy. Make sure on screen keyboard is set to enabled in the boot options and start the live boot. Once the system is fully booted, plug in the usb mouse and use the onscreen keyboard to set your options and install ubuntu.

Shutdown, unplug mouse. Start system fully again, plug mouse back in. Use onscreen keyboard to do a sudo apt-get update and a sudo update-manager

Install ALL updates that are available.

Shut down system, unplug usb mouse.

Now, unplug the laptop. Turn it on and let ubuntu fully boot. Mouse and keyboard should magically work at this point, and you may now plug it back in. It must be plugged in to shut down properly, but if you plug it in during the startup it will have no mouse/keyboard (no idea why...)

Sound isnt working yet.
Comment out the last line in /etc/modprobe.d/alsa-base.conf which is something about intel hda and power save
Add options snd-hda-intel model=asus-laptop to the end of this file.

Reboot, sound should be fine now. :)

There ya go! systems working now! Sorry but as I never use a webcam I havent bothered to check if its working. Might try that sometime but really dont care.
:popcorn:

---

### Post by incade on 2010-01-29
Wrong forum post, sorry.

---

