---
title: "Error mounting SSD"
date: 2024-07-05
forum: Hardware
---

### Post by oygle on 2024-07-05
There are 2 SSD's with this laptop, one internal I use to boot to Windows, the other has Kubuntu on it. I can usually use Dolphin to navigate the internal/Windows drive , but now it is giving an error

> An error occurred while accessing '237.9 GiB Internal Drive (nvme0n1p3)', the system responded: The requested operation has failed: Error mounting /dev/nvme0n1p3 at /media/*****/******
: wrong fs type, bad option, bad superblock on /dev/nvme0n1p3, missing codepage or helper program, or other error

The mount command shows it as

> /dev/nvme0n1p1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)

I can do a ls from the terminal

```
$ ls -al /dev/nvme0n1p1
```

> brw-rw---- 1 root disk 259, 1 Jul  5 10:55 /dev/nvme0n1p1

and also ..

$ ls -al /dev/nvme0n1p3
brw-rw---- 1 root disk 259, 3 Jul  5 10:55 /dev/nvme0n1p3

I can display both the SSD's in KDE Partion Manager. This journal entry is concerning ..

> Jul 05 11:25:23 ThinkPad-T470s smartd[655]: Device: /dev/nvme0, number of Error Log entries increased from 4799 to 4814

---

### Post by vanadium on 2024-07-05
Show information about /dev/nvme0n1p3 by providing the output of the following command:
```

{ sudo blkid && mount && cat /etc/fstab ; } | grep nvme0n1p3

```

---

### Post by oygle on 2024-07-05
Thanks @vanadium

```
$ { sudo blkid && mount && cat /etc/fstab ; } | grep nvme0n1p3
```

> /dev/nvme0n1p3: BLOCK_SIZE="512" UUID="DABA0B69BA0B418D" TYPE="ntfs" PARTUUID="21600ef4-2f6d-4bf9-b98a-6eecd29f09ef"

---

### Post by yancek on 2024-07-05
In your initial post, you indicate you are having problems with partition 3 on the device then post information from the mount and ls commands on "partition 1", the EFI partition.  Is partition 3 the actual problem partition and is it a data partition?  There would be no reason to access the windows system partition from Linux, at least no reason to write to it so hopefully you have not done that.  Since you have some version of windows installed, boot into windows and run chkdsk to see if it can repair the problem.  It might be that it is just hibernated but probably not as you would have seen a different error.

---

### Post by oygle on 2024-07-06
> **yancek said:**
> In your initial post, you indicate you are having problems with partition 3 on the device then post information from the mount and ls commands on "partition 1", the EFI partition.  Is partition 3 the actual problem partition and is it a data partition?  

The entry is Dolphin file Manager was setup automatically, for some reason it addressed partition 3, and gave an error message on partitiion 3.

> **yancek said:**
> There would be no reason to access the windows system partition from Linux, at least no reason to write to it so hopefully you have not done that. 

I have been accessing the windows system files via the network when it was on another computer. Now it is on the same computer, the need is still there, and I have had no errors or problems to date, ..until now.

> **yancek said:**
>  Since you have some version of windows installed, boot into windows and run chkdsk to see if it can repair the problem.  It might be that it is just hibernated but probably not as you would have seen a different error.

Yes it seems so ..

```
sudo ls -al /boot/efi
```

> total 462
drwx------ 4 root root  1024 Jan  1  1970  .
drwxr-xr-x 4 root root  4096 Jun 27 12:16  ..
drwx------ 5 root root  1024 Apr 27 13:06  EFI
-rwx------ 1 root root 80896 Jan  1  1980  FSCK0000.REC
-rwx------ 1 root root 80896 Jan  1  1980  FSCK0001.REC
-rwx------ 1 root root 46080 Jan  1  1980  FSCK0002.REC
-rwx------ 1 root root 78848 Jan  1  1980  FSCK0003.REC
-rwx------ 1 root root 79872 Jan  1  1980  FSCK0004.REC
-rwx------ 1 root root 46080 Jan  1  1980  FSCK0005.REC
-rwx------ 1 root root 20480 Jan  1  1980  FSCK0006.REC
-rwx------ 1 root root 32768 Jan  1  1980  FSCK0007.REC
drwx------ 2 root root  1024 Jul 28  2022 'System Volume Information'


So I logged into the Windows SSD, ran **chkdsk** as admin, it found errors, supposedly fixed them. However the partitiion still cannot be displayed from Kubuntu. Everytime I do an autoremove it references /boot/efi and partition 1, not partition 3. Here is a log from about 6 weeks ago.

> 
sudo apt autoremove
[sudo] password for ********:
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-6.5.0-9 linux-headers-6.5.0-9-generic linux-image-6.5.0-9-generic linux-modules-6.5.0-9-generic linux-modules-extra-6.5.0-9-generic
0 to upgrade, 0 to newly install, 5 to remove and 0 not to upgrade.
After this operation, 273 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 261754 files and directories currently installed.)
Removing linux-headers-6.5.0-9-generic (6.5.0-9.9) ...
Removing linux-headers-6.5.0-9 (6.5.0-9.9) ...
Removing linux-image-6.5.0-9-generic (6.5.0-9.9) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-6.5.0-9-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.5.0-35-generic
Found initrd image: /boot/initrd.img-6.5.0-35-generic
Found linux image: /boot/vmlinuz-6.5.0-28-generic
Found initrd image: /boot/initrd.img-6.5.0-28-generic
Found memtest86+ 64bit EFI image: /boot/memtest86+x64.efi
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
done
Removing linux-modules-extra-6.5.0-9-generic (6.5.0-9.9) ...
Removing linux-modules-6.5.0-9-generic (6.5.0-9.9) ...

This is how KDE Partition Manager views the Windows SSD

---

### Post by oygle on 2024-07-06
Some more info ..

```
lsblk
```

> 
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0         7:0    0  74.2M  1 loop /snap/core22/1380
loop1         7:1    0  73.9M  1 loop /snap/core22/864
loop2         7:2    0 268.6M  1 loop /snap/firefox/4451
loop3         7:3    0     4K  1 loop /snap/bare/5
loop4         7:4    0 268.7M  1 loop /snap/firefox/4483
loop5         7:5    0   497M  1 loop /snap/gnome-42-2204/141
loop6         7:6    0 505.1M  1 loop /snap/gnome-42-2204/176
loop7         7:7    0  91.7M  1 loop /snap/gtk-common-themes/1535
loop8         7:8    0  38.7M  1 loop /snap/snapd/21465
loop9         7:9    0  38.8M  1 loop /snap/snapd/21759
loop10        7:10   0 127.8M  1 loop /snap/yt-dlp/578
sda           8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1        8:1    0   480M  0 part 
&#9492;&#9472;sda2        8:2    0   931G  0 part /var/snap/firefox/common/host-hunspell
                                      /
sdb           8:16   1     0B  0 disk 
nvme0n1     259:0    0 238.5G  0 disk 
&#9500;&#9472;nvme0n1p1 259:1    0   100M  0 part /boot/efi
&#9500;&#9472;nvme0n1p2 259:2    0    16M  0 part 
&#9500;&#9472;nvme0n1p3 259:3    0 237.9G  0 part 
&#9492;&#9472;nvme0n1p4 259:4    0   509M  0 part 


Some related reading at [https://askubuntu.com/questions/1502112/how-to-access-windows-files-from-ubuntu-23-10-which-is-installed-alongside-windo](https://askubuntu.com/questions/1502112/how-to-access-windows-files-from-ubuntu-23-10-which-is-installed-alongside-windo) , [https://askubuntu.com/questions/113733/how-to-mount-a-ntfs-partition-in-etc-fstab](https://askubuntu.com/questions/113733/how-to-mount-a-ntfs-partition-in-etc-fstab) ,  [https://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](https://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

```
journalctl -b | grep nvme
```

> 
Jul 06 13:56:34 ThinkPad-T470s kernel: nvme nvme0: pci function 0000:3c:00.0
Jul 06 13:56:34 ThinkPad-T470s kernel: nvme nvme0: 4/0/0 default/read/poll queues
Jul 06 13:56:34 ThinkPad-T470s kernel:  nvme0n1: p1 p2 p3 p4
Jul 06 13:56:34 ThinkPad-T470s (udev-worker)[338]: nvme0n1: Process '/usr/bin/unshare -m /usr/bin/snap auto-import --mount=/dev/nvme0n1' failed with exit code 1.
Jul 06 13:56:34 ThinkPad-T470s (udev-worker)[330]: nvme0n1p3: Process '/usr/bin/unshare -m /usr/bin/snap auto-import --mount=/dev/nvme0n1p3' failed with exit code 1.
Jul 06 13:56:34 ThinkPad-T470s (udev-worker)[338]: nvme0n1p1: Process '/usr/bin/unshare -m /usr/bin/snap auto-import --mount=/dev/nvme0n1p1' failed with exit code 1.
Jul 06 13:56:34 ThinkPad-T470s (udev-worker)[332]: nvme0n1p4: Process '/usr/bin/unshare -m /usr/bin/snap auto-import --mount=/dev/nvme0n1p4' failed with exit code 1.
Jul 06 13:56:34 ThinkPad-T470s (udev-worker)[323]: nvme0n1p2: Process '/usr/bin/unshare -m /usr/bin/snap auto-import --mount=/dev/nvme0n1p2' failed with exit code 1.
Jul 06 13:56:34 ThinkPad-T470s systemd-fsck[367]: /dev/nvme0n1p1: 197 files, 32542/98304 clusters
Jul 06 13:56:36 ThinkPad-T470s smartd[643]: Device: /dev/nvme0, opened
Jul 06 13:56:36 ThinkPad-T470s smartd[643]: Device: /dev/nvme0, SAMSUNG MZVLW256HEHP-000L7, S/N:S35ENX0K685866, FW:5L7QCXB7, 256 GB
Jul 06 13:56:36 ThinkPad-T470s smartd[643]: Device: /dev/nvme0, is SMART capable. Adding to "monitor" list.
Jul 06 13:56:36 ThinkPad-T470s smartd[643]: Device: /dev/nvme0, state read from /var/lib/smartmontools/smartd.SAMSUNG_MZVLW256HEHP_000L7-S35ENX0K685866.nvme.state
Jul 06 13:56:36 ThinkPad-T470s smartd[643]: Device: /dev/nvme0, number of Error Log entries increased from 4832 to 4837
Jul 06 13:56:36 ThinkPad-T470s smartd[643]: Device: /dev/nvme0, state written to /var/lib/smartmontools/smartd.SAMSUNG_MZVLW256HEHP_000L7-S35ENX0K685866.nvme.state
Jul 06 13:57:02 ThinkPad-T470s kernel: ntfs3: nvme0n1p3: It is recommened to use chkdsk.
Jul 06 13:57:02 ThinkPad-T470s kernel: ntfs3: nvme0n1p3: volume is dirty and "force" flag is not set!
Jul 06 14:00:56 ThinkPad-T470s plasmashell[2117]: getting temp failed for  "/dev/nvme0n1" :  Success
Jul 06 14:00:56 ThinkPad-T470s plasmashell[2117]: getting powered on time failed for  "/dev/nvme0n1" :  Success
Jul 06 14:00:56 ThinkPad-T470s plasmashell[2117]: getting power cycles failed for  "/dev/nvme0n1" :  Success
Jul 06 14:00:56 ThinkPad-T470s plasmashell[2117]: unknown file system type  ""  on  "/dev/nvme0n1p2"
Jul 06 14:00:56 ThinkPad-T470s plasmashell[2117]: "Partition &#8216;/dev/nvme0n1p3&#8217; is not properly aligned (last sector: 499,071,628, modulo: 653)."
Jul 06 14:01:59 ThinkPad-T470s plasmashell[2117]: "Add operation: Check and repair partition &#8216;/dev/nvme0n1p3&#8217; (237.86 GiB, ntfs)"
Jul 06 14:02:31 ThinkPad-T470s plasmashell[2117]: "Undoing operation: Check and repair partition &#8216;/dev/nvme0n1p3&#8217; (237.86 GiB, ntfs)"
Jul 06 14:26:36 ThinkPad-T470s smartd[643]: Device: /dev/nvme0, number of Error Log entries increased from 4837 to 4852
Jul 06 16:50:04 ThinkPad-T470s kernel: ntfs3: nvme0n1p3: It is recommened to use chkdsk.
Jul 06 16:50:04 ThinkPad-T470s kernel: ntfs3: nvme0n1p3: volume is dirty and "force" flag is not set!
Jul 06 16:50:12 ThinkPad-T470s kernel: ntfs3: nvme0n1p3: It is recommened to use chkdsk.
Jul 06 16:50:12 ThinkPad-T470s kernel: ntfs3: nvme0n1p3: volume is dirty and "force" flag is not set!
Jul 06 16:50:13 ThinkPad-T470s kernel: ntfs3: nvme0n1p3: It is recommened to use chkdsk.
Jul 06 16:50:13 ThinkPad-T470s kernel: ntfs3: nvme0n1p3: volume is dirty and "force" flag is not set!
Jul 06 16:50:14 ThinkPad-T470s kernel: ntfs3: nvme0n1p3: It is recommened to use chkdsk.
Jul 06 16:50:14 ThinkPad-T470s kernel: ntfs3: nvme0n1p3: volume is dirty and "force" flag is not set!
Jul 06 16:50:33 ThinkPad-T470s kernel: ntfs3: nvme0n1p3: It is recommened to use chkdsk.
Jul 06 16:50:33 ThinkPad-T470s kernel: ntfs3: nvme0n1p3: volume is dirty and "force" flag is not set!
Jul 06 18:43:58 ThinkPad-T470s kernel: ntfs3: nvme0n1p3: It is recommened to use chkdsk.
Jul 06 18:43:58 ThinkPad-T470s kernel: ntfs3: nvme0n1p3: volume is dirty and "force" flag is not set!


---

### Post by oldfred on 2024-07-06
Do not know latest version of chkdsk, but it had multiple parameters.
Some versions just run check without fixing, others fix some things.

It used to be you have to run chkdsk several times until you got no errors.

You do have to make sure fast startup & bitlocker are both off in Windows.
And really better not to mount the Windows "c:drive" partition, but create a shared NTFS data partition.
Back with XP I corrupted it multiple times viewing & clicking & moving mouse to fast & it moved folders around.

---

### Post by yancek on 2024-07-06
> I have been accessing the windows system files via the network when it was on another computer. Now it is on the same computer, 

Modifying folders/files (images, music files, etc.) on an ntfs filesystem from Linux should work but modifying any system files on a windows OS from Linux is a bad idea.

When you run the ls -al command on /boot/efi/EFI, you should see an ubuntu directory.  If you have windows installed also, you should see a Microsoft directory with EFI files in the respective directories.  I don't know what the files you shown under efi with the '.REC' extension are and have never seen that before.  Can you read those files?

The exit code 1 error from the mount command you posted means those commands need to be run as root (sudo) and were not.

Your journalctl output clearly shows the 3rd partition (ntfs) needs chkdsk run from windows so that would be the obvious next step if you have not done it and if you have, what was the result?

You should also check the various parameters for chkdsk to see what would be most appropriate in your case.

---

### Post by oygle on 2024-07-06
Thanks @oldfred

> **oldfred said:**
> Do not know latest version of chkdsk, but it had multiple parameters.
Some versions just run check without fixing, others fix some things.

It used to be you have to run chkdsk several times until you got no errors.

I have run it a few times now, states it "fixes" errors, yet when I display the following, one can see it has 'chkdsk' type files still there.

```
sudo ls -al  /boot/efi
```

> 
total 462
drwx------ 4 root root  1024 Jan  1  1970  .
drwxr-xr-x 4 root root  4096 Jun 27 12:16  ..
drwx------ 5 root root  1024 Apr 27 13:06  EFI
-rwx------ 1 root root 80896 Jan  1  1980  FSCK0000.REC
-rwx------ 1 root root 80896 Jan  1  1980  FSCK0001.REC
-rwx------ 1 root root 46080 Jan  1  1980  FSCK0002.REC
-rwx------ 1 root root 78848 Jan  1  1980  FSCK0003.REC
-rwx------ 1 root root 79872 Jan  1  1980  FSCK0004.REC
-rwx------ 1 root root 46080 Jan  1  1980  FSCK0005.REC
-rwx------ 1 root root 20480 Jan  1  1980  FSCK0006.REC
-rwx------ 1 root root 32768 Jan  1  1980  FSCK0007.REC
drwx------ 2 root root  1024 Jul 28  2022 'System Volume Information'


but of course /boot/efi is mounted at partition 1, from the **mount** command

> **oldfred said:**
> 
You do have to make sure fast startup & bitlocker are both off in Windows.

Won't that affect Kubuntu, as the one lenovo laptop has an internal SSD (windows 8.1) and an external SSD (Kubuntu)  ??

> **oldfred said:**
> 
And really better not to mount the Windows "c:drive" partition, but create a shared NTFS data partition.
Back with XP I corrupted it multiple times viewing & clicking & moving mouse to fast & it moved folders around.

It was a bit of a learning exercise, but have now 'shrunk' drive C, made a drive D, and moved all the data, there. Even gave it a label of "Data".  Then booted into Kubuntu, and wow, can now see "Data" in Dolphin. I won't bother trying to click on the entry that is causing problems, all the data is where I want it and accessible, thanks.

---

### Post by oygle on 2024-07-06
Thanks @yancek

> **yancek said:**
> Modifying folders/files (images, music files, etc.) on an ntfs filesystem from Linux should work but modifying any system files on a windows OS from Linux is a bad idea.

Yes I agree, I only want access to the data. nothing else.

> **yancek said:**
> 
When you run the ls -al command on /boot/efi/EFI, you should see an ubuntu directory.  If you have windows installed also, you should see a Microsoft directory with EFI files in the respective directories.  I don't know what the files you shown under efi with the '.REC' extension are and have never seen that before.  Can you read those files?

This is what I see ..

```
sudo ls -al  /boot/efi/EFI
```

> total 5
drwx------ 5 root root 1024 Apr 27 13:06 .
drwx------ 4 root root 1024 Jan  1  1970 ..
drwx------ 2 root root 1024 Apr 27 13:06 Boot
drwx------ 4 root root 1024 Jul 28  2022 Microsoft
drwx------ 2 root root 1024 Apr 27 13:06 ubuntu


> **yancek said:**
> The exit code 1 error from the mount command you posted means those commands need to be run as root (sudo) and were not.

Okay thanks

> **yancek said:**
> Your journalctl output clearly shows the 3rd partition (ntfs) needs chkdsk run from windows so that would be the obvious next step if you have not done it and if you have, what was the result?

You should also check the various parameters for chkdsk to see what would be most appropriate in your case.

I did run it and all was okay, but now that I have shrunk drive C , added a D: drive, a chkdsk on Drive C: can only be scheduled. I may try that later.

---

### Post by oygle on 2024-07-07
Considering the following information, how can I:

1.  Be able to add/delete/modify files on the (Windows) partion called "Data".  The mount parameters for '/dev/nvme0n1p4' has "rw" so I assume Windows has some flags set ?
2.  Reduce or eliminate the errors on the partitions on /dev/nvme0 ?  That may indicate some sort of deeper level 'chkdsk' or similar from Windows, as I think all the Kubuntu reported errors are from the **.CHK files ??

```
cat /etc/fstab
```

> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=3afe92fc-cc10-4356-b29e-81029b00590d /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=D409-6E0B  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0


```
mount | grep nvme
```

> 
/dev/nvme0n1p1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/nvme0n1p4 on /media/********/Data type ntfs3 (rw,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,uhelper=udisks2)


```
sudo journalctl -b | grep nvme
```

> 
Jul 08 07:45:10 ThinkPad-T470s kernel: nvme nvme0: pci function 0000:3c:00.0
Jul 08 07:45:10 ThinkPad-T470s kernel: nvme nvme0: 4/0/0 default/read/poll queues
Jul 08 07:45:10 ThinkPad-T470s kernel:  nvme0n1: p1 p2 p3 p4 p5
Jul 08 07:45:10 ThinkPad-T470s (udev-worker)[324]: nvme0n1: Process '/usr/bin/unshare -m /usr/bin/snap auto-import --mount=/dev/nvme0n1' failed with exit code 1.
Jul 08 07:45:10 ThinkPad-T470s (udev-worker)[324]: nvme0n1p1: Process '/usr/bin/unshare -m /usr/bin/snap auto-import --mount=/dev/nvme0n1p1' failed with exit code 1.
Jul 08 07:45:10 ThinkPad-T470s (udev-worker)[322]: nvme0n1p3: Process '/usr/bin/unshare -m /usr/bin/snap auto-import --mount=/dev/nvme0n1p3' failed with exit code 1.
Jul 08 07:45:10 ThinkPad-T470s (udev-worker)[331]: nvme0n1p4: Process '/usr/bin/unshare -m /usr/bin/snap auto-import --mount=/dev/nvme0n1p4' failed with exit code 1.
Jul 08 07:45:10 ThinkPad-T470s (udev-worker)[332]: nvme0n1p2: Process '/usr/bin/unshare -m /usr/bin/snap auto-import --mount=/dev/nvme0n1p2' failed with exit code 1.
Jul 08 07:45:10 ThinkPad-T470s (udev-worker)[320]: nvme0n1p5: Process '/usr/bin/unshare -m /usr/bin/snap auto-import --mount=/dev/nvme0n1p5' failed with exit code 1.
Jul 08 07:45:10 ThinkPad-T470s systemd-fsck[371]: /dev/nvme0n1p1: 197 files, 32542/98304 clusters
Jul 08 07:45:11 ThinkPad-T470s smartd[653]: Device: /dev/nvme0, opened
Jul 08 07:45:11 ThinkPad-T470s smartd[653]: Device: /dev/nvme0, SAMSUNG MZVLW256HEHP-000L7, S/N:S35ENX0K685866, FW:5L7QCXB7, 256 GB
Jul 08 07:45:11 ThinkPad-T470s smartd[653]: Device: /dev/nvme0, is SMART capable. Adding to "monitor" list.
Jul 08 07:45:11 ThinkPad-T470s smartd[653]: Device: /dev/nvme0, state read from /var/lib/smartmontools/smartd.SAMSUNG_MZVLW256HEHP_000L7-S35ENX0K685866.nvme.state
Jul 08 07:45:11 ThinkPad-T470s smartd[653]: Device: /dev/nvme0, number of Error Log entries increased from 4901 to 4904
Jul 08 07:45:11 ThinkPad-T470s smartd[653]: Device: /dev/nvme0, state written to /var/lib/smartmontools/smartd.SAMSUNG_MZVLW256HEHP_000L7-S35ENX0K685866.nvme.state
Jul 08 07:52:26 ThinkPad-T470s udisksd[663]: Mounted /dev/nvme0n1p4 at /media/********/Data on behalf of uid 1000


```
lsblk
```

> 
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0         7:0    0     4K  1 loop /snap/bare/5
loop1         7:1    0  73.9M  1 loop /snap/core22/864
loop2         7:2    0  74.2M  1 loop /snap/core22/1380
loop3         7:3    0 268.6M  1 loop /snap/firefox/4451
loop4         7:4    0 505.1M  1 loop /snap/gnome-42-2204/176
loop5         7:5    0  38.7M  1 loop /snap/snapd/21465
loop6         7:6    0 268.7M  1 loop /snap/firefox/4483
loop7         7:7    0 127.8M  1 loop /snap/yt-dlp/578
loop8         7:8    0  91.7M  1 loop /snap/gtk-common-themes/1535
loop9         7:9    0  38.8M  1 loop /snap/snapd/21759
loop10        7:10   0   497M  1 loop /snap/gnome-42-2204/141
sda           8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1        8:1    0   480M  0 part 
&#9492;&#9472;sda2        8:2    0   931G  0 part /var/snap/firefox/common/host-hunspell
                                      /
sdb           8:16   1     0B  0 disk 
nvme0n1     259:0    0 238.5G  0 disk 
&#9500;&#9472;nvme0n1p1 259:1    0   100M  0 part /boot/efi
&#9500;&#9472;nvme0n1p2 259:2    0    16M  0 part 
&#9500;&#9472;nvme0n1p3 259:3    0   189G  0 part 
&#9500;&#9472;nvme0n1p4 259:4    0  48.8G  0 part /media/********/Data
&#9492;&#9472;nvme0n1p5 259:5    0   509M  0 part


```
sudo blkid
```

> /dev/sda2: UUID="3afe92fc-cc10-4356-b29e-81029b00590d" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="0d661e46-5361-4aa7-91cc-0f397f518246"
/dev/loop1: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/nvme0n1p5: BLOCK_SIZE="512" UUID="9862A51762A4FB60" TYPE="ntfs" PARTUUID="e7e22210-cb00-418d-ba4b-c2def6047377"
/dev/nvme0n1p3: BLOCK_SIZE="512" UUID="DABA0B69BA0B418D" TYPE="ntfs" PARTUUID="21600ef4-2f6d-4bf9-b98a-6eecd29f09ef"
/dev/nvme0n1p1: UUID="D409-6E0B" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="91328940-5e3a-426d-8d8e-f56ddc0c8478"
/dev/nvme0n1p4: LABEL="Data" BLOCK_SIZE="512" UUID="AA429B21429AF175" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="14e53fb8-71d8-4d61-b23c-c0c08c262842"
/dev/nvme0n1p2: PARTUUID="114c146a-55af-439d-b338-30cd1ae82a6d"
/dev/loop8: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop6: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop4: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop2: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop0: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop9: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop7: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/sda1: UUID="4EEB-9861" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="df0eeac9-da2a-46b2-b571-a91ec5bcf1d2"
/dev/loop5: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop3: BLOCK_SIZE="131072" TYPE="squashfs"
/dev/loop10: BLOCK_SIZE="131072" TYPE="squashfs"

```
sudo fdisk -l /dev/nvme0n1
```

> Disk /dev/nvme0n1: 238.47 GiB, 256060514304 bytes, 500118192 sectors
Disk model: SAMSUNG MZVLW256HEHP-000L7              
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: ADE8ABB0-4F85-41E5-BCA4-D29D398B84FF

Device             Start       End   Sectors  Size Type
/dev/nvme0n1p1      2048    206847    204800  100M EFI System
/dev/nvme0n1p2    206848    239615     32768   16M Microsoft reserved
/dev/nvme0n1p3    239616 396671628 396432013  189G Microsoft basic data
/dev/nvme0n1p4 396673024 499070975 102397952 48.8G Microsoft basic data
/dev/nvme0n1p5 499073024 500115455   1042432  509M Windows recovery environment

---

### Post by oygle on 2024-07-07
If a Windows **chkdsk** is stating no errors found, is it okay, from Ubuntu to remove the *.REC files ?

```
sudo ls -al /boot/efi
```

> 
total 462
drwxr-xr-x 4 root root  1024 Jan  1  1970  .
drwxr-xr-x 4 root root  4096 Jun 27 12:16  ..
drwxr-xr-x 5 root root  1024 Apr 27 13:06  EFI
-rwxr-xr-x 1 root root 80896 Jan  1  1980  FSCK0000.REC
-rwxr-xr-x 1 root root 80896 Jan  1  1980  FSCK0001.REC
-rwxr-xr-x 1 root root 46080 Jan  1  1980  FSCK0002.REC
-rwxr-xr-x 1 root root 78848 Jan  1  1980  FSCK0003.REC
-rwxr-xr-x 1 root root 79872 Jan  1  1980  FSCK0004.REC
-rwxr-xr-x 1 root root 46080 Jan  1  1980  FSCK0005.REC
-rwxr-xr-x 1 root root 20480 Jan  1  1980  FSCK0006.REC
-rwxr-xr-x 1 root root 32768 Jan  1  1980  FSCK0007.REC
drwxr-xr-x 2 root root  1024 Jul 28  2022 'System Volume Information'


---

### Post by oldfred on 2024-07-07
.REC files are the recovery files that chkdsk created.

Generally you should not need chkdsk from Windows or dosfsck from Linux on the ESP.
But if you have Windows repair/recovery drive and Ubuntu live installer, you can always restore any missing files in ESP, by reinstalling Windows boot or Ubuntu boot with total reinstall of grub.

---

### Post by oygle on 2024-07-07
Thanks @oldfred

> **oldfred said:**
> .REC files are the recovery files that chkdsk created.

Yes, and I did wonder if removing them may 'fix' the problem, but I don't think so. I have redone the complete **chkdsk** thing on Windows, it took a while, had to be done on a reboot. Then also made Drive D: from windows 'shareable' as I thought that may fix the 'unable to delete files' problem. Nope. Have now been reading up more on the issues and many articles agree with what you suggested, disable fastboot. At the time I thought if I change it in BIOS it may affect the Kubuntu boots. But these articles mention adjusting the settings under windows power settings, the shutdown. That was how to do it. Have still to test that though.

> **oldfred said:**
> Generally you should not need chkdsk from Windows or dosfsck from Linux on the ESP. But if you have Windows repair/recovery drive and Ubuntu live installer, you can always restore any missing files in ESP, by reinstalling Windows boot or Ubuntu boot with total reinstall of grub.

I don't think I have a windows repair/recovery disk. If I need to reinstall GRUB no doubt the instructions will be at [https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295)

Have noticed any changes to the kernels, even a autoremove adjusts the boot process, recent log ..

> sudo apt autoremove
[sudo] password for ********:
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-6.5.0-9 linux-headers-6.5.0-9-generic linux-image-6.5.0-9-generic linux-modules-6.5.0-9-generic linux-modules-extra-6.5.0-9-generic
0 to upgrade, 0 to newly install, 5 to remove and 0 not to upgrade.
After this operation, 273 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 261754 files and directories currently installed.)
Removing linux-headers-6.5.0-9-generic (6.5.0-9.9) ...
Removing linux-headers-6.5.0-9 (6.5.0-9.9) ...
Removing linux-image-6.5.0-9-generic (6.5.0-9.9) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-6.5.0-9-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.5.0-35-generic
Found initrd image: /boot/initrd.img-6.5.0-35-generic
Found linux image: /boot/vmlinuz-6.5.0-28-generic
Found initrd image: /boot/initrd.img-6.5.0-28-generic
Found memtest86+ 64bit EFI image: /boot/memtest86+x64.efi
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
done
Removing linux-modules-extra-6.5.0-9-generic (6.5.0-9.9) ...
Removing linux-modules-6.5.0-9-generic (6.5.0-9.9) ...

---

### Post by oldfred on 2024-07-08
There is UEFI fastboot and Windows fast startup.

Fast boot is a setting that assumes no system changes and the data written to the drive for the operating system by the UEFI/BIOS is not updated.
Often then boot is so quick you do not have time to press any key to get into UEFI settings or one time boot.
You can "cold" boot or full power down instead of "warm" reboot which cold boot then uses a full boot or write of hardware configuration to drive.
Fast startup should be off whenever making system changes. It can be turned back on when all changes are done.

Fast start up is Windows partial hibernation that is always used. It writes main boot info into a hibernation file and sets hibernation flag on all NTFS (and FAT32?) partitions. Linux NTFS driver will see hibernation flag and not normally mount NTFS that is hibernated to prevent damage. Partition may be mounted read only. Have seen a few uses that were able to write into NTFS, then wondered why files were lost. Hibernation restored system to as it was before use by any other system. Two Windows installs can have same issues.
If never mounting and using any NTFS partitions in Linux fast startup can be on, otherwise you have to have it off.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/](https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/)
[https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/](https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

---

### Post by oygle on 2024-07-08
Thank you @oldfred

Those links have been very helpful.  Have now turned **off** Fast Startup in the shutdown settings in Windows. I will leave it off, as no need for it to be on, and keep on eye on it after any Windows updates.

Booting back into Kubuntu, still cannot delete any files, and of course Dolphin spits the dummy on /dev/nvme0n1p3 , butt that's fine, as I only use the new 'Data' partition.

What has changed are some new Journal entries as foolows:

> 
Jul 09 07:55:04 ThinkPad-T470s kernel: ntfs3: nvme0n1p3: It is recommened to use chkdsk.
Jul 09 07:55:04 ThinkPad-T470s kernel: ntfs3: nvme0n1p3: volume is dirty and "force" flag is not set!


Having run chkdsk a number of times, it still leaves those files there. I see no harm in manually deleting them from Kubuntu, because I cannot see them in Windows, not even from Power shell. Have done some searching and this warning from [https://bbs.archlinux.org/viewtopic.php?id=271650](https://bbs.archlinux.org/viewtopic.php?id=271650) ..

> The more proper reply would be: DON'T use ntfs on linux!
if you want to proper fix a ntfs partition: use windows! and use the full suite of chkdsk: /F /X /R /B
if you need some FS for data exchnage between OSs: use exFAT

and yes, better to fix the problem from Windows. I will later try using all of those flags in **chkdsk**

---

### Post by oldfred on 2024-07-08
I agree that you should only use NTFS if also booting Windows & then run any repairs from Windows.
But still think NTFS is better than exFAT. Although exFAT is better than FAT32.
FAT32 should only be used for smaller partitions (like ESP where required) as it cannot store files over 4GB and has no journal.

The standard exFAT implementation is not journaled and only uses a single file allocation table and free space map. 
But exFAT will store larger files than FAT32. But still should not be used for larger partitions as chkdsk may take forever. 
And it does not have Linux ownership & permissions.

---

### Post by oygle on 2024-07-08
Have read quite a few posts about deleting or recovering the .CHK files. The reasons to support deletion is that they seem to be fragments of corrupted files. That said I will still run chkdsk with all those parameters. Will also try this method as it is for Win 8.1 , same version. It is hard to locate the files though, they don't show up under 'hidden', I assume a 'system' flag may reveal them -  [https://support.microsoft.com/en-us/topic/use-the-system-file-checker-tool-to-repair-missing-or-corrupted-system-files-79aa86cb-ca52-166a-92a3-966e85d4094e](https://support.microsoft.com/en-us/topic/use-the-system-file-checker-tool-to-repair-missing-or-corrupted-system-files-79aa86cb-ca52-166a-92a3-966e85d4094e)

---

### Post by oygle on 2024-07-09
Yesterday I ran all sorts of system scans and supposed 'file fixing' tools on Windows. Also ran **chkdsk** with the 4 parms, ..no changes.

```
sudo apt upgrade
```

> Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  grub-common grub-efi-amd64-bin grub-efi-amd64-signed grub-pc grub-pc-bin grub2-common
0 to upgrade, 0 to newly install, 0 to remove and 6 not to upgrade.

So I decided to force the update ...

```
sudo apt-get install grub-common grub-efi-amd64-bin grub-efi-amd64-signed grub-pc grub-pc-bin grub2-common
```

> Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Suggested packages:
  multiboot-doc grub-emu mtools desktop-base
The following packages will be upgraded:
  grub-common grub-efi-amd64-bin grub-efi-amd64-signed grub-pc grub-pc-bin grub2-common
6 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 7,004 kB of archives.
After this operation, 48.1 kB disk space will be freed.
Get:1 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) mantic-updates/main amd64 grub2-common amd64 2.12~rc1-10ubuntu4.2 [666 kB]
Get:2 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) mantic-updates/main amd64 grub-pc amd64 2.12~rc1-10ubuntu4.2 [137 kB]
Get:3 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) mantic-updates/main amd64 grub-pc-bin amd64 2.12~rc1-10ubuntu4.2 [1,100 kB]
Get:4 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) mantic-updates/main amd64 grub-common amd64 2.12~rc1-10ubuntu4.2 [2,107 kB]
Get:5 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) mantic-updates/main amd64 grub-efi-amd64-signed amd64 1.197.2+2.12~rc1-10ubuntu4.2 [1,378 kB]
Get:6 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) mantic-updates/main amd64 grub-efi-amd64-bin amd64 2.12~rc1-10ubuntu4.2 [1,617 kB]
Fetched 7,004 kB in 2s (4,218 kB/s)           
Preconfiguring packages ...
(Reading database ... 244629 files and directories currently installed.)
Preparing to unpack .../0-grub2-common_2.12~rc1-10ubuntu4.2_amd64.deb ...
Unpacking grub2-common (2.12~rc1-10ubuntu4.2) over (2.12~rc1-10ubuntu4) ...
Preparing to unpack .../1-grub-pc_2.12~rc1-10ubuntu4.2_amd64.deb ...
Unpacking grub-pc (2.12~rc1-10ubuntu4.2) over (2.12~rc1-10ubuntu4) ...
Preparing to unpack .../2-grub-pc-bin_2.12~rc1-10ubuntu4.2_amd64.deb ...
Unpacking grub-pc-bin (2.12~rc1-10ubuntu4.2) over (2.12~rc1-10ubuntu4) ...
Preparing to unpack .../3-grub-common_2.12~rc1-10ubuntu4.2_amd64.deb ...
Unpacking grub-common (2.12~rc1-10ubuntu4.2) over (2.12~rc1-10ubuntu4) ...
Preparing to unpack .../4-grub-efi-amd64-signed_1.197.2+2.12~rc1-10ubuntu4.2_amd64.deb ...
Unpacking grub-efi-amd64-signed (1.197.2+2.12~rc1-10ubuntu4.2) over (1.197+2.12~rc1-10ubuntu4) ...
Preparing to unpack .../5-grub-efi-amd64-bin_2.12~rc1-10ubuntu4.2_amd64.deb ...
Unpacking grub-efi-amd64-bin (2.12~rc1-10ubuntu4.2) over (2.12~rc1-10ubuntu4) ...
Setting up grub-common (2.12~rc1-10ubuntu4.2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Setting up grub-efi-amd64-bin (2.12~rc1-10ubuntu4.2) ...
Setting up grub2-common (2.12~rc1-10ubuntu4.2) ...
Setting up grub-pc-bin (2.12~rc1-10ubuntu4.2) ...
Setting up grub-pc (2.12~rc1-10ubuntu4.2) ...
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.5.0-42-generic
Found initrd image: /boot/initrd.img-6.5.0-42-generic
Found linux image: /boot/vmlinuz-6.5.0-41-generic
Found initrd image: /boot/initrd.img-6.5.0-41-generic
Found memtest86+ 64bit EFI image: /boot/memtest86+x64.efi
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
done
Setting up grub-efi-amd64-signed (1.197.2+2.12~rc1-10ubuntu4.2) ...
Trying to migrate /boot/efi into esp config
Installing grub to /boot/efi.
Installing for x86_64-efi platform.
Installation finished. No error reported.
Processing triggers for install-info (7.0.3-2) ...
Processing triggers for man-db (2.11.2-3) ...

Will see on the next boot if it made any changes, but I don't think so, when the problem seems to be _**all sourced from**_ Windows.

---

### Post by oygle on 2024-07-16
Still getting journal errors, although the Windows partition I need (internal SSD) is totally accessible.

```
journalctl -b | grep nvme
```

> Jul 17 07:43:02 ThinkPad-T470s kernel: nvme nvme0: pci function 0000:3c:00.0
Jul 17 07:43:02 ThinkPad-T470s kernel: nvme nvme0: 4/0/0 default/read/poll queues
Jul 17 07:43:02 ThinkPad-T470s kernel:  nvme0n1: p1 p2 p3 p4 p5
Jul 17 07:43:02 ThinkPad-T470s systemd[1]: nvmefc-boot-connections.service - Auto-connect to subsystems on FC-NVME devices found during boot was skipped because of an unmet condition check (ConditionPathExists=/sys/class/fc/fc_udev_device/nvme_discovery).
Jul 17 07:43:02 ThinkPad-T470s (udev-worker)[317]: nvme0n1: Process '/usr/bin/unshare -m /usr/bin/snap auto-import --mount=/dev/nvme0n1' failed with exit code 1.
Jul 17 07:43:02 ThinkPad-T470s (udev-worker)[317]: nvme0n1p1: Process '/usr/bin/unshare -m /usr/bin/snap auto-import --mount=/dev/nvme0n1p1' failed with exit code 1.
Jul 17 07:43:02 ThinkPad-T470s (udev-worker)[328]: nvme0n1p2: Process '/usr/bin/unshare -m /usr/bin/snap auto-import --mount=/dev/nvme0n1p2' failed with exit code 1.
Jul 17 07:43:02 ThinkPad-T470s (udev-worker)[314]: nvme0n1p4: Process '/usr/bin/unshare -m /usr/bin/snap auto-import --mount=/dev/nvme0n1p4' failed with exit code 1.
Jul 17 07:43:02 ThinkPad-T470s (udev-worker)[326]: nvme0n1p3: Process '/usr/bin/unshare -m /usr/bin/snap auto-import --mount=/dev/nvme0n1p3' failed with exit code 1.
Jul 17 07:43:02 ThinkPad-T470s (udev-worker)[338]: nvme0n1p5: Process '/usr/bin/unshare -m /usr/bin/snap auto-import --mount=/dev/nvme0n1p5' failed with exit code 1.
Jul 17 07:43:02 ThinkPad-T470s systemd-fsck[366]: /dev/nvme0n1p1: 197 files, 32518/98304 clusters
Jul 17 07:43:03 ThinkPad-T470s ntfs-3g[469]: Mounted /dev/nvme0n1p4 (Read-Write, label "Data", NTFS 3.1)
Jul 17 07:43:03 ThinkPad-T470s ntfs-3g[469]: Mount options: allow_other,nonempty,relatime,rw,fsname=/dev/nvme0n1p4,blkdev,blksize=4096
Jul 17 07:43:03 ThinkPad-T470s smartd[663]: Device: /dev/nvme0, opened
Jul 17 07:43:03 ThinkPad-T470s smartd[663]: Device: /dev/nvme0, SAMSUNG MZVLW256HEHP-000L7, S/N:S35ENX0K685866, FW:5L7QCXB7, 256 GB
Jul 17 07:43:03 ThinkPad-T470s smartd[663]: Device: /dev/nvme0, is SMART capable. Adding to "monitor" list.
Jul 17 07:43:03 ThinkPad-T470s smartd[663]: Device: /dev/nvme0, state read from /var/lib/smartmontools/smartd.SAMSUNG_MZVLW256HEHP_000L7-S35ENX0K685866.nvme.state
Jul 17 07:43:04 ThinkPad-T470s smartd[663]: Device: /dev/nvme0, number of Error Log entries increased from 5341 to 5344
Jul 17 07:43:04 ThinkPad-T470s smartd[663]: Device: /dev/nvme0, state written to /var/lib/smartmontools/smartd.SAMSUNG_MZVLW256HEHP_000L7-S35ENX0K685866.nvme.state

```
mount |grep nvme
```

> /dev/nvme0n1p1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/nvme0n1p4 on /media/********/Windows_Data type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)

Those **failed exit code 1 errors** , someone mentioned it was permissions, which is verified at [https://askubuntu.com/questions/402850/unable-to-mount-exit-code-1/402855#402855](https://askubuntu.com/questions/402850/unable-to-mount-exit-code-1/402855#402855)

The **number of Error Log entries increased** messages are a debian bug

it is the root (Drive C:\ on windows) that is the cause I think. Unbale to get rid of the **chkdsk** errors. Actually can't find those files from Windows but Kubuntu can see them.

Possibly .. 1.  Take a image of the Windows SSD drive, then 2. Reformat it, then 3.  Restore  may get rid of the errors.

---

### Post by ramon-godoy on 2024-10-11
started having the same problem yesterday.

i've been using 2 SSDs to dual boot my laptop for years.

yesterday after ubuntu applied a live patch the laptop froze and the windows partition wont automatically mount anymore.

for some reason dolphin says the error is in /dev/nvme0n1p3 when the winndows ssd partition to be mounted actually is /dev/nvme1n1p3

```

An error occurred while accessing 'Windows-SSD', the system responded: The requested operation has failed: 
Error mounting /dev/nvme0n1p3 at /media/usuario/Windows-SSD1: 
wrong fs type, bad option, bad superblock on /dev/nvme0n1p3, missing codepage or helper program, or other error

```
i noticed that it does mount if i add it to /etc/fstab

```
/dev/nvme1n1p3   /media/usuario/Windows-SSD  ntfs   defaults,nofail   0 0

``` 

but that is not what i had before and its not what i want, so i'll keep searching for an answer.

if you found anything else, please let me know.

---

### Post by ramon-godoy on 2024-10-11
well... i just found out that on each reboot the SSDs switch positions.

sometimes windows-ssd is nvme0 and ubuntu is nvme1. and vice-versa.

and for some reason dolphin cant update this reference and tries to mount the old device partition in /media/

it all started yesterday after the update. something happened and i cant find out what.

---

### Post by ramon-godoy on 2024-10-11
problem solved.

the ntfs partition was marked as dirty, and ubuntu does not automount when this happens

to unmark it:

```
ntfsfix --clear-dirty /dev/nvme0n1p3
```

and a reboot.

everything back to normal now.

---

### Post by yancek on 2024-10-11
If you are accessing reading and writing to an ntfs partition from both windows and Linux, you need to be aware that some windows updates will turn on hibernation and Linux will not mount those partitions so you will then not be able to access them.  If you have hibernation off, there should not be a problem but note that some windows updates will turn it back on and will not ask or notify you that it is happening.  Usually when this happens you will get a message on your Linux system indicating the windows partition is in an unsafe state.

---

### Post by oygle on 2024-10-11
Definitely Windows hibernation plays a part in this. It's important to turn off hibernation at shutdown. Since I had the errors I have done a fresh install of Kubuntu 24.04.1 , and now Dolphin has no errors at all. I'm assuming something happened to fix things on the Windows SSD at install time.

My setup is slightly different to @ramon-godoy , in it is not dual boot off the one SSD. I have Windows on an internal SSD and Kubuntu on an external SSD. I don't use grub to boot to Windows, just power down Kubuntu, disconnect the external SSD (have seen too many problems on different posts to try dual boot with Windows), then power up into Windows. I only use Windows every 3 or 4 weeks so this suits me.

When the problem appeared I did try to attempt to fix the CHKDSK errors on Windows, as Kubuntu kept recognising those errors, despite having run a number of tools on Windows to fix it. Here are some commands run from Windows ..

```
C:\>sfc /scannow
```

> Beginning system scan.  This process will take some time.

Beginning verification phase of system scan.
Verification 100% complete.

Windows Resource Protection found corrupt files and successfully repaired them.
For online repairs, details are included in the CBS log file located at
windir\Logs\CBS\CBS.log. For example C:\Windows\Logs\CBS\CBS.log. For offline
repairs, details are included in the log file provided by the
/OFFLOGFILE flag.

and Kubuntu ..

# Nvme error logging
```
sudo apt install nvme-cli
sudo nvme error-log /dev/nvme0
```

When to Use fsck  - [https://www.linode.com/docs/guides/how-to-use-fsck-qa/](https://www.linode.com/docs/guides/how-to-use-fsck-qa/)

```
chkdsk /f /r c:
```

# Finding details by id, by uuid and by label

```
  ls -l /dev/disk/by-id
ls -l /dev/disk/by-uuid
ls -l /dev/disk/by-label

```

---

### Post by Morbius1 on 2024-10-12
When you go through the file manager to mount an ntfs partition it will use the ntfs3 driver.

ntfs3 has "issues" while the older ntfs-3g driver does not. Both are available on your system.

If you prevent ntfs3 from being used the file manager will use the more reliable ntfs-3g driver.

TO prevent ntfs3 from being used blacklist it:
```
echo 'blacklist ntfs3' | sudo tee /etc/modprobe.d/disable-ntfs3.conf
```
You need to reboot.

---

### Post by ramon-godoy on 2024-10-12
cool. learned something new today.

---

### Post by ramon-godoy on 2024-10-12
does dmesg shows your windows partition as "dirty"?

```

dmesg | grep "dirty"

```

thats what happened with my pc, probably related to hibernation as @yancek said above.

but all i had to do fix it was 

```

ntfsfix --clear-dirty /dev/nvme0n1p3

```

(and disable windows hibernation/fast startup)

---

### Post by Morbius1 on 2024-10-12
The problem is that **[COLOR="#FF0000"]may[/COLOR]** not be the end of it: [Does the Linux NTFS3 Driver Corrupt Directories?](https://www.heiko-sieger.info/does-the-linux-ntfs3-driver-corrupt-directories/)

---

### Post by yancek on 2024-10-12
If you are using windows and Linux on a data partition, you need to bear in mind that  windows will sometimes turn hibernation back on during an update.  You will not be asked if you want this nor will you be informed that it is happening and Linux won't mount a hibernated partition due to high risk of data loss.

---

