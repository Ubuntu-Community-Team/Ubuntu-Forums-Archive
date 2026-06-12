---
title: "safe to edit /etc/fstab to automount usb devices"
date: 2009-07-05
forum: Hardware
---

### Post by pythonscript on 2009-07-05
The two usb devices in question are an external hard drive, formatted as ntfs, and a flash drive, formatted as vfat. I have to use these devices with a good amount of windows computers, so formatting them as ext* isn't really an option. I'm wondering about any negative implications of adding them to the fstab file with their UUID's, so they automatically mount when I plug them in. For the ntfs one, if I just add
```

UUID=94547C6D547C53C8, /media/WD ntfs defaults,relatime 0 0

```

would that be a problem in any way? Since I don't always insert them in the same order, of course, referring to them in fstab by their partition numbers seemed like a bad idea. If this *is* a good idea, would this code work for the second device (enabling read, write, etc)?

```

UUID=F8B1-1AFE, /media/TRANSCEND vfat defaults,relatime 0 0

```

Thanks!

---

### Post by ajgreeny on 2009-07-05
USB devices always mount automatically on my machine, and always have, so I'm surprised they don't on yours.  Are you certain they do not already do so.  If you have your computer setup not to show volumes on the desktop, you may not be aware that they are mounted.  Have a look in gconf-editor- apps- nautilus- desktop and see if the *volumes visible* is selected, and also look in /media for folders that may be your disks.

---

