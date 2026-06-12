---
title: "Upgrade from ext3 to ext4"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by hesjnet on 2009-04-18
Is it possible to upgrade from ext3 to ext4 without formating the partition first?

---

### Post by Partyboi2 on 2009-04-18
You can convert to ext4 from ext3 without formatting and loosing data.

---

### Post by hesjnet on 2009-04-18
Is this choice availiable in the jaunty install?

---

### Post by dksite on 2009-04-18
> **Partyboi2 said:**
> You can convert to ext4 from ext3 without formatting and loosing data.

Are you sure? Someone in IRC told me you need to do a clean install to get ext4 w/o losing any data.

---

### Post by Partyboi2 on 2009-04-18
> **dksite said:**
> Are you sure? Someone in IRC told me you need to do a clean install to get ext4 w/o losing any data.
I converted my ext3 to ext4 without loosing any data.

@hesjnet
You have to convert it manually, Jaunty does not come automatically with it.

---

### Post by CheesyD on 2009-04-18
> **Partyboi2 said:**
> I converted my ext3 to ext4 without loosing any data.

May I ask how you accomplished this?

---

### Post by 54y89 on 2009-04-18
> **hesjnet said:**
> Is it possible to upgrade from ext3 to ext4 without formating the partition first?

Yes this is possible but from what i hear and have expirinced on virtual machenes is that ext4 causes grub to become unstable

---

### Post by Partyboi2 on 2009-04-18
> **CheesyD said:**
> May I ask how you accomplished this?This is what I did running Jaunty.
**First backup your important stuff** then boot the ubuntu live cd and open a terminal and covert with
```
sudo tune2fs -O extents,uninit_bg,dir_index /dev/XXX
```*change the /dev/XXX to actual partition number (sudo fdisk -l to find correct one)
then run a filesystem check
```
sudo fsck -pf /dev/XXX 
```*change /dev/XXX to the correct one.
Then you would need to edit your fstab file[FONT=monospace]
[/FONT]```
sudo mount -t ext4 /dev/XXX /mnt
``` *change /dev/XXX to the correct one. 
```
gksu gedit /mnt/etc/fstab
```and change ext3 to ext 4 for the partition that you converted as you can see i converted my / and /home
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=ff13903a-c958-47a0-8292-f482063226ee /               [COLOR=Red]ext4[/COLOR]    relatime,errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=7093b79b-0c36-4fdf-a144-effefceb618d /home           [COLOR=Red]ext4[/COLOR]    relatime        0       2
# none was on /dev/sda6 during installation
UUID=e1a99e2a-a6d2-495d-8101-c230672981b2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```Once changes are made save then reboot.

Edit: I did not need to do a grub-install to reinstall the boot loader but according to [[COLOR=Blue]this[/COLOR]]("https://wiki.ubuntu.com/JauntyJackalope/ReleaseNotes#Switching%20to%20ext4%20requires%20manually%20updating%20grub") you need to.

---

### Post by inobe on 2009-04-18
thanks for the information Partyboi2

---

### Post by Ericyzfr1 on 2009-04-19
I would back-up any important files,  but I have not heard of loss data while upgrading to ext4.

---

