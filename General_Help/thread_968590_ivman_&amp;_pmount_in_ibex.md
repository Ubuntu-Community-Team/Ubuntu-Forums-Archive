---
title: "ivman &amp; pmount in ibex"
date: 2008-11-02
forum: General Help
---

### Post by superbondbond on 2008-11-02
I use fluxbox as my window manager, because I find it much faster and simpler than GNOME.

When I was running 8.04, I used ivman and pmount to handle the mounting of my CD drives and other removable media (SD cards, jump drives, etc).

Now that I've upgraded to 8.10 this no longer works. I installed ivman and pmount, and the first thing I noticed was one of the CD drives would not mount, while the other one did. I ran ivman from the terminal and it gave me this:
```
Error: device /dev/scd1 is not removable
Error: could not execute pmount
```
What I discovered was that the first CD drive (scd0) had an entry in the fstab (pre-configured at installation), and would mount OK. So I added an entry for the second one, and now it works too.

Now I'm left with the same errors for each USB and SD card I connect. I never had specific entries in fstab for each device before, and they would mount without problems before (all handled by hal I assume).

It still gives me the "device is not removable" message even though I get this

```
root@optiplex:/# cat /sys/block/sde/removable 
1
```

Something changed in 8.10 that this no longer works. Any advice or clues to this puzzle would be greatly appreciated.

Thanks

---

### Post by Pete N. on 2008-11-03
Had the same problem as you and wasted 2 hours on worthless fstabbing AGAIN (my external drive has been a problem since Ubuntu 7.04).

Easy fix for pmount "Error: device /dev/scd1 is not removable"-problem.

Add "/dev/scd1" to the "/etc/pmount.allow" -file.

---

### Post by superbondbond on 2008-11-03
Thanks Pete.

That was going to be my next step. I'm happy if that solves my problem, but this sure smells of bug.

Off to search through bugzilla......

---

### Post by nxmehta on 2008-12-09
Has anyone taken a look at this recently?  I get the same "Error: device is not removable" message for a usb stick that is very clearly marked as removable by looking at lshal.  There is clearly something wrong here.

---

### Post by PorcelainMouse on 2009-02-06
All,

You might find this useful: [http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg599440.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg599440.html).   Basically, it says the bug is in libsysfs, which will not likely be fixed soon, and a workaround from pmount development is forthcoming, but will also take some time.

---

