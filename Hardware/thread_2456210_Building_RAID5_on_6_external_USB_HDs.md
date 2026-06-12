---
title: "Building RAID5 on 6 external USB HDs"
date: 2021-01-06
forum: Hardware
---

### Post by hikariws on 2021-01-06
Hello. I'm building a new NAS, and it's gonna have 6 external USB HDs. As they are so many, I wanna build a RAID5 array on them, so that I'm safer in case any of them fail, and also to merge their storage.


Is there any issue I must be aware of?


I'm testing connect them on the server, using a USB hub which has its own power cable. I notice that each time I unplug and replug them, they receive a different /dev/sdx name. Is there any way to give a fixed name to them?


To build the RAID5 array, do I need all the HDs to have the same order, or is mdadm able to handle them in any order?


It's troubling if every time I reboot the server I'd need to figure their names, but it's gonna be impossible to keep them on the array if every time I need to figure them in a proper order.

---

### Post by TheFu on 2021-01-06
Using USB for RAID connectivity is a terrible idea. USB connections flake out all the item.  Stick with internal SATA and eSATA and Infiniband connections. Almost always, USB storage devices will insist on spinning down drives which will cause problems for RAID arrays too.

Don't expect a USB hub to help things at all.

As for device names, there are multiple solutions for that. Use UUIDs is generally the best one for disks, but you can use any of the links created under /dev/disk/*  by-path/ is probably the next safest, provided you don't change which port a device is plugged into.  There is no guarantee for device names following the /dev/sd?? naming.  That is purely determined by timing of the kernel and devices. There's no reliable way to predict it with multiple devices.

Did I mention that you shouldn't ever use USB devices for RAID connections?  You shouldn't.

---

### Post by hikariws on 2021-01-07
Tnx a lot for the tips.

Indeed, I had issue because all tutorials I had used fdisk to partition the drives, and all tutorials used VM virtual drives or small HDs for testing. Of course my HDs are bigger than 2TB and MBR doesn't work. I had to look for how to partition Linux RAID on GPT, learned about parted and how gparted doesn't support it, and then UUID and partuuid, to finally learn about labels and /dev/disk/by-label/.

Anyway, I had already partitioned 5 of them, so I'm gonna try the RAID. I've been using USB HDs connected to my QNAP and never had any issue like USB connection or them being turned off. I'm gonna test the RAID for some days without any file present exclusively on them, to see how it works. At the worst, I'll have first hand experience on the issues that might arise.

About the hub, I mensioned it because USB HDs do suffer from lack of power. On the 4 HDs I just bought, I used my Intel NUC to make surface scan test on them, and during the first one I plugged it on a back port. It was detected, its file system was available and all looked good, but surface test app just stopped after start. It didn't hang or crashed, it just stopped. I then plugged it on the orange port with quick charge, and it worked.

---

### Post by TheFu on 2021-01-07
You are using non-powered USB disks?

Crazy, you are.

Problems don't happen on demand.  They wait, until you really don't have time to deal with the issue.  THEN.  Your storage is down.
Regardless, you've heard this before, RAID is never a backup. You still need backups.  With some RAID issues, the best answer is to wipe the assembled array and start over.

RAID solves 2 issues, no more.  Backups solve 1000+ issues.  Backups are 9998x more important than RAID.

fdisk, parted, gparted all deal with RAID just fine - but I suppose it depends on what you expect.  Don't do any RAID stuff except marking partitions as RAID members in any of those tools.  Use mdadm for everything else ... assuming you don't want to have the power of LVM and let it handle the RAID stuff.  Or if you want to skip all this stuff and jump to where you'll want to be in 3 yrs, forget mdadm and use ZFS now.

Regardless, USB is a bad idea.

---

### Post by hikariws on 2021-01-07
Yeah I get that, I will probably just wipe them once the RAID is done and tested. It's not worth the risk, still I had learned a lot in these 2 days. I had created a RAID on a VM prior, but as tutorials did, I was using 1GB virtual disks. Now on real HDs I had faced more than a couple of issues that no tutorial tell and haven't seen on VM.

I verified gparted and at least couldn't find raid option. fdisk/MBR has a partition code - fd - specific for linux raid. parted has a flag. At least that's how their UIs show it.

I have 2 HDs with AC power. The problem is the need for connectors for each HD. USB powered HDs don't need that. But not all USB connectors are able to feed their hunger.

Backup is troubling. I have tens of TB of files, on 2 NAS and almost 10 external HDs. I'm struggling to be able to increase my storage capacity, it'd be even more expensive to duplicate it.

And backup doesn't solve all issues. If the building burns and my backup is at home, it will all be lost.

Still, I have CrashPlan service subscription. I've been spending all my upstream for almost 2 years, and haven't backed up 20% of my stuff. Twice I had needed to download something from them, neither from HD failure. Yet.

What scares me is that a few years ago my 2nd NAS was getting full and I had to start using external HD to increase capacity. 1 NAS has RAID1 and the other has RAID5, USB HDs are hopeless. I just built a new PC to use as my personal server. When I have the money I'm gonna buy 6 (SATA) HDs and build a RAID on them. But I had to buy a couple new USB HDs, so I decided to try RAID5'ing them.

**6 HDs on RAID5 is safer than 6 HDs with no RAID, isn't it? Or do you think it's not? And they also have their storage joined.**&#8203; I haven't mentioned it before on the thread, but let me reinforce that I'm using these USB HDs regardless of them being on RAID or not.

Anyway, I finished the setup and it's reporting 10 days to be created. Let's see if this estimation is right, and if any issue will happen during it.

---

### Post by TheFu on 2021-01-07
> **hikariws said:**
> Y 
Anyway, I finished the setup and it's reporting 10 days to be created. Let's see if this estimation is right, and if any issue will happen during it.

10 days!  Those must be the slowest drives made! 10 minutes is what I would expect, but it as been a few yrs since I built anything RAID5.  Have you looked at raidz and raidz2?

If this storage is for media files, modern media center software will happily merge multiple storage locations into a single virtual view. No need for us to bother at the OS or file system level. No need for the added complexity.

---

### Post by hikariws on 2021-01-07
Yes, looks like it's not going well, it's been a few hours and it's on 1,5%. 6200KB/s. I've read some threads of ppl having their array losing some drive after some weeks and having to resync. Building scripts to verify if all drives are available before mounting, scary.

I don't like these media centers. For video, I only accept MPC-HC.

---

