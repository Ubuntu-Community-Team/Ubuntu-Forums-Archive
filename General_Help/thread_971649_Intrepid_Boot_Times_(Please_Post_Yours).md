---
title: "Intrepid Boot Times (Please Post Yours)"
date: 2008-11-05
forum: General Help
---

### Post by JamieKitson on 2008-11-05
Hi,

upgrading to Intrepid has increased my boot time by about 10 seconds (25 to 35 approx), even after sorting out my network settings as best I can and running a profile. I am pretty disappointed by this but have heard that doing a clean install might improve matters. Has anyone else any experience of this? I have a Dell M1330 2ghz with 2gig ram. Feel free to post your boot times and any relevant experiences.

Thanks, Jamie

---

### Post by Muflon on 2008-11-05
Hi Jamie

What is your definition of a 'boot time'?  Is it from the time you turn on the PC or from when you select an option in GRUB?  Is it until the logon screen is displayed or until the desktop is displayed?

Thanks

Sam

---

### Post by hyper_ch on 2008-11-05
Bootchart might give you a clue at what's going on during boot :)

---

### Post by JamieKitson on 2008-11-05
Muflon: I'm going on bootchart so from the grub screen yes, to whenever it stops. My WM does seem to take a bit longer to become useable though, but these points aren't really relevant as I am going on bootchart before and after the upgrade.

hyper_ch: I'm not sure many users know what to do with bootchart pngs, I know that network starting takes too long (I was happier when ubuntu didn't wait for it), but I don't really know what to do about it now that I've removed eth0 from interfaces.

---

### Post by scouser73 on 2008-11-05
I have a boot time (desktop appears with Screenlets & AWN running) of 19 seconds. I upgraded to Intrepid rather than do a fresh install; [http://www.kshoster.net/node/22]("http://www.kshoster.net/node/22")

---

### Post by JamieKitson on 2008-11-05
Thanks, what hardware is that on?

---

### Post by VMC on 2008-11-05
19 seconds! Tht must be on a very fast cpu. Mine also decreased from Harty. It takes 45-55 seconds, depending on if fully booted to desktop. Once background appears it waits a several seconds before Gnome is usable.

---

### Post by scouser73 on 2008-11-05
**System specs:**
Hi-Grade Winputer
**CPU Information:**
Model Name: Intel(R) Celeron(R) CPU 2.80GHz
Frequency: 2800.069 MHz
L2 cache: 256 KB
Memory Information: Memory Total: 1009 MiB
Swap Total: 2957 MiB
Cached: 520 MiB
Active: 525 MiB
Inactive: 396 MiB

1GB RAM, 80GB internal HDD, Maxtor Basics 3200 500GBx3 External HDDs, Lacie 250GB External HDDs

I have automatic login and I only have 6 services running: CPU Frequency Manager (powernowd), Graphical Login Manager (gdm), Multicast DNS Service, Power Management (acpid), Power Management (apmd) & System Communication Bus (dbus)

The computer was bought in January 2006.

---

### Post by Muflon on 2008-11-06
35 seconds

---

### Post by Xavura on 2008-11-06
From the screen where you select your OS to the login screen?

I'd say about 15 seconds, here. Hardy was the same. I have never counted though, I might go do that now.

EDIT:

Boy was I wrong: [http://img355.imageshack.us/img355/1614/intrepid200811061rv0.png](http://img355.imageshack.us/img355/1614/intrepid200811061rv0.png) That's my boot chart, 41 seconds... can anyone tell me if that looks normal?

---

### Post by diilbert on 2008-11-08
38 seconds.  Faster then my XP install by far.

---

### Post by philinux on 2008-11-08
From grub to login screen 29 seconds.
From login screen to usable Desktop 30 Seconds.

Why the heck is gnome taking so long and how can I trim this. I've been in sessions and services and knocked off stuff like bluetooth etc.

---

### Post by Jorge_C on 2008-11-08
My boot time is 49 seconds, read from bootchart. Very much like with Hardy

But according to bootchart, the whole first 17 seconds nothing is really happening, init is there but uses no processor nor harddrive, it seems to just hang for too many seconds, and it looks like that isn't normal according to your bootcharts.

Any ideas to solve that?

EDIT: it seems there is a bug in my bios, here is the relevant part of dmesg:
```
[    2.198486] io scheduler deadline registered
[    2.198583] io scheduler cfq registered (default)
[   10.196006] pci 0000:00:1a.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[   18.196006] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[   18.196158] pci 0000:01:00.0: Boot video device
[   18.196264] pcieport-driver 0000:00:01.0: setting latency timer to 64
```
I updated my bios but still the same problem.

---

### Post by philinux on 2008-11-08
The gnome login problem has been bugged here.
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/292376](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/292376)
```
Nov  8 12:57:06 philcb-desktop gnome-session[5709]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Nov  8 12:57:16 philcb-desktop gnome-session[5709]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Nov  8 12:57:26 philcb-desktop gnome-session[5709]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout
```

---

