---
title: "How to? Get db and recordings from old/new Myth"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by MykeBuntu on 2009-02-03
I'm new in *nix so be gentle. I *think* I am in the right place for this question:

I recently set up Mythbuntu 8.10 box. It has a 1tb drive. I started in November with a 500gb drive and MB 8.04.1... to do the 8.10 install I just disconnected the old drive and connected the new.

Now-- I'd like to transfer the recordings done on the old system to the new. THE ONLY CHANGE was the HDD; I have 2 HDDs physically in the PC and only 1 has ever been powered at once. As I was testing I just had to power down and move power and data cables from one drive to the other.

Please confirm whether the following assumptions are correct and that these steps won't cause me a problem:
* If I do nothing but power down and run power and data to the 500gb drive-- and tell BIOS the boot drive is the 1tb, the system will boot as before with no problems. It will be READY to use the 500gb but won't "mount" anything yet.
* Assuming the old 500gb drive is similarly configured-- I think it will become "/dev/sdb" on boot and I should be able to find my OLD ROOT DRIVE at "/dev/sdb1" and my old mass storage stuff (all recordings,video and hopefully the db?) at "/dev/sdb6"-- running "sudo fdisk -l" should give me enough information to alter the names appropriately-- if it comes up as "/dev/sdc" as an example.
```

**_RESULTS FOR "sudo fdisk -l"_**
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008d9b2
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1459    11719386   83  Linux
/dev/sda2            1460      121601   965040615    5  Extended
/dev/sda5            1460        1583      995998+  82  Linux swap / Solaris
/dev/sda6            1584      121601   964044553+  83  Linux

**_PARTIAL RESULTS FOR "mount"_**
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
...
/dev/sda6 on /var/lib type xfs (rw)

```
If the above assumptions are correct and I want to mount the OLD DRIVE to get recordings and recording metadata into my new system-- does this get me there without danger:

sudo mkdir /media/gb500varlib
sudo mkdir /media/gb500root
mount -t xfs /dev/sdb6 /media/gb500varlib
mount -t ext3 /dev/sdb1 /media/gb500root

Do I need to tweak permissions? once? each time I mount?
I think "mkdir" only has to be run 1x but "mount" each time I boot-- I don't want to make this permanent until after pulling data across-- but that'll add OTHER questions about reformatting/partitioning.

If I do this-- I *think* I could at least pull the recordings across-- into my **_videos_** folder on my 1tb drive. If I can extract the appropriate data from several tables in the 8.04.1 db-- I think I could get the metadata as well--and thereby save the files in the **_recordings_** folder instead.

---

### Post by MykeBuntu on 2009-02-05
Am I going in the right direction?
Did I ask this in the *wrong* place???

---

### Post by MykeBuntu on 2009-02-28
One more try to get a response.

---

