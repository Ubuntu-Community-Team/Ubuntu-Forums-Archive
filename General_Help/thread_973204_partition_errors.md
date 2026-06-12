---
title: "partition errors"
date: 2008-11-06
forum: General Help
---

### Post by KenSpeedie on 2008-11-06
I am running dapper on an HP motherboad with a CD and two removable HDs.

I have dapper loaded on the first HD and use the second for backup storage.

The only way I can get HDA to run properly is to turn off HDB.

When both HDs are turned on and it boots up, it has a long pause at "Files needed to boot".  About half of the time it gives me hda1 errors. Every so often it will run a check on hda1 files.  a couple of times it told me to run fsck.   When It does run I get all kinds of strange errors (mainly keyboard errors)

(Seems to me that HD partition and keyboard are two different issues.  All I can tell you is that I get keyboard errors when HDB is turned on and I don't when HDB is off.)

I even changed out the keyboard but got the same errors.

I ran testdisk on HDA and got the following:


Disk /dev/hda - 38166 MB - CHS 77545 16 63

Check current partition structure

     Partition                  Start        End    Size in sectors
 1 * Linux                    0   1  1 74587   7 63   75184137
Warning: Bad ending head (CHS and LBA don't match)
 2 E extended             74587   8  1 77535  14 63    2972025
Warning: Bad starting head (CHS and LBA don't match)
 5 L Linux Swap           74587   9  1 77535  14 63    2971962
Warning: Bad starting head (CHS and LBA don't match)


I cannot run testdisk on HDB beause when I boot up with HDB turned on I get keyboard errors that prevent me from running anything from the terminal.

Any ideas of how to fix the problem?  If you have any suggestions, please be VERY specific.  I am afraid I am geting into uncharted areas when it comes to partitions.  It would very easy for me to blow up the whole thing and have to start over from scratch.  Not fun to even think about.

I backed up critical data files and pictures on an external laptop, but still would not like to have to rebuild from scratch.

Thanks for your help.

---

### Post by Coreigh on 2008-11-06
Are these external drives? You said they are removable. It also sound from your description that you are getting past the BIOS and in to the boot process. Will the system boot to a LiveCD? If you can, then do the disks show up properly? You could also run fsck from a LiveCD because you could unmount the hard disks.
```
sudo umount /dev/hda
sudo fsck /dev/hda
```

and again for hdb

for detailed info on fsck type man fsck in a terminal window (or google)

---

### Post by KenSpeedie on 2008-11-07
I ran fsck from a rescue disk and it came up hda1 is clean!

I also ran testdisk from the rescue disk and it says I need to run MBR from testdisk.  Like I said, I am getting in over my head when it comes to disk partitions.

What would happen if I run MBR and it makes a new master boot record on the HD?

I don't know if I stand a good chance of having it not boot at all.

Help!!!

Thanks for your reply.

---

### Post by KenSpeedie on 2008-11-07
I forgot to add other bits of information.

it is getting past the BIOS.  Both HDs are correctly identifed in the BIOS.

When I try to run kate (my favorite text editor) from the terminal with the 2nd HD  turned on I get the following errors:

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
QObject::disconnect: Unexpected null parameter
QFile::open: No file name specified

Kate starts, but it acts as if the F1 key is stuck on.  When you try to make an entry it drops down the "File" menu and won't let you type in anything.

Stange, strange.

---

### Post by KenSpeedie on 2008-11-07
I found the answer in another forum.

I set ACPI to "Enable" in the BIOS.

No more keyboard errors and hdb1 mounts correctly under fstab.

Thanks for your help.

---

