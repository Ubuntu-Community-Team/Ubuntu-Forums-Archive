---
title: "Question about partition(s) on my backup drive"
date: 2023-10-29
forum: Hardware
---

### Post by paulshaffer4 on 2023-10-29
Ubuntu 22 lts

I have an internal, bootable drive that has my Ubuntu OS on it, is a 1TB  SSD that when I examine it in "Disks" it has 2 partitions - one is a file system partition about 537 MB in size

I formatted the drive that's built onto the mother board of my HP Desktop, using it as a backup drive even though it's faster, but it doesn't have such a file system partition - should it, or should I create one?

Two images attached of each drive.

---

### Post by deadflowr on 2023-10-30
The 537Mb partition is your efi partition.
It holds the efi data required to boot while in UEFI boot mode.

No need for it to exist on the backup drive.

---

### Post by paulshaffer4 on 2023-10-30
> **deadflowr said:**
> The 537Mb partition is your efi partition.
It holds the efi data required to boot while in UEFI boot mode.

No need for it to exist on the backup drive.


Thank you so much deadflowr,

I thought that perhaps the backup drive needed a little partition, to swap data or something, but if no partition is needed on it because it's not a boot drive, then great.

Some, on another forum, suggested I use the 256 GB drive for my OS and boot, because it's faster, but that would kinda confuse me.  I like my 1TB SSD to be my main boot and storage drive.   The 1TB is plenty fast as it is, and I don't have the skills to make the 256 GB drive as the boot one and automatically store my data on my 1 TB older SSD drive.

Thanks again!

---

### Post by yancek on 2023-10-30
I don't know enough about hardware to be definitive about this, but I don't know why one SSD drive would be faster than another.  One an off brand, poor quality drive?  Maybe because 1 drive is larger?  As to putting everything on the smaller drive, you could get help here but as you seem unfamiliar with the process and small mistakes can have serious consequence, I would not waste the time if I were you.  Stay with your current  setup.

---

### Post by coffeecat on 2023-10-30
Your 256GB drive is /dev/nvme0n1 = NVMe SSD
Your 1TB drive is /dev/sda = (probably) SATA SSD

Notwithstanding any speed differences between manufacturers, NVMe drives are much faster than SATA solid state drives. I believe in the region of ten times faster. That's why the usual advice is to put the OS on the NVMe drive, where the higher speed is advantageous, and use the SATA drive for data.

---

### Post by TheFu on 2023-10-30
> **yancek said:**
> I don't know enough about hardware to be definitive about this, but I don't know why one SSD drive would be faster than another.  One an off brand, poor quality drive?  Maybe because 1 drive is larger?  As to putting everything on the smaller drive, you could get help here but as you seem unfamiliar with the process and small mistakes can have serious consequence, I would not waste the time if I were you.  Stay with your current  setup.

There can be a huge performance difference in SSDs for a number reasons.  Cheaper ones don't have more expensive fast cache chips that is common in better quality models.  This is why some relatively new SSD vendors can sell for 20-40% less than the more established vendors.  Plus the wear leveling controllers used in some of the better brands is significantly better than the cheapo "do your best" controllers in the cheap SSDs.

Whether any user would notice the performance differences between vendors and models is a different question.  The first SSD I had was slow and cheap inside a Chromebook. It was from Kingston, but I quickly needed more than 16GB of storage, so I bought the cheapest m.2 SATA 120G SSD I could get. Think it was from "dogfish" - not a name many people know.  That SSD lasted under 2 yrs before is went read-only and eventually even read failed. "He's dead, Jim."  I was lucky, since many SSDs fail completely without going read-only for weeks before death.

My next SSD was a Micron 512GB SATA SSD. It replaced a "Blue" 500GB HDD. Micron is the manufacturer behind a few storage brands you know well.  I think WD bought them, so all those WD SSDs are really MicronSSDs.  They are almost top tier SSDs, but not quite, unless you buy the datacenter specific models, which I didn't.  Performance between the Micron and spinning rush HDD was probably 3-5x faster, so I was happy.  I still have that SATA SSD, but it has been moved to an external enclosure and is used as sneakernet storage for transferring files.  

It was replaced by a 1TB m.2 NVMe Samsung 980 PRO.  Honestly, I only see the better performance when moving large files around.  The older SATA SSD wasn't used for file storage, it was used just for VMs and the OS.  The 980 PRO is an excellent SSD with a reasonable cache.  I still don't default to using it for file storage, just VMs and the OS on the computer.  I think it is a gen3 NVMe SSD, so about 32,000 Mbps is the theoretical max.  The Micron max was around 4,400 Mbps. Hugh difference, that I never actually feel, but I suppose people who use their SSDs for all storage would come to notice the difference between 4.4Gbps and 32Gbps, right?

I have another system with a Samsung 970 EVO (not Pro) and it performs nice as well.  I started using it for file storage a few months ago because I had an issue that may have been caused by a too slow disk unable to keep up with all the data being saved in real-time.  Turns out that wasn't actually the root cause of the problem, but I've already migrated a scratch area to be used on the SSD.  It is working well, though when the weekly trim task runs, about 50GB is reported as trimmed.

```
/etc/cron.weekly/fstrim:
Weekly fstrim job run 
/boot/efi: 43.2 MiB (45271552 bytes) trimmed on /dev/nvme0n1p1
/var: 9.3 GiB (9949540352 bytes) trimmed on /dev/mapper/vg00-var
/home: 799 MiB (837763072 bytes) trimmed on /dev/mapper/vg00-home
/TV:** 46.2 GiB **(49602633728 bytes) trimmed on /dev/mapper/vg00-lv--tv
/boot: 0 B (0 bytes) trimmed on /dev/nvme0n1p2
/: 1.3 GiB (1367961600 bytes) trimmed on /dev/mapper/vg00-root--00

```

On the other system, 
/etc/cron.weekly/fstrim:
Weekly fstrim job run
```
/var/lib/libvirt: 0 B (0 bytes) trimmed on /dev/mapper/vg01-libvirt--01
/boot/efi: 43.9 MiB (45963264 bytes) trimmed on /dev/nvme0n1p2
/var: 14.1 GiB (15118532608 bytes) trimmed on /dev/mapper/vg01-var01
/tmp: 314.6 MiB (329867264 bytes) trimmed on /dev/mapper/vg01-tmp01
/home: 9.2 GiB (9863827456 bytes) trimmed on /dev/mapper/vg01-home01
/boot: 0 B (0 bytes) trimmed on /dev/nvme0n1p3
/: 961.6 MiB (1008300032 bytes) trimmed on /dev/mapper/vg01-root01
```
Significantly less. Though /var is being abused on both, it seems. I can only guess that is some logs, deb package cleanup and snap package rotations.
You can also see that /boot/ wasn't modified at all in the last week.

---

