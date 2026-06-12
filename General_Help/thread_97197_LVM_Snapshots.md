---
title: "LVM Snapshots"
date: 2005-11-30
forum: General Help
---

### Post by j-a-p on 2005-11-30
I am trying to create a LVM snaphot logical volume (LV), but am having problems.

I have made 2 Physical Volumes (PV), both of 50GB.

Each Physical Volume is assigned to a different Volume Group (VG).

The first VG (vg-system) consists of the folowing Logical Volumes (LV):
[LIST]
[*]lv-root (15GB ext3 mounted at /)
[*]    lv-home (30GB ext3 mounted at /home)
[/LIST]

The second VG (vg-backup) consists of the folowing Logical Volumes (LV):
[LIST]
[*]lv-root (15GB ext3 mounted at /backup/root)
[*]lv-home (30GB ext3 mounted at /backup/home)
[/LIST]

I have left space in each VG for the purpose of creating snapshots.

As you can see, I have made similar LV's in each VG.  The idea was to be able to use the LV's in the VG vg-backup to store the backups from VG vg-ystm LV's.  These backups would be on a physically seperate hard drive, and hopefuly erradicate problems if the main hard drive failed.

When attempting to create a Snapshot LV is issued the following command:

```
lvcreate -L500M -s -n lv-snapshot vg-system/lv-root
```

This is the output I get:

 ```
 snapshot: Required device-mapper target(s) not detected in your kernel
  lvcreate: Create a logical volume

```

I'm not sure I'm referring to the LV's correctly.  Here is output from the mount command:```


/dev/mapper/vg--system-lv--root on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-k7/volatile type tmpfs (rw,mode=0755)
/dev/mapper/vg--backup-lv--home on /backup/home type ext3 (rw)
/dev/mapper/vg--backup-lv--root on /backup/root type ext3 (rw)
/dev/hda1 on /boot type ext3 (rw)
/dev/mapper/vg--system-lv--home on /home type ext3 (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
/dev/hdc on /media/cdrom0 type iso9660 ro, noexec, nosuid, nodev,  user=jap) 
```

I'm curious as to how the double hyphens occurred in the LV names, i.e. ```
/dev/mapper/vg--backup-lv--home
```

Please help me out here people.  I have just satrted with Ubuntu Breezy and would like to backup before I proceed to wreck everything whilst playing about.

Thanks in advance.

JAP
[email]j-a-p@bluebottle.com[/email]

---

### Post by j-a-p on 2005-11-30
It seems I needed to modprobe dm_snapshot.  All I need to do now is load this module at boot.

I'm happy now. ;) 

Any feedback about Snapshot backups (especially on automating them) is gratefully received.

Cheers.

---

