---
title: "Graphics Card Problems"
date: 2011-09-03
forum: Hardware
---

### Post by aaroncam2 on 2011-09-03
Hi all,
So I recently bought two Visiontek 900089 Radeon 7000 Video Cards. When I Plugged them into my computer, they weren't recognized by Ubuntu, so in the Bios I changed "Let OS configure PnP PCI Devices" from no to yes. Now I can see the graphics cards inside gnome device manager, but the monitors aren't under Monitors in Preferences. When Ubuntu loads it briefly displays the loading screen on one of the new monitors, but then it switches back to the monitor on the old graphics card! Ideally I'm trying to get a multi-monitor setup with 3 monitors.
Any Help is Appreciated!
-Aaron

---

### Post by .... on 2011-09-03
I would try disabling KMS, as that seems to help a lot of people with old radeon cards. [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

---

### Post by aaroncam2 on 2011-09-03
I get the following error when trying to disable KMS.
```
bash: /etc/modprobe.d/radeon-kms.conf: Permission denied
```

---

### Post by .... on 2011-09-03
```
gksu gedit /etc/modprobe.d/radeon-kms.conf
```
Copy/paste  this into the new file:
```
options radeon modeset=0
```
Save. Quit. Restart

---

### Post by aaroncam2 on 2011-09-04
Well turns out I Couldn't leave the old AGP card plugged in with the new PCI card. The problem I'm having now is that nothing is displayed on the new card, not even the Bios screen, and then it seems to freeze during boot as I can't toggle the caps, num, and scroll lock keys, as well as I don't hear the Ubuntu startup sound. I'm starting to think this is a BIOS issue, but I have no idea on what settings are needed to correct it. :(

---

