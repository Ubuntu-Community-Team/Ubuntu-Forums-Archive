---
title: "Want to completely reformat USB"
date: 2012-06-09
forum: Hardware
---

### Post by furmada on 2012-06-09
Hello:

I am trying to format a friend's 8GB Dane-Elec USB.
Disk manager shows only one "Unknown" partition of 8.4MB on the drive and will not format the drive.
I just need to completely wipe the drive and restore 8GB size.

Any help?
Thank You.

---

### Post by wilee-nilee on 2012-06-09
> **furmada said:**
> Hello:

I am trying to format a friend's 8GB Dane-Elec USB.
Disk manager shows only one "Unknown" partition of 8.4MB on the drive and will not format the drive.
I just need to completely wipe the drive and restore 8GB size.

Any help?
Thank You.

Try using gparted, you may need to install it.

---

### Post by Handssolow on 2012-06-09
This may not be relevant to your problem but here goes.
I had a problem formatting a new SD memory card for my Panasonic camera, the Disk Utility needed the memory to be unmounted first before I could format using Ubuntu. Even then before I could use the memory, the camera still needed to format the memory again.

---

### Post by N0oki3 on 2012-06-09
Hi there
If you don't have, you can install gparted via
```
sudo apt-get install gparted
```

access it via ```
sudo gparted
```

1) select usb 

2) change file system

3) click format button

---

