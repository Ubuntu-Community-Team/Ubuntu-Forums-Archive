---
title: "lenovo v460"
date: 2010-08-09
forum: Hardware
---

### Post by hupsen on 2010-08-09
Hello, i've recently got his new laptop (lenovo v460 )and after installing ubuntu 10 (it was running pretty smooth) i could not check most of the things.

I've activated the Nvidia driver, rebooted and it is gone. notthing on the display. i have try to access the tty but cant.. here says it uses nvidia cuda, that might be a problem for compatibility or drivers.

does anyone if this laptop can be used with ubuntu just fine? it has several buttons, i think those are acpi buttons. some might be important, for performance and i dont know if they could be activated..

best regards

---

### Post by hupsen on 2010-08-09
the trackpad/integrated mouse is completely unusable, on top of it, when using a usb mouse if the trackpad is not deactivated it will render the usb mouse pretty much unusable too. so anyone with same problem, use the function key to deactivate the trackpad before touching it and use usb mouse.

installing nvidia driver broke the x beyond repair, that is with my skills... but with the other driver its fine

tty is also not working with a clean install, i suspect it is because of resolution problems, i will try to get it fix and write it here for anyone that needs it..

---

### Post by bhaverkamp on 2010-09-19
So did you get the trackpad issue resolved? I am having same problem. Have not tried updating video drivers. 

> **hupsen said:**
> the trackpad/integrated mouse is completely unusable, on top of it, when using a usb mouse if the trackpad is not deactivated it will render the usb mouse pretty much unusable too. so anyone with same problem, use the function key to deactivate the trackpad before touching it and use usb mouse.

installing nvidia driver broke the x beyond repair, that is with my skills... but with the other driver its fine

tty is also not working with a clean install, i suspect it is because of resolution problems, i will try to get it fix and write it here for anyone that needs it..

---

### Post by hupsen on 2010-09-19
i didnt have much time to get into it yet. But i heard that you can actually set the dimensions of the trackpad manually.

From the first impression, it looks like it recognize only the sides of the trackpad, the scroll thingy. Perhaps its recognizing the scrolling side as the trackpad. There is a driver somewhere that i have tried too. It makes a very small difference, instead of just jumping around to random places you can actually try to aim, but still not enough to be usable.. For now, what i do is deactivate it with the acpi key, to avoid touching it by mistake and render it unusable and use a usb mouse.

For the video drivers.. i got compiz working great setting it up first with the cdlive and then installing it. im not using nvidia drivers, just the one that comes with ubuntu.

I did one fresh installation without the wireless drivers and later i could not make it work. So i just had to set it up right in the cdlive and then install it.. 

let me know if you get anything, good luck^^

---

### Post by ghelbig on 2010-09-22
I added the line "options psmouse proto=imps" to the end of the alsa....conf (I don't remember the exact file name) file in /etc/modeprobe.d

That seemed to make basic functionality of the touchpad work.

I saw a lot of posts regarding the V460 touchpad not working - I'm guessing that a new driver will be needed to make it work properly.

---

### Post by stevefranks on 2010-10-15
Wifi worked great under 10.04, except that I couldn't seem to connect to wireless N routers.

Now I've upgraded to 10.10, and the wireless is about to send me back to lucid, I don't know how else to say it.  It drops in & out 15 minutes or so after boot, and if you suspend, it's gone period until you reboot.  All my other systems (freebsd, fedora) are running fine, so I know it's not the net per se...what a downgrade, man.  On the plus side, no trackpad or sound issues...

I've tried switching newtorkmanager to wicd, no real changes there.  I've also added "b43" to STOP_SERVICES in **/etc/default/acpi-support**

---

### Post by bhaverkamp on 2010-10-16
My experience as well. I see nothing of value with 10.10 anyway and am staying happily with the 10.04 release on my other PCs. The v460 is my entertainment PC anyway so I am just sticking with windows and running 10.10 in a VM where is works just fine.

---

### Post by ghelbig on 2010-11-25
The touchpad has stopped working after recent updates.  ARGH!

The fix (above) no longer works, and it looks like the "correct" module doesn't even load.

---

### Post by jimik on 2010-12-22
hi, please do you know how to control fan speed?

---

### Post by juicyoner on 2011-01-20
> **ghelbig said:**
> The touchpad has stopped working after recent updates.  ARGH!

The fix (above) no longer works, and it looks like the "correct" module doesn't even load.



^^ same!

---

