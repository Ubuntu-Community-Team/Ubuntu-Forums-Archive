---
title: "P4  can't get LiveCD to work..."
date: 2007-05-25
forum: Hardware &amp; Laptops
---

### Post by nineteeneightyone on 2007-05-25
I've installed Ubuntu on a couple of machines succesfully (inluding parts I've salvaged from a dumpster) and wanted to do the same on an old P4 box laying around at work.

As far as I can find out it is a:

Intel D850GB Desktop Board 400Mhz
Pentuim 4 1.40GHz

I'm trying to run a liveCD first but have a frustrating couple of issues:

1). After the install/liveCD screen an error flashes up that reads:

08:49:09 mail kernel: Uhhuh. NMI received for unknown reason 2d on CPU 0.
08:49:10 mail kernel: Dazed and confused, but trying to continue
08:49:10 mail kernel: Do you have a strange power saving mode enabled?

However the LiveCD continues and gets to the loading screen (sorry newbie)...

2). and then seems to hang loading Nautulis and comes back with the following error:

There was an error starting the GNOME Settings Daemon.
Some things, such as themes, sounds, or background settings may not work correctly.
The last error message was:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken. 

I've googled both errors and have tried pulling all the PCI cards out, reseating and switching around the RAM modules, tried adjusting the power setting via the BIOS - but to no avail, nothing at all seems to be able to get around this issue using the LiveCD (I've tried checking the CD for defects, Memory Test etc), tried adding noipv6 and notsc on the install options, tried reconfiguring the x-server but nothing happens.

Any help or pointers in the right direction would be gratefully welcome.

Thanks.

---

### Post by Immolatus on 2007-05-25
Try a Knoppix live cd or fedora core 6 live , as they have slightly different hardware compatibilities. For example my pcmcia sound card works in fedora by default but not ubuntu.
Just to rule in or out hardware issues. The P4 should work though, I rum feisty on a Pemtium M (laptop). It's basically a low power p4 so it should work.

---

### Post by nineteeneightyone on 2007-05-25
Thanks - I'll have to take a look with the other distro's on Tuesday. Still it's a shame trying to persuade other users to take the Ubuntu challenge only to witness me having a royal to-do with getting it running.

---

### Post by Immolatus on 2007-05-26
please post the result, I'd be interested to see.

---

### Post by tturrisi on 2007-05-26
Go into the bios and if supported, set it to load fail safe defaults.  Boot the live cd.
If ok, reboot, access bios and load optimal defaults.  Boot live cd.
If ok, one by one make preferred bios changes until see where it begins to break down.

---

