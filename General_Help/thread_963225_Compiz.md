---
title: "Compiz"
date: 2008-10-30
forum: General Help
---

### Post by A1len on 2008-10-30
Hey guys.

So I discovered compiz the other day, so naturally I've been tinkering around with that a bit. I finally got my desktop exactly where I want it in terms of aesthetics, but I hit a few problems that I don't really know how to deal with. 

I noticed up on my top panel where the network manager's WLAN status bar normally is... well, it's not there anymore. I tried to find it in the 'add to panel' menu, but it wasn't there either. I can't seem to find my network manager anywhere. So if someone could tell me where that is I'd appreciate it.

Also, when this happened I naturally wanted to take off all the active desktop effects, but I hit a wall when the compiz fusion icon in the system tools became unresponsive. From here I figured that I'd just uninstall it altogether, but alas, after I took off the compiz icon and all the other components, the compiz effects were still on my computer and my WLAN monitor was still not where it is supposed to be. 

So I have an unresponsive compiz that won't be uninstalled, and a missing WLAN monitor.. and I don't know where to find the network manager.

If anyone could help me at all I'd appreciate it.

Thanks.

---

### Post by spiderbatdad on 2008-10-30
the network monitor-applet lives in a space called "notification area." You must have notification area added to your panel. If the applet is still missing, unlikely, try running nm-applet, after pressing alt-F2.

The compiz icon I remember was a thing called fusion-icon. I don't believe it comes from the universe or multiverse...that is I think you added it from somewhere else. It helps to start or stop compiz. Alternatively you can install compizconfig-settings-manager from synaptic and launch it from system preferences to control compiz settings. I would highly recommend upgrading to intrepid asap, as drivers and the api's, or whatever, have been greatly improved. For example compiz runs great on my older video card now, where it would not previously. On Intrepid, I noticed certain effects from the panel by default. On a hunch I installed ccsm (configconfig-settings-manager) and voila...compiz working smoothly.

---

### Post by A1len on 2008-10-30
Thanks a lot!

Works fine now. 

Planning on doing the upgrade in about a week XD

---

