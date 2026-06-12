---
title: "Kpilot hosed in 8.04?"
date: 2008-10-01
forum: General Help
---

### Post by devnulljp on 2008-10-01
Is KPilot completely hosed for anyone else? I've been using it quite happily on Kubuntu up to 7.x synching through bluetooth on a Palm Treo 650, but after recent upgrade to 8.04 it refuses to sync, with the daemon crashing after a few seconds. I can still sync to jpilot or to pilot-xfer, but I like the integration of kdepim. 
Anyone else?

---

### Post by Harbard on 2008-12-21
Have you had resolution on this?  I am now unable to sync my PDA because kpilot keeps crashing.  I see several bug reports filed but no solutions.  I would hate to have to go back to windows just to sync and back up my pda....but I can't live without my pda either.

---

### Post by jglen490 on 2008-12-22
After working like champ on Kubuntu 7.10, kpilot was hosed when I went to Kubuntu 8.04.  However, I tried a few things and it's only semi-hosed now.

In Settings->Confgure Kpilot->device, if I enter ```
usb:
``` in the Device block, sync is pretty much automagic, but Kpilot is also somewhat unstable.  When I enter ```
/dev/ttyUSB1
```, sync will usually only happen if I enter ```
lsusb
``` at the command line, but Kpilot seems very stable.  Sometimes it doesn't require a ```
lsusb
```, but I haven't quite figured out the condition.

But the biggest thing that got me this far was loading the visor kernel module.  I initially did a ```
sudo mdprobe visor
``` at the command line, and that worked. So I added ```
visor
``` to /etc/modules to load it every boot.  Before loading the module nothing I did in the config screen did anything -- except pump up my blood pressure :eek:!

---

### Post by jglen490 on 2008-12-23
Nevermind, figured it out.  I had attached a USB hub to the USB port on my laptop.  I then plugged my Zire 31 into the extension hub.  When I connected the Zire directly to the port on the laptop, it just worked.

So apparently the extension USB hub isn't picked up by hald or anything else until an ```
lsusb
``` is entered.  Just need to figure that one out - a udev rule perhaps.

---

### Post by devnulljp on 2008-12-24
To make things more complicated, I'm using bluetooth to connect. works fine with jpilot and pilot-xfer. kpilot just crashes.

---

