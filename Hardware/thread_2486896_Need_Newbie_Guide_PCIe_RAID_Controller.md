---
title: "Need Newbie Guide: PCIe RAID Controller"
date: 2023-05-16
forum: Hardware
---

### Post by littlehome2 on 2023-05-16
I am looking for the general steps of plugging in a PCIe RAID controller including:
* Where to check if my card is compatible with server 22.04 LTS
* Step by step (specific cards or general)
     * Drivers? Software? MMDAM? <--- I think it is a boot key combination with it's own interface?

I have an LSI Logic PCIe 2 SAS controller that is not letting the machine boot, but I can easily search the "check site" for compatible cards and buy a new inexpensive model.

Getting frustrated...

I'd be happy to post some sort of "how to" from my findings if needed.

Thank You!
-j

---

### Post by TheFu on 2023-05-16
If you are using a RAID controller, then you won't be using mdadm.  mdadm is for SW-RAID and any JBOD disk connection can work.  HW-RAID has setups in the card's BIOS, before any OS is booted.

You should be clear about what the final goal is for someone to spell out what you need to accomplish those goals.  For example, I don't know how to use mdadm for a boot device in Ubuntu.  Perhaps it is possible, but I've never seen it.  

I do know how to use LVM for Linux boot, then add a mirror for the / logical volume.  LVM-RAID is sorta ugly and I'd not gotten failures to work seamlessly, as we'd expect if a disk were to fail.  Booting a system with a failed disk when LVM-RAID is used isn't automatic. It doesn't degrade gracefully, IME.

My feeling (no facts) is that to get a real HW-RAID card, then $300+ will need to be spent.

As for a SAS HBA (JBOD), to be used with SW-RAID or ZFS or LVM-RAID, I do have 2 in my Amazon lists
[LIST]
[*]LSI Logic SAS9211-8I 8PORT Int 6GB Sata+SAS Pcie 2.0 ($70 currently)
[*]Supermicro AOC-SAS2LP-MV8 Add-on Card, 8-Channel SAS/SATA Adapter with 600MB/s per Channel (unavailable)
[/LIST]
Cables that convert 1 SAS port into 4 SATA ports would be needed, if you have SATA drives. Think those are $14 currently.  I've not used these. Sorry.

Getting ubuntu to boot with mdadm may be possible.  IDK.  If I have time, I'll try on a VM system running 20.04. I don't have any use for 22.04, sorry.  [https://gist.github.com/fevangelou/2f7aa0d9b5cb42d783302727665bf80a](https://gist.github.com/fevangelou/2f7aa0d9b5cb42d783302727665bf80a) shows a layout and says that the Ubuntu Documentation is wrong.

Google found this guide [https://forums.linuxmint.com/viewtopic.php?t=391037](https://forums.linuxmint.com/viewtopic.php?t=391037) for Mint 21.1 (Ubuntu 22.04).  The key steps are the chroot at the end and the initramfs rebuild.  Hummmm.   

Interesting that 20.04 doesn't seem to need the initramfs step, but 22.04 does.  Again, these are for SW-RAID, not HW-RAID.

---

### Post by littlehome2 on 2023-05-16
Thanks, TheFu! Just what I need. Yeah, my disability makes it hard to communicate some times.

The end goal here is not to boot from the RAID - I have that in PCIe sticks on the MB. The RAID 6 will provide asset protection of data from failed drives. The data is used in different KVM and server modules. I will get that card you mentioned.

---

### Post by TheFu on 2023-05-16
> **littlehome2 said:**
> Thanks, TheFu! Just what I need. Yeah, my disability makes it hard to communicate some times.

The end goal here is not to boot from the RAID - I have that in PCIe sticks on the MB. The RAID 6 will provide asset protection of data from failed drives. The data is used in different KVM and server modules. I will get that card you mentioned.

I think you would want to research whether that card is still what you want.  I provided it as an example. My research was a few years ago.  And as we all get older, "a few" could be 15.  It isn't a RAID card.

For RAID6, I'd seriously look at using RAIDz2 with ZFS instead, but I don't know how well that will work with KVM. I don't know if there are, or are not, issues with KVM and ZFS - definitely do some research on that.  I know KVM had some issues with CoW file systems previously.

---

### Post by littlehome2 on 2023-05-16
Ah. OK. A RAID controller card has it's own UI that I use when I boot? Volumes are presented as a single drives? In that case, there is really no such thing as Ubuntu compatibility right?

---

### Post by TheFu on 2023-05-16
> **littlehome2 said:**
> Ah. OK. A RAID controller card has it's own UI that I use when I boot? Volumes are presented as a single drives? In that case, there is really no such thing as Ubuntu compatibility right?

There are 3 types of RAID.
[LIST]
[*]Software-RAID
[*]Fake-RAID
[*]HW-RAID
[/LIST]

For enterprises who are willing to have spare HW-RAID controllers stocked on-site with their support contracts from the different vendors, this makes sense.  When a HW-RAID controller dies, sometimes, only the exact same model, lot, version, can be used to access the data.  The data and card are tightly coupled.

Software-RAID has made more sense as CPUs became faster and provide tremendous flexibility.  In Linux today, there are 4 methods to have SW-RAID. They all use JBOD disk access.
[LIST=1]
[*]mdadm
[*]LVM-RAID
[*]ZFS-RAID
[*]BTRFS-RAID
[/LIST]
You can read up on the pros/cons for each of those different methods. Each has good and bad things for consideration.

FakeRAID is what motherboards and cheap "RAID cards" provide.  This mode has very little reason to be used, because it has the tightly-coupled hardware restriction AND still offloads the heavy work to the CPU, so why bother with it?  Are you going to keep a spare motherboard around to be able to access the data?  I understand there are a few edge situations where FakeRAID makes sense ... but I don't run using those configurations.

The most common way that people deploy RAID on Linux is with mdadm for the RAID, but LVM for the volume management (not LVM in RAID mode).  ZFS has been taking over many of those configurations.  BTRFS has some odd issues when multiple storage devices are used ... like would happen with any RAID, so I'd stay away from using it.  

Of course, others will have different opinions about all this stuff. Hopefully, some others will post with their opinion and correct anything I got wrong.  It isn't possible to know everything.

As for your question ... _really no such thing as Ubuntu compatibility_?  IDK.  I've only used HW-RAID on UNIX systems and the RAID HBAs came with the server from the vendor.  Once I tried to get a HW-RAID card for a Linux system at home, but failed and ended up with a Fake-RAID HBA instead that didn't have RAID drivers for any kernels after v2.6.x.   At the time, all my systems were already running v3 kernels.

---

### Post by littlehome2 on 2023-05-17
Wow. Thank you for all the time you have put in teaching me. Yes, I see your point about cards and "fake". In fact, one MB died and I have a lot of data to recover that was in storage for years (another topic).

My motherboard simply does not provide enough SATA ports, but easier to add ports than to rely on a PCIe card that may fail. VERY good point!

What about in Windows and I need software RAID 6?

---

### Post by TheFu on 2023-05-17
I care nothing about MS-Windows. Don't know.
I've never used RAID6, since RAID never replaces backups.  Never.  I stopped using RAID5 about a decade ago.  These days I only have RAID1 and RAID10 and only for really important things that aren't on SSDs ... or 1 virtual environment where the RAID1 isn't really RAID1 since both of the virtual storage devices are on the same SSD.

JBOD is JBOD and doesn't really matter for Linux SW-RAID provided the access works and performs as needed.  I've migrated an array through 3 different systems, each with different SATA controllers over the last 15-ish years. Avoid USB-connected storage for anything RAID.

---

### Post by littlehome2 on 2023-05-17
In principal I agree with you. In practice, some data is too big and/or too dynamic to back up with normal methods and some implementations need
 the speed of RAID.

---

### Post by TheFu on 2023-05-17
> **littlehome2 said:**
> In principal I agree with you. In practice, some data is too big and/or too dynamic to back up with normal methods and some implementations need
 the speed of RAID.

If you cannot backup the data, then it isn't important enough for RAID.  RAID solves 2 issues and only 2 issues.  
[LIST]
[*]High Availability
[*]Performance (sometimes, but not always)
[/LIST]
Backups mitigate 1001 issues, including a RAID failure.  So many times, we see people using RAID inappropriately.  Sometimes, RAID is just a way to have corrupted data written to multiple disks, concurrently.

I've worked places where backups of our data required over 2 days to complete with the back hardware we had at the time.  We didn't stop doing backups. We just scheduled it to run 3x a week, rather than daily.  It is sorta amazing that I have more storage sitting next to me today than our entire enterprise had in 2000.  At that time, we spent $5M to add storage for 1 project.  Last fall, I bought 8TB in a single WD-Black drive for $140.  Crazy. I shifted some older storage around so the new HDD would be primary, but there most definitely are daily, automatic, backups for the storage in that system, including the new 8TB storage which is currently using under 2TB after I migrated some files from other really-full volumes.

There is no replacement for backups.  I hope you don't have to learn that the hard way like so many other people do.

RAID performance doesn't usually scale in the way people hope.  Don't be surprised when it doesn't get faster than 2 disks allow even with more striping is used.

---

