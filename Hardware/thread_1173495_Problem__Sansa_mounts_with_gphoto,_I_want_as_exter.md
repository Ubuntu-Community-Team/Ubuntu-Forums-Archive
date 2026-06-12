---
title: "Problem:  Sansa mounts with gphoto, I want as external disc!"
date: 2009-05-29
forum: Hardware
---

### Post by Keith_Beef on 2009-05-29
Since installing 9.04, I have a problem.

My Sansa e280 used to show up as an external disc. I could read from it, write to it, as a normal user, and do everything just fine.

Now, when I plug it in I sometimes get a Nautilus window, where the device shows as being connected through gphoto2. Sometimes, it just does not appear at all.

When it connects, I cannot read the permissions on the files or folders. This means I can't delete a file, or edit it directly on the device.

I looked around the forums, and found some info about udev rules... but I still don't understand well enough.

The device seems to be correctly identified, as shown below.
```
$ lsusb
Bus 001 Device 006: ID 0781:7420 SanDisk Corp. Sansa E200 series (mtp)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0fce:d019 Sony Ericsson Mobile Communications AB VDC EGPRS Modem
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 044e:300c Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```


And even /lib/udev/rules.d/45-libmtp8.rules contains the rules below.
```

# SanDisk Sansa m230/m240
ATTR{idVendor}=="0781", ATTR{idProduct}=="7400", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa c150
ATTR{idVendor}=="0781", ATTR{idProduct}=="7410", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa e200/e250/e260/e270/e280
ATTR{idVendor}=="0781", ATTR{idProduct}=="7420", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa e280
ATTR{idVendor}=="0781", ATTR{idProduct}=="7421", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
# SanDisk Sansa e280 v2
ATTR{idVendor}=="0781", ATTR{idProduct}=="7422", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
```

But still the device doesn't mount... any ideas why?

K.

---

### Post by drewkime on 2009-06-14
Same issue here, with a Sansa Clip. This used to work.  Now it consistently shows up as gphoto, and I can see the folder structure but none of the contents.

---

### Post by icheyne on 2009-06-20
I wrote some Sansa Clip instructions [here]("https://help.ubuntu.com/community/SansaClip").

---

### Post by inspired on 2009-06-26
> **icheyne said:**
> I wrote some Sansa Clip instructions [here]("https://help.ubuntu.com/community/SansaClip").

I have the same issue. Glad to see I am not the only one. I will check out these instructions and see if that sorts it out.
Anyone else got feedback re these instructions?

---

### Post by inspired on 2009-06-26
Okay. So those instructions are totally clip specific.

Has anyone figured out how to fix this issue with an e200 series? (e280 in my case).

Regards,
Jonathan

---

