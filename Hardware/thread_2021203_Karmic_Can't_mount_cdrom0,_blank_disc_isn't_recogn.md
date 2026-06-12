---
title: "Karmic: Can't mount cdrom0, blank disc isn't recognized"
date: 2012-07-08
forum: Hardware
---

### Post by Robin-chan on 2012-07-08
**Edit: **Tried to update with the update manager... now I can't run Ubuntu at all. Tried to use Wubi but I keep getting error code 7. Not sure if I should make a new thread or not...

Okay, my OS is badly outdated, I know... and that's what I'm trying to fix. Got a little problem with that, though.

After having spent a lot of time on my other laptop, I've had to temporarily go back to this one, which only has Vista (doesn't work) and Ubuntu. Since it's been so long since I've worked on here, I'm still on Karmic, and when I try to update anything, the links all seem to be broken.

So I figured I'd check out the newest release and get that. Downloaded the iso and all that jazz, then popped in a blank CD for burning and stumbled upon my problem.

I right-clicked on the iso, chose "Write to disc", then the Image Burning Setup window popped up. However, even though the drive makes noises sometimes like it might be working, it says there is no disc available to write to.

I wanted to check to see if the CD was in fact blank in case that was my problem, but when I try to open cdrom0, it gives me this error:
Unable to mount cdrom0
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I've checked a dozen old threads and I've had no luck finding a solution. I fear that no one will help because my OS is so old, but I don't have any other way to upgrade unless I want to try wrestling with Vista and see if it would let me burn a CD (chances are, it won't).

---

### Post by Robin-chan on 2012-07-09
I tried to use the update manager to update and now Ubuntu won't work, I just get stuck at endless disk check screens without the system even fully booting. And I'm on my Vista partition trying to install with Wubi but I keep getting error code 7. Should I start a new thread?

---

