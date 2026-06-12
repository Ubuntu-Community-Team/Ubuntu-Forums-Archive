---
title: "Install Ubuntu with RAID 5"
date: 2019-10-09
forum: Hardware
---

### Post by hikariws on 2019-10-09
Hello everybody.


I have a GigaByte GA-H170-Gaming 3 DDR3. Its spec says "Support for RAID 0, RAID 1, RAID 5, and RAID 10", but it doesn't offer any driver for linux.


I'd like to put 6 HDs on it, install Ubuntu, and use it as a NAS/File server. Before buying the drives, I'd need to figure some stuff, thanks a lot anybody that can help!


1) Is Ubuntu able to use RAID 5 on it?


2) Am I able to create the RAID 5 array during Ubuntu installation? If not, how to do it? Would I be able to create it from a Live USB or some sort? I'll install Ubuntu on the raid, so it must either be already present prior installation or be created during it.


3) Say I use 6 disks with 4TB each and install Ubuntu on the array. Will I be able to later upgrade then to bigger drives, like 12TB? Am I able to upgrade one by one? Or what's the best procedure for that?


4) Am I able to mount this RAID 5 array on a Linux running from a Live USB, in case I need some troubleshoot?


5) What's the best tool to mount root and /home partitions and backup them to /nas one?

---

### Post by TheFu on 2019-10-09
My advice.

RAID solves 2 issues.  High Availability is the main thing.  RAID is a slight hassle, so if you don't really need HA and have redundant power supplies, redundant UPSes, redundant NICs, then you don't have any business using RAID, IMHO.  The 2nd reason for RAID only applies to HW-RAID, slightly higher performance. With SW-RAID and a modern system, the performance is debatable.

You can learn about RAID setups using virtual machines.  Setup a VM, setup 5 or 10 or 15 virtual HDDs, then try out your "RAID" design inside the VM. See what works and what doesn't.  30 minutes doing that will actually save you time compared to asking here and waiting.  Plus, your questions here will be better since there will be hands on experience.

**Don't use Fake RAID.** That's what motherboards offer.  You get tied to a motherboard HW, which removes the flexibility that normal SW RAID provides.  You don't want that.  If you want the slightly higher performance that real HW-RAID can provide, then buy a $350+ RAID card from a reputable source that is well-supported in Linux. Basically, that means LSI.  And since RAID cards fail, you should buy 2, identical cards so when 1 fails, you don't loose access to the data.  After all, HA is the main reason to use RAID and a single RAID card is a single point of failure, which defeats the purpose.  You can google why.

Don't use RAID5 for disks over 1TB in size.  For larger disks, use RAID1 or RAID10.  It is a rebuild issue. You can google why.

Assuming you use RAID1, then you can replace the partitions 1 at a time, provided you setup partitions initially (which you should) and you make the new disk use the same sized partition.

Or you can use LVM + the RAID1/5/6 solution it provides.  LVM allows changing an LV from single to RAID with just a few commands.  If you need to, you can change it back.  LVM is freakin' awesome.

Or you can use ZFS which is good for storage systems for lots of reasons. ZFS has some very interesting advanced capabilities. It is worth trying those out inside a VM to get a feel.  Spend the 30 minutes with it and a zfs tutorial.

You didn't mention much about backups.  How were you planning to backup all this data?  Some RAID problems have only one solution - wiping everything and restoring from backups.

Tool for mounting?  mount.  Is this a trick question?  There aren't any GUI tools for this stuff - at least none that don't have serious faults.  Unix admin is CLI and text config files.  If that isn't what you want, then you'll want a different solution.  Don't try to put lipstick on a pig when the pig is already beautiful.

---

### Post by hikariws on 2019-10-10
Thanks a lot for your advices!

Today I have 2 NAS: 1 Asustor and 1 QNAP. I was reading a thread about QNAP and noticed most ppl use it as HTPC and I don't need such features, while its QTS/Busybox is very limited. A few months ago I built an Ubuntu server and moved to it all services I had on my old Win10 server. So I figured it's better to just have an Ubuntu PC, with a full linux experience, and put HDs on it, than buy such devices.

My old Win10 PC is still very good (i5 Kaby Lake, 16GB RAM), so I'll buy 6 HDs and reinstall Ubuntu on it and move all services to it. I'll have what I need from a NAS and a good server.

I have my Asustor with 2 HDs in RAID 1 and my QNAP with 4 HDs in RAID 5. I'll never use RAID0, as if 1 HD dies the whole array dies. RAID 0+1 is too overkill and expensive. RAID 5 isn't so quick to recover, but it sustains 1 HD failure and I have 5 of 6 HDs as usable storage. I'm not looking so much for performance improvement, what I want is a single storage volume summing all HDs capacity, and I'm willing to spare 1 of them for fail safing.

In the volume I'll create 3 partitions: root, /home and /nas. The first 2 with 20GB and /nas with most the storage.

Regareding mobo provided RAID and hardware RAID, then these both solutions strict the volume to the hardware that created it? If the mobo or the card die, I lose access to the whole volume? And doesn't that happen with software RAID?

In example, can I create a RAID volume with Ubuntu, and then boot from Parted Magic and mount this volume and use Clonezilla to backup root? Or even better, boot from Ubuntu live USB, create the volume, then install configuring it to mount, and also mount from Parted Magic.

Regarding tools. I was just searching for a new backup solution when I asked that. Currently I use Acronis True Image to backup Windows, I haven't yet tried it for lix. I just got mad with it, because I (also) just got a Intel NUC and True Image didn't recognize its network chip. What I have been doing is connect to my NAS over FTP, True Image is able to create, restore and validate backups from FTP. But now, without network, I was unable to do it.

I was then thinking on moving to a open backup solution. Boot from USB into a real linux system, mount my NAS over SSH, and do the job. My question was dumb, what I meant was what driver/software/whatever I'd need to be able to mount my RAID volume on a linux live USB. Then I can mount root and /home and back them up into /nas directly, as I'm booting directly on my NAS.

I'll indeed create a VM with 6 VHDs and do some tests. But I need some suggestions on what software to use, and I can't test mobo and hardware RAID on it or if I can move the volume to other hardware if needed, then I had to ask its differences over software RAID. I'd also like some advices regarding risks.

Again tnx a lot!

---

