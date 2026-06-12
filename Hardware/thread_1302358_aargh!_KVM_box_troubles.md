---
title: "aargh! KVM box troubles"
date: 2009-10-27
forum: Hardware
---

### Post by loosie on 2009-10-27
Hi

Since having no success trying to network or remote desktop with my Ubuntu & Windows machines, I bought a KVM box & leads, so I can at least use both machines without having to unplug & reconnect the monitor every change.

Connected it all up the first time today & IT ISN'T WORKING!@ The keyboard & mouse work fine on both machines, but the monitor, while it shows the boot up stuff OK & goes thru to show the desktop on both machines, says "Out of range!" on both of them. Can't make it work.

In the past, if I've been switching between machines, having to unplug & reconnect the monitor, *sometimes* when I switched it while the computers were on, it would come up with "Out of range!" & I resolved it by rebooting the machine. I thought it was some discrepancy between settings for Windows & Ubuntu. Now I'm not so sure. BTW, did try rebooting too.

Any suggestions?? Please?? TIA!

---

### Post by Dark_Stang on 2009-10-27
Hook the monitor direct to each system. Turn the resolution and refresh rates down. Hook the monitor back up to the KVM. See if you have video. If you do, slowly turn up the resolution and I wouldn't put the refresh rate above 60. I'm having an issue with a KVM switch at work now that just decided that it was no longer going to support 1440x900 or higher resolutions. Yay.

---

### Post by loosie on 2009-10-27
Thank you very much! But I'm embarrassed to say, I've forgotten how you adjust all that properly??:redface: I just went to display in control panel, adjusted the resolution from 1024x768 to 832x624 , which has given me a large, blurry looking display. But the refresh rate is on 75Hz & it seems to be unchangeable.

---

### Post by Dark_Stang on 2009-10-27
> **loosie said:**
> Thank you very much! But I'm embarrassed to say, I've forgotten how you adjust all that??:redface:
In Windows XP or older: Right click on desktop, properties. Go to the settings tab. Drag that slider to the left. If you adjusted your refresh rate you can change that under an advanced tab... I don't have an XP machine so I'm not to sure where it's at exactly. It's been a while.

In Windows Vista: Right click on the desktop, personalize. Go to display settings. Drag that slider to the left. Refresh rate is adjustable as well if you have tweaked it.

In Windows 7: Right click on the desktop, screen resolution. There is a drop down menu for the resolution, decrease it. Refresh rate is under advanced settings.

In Ubuntu: System > Preferences > Display. Resolution and refresh rate are adjustable in there.

---

