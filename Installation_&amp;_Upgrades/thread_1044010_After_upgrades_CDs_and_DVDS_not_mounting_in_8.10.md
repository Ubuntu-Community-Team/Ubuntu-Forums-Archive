---
title: "After upgrades CDs and DVDS not mounting in 8.10"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by Sorandal on 2009-01-19
Hi, I installed ubuntu 8.10 64bit, and basically everything was working, and then I did two things, I installed the restricted drivers so that I could play DVDs, and I installed a long list of upgrades.  One of these things caused CDs and DVDs not to be mounted.  I don't know how to manually mount a CD.  

I believe that one of the upgrades is probably the culprit because I installed Kubuntu, then installed the gnome desktop, and installed the updates previously, and the same thing happened, no cds/dvds would mount.  That is when I did a fresh install of ubuntu (Using Wubi).  

I am running an ASUS x83vb-x1 laptop (similar to the N80).

since it is a fresh install it wouldn't be a huge deal to reinstall if it comes to that, but I don't really want to have it happen again as soon as I download the buggy update.  any ideas?  also how do you manually mount a CD?
thanks

---

### Post by Kelvari on 2009-01-19
I'm afraid I don't know how to get the discs to auto-mount again, but you can manually mount them by putting the following code in to the terminal:

```
sudo mount /dev/cdromx /media/cdrom
```where x is the number of the drive (most likely 0, but may be 1 if you have two optical drives. Feel free to experiment with the eject command to figure out which drive is associated with which dev entry.

---

### Post by Sorandal on 2009-01-19
Hi, I tried several variations on that command, and none worked.  I looked in the media folder, and there is a cdrom0.  I looked in the the /dev folder, and there is no cdrom0 or cdrom...  the only file I saw with cd in it was scd0.  I saw in terminal that it was searching /etc/fstab and /etc/mtab.  neither has any reference to a cd drive that I can see, should they?

Last time I booted my computer, it did automount a music cd, but it froze when I tried to play it.  I force quite, and it unmounted.  I just keeps spinning, and will not let me eject.  This is also what happens when I insert a cd, it spins as if it is trying to read it, but never mounts it, and will not let me eject it.

---

### Post by Kelvari on 2009-01-19
I just did a quick check, and /dev/scd0 would be your optical drive. The /dev/cdrom is actually just a link to /dev/scd0. Haven't heard of that disappearing before, but it doesn't sound like it's that major an issue at the moment. Maybe if I weren't half-asleep. :lolflag:

So, just replace the /dev/cdromx in my previous post with /dev/scd0, and it should work.:)

---

### Post by Sorandal on 2009-01-19
I get a "No medium found" message, but I think this is the correct command because before I was getting "special device /dev/cdrom0 does not exist.  It just doesn't seem to be able to manually mount it.  

If I were to reinstall, is there a way to back up old files such that I can undo certain updates?  I was thinking that this might be useful to others because I could pinpoint which update has the bug.

---

### Post by Sorandal on 2009-01-19
Okay, I reinstalled a couple of times and I reallised that the CD doesn't always work perfectly on a fresh install with no updates of any kind, but it does work.  What makes it stop working entirely is the propriatary video card driver that I need for the video card to work.  the driver is: NVIDIA accelerated graphics driver (version 177).

Any hope of finding a solution to this, or am I out of luck since it is a propriatary driver?  Is there somewhere else I should be posting on this forum, or should I be pestering NVIDIA to work out the bugs since it is their driver?

---

### Post by Sorandal on 2009-01-21
Okay, I did a little searching on the internet for other people with my laptop running ubunto 8.10, and I found that I'm not alone, and the sollution is to go into the BIOS and set SATA to compatability mode (rather than enhanced).  I think that the video driver was a symptom, not the problem.  Everything works great in now, the problem is that Vista does not seem to boot in compatability mode, so I have to change BIOS settings whenever I switch between the two.  If anyone knows a way to get around this please let me know, gland it's working at all though!

---

