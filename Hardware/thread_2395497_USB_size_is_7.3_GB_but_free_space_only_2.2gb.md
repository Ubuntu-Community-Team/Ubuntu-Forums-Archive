---
title: "USB size is 7.3 GB but free space only 2.2gb"
date: 2018-07-02
forum: Hardware
---

### Post by alexalmis on 2018-07-02
USB size is 7.3 GB but free space only 2.2gb how to make free space 7.3gb???    
[ATTACH=CONFIG]280268[/ATTACH]

---

### Post by oldfred on 2018-07-02
Post this:

sudo gdisk -l /dev/sdc
Assumes drive is still sdc, otherwise use correct device.

---

### Post by alexalmis on 2018-07-03
Disk /dev/sdc: 7,3 GiB, 7873757184 bytes, 15378432 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: C8A7A073-0640-4EB6-9CFF-03D3EFDCF444


Device     Start     End Sectors  Size Type
/dev/sdc1   2048 4640767 4638720  2,2G Linux filesystem
 Thats the output.

---

### Post by westie457 on 2018-07-03
Was this device used to install a Linux OS onto a UEFI enabled computer?

If the answer to the question is yes, to reclaim the spase on the device you have to wipe it and give it a new partition table.

See this for a 'safe' way. [https://help.ubuntu.com/community/mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

or look at ```
man gdisk
``` to achieve this in the terminal.

---

