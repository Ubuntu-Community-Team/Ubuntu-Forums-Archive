---
title: "Breezy install ends up with IDE device mismatch"
date: 2006-01-03
forum: Installation &amp; Upgrades
---

### Post by benco on 2006-01-03
Hi.
It is my first post in this forum and I am sorry it is so long but I want to be as clear as possible.
I have spent the last three days trying to install [K]ubuntu (Breezy) but it just ends up with a non working install.
First, here is my configuration :
On the motherboard, I have 2 disks on the first IDE channel, the master disk has a WinXP on it and the slave disk is just data.
I have a CD Writer and a DVD drive on the second IDE channel.
I have a PCI IDE card with a data disk attached.
Here is the naming of the devices :
MOBO-IDE-1 :
[INDENT]master disk = hde (60 GB)[/INDENT]
[INDENT]slave disk = hdf (120 GB)[/INDENT]
MOBO-IDE-2 :
[INDENT]master CD = hdg[/INDENT]
[INDENT]slave DVD = hdh[/INDENT]
PCI-IDE-1 :
[INDENT]master disk = hda (300 GB)[/INDENT]
I tried to install [K]ubuntu on hde (just an ext3 / filesystem on /dev/hde5 and a swap on /dev/hde6) and the installation went just fine. The GRUB installer recognized my WinXP partition and offered to install itself on the MBR of hde, which I accepted.
After that, on the first reboot, my PC restarted on WinXP. The GRUB menu did not appear.
I rebooted on a Live CD, and forced an installation of GRUB on /dev/hde
> 
# mount -t ext3 -o rw /dev/hde5 /mnt
# chroot /mnt
# grub-install /dev/hde

On the next reboot, the GRUB menu appeared with the classical Ubuntu, failsafe, memtest and WinXP options.

**Question 1** : why did I have to install manually GRUB while the GRUB confg files (device.map and menu.lst) were correctly created during installation ?

When I selected Ubuntu, I got an "Error 22: No such partition"
When I tried Windows, I got a "filesystem unknown, partition type 0x7"
After investigation, I realized that GRUB, or whatever it is at this stage of the process, had an incorrect vision of my devices.
To make things clear :
my /boot/grub/device.map is 
> 
(hd0) /dev/hda           # my 300 GB disk on the PCI IDE 
(hd1) /dev/hde           # my 60 GB disk
(hd2) /dev/hdf           # my 120 GB disk

and my /boot/grub/menu.lst is something like :
> 
title Ubuntu 2.6.12-9-386
root (hd1,4)
kernel /boot/vmlinuz-2.6.12-9-396 root=/dev/hde5 ro quiet splash
initrd /boot/initrd.img-2.6.12-9-386
...
title Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1


If I modify the menu.lst to show :
> 
title Ubuntu 2.6.12-9-386
root (hd0,4)
kernel /boot/vmlinuz-2.6.12-9-396 root=/dev/hde5 ro quiet splash
initrd /boot/initrd.img-2.6.12-9-386
...
title Windows XP
root (hd0,0)
#map (hd0) (hd1)
#map (hd1) (hd0)
savedefault
makeactive
chainloader +1

I can boot my Windows XP normally (well, like an XP ;-)), log in, log out, reboot and back to GRUB. OK. Fine for windows.

**Question 2** : I read somewhere that the 'map (hdxx) (hdyy)' lines were necessary to boot on a secondary disk. It is not the case. The disk I want Windows to boot is the primary disk. So why did the GRUB installer generate these lines ?

If I select Ubuntu, the boot process starts, I have the splash screen, then :
> 
Loading modules     [ok]
Initializing dev    [ok]
Mounting root file system    [failed]

And it goes back to a text screen, showing :
> 
....
Uncompressing linux ... OK, booting the kernel
Loading, please wait
No volume groups found
/script/local-top/evms: 31: /sbin/evms_activate not found
ALERT! /dev/hde5 does not exist. Dropping to a shell


**Question 3 **: what is this evms stuff ? I believe it has something to do with Logical Volumes but I don't have logical volumes (but my IDE card has RAID capabilities - that I don't use)

After that, I have the Busybox prompt and if I do :
> 
# ls /dev/hd*

I have :
> 
hde1 hde hdd hdc hdb1 hdb hda6 hda5 hda2 hda1 hda


**Question 4 **: why don't the IDE devices match what the Ubuntu installer detected (my boot disk with different partitions is hde, not hda !)

**Question 5** : I tried to install a pure Debian (Sarge 3.1) and ran into the same problem, while a Mandriva 2006 or an OpenSuse 10.0 worked perfectly well.

I have Ubuntu installed at work (just 1 disk) and it works fine. I would like to have it at home, too, but I can't make it work !!

Can anybody help, please ?

Thanks in advance (thank you if you read all this in the first place ;-))
Feel free to ask any information if something is unclear.

Benco.

---

