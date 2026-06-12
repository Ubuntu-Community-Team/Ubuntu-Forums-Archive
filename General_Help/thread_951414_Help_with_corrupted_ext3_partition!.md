---
title: "Help with corrupted ext3 partition!"
date: 2008-10-18
forum: General Help
---

### Post by magichours on 2008-10-18
Hello all,

Ubuntu crashed on me yesterday, the screen just froze and the mouse/keyboard stopped responding. I did a hard reset and got this error from GRUB:-

GRUB loading stage1.5

Error 17

I got the live cd, booted up. Run Gparted to check against my linux partition and got the following output:-

**calibrate /dev/sdb2**

path: /dev/dbs2
start: 629153595
end: 781417664
size: 152264070 (72.61 GiB)

**e2fsck -f -y -v /dev/sdb2**

Could this be a zero length partition?

e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb2

Having only been running ubuntu for 8 months I'm a little stuck now! I'd just got ubuntu running the way I wanted :(

If anyone could help me to recover this partition it would be greatly appreciated!

---

### Post by magichours on 2008-10-18
I attempted to mount the device, no luck!

error msg: [B]mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
              missing codepage or helper program, or other error[/B]

dmesg output attached

---

