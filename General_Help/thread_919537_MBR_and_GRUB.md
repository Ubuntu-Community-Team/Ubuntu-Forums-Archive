---
title: "MBR and GRUB"
date: 2008-09-14
forum: General Help
---

### Post by Hobson on 2008-09-14
I'm new to Ubuntu and i recently installed Ubuntu to my harddrive and I had a conversation with a friend and he stated the following.

ME: As far as I know I don't know anythign about a boot partition
ME: at least fdisk doesn't see one
ME: i have 4 partitions
ME: wait 4...
ME: oh right
ME: Windows, Dell, Swap, Linux
ME: in that order
HIM: Then GRUb was installed to your MBR
HIM: and you're ****** 
ME: why am I ******
HIM: certain things in windows can overwrite the mbr
HIM: and you won't be able to boot linux
HIM: which is EXACTLY WHY
HIM: I'm trying to figure out boot partitions
ME: Couldn't I just reoverwrite the MBR with grub if that were to happen
ME: and why does windows always have to be a dick
HIM: yes you can but it's a hassle, the solution is to have this damn boot partition


This concerns me because I don't know how to do it if GRUB was overwritten by Windows and also concerns me because i purchased a new harddrive today and I'm backing up my windows Partion with Norton Ghost and placing it on the new harddrive.  Then I'm just going to start fresh with Ubuntu on a much bigger partition for both Operating Systems.  And it concerns me what he said there, I don't want to run into problems.

---

### Post by rraj.be on 2008-09-14
> **Hobson said:**
> 


This concerns me because I don't know how to do it if GRUB was overwritten by Windows 

To reinstall GRUB do the following

Boot into live CD.

open up the terminal and type
```

sudo grub

find /boot/grub/stage1

```
if it returns like ```
[hdX,Y]
```

then type```
 root [hdX,Y]

setup [hdX]

quit

sudo reboot
```



This will restore ur GRUB back.

---

### Post by Hobson on 2008-09-14
Thanks for the quick very helpful reply.

One more quick question though, I have windows as my first partition, how likely/frequent will it be that windows will overwrite the MBR.  Thanks

---

### Post by koenn on 2008-09-14
normally, 
only during the OS setup, 
and when you run FIXMBR or do similar repairs.

During normal operations, you have nothiong to worry about. 
There are some boot sector viruses, but when they infect your boot sector, they usually make sure that you can still boot, so that they can propagate. So, in terms of keeping your system bootable, there's not much to worry about

---

### Post by Hobson on 2008-09-14
What's the point of a boot partition if you just want to book XP and Linux?

---

### Post by rraj.be on 2008-09-14
> **Hobson said:**
> What's the point of a boot partition if you just want to book XP and Linux?

Definitions of boot volume and system volume according to wikipedia is 

> In Microsoft Windows, the system partition and boot partition use terminology than can be misleading:

    * The system partition is a disk partition that contains the boot sector and files such as NTLDR that are needed for booting Windows XP and earlier. (Windows Vista and Windows Server 2008 use a newer boot loader called bootmgr that replaces NTLDR and is configured using BCDEdit.exe).

    * The boot partition is the disk partition that contains the Windows operating system files and its support files, but obtusely, not any files responsible for booting.

There is only one system volume. However, there is one boot volume for each operating system in a multiboot system.

So your ubuntu partition will be the boot volume of ubuntu and windows partition will be the boot volume of windows.

Try this command in ubuntu terminal

```
sudo fdisk -l
```

this will list like this

> raj@raj-desktop:~$ sudo fdisk -l
[sudo] password for raj:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbedebede

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20971520    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            2612        3947    10731420    5  Extended
/dev/sda3            3948        5314    10973184   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4            5315       19457   113603647+  83  Linux
/dev/sda5            2612        3947    10731388+  83  Linux
raj@raj-desktop:~$ 


The ' * ' ndicates the boot partition.

---

