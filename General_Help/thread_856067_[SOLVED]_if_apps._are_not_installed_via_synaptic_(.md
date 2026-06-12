---
title: "[SOLVED] if apps. are not installed via synaptic (3rd party soft.) is a separate /usr"
date: 2008-07-11
forum: General Help
---

### Post by streamsanddragonflies on 2008-07-11
Hi!
I had asked a similar question about /home partition since I want to install hardy fresh on 2 separate small SCSI drives (linux dir. supposedly work fine on multiple drives, right?).  Since I use Ubuntu Studio and some software are not automatically available through synaptic and their dependancies are multiple and a bit of a pain to install, I am hoping to find the simplest way to keep them when the version upgrades happen.  This will be my first upgrade; I waited for it to become stable since I am still not well versed in the linux world and I haven't gotten around to backing up Gutsy yet...

It seems that this is the long term version- 3 years- so I shouldn't worry.  but when the upgrades are every 6 months, isn't there a way of creating a separate partition for all 3rd party apps. so I can upgrade without problems and keep my apps?  I saw an forum entry on partitionning a separate /usr but I can't seem to find it...

I already had to manually install the last time so even though I have multiple drives, I think I'll manage, but I'd like to know if this is ok to do or not and the best way to configure my installation!?

:confused:

---

### Post by ad_267 on 2008-07-11
I think you would want the extra partition mapped to /usr/local or /opt as those are the two places where applications are usually installed if they are not installed through a package manager.

I haven't done this but it should work just the same as having a separate /home. Create a new partition using the live CD and then mount it at /usr/local.

---

