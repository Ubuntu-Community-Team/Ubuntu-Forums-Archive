---
title: "Boot from an SD card?"
date: 2010-06-01
forum: Hardware
---

### Post by Cogizio on 2010-06-01
I just installed Ubuntu 10.04 Netbook Edition onto an SD card (using [Pendrive Linux]("http://www.pendrivelinux.com/")) for a laptop that, let's just say it doesn't have much life in it. The hard drive is dead, the case is cracking, and the wire to the hard drive *slot* is probably broken. But, being cheap, I wanted a persistent OS to use, so I installed 10.04NE on my SD card. 
However, I can't boot off the SD card--is there any way? (I'm thinking maybe a CD that does it, kinda like there used to be floppies that booted CDs.)

---

### Post by fiddler616 on 2010-06-01
If you have a USB card reader, then the BIOS will see the SD card as being the same thing as a USB flash drive, so assuming your BIOS supports booting from a USB drive, that'll work.

If you don't have a USB card reader, apparently it's possible to perform GRUB voodoo. So you'd boot off an Ubuntu CD, load GRUB off of that, and then use GRUB to boot the SD card. However, I have no idea what magic you would need to pull with GRUB.

[Source / further reading.]("http://www.mydellmini.com/forum/other-distributions/586-booting-sd-card.html")

And I don't mean to be rude, but...[Google is your friend]("http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=boot+off+an+sd+card").

---

### Post by Cogizio on 2010-06-02
> **fiddler616 said:**
> 
And I don't mean to be rude, but...[Google is your friend]("http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=boot+off+an+sd+card").
I tried Google, and I couldn't find what I wanted :(. But that result seems to help; I'll check it out!
----------
Ahh. Darn. It requires GRUB on the *internal drive*, which is exactly why I need to use the SD card: the HD port has killed two HDDs already. Thanks, though!

---

### Post by fiddler616 on 2010-06-02
> **Cogizio said:**
> I tried Google, and I couldn't find what I wanted :(. But that result seems to help; I'll check it out!
----------
Ahh. Darn. It requires GRUB on the *internal drive*, which is exactly why I need to use the SD card: the HD port has killed two HDDs already. Thanks, though!

Don't you have a CD-ROM? You can get GRUB going off of that. That's essentially what "a CD that does it, kinda like there used to be floppies that booted CDs" would be.

---

### Post by Cogizio on 2010-06-04
> **fiddler616 said:**
> Don't you have a CD-ROM? You can get GRUB going off of that.

OK, well I found those instructions. But now my Google-fu has failed me again; while when I run the *sudo fdisk -lu* command I found elsewhere it reports this:

```
locutus@locutus-laptop:~$ sudo fdisk -lu

Disk /dev/sda: 38.5 GB, 38502535680 bytes
255 heads, 63 sectors/track, 4681 cylinders, total 75200265 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00040627

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    72019967    36008960   83  Linux
/dev/sda2        72022014    75198463     1588225    5  Extended
/dev/sda5        72022016    75198463     1588224   82  Linux swap / Solaris

Disk /dev/mmcblk0: 1977 MB, 1977614336 bytes
62 heads, 61 sectors/track, 1021 cylinders, total 3862528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1             135     3862527     1931196+   6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 2, 10) logical=(0, 2, 14)
Partition 1 has different physical/logical endings:
     phys=(957, 61, 61) logical=(1021, 18, 8)
```

So this my 2GB SD card is SDA, correct? How would I add this to a GRUB CD (made from [these instructions]("http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html"))? Someone on Linux Questions said (to another person) that you do this:
[I]Edit your /boot/grub/menu.lst and ad the following:
[/I] 
 	Code:
 	title Windows
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
chainloader +1 
for adding Windows to GRUB. I'm assuming my file needs this:
 	Code:
 	title Ubuntu 10.04 LTS
map (sda0) (sda1)
map (sda1) (sda0)
root (sda1,0)
chainloader +1 
Is that correct? Also, where would */boot/grub/menu.lst* be on the GRUB CD?
Thanks for all your help--I hope I can get this to work!

---

### Post by efflandt on 2010-06-05
If your SD is 2 GB, that would be mmcblk0, not sda.  It looks like sda may be the internal drive (38.5 GB).  I am not sure if grub will boot from mmcblk0.  I know that my laptop will not natively boot from its card slot.

The multi-card reader in my desktop is internally connected through USB, so I can boot SD on that.

Do you have a USB card reader you could use to attempt to boot from SD (which will then appear to be regular USB mass storage)?

---

### Post by Cogizio on 2010-06-05
I don't have a USB card reader--but at this point in time I am considering getting one. After all I was at Target recently and found one for $6. Not bad! 
However, I recently discovered that the original hard drive it killed still works (somehow) so I Hackintoshed it. Thanks for your help!

---

