---
title: "MDADM raid 1 array rebuild always crashes/freezes system"
date: 2008-07-29
forum: General Help
---

### Post by usingruby on 2008-07-29
Hi,

I got a problem with my raid1 array after a system crash. The array tries to rebuild itself and crashes/freezes the system at end of sync. I have started the PC three times always with the same result. So I cannot use the PC till this issue is resolved :(

MDADM is rebuilding and does this for ~5 hours (a 1 TB raid1 array). I have been sitting in front of the PC two times, once I checked "/proc/mdstat" and it was ~2 minutes to complete the rebuild, once it was less than a minute. Shortly after the system freezes (cannot toggle numlock, cannot switch to other console, only hard restart works). The problem is that mdadm tries to rebuild the disks again, after the hard restart. So I am in an endless loop :(

I am no linux/ubunutu wiz, so I don't know what logs or system outputs I should check or append.

Ubuntu: 64 bit version 8.04 fully updated at 2008/07/28
My system: AMD x2 4400+, with 2GB
2x1TB harddisk with raid1 and LVM

other stuff:
- Rebuild starts automatically
- Tried with login on gnome and with "init 3" state
- no additional work while rebuilding
- googled for a solution for a few hours, but all rebuild related problem are old (2007 and older)
- The array contains ~600GB of data, that I don't want to loose


Any help is highly appreciated, I am out of ideas.

Regards Klaas

---

### Post by alecm3 on 2008-08-03
One idea that might help you would be

look at /proc/mdstat, see which device it's trying to add:

when you look at a given raid container, you will see something like [UU_]. _ will stand for the failed device, that it's trying to add. Then manually fail this device (mdadm -f /dev/mdX /dev/sdX ), and then remove this device (mdadm -r /dev/mdX /dev/sdX ). That would presumably halt the rebuilding process.

After that, it should not try to rebuild when you reboot.

---

### Post by Midahed on 2008-08-03
I'm possibly no more experienced than you are, but I had a similar problem just a couple of days ago.  I had an old system based on a couple of 200 meg disks set as a raid 1 configuration.  I'd bought two 1TB drives and was rebuilding the system using Ubuntu 8.04.  I was at the point of occasionally running the new system and occasionally re-installing the old drives and booting up the old system.

After doing this a few times - and suffering a crash while I was using the old system - I found myself in the same state.  The re-build would get to 70.6% complete and then it would lock-up.  A hard re-boot caused the whole process to start again.  Fortunately this happened on my old, nearly redundant drives.

As I was so close to completing the re-build I just mounted one of the drives from the old array as read-only and continued my data migration onto the new drives.

You should be able to fail the array or physically disconnect one of the drives in your array and temporarily work off the other one.  With one drive working in the system you should be able to backup your data - preferably a couple of times using different backup devices.  You could even repeat the exercise using the other drive - that's what I'd do, but I'm paranoid when it comes to potential loss of data.  

Having done that, I'd thoroughly test the drives, re-partition them and start the rebuild from scratch.

But make sure you have plenty of reliable backups first.

---

### Post by usingruby on 2008-08-04
Thank you for your tips, I did not manage to do anything yet, because the Motherboard is gone --> maybe the hardware defect is my problem?! Hopefully all problems are going away after I receive my new hardware. I will report on it, when I finished to install the new PC add the end of the week.

Regards Klaas

---

### Post by usingruby on 2008-08-07
It does finally work. Bootting into recovery mode, using the root shell. No activity beside the mdadm resync. It works fine to the end (seeing 0.0 minutes remaining).

output on root console (typed from display):
[11162.195527] ata2.00: status: { DRDY ERR }
[11162.195585] ata2.00: error: { UNC }
[11163.272235] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[11163.272290] ata2.00: BMDMA stat 0x64
[11163.272346] ata2.00: cmd 25/00:08:05:55:70/00:00:74:00:00/e0 tag 0 dma 4096 in

this is repeated a lot of time (cannot scroll so don't know how often. Only the beginnging [xxxxxx.xxxxxx] changes. Other times or something.

Now cat /proc/mdstat shows that everything is fine. So maybe I had just needed to use the recovery mode with the root console...

---

### Post by Midahed on 2008-08-07
If that was my PC I'd be doing some more checks for a hardware problem.

That console message that mentions 'DRDY error' suggests a controller, drive or cabling problem to me.

Now that your drives are sync'd I'd have a look around the log files to see if there's anything suspicious reported there.

---

