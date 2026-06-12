---
title: "Virtual Disk on RAID5 not recognized by Ubuntu Server"
date: 2024-01-22
forum: Hardware
---

### Post by cptkrabbe77 on 2024-01-22
Hi all!

I'm really new to linux in general, i hope i found the right place for this question:
 
I have this old PC which I wanted to use when I sometimes have to rsync a lot of data from some other machines. My idea was to put some old 8TB HDDs and one smaller M.2-disk into it and create a raid5 on the HDDs. I created the RAID5 within the BIOS of the mainboard: ASrock H51DM. It shows me the virtual Disk with ~21TB on all 4 HDDs just fine.
Now when I installed Ubuntu Server 22.04.3 LTS the virtual disks wasn’t listed, the Installer instead would present me all 5 individual disks (4xHDD+1xM.2).

So I continued installing the OS on the M.2.

Is there a way to see the virtual disk and mount/use it? I can see that the individual HDDs are kind of recognized as member of the RAID:

```
root@tkrpm0x:~# lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT
NAME                        SIZE FSTYPE          TYPE  MOUNTPOINT
loop0                      63,4M squashfs        loop  /snap/core20/1974
loop1                     111,9M squashfs        loop  /snap/lxd/24322
loop2                      53,3M squashfs        loop  /snap/snapd/19457
loop3                      40,4M                 loop  /snap/snapd/20671
loop4                      63,9M                 loop  /snap/core20/2105
sda                         7,3T **ddf_raid_member disk**
&#9500;&#9472;md126                       0B                 raid6
&#9492;&#9472;md127                       0B                 md
sdb                         7,3T **ddf_raid_member disk**
&#9500;&#9472;md126                       0B                 raid6
&#9492;&#9472;md127                       0B                 md
sdc                         7,3T **ddf_raid_member disk**
&#9500;&#9472;md126                       0B                 raid6
&#9492;&#9472;md127                       0B                 md
sdd                         7,3T **ddf_raid_member disk**
&#9500;&#9472;md126                       0B                 raid6
&#9492;&#9472;md127                       0B                 md
nvme0n1                   953,9G                 disk
&#9500;&#9472;nvme0n1p1                   1G vfat            part  /boot/efi
&#9500;&#9472;nvme0n1p2                   2G ext4            part  /boot
&#9492;&#9472;nvme0n1p3               950,8G LVM2_member     part
  &#9500;&#9472;ubuntu--vg-ubuntu--lv   100G ext4            lvm   /
  &#9492;&#9472;ubuntu--vg-lv--0      850,8G ext4            lvm   /home

```
But I have no idea how to mount them or mount the virtual disk i created in BIOS… anyone willing to help me? Or am I going in the wrong direction? Maybe I can just use all 4 HDDs with linux tools to create a software RAID5 (since I don’t think the cheap mainboard has a “real” raid controller anyways…)?
Any help would be highly appreciated.

---

### Post by TheFu on 2024-01-23
Did you create the RAID in the BIOS?  If so, that's a mistake - look up "fake raid" and all the reasons you don't want to use it.  Friends don't let friends use Fake-RAID.  Just don't.

What you want is software-raid, created post-install.

It is a bad idea to mix disks of different speeds into a RAID device.  The slowest one will be the performance you get.

BTW, you have created two RAID6 arrays according to that lsblk output .... the device names are /dev/md126 and /dev/md127. Those would be the devices that you add either LVM onto and create PVs, VGs, and LVs, then format the LVs with a file system.  While you can leave LVM out, that usually isn't done, since having huge file systems is a liability.  You are probably too new to know that.  

And lastly, backups are 100x more important than RAID.  Backups can solve 1001 problems, whereas RAID solves just 2.  Backups are sometimes needed to fix a broken RAID, so be 100% certain you have a backup plan **before** you bother with RAID at all.

Now that you know the devices, you can use that to mount the storage, if you like.  But really, you should remove all the Fake-RAID stuff from those devices, ensure all the RAID flags are removed and start over using **mdadm** to create, assemble, and maintain your SW-RAID. [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) explains the configuration of the fstab file, which is where you'd configure mounts.

---

### Post by cptkrabbe77 on 2024-01-23
Thank you very much, this is pretty much what i allready assumed. I will delete all settings i made in BIOS and start over, then i will try to set up a software raid in linux.
I will not use this machine for backups, i just sometime need to transfer big files (4-16 TB file size) between offifces and my idea was to set up this "old" computer with a big raid disk and a 10GBit card so i can speed up this task - at this moment i use a 24 TB Synology NAS which has only a 1GBit link (transfer over WAN/VPN is out of the questions, we get 40MBit upload max).

---

### Post by TheFu on 2024-01-23
Old RAID5 disks can be slow. You won't see 4x the throughput. Back when I ran RAID5, I was seeing about 40Mbps writes and reads. Nothing great for individual disks that could do 125 Mbps alone.  That array was using an infiniband connection, BTW.

---

