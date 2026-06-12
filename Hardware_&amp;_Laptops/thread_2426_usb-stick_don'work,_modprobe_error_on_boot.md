---
title: "usb-stick don'work, modprobe error on boot"
date: 2004-10-28
forum: Hardware &amp; Laptops
---

### Post by paulle on 2004-10-28
ello, when booting ubuntu, the boot screen tells me:

modprobe: Fatal: error inserting shpchp (/lib/modules.2.6.8.1-3-386/rs/pci/hotplug/pciehp.ko)

and i can't get my usb-stick to work.
i've a laptop dell inspiron 4000, 128mb ram.

any idea how to resolve this problem, i'm new to ubuntu and linux.

greetings  chris

---

### Post by FLeiXiuS on 2004-10-28
[QUOTE=paulle]ello, when booting ubuntu, the boot screen tells me:

modprobe: Fatal: error inserting shpchp (/lib/modules.2.6.8.1-3-386/rs/pci/hotplug/pciehp.ko)

and i can't get my usb-stick to work.
i've a laptop dell inspiron 4000, 128mb ram.

any idea how to resolve this problem, i'm new to ubuntu and linux.

greetings  chris[/QUOTE]

The modprobe error wouldn't be your usb-stick.  Its a bug in the fixing stage.

Plug in the stick, then if its already formatted then mount it.

```

mount -t FS /dev/sda /path/to/mount-dest

```

Replace FS with the stick's file system.  Then replace the mount destination to where ever you want.

---

