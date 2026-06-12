---
title: "no block devices found after an upgrade from 8.10 to 9.04 on a soft RAID1 system"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by mansonthomas on 2009-04-09
Hi,

I've decided to upgrade to kubuntu 9.04(64bit)  from kubuntu 8.10(64bit)
on the following system :

P5N32-E Sli plus motherboard
C2D 6250
4GB of RAM
2x 250GB SATA, RAID1 software for linux (sdc, sdd)
2x150GB Raptor SATA Raid0 for windows (fake raid from motherboard)  (sda, sdb)


I run as told the "update-manager -d" command.

Nothing to report on the upgrade (just ask me what to do with the vim conf file). 
The system was running well before the upgrade (and as already been upgraded from 8.04 to 8.10)

On reboot I have this message:

no block devices found (4 times)
Gave up waiting for root device.
ALERT! /dev/md3 does not exist. dropping to a shell!

I've tryed to reboot with the fake raid for windows disabled (hard drives unplugged). no change.

on busybox (which I get after the errors):
in dmesg output I can see these kind of message:

sdd : sdd1 sdd2 <<6>attept to access beyond end of device
sda: rw=0 want=586067137, limit=293046768
Buffer I/O error on device sda1, logical block 293033536
(but these kind of message appears on gparted livecd)

in ls /dev, I can see the and sdcX sddX partitions are here.

I've no clue on how to bring my system back... 

any Idea ?

when I'm on busybox,
if I do mdadm --assemble --scan I get the md 0,1,2,3 of my system

So I tryed to chroot and reinstall grub : 

mkdir /mnt

mount -t ext3 /dev/md3 /mnt
mount -o bind /dev /mnt/dev
mount -t proc none /mnt/proc
mount -t sysfs none /mnt/sys
mount -t ext2 /dev/md0 /mnt/boot
mount -t ext3 /dev/md2 /mnt/var
chroot /mnt /bin/bash

grub
grub>root (hd0,0)
grub>setup (hd0)
grub>quit

with no luck...

I then tryed (after chroot) to 

/usr/sbin/grub-install -–recheck /dev/md3 –-root-directory=/

but it won't work (I guess the /dev/md3 is wrong... i've tryed some other thing like /dev/sda with no luck)

I really need some help... I've no other idea...

Thomas

---

### Post by ronparent on 2009-04-09
It looks like the upgrade din not restore the raid software. Do you know what software drivers were used under 8.10 (dmraid, mdadm, etc.)?

---

### Post by mansonthomas on 2009-04-09
mdadm --assemble --scan 

gives : 

mdadm: CREATE user root not found
mdadm: CREATE group disk not found

and then it output success in creating /dev/mdX devices...

Is the first two lines wrong ?

Thomas

---

### Post by mansonthomas on 2009-04-09
> **ronparent said:**
> It looks like the upgrade din not restore the raid software. Do you know what software drivers were used under 8.10 (dmraid, mdadm, etc.)?

I don't know.

I've documented my installation, and I just use the kubuntu alternate CD to setup raid... but i don't have any clue of what drivers it uses.

As I can chroot to my system, is there a way I can guess which one has been used?

Thomas

---

### Post by ronparent on 2009-04-09
The answer lies in what gparted now tells you (finds the raid array) and whether or not you can reboot?

---

### Post by mansonthomas on 2009-04-09
Note that I might have been using both...

because I use dmraid to mount my RAID0 windows partition which is on fakeraid.

But as far as I remember, I don't think the raid0 partition of windows was automatically mounted at system startup.

---

### Post by mansonthomas on 2009-04-09
I'm not familiar with gparted.

Can you tell me where to check that information ? 

I can see "flag: RAID" but nothing related to dmraid or mdadm...

---

### Post by ronparent on 2009-04-09
In my case they weren't automatically mounted. I ultimately had to use dmraid to find them and then reference them in fstab to make them mountable. I don't know if that was the best/approved approach but it works for me until I find better.

---

### Post by mansonthomas on 2009-04-09
So I should chroot again and check my fstab ?

>I ultimately had to use dmraid to find them and then reference them in fstab to make them mountable

Can you tell me more about that?

Thomas

---

### Post by mansonthomas on 2009-04-09
when I check 

sudo mdadm --query --detail /dev/md0

and compare the UUID to the one in /etc/fstab 

I find it different ! (also it's not written the same way, : separated in mdadm output, - separated in /etc/fstab)

but what trouble me, how can it read the fstab if the /dev/md3 is not able to be mounted ?


my grub conf file looks like : 

```
title Ubuntu 8.10, kernel 2.6.27-7-generic
root (hd0,0)
kernel /vmlinuz-2.6.27-7-generic root=/dev/md3 ro quiet splash
initrd /initrd.img-2.6.27-7-generic
quiet
```

the /etc/fstab : 

```
thomas@daisybox:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#<file system>                                  <mount point>                   <type>                                  <options>                                                                       <dump> <pass>
proc                                            /proc                           proc                                    defaults                                                                        0       0
# /dev/md3
UUID=85c16b12-9086-4973-a9ba-deb694609a3f       /                               ext3                                    relatime,errors=remount-ro                                                      0       1
# /dev/md0
UUID=483d5bb4-bde0-4291-b94f-7601528cef5f       /boot                           ext2                                    relatime                                                                        0       2
# /dev/md2
UUID=3529ccb3-a750-4923-8129-a8bb8bbf3125       /var                            ext3                                    relatime                                                                        0       2
# /dev/md1
UUID=082e0be7-f9c7-4dfe-80ec-be8892c03aa1       none                            swap                                    sw                                                                              0       0
/dev/scd0                                       /media/cdrom0                   udf,iso9660 user,noauto,exec,utf8                                                                                       0       0
```

the mdadm output gives:

UUID : 9793c91d:32043d57:8bcf0b22:7b92e5c9

not the same format... strange

But in /etc/mdadm.conf I found the same id than the mdadm --query output...

---

### Post by ronparent on 2009-04-09
A typical instruction I added to fstab:

#/dev/sdb  nvidia_aebhdfib10  i:\FILES
/dev/mapper/nvidia_aebhdfib10	/media/WinXP-i:FILES	auto	relatime	0	1

I had to manually create the trget (/media/WinXP-i:FILES).
If you used a simular prior arrangement, the fstab and file structure are probably still intact and will appear with a reboot? This hold true also for files which appear in /dev/mapper/ which are actually symbolic links to the mapped drives as created by dmraid.

---

### Post by mansonthomas on 2009-04-09
Yes...

I've succeeded in booting my system like before the upgrade (with kde...) .

On busybox console,

I typed : 

mdadm -As (--assemble --scan)

so that it create /dev/mdX devices.

then type exit and it resume the boot process, which succeed as the raid device are up.


but this won't fix the problem, but at least I've my system back...

---

### Post by mansonthomas on 2009-04-09
I use the /dev/mapper/nvidia*

when I try to mount my windows raid0 partition on fake raid (that use dmraid). 

The ubuntu disks are using soft RAID1 so I think my fstab (that uses ID is in good shape,maybe the wrong id so)



> **ronparent said:**
> A typical instruction I added to fstab:

#/dev/sdb  nvidia_aebhdfib10  i:\FILES
/dev/mapper/nvidia_aebhdfib10	/media/WinXP-i:FILES	auto	relatime	0	1

I had to manually create the trget (/media/WinXP-i:FILES).
If you used a simular prior arrangement, the fstab and file structure are probably still intact and will appear with a reboot? This hold true also for files which appear in /dev/mapper/ which are actually symbolic links to the mapped drives as created by dmraid.

---

