---
title: "Can't boot after hard drive change."
date: 2007-01-07
forum: Hardware &amp; Laptops
---

### Post by WetWired on 2007-01-07
Ok, here's the deal. I added a new hard drive to my system, and the way my case was arranged, I had to swap some ide cables, jumpers, everything. Anyway, obviously Ubuntu doesn't like that. Now, when I boot, I get a waiting for root filesystem error. I've tried remounting it, and I've tried avms_activate, but to no avail.

I don't remember what I did, but I got it to spit another error at me. It told me hdb5 doesn't exist, because it's now on hdA5, or so the "Disks" program on the system menu tells me (live cd)... is there any way to recover from this?

---

### Post by WetWired on 2007-01-07
I guess what I need to do is tell it to look for hda rather than hdb... is that possible without a reinstall?

---

### Post by WetWired on 2007-01-07
Anyone have any ideas?

---

### Post by bmt on 2007-01-07
All you need to do (lol) is install grub again, so that it knows where the OS is.

The general procedure is to boot with a LiveCD, mount the hard disk partition containing Ubuntu and run grub-install from that partition, telling it what the new location is for the boot partition.  Google 'grub-install' (from the LiveCD, if necessary) to get more information.

Sorry I can't be more specific, but I don't know exactly how to do it without researching, but I hope that will get you started.

---

