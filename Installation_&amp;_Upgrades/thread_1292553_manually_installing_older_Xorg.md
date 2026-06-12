---
title: "manually installing older Xorg"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by laramichaels1978 on 2009-10-16
Dear all,

I am a very happy user of Ubuntu! Thank you to all the developers and distribution workers who made this possible. : )

I have the following situation: my old Thinkpad has an intel graphics chipset that current Xorg and/or kernel drivers do not like. I have gone through both

[https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance)

as well as

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

and neither helped. I am stuck using the VESA driver which makes my relatively old computer feel VERY old. : (

I remember that before instaling Ubuntu I had a version of Slackware (I can figure out which one it was, the CD is still here) on this computer with which I could use the nice and fast intel driver in Xorg/kernel without the screen corruption that so many people experience. Over the last months I have become sufficiently annoyed by the slowness of the graphics (especially when scrolling and switching workspaces) that I have decided to do something about it. Basically, my question is:

I would like to manually install the old version of Xorg that I know works on this hardware (either from an older Ubuntu repository or from source) [and if necessary the older 2.6 kernel with its intel graphics driver]  I had been using on Slackware.

Can I do this on Ubuntu? Is there a way to keep synaptic and the update manager (which I otherwise love!) from interfering with this change?  Should I expect any problems?

Thank you for any help

-lara

---

### Post by tommcd on 2009-10-16
> **laramichaels1978 said:**
> 
I would like to manually install the old version of Xorg that I know works on this hardware (either from an older Ubuntu repository or from source) [and if necessary the older 2.6 kernel with its intel graphics driver]  I had been using on Slackware.

Trying to install an older xorg from the Ubuntu repos would likely lead to broken dependencies that could break your system. Trying to install xorg from source is not a trivial task, especially on Ubuntu which uses custom packages for everything. Slackware uses "plain vanilla" packages unchanged from the upstream developers, so something like this would be a bit easier. Plus Slackware uses no dependency management so you can do what you want.

I would suggest doing a clean install of Ubuntu Karmic 9.10 beta. Yes, it is still in beta, but it is pretty stable at this point. The intel driver situation is greatly improved in Karmic. The release candidate for Karmic should be out in a few days if you don't want to use the beta.  Karmic final will be out in 13 days, so you could just wait for that. Karmic may fix your intel driver problems without all the hassle of installing an older xorg on Jaunty.
You could do a dist-upgrade to Karmic, but a clean install is the best way to avoid problems imo.
If it were me, I would just stick with Slackware ;), but if you want Ubuntu I would go with Karmic.
Another option would be to use Hardy 8.04 LTS which does not have this problem. Hardy will have older versions of the software you use though.

And welcome to the Ubuntu forums!

---

### Post by laramichaels1978 on 2009-10-16
Hi Tom,

Thank you for the excellent help. Yeah, I guess the "magic" of a full package/dependency system is great... until something stops working. : )

I will try the new release, hopefully that will fix things.

Bye and again thanks

lara

---

