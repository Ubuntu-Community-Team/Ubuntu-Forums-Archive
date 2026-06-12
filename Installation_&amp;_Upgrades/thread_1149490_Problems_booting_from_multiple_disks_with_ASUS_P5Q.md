---
title: "Problems booting from multiple disks with ASUS P5Q Deluxe Motherboard"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by quissicks on 2009-05-05
I have an ASUS P5Q Delux motherboard, with two Samsung 1TB disks set up as RAID 0 (fakeraid) and a Hitachi 1TB disk set up as a SATA drive. 

My machine has Vista (64 bit) installed on the RAID. However, when I installed Ubuntu on the SATA drive I became unable to boot to window. The file browser in Ubuntu sees both the RAID and the Hitachi disk. Thankfully, I have been able to back up all my (Vista) files on the RAID onto a USB drive through Ubuntu. I am wanting to get the machine to dual boot into either Ubunto 9.04 (on the Hitachi drive) or Vista x64 on the RAID.

I can't get Grub to work. When I boot there is no grub menu - it just takes me straight into Ubuntu. If I do a df -k I get:

root@MMME1:/# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc1            949921868   2337256 899331380   1% /
tmpfs                  1996572         0   1996572   0% /lib/init/rw
varrun                 1996572       112   1996460   1% /var/run
varlock                1996572         0   1996572   0% /var/lock
udev                   1996572       172   1996400   1% /dev
tmpfs                  1996572        76   1996496   1% /dev/shm
lrm                    1996572      2760   1993812   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda1            499896300 246161812 253734488  50% /media/Vista64

However, the file /boot/grub/device.map contains:
(hd0)    /dev/sda

Grub doesn't seem to recognise sda, sdc, sda1 or sdc1.

If I do the command  sudo grub device-map=test.map I get:
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

but it does not produce a test.map file. 

If I try to get grub to list out its drives using the tab function it doesn't work either:
grub> root (hd        
root (hd

Error 21: Selected disk does not exist

I have tried to install super grub by both USB pendrive and also a DVD, but neither will boot (I have changed the bios to make the USB/DVD bootable).

I would be grateful if anybody could help me - thanks.

Chris.

---

### Post by quissicks on 2009-05-05
My motherboard is an ASUS P5Q3 Deluxe WiFI-AP. I put the wrong model in my previous post.

---

