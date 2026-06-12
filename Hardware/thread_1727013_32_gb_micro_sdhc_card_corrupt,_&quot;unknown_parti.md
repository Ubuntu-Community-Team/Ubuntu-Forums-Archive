---
title: "32 gb micro sdhc card corrupt, &quot;unknown partition table&quot;"
date: 2011-04-11
forum: Hardware
---

### Post by limescout on 2011-04-11
Hello all,
I recently received a 32gb micro sdhc card for storing music on my phone.  I first formatted the card on my phone for use with it's music player.  Then I inserted the card into my computer's sd slot.  I began to copy music to the card, but it froze during a file sample.  I couldn't force quit the process, so I shut down ubuntu thinking I'll reformat the card and start again.  Something went wrong with the card and I don't know what to do about it.

My phone won't recognize the card like it did before.  It behaves as if there is no card.

Windows shows the card, but when I try to format it in Windows, it gives me an error; something like "windows could not format the drive"

Here is what I get from dmesg:
```
[  215.780234] mmc0: new SD card at address 0001
[  215.780490] mmcblk0: mmc0:0001 AF HM 8.00 MiB 
[  215.780616]  mmcblk0: unknown partition table

```

please don't hesitate to ask for any more information.

---

### Post by dandnsmith on 2011-04-12
I'd be tempted to dd /dev/zero to the first 512 bytes to scrub the partition and other info, and then check if the phone can now 'see' it.

---

### Post by Grenage on 2011-04-12
> **limescout said:**
> Hello all,
I recently received a 32gb micro sdhc card for storing music on my phone.  I first formatted the card on my phone for use with it's music player.  Then I inserted the card into my computer's sd slot.  I began to copy music to the card, but it froze during a file sample.  I couldn't force quit the process, so I shut down ubuntu thinking I'll reformat the card and start again.  Something went wrong with the card and I don't know what to do about it.

My phone won't recognize the card like it did before.  It behaves as if there is no card.

Windows shows the card, but when I try to format it in Windows, it gives me an error; something like "windows could not format the drive"

Here is what I get from dmesg:
```
[  215.780234] mmc0: new SD card at address 0001
[  215.780490] mmcblk0: mmc0:0001 AF HM 8.00 MiB 
[  215.780616]  mmcblk0: unknown partition table

```

please don't hesitate to ask for any more information.

32GB Ebay purchase, so cheap it seemed too good to be true?

What does ```
sudo fdisk -l
``` tell you?

---

### Post by limescout on 2011-04-12
relevant info from "fdisk -l"
```
Disk /dev/mmcblk0: 8 MB, 8388608 bytes
4 heads, 16 sectors/track, 256 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe846a429

Disk /dev/mmcblk0 doesn't contain a valid partition table

```

sudo dd if=/dev/zero of=/dev/mmcblk0 bs=512
```
$ sudo dd if=/dev/zero of=/dev/mmcblk0 bs=512
dd: writing `/dev/mmcblk0': No space left on device
16385+0 records in
16384+0 records out
8388608 bytes (8.4 MB) copied, 2.85786 s, 2.9 MB/s
$ 

```

card is still not recognized on phone or computer

---

### Post by coffeecat on 2011-04-12
> **limescout said:**
> card is still not recognized on phone or computer

When you say not recognised on computer, does fdisk still see it, albeit with no partition table? If you get:

```
Disk identifier: 0x00000000
```

Try seeing if you can create a new partition table in Gparted (from the device menu) and then a formatted partition.

---

### Post by limescout on 2011-04-13
It won't show up in Gparted at all

I've been reading up lately about fake memory cards, and I'm convinced this is one of them.  The place where I bought it is going to give me a full refund, so I think I'm going to just return it and get one from a different company.  Thanks for your suggestions everyone.

---

### Post by Grenage on 2011-04-13
> **limescout said:**
> It won't show up in Gparted at all

I've been reading up lately about fake memory cards, and I'm convinced this is one of them.  The place where I bought it is going to give me a full refund, so I think I'm going to just return it and get one from a different company.  Thanks for your suggestions everyone.

Yes, that was and is my suspicion; there have been a lot of people coming here with '8GB+' drives.

---

