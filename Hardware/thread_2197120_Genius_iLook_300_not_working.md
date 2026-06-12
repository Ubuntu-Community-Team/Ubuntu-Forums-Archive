---
title: "Genius iLook 300 not working"
date: 2014-01-02
forum: Hardware
---

### Post by ivanr19822 on 2014-01-02
I'm using ubuntu 12.04 and unsuccessfully trying to get genius iLook 300 camera to work. It works very well with Windows, but here I'm not even succeeding to get the picture from camera to Cheese.

This is what I get from lsusb:
```

ivan@ivan-laptop:~$ lsusb
Bus 003 Device 005: ID 093a:2628 Pixart Imaging, Inc. 
Bus 005 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

but dmesg gives me this all the time:

```

ivan@ivan-laptop:~$ dmesg | grep -i cam
[    0.000000]   AMD AuthenticAMD

```

Also, when I start Cheese the light on camera turns green as if it is on.

Kernel version is:
```

ivan@ivan-laptop:~$ uname -a
Linux ivan-laptop 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 15:31:16 UTC 2013 i686 i686 i386 GNU/Linux

```

Also tried everything in old threads but no help.

I would appreciate any help.

---

### Post by mörgæs on 2014-01-05
If you have tried "everything" there's nothing we can add, sorry.

Does everything include a live boot of 13.10?

---

### Post by ivanr19822 on 2014-01-05
Didn't try live boot of 13.10, but did a safer thing. Bought other webcam that works with 12.04 and everything's perfect now. :) They let me try it in store, so I took one that's on lists of webcams on this link: [https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras). That's pretty much it. Thanks for your answer, but webcams are that cheap nowadays, so it's better to buy a new one and sell or give the old one rather than losing a few days if you're not advanced user.

---

