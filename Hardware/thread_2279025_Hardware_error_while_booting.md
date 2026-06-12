---
title: "Hardware error while booting?"
date: 2015-05-20
forum: Hardware
---

### Post by cearlp on 2015-05-20
I'm running ubuntu 14.04 (with all updates) on an HP dv7 laptop. While booting i get a pause with the message
"error occurred while mounting /mnt/ata-HL-DT-ST_BDDVDRW_CT10L_K0591F63102".
If I select S for skip I get a further message about a UUID not ready yet or not present.
Then, usually if I wait long enough, it boots successfully. 
Does this indicate there is a hardware problem with the DVD disk drive? 
Any suggestions?

---

### Post by weatherman2 on 2015-05-20
What are the contents of the file /etc/fstab ?

---

### Post by cearlp on 2015-05-20
Here are the contents of fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=09c4f318-382e-4ee9-aafd-707f49ee2c36 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e414a4b2-133b-4e05-b96a-f03844c9fd3f none            swap    sw              0       0
# swap was on /dev/sda8 during installation
UUID=3ebc2e89-cf6a-49f6-9aa7-394657da1c3e none            swap    sw              0       0
/dev/disk/by-id/ata-HL-DT-ST_BDDVDRW_CT10L_K0591F63102 /mnt/ata-HL-DT-ST_BDDVDRW_CT10L_K0591F63102 auto nosuid,nodev,nofail,x-gvfs-show 0 0

---

### Post by weatherman2 on 2015-05-20
I'm not sure why your DVD drive is in your fstab file.  I'd remove it (the last line).  Or just comment it out - that is in front of that last "UUID=3ebc...." put a "#" in front, so you can always go back later and put it back if need be.

You need to edit the file with sudo.  You can always make a backup copy of the file first, before editing it, to make sure you don't mess something up:

```
sudo cp -p /etc/fstab /etc/copy.fstab
```

then edit:

```
sudo gedit /etc/fstab
```

and then comment out the last line or remove it.

Finally type this command to make sure the new fstab file is OK:

```
sudo mount -a
```

It should return nothing (just another command prompt) if everything is OK.  Otherwise, it will give you an error message.  Of course, reboot to see if the original error is gone.

Then try inserting a disc in the CD/DVD drive and make sure you can still mount/access it.

---

### Post by cearlp on 2015-05-21
Thanks weatherman2, that solved my problem.

---

### Post by tgalati4 on 2015-05-21
You can leave your DVD drive in /etc/fstab as long as you always keep a disk in it.  No disk means nothing to mount, so you will get an error on boot.

---

