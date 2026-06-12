---
title: "Logitech quickcam pro 4000"
date: 2005-12-08
forum: Hardware &amp; Laptops
---

### Post by meestayenkins on 2005-12-08
```
8.8 (kernel 2.4.19, 2.5.33) pwc-8.8.tar.gz

This is not a patch but a whole package. Just copy the source code files over the existing ones, build and install the modules and you should be on the road.

    * Added IDs for QuickCam Pro 4000.
    * Fixed 'leds' parameter
    * Minor cleanups, code is more reliable on 2.5.* kernel series
```
That is the package I downloaded because it is the one that supports the Logitech Quickcam 4000 pro. My question is now that I've downloaded it, how do I go about installing it? The contents of the tar is two directories, kernel-2.4 and kernel-2.5. Here is the contents of those folders...
```
./pwc-8.8/kernel-2.4/ChangeLog
./pwc-8.8/kernel-2.4/philips.txt
./pwc-8.8/kernel-2.4/pwc.h
./pwc-8.8/kernel-2.4/pwc-ctrl.c
./pwc-8.8/kernel-2.4/pwc-if.c
./pwc-8.8/kernel-2.4/pwc-ioctl.h
./pwc-8.8/kernel-2.4/pwc-kiara.h
./pwc-8.8/kernel-2.4/pwc-misc.c
./pwc-8.8/kernel-2.4/pwc_nala.h
./pwc-8.8/kernel-2.4/pwc_timon.h
./pwc-8.8/kernel-2.4/pwc-uncompress.c
./pwc-8.8/kernel-2.4/pwc-uncompress.h

./pwc-8.8/kernel-2.5/ChangeLog
./pwc-8.8/kernel-2.5/philips.txt
./pwc-8.8/kernel-2.5/pwc.h
./pwc-8.8/kernel-2.5/pwc-ctrl.c
./pwc-8.8/kernel-2.5/pwc-if.c
./pwc-8.8/kernel-2.5/pwc-ioctl.h
./pwc-8.8/kernel-2.5/pwc-kiara.h
./pwc-8.8/kernel-2.5/pwc-misc.c
./pwc-8.8/kernel-2.5/pwc_nala.h
./pwc-8.8/kernel-2.5/pwc_timon.h
./pwc-8.8/kernel-2.5/pwc-uncompress.c
./pwc-8.8/kernel-2.5/pwc-uncompress.h
./pwc-8.8/kernel-2.5/.#philips.txt.1.4
./pwc-8.8/kernel-2.5/.#pwc.h.1.41
```

I dont know enough about using the terminal and modules or w/e. So any help you guys could give me so I can get my webcam working would be much appreciated.

---

### Post by mlomker on 2005-12-08
Breezy uses a 2.6.x kernel, so those drivers are all too old.  Does Breezy not recognize your camera when you plug it in?  I have a Quickam and Ubuntu loads the driver on its own.

Plug it in and then look at the output of **lsusb** and **dmesg | tail** to see if it is being recognized at all.

Finding software to work with it is entirely another matter...pickings are fairly slim on linux.  Gnome meeting and command-line stuff for taking snapshots are about all that I found.

---

### Post by meestayenkins on 2005-12-08
```
Bus 005 Device 005: ID 06e1:d835 ADS Technologies, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 005: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 046d:c00e Logitech, Inc. Optical Mouse
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```

It does recognize it... any thoughts on what i should do?

---

### Post by meestayenkins on 2005-12-08
Issue resolved. Mods can close.

---

