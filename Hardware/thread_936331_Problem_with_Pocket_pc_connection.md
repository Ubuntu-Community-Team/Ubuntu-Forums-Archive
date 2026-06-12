---
title: "Problem with Pocket pc connection"
date: 2008-10-02
forum: Hardware
---

### Post by spenko on 2008-10-02
Hi all,
I'm a new ubuntu user

I have some problem with the sync of my pocket pc, a Mitac Mio 168

I read some "how to" in this forum and wiki and also in ubuntu italian site.

I see that dmesg command return an error, and PPC doesn't mount in ttyUSB:

```

[  476.644601] usb 2-2: new full speed USB device using uhci_hcd and address 2
[  476.794406] usb 2-2: configuration #1 chosen from 1 choice
[  476.866188] usbcore: registered new interface driver usbserial
[  476.866367] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[  476.866576] usbcore: registered new interface driver usbserial_generic
[  476.866578] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[  476.888156] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for PocketPC PDA
[  476.888160] /build/buildd/linux-2.6.24/drivers/usb/serial/ipaq.c: USB PocketPC PDA driver v0.5
[  476.888191] ipaq: probe of 2-2:1.0 failed with error -5
[  476.888197] usbcore: registered new interface driver ipaq
[  654.543695] usb 2-2: USB disconnect, address 2
[ 2520.068380] usb 2-2: new full speed USB device using uhci_hcd and address 3
[ 2520.214783] usb 2-2: configuration #1 chosen from 1 choice
[ 2520.217744] ipaq: probe of 2-2:1.0 failed with error -5

```

however lsusb command see its presence.
```

Bus 002 Device 003: ID 3340:043a Yakumo Mio A701 DigiWalker PPCPhone

```

moreover i can't find ttyUSB in /dev/ but there are only usbdev etc.

So, how i read i some forum i try to update ipaq driver, but I can't compile because of this mistake:
```

alessio@alessio-desktop:~/Scrivania/temp/kernel-2.6-driver$ sudo make
ln -sf /usr/src/linux-source-2.6.24/drivers/usb/serial/usb-serial.c usb-serial.c
ln -sf ipaq.h-2.6.15 ipaq.h
cp -p ipaq.c-2.6.15 ipaq.c
patch -N -p0 < ipaq-select-endpoints.diff
patching file ipaq.c
Hunk #2 FAILED at 74.
Hunk #3 succeeded at 974 (offset 414 lines).
Hunk #4 succeeded at 1009 (offset 414 lines).
1 out of 4 hunks FAILED -- saving rejects to file ipaq.c.rej
make: *** [.patched] Error 1

```

I download driver source from svn of synce ([https://svn.sourceforge.net/svnroot/synce/branches/legacy/kernel-2.6-driver](https://svn.sourceforge.net/svnroot/synce/branches/legacy/kernel-2.6-driver)).

For who understand italian i follow this guide : [http://wiki.ubuntu-it.org/Hardware/PocketPC?highlight=(pc)|(pocket)](http://wiki.ubuntu-it.org/Hardware/PocketPC?highlight=(pc)|(pocket))

Thanks 

Bye

PS: sorry for my bad english

---

### Post by spenko on 2008-10-03
up

---

