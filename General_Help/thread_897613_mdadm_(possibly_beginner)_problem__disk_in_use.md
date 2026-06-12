---
title: "mdadm (possibly beginner) problem : disk in use"
date: 2008-08-22
forum: General Help
---

### Post by boomerzz on 2008-08-22
I'm doing a first time RAID configuration (striped) on my server that is already running Ubuntu 8.04.

I've read so many man pages and examples of how to do it, but I'm still stuck on creating the md0 "array", with both drives.

The two drives are the same model, 160g caviars, and they have the exact same partition setup.  1 large partition and a swap partion.  

If I use the create command to create md0 with /dev/sda1 /dev/sdb1 , it tells me that sda1 is in use.  (I can't remember if that is the exact error, it essential tells me that the drive is busy, so it can't add it to md0)

I can create it with just "/dev/sdb1 missing".  I tried manually editing the /etc/mdadm/mdadm.conf file and adding it in and rebooting, but it doesn't use it as such.


Do I need to copy the data over and boot off of the other drive?  Then add it?  I'm a bit confused because none of the walkthroughs I saw ran into this or did something like that.

I'd love for it to handle the resync / copy, and not me do it manually.

I just downloaded the alternate CD, and I'm going to give that a try when I get home from work, unless there is some other option.

---

### Post by livestockPimp on 2008-08-22
you cannot make a raid array with a mounted volume since the volume needs to be formatted once it is made.

The way you setup software raid on a currently installed system is as follows. (This is how I do it for raid-1 but the concept should be the same!)

1) ensure that under fdisk the partition type is not ext3 but RAID auto-detect (type 82 from memory)

2) create an array with a missing drive (as you have already done by the looks)

3) format the new raid array and mount it.

4) copy all the data across from your drive to the raid array:
    cp -aRx / /mnt/mounted-raid-volume

5) make md0 bootable and install a bootloader on it, ie grub.

6) modify your menu.1st and change your system to boot from the md0 device

7) add the drive that is is missing in the array since it is no longer been used to complete the array.

8) sit back and watch them sync!

NOTE: do not put your swap in a raid array.

---

### Post by boomerzz on 2008-08-22
Thanks so much.

So I've got to copy the data over to sdb1, make it boot from md0.

Do I need to reboot after?  Then add /dev/sda1 and watch them sync?

Thanks for the swap note, I hadn't planned on it, but it had crossed my mind.  (now I wont do it)

EDIT: sdB1

---

### Post by livestockPimp on 2008-08-23
yes, you need to reboot before you can add the other drive, this is because you need to be using a drive that is not mounted.

when you have rebooted you can use "df" to ensure your root is not using your non-raid drive.

---

