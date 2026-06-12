---
title: "[SOLVED] Intrepid Ibex crashes on startup"
date: 2008-11-02
forum: General Help
---

### Post by mgangav on 2008-11-02
I've been using Ubuntu since a couple of months now and I've been very satisfied with it. So, when I noticed yesterday that Intrepid Ibex came out, I immediately installed it. It worked fine for most of today.

I was just playing around with some of the new Compiz Config settings when suddenly, the computer crashed and I had to do a reboot. The computer booted fine until it reached the user selection screen. Then, when I selected my regular account, (the only one that has root access) it goes through the rest of the setup process, it loads my wallpaper, etc, then the whole screen gets messed up, and it crashes. This does not happen in another account that I created earlier.

This whole thing happened when I was playing around with the new Compiz Config settings. I'm on another account that I've created and I cannot access my files. What could be wrong? I cannot log into my account using any of the session types available except for the fail safe terminal type.

---

### Post by mgangav on 2008-11-02
ok, now for some reason after reinstalling compiz, I'm able to use my account. But AWN dock isn't working. Anyways, I'm happy enough to access my files.

---

### Post by yaknowwat on 2008-11-02
It sounds like a driver issue do you have an ATI card?

The fglrx driver doesn't have true support for X.org 1.5 so you have to wait a while until they release a driver that truley supports X.org 1.5 the only ATI driver that does this right now is the open source ones.

---

### Post by mgangav on 2008-11-03
Nope, I don't have an ATI card. Also, I'm unable to turn on any desktop effects at all. All this was working fine before. Is there any way to reinstall the required drivers?

---

### Post by Peter09 on 2008-11-03
Hi can you post the the output of

```
lshw -C display
```

That will tell us your display device and driver

---

### Post by mgangav on 2008-11-03
This is what I got

```

 *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0


```

---

### Post by Peter09 on 2008-11-03
Check that your /etc/X11/xorg.conf file is empty (or nearly so). With Intrepid it is not really used. If it is not empty move it to a different file name say - xorg.conf.saved.

Then reboot into recovery mode and select the reconfigure x option (cannot remember the exact wording). See if that helps.

---

### Post by mgangav on 2008-11-03
OK, I'll try that. Here is what my Xorg File says anyway:

```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

---

### Post by sdowney717 on 2008-11-03
could be some weird configuration in your home user account. I would suggest switching over to the other user ID, give it super user priveleges for synaptic etc...
And take the home files you want and copy them over.

You can change the user and group ownership of the files to the new user

sudo chown -R test:test /home/test

just substitute test for whatever user name you want

---

### Post by mgangav on 2008-11-03
Ok, so I moved my xorg.conf file to another directory and ran the fix x-server (I kinda forgot the exact name) under recovery mode and continued the boot as normal. Then, I went to the apperance manager and enabled advanced desktop settings (It said searching for drivers) and everything worked!! I lost all my Compiz Config settings, but emerald, compiz and AWN dock are all working well now. The new Xorg.conf is same as the one I removed.

Thanks for all the help. The Ubuntu Forum members are really helpful!!

---

