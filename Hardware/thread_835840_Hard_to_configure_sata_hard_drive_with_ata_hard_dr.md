---
title: "Hard to configure sata hard drive with ata hard drive"
date: 2008-06-20
forum: Hardware
---

### Post by sofasurfer on 2008-06-20
I was running fine with my sata HD. Now I have installed a ata HD along side it. I jumpered the ata HD as a single (Western Digital, no jumper). When I reboot now my system hangs up on the Ubuntu splash screen as soon as the progress bar appears.

Shouldn't I be able to just plug the ata drive in and have the system still work. Is there a special setup process?

Both hard drives are recognized in BIOS and on the POST screen at startup.

---

### Post by Rocket2DMn on 2008-06-21
I suggest the following:
Boot into the LiveCD and mount your filesystem.  You will need to check
```
sudo fdisk -l
sudo blkid
```
for the device information
Then add the new drive to /etc/fstab (which since it is on the filesystem will be at /path/to/mount/point/etc/fstab).  You may need to format it first using GParted from System->Administration->Partition Editor on the LiveCD.
Also make sure that your root partition still matches the entry in the fstab file on your real file system (NOT the one of the LiveCD).

---

### Post by sofasurfer on 2008-06-21
Thank you for that information. I will use it.
But the question still remains, shouldn't I be able to just plug my new ata HD in without it messing with my current sata HD which contains Ubuntu? As I said, Ubuntu now hangs up on the splash screen.
I don't think that should happen, do you? But it did, and there MUST be a logical reason.

---

### Post by Aearenda on 2008-06-21
I suspect you've encountered an increasingly common problem at the moment - adding a drive changes the order the drives are listed by the BIOS in mixed SATA/non-SATA systems. Your Ubuntu drive was probably drive 0 before you added the new drive, and now it is drive 1 (or more). Unfortunately, this affects the boot process.

The steps Rocket2DMn has suggested will help in figuring out what is happening. I would do the 'fdisk -l' step using the liveCD both with and without the new drive connected.

I would add a request for you to post the contents of /boot/grub/menu.lst and /boot/grub/device.map.

---

### Post by Odrodzona-Sarmacja on 2008-06-21
I didn't need even to install new hd. I just booted up with Partition Magic to check a fat32 drive for errors and I got all uuids changed on my harddrives. Now that caused me entire hour of rewriting from "uuid=..." to "/dev/sd.." in all my fstab and menu.lst. It was just crazy. I wonder why uuid is so important, when anything does change it making Ubuntu unbootable.

---

### Post by Aearenda on 2008-06-21
Actually, the UUID is supposed to help us get over moved drives, by finding the right partitions no matter where they are! Partition Magic should not have changed them - I would say this is a Partition Magic bug, if it happened automatically. The problem with booting is that there is no intelligence in the BIOS or in Grub able to identify UUIDs. It should work once the Linux kernel is loaded - but getting the kernel loaded, when the drive order has changed since Grub was installed, is problematic.

---

### Post by Odrodzona-Sarmacja on 2008-06-21
Actually I think except checking up on my fat32 hds for errors I also had a fat32 partition, which was formated with gparted, which didn't allow to label it, so I think I did correct this bug on this partition with Partition Magic...

---

