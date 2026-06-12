---
title: "Trouble with Resolutions after Monitor Switch"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by runnir on 2009-03-16
Hey all.  Having some problems with my screen resolution, and after much searching have not been able to borrow ideas from other posts to get it done.

I installed using one monitor and that seemed to work fine.  I need to switch to a different monitor and when I booted up with it, and my result is a messed up display, with all horizontal lines where it looks like the vertical sync is wrong.  The login screen displays in a beautiful resolution, but as soon as it goes to resize it after login, I get the line problem.

I used

```
sudo dpkg-reconfigure xserver-xorg
```

to no avail.

Looking at my xorg.conf file, I noticed there's not that much too it, it doesn't recognize the graphics card (whatever's on a Dell Dimension L886R.)

Here it is:

```

Section "Device"
[INDENT]Identifier "Configured Monitor"[/INDENT]
End Section

SubSection "Monitor"
[INDENT]Identifier "Configured Monitor"[/INDENT]
End Section

Section "Screen"
[INDENT]Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"[/INDENT]
EndSection

```

I've tried editing it, but it always says that it can't parse it, and I can get in under low-res settings.

I've also tried the Hardware Drivers under Administration, but I don't see any drivers at all.

---

### Post by runnir on 2009-03-17
So, I've managed to fix it, after a fashion.

Because I had a nearly clean install, I simply reinstalled it with the new monitor attached.  This has resolved the problem.

It seems like the monitor and graphics card were configured during install.  I think I'm too much a n00b right now to understand how Ubuntu is interacting with xorg.conf.  I do worry that the next time I need to change a monitor, I'll have problems again.  

Anyways, solved for the moment.

---

