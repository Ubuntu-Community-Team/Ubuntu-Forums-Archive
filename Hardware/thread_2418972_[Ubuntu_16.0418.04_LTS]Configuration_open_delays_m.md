---
title: "[Ubuntu 16.04/18.04 LTS]Configuration open delays more than 2 min"
date: 2019-05-14
forum: Hardware
---

### Post by Marco_Ros on 2019-05-14
Hello,
I have just installed Ubuntu 16.04 (again after using 18.04 for several months) and encountered that for opening CONFIGURATION, it takes more than 2 minutes each time, it does the same when opening "About this PC" (Acerca de este equipo)
In the former installation, I have solved this issue changing some parameter for the VIDEO DEVICE DRIVER at startup, but I don't find that information again.

---

### Post by Marco_Ros on 2019-05-14
I added the following parameter to GRUB:
```

video=SVIDEO-1:d

```

Inserting the line:
```

GRUB_CMDLINE_LINUX="video=SVIDEO-1:d"

```

To open GRUB configuration file, you need to use:
```

sudo gedit /etc/default/grub

```

Then update GRUB with
```

sudo update-grub

```

---

