---
title: "How to: Repairing Your Filesystem"
date: 2008-07-28
forum: General Help
---

### Post by abazoskib on 2008-07-28
I looked for a straight week for a clear, concise guide in helping me repair my filesystem, and I could not find one. I did manage to find bits and pieces of information that I used together to completely repair my filesystem. For all the Linux noobs like myself out there, here's a step by step on how to repair your filesystem.


PREREQUISITE - do this while in normal user mode in Ubuntu

a. Find your ubuntu installation path.

```
sudo nano /etc/fstab
```

this will list all your partitions basically. You want the one that is of the format 'ext3'

now on my machine, it gives me /dev/hda3, however i soon realised that this must be pointed to by /dev/sda3 

so just to check this before the recovery i ran:

```
sudo parted /dev/sda3 p
```

which gave me a confirmation that the partition is of type 'ext3' and therefore is my Ubuntu installation path

...onto the RECOVERY!

1. Using an Ubuntu installation cd, boot into 'Live CD Mode' or in other words, run Ubuntu from the cd.

2. Once everything has finished loading go to your terminal and enter:

```
sudo passwd root
```

after which you will be prompted for a root password. Pick something, and write it down in case you forget(you never know!).

3. Try using the command:

```
sudo e2fsck -C0 -p -f -v UBUNTU_INSTALLATION_PATH
```

If this fails, which it did for me with an error message that said:

```
Inodes that were part of a corrupted orphan linked list found...bad superblock...run fsck manually
```

This is OK.

4. If you don't get an error message and everything runs smoothly then you should be good to go. Otherwise:

```
sudo fsck -f UBUNTU_INSTALLATION_PATH
```

This will run through a series of passes and will prompt you to FIX and CLEAR items that are corrupted or fragmented. I hit 'y' for all the prompts, and this will eventually lead you to have successfully repaired your filesystem, depending on how badly corrupted your filesystem has become. Good luck!


*and sorry if this has been posted before, like I said, I could not find it, so I wanted to help the next person who struggles to find the answer.:KS

---

### Post by mssever on 2008-07-30
Step 2 is irrelevant, as setting a root password has nothing to do with FS repair or following the commands you give. (I actually think it's preferable to not have a root password.)

---

### Post by vanadium on 2008-07-30
I do not support these suggestions. In my opinion, they are unnecessarily complicated and dangerous. Indeed, among other issues, setting the root pasword is not needed nor recommended as mssever pointed out. Using parted might damage your partitioning if you are not careful. With "sudo nano /etc/fstab", you risk inadvertently changing the file. Just a "nano /etc/fstab" or even more simple, "cat /etc/fstab" will display the file without any risk?

Here are some instructions that should be safer. A is for checking your system partitions, B is  a general procedure for any partition (great for checking removable drives as well).

A -- To check and repair your root file system,  schedule a full check on the next reboot. The default checking procedures do perform repairs if needed.

1) In a command prompt, type
```

sudo touch /forcefsck

```

2) Shut down and restart: a full check will be performed on the next reboot.

Your system does this automatically after every 30 boots or after one month. You only would want to to do this yourself e.g. after a power outage.

B -- To check whatever partition apart from your system partitions (good idea for removable drives because these are never automatically checked)

1) Determine the name of the partition from the output of "sudo blkid", for example

```

vanadium@vanadium:~$ sudo blkid
/dev/sda1: UUID="c9cb8b29-152a-47ac-b952-5b9909a290ba" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="17053c24-7853-42ba-af90-b8275742dd0b" 
/dev/sdd1: SEC_TYPE="msdos" LABEL="USB" UUID="3B69-1AFD" TYPE="vfat"

```

The output of blkid shows that my removable drive is /dev/sdd1. It is formatted as vfat.

2) Unmount that partition (either by using the "sudo umount <devicename>" command or right-clicking the drive icon if there is one) and then check it with the command "sudo fsck <devicename>":

```

vanadium@vanadium:~$ sudo umount /dev/sdd1
vanadium@vanadium:~$ sudo fsck /dev/sdd1
fsck 1.40.8 (13-Mar-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sdd1: 2854 files, 26697/62472 clusters

```

The fsck command will normally (except if the file system is badly damaged!) recognize the file system automatically and invoke the correct checking tool.

This procedure is perfectly safe as it will not write to your file systems. The procedure only provides a diagnosis, a health report of your file system.

If there are no error messages, the file system is in a healthy state. If there are problems, then you need to run the dedicated tool for the file system at hand with specific options to repair the file system (you can also run fsck with the file system specific options). Unfortunately, the options differ between the tools. (e.g. "sudo dosfsck -a" to autorepair a fat volume, "sudo fsck -p" to auto-repair an ext3 system (the command provided by abazoskib is appropriate here and will provide you with a progress bar). "man <name_of_tool>" gives the manual.

---

