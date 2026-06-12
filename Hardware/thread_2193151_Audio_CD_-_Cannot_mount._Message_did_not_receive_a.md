---
title: "Audio CD - Cannot mount. Message did not receive a reply (timeout by message bus)"
date: 2013-12-11
forum: Hardware
---

### Post by psychok92 on 2013-12-11
Hi,
Ubuntu/gnome cannot mount audio cd on a Sony Laptop, SVE1712Z1EB, I get the message "cannot mount audio cd - Message did not receive a reply (timeout by message bus)".

```
dmesg | grep CD-ROM
[    1.531446] scsi 4:0:0:0: CD-ROM            PIONEER  BD-RW   BDR-TD04 1.01 PQ: 0 ANSI: 5
[    1.548082] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.548266] sr 4:0:0:0: Attached scsi CD-ROM sr0
```

```
wodim --devices
wodim: No such file or directory.  Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'. For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from the wodim documentation.

```

```
ls -lah /dev/cd*
lrwxrwxrwx 1 root root 3 dic 11 18:31 /dev/cdrom -> sr0
```

I can open it with VLC only, open disc -> audio cd /dev/cdrom.
**I need to open completely**, using Exaile. Any solutions?

---

