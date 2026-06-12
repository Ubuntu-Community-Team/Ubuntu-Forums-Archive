---
title: "Toshiba external hard drive invisible to Ubuntu"
date: 2008-03-31
forum: Hardware &amp; Laptops
---

### Post by SEMW on 2008-03-31
I have a Toshiba external USB hard drive (300GB).  It works fine in Windows.  But it seems to be almost invisible to Ubuntu.  As in, the only thing that happens when you plug it in is that the following entry appears in /var/log/messages:
```
usb 4-4: new high speed USB device using ehci_hcd and address 4
```
...And that's it.  Nothing about whereabouts, if anywhere, in /dev it should be.

And, indeed, it doesn't seem to be anywhere in /dev!  Running ```
ls -1 | wc -l
``` in /dev reports the same thing whether the drive's connected or not.

[LIST]
[*]There's no sign of it in Computer.
[/LIST]
[LIST]
[*]There's no sign of it in gparted.
[/LIST]
[LIST]
[*]There's no sign of it in /etc/mtab:
```
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-12-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
/dev/hdc /media/cdrom0 iso9660 ro,nosuid,nodev,user=simon 0 0
/dev/sda1 /mnt/data fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
```
(The last line's not it: sda1 is a 500GB SATA internal hard drive).
[/LIST]
[LIST]
[*]There's no sign of it from a sudo fdisk -l:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
[details removed]
Disk /dev/hda: 40.0 GB, 40000020480 bytes
[details removed]
Disk /dev/hdb: 122.9 GB, 122942324736 bytes
[details removed]

```
My three internal hard drives.
[/LIST]

I should note that I'm running the Hardy beta (because xrandr in Xorg 7.3 has been the only way I have been able to get dual screens running and still retain my sanity).

Any ideas?

Thanks!

---

### Post by dannyboy79 on 2008-03-31
does dmesg show anything? and you're positive that the drive works correct? it's spinning and on when you plug in the usb cable? does that usb port work? even if it wasn't formatted, it should show up when issueing 
sudo fdisk -l

this is very weird behavior

---

### Post by SEMW on 2008-03-31
> **dannyboy79 said:**
> does dmesg show anything?
dmesg shows the same thing that /var/log/messages shows -- "usb 4-4: new high speed USB device using ehci_hcd and address 4" -- only with a less human-readable timestamp.

> **dannyboy79 said:**
> and you're positive that the drive works correct? it's spinning and on when you plug in the usb cable? does that usb port work? even if it wasn't formatted, it should show up when issueing 
sudo fdisk -l
Respectively: Yes, it works fine when connected to a Windows box; it's definitely spinning up correctly; and I've tried it in several different USB ports (the only difference is that the entry in /var/log/messages becomes "usb 6-2..." (say) rather than 4-4).

Thanks,
Simon

---

