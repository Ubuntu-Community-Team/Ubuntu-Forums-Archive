---
title: "Error writing on HDD"
date: 2013-09-30
forum: Hardware
---

### Post by LinuxUser666 on 2013-09-30
Hello fellow Linux users, I am running Ubuntu 12.04 32-bit with Xubuntu DE and recently got a hold of Maxtor 6Y080M0 SATA HDD and I formatted it to ext4 filesystem using Gparted tool. But since then I have a problem, I cannot write anything on it nor can I format it. When I try to mount it from Disks tool this is what it says: ```
Error mounting system-managed device /dev/sdb1: Command-line `mount "/mnt/088464b0-321b-4690-bde7-9850831f22d4"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


 (udisks-error-quark, 0)
``` 

I have no idea anymore why is it not working, so please give me some advice.
My regards, stay brutal.

---

### Post by slickymaster on 2013-09-30
> **LinuxUser666 said:**
> Hello fellow Linux users, I am running Ubuntu 12.04 32-bit with Xubuntu DE and recently got a hold of Maxtor 6Y080M0 SATA HDD and I formatted it to ext4 filesystem using Gparted tool. But since then I have a problem, I cannot write anything on it nor can I format it. When I try to mount it from Disks tool this is what it says: ```
Error mounting system-managed device /dev/sdb1: Command-line `mount "/mnt/088464b0-321b-4690-bde7-9850831f22d4"' exited with non-zero exit status 32: mount: wrong fs type, bad option, [COLOR=#ff0000]bad superblock on /dev/sdb1[/COLOR],       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


 (udisks-error-quark, 0)
``` 

I have no idea anymore why is it not working, so please give me some advice.
My regards, stay brutal.

Your error message indicates a filesystem failure, which can be caused by several reasons and it's causing it's refuse to mount. First you have to figure out what partition you're dealing with, by running```
sudo fdisk -l
```The above will list all the partitions on all the drives in your computer. Then make sure your superblock is the problem, by starting a filesystem check, replacing xxx with your partition name```
sudo fsck.ext4 -v /dev/xxx
```If your superblock is corrupt, the output will look something like this> The superblock could not be read or does not describe a correct ext4 filesystem.  If the device is valid and it really contains an ext4 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock: e2fsck -b 8193 &lt;device&gt;You'll have to find where your superblock backups are kept```
sudo mke2fs -n /dev/xxx
```Down at the bottom of the output, you should see a list of the backups, something like this```
[COLOR=#333333]Superblock backups stored on blocks:
[/COLOR][COLOR=#333333]32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632[/COLOR]
```Restore the superblock from the backup, again replacing xxx with your partition name, and block_number with the first backup superblock```
sudo e2fsck -b block_number /dev/xxx
```Reboot, and the superblock should be fixed. If it’s not, repeat the steps, but restore a different backup superblock.

---

### Post by LinuxUser666 on 2013-10-02
I will most certainly try that solution, but if superblock backups fail, is that it or is there any other solutions there? 
One more question, how to deal with bad sectors on my hdd, what tool is best to use or however it works? 

My regards, stay brutal. \\:D/

---

### Post by slickymaster on 2013-10-02
> **LinuxUser666 said:**
> I will most certainly try that solution, but if superblock backups fail, is that it or is there any other solutions there?
See these links:
[FilesystemTroubleshooting]("https://help.ubuntu.com/community/FilesystemTroubleshooting")
[Btrfs]("https://btrfs.wiki.kernel.org/index.php/Main_Page")
> **LinuxUser666 said:**
> One more question, how to deal with bad sectors on my hdd, what tool is best to use or however it works?
My regards, stay brutal. \\:D/
There is no way to repair bad sectors, they are automatically marked as unusable, without user intervention. To find out what various programs do that, see the man pages at a terminal window, of the following:```
man badblocks
``````
man fsck
``````
man smartctl
```

---

### Post by LinuxUser666 on 2013-10-03
Thanks Slickymaster, you are the best. 

My regards, stay brutal. :guitar:

---

### Post by slickymaster on 2013-10-03
Glad to be of help. Please don't forget to mark the thread as SOLVED so other people searching the forums know that this thread provides a working solution for their problem.

---

