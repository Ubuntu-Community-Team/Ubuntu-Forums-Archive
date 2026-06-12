---
title: "Unable to write usb drive!"
date: 2011-09-17
forum: Hardware
---

### Post by Esai on 2011-09-17
Hello, I tried formating my usb flash drive in windows and it got stuck in the end... After waiting for about 20 minutes I disconnected it ;( When I replugged it I was told to format it... So I tried formating it again and it gave me an error that my drive is write protected... I guessed that it just didn't format it correctly which should be pretty obvious... So I fired up my B|T4 r1 and tried 'sudo fdisk /dev/sdc' got a message:
```
 You will not be able to write the partition table. Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel Building a new DOS disklabel with disk identifier 0xd8c68ffb. Changes will remain in memory only, until you decide to write them. After that, of course, the previous content won't be recoverable.  Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite) 
``` so I typed w and it answered: Unable to write /dev/sdc 
Raw data in partition table: ```
  
0x000: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x010: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x020: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x030: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x040: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x050: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x060: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x070: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x080: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x090: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x0A0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x0B0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0C0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0D0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x0F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x100: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x110: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x120: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x130: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x140: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x150: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x160: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x170: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x180: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x190: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x1A0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x1B0: 00 00 00 00 00 00 00 00 28 D7 3D 12 00 00 00 00 
0x1C0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x1D0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x1E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x1F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 AA 

```

---

### Post by ajgreeny on 2011-09-17
Try gparted in a live CD if necessary, or you can install it in a Ubuntu installation and use it for unmounted non-system partitions.

For your usb drive choose Device, Create partition table, and make an ms-dos partition table. You should then be able to make a new fat32, or any other filesystem type partition that you want on the disk.

---

### Post by Esai on 2011-09-17
> **ajgreeny said:**
> Try gparted in a live CD if necessary, or you can install it in a Ubuntu installation and use it for unmounted non-system partitions.
 
For your usb drive choose Device, Create partition table, and make an ms-dos partition table. You should then be able to make a new fat32, or any other filesystem type partition that you want on the disk.
 
I already tried gparted and it doesn't show up over there :(

---

### Post by Esai on 2011-09-18
Anyone?
I really need it.....

---

