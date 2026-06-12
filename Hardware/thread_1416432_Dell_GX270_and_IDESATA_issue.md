---
title: "Dell GX270 and IDE/SATA issue"
date: 2010-02-26
forum: Hardware
---

### Post by derryt on 2010-02-26
Hi all,
 
I just got an old GX270 running BIOS A07 from my work, installed Karmic on it and it works perfectly, compiz running smoothly and everything so that made me very happy!
 
The problem is I need to use my old IDE drive running windows as there are some programs I can't do without but when I connect it via the IDE cable (it has both SATA and IDE connections, Karmic is on the SATA) it is nowhere to be seen in the BIOS so I can't boot from it.
 
I tried changing the jumper on the IDE drive but still had no joy.
 
Has anyone else encountered this problem or any ideas how I can fix it?
 
ps. I'm currently at work so probably wont get the chance to try any solutions till much later tonight!
 
Thanks in advance, 
 
Derry

---

### Post by jombo_777 on 2011-06-09
yes i have the same isue!!!  (i have ubuntu 10.10)  and a ide + sata combo and in linux my windows drive will not mount  (says error already mounted) in disk manager
 
can some one help?

---

### Post by tgalati4 on 2011-06-09
Check for a switch in the BIOS.  You might have to activate both IDE and SATA.  Also, check for an upgrade to your BIOS.  The IDE module won't get loaded if the BIOS doesn't reveal it.

dmesg | tail

You should see something similar to (from hardy server):


[   69.545912] hub 1-0:1.0: 2 ports detected
[   69.979841] libata version 3.00 loaded.
[   70.284699] ata_piix 0000:00:07.1: version 2.12
[   70.295532] scsi0 : ata_piix
[   70.302922] scsi1 : ata_piix
[   70.303374] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   70.303420] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   70.472641] ata1.00: ATA-3: FUJITSU MPA3035AT, 9147, max MWDMA2
[   70.472689] ata1.00: 6835952 sectors, multi 32: LBA 

libata and ata_piix are required and can be seen in:

lsmod


ata_piix               19588  2 
pata_acpi               8320  0 
ata_generic             8324  0 
libata                159600  3 ata_piix,pata_acpi,ata_generic

If the modules are missing, you can force them by putting them in /etc/modules.

If the modules are loaded then check the mounting tables:

Post the output of:

cat /etc/fstab

cat /etc/mtab

---

### Post by jombo_777 on 2011-06-09
i did not find any switch in bios ans bios is updated to a07 (a07 is most recent)

i have actualy 4 hard drive on my dell gx270

1- 40Gb hd with ubunutu on the first sata port
2- 320Gb hd with mp3 on the second sata port
3- 40 Gb with windows xp on the 1st ide port as master
4- 30gb with windows 7 on the  ide port as slave

this is what you wanded me to post:

jonathan@jonathan-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3e954a7a-50fb-4d51-989f-2b5a59bfa9f6 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
jonathan@jonathan-desktop:~$ cat /etc/mtab
/dev/sdc1 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/jonathan/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=jonathan 0 0
/dev/sdd3 /media/jonathan fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
/dev/sdb1 /media/30win7 fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0

---

### Post by tgalati4 on 2011-06-10
I forgot to include:

sudo fdisk -l

fstab:  file system table is what is supposed to be mounted at boot
mtab:  What is currently mounted
fdisk  What devices (mounted or not) are known to the system

So your fstab shows that 5 things are supposed to be mounted at boot:

proc:  This is what the kernel interacts with.
/dev/sda1: Presumably your Ubuntu boot disk (first partition on first SATA)
swap disk:  This is handy to have
/dev/fd0:  Floppy disk, so this is an older machine

Your mtab show:

sdc1 (ext4) perhaps your music drive?
fuse  File system User Space--allows the user to mount several different types of file systems into their own user space.

sdd3 named "jonathan" perhaps your WinXP disk
sdb1 named "30win7" perhaps your 30 GB Win7 disk

When you open nautilus and go into /media what do you see?
If you click on 30win7 does it open your Windows7 disk?

If you are getting errors in this situation, then it's time to file a bug against 10.10 related to mixed SATA/PATA drives and FUSE.

Reference this thread.

---

### Post by jombo_777 on 2011-06-11
actualy this is how my system are: (and how /media shows to)

sdc1 is the the 1st sata disk with ubuntu 10.10

sda1 is the win xp disk on ide master

sdd 1 2 and 3 are the 320 Gb hard drive for storage and winxp swap files respectly sdd1:swap sdd2:temp and sdd3 : called jonathan for my mp3

and finaly you gest this one right sdb1 :win7

so what i understand is that ubuntu put ide drive in front of the list but my bios sets them the other way around ( sata befor ide) 

secondly i managed to mount in terminal sda1 using :

gksudo mount /dev/sda1 /home/jonathan/winxphdd

i would rather like it to mount it self automaticaly and/or show it self like the others in the shortcut menu...  at best i managed to make a script on my mouse right clic menu :P

thirdly : i presume that the same reason respopnsable for it not shownig in the menu is why the disk manager (in system/admin menu) showed this error message when trying to mount:

Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdc1 is already mounted on /
mount failed

---

### Post by tgalati4 on 2011-06-12
If you want it to mount at every boot, you can either put it in /etc/fstab (with the correct parameters--you will have to research) or you can put a mount command in /etc/rc.local

cat /etc/fstab
cat /etc/rc.local
sudo nano /etc/rc.local

You would put the mount command before the "exit 0" statement.  Exit 0 means exit this script with "0" error status.

---

