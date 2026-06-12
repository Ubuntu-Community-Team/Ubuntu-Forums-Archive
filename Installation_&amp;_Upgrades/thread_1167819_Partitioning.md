---
title: "Partitioning"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by neoncode on 2009-05-23
For the last few years I've been running my PC with 5 hard drives. 4 250GB drives in software (mdadm) RAID5 for /home and a Western Digital 10,000RPM Raptor for /, swap and Windows Vista (I use Vista for gaming so it can benefit from the speed increase.)

However the Raptor is only 150GB and with Vista and various games takeing up the majority of the space I only had 10GB for /. This was fine for a while but it's been a little tight. For example I'm still on Kubuntu 8.10 because I don't have enough temporary space to perform the upgrade.

So I have recently taken delivery of a brand new shiny 160GB drive. My question is what's the best way to setup the partitions? I want to keep the four 250's in RAID for /home and Vista on the Raptor. So I was planning to Put /tmp, /boot and swap on the Raptor but move / to a 40GB partition on the new drive.

Is this a good idea or is there a better way to do it?

---

### Post by GOfree on 2009-05-23
Hi,

Your setup is way more complex than I am used to, so I will probably not be much help to you.

But here is my (non-expert) opinion...

How about keeping everything together on one partition except swap? 40 GB should be more than enough.

Personally, I don't like having /home on a separate partition, because it make sense to me to keep the configuration files specific to the OS exclusive to that OS. I have tried dual boot setups with a shared home directory, and that did not work very well.

Instead of using /home for storage, how about setting up a "/data" (or whatever) partition that is solely for documents, pictures, music, etc?

When it comes time to upgrade, you might want to start with fresh /home configurations, but obviously leave your /data storage files alone.

Also, the /data partition works well with a file server.

---

### Post by neoncode on 2009-05-23
Thanks for your advice but the main reason I have my /home in a RAID array, other than extra space, is redundancy. If a drive fails then I don't loose any user configuration or data. Also I wanted to put /tmp on the faster drive to try to get better performance. 

I figure even if the increase in speed from the raptor is only slight, simply having /tmp and / on a different drive will be a good idea. Especially with /tmp being accessed a lot in general usage.

What I've tended to do when a new version of ubuntu comes out is install the new version on / fresh, then just mount the RAID array as /home and make sure all the permissions are set for my main user and all my pre-reinstall settings are still there. 

I only have the one copy of Linux on this system anyway so I don't need to worry about different versions or anything messing up the config files on /home.

---

### Post by neoncode on 2009-05-24
Can anyone else offer advice? :o

---

