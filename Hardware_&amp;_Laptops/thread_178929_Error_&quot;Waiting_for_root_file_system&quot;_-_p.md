---
title: "Error: &quot;Waiting for root file system&quot; - please help!"
date: 2006-05-18
forum: Hardware &amp; Laptops
---

### Post by esscea on 2006-05-18
Having looked around here a while but I have not found any solution to my problem. The error is the same old one: The system stops during boot and cannot mount the root file system, displaying "Waiting for root file system", and dropping to a shell.

I have tried evms_activate (don't think it makes any difference though, since it says "Unable to open the control mode for Device-Mapper. The engine will run without Device-Mapper support." After pressing CTRL+D, it says /dev/hdb1 does not exist.

Does anybody have a solution for this? It seems that the forum contains more questions than answers on this point. Pleaste help me (and everybody else having this problem).

---

### Post by Fuctinger on 2006-05-19
I got this problem too. There has not been any solution yet. There's also a bug report [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/41061/+index](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/41061/+index) . But this one is only concerning scsi disks. Kernel 2.6.15-22 should have solved this problem, but not for me.

So if anyone gets an idea, pls post it here.

---

### Post by trakeen on 2006-05-19
I have this error as well. One thing I noticed is that running evms_activate does not populate /dev/evms with any devices (I guess because the device mapper can't be run?)

Is this a kernel issue or something else? The above mentioned bug report for SCSI devices sounded like it might be different then the one I (and other IDE) users are experiencing

The only solution I found was to remove the extra disks and put it back into the same config that was present at install time (which is not really a solution since I need the extra disks as file server stoarge)

---

### Post by esscea on 2006-05-19
Well, as people maybe already know, I am trying to install Dapper Beta on a system using the infamous IT8212 a.k.a. ITE 8212 RAID/ATA133 controller card as the only booting device.

What really confuses me is that Dapper officially supports this controller card, and that it does begin the boot process, which I think excludes any kind of unsupported drivers issue. Maybe it is somehow related to the evms/lvm problems that sometimes happens with the Live CD on that same computer. 

This must be treated as a quite seriuos problem with the new release, since I know that many people have the card onboard mobo (my IT8212 is a PCI addon card). Maybe there could be a way to disable evms from beginning.

I guess that there may be some way to use the Live CD and manually edit the startup scripts, but since I do not have the appropriate knowledge, let's wait for some kind of expert answer.

---

### Post by MartinRunge on 2006-10-30
Hi all,

I had a problem like this, too. Same Error message. After an upgrade from Dapper to Edgy, the new Kernel 2.6.17-10.
I figured out, that there were no partitions detected on my disk, because the ide-disk module was not loaded in the initrd.

Check in the busybox shell which appears after waiting for root FS for 5 min with:

cat /proc/protitions

-> should list you HD partitions. If not, change initrd to load the ide-disk module (analogue for other disk types...)

Now it works :-)

---

### Post by xyz on 2006-10-30
I had the same problem in Dapper lately.
This didn't really solve or explain the problem but I got my computer back on its 2 feet by booting on a Live-CD and restored my backup.tgz file.

---

### Post by ellion on 2006-11-01
> **MartinRunge said:**
> 
-> should list you HD partitions. If not, change initrd to load the ide-disk module (analogue for other disk types...)

hey,

I have the same problem, but with a SATAII disk on a Promise SATAII Controller. My IDE Disk partitions (primary slave) were all recoginized, but my SATA (primary master) with boot, swap and root werent.

So I edited /etc/initramfs-tools/modules and added ide-disk (doesnt make much sense, but I tried it) and sata_promise, set output to /boot/initrd.img-test, rebooted and edited the initrd line in grub to my initrd and booted. Sadly it made it worse: now even the ide partitions are missing

did I do anything wrong? Or any further ideas what to do?

Gotta catch some sleep now :)

---

### Post by apricot on 2007-05-20
I had also the problem: "waiting for root file system...". The problem arised due to kernel upgrade. Ubuntu changed partition names from hda to hdc, so i modificated /boot/grub/menu.lst line:

kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda7
to:
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hdc7

and i also modificated /etc/fstab on points where hda appears i changed it to hdc.
If you have mounted partitons, leave only names of the directory in /etc/fstab like they was:
example:
/dev/hdc5 /media/hda5 vfat defaults,utf8,umask=007,gid=46 0 1

Also, i do not know what changed, but my Ubuntu partition was on hda3, and now is on hdc7.
You can verify on which partition Ubuntu is by running gparted on Ubuntu Live CD.

That's all.

---

### Post by apricot on 2007-05-20
To modificate files you need use Ubuntu Live CD and mount the partition with command:

mount /dev/hdx

Change x with the number of Ubuntu partition. You can check it by entering:

sudo gparted 

in the terminal.

---

