---
title: "fdisk losing it - yet another external drive problem"
date: 2009-04-23
forum: Hardware
---

### Post by AmberG on 2009-04-23
I have added a Maxtor usb external drive.
I have downloaded ntfs-config and ntfs3g as per instructions
plug in - nothing happens
reboot - "new disk" appears in panel and I follow instructions to auto mount.
all ok so far - drive appears in Nautilus and I can save files ok. Even run a simple backup (that is what the drive is for).

but I look back later and the drive has vanished (from the file system)

this happens every day, even though the drive is permanently connected.

I have looked around for similar problems and suggestions always start with a:
```
 sudo fdisk -l 
```

If this is done after a reboot then the drive is listed (and after auto mount it gets assigned /media/disk as expected.

But after a seemingly random period it disappears from fdisk so I cannot mount it manually.

I hate having to keep rebooting the machine.
Is there some way to reboot the disk "locator" withut having to unload all programs and reboot and start all over?

Anyway surely this shouldn't happen?

PS. 8.10 running and there are 2 internal drives

---

