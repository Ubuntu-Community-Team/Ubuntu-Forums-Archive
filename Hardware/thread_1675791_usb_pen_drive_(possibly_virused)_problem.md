---
title: "usb pen drive (possibly virused) problem"
date: 2011-01-26
forum: Hardware
---

### Post by I'mGeorge on 2011-01-26
a few days ago I've used my flash drive on a virused computer and now either windows or linux doesn't recognize it. If I try in windows it assigns a drive letter for my pen drive but it's seen as an empty CD-ROM drive with the exception it's called a removable disk and has assigned the proper removable disk icon.

So I can't format it or access it because it says it's empty, just like you were trying to access a CD-ROM unit with no disk in it I've already tried the command lines and graphical options in windows to format it or running a check disk on it (chkdsk) thinking that the file system might be damaged, so a check disk might had helped fixing that but with no luck, it's seen as empty so there's nothing to format or scan.

Well I thought if windows can't do it than linux might. But the thing is that in linux it's not even recognized by the OS so it hasn't assigned any sda or sdb partition that I could mount or work with it, though if I do lsusb I get the following output regarding the flash drive
```
Bus 001 Device 004: ID 1307:0163 Transcend Information, Inc. 256MB/512MB/1GB Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

My flash drive it's a 8Gb Corsair voyager.

I'm pretty much out of ideas. Thanks with anticipation for any suggestion at all.

---

### Post by theozzlives on 2011-01-26
That sounds like what happened to me when my 8 GB SanDisk Cruser went bad. You can only write to a Flash Drive so many times. Does your light come on? If not you may need a new one.

EDIT: Also, have you tried Windows Disk Manager to redo it? (control panel > administrative tasks > computer management > disk manager)

---

### Post by I'mGeorge on 2011-01-26
> **theozzlives said:**
> That sounds like what happened to me when my 8 GB SanDisk Cruser went bad. You can only write to a Flash Drive so many times. Does your light come on? If not you may need a new one.

EDIT: Also, have you tried Windows Disk Manager to redo it? (control panel > administrative tasks > computer management > disk manager)

Yup but even disk manager sees it as an empty CD-ROM drive so I can't do much about it.

---

