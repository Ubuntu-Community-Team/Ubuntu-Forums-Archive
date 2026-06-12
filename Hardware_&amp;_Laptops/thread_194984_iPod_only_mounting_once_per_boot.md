---
title: "iPod only mounting once per boot"
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by REBELinBLUE on 2006-06-12
I have a problem with my iPod.

If I boot with it in the dock, it never mounts however if I place it in the dock after I get to the desktop it does mount.

After that though, if I unmount it and then reconnect it it does not mount again until I next reboot.

It is however being detected, as shown by dmesg
> [4295171.879000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[4295171.879000] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[000a270002dc91ac]
[4295182.823000] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[000a270002dc91ac]
[4295182.823000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[4295182.823000] scsi3 : SCSI emulation for IEEE-1394 SBP-2 Devices
[4295183.926000] ieee1394: sbp2: Logged into SBP-2 device
[4295183.926000] ieee1394: Node 0-00:1023: Max speed [S400] - Max payload [2048][4295183.930000]   Vendor: Apple     Model: iPod              Rev: 1.62
[4295183.930000]   Type:   Direct-Access-RBC                  ANSI SCSI revision: 00
[4295183.941000] sdb: Spinning up disk.......ready
[4295187.983000] SCSI device sdb: 39063024 512-byte hdwr sectors (20000 MB)
[4295187.985000] sdb: Write Protect is off
[4295187.985000] sdb: Mode Sense: 00 08 00 00
[4295187.988000] SCSI device sdb: drive cache: write through
[4295187.994000] SCSI device sdb: 39063024 512-byte hdwr sectors (20000 MB)
[4295187.996000] sdb: Write Protect is off
[4295187.996000] sdb: Mode Sense: 00 08 00 00
[4295187.999000] SCSI device sdb: drive cache: write through
[4295187.999000]  sdb: sdb1 sdb2
[4295188.046000] sd 3:0:0:0: Attached scsi removable disk sdb
[4295188.047000] sd 3:0:0:0: Attached scsi generic sg1 type 14

If I go into disks-admin I can mount it from there, but that is a PITA.

Any idea how I can fix this so that it auto mounts?

---

### Post by megamania on 2006-06-12
[QUOTE=REBELinBLUE]If I go into disks-admin I can mount it from there, but that is a PITA.

Any idea how I can fix this so that it auto mounts?[/QUOTE]
I don't have an iPod anymore, but I remember that unmounting it with

```

sudo eject ipod
```

allowed me to have it re-mounted with no problems. I just hope that helps.

---

### Post by REBELinBLUE on 2006-06-13
Thanks, sadly that doesn't appear to make much difference :(

---

### Post by denisesballs on 2006-06-14
I've noticed this too. Drives me nuts.

---

### Post by denisesballs on 2006-06-14
Ok, after playing around a little, I found a workaround. If your iPod isn't mounting, do a dmesg and see if it's on sda or sdb (I think this is mostly a Firewire issue). Then make a directory to mount to, and do sudo mount /dev/sd(a or b)2 /mnt/YourMountPoint . Then your ipod should be mounted and recognized, I can see it again in Banshee. Then, when you're done with it, just do sudo umount /mnt/YourMountPoint . That will unmount it, but your iPod will still say "Do not Disconnect", so do sudo eject sd(a or b).

---

### Post by REBELinBLUE on 2006-06-14
[QUOTE=denisesballs]Ok, after playing around a little, I found a workaround. If your iPod isn't mounting, do a dmesg and see if it's on sda or sdb (I think this is mostly a Firewire issue). Then make a directory to mount to, and do sudo mount /dev/sd(a or b)2 /mnt/YourMountPoint . Then your ipod should be mounted and recognized, I can see it again in Banshee. Then, when you're done with it, just do sudo umount /mnt/YourMountPoint . That will unmount it, but your iPod will still say "Do not Disconnect", so do sudo eject sd(a or b).[/QUOTE]

yeah, that is what I'm been doing but it is still a PITA ;) Also, listen doesn't appear to pick it up when you do that

---

### Post by Ferrat on 2006-07-07
For me it works flawless using sudo eject ipod :) thx

---

### Post by benguin on 2006-08-25
Just to raise my hand and say my 3rd gen iPod is doing the same. I'm using Dapper by the way.

While its good to hvae one, I'd rather not do that workaround to get it to work. Any ideas anyone?

Thanks,
-J-

---

### Post by denisesballs on 2006-08-25
I'm pretty sure this is a firewire issue. Is you use USB it should mount normally every time.

---

### Post by g_rael on 2006-08-28
If only "should" and "does" were that same things !

however, I used to have the same problems.

I think in the end, I got them working by removing all specific USB HD lines from my fstab and uninstalling and then reinstalling the various USB packages in the repositories.

However, I have to find them in "Places/Computer", they don't make a pop-up nautilus window by themselves.:shock:

---

