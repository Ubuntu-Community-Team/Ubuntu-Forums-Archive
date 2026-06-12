---
title: "I think i transferred ubuntu to its own partition..."
date: 2008-09-21
forum: General Help
---

### Post by AdamMPkins on 2008-09-21
but how can i tell? in the LVPM i allocated 10Gib for the new root partition, now there is a disk called extra and that's where most of my ubuntu files are stored. How can I be sure that i did it right? I initially installed ubuntu through WUBI and was attempting to transfer it to its own partition.

---

### Post by AdamMPkins on 2008-09-21
any help?

---

### Post by AdamMPkins on 2008-09-21
anything?

---

### Post by ago on 2008-09-22
Once you have booted type in a terminal 

cat /proc/mounts

Check whether root (/) is mounted on top of a real partition (/dev/*)

---

### Post by AdamMPkins on 2008-09-22
This is a screenshot of the results of that command. Where do i stand and how should i continue in my attempts to move ubuntu to its own partition?

---

### Post by Bucky Ball on 2008-09-22
If you installed in wubi, then your ubuntu files would have been somwhere in C:\ubuntu on the Windoze partition. Wubi creates a virtual drive within windoze so you haven't wiped anything there. Maybe copy and paste the results of this command:

**sudo blkid**

straight from your terminal into a post. And also:

**sudo fdisk -l**

Brief explanation of exactly what you're trying to move from where to where? :)

ps: [quote=ago]Check whether root (/) is mounted on top of a real partition (/dev/*)[/quote]

Sounds right. cat /proc/mounts ... nice, ta. So, maybe copy the results of that command again and paste from the terminal into a post making sure to get the whole file.

---

### Post by ago on 2008-09-22
You are still booting off a wubi loopfile installation (see the /host entry?). 

That does not necessarily mean that the LVPM installation failed, it might be simply that grub is not in the MBR of the correct disk, so you are using the old boot options. LVPM does not delete the old installation but it should replace the default bootloader (grub instead of ntldr+grub4dos). This last step might fail, particularly if you have more than 1 hard disk.

You can check whether you have an ext3 file system in the partition you migrated things to in LVPM, by mounting that partition and quickly comparing the content with /. It should be almost identical.

In that case you can try to boot manually into the new partition, at boot press ESC after selecting "Ubuntu", then press "C" to get the grub console. There type:

configfile (hdX,Y)/boot/grub/menu.lst

Replacing X, Y with the disk and partition number (minus 1) where you migrated wubi. If you can boot like that then it means that LVPM mostly succeed and you need to install grub into the MBR of the correct hard disk using the grub command (see online guides for that).

---

### Post by AdamMPkins on 2008-09-22
> **Bucky Ball said:**
> If you installed in wubi, then your ubuntu files would have been somwhere in C:\ubuntu on the Windoze partition. Wubi creates a virtual drive within windoze so you haven't wiped anything there. Maybe copy and paste the results of this command:

**sudo blkid**

straight from your terminal into a post. And also:

**sudo fdisk -l**

Brief explanation of exactly what you're trying to move from where to where? :)

ps: 

Sounds right. cat /proc/mounts ... nice, ta. So, maybe copy the results of that command again and paste from the terminal into a post making sure to get the whole file.

cat /proc/mounts:
> 
adammpkins@adammpkins-laptop:~$ cat /proc/mounts
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw,relatime 0 0
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0
/dev/sda1 /host fuseblk rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other 0 0
/dev/loop0 / ext3 rw,relatime,errors=remount-ro,data=ordered 0 0
/dev/loop0 /dev/.static/dev ext3 rw,relatime,errors=remount-ro,data=ordered 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.24-19-generic/volatile tmpfs rw,relatime 0 0
tmpfs /dev/shm tmpfs rw,relatime 0 0
devpts /dev/pts devpts rw,relatime 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
/dev/sda1 /boot fuseblk rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other 0 0
/dev/sda1 /media/Windows\040Partition fuseblk rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other 0 0
securityfs /sys/kernel/security securityfs rw,relatime 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec 0 0
gvfs-fuse-daemon /home/adammpkins/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0
adammpkins@adammpkins-laptop:~$



sudo blkid: 

adammpkins@adammpkins-laptop:~$ sudo blkid
[sudo] password for adammpkins: 
/dev/sda1: UUID="28C643A2C6436EDE" TYPE="ntfs" 
/dev/loop0: UUID="35c6cf30-cf77-4a8a-8fb1-960409f9f6a0" TYPE="ext3" 
adammpkins@adammpkins-laptop:~$ 
[/quote]  

sudo fdisk -l
> 
adammpkins@adammpkins-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc64f5848

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19458   156288000    7  HPFS/NTFS
adammpkins@adammpkins-laptop:~$ 

I guess what this means is that i still have to create a new partition for ubuntu. Am i right by assuming this? I'm new to ubuntu and not very good at partitioning so i apologize for my lack of terminal knowledge etc...

---

### Post by ago on 2008-09-22
Well it does not look like you have a dedicated partition at all. You have to create that BEFORE running LVPM.

---

### Post by AdamMPkins on 2008-09-22
> **ago said:**
> Well it does not look like you have a dedicated partition at all. You have to create that BEFORE running LVPM.
Where can i find a tutorial on partitioning in linux. I have all the partitioning applications already I just misunderstood.

---

### Post by AdamMPkins on 2008-09-22
> **AdamMPkins said:**
> Where can i find a tutorial on partitioning in linux. I have all the partitioning applications already I just misunderstood.

Also, when i boot into gparted i get the message:
> root (hd1,) 
Error 21: Selected disk does not exist
How do i make a dedicated partition for ubuntu/ how do i fix this TO make the partition?

---

### Post by ago on 2008-09-22
Boot from a live CD and run gparted from there.

---

### Post by AdamMPkins on 2008-09-26
> **ago said:**
> Boot from a live CD and run gparted from there.

I ran gparted on a live cd and it worked successfully. I then tried to boot to the windows partition and ran chkdsk. After rebooting, I attempted to boot to ubuntu so i could run the LVPM but instead recieved this error:
file:\ubuntu\winboot\wubildr.mbr
Status: 0x000000e
Selected entry could not be located because the application is missing or corrupt

What have i done wrong? Can I rectify this without uninstalling my wubi partition and reinstalling?

---

### Post by AdamMPkins on 2008-09-26
any advice on this?

---

### Post by Bucky Ball on 2008-09-27
file:\ubuntu\winboot\wubildr.mbr

Seems to be looking for the mbr of your wubi install (which would/would have been in windoze).

---

### Post by AdamMPkins on 2008-09-27
and how could i rectify this problem?

---

### Post by ago on 2008-09-29
look if the file is there to begin with, also check that you have the /ubuntu/disks/root.disk.

---

### Post by AdamMPkins on 2008-09-30
> **ago said:**
> look if the file is there to begin with, also check that you have the /ubuntu/disks/root.disk.

both of those are present

---

### Post by AdamMPkins on 2008-10-03
> **AdamMPkins said:**
> both of those are present

anything?

---

### Post by AdamMPkins on 2008-10-08
> **AdamMPkins said:**
> anything?

bumping this back up to get an answer.

---

### Post by ago on 2008-10-09
There was another thread a few days ago' with instructions about using the newer grub4dos, it should help

---

