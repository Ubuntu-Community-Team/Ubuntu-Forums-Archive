---
title: "Auto-Configuring 2.6.27-14-generic kernal hangs during Jaunty Upgrade"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by phreaknite on 2009-05-15
I looked all over google and the forums and it seems like I am the only one with this problem.  I am still pretty new to Linux overall (maybe 2 months in, now) and decided to take the risk and upgrade to 9.04 just to be current and since there are a lot of existing little problems with 8.10 for me.

I am currently running an HP dv6t that was purchased in March 2009.  The system has a Intel T6400 Dual Core 2.0 GHz Processor, 4 GB of RAM, ATI Mobility HD 4530.  I am currently running on GNOME.

I have been trying to use the auto-updater to get system updates but the updater would hang on the new kernal install of 2.6.27-14-generic.  I decided that I would try to upgrade to Jaunty and that may fix the problem -- n00b mistake because now the installer is hanging.

I don't want to restart now because I have a nagging feeling it won't boot up again if I do that.  Attached is a picture showing the current readout of my terminal in the auto-upgrader (and the same readout when I tried to do it manually with "sudo apt-get install").

I really don't even know where to start - so any help is greatly appreciated!

---

### Post by phreaknite on 2009-05-15
OK...so I rebooted, didn't have much of a choice...and now my Ubuntu doesn't boot on any kernel (I have 2.6.7-7, -11 and -14 "installed" as well as 2.6.28-11 and none of them boot into ubuntu.

Currently I am trying to run the update as root in recovery mode and it is STILL handing at the run-parts portion of the install.  

Please help...

---

### Post by phreaknite on 2009-05-15
OK, so i have included my dmesg and syslog....hopefully these files help someone ID my problem...

---

### Post by roboa1983 on 2009-07-21
phreaknite:
I actually have had the same problem for quite a while, but other responsibilities have prevented me from posting/looking for an answer. Have you figured it out?

So far, I am using the second to last kernel in grub, which seems to work fine except for Synaptic (where I get a similar output than the one you posted.

Hopefully by bumping this, there will be an answer.

---

