---
title: "Can't mount my 2tb internal HDD"
date: 2013-02-07
forum: Hardware
---

### Post by ALEXALEX1432 on 2013-02-07
Hi everyone,

I have ubuntu installed on an SSD and I have a 2tb HDD that I like to keep my media on.  I did a fresh install of ubuntu because I was having some other problems and everything was fine for the first few days.  After I installed a few things, I am getting the attached error and I have no idea how to solve it.

Any help is appreciated, thank you.

---

### Post by linuxtechguy on 2013-02-07
Are you sure that the 2tb harddrive is formatted in ext4? Maybe you have the filesystem type wrong.

---

### Post by ALEXALEX1432 on 2013-02-07
Yes I am 100% sure it is formatted in ext4. I formatted it, transferred ~320gb worth of media and then the next day I wasn't able to mount it.  I'll double check in gparted

---

### Post by ahallubuntu on 2013-02-07
~

---

### Post by ALEXALEX1432 on 2013-02-07
> **ahallubuntu said:**
> Have you checked the drive's S.M.A.R.T. status with GSmartControl?  You can install GSmartControl in Ubuntu.  Look for any Attributes highlighted in pink; if none are, the drive is probably not failing.  If any Attributes are highlighted in Pink, what are they?

Nothing in pink,

Thanks for helping me, though.

---

### Post by ahallubuntu on 2013-02-07
~

---

### Post by ALEXALEX1432 on 2013-02-07
> **ahallubuntu said:**
> Looks healthy.  Looks like an almost new drive.

What kind of other problems caused you to need to do this re-install?  Perhaps you have some other system hardware problem.  Example: I had a failing power supply once that caused a corruption on one of my hard drives.  The drive was fine; the power supply was bad.

Yeah it is a new drive. The reason I uninstalled was because I was having problems with my graphics drivers (I have a rotatable monitor, and it kept defaulting to vertical mode when I wanted it to default to horizontal mode. It was a relatively fresh install so I didn't mind it. I also just had a bunch of experimental things I installed like VMware and a few things through wine that I wanted to try out)

This might be related though, I was having a problem with Plex Media Server which I had a thread going on over on their forums ( [http://forums.plexapp.com/index.php/topic/59315-ubuntu-permission-help/page__pid__350301](http://forums.plexapp.com/index.php/topic/59315-ubuntu-permission-help/page__pid__350301) )

---

### Post by ALEXALEX1432 on 2013-02-08
SOLVED

This link helped me out. Apparently I had a bad superblock
[http://ubuntuforums.org/showthread.php?t=1245536](http://ubuntuforums.org/showthread.php?t=1245536)

I would HIGHLY recommend not forgetting the recursive yes part " -y" because I probably hit "y" 500+ times.

However, after it was done what it was doing, I am able to view my hard drive

---

### Post by ahallubuntu on 2013-02-08
~

---

### Post by ALEXALEX1432 on 2013-02-08
Will do!

I definitely will not hesitate to RMA it if it gives me even one more problem.

---

