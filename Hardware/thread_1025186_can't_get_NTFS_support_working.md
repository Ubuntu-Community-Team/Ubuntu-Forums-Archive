---
title: "can't get NTFS support working"
date: 2008-12-29
forum: Hardware
---

### Post by cowboys2010 on 2008-12-29
Heres what I'm trying to do.

I have a desktop that has Ubuntu 8.04 on it. I have a 750GB External Drive hooked up to it. Its formatted NTFS by default. I plugged it in hoping Ubuntu would find automatically. I knew that linux did not support NTFS, so I downloaded the ntfs-3g drivers. It told me check to make sure I have the basic developmental tools. I guess I don't because when I ran the first command to install it gave me errors about the C compiler not able to create executable. I checked the log file, but couldn't understand anything in there. After I get it to work, what I want to do is share the drive out to a bunch of laptops to back up their data to it. 
Help, thanks.

---

### Post by taurus on 2008-12-29
Are you trying to build ntfs-3g from source?  It should be in the repos.  Which release are you running anway?

If the external drive does not automount when you plug it in, open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

p.s.  If you ever use that external harddrive in windows, _do not_ just unplug it when you are done.  Instead, use the Safely Remove Hardware icon (bottom right corner) to unmount it first before you unplug it.

---

### Post by conqeror on 2008-12-30
Did you close last session on Windows properly???

---

### Post by cowboys2010 on 2008-12-30
umm...no. I just pulled the plug.

The outputs of the commands were:

fdisk -l:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf9c1f9c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29930   240412693+  83  Linux
/dev/sda2           29931       30401     3783307+   5  Extended
/dev/sda5           29931       30401     3783276   82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x208366cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       91201   732572001    7  HPFS/NTFS



df -h:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             228G  2.2G  214G   1% /
varrun                632M  100K  632M   1% /var/run
varlock               632M     0  632M   0% /var/lock
udev                  632M   52K  632M   1% /dev
devshm                632M   12K  632M   1% /dev/shm
lrm                   632M   38M  595M   6% /lib/modules/2.6.24-19-generic/volatile



If unplugging the drive improperly in Windows did something to it, is there a way to fix it.

---

### Post by taurus on 2008-12-30
See if you can mount it with

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```
it's best to plug it back to a windows machine and use the safely remove hardware option to unmount it.  Then, unplug it.

---

### Post by cowboys2010 on 2008-12-30
thanks guys. I plugged it in to my Vista machine, removed it properly, plugged into ubuntu and it found it and mounted it automatically. I guess I should start using that Safely Remove Hardware feature.

---

### Post by 2hot6ft2 on 2008-12-30
> **cowboys2010 said:**
> thanks guys. I plugged it in to my Vista machine, removed it properly, plugged into ubuntu and it found it and mounted it automatically. I guess I should start using that Safely Remove Hardware feature.
Don't forget to use the unmount feature in ubuntu either. Right click on the drive and select unmount, give it a moment before removing it. It should warn you if it's still in use with a pop up.

---

