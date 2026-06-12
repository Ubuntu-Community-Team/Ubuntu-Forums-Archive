---
title: "linux noob needs help"
date: 2008-10-28
forum: General Help
---

### Post by john-tomhas on 2008-10-28
hi im new to ubuntu and i want to install wow. i have the discs and all the guides say to install it through WINE you need the installer.exe file. when i go into the disc it does not have this file. can anyone please help me. (dont tell me to download the client as i do not have enough broadband useage )

---

### Post by geirha on 2008-10-28
I remember a thread some months ago with a similar problem. The problem then was that the wow dvd had two filesystems, iso9660 for windows and udf for mac osx. Ubuntu supports both, and will default to mounting udf if the CD/DVD has it, which in turn will only display the mac osx files. So, the easiest option is to unmount the CD/DVD manually, then manually mount it with iso9660.

Try this. 
```
sudo umount /media/cdrom
sudo -t iso9660 /dev/scd0 /media/cdrom

```

I'm guessing at the correct device node and mount point to use here. If you don't know these things your self, and the above does not work, post the output of ```
mount
``` while the CD/DVD is in the drive and mounted.

---

