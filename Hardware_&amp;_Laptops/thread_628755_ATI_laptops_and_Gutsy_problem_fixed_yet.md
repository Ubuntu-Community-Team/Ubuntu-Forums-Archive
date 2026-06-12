---
title: "ATI laptops and Gutsy problem fixed yet?"
date: 2007-12-01
forum: Hardware &amp; Laptops
---

### Post by LittleLebowski on 2007-12-01
Last time I checked, ATI's driver would not work with Gutsy and I tried Gutsy a couple of times before reverting to Feisty.  Has this been resolved?

---

### Post by ijason on 2007-12-01
i've got an ati-card in my dell laptop. i'm running the included restricted drivers and have installed XGL-Server to get compiz goodness. so far everything seems happy and stable, but i still need to look into the process of getting games to launch in their own x-server, since XGL-Server doesn't handle openGL.

---

### Post by LittleLebowski on 2007-12-01
Does suspend work?

---

### Post by nikhilgupta on 2007-12-01
I've got the radeonhd driver working (with suspend and resume) on a dell E1505 with mobility radeon x1300. Although there is not 3d acceleration yet, the driver is quite usable.

---

### Post by LittleLebowski on 2007-12-01
Does anybody have suspend and 3D working?

---

### Post by LittleLebowski on 2007-12-01
I see other Gutsy laptop users having the same issues, anyone have an ATI card with 3D and suspend working?

---

### Post by bomanizer on 2007-12-02
> **LittleLebowski said:**
> I see other Gutsy laptop users having the same issues, anyone have an ATI card with 3D and suspend working?

Me here! Altough the gui-experience would be better with the low latency kernel, but low latency = no suspend / hibernate :(

see here: [http://ubuntuforums.org/showthread.php?t=584439&highlight=radeon+7500+acceleration&page=2](http://ubuntuforums.org/showthread.php?t=584439&highlight=radeon+7500+acceleration&page=2)

Using Thinpad R50 & ATI mobility radeon 7500.

---

### Post by s3phiroth on 2008-03-01
> **nikhilgupta said:**
> I've got the radeonhd driver working (with suspend and resume) on a dell E1505 with mobility radeon x1300. Although there is not 3d acceleration yet, the driver is quite usable.

Hi there. I have a newly acquired Sony Vaio with a mobility radeon x2300 and i'm also using radeonhd (the only way i could get X to start).

Have you taken any special steps to get suspend/resume working ? Or did it work out of the box ?

---

### Post by Foster Grant on 2008-03-01
No suspend/resume here (Gateway MT6451 with the ATI driver installed).

And now, finally, some answers.

There's a problem in the ATI proprietary driver included in Gutsy (fglrx kernel module), and it's been [well-documented at Launchpad](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653), I'm going to disable the proprietary driver and see if that makes a difference.

---

### Post by nikhilgupta on 2008-04-22
> **s3phiroth said:**
> Hi there. I have a newly acquired Sony Vaio with a mobility radeon x2300 and i'm also using radeonhd (the only way i could get X to start).

Have you taken any special steps to get suspend/resume working ? Or did it work out of the box ?
I got suspend/resume working without any additional effort. The only thing that I did was disabling the atieventsd from running, but I don't think that it mattered.

---

