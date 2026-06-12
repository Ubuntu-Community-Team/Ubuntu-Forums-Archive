---
title: "Ubuntu 9.10 on Toshiba Portege R500 - External screen not working with ubuntu 9.10"
date: 2010-01-19
forum: Hardware
---

### Post by k999 on 2010-01-19
Hi,

I recently installed Ubuntu 9.10 on my Toshiba Portege R500. It's a pretty basic install, I haven't changed many settings. I've had Ubuntu on it before, but this is a complete reinstall on a new hard drive.

Most of what I need seems to be working, but I can't get my external monitor to show anything. The display is correctly detected as a BENQ 24" (it is a BENQ T24IWA to be precise). I have tried lots of different settings, and the screen shows "No signal detected !", but at one point it also said something about being unable to display the signal, though I was unable to reproduce that...

I ran lspci on my laptop, and it shows these display controllers:

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

I had this working on an earlier install of Ubuntu 7/8. Any ideas what the issue could be, or - even better - what the fix is? :)

---

### Post by pmlxuser on 2010-01-19
I don't know if you tried restarting the machine with the external monitor attached.. 
My LG screen also refused to be configured whn i attached it to the laptop so i restarted the laptop with the screen attached it worked. 

sometimes login out and in again seems to work...

---

### Post by k999 on 2010-01-19
Well I'll be damned - a reboot with the monitor attached worked! 

That's good to know, but not an ideal fix, since I often have applications running on my computer, and travel with the laptop suspended.

Perhaps it will just continue working now that I've had it up once? Hope so. ;)

---

### Post by pmlxuser on 2010-01-19
did you also try the logout login.

basically the killing and starting x.

not ideal but well one day it will be usefull the restarting i mean....

---

### Post by k999 on 2010-01-19
I didn't try logout/login, but I'll try that if this happens again. Though there's not much point, I guess. If I have to kill everything I'm doing, a reboot at least cleans up any "stale" processes. I've experienced stale processes hogging resources and devices in the past when logging off and on again in Ubuntu, especially when switching users too.

I wish stuff like this was fixed. It certainly doesn't look good if you're holding a presentation in front of 50 people and "sorry, I have to reboot/log out to get Ubuntu working with the projector".

---

### Post by k999 on 2010-01-20
Logout/login doesn't help. I also tried connecting the external monitor before waking from suspend. As I tested variants and combinations of suspend, logout/login, System->Preferences->Display settings, and laptop keycombos, I experienced that the resolutions got screwy on both screens, both screens were blank, only one screen showed anything but the desktop expanded across both, and other weirdness.

So I'm stuck with rebooting for now...:(

---

### Post by k999 on 2010-01-21
And interestingly, when I go to work with my laptop suspended and wake it there, the remote screen just never works, but the laptop works fine. So I end up rebooting with the remote monitor connected. When I'm done for the day, I use the keyboard keycombo to change back to the laptop display, and close the lid to suspend the laptop to go home.

When I get home and open the lid to wake the laptop from suspend, and so far the screen always been black. The computer appears to be alive, because pressing backspace plays a sound through the speaker sometimes, and some keycombos cause the disk to work. But nothing I do brings the screen back to life, so I always end up switching it off with the on-off-button. When it starts up again, all is fine.

Does anybody else experience anything like this?

---

### Post by k999 on 2010-02-02
I keep trying (at least once) to get the external monitor working each time I connect it, before I reboot. The error message I get when I try the laptop keycombo to toggle through screen settings is:

> **Could not switch the monitor configuration**
could not set the configuration for CRTC 58

and my external monitor remains black (despite being on).

---

