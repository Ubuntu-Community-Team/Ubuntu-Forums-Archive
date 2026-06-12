---
title: "After Unmount, Can't Boot With SATA Drive In Specific SATA Port?"
date: 2013-06-09
forum: Hardware
---

### Post by swormuth on 2013-06-09
Greetings all,

First, I'm loving Ubuntu.  I took the plunge.  No dual-booting and sticking my toe in the pool.  I erased all my computers and installed 13.04 on all of them.  All was going well, until...  :D

My main desktop PC had a single drive installed (Motherboard SATA Port-1), with the CD on SATA Port-0.  All was working great, and I installed and configured software, etc...  Today, I purchased a 3TB SATA disk for storage and installed it on SATA Port-2, which was found in GParted.  I tinkered around with MS-DOS limits, and finally decided to delete that and make a GPT Partition to do the whole disk in one Extended partition.  I noticed it was mounted under MYUSERNAME/Media, which didn't seem correct, since I want this accessible to all users, so I unmounted the disk.

Figuring I'd tinker more later, I shut down.  When I powered back up, the system hung just before GRUB would kick in, and went no further.  Lost, I pulled the disk data cable off the motherboard, and viola, booted.  Got a message to proceed because a drive couldn't be located (duh), but it booted.  Removed the reference to the drive in FSTAB, no more error.  Reboot, I'm back to a working system with the drive visible in GParted.  The only difference is the disk is now in SATA Port-2 instead of SATA Port-1 on the motherboard.

The issue is that if I reconnect the drive to SATA Port-1 on the motherboard, it won't boot again.  The disk has to remain in SATA Port-2 for Ubuntu to boot.  I'm afraid if I create a new partition now, I may create the issue again, and end up with no way to use the drive on my system, because I'll run out of SATA Ports on the motherboard.

Any ideas from the Guru's?

Thanks!

---

### Post by Bashing-om on 2013-06-09
[COLOR=#000000]swormuth;
I do not consider myselfg a "guru" ...but here is a suggestion.

Remove the present mountpoint in <user_name>/media - if such a thing exist on a new install //
Make a new mount point as /media/data;
Then verify the uuid of the drives partition(s);
```
sudo blkid
```
And edit the /etc/fstab file to reflect the new mount point and that the UUID was correct (changing the port may have changed the devices UUID).

You want the drive on the port that it will remain on when you run the "blkid" command !
[/COLOR][INDENT=2][COLOR=#000000]
just try'n to help

[/COLOR][/INDENT]

---

### Post by swormuth on 2013-06-09
> **Bashing-om said:**
> [COLOR=#000000]swormuth;
I do not consider myselfg a "guru" ...but here is a suggestion.

Remove the present mountpoint in <user_name>/media - if such a thing exist on a new install //
Make a new mount point as /media/data;
Then verify the uuid of the drives partition(s);
```
sudo blkid
```
And edit the /etc/fstab file to reflect the new mount point and that the UUID was correct (changing the port may have changed the devices UUID).

You want the drive on the port that it will remain on when you run the "blkid" command !
[/COLOR][INDENT=2][COLOR=#000000]
just try'n to help

[/COLOR][/INDENT]


If I run blkid, the only mount points that show are the ones for SDA1, and they are correct.  I've gotten rid of all the references to that incorrect mount point, and the system boots fine.  It only has an issue if I swap the SATA ports.  It's almost as if GRUB is pointing to the wrong place after I switch, because I can't boot from a CD at this point either.

---

### Post by VMC on 2013-06-09
I think you may have issue using to types of partitioning - GUID and MBR. Not sure thought, just a guess, since I no next to nothing regarding guid, but I keep reading of problems when their mixed.

---

### Post by Bashing-om on 2013-06-13
[COLOR=#000000]swormuth;
Swapping ports: It is my experience that bios maps the ports, and hands this mapping off to the operating system once.
When changing the devices to another port, bios may be aware of it and re-do it's mapping... but the operating system may not pick up this change. My memory is hazy on this point... last time I ran into it... to the best I recall I ran the command
```
device.map
``` for the operating system to pick up the alteration in the ports.
If you respond to this thread and continue to have problems, I will be willing to hunt up the docs and howto.
[/COLOR][INDENT=3][COLOR=#000000]
try'n to help

[/COLOR][/INDENT]

---

### Post by swormuth on 2013-06-15
Thanks all...

I decided to just leave the drive in the new port for now.  What I will try when the day comes to add another disk, is to put the new disk in the original location and see what happens.  What I have noticed is the SATA ID's get swapped by my BIOS when I change the drive location, and Ubuntu is looking for GRUB on the new data disk, rather than the original OS disk.  My thinking is that once I add a third drive, my BIOS will be unable to swap the existing AHCI ID's (like it does now), and will have to assign a new one for the new disk.  This should leave the AHCI ID for the current boot drive alone, and hopefully fix the issue.

Not much else to try here, since I think the issue is my BIOS swapping the AHCI ID for the drive, and not Ubuntu.  Perhaps there is a way to have Ubuntu update it's mapping (device.map?), but I can't even boot with the drive attached to explore that.  :D

Thanks guys...  I'll update this when the day comes to install another drive.

---

### Post by Bashing-om on 2013-06-15
[COLOR=#000000]swormuth;

Yeah, seems you are on the right track...look at:
```
sudo grub-mkdevicemap
``` for grub to regenerate the device map.
[/COLOR][INDENT=2][COLOR=#000000]
hope that helps

[/COLOR][/INDENT]

---

