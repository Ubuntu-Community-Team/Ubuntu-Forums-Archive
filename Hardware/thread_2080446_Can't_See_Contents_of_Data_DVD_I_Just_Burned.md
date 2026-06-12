---
title: "Can't See Contents of Data DVD I Just Burned"
date: 2012-11-04
forum: Hardware
---

### Post by DrewT on 2012-11-04
I've found a lot of threads about optical disk drives not mounting properly, but I haven't seen anything like this. I just burned a data DVD in KDE. When finished the disk was ejected. When I pushed the drawer back in, the drive spun for a while but nothing happened. Tried the other drive (a blu-ray drive) and even less happened. 

But when I run

```
wodim --devices
```

both drives are correctly identified. Also, both drives can "see" other disks. This might suggest the disk is defective, but it seems to work fine in other machines. In fact -- here's the really weird part -- I can see the disk and browse its contents in a VirtualBox XP guest running under the same Ubuntu host that can't see it.

I am running under a (mostly) clean install of 12.10. I'm also seeing the [_[COLOR="Blue"]Unable to mount Blank DVD-R Disc[/COLOR]_]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1071739") bug. I doubt the problems are related, but who knows?

---

### Post by DrewT on 2012-11-04
So to summarize, both drives are working in Ubuntu but the OS seems unable to mount some disks, even some that were burned under Ubuntu. 

Where would I start to troubleshoot such a problem? (As I said above, it seems especially weird that a disk can be invisible in Ubuntu but visible in another OS running as a guest of Ubuntu in the same session.)

---

