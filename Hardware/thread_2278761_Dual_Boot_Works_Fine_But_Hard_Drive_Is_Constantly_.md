---
title: "Dual Boot Works Fine But Hard Drive Is Constantly Active"
date: 2015-05-18
forum: Hardware
---

### Post by SuperKev on 2015-05-18
Hi all,

I got a new Seagate 1 TB SSHD to replace the HD I had my Linux distro on due to bad sectors popping up, I decided to dual boot with the Win 7 install I have on an existing HD so I could use PS and all those things that only run on windows. Boot up is fine, GRUB looks right but when I boot up my HD activity light is pegged to the wall, and stays that way, even on Win 7, same thing. So obviously a hardware issue. I think what is happening is something to do with the fact that I created a 300 GB ntfs partition so I could share files across OS's easily on the master drive. I get this error when booting up:

"Disk drive for /mnt/data is not ready yet or is not present

Key: Continue to wait or press S to skip or press M for manual recovery"

fdisk -l gives this:

Device Boot Start End Blocks Id System
/dev/sdb1 * 2048 799999999 399998976 83 Linux
/dev/sdb2 800002046 1953523711 576760833 5 Extended
Partition 2 does not start on physical sector boundary.
/dev/sdb5 800002048 811999231 5998592 82 Linux swap / Solaris
/dev/sdb6 812001280 1311999999 249999360 83 Linux
/dev/sdb7 1312002048 1953523711 320760832 7 HPFS/NTFS/exFAT

Anyone know what I should do here to get the HD to settle down? Thanks in advance.

---

### Post by weatherman2 on 2015-05-18
Several questions here.

To fix the /mnt/data message, you'll need to find/fix/add a line in your /etc/fstab file that tries to mount a partition to /mnt/data .  Presumably the line is wrong (is this the NTFS partition?)  You have a reference to the data partition - a UUID (which may have changed) or a different partition reference.    You can use the command "sudo blkid" to find out current UUIDs of partitions, if you need to edit that in your /etc/fstab file.  You can use the command "sudo mount -a" without rebooting to check that everything in your /etc/fstab file mounts correctly.  If "sudo mount -a" returns without error, then /etc/fstab is correct; if you get an error then fix it.


As for the drive activity: not sure what to tell you there.  If it does exactly the same thing in Windows, then I guess I'd check with Seagate support or a Seagate forum - maybe there's a firmware update or something.  Don't even mention Linux, get it fixed in Windows first.

This is a caching hard drive, though: when new, the cache is empty and presumably must fill up so perhaps until then you'll see a lot of drive activity until the cache is full (which should speed up access).  Maybe this is normal behavior for this drive then until the cache is full

---

### Post by SuperKev on 2015-05-19
> **weatherman2 said:**
> Several questions here.

To fix the /mnt/data message, you'll need to find/fix/add a line in your /etc/fstab file that tries to mount a partition to /mnt/data .  Presumably the line is wrong (is this the NTFS partition?)  You have a reference to the data partition - a UUID (which may have changed) or a different partition reference.    You can use the command "sudo blkid" to find out current UUIDs of partitions, if you need to edit that in your /etc/fstab file.  You can use the command "sudo mount -a" without rebooting to check that everything in your /etc/fstab file mounts correctly.  If "sudo mount -a" returns without error, then /etc/fstab is correct; if you get an error then fix it.


As for the drive activity: not sure what to tell you there.  If it does exactly the same thing in Windows, then I guess I'd check with Seagate support or a Seagate forum - maybe there's a firmware update or something.  Don't even mention Linux, get it fixed in Windows first.

This is a caching hard drive, though: when new, the cache is empty and presumably must fill up so perhaps until then you'll see a lot of drive activity until the cache is full (which should speed up access).  Maybe this is normal behavior for this drive then until the cache is full

Thanks, when I created the partition it was in fat32 as Gparted did not give me an option for ntfs when doing the install. When I first booted in to Win 7 I formatted the partition to ntfs using the Windows utility and then went back in to Linux to modify the fstab as I knew the reformat would have changed the original UUID. But I will check to see what mount -a returns and let you know.

I considered the caching aspect myself but my HD light was solid with not even a pause for over 3 hours and I was afraid I might being doing damage to my drive. I will check that machine and post back, been using my laptop until I know for sure what is up with my main machine. 

Thanks for the reply

---

### Post by SuperKev on 2015-05-19
Result of 'sudo mount -a' 

mount: special device UUID=CF83-5F8E does not exist

Not sure what to do from here

---

### Post by weatherman2 on 2015-05-19
The UUID of your Windows partition changed when you re-formatted it to NTFS.  Use the command "sudo blkid" to find the new UUID, then edit the fstab file to replace the old UUID.

---

### Post by SuperKev on 2015-05-19
> **weatherman2 said:**
> The UUID of your Windows partition changed when you re-formatted it to NTFS.  Use the command "sudo blkid" to find the new UUID, then edit the fstab file to replace the old UUID.

I edited the fstab after I had done the format to ntfs


 $ sudo blkid
/dev/sda1: LABEL="System Reserved" UUID="9AB2D874B2D855FB" TYPE="ntfs" 
/dev/sda2: UUID="7A52DA9752DA5809" TYPE="ntfs" 
/dev/sdb1: UUID="36484841-7720-46a1-9c34-b1ba259b6002" TYPE="ext4" 
/dev/sdb5: UUID="24e39336-0da4-4535-8eb0-27eb6dd5610e" TYPE="swap" 
/dev/sdb6: UUID="1f4973e4-50e6-43b9-a5e9-eeccdbcc768b" TYPE="ext4" 
/dev/sdb7: LABEL="/mnt/data" UUID="F226E7CD26E790C1" TYPE="ntfs" 
/dev/sdc1: UUID="2E8B-EB5E" TYPE="vfat" 

fstab output

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=36484841-7720-46a1-9c34-b1ba259b6002 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=1f4973e4-50e6-43b9-a5e9-eeccdbcc768b /home           ext4    defaults        0       2
# /mnt/data was on /dev/sdb7 during installation
UUID=CF83-5F8E  /mnt/data       vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sdb5 during installation
UUID=24e39336-0da4-4535-8eb0-27eb6dd5610e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


# storage mount data
UUID=F226E7CD26E790C1 /media/storage/    ntfs-3g        auto,user,rw 0 0

IF I am reading that correctly, the UUID's match. Can you see something else I am not seeing? Thanks!

---

### Post by weatherman2 on 2015-05-19
It looks like you have created a new mount point at /media/storage for the NTFS partition.

You still have the line for the old partition that was CF83-5F8E, trying to mount to /mnt/data.  That's why you're getting the error.

Erase the line with CF83-5F8E in it.  Then, if you want to mount the NTFS partition at /media/storage, you're done.  If you want it at /mnt/data, change "/media/storage" to "/mnt/data" .

Use "sudo mount -a" when you're finished to test the edited fstab file.

---

### Post by oldfred on 2015-05-19
You still have this entry:

```
# /mnt/data was on /dev/sdb7 during installation
UUID=CF83-5F8E  /mnt/data       vfat    utf8,umask=007,gid=46 0       1
```

And now you are mounting that reformatted partition as /media/storage?

---

### Post by SuperKev on 2015-05-19
> **weatherman2 said:**
> It looks like you have created a new mount point at /media/storage for the NTFS partition.

You still have the line for the old partition that was CF83-5F8E, trying to mount to /mnt/data.  That's why you're getting the error.

Erase the line with CF83-5F8E in it.  Then, if you want to mount the NTFS partition at /media/storage, you're done.  If you want it at /mnt/data, change "/media/storage" to "/mnt/data" .

Use "sudo mount -a" when you're finished to test the edited fstab file.

Okay, I did all that and am no longer getting this error: "Disk drive for /mnt/data is not ready yet or is not present | Key: Continue to wait or press S to skip or press M for manual recovery"

sudo mount -a returns nothing, just a prompt

=================================================================


sudo blkid
/dev/sda1: LABEL="System Reserved" UUID="9AB2D874B2D855FB" TYPE="ntfs" 
/dev/sda2: UUID="7A52DA9752DA5809" TYPE="ntfs" 
/dev/sdb1: UUID="36484841-7720-46a1-9c34-b1ba259b6002" TYPE="ext4" 
/dev/sdb5: UUID="24e39336-0da4-4535-8eb0-27eb6dd5610e" TYPE="swap" 
/dev/sdb6: UUID="1f4973e4-50e6-43b9-a5e9-eeccdbcc768b" TYPE="ext4" 
/dev/sdb7: LABEL="/mnt/data" UUID="F226E7CD26E790C1" TYPE="ntfs" 

==============================================================

And fstab looks like this:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

# / was on /dev/sdb1 during installation
UUID=36484841-7720-46a1-9c34-b1ba259b6002 /               ext4    errors=remount-ro 0       1

# /home was on /dev/sdb6 during installation
UUID=1f4973e4-50e6-43b9-a5e9-eeccdbcc768b /home           ext4    defaults        0       2

# swap was on /dev/sdb5 during installation
UUID=24e39336-0da4-4535-8eb0-27eb6dd5610e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


# storage mount data
UUID=F226E7CD26E790C1 /mnt/data/    ntfs-3g        auto,user,rw 0 0

========================================================


Problem is that my HD activity light is still glowing solid and I don't know if I am harming my drive or not. Checked both 'sudo top' and 'iotop' and did not see anything that looked unusual and in fact with just the terminal open reads and writes were nominally zero across the board. CPU and other activity was equally low or normal looking. 

I booted in to Win 7 and used Seagate's software to analyze the disks and both passed several tests including SMART. Win 7 does see the data partition as well, lists it as D: drive. I should also say that there does not "seem" to be any performance issue, I would think with maxed out HD usage my system would be almost unusable, but I am on it right now. 

Any ideas why my activity light is glowing like Rudolph's nose? And am I harming my drive by using it? Thanks for all the help!!

---

### Post by weatherman2 on 2015-05-19
"mount -a" will return nothing if everything in fstab is correct, so you got that fixed.

As I said above, if you have the problem in Windows too, I'd check with Seagate support and/or with their forums.  There may be an updated firmware available for the drive, or this may be normal behavior for this drive while the cache is loaded during regular use.  I installed a similar drive in a Windows laptop once but don't recall any issue like you describe.  You're asking about a specific drive, not a generic Linux hardware issue, so your best bet is asking Seagate or their user forums for help.  Don't tell them you are using Linux unless you want to be told "We don't support Linux."

---

### Post by SuperKev on 2015-05-19
> **weatherman2 said:**
> "mount -a" will return nothing if everything in fstab is correct, so you got that fixed.

As I said above, if you have the problem in Windows too, I'd check with Seagate support and/or with their forums.  There may be an updated firmware available for the drive, or this may be normal behavior for this drive while the cache is loaded during regular use.  I installed a similar drive in a Windows laptop once but don't recall any issue like you describe.  You're asking about a specific drive, not a generic Linux hardware issue, so your best bet is asking Seagate or their user forums for help.  Don't tell them you are using Linux unless you want to be told "We don't support Linux."

Thanks, like I said, I don't seem to be experiencing any performance hit, so maybe it is like you say and the SSD part of this drive is doing some caching, granted my hardware is a few years old, before anything like a hybrid drive existed so maybe the MoBo SATA controller just does not know how to handle it? 

The issue is there in both OS's so definitely a hardware issue of some sort, just hoping I am not burning this drive to the ground by using it :) 

I have been using Ubuntu, and flavors since 6.10 so yeah, I have learned not to tell them I am using Linux. 

Thanks for all the help, I really appreciate it!!

---

