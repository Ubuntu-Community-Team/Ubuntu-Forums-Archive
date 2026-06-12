---
title: "Gnome-pilot fails, but pilot-link works"
date: 2008-07-25
forum: Hardware
---

### Post by navaburo on 2008-07-25
I have run into some trouble while attempting to sync my Tungsten|E2 via USB cable on my newly-installed 8.04 system.

The pilot-link program works fine, using the command:

```
pilot-xfer -p usb: -l
```

However, gnome-pilot (via Evolution) fails to see the device, when using either the usb: or the various /dev/ addresses. The failure of the latter kind of address may be due to a visor module issue (as Evolution and a launchpad bug report claims), however I see no reason why Evolution/Gnome-pilot cannot use the usb: address.

Any help is greatly appreciated. I will reply if I succeed on my own.

---

### Post by evets25 on 2008-07-25
Hey! tungsten E2! I have one of those! :D I haven't used it for a while though. From what I remember of trying to get it to sync from a year or two ago, I never got gnome-pilot working correctly, because I couldn't guess the correct USB number that it was plugged into or something like that. I did get kpilot to work for me though. Sorry I'm not being much help; I'd like to know the answer to this two. :P

---

### Post by celem on 2008-08-18
My fresh install of Mint Elyssa 5r1, which is based upon Ubuntu 8.04, indicated that Gnome-Pilot was installed, so I tried to sync. Nothing! I tried all of the various settings to no avail. Next, I noticed that Pilot-Link was not installed, so I installed it. It didn't appear to help anything, that I can tell, but it didn't hurt either. Next I read Daniel Baggio's blog about getting gnome-pilot working with a palm Z22 on Fedora 8. After reading the blog I entered sudo modprobe visor. Success!!! now with gnome-Pilot ser to usb: I can sync!

---

### Post by DavidVS on 2008-10-02
My Tungsten E2 is having the same problem with gnome-pilot.

Can someone explain "sudo modprobe visor" to me?  Is this good to try?  Is there a better way to fix things?

---

### Post by jcryan on 2008-11-14
I just figured out how to connect my Tungsten E2 to gnome-pilot and evolution.  Use the usb: for the type of connection.

I have a problem with the sync however.  It never completes and hangs up gnome-pilot.  The sync seems to work OK, but my Palm says that the connection terminated and gnome-pilot says that the sync goes on forever.

Let me know if you have better luck that I have.

---

