---
title: "I can't no boot ubuntu with debian-lilo installed"
date: 2005-01-14
forum: Installation &amp; Upgrades
---

### Post by Xan on 2005-01-14
Hi,

I have this partition schema:

# fdisk -l

Disk /dev/hda: 20.5 GB, 20547841536 bytes
240 heads, 63 sectors/track, 2654 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2655    20071768+   c  W95 FAT32 (LBA)

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       98865    49827928+  83  Linux
/dev/hdb2           98866      101818     1488312   82  Linux swap / Solaris
/dev/hdb3          101819      104298     1249920   83  Linux
/dev/hdb4          104299      155061    25584552    f  W95 Ext'd (LBA)
/dev/hdb5          104299      126247    11062264+  83  Linux
/dev/hdb6          126248      142891     8388544+  83  Linux
/dev/hdb7          142892      155061     6133648+  83  Linux

hdb1 is Debian
hdb2 swap

I wanted to install ubuntu in hdb5 and hdb7 (/ in hdb5 and /home in hdb7) but without touching (debian) lilo. I wanted to add some lines to lilo (so modify /hdb1/etc/lilo.conf).

The installation of ubuntu were fine until I arrived to boot manager. I chose no-boot-manager option (thinking I just have to add lines to debian lilo). Immediately after installation reboot, I went to debian and I touch lilo.conf.

I add the lines:

"other=/dev/hdb5
  label="Linux-Ubuntu""

but lilo show me the error:
 lilo
Warning: The boot sector and map file are on different disks.
Added Linux-2.6.8rc2 *
Added Windows
-->Fatal: First sector of /dev/hdb5 doesn't have a valid boot signature <--

So I want to know how can I do?

Thanks in advance,
Xan.

PS: Please, I'm a novice user. Say most details as you can.

---

### Post by hardcandy on 2005-01-14
Is /dev/hdb5 have the bootable flag set in fdisk? 
You'll want to boot into Debain and then mount the Ubuntu partition. First "mkdir /mnt/ubuntu". Then "mount /dev/hdb5 /mnt/ubuntu -t ext3". Navigate to /mnt/ubuntu/boot and write down what the kernel is named and  the exact wording of the initrd.img name. Then add those to your Debian /etc/lilo.conf using /mnt/ubuntu/kernel-***(fill in your numbers) and /mnt/ubuntu/initrd.img-** and "root = /dev/hdb1". Then, keeping Ubuntu mounted, run "/sbin/lilo" and see if it picks those up and adds them.

---

### Post by Xan on 2005-01-14
>Is /dev/hdb5 have the bootable flag set in fdisk?
No. The * is the mask of bootable flag in fdisk.

>You'll want to boot into Debain and then mount the Ubuntu partition. First "mkdir /mnt/ubuntu". Then "mount /dev/hdb5 /mnt/ubuntu -t ext3". Navigate to /mnt/ubuntu/boot and write down what the kernel is named and the exact wording of the initrd.img name.

The files in ubuntu are:

mnt/ubuntu/boot$ ls
config-2.6.8.1-3-386      memtest86+.bin            vmlinuz-2.6.8.1-3-386
initrd.img-2.6.8.1-3-386  System.map-2.6.8.1-3-386
$


>Then add those to your Debian /etc/lilo.conf using /mnt/ubuntu/kernel-***(fill in your numbers) and /mnt/ubuntu/initrd.img-** and "root = /dev/hdb1".

How?
With this lines?:
"image=/mnt/ubuntu/boot/vmlinuz-2.6.8.1-3-386
initrd=/mnt/ubuntu/boot/initrd.img-2.6.8.1-3-386
label="Linux-Ubuntu"
root=/dev/hdb1
read-only
"

But do I have to put hdb5 instead of hdb1? I want that ubuntu moves in hdb5, not in hdb1. Sorry if I'm wrong.

>Then, keeping Ubuntu mounted, run "/sbin/lilo" and see if it picks those up and adds them.

Yes. I know this. Perhaps it's the only that I know ;-)


Thanks,
Xan.

---

### Post by CompShrink on 2005-01-14
You should probably remove the read-only line...

Yes, root=/dev/hdb5. I think that should be right then, but I've only used lilo once (normally use grub).

---

### Post by hardcandy on 2005-01-14
Yes, the "dev/hdb1" was a mistake on my part. Use hdb5. And double check on the readonly line, I think it is recommended you keep it for a linux kernel. 
"How?
With this lines?:
"image=/mnt/ubuntu/boot/vmlinuz-2.6.8.1-3-386
initrd=/mnt/ubuntu/boot/initrd.img-2.6.8.1-3-386
label="Linux-Ubuntu"
root=/dev/hdb5
read-only"

Yes, lilo will let you know if it is correct when you run /sbin/lilo. . And you can just keep going back to the line that it finds an error on and correct it.

---

### Post by Xan on 2005-01-15
[QUOTE=hardcandy]Yes, the "dev/hdb1" was a mistake on my part. Use hdb5. And double check on the readonly line, I think it is recommended you keep it for a linux kernel. 
"How?
With this lines?:
"image=/mnt/ubuntu/boot/vmlinuz-2.6.8.1-3-386
initrd=/mnt/ubuntu/boot/initrd.img-2.6.8.1-3-386
label="Linux-Ubuntu"
root=/dev/hdb5
read-only"

Yes, lilo will let you know if it is correct when you run /sbin/lilo. . And you can just keep going back to the line that it finds an error on and correct it.[/QUOTE]

With this lines, lilo did not say me nothing. All ok.
But when I booted in ubuntu, it tell me an error with ide0 (problem related to reading, that repeats recursively). [I have to restart]. How can I catch this error in a text file?

Is it possible that it were due that, someway, I run ubuntu inside debian?. Why I have to mount ununtu on debian and I can't only put

other=/dev/hdb5
label=ubuntu?

Is it a limitation of lilo?
Could I do that in more simple way with grub?


Thanks,
Xan.

---

### Post by hardcandy on 2005-01-16
Perhaps installing grub may be easier. Before you do that, lets try one more thing. Add "table = /dev/hda1" at the end of the Ubuntu section in the lilo.config. And remount your ubuntu and run /sbin/lilo. This will let ubuntu know where the partition table is located, for some reason it may be having trouble seeing the partition table.

---

### Post by Xan on 2005-01-16
[QUOTE=hardcandy]Perhaps installing grub may be easier. Before you do that, lets try one more thing. Add "table = /dev/hda1" at the end of the Ubuntu section in the lilo.config. And remount your ubuntu and run /sbin/lilo. This will let ubuntu know where the partition table is located, for some reason it may be having trouble seeing the partition table.[/QUOTE]

If I put that, lilo shows me:
Syntax error at or above line 215 in file '/etc/lilo.conf'

---

### Post by Xan on 2005-01-16
[QUOTE=hardcandy]Perhaps installing grub may be easier. Before you do that, lets try one more thing. Add "table = /dev/hda1" at the end of the Ubuntu section in the lilo.config. And remount your ubuntu and run /sbin/lilo. This will let ubuntu know where the partition table is located, for some reason it may be having trouble seeing the partition table.[/QUOTE]


I install grub with the entry

title           Linux: Ubuntu-linux 4/10
root            (hd1,4)
kernel          (hd1,4)/vmlinuz root=/dev/hdb5 ro
initrd          (hd1,4)/initrd.img
boot

in menu.lst

and the same error reading hda. I don't know how can I copy that error in a file for show you.

Even I reinstalled ubuntu with expert mode. At final text, I give you a installtion report.

A hint could be that when I detect my hardware in installation process, ubuntu says me that ide-mod, ide-probe-mod, ide-detect and ide-floppy are missing and that perhaps if I continue the installation this problem will solve. Perhaps it's not the cause of that error.

But I want to know how can I choose the modules of a custom kernel, if I can.

*** Instalation report ****
Too much files.

If you are insterested, I could send you.

**** list of config-2.6.8.1-3-386 (vmlinuz --> /boot/vmlinuz-2.6.8.1-3-386) ****

[too long This gui does not allow me more than 30000 lines!!!!]

---

### Post by hardcandy on 2005-01-16
> >Is /dev/hdb5 have the bootable flag set in fdisk?
No. The * is the mask of bootable flag in fdisk. 

The only thing I can think of would be to double check the "fdisk /dev/hdb5" or you may be able to use "fdisk -l" from Debian and make sure the "*" shows up for /dev/hdb5.

---

### Post by Xan on 2005-01-16
The error when I boot into ubuntu is:

hda task-in-initr: status=0x59 {DriveReady SeekComplete DataRequest Error}
hda task-in-initr: error 0x04 {DriveStatusError}

that repeats itself one time over another.

Before, I rebooted (with reset button) my pc thinking it does not run.
Now, I waited for see what happens.
Ubuntu could boot completed but with amount of errors.

In messages.log you could see that:

**** messages.log ****

Jan 16 13:20:50 ubuntu syslogd 1.4.1#14ubuntu4: restart.
Jan 16 13:20:50 ubuntu kernel: klogd 1.4.1#14ubuntu4, log source = /proc/kmsg started.
Jan 16 13:20:50 ubuntu kernel: Inspecting /boot/System.map-2.6.8.1-3-386
Jan 16 13:20:51 ubuntu kernel: Loaded 28166 symbols from /boot/System.map-2.6.8.1-3-386.
Jan 16 13:20:51 ubuntu kernel: Symbols match kernel version 2.6.8.
Jan 16 13:20:51 ubuntu kernel: No module symbols loaded - kernel modules not enabled. 
Jan 16 13:20:51 ubuntu kernel: 0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: end_request: I/O error, dev hda, sector 40143549
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: ide0: reset: success
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: ide0: reset: success
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: end_request: I/O error, dev hda, sector 40143550
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: ide0: reset: success
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: ide0: reset: success
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: end_request: I/O error, dev hda, sector 40143423
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: ide0: reset: success
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: ide0: reset: success
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: end_request: I/O error, dev hda, sector 40143424
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: ide0: reset: success
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: ide0: reset: success
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: end_request: I/O error, dev hda, sector 40143425
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x5b { DriveReady SeekComplete DataRequest Index Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: ide0: reset: success
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: ide0: reset: success
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: end_request: I/O error, dev hda, sector 40143426
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: ide0: reset: success
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: ide0: reset: success
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: end_request: I/O error, dev hda, sector 40143427
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: ide0: reset: success
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x5b { DriveReady SeekComplete DataRequest Index Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: ide0: reset: success
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: end_request: I/O error, dev hda, sector 40143428
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: ide0: reset: success
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: ide0: reset: success
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: end_request: I/O error, dev hda, sector 40143429
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: ide0: reset: success
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: ide0: reset: success
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Jan 16 13:20:51 ubuntu kernel: hda: task_in_intr: error=0x04 { DriveStatusError }
Jan 16 13:20:51 ubuntu kernel: end_request: I/O error, dev hda, sector 40143430
Jan 16 13:20:51 ubuntu kernel: cdrom: open failed.
Jan 16 13:20:51 ubuntu last message repeated 2 times
Jan 16 13:20:51 ubuntu kernel: kjournald starting.  Commit interval 5 seconds
Jan 16 13:20:51 ubuntu kernel: EXT3 FS on hdb7, internal journal
Jan 16 13:20:51 ubuntu kernel: EXT3-fs: mounted filesystem with ordered data mode.
Jan 16 13:20:51 ubuntu kernel: Real Time Clock Driver v1.12
Jan 16 13:20:51 ubuntu kernel: input: PC Speaker
Jan 16 13:20:51 ubuntu kernel: inserting floppy driver for 2.6.8.1-3-386
Jan 16 13:20:51 ubuntu kernel: Floppy drive(s): fd0 is 1.44M
Jan 16 13:20:51 ubuntu kernel: FDC 0 is a post-1991 82077
Jan 16 13:20:51 ubuntu kernel: Linux agpgart interface v0.100 (c) Dave Jones
Jan 16 13:20:51 ubuntu kernel: agpgart: Detected SiS 648 chipset
Jan 16 13:20:51 ubuntu kernel: agpgart: Maximum main memory to use for agp memory: 690M
Jan 16 13:20:51 ubuntu kernel: agpgart: AGP aperture is 64M @ 0xe0000000
Jan 16 13:20:51 ubuntu kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
Jan 16 13:20:51 ubuntu kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 16 13:20:51 ubuntu kernel: ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
Jan 16 13:20:51 ubuntu kernel: ACPI: PCI interrupt 0000:00:02.3[B] -> GSI 11 (level, low) -> IRQ 11
Jan 16 13:20:51 ubuntu kernel: ohci1394: fw-host0: Unexpected PCI resource length of 1000!
Jan 16 13:20:51 ubuntu kernel: ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[11]  MMIO=[e7104000-e71047ff]  Max Packet=[2048]
Jan 16 13:20:51 ubuntu kernel: ACPI: PCI interrupt 0000:00:02.7[C] -> GSI 11 (level, low) -> IRQ 11
Jan 16 13:20:51 ubuntu kernel: intel8x0_measure_ac97_clock: measured 62243 usecs
Jan 16 13:20:51 ubuntu kernel: intel8x0: clocking to 48000
Jan 16 13:20:51 ubuntu kernel: usbcore: registered new driver usbfs
Jan 16 13:20:51 ubuntu kernel: usbcore: registered new driver hub
Jan 16 13:20:51 ubuntu kernel: ACPI: PCI interrupt 0000:00:03.0[A] -> GSI 10 (level, low) -> IRQ 10
Jan 16 13:20:51 ubuntu kernel: ohci_hcd 0000:00:03.0: Silicon Integrated Systems [SiS] USB 1.0 Controller
Jan 16 13:20:51 ubuntu kernel: ohci_hcd 0000:00:03.0: irq 10, pci mem f0aec000
Jan 16 13:20:51 ubuntu kernel: ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
Jan 16 13:20:51 ubuntu kernel: hub 1-0:1.0: USB hub found
Jan 16 13:20:51 ubuntu kernel: hub 1-0:1.0: 2 ports detected
Jan 16 13:20:51 ubuntu kernel: ACPI: PCI interrupt 0000:00:03.1[B] -> GSI 11 (level, low) -> IRQ 11
Jan 16 13:20:51 ubuntu kernel: ohci_hcd 0000:00:03.1: Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
Jan 16 13:20:51 ubuntu kernel: ohci_hcd 0000:00:03.1: irq 11, pci mem f0aee000
Jan 16 13:20:51 ubuntu kernel: ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
Jan 16 13:20:51 ubuntu kernel: hub 2-0:1.0: USB hub found
Jan 16 13:20:51 ubuntu kernel: hub 2-0:1.0: 2 ports detected
Jan 16 13:20:51 ubuntu kernel: ACPI: PCI interrupt 0000:00:03.2[C] -> GSI 10 (level, low) -> IRQ 10
Jan 16 13:20:51 ubuntu kernel: ohci_hcd 0000:00:03.2: Silicon Integrated Systems [SiS] USB 1.0 Controller (#3)
Jan 16 13:20:51 ubuntu kernel: ohci_hcd 0000:00:03.2: irq 10, pci mem f0af0000
Jan 16 13:20:51 ubuntu kernel: ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
Jan 16 13:20:51 ubuntu kernel: hub 3-0:1.0: USB hub found
Jan 16 13:20:51 ubuntu kernel: hub 3-0:1.0: 2 ports detected
Jan 16 13:20:51 ubuntu kernel: ACPI: PCI interrupt 0000:00:03.3[D] -> GSI 11 (level, low) -> IRQ 11
Jan 16 13:20:51 ubuntu kernel: ehci_hcd 0000:00:03.3: Silicon Integrated Systems [SiS] USB 2.0 Controller
Jan 16 13:20:51 ubuntu kernel: ehci_hcd 0000:00:03.3: irq 11, pci mem f0af9000
Jan 16 13:20:51 ubuntu kernel: ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
Jan 16 13:20:51 ubuntu kernel: ehci_hcd 0000:00:03.3: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
Jan 16 13:20:51 ubuntu kernel: hub 4-0:1.0: USB hub found
Jan 16 13:20:51 ubuntu kernel: hub 4-0:1.0: 6 ports detected
Jan 16 13:20:51 ubuntu kernel: ACPI: PCI interrupt 0000:00:08.0[A] -> GSI 11 (level, low) -> IRQ 11
Jan 16 13:20:51 ubuntu kernel: gameport: pci0000:00:08.1 speed 1046 kHz
Jan 16 13:20:51 ubuntu kernel: 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
Jan 16 13:20:51 ubuntu kernel: 8139too Fast Ethernet driver 0.9.27
Jan 16 13:20:51 ubuntu kernel: ACPI: PCI interrupt 0000:00:0d.0[A] -> GSI 11 (level, low) -> IRQ 11
Jan 16 13:20:51 ubuntu kernel: eth0: RealTek RTL8139 at 0xe000, 00:01:80:36:69:6e, IRQ 11
Jan 16 13:20:51 ubuntu kernel: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jan 16 13:20:51 ubuntu kernel: NET: Registered protocol family 10
Jan 16 13:20:51 ubuntu kernel: Disabled Privacy Extensions on device c02cc0c0(lo)
Jan 16 13:20:51 ubuntu kernel: IPv6 over IPv4 tunneling driver
gen 16 13:20:55 ubuntu termwrap: info: Switching console charset mapping to ISO-8859-15
gen 16 14:23:48 ubuntu termwrap: info: Switching console charset mapping to ISO-8859-1
Jan 16 14:24:42 ubuntu shutdown[4594]: shutting down for system reboot
Jan 16 13:24:49 ubuntu kernel: Kernel logging (proc) stopped.
Jan 16 13:24:49 ubuntu kernel: Kernel log daemon terminating.
Jan 16 13:24:49 ubuntu exiting on signal 15

If you need other logs, say to me.

That's all.
Can you know with that what's happen and what can I do?
Will it be solved if I recompiled (manually) the kernel?. Could it be done in install process?

Thanks,
Xan.

---

### Post by hardcandy on 2005-01-16
"Jan 16 13:20:51 ubuntu kernel: No module symbols loaded - kernel modules not enabled."
 I think that is your problem, somehow it is not initially recognizing the modules and enabling them. Do the initrd and the kernel have the same exact version numbers? I'm wondering it grub is picking up the incorrect initrd.img for the kernel it is trying to boot?

---

### Post by Xan on 2005-01-17
>Jan 16 13:20:51 ubuntu kernel: No module symbols loaded - kernel modules not enabled."
 I think that is your problem, somehow it is not initially recognizing the modules and enabling them.

Why?
What can I do for solve it?

>Do the initrd and the kernel have the same exact version numbers? I'm wondering it grub is picking up the incorrect initrd.img for the kernel it is trying to boot?

These are the same:

ubuntu$ ll initrd.img
lrwxrwxrwx  1 root root 29 2005-01-16 14:52 initrd.img -> boot/initrd.img-2.6.8.1-3-386
ubuntu$ ll vmlinuz
lrwxrwxrwx  1 root root 26 2005-01-16 14:52 vmlinuz -> boot/vmlinuz-2.6.8.1-3-386

and I have this entry in grub menu.lst:

title           Linux: PROVA - Ubuntu-linux 4/10
root            (hd1,4)
kernel         (hd1,4)/vmlinuz root=/dev/hdb5 ro
initrd           (hd1,4)/initrd.img
boot


So, this is not the problem.
What is it?

Thanks,
Xan.

---

