---
title: "can't log into windows after installing ubuntu"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by klarki on 2009-11-04
Hello

I installed ubuntu 9.10 and now I can't log back into windows xp, that was installed before.

There was one strange thing during the install - the partition that I installed ubuntu on was listed as the partition with windows xp system by the ubuntu installer(even though it wasn't - there were just some normal files there, certainly not the "windows" dir)

After installing ubuntu there were no entries for windows in grub, so I added my own:

```
#! /bin/sh -e
echo "Adding Windows" >&2
cat << EOF
menuentry "Windows XP" {
set root=(hd0,3)
chainloader +1
}
EOF

```

this is my fdisk -l /dev/sda (windows is on sda3)

```

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa629a629

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406   83  Linux
/dev/sda2            1276       22241   168409395    f  W95 Ext'd (LBA)
/dev/sda3           22242       24791    20482875    7  HPFS/NTFS
/dev/sda5            1276        6374    40957686    7  HPFS/NTFS
/dev/sda6            6375       14660    66557263+   7  HPFS/NTFS
/dev/sda7           14661       22241    60894351    7  HPFS/NTFS

```

Now windows appears in grub all right, but after booting into windows I just get the message "NTLDR is missing, press alt+ctrl+del to restart"


it seems NTLDR has something to do with booting in windows, and it can be fixed by using fixboot executable, but now I'm worried that after "repairing" in this way, I'll loose my ubuntu. Ideally I'd want to repair windows while not breaking ubuntu.

Could anyone help me?

---

### Post by jjcv on 2009-11-04
This is not probably ver helpful but I have come across this some years ago and there was a command I had to run to be able to boot windows properly again.

Probably something with chkdisk.

It may be worth doing a wider goggle on this and see what comes up.

---

### Post by klarki on 2009-11-05
Ok I know what happened and it's not Ubuntu fault at all - it's my own stupidity

I somehow had the ntldr file, which is windows equivalent of grub so to speak, on the partition I installed Ubuntu on. Windows couldn't boot without it. I had to copy it from the windows install cd and create a new boot.ini file, since the old one was lost in the same way.

Now windows is booting normally and update-grub even started to detect windows on its own (on top of my manual menu entry)

---

