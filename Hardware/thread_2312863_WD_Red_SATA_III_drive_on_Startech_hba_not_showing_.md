---
title: "WD Red SATA III drive on Startech hba not showing after every reboot"
date: 2016-02-07
forum: Hardware
---

### Post by mike_johnson2 on 2016-02-07
I have a [pcie to sata iii 6g 4port [COLOR=#ff0000]Startech[/COLOR] adapter]("http://www.startech.com/Cards-Adapters/HDD-Controllers/SATA-Cards/4-Port-PCI-Express-SATA-6Gbps-RAID-Controller-Card~PEXSAT34RH") with a missing drive problem. Sounds similar to another thread, but that one was marked as solved with no answers. So I hope I'm not just re-asking the same exact issue as in a [separate thread.]("http://ubuntuforums.org/showthread.php?t=2293626&highlight=startech")

I get an error during startup stating "bay1" (which is a full drive ext4 partition on my "sdc" drive) is not available and can't be mounted - and asks retry or skip.

Retry doesn't work so I skip. After completely booting, using "lshw -C disk" the "sdc" is nowhere to be found.

The drive is in a hot swap bay...so I pull the drive out and push it back in. That causes it to appear, but causes "sdb" to disappear.

Doing the same thing to "sdb" causes it to reappear, but registered now as "sdd."

The way I get them both back on is to leave "sdc" pulled out while booting, then push it back in and do a "sudo mount -a" to remount it.

I verified in the startech adapter's bios that there are no raid configurations, so the drive is not being automatically paired in a raid configuration as part of "sdb" (which is plugged into the same card). Also I verified both drives appear in this bios correctly on rebooting.

So, everything I do know is; all the hardware _does_ see the drive, there is no hardware raid configuration to disguise this drive as part of another, the startech card and driver seem fine because "sdb" seems ok, and "sdc" does work and the operating system also sees it if I insert it after booting up. So it seems to me that everything is configured correctly??? Hmm

Can anybody pleeeease help?

[Asus N3150I-C]("http://www.asus.com/us/Motherboards/N3050IC/") / [8gb ram]("http://www.adata.com/en/xpg/feature/206") / [Startech PEXSAT34RH]("http://www.startech.com/Cards-Adapters/HDD-Controllers/SATA-Cards/4-Port-PCI-Express-SATA-6Gbps-RAID-Controller-Card~PEXSAT34RH") / [Ubuntu server 14.04.3]("http://www.ubuntu.com/download/server") / [Sandisk plus 120G ssd for OS]("http://www.sandisk.com/home/ssd/ssd-plus")/ [2x WD Red 4TB drives]("http://www.wdc.com/en/products/internal/nas/") / [350w PS]("http://www.solidgearusa.com/en/product_4/22/")

---

### Post by mike_johnson2 on 2016-02-12
Update - SOLUTION FOUND! 

Moving one sata cable ("sdb") off the Startech card to the spare sata port on the motherboard seemed a nice workaround for the problem with the first two storage drives "sdb" and "sdc."  This worked well.

BUT, the Startech has four ports, and my case is designed for FOUR storage drives and an operating system drive, all of which I intended to use.

Now, this Startech card has two separate physical blocks soldered to separate sides of the card, each block with two sata ports stacked together (four ports total). I was using the first block for "sdb" and "sdc" when I first encountered the problem.
Sooo, when I connected the other two drives to the Startech card, I put them both on the second block.
Like the first two drives, they both showed up fine. They remained live and consistent all the way through zeroing, partitioning, formatting, and a few reboots too. Each kept it's same drive designation the entire time.

Then I edited the /etc/fstab and added the auto mounting information. And well, "sde" became "sdd" and the original "sdd" disappeared.
This did not effect the other drive still on the card ("sdc"). I figure maybe the second block of ports must be on a separate bus than the first block.
However, I was now having the same exact issues with "sdd" and "sde" as I had with the other two, before relocating "sdb" to the motherboard. Swapping the two cables around didn't help either. One drive would always disappear from the system after reboot.
This problem would go away after deleting the fstab entries, and all drives would "list" again after reboot, with their original designations.

So, not having worked with so many drives in a case before, I edited my fstab entries like I had done before without problem.
I simply used /dev/"partition" to identify which drive I wanted to auto mount.
Thinking they would not change, I had used the drive designations the system so consistently assigned throughout partitioning and formatting.
But apparently, inclusion into the fstab file, causes these consistent designations to be a little more inconsistent.
By block of pairs on the card ("sdb" with "sdc", or "sdd" with "sde") the second drive was assigned the designation the first drive had, and the first drive, instead of being given another designation, no longer showed in the system at all (until pulled and pushed back in, causing other problems).

Now, frustrated with almost no hair left to pull out, I decided to try to follow the comments in the fstab file. (duh)

My fstab file was set up as;
/dev/sdb1 /media/bay1 ext4 defaults  0    2
/dev/sdc1 /media/bay2 ext4 defaults  0    2
/dev/sdd1 /media/bay3 ext4 defaults  0    2
/dev/sde1 /media/bay4 ext4 defaults  0    2

So, by simply using the "blkid" or "sudo blkid" method for the partition id
I reconfigured the file entries to;
UUID=376bd23c-f58e-41e0-ad16-461081c08adb       /media/bay1     ext4    defaults        0       2
UUID=f55fb7a4-63fa-49df-9aaa-99f1e68075a9       /media/bay2     ext4    defaults        0       2
UUID=0ea8654c-776f-4d34-a734-071ee39104dc       /media/bay3     ext4    defaults        0       2
UUID=e8af08cb-c8d8-4783-9ca5-f22e4bfc0a43       /media/bay4     ext4    defaults        0       2

And now reboot after reboot, everything keeps booting and mounting perfectly. Just need to grow back all of my pulled out hair now. (Where's the slapping my forehead emote?)

---

### Post by QIII on 2016-02-12
I'd offer you some of my hair, but what is left of it is grey and of little value.

Thanks for posting the resolution you found.  It will be helpful for the next solution seeker -- unlike the other thread.

---

