---
title: "[SOLVED] Problem accessing external USB hard disk"
date: 2009-01-06
forum: Hardware
---

### Post by MaxMax on 2009-01-06
Hello,

I'm using Ubunto 8.04. When plugging in a USB external HD, an error message suggests to force mount the device with this command:

[INDENT]mount -t ntfs-3g /dev/sdc1 /media/PortableData -o force[/INDENT]

However, when I type it in the terminal, I get an error message saying it's only possible for root... Can anyone help?

Thanks!

---

### Post by 2hot6ft2 on 2009-01-06
You didn't start that command with sudo i.e.
```
sudo mount -t ntfs-3g /dev/sdc1 /media/PortableData -o force
```

Did you unplug it from a windows pc without using the safely remove hardware option?

Then you wont have to use force.

If so it would be best to plug it into a windows pc and use the safely remove hardware option located in the lower right by the clock before unplugging it.

Likewise in ubuntu you should right click and choose unmount before removing it.

---

### Post by MaxMax on 2009-01-07
Thanks! The problem was exactly as you said, and now it works.

---

