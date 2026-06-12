---
title: "Kernel 2.6.24-24 Issues"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by joebrueske on 2009-04-18
Quick question to those of you on the kernel 2.6.24-24 update. Did you have any issues after you downloaded it? Mine were: Grub's menu.lst wasn't updated with the new boot line, and I had to reconfigure X.org after booting because I got a white screen.

I've filed a [bug report]("https://bugs.launchpad.net/bugs/363446") as Ubuntu downloaded the kernel update twice in a row but never updated GRUB. So, I don't know.

Thanks.

---

### Post by djdjules on 2009-05-04
I just updated and had some crazy issues

After rebooting:

Gnome panels didnt have my applets anymore, they were gone
I tried to run gnome-do and nothing happened it didnt come up
I tried to open de sessions control panel and it didnt come up

I tried to open firefox to search for help and my profiles didnt show up in the profilemanager

at this point i started to worry.
I rebooted the system and came back to the same result

I then rebooted to the older kernel 2.6.24-23
Gnome panel was still crazy and my session was incomplete

I looked at the apt logs to see what it did during the update and everything looked normal.
I fired up synaptic and reinstalled 2.6.24-24
then proceeded to reboot and when it tried to boot to 2.6.24-24 it just stuck there saying that it couldnt find the device at /dev/disk/by-uuid/aoisoaiscnoascnoanco or something like that

wow, now I was really really worried

I rebooted to 2.6.24-23 and I got back into my session, this time programs are running, and the only weird thing is that my places menu and other customized options are back to defaults...

I was able to recover my firefox profiles since the files were still there. I just had to manually edit the profiles.ini file and read the desired profiles.

Im really surprised with the outcome of this latest kernel update
Maybe canonical is paying too much attention to Jaunty and forgot about Hardy...

Disappointing

---

