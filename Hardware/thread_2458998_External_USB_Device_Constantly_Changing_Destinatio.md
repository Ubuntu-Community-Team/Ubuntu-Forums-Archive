---
title: "External USB Device Constantly Changing Destination After Reboot"
date: 2021-03-08
forum: Hardware
---

### Post by nietzogoed on 2021-03-08
So I have six disks internally, /dev/sda is my SSD for boot, /dev/sdb and /dev/sdc are in a zpool, and /dev/sdd, /dev/sde, and dev/sdf are in another zpool.  Those are all fine and dandy.

I plugged in a large external for backups. It mounted the first time to /dev/sdg and I used that to point when setting up Deja Dup to do my backups. All good until I apply updates and a reboot is needed. The external USB will show up at /dev/sdc or somewhere else.

What can I do to remedy this? I'm not the smartest at this but with a lot of trial and error in virtual machines, I've got pretty much everything I want configured the way I need for my use case. The only thing I can't figure out is this. I have to unplug the device, reboot, wait, then plug back in and it automounts to /dev/sdg and Deja Dup stops complaining.

I appreciate the help!

---

### Post by CatKiller on 2021-03-08
Those device identifiers aren't remotely permanent; they're just the order that they got round to notifying that they exist. Use UUIDs instead.

---

### Post by ajgreeny on 2021-03-08
As CatKiller says you are doing things wrongly as the device names are not static.

I'm not sure how deja-dup works as I have never used it but if you either use its UUID which you can find with command ```
sudo blkid
``` or give the partition on your external hard drive a label it will automatically mount to ***/media/<username>/label*** and it will not matter if the ***/dev/sdx*** nomenclature changes as that is not the way it will now work.

As this is an external drive I suggest the label is the better way to go with this; if it is mounted with an entry in /etc/fstab then the UUID is probably better but both will work better than /dev/sdx.

See ```
Indicating the device and filesystem
       Most  devices  are  indicated by a filename (of a block special device), like /dev/sda1, but there are other possibili&#8208;
       ties.  For example, in the case of an NFS mount, device may look like knuth.cwi.nl:/dir.  It is also possible to  indi&#8208;
       cate  a block special device using its filesystem label or UUID (see the -L and -U options below), or its partition la&#8208;
       bel or UUID.  Partition identifiers are supported for example for GUID Partition Tables (GPT).
```
which is from man mount.

Format the external disk partition as ext4 if it's not already ext4 to ensure permissions are retained for the backup files, label it as something meaningful to you, and all should then be good to go once you edit your current deja-dup destination configuration.

---

### Post by nietzogoed on 2021-03-09
Thank you. I swear I tried that but for some reason it didn't work and thought maybe I stumbled upon some outdated info. Worked this time with no issues.

---

### Post by ajgreeny on 2021-03-09
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

