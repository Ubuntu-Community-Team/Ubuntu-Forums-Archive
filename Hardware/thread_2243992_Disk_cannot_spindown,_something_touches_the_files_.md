---
title: "Disk cannot spindown, something touches the files every now and then"
date: 2014-09-12
forum: Hardware
---

### Post by pellefantus on 2014-09-12
I have an 14.04LTS box that has an usb-disk mounted, and using [spindown]("https://code.google.com/p/spindown/") was problem free. as per the recommended value the disk spins down after 3600 seconds, and I use it once every week for a backup job.

But something keeps the disk awake by doing "something" to it. It is a normal ext4 disk mounted and used only for the git-annex program once per week and still it cannot be kept in a spun down mode, these are the spindown logs:

```

Sep 12 10:04:34 pc-1 spindown: sdd is now active.
Sep 12 14:03:40 pc-1 spindown: sdd is now active.
Sep 12 17:23:03 pc-1 spindown: sdd is now active.
Sep 12 18:25:01 pc-1 spindown: sdd is now active.
Sep 12 19:26:07 pc-1 spindown: sdd is now active.

```

as you can see it now and then spins up the disk, could someone explain what might be doing this? If not, then I am forced to umount the disk when not using it, which is a bit too much...

---

### Post by ThatBum on 2014-09-12
Try [FONT=courier new]iotop[/FONT], perhaps.

---

