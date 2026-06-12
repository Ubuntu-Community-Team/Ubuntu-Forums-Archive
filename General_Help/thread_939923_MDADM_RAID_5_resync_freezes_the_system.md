---
title: "MDADM RAID 5 resync freezes the system"
date: 2008-10-06
forum: General Help
---

### Post by emid on 2008-10-06
I came to my desktop yesterday morning and realized that it was frozen.  I restarted it, and after about 2 hours or so it locked up again.  After poking around I realized that my mdadm RAID 5 was resyncing, and that right as it was about to finish the system locks up.  I have no idea what to do, and I don't know what started this constant loop that I'm in.  If I restart, mdadm restarts the syncing process.  When it nears completion the systems locks up.

my proc/mdstat looks like this:
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sda1[0] sdc1[2] sdb1[1]
      976767872 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]
      [=====>...............]  resync = 27.3% (133356568/488383936) finish=76.9min speed=76929K/sec

```

and running "mdadm --detail /dev/md0" gives me this:
```

/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Jul 21 05:55:15 2007
     Raid Level : raid5
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Oct  6 13:17:55 2008
          State : active, resyncing
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 29% complete

           UUID : 1cde6ce9:d9d27fe7:84491a9a:bd46c765 (local to host d-desktop)
         Events : 0.151

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1


```

I would really appreciate any help I can get.  I can access the data in the array with no problems, I just want this constant resync/freeze to end.

---

### Post by fjgaude on 2008-10-06
The only think I can think of is a flakey drive in the array that **md** is not catching.

Suggestion: using a liveCD run **fsck** on the unmounted array.

---

### Post by emid on 2008-10-06
> **fjgaude said:**
> The only think I can think of is a flakey drive in the array that **md** is not catching.

Suggestion: using a liveCD run **fsck** on the unmounted array.

So you think one of the drives might be going bad?

If I were to boot up Knoppix for instance, would it see the array or would it only recognize the three individual drives?

---

### Post by fjgaude on 2008-10-06
Well, for the array to be assembled you have to have **md** in the kernel... try it and see, Knoppix is good stuff.

Yes, it could be a byte or two bad in a drive. fsck will find it if you can run it and if the array isn't too large. In your case I would think fsck will run just fine.

---

### Post by emid on 2008-10-06
Ok, I'm in Knoppix right now and I'm kinda lost on what to do next.  mdadm seems to be installed but I don't see a /dev/md0 device.

Could you nudge me in the correct direction? :)

---

### Post by emid on 2008-10-06
running "fdisk -l" while in Knoppix gives me the following:

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdd: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       14352   115282408+   7  HPFS/NTFS
/dev/sdd2           14353       19203    38965657+  83  Linux
/dev/sdd3           19204       19452     2000092+  82  Linux swap / Solaris

```

---

### Post by emid on 2008-10-06
OK, so I loaded the md driver with:
```
modprobe md
```

I then tried to assemble the array with:
```
mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1
```

and I got this in return:
```
mdadm: no recogniseable superblock on /dev/sda1
mdadm: /dev/sda1 has no superblock - assembly aborted

```

I'm not really sure what to do next.

---

### Post by fjgaude on 2008-10-06
You might try a scan:

```
mdadm --assemble -f --scan
```

like so to force the assemble.

Somehow the drives may have changed their names.

---

### Post by emid on 2008-10-06
> **fjgaude said:**
> You might try a scan:

```
mdadm --assemble -f --scan
```

like so to force the assemble.

Somehow the drives may have changed their names.

I should do this while I'm booted into Knoppix right?

---

### Post by fjgaude on 2008-10-06
I'd try it both ways, in Ubuntu and otherwise.

---

### Post by emid on 2008-10-06
The reason I ask is that I can currently access the array in Ubuntu, so I'm assuming that means it is already assembled.

I'm just trying to stop it from the resyncing/freezing that is going on.

Correct me if I'm wrong.

I still don't understand why it is freezing though.  If it was to fail during the resync that would be one thing, but why does it lock up the whole system?

---

### Post by fjgaude on 2008-10-06
Okay, what you are really wanting to do is to run **fsck** on the unmounted but assembled array, eh?

You can do that in Knoppix.

---

### Post by emid on 2008-10-06
Ok, so I rebooted into Knoppix and ran:
```
mdadm --assemble -f --scan
```

I got this in response:
```
mdadm: No arrays found in config file
```

then I ran:
```
dadm --assemble /dev/md0 /dev/sda1 /dev/sdb
1 /dev/sdc1
```
and I got:
```
mdadm: /dev/md0 has been started with 3 drives.
```

This surprised me so I decided to run "mdadm --detail /dev/md0" and got this:
```
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Jul 21 05:55:15 2007
     Raid Level : raid5
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
    Device Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Oct  6 21:20:18 2008
          State : clean, resyncing
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 28% complete

           UUID : 1cde6ce9:d9d27fe7:84491a9a:bd46c765
         Events : 0.159

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1

```

I ran this detail command again a few minutes later and realized that it is actively resyncing because the Rebuild status jumped from the 28% shown above, to 31%.  Does this probably mean it is going to freeze again?

I do notice that it says:
```
State : clean, resyncing
```

vs

```
State : active, resyncing
```
which is what it says in Ubuntu.

I don't know if that makes a difference or not.

P.S. I really do appreciate your help, I know this is getting kind of long. :)

---

### Post by emid on 2008-10-06
I just realized the "clean" vs. "active" is probably because the array isn't mounted in Knoppix.

Or not.....because I'm totally shooting in the dark.

---

### Post by emid on 2008-10-06
Should I run fsck while it is resyncing the array?  My inclination is to say no.

---

### Post by fjgaude on 2008-10-07
Please don't run **fsck** while it is resyncing...

Active means it is being used. Clean is no error is detected by **mdadm**.

Looks like you are may be on your way... after resyncing, run fsck and see what happens.

---

### Post by emid on 2008-10-07
It finished resyncing the array in Knoppix and everything seemed to be normal.  I rebooted back into Ubuntu, checked the array and saw that everything seemed to be back as it should.  The array said clean and wasn't trying to resync anymore.  I left the system on overnight and it was still up and running this morning (always a plus :)).  I'll run fsck on it a little later and see what I get.

Thanks for all your help, it's always reassuring to know someone out there can point you in the right direction.

---

### Post by fjgaude on 2008-10-07
Okay, very good... remember, do not run fsck on a mounted array, or drive.

Good luck!

---

### Post by newber on 2011-07-23
FIRST POST!!!

i have been using ubuntu for a few years now and have had to refer to this site numerous times but im finally in need of some more help so i decided to post.

i have an old computer which i moved my raid into as it was taking over my new desktop.
the old computer has a drive for the OS and 4-1.5TB WD green drives in mdadm raid 5. the os drive and one raid drive is connected to the sata on the mobo, two drives are connected to a sata pci card and the 4th drive is connected to another sata pci card. i just added the fourth drive a few months ago. it took a while to add it in but it worked fine. i believe the original two drives were the 'eads' version and the new two are the 'ears' version. if that matters.
ANYWAYS!!
it froze up the other day and after reboot, and reassemble, it starts right away into a resync. it doesnt get very far and then it freezes. have to hard reset. it was resyncing extremely slow, like 200k/s so i upped to min and max speed limits. didnt do anything at first but the next reset it started going faster. now it was only going to take 2 days instead of 2 months. it only gets to 1% or up to 5% before it completely freezes again.
i found this thread and it is the closest related problem i could find but i dont know what to do because it automatically starts to resync after i assemble..

please help :(

thanks alot

---

### Post by newber on 2011-07-24
bump...

i might have to move this thread to a better category

---

### Post by bakegoodz on 2011-07-24
Boot-To-The-Head to whoever suggested fsck for a Raid problem. fsck is for filesystem errors, a Raid is block device which is level below the filesystem. This what I would do: Run Drive manufacturer's diagnostic boot disk and do a full media scan on each drive. I believe on of the drives has bad sectors and the utility will tell if it can fix it (reallocate the bad sectors to good sectors) or to send the drive back.

---

### Post by newber on 2011-07-24
bump

---

### Post by newber on 2011-07-24
sorry for the bump didnt realize there was a reply

---

### Post by newber on 2011-07-24
k i am running self-tests (in disk utility) on each drive. the short ones were fine, now running the extended tests. will see if there are bad sectors. i found on the WD site 'lifeguard diagnostics', is this what you are referring to? it says to boot from a floppy. can i put it on a usb stick and boot it from there?
here is the link

[http://support.wdc.com/product/download.asp?groupid=608&sid=2&lang=en](http://support.wdc.com/product/download.asp?groupid=608&sid=2&lang=en)

thanks for your help

---

### Post by bakegoodz on 2011-07-25
It a CD Boot disk. Download the iso and burn it
[http://support.wdc.com/product/download.asp?groupid=613&sid=30&lang=en](http://support.wdc.com/product/download.asp?groupid=613&sid=30&lang=en)

---

### Post by newber on 2011-07-28
i was running the extended disk checks in the disk utility program in ubuntu. when the third drive was almost done checking i noticed the 4th drive wasnt showing up. after the third disk finished i rebooted and it was there again. ran the check on it and it was fine. started the raid again and it got to like maybe 70% resync so i was optimistic but it ended up freezing again. so since that drive had disappeared for a bit i thought it might be one of the cheap ebay pci sata cards. so i went to Tiger and bought a 4 port sata pci card, so i replaced both cards with this new single one. got home installed it and now it is resyncing again. it is going alot faster though. it should complete in about 10 hours from start to finish, vs before it was going to take a day and a half. so hopefully this finished by morning without freezing. if it does then i hope, problem solved. maybe my raid speeds will be increased now who knows. my understanding was that pci slots were around 150mb/s max and i had read rates of 135ish before so we will see if it has improved with new card.
(3 drives are now plugged into the one card and the 4th drive and os drive are direct to the mobo)

---

