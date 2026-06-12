---
title: "Mount Points for Multi Ubuntu/Linux Installs and Partitions"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by mbender on 2009-05-14
Hello,

I am trying to figure out how you set the mount points when installing multiple distributions without sharing any folders but the swap drive.  Here's my current setup according to the partition editor:

/dev/sda1 mounted to /
/dev/sda2 mounted to /mnt/sda2
2 GB swap drive

My question is this.  Is there a correct way to set the mount points for multiple installations so that nothing gets messed up?  Keep reading for an example.

 A few months ago, I had the entire drive setup with just a Xubuntu install on a single partition.  I tried out Kubuntu-desktop with this and it cluttered things up too much so I decided to re-partition the drive to make room for another installation.  So the old Xubuntu/Kubuntu install is now sda2 and I install a fresh Xubuntu install on the newly created sda1.  When I got to the partition setup of the new install, I set the new sda1 mount point as /, and the old sda2 partition was automatically defaulting to /boot, which is how I left it.  Long story short, the install on sda2 comes out unusable.  It will boot but the entire drive got owners and groups on all the files somehow scrambled.  Nothing needing root priveleges will run.  A little research on the web says this is basically unfixable.

I'd go ahead and try wiping the old install on sda2, installing something new, and using / as the mount point for both partitions but I'm not sure you can do this.  I'm somewhat new to linux so please forgive any ignorance.

Thanks,
Mike

---

### Post by dandnsmith on 2009-05-14
When you have multiple linux distros/versions, you can keep them separate by using a separate partition for each. It is, I think, best to select a separate partition for /boot initially (so that, if you decide to blitz the first install, the grub files can be kept intact).

What you don't do is to arrange to mount one installs / when you're using a different one (except for copying purposes) - each install partition will be mounted as / when you boot it.

I don't know how your destruction arose - I've never seen anything like that happen.

I hope that clarifies things a bit

---

