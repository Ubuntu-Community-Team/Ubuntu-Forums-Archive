---
title: "Shared partition between XP and Ubuntu does not work"
date: 2010-05-19
forum: Hardware
---

### Post by deeptiman.panda on 2010-05-19
Hello Everyone

I have a curious but acute problem. Hope someone can help me at the earliest. Here it goes

I have a laptop, which has XP installed in it. It has a partition for data. I want to share this partition between XP and my live Ubuntu CD. 

Option 1: Access the NTFS data drive from Ubuntu. When I open the GPARTED, it shows the particular file system as "unknown". So I cannot mount it. Now I can format it to NTFS and load it. This works fine in Ubuntu.

But the moment I go to Windows and tries to access this partition. It asks me to format it (even though it was created as a NTFS partition in Ubuntu).

Option 2: Access the Ubuntu file system (If I format the data drive as EXT2), from windows. I tried many applications in windows like EXT2IFS etc, but none would allow me to open the Ext2 file. No matter what I do, the moment, I click on that drive in windows, it says, I need to format it.

Is there any third way, to share data across the operating systems?

Please let me know, if you need any further informations.

thanks in advance for all your help

BR
Deeptiman

---

### Post by Hobgoblin on 2010-05-20
There's something odd going on there.

Assuming /dev/sda1 is your XP C: drive it should be showing up as NTFS as well (not unknown anyway).

What make/model laptop is it?

---

### Post by deeptiman.panda on 2010-05-20
Mine is Dell latitude . The one most commonly given in all the offices. If you need any specifics, please let me know and I can get it for you.

---

### Post by srs5694 on 2010-05-20
Try posting the output of the text-mode "sudo fdisk -lu" command. Please post it between "[noparse]```
[/noparse]" and "[noparse]
```[/noparse]" strings for legibility.

---

### Post by deeptiman.panda on 2010-05-20
Here is the output of the command you requested for . Hope this helps...

> 
custom@custom:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2bc92bc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81915434    40957686    7  HPFS/NTFS
/dev/sda2        81915435   234436544    76260555    7  HPFS/NTFS


---

### Post by srs5694 on 2010-05-20
The partition type codes are correct, which is what I thought might have been wrong. What do "blkid /dev/sda1" and "blkid /dev/sda2" produce? Those commands should identify the filesystem(s) in use on the partitions.

---

### Post by deeptiman.panda on 2010-05-20
here is the output of the commands you asked for

> 
custom@custom:~$ blkid /dev/sda1
custom@custom:~$ blkid /dev/sda2
/dev/sda2: UUID="2fb08765-6dc3-4bde-83df-ce748948bb28" TYPE="ext4" 
custom@custom:~$ 
Even though both the partitions are NTFS, sda2 shows as ext4 in this output.

Hope this helps.

---

### Post by srs5694 on 2010-05-21
Well, blkid isn't identifying /dev/sda1 as anything. What happens when you mount /dev/sda2? For instance, "sudo mount /dev/sda2 /mnt"? Can you see files in /mnt ("ls /mnt")? If it mounts successfully, what filesystem does it show as in /etc/mtab ("grep sda2 /etc/mtab")? It could be that it really is ext4, despite what you think; or it could be that there are overlapping ext4 and NTFS data structures that are confusing the system; or it could be that something stranger is going on.

For "something stranger," my vague notion is that there may be some sort of RAID or other low-level drive configuration that Windows and Linux are reading differently. Many BIOSes include such options, and if something is activated that Windows understands but that Linux doesn't (or that Linux ignores), they could be reading the drive very differently, which could result in weird problems such as you report. If so, your best bet may be to change whatever BIOS option is causing problems and start from scratch, re-installing Windows and the shared-data partition.

---

### Post by deeptiman.panda on 2010-05-21
Hi

Thanks for your efforts in helping me. I did as per your request and following is the output. It did not work with the command exactly as you posted. So I modified it a little bit to include the NTFS option. Please let me know, if it is not right. It confirms to what I have originally observed in GPARTED. 


> 
custom@custom:/usr/share/man$ sudo mount -t ntfs /dev/sda2 /mnt
NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

For me, formatting the whole system and starting from scratch is not an option. I can only play around with the data drive. Even if I change the sda2 drive to NTFS, when I go back to Windows, it says, it has to be formatted. and once I format in windows, it again does not get recognized in Ubuntu.

Appreciate any further help on this.

---

### Post by srs5694 on 2010-05-21
I take it from your last post that the mount command without the "-t ntfs" also didn't work. You could try it with "-t ext4", but it's looking more and more like you've got some weirdness going on related to BIOS settings -- perhaps a RAID option is active or some other option that's causing Windows and Linux to look at the drive in different ways. You could have a look at your BIOS to try to locate any such options, but beyond that I'm really at a loss.

---

### Post by deeptiman.panda on 2010-05-22
Thanks for all your help. Seems like I am stuck!!

---

