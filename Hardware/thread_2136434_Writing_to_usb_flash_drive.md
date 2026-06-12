---
title: "Writing to usb flash drive"
date: 2013-04-17
forum: Hardware
---

### Post by tomasz_svk on 2013-04-17
I experience small problem with writing big files to usb flash drives (FAT32/NTFS/EXT). I think it casues buffering before write.

Example:
I have 2GB file
[LIST=1]
[*]I start to copy it to usb flash drive.
[*]First few seconds works only HDD (reading, almost 300 MB), USB flash drive is idle.
[*]After that USB flash drive starts to write.
[*]Reading has finished, but writing is still running (nautilus/midnight commander shows 99 or 100% of progess) for about minute after.
[/LIST]

Is there any solution for immediately writing? It causes some problems when usb drive is slow, there is no led indicator and I don't see any progress (except iotop).

---

