---
title: "External Cardreader"
date: 2008-09-22
forum: Hardware
---

### Post by Smika on 2008-09-22
Hello,

I tried to use my card reader, but it doesn;t work. If I use the command lsusb, I can see my card reader:

Bus 002 Device 004: ID 0d8c:5200 C-Media Electronics, Inc.

What can i do, so I can use it?

Smika

---

### Post by timcredible on 2008-09-22
what happens when you put a card in the reader?

---

### Post by Smika on 2008-09-22
completely nothing

---

### Post by RaZoR1394 on 2008-10-18
Hello.

I have an internal C-media card reader branded as Equip. It seems this doesn't work like normal card readers and you'll have to use special drivers. I found drivers on the Equip website for Red hat 9 (Linux 2.4.20) and Fedora Core 3 (Linux 2.6.9).

[http://www.equip-info.net/english/index.php?main=10&gruppe=100&pagenum=2&prod=2154](http://www.equip-info.net/english/index.php?main=10&gruppe=100&pagenum=2&prod=2154)

Here are the files in the deb packages:

Red hat 9

```

./
usr/
usr/share/
usr/share/doc/
usr/share/doc/cm-usb-storage/
usr/share/doc/cm-usb-storage/changelog.Debian.gz
usr/share/doc/cm-usb-storage/copyright
usr/lib/
usr/lib/modules/
usr/lib/modules/2.4.20-8/
usr/lib/modules/2.4.20-8/extra/
usr/lib/modules/2.4.20-8/extra/cm-usb-storage.o

```

Fedora core 3

```

./
usr/
usr/share/
usr/share/doc/
usr/share/doc/cm-usb-storage/
usr/share/doc/cm-usb-storage/changelog.Debian.gz
usr/share/doc/cm-usb-storage/copyright
usr/lib/
usr/lib/modules/
usr/lib/modules/2.6.9-1.667/
usr/lib/modules/2.6.9-1.667/extra/
usr/lib/modules/2.6.9-1.667/extra/cm-usb-storage.ko

```

Insmodding the last one gives:

```

razor1394@gemenon:/usr/lib/modules/2.6.9-1.667/extra$ sudo insmod cm-usb-storage.ko 
insmod: error inserting 'cm-usb-storage.ko': -1 Invalid module format

```

but that's understandable as It's for a very old kernel and I'm running 2.6.27-7.

The c-media website has pulled It's drivers.

edit:

```

razor1394@gemenon:/usr/lib/modules/2.6.9-1.667/extra$ lsusb | grep C-Media
Bus 001 Device 005: ID 0d8c:5200 C-Media Electronics, Inc. Mass Storage Controller(0D8C,5200)

```

---

### Post by kvaka on 2008-11-25
I can't believe nobody got this piece of s**t working!!!
I'm having exact same problem. none of older drivers worked for me.

HEEEEELP! :)

---

