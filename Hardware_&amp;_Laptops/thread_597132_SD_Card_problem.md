---
title: "SD Card problem"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by thommo on 2007-10-30
Hello all, have been having a few problems with my IBM T21 Thinkpad since upgrading recently. I first upgraded from 6.10 to 7.04 and then to 7.10, and had a few problems with wifi and screen resolution. These are now fixed thanks to answers found on this forum. One issue remains however that I cannot find an answer to, hence this post.

I have a Toshiba PCMCIA SD Card reader that worked fine under previous distributions. Today I went to use if for the first time since upgrading and no joy - the SD card didn't mount when inserted in the reader.

I checked - permissions, membership of plugdev group, and the settings relating to autoloading under System > Preferences > Removable drives and Media.

All appear fine. Tried ejecting and reseating the PCMCIA card (with the SD card still inserted in it) and it worked! Great I thought, I then copied some data from the SD card and attempted to delete some files from it. This seemed to work fine. 

THEN I unmounted the device and received a message about emptying the garbage bin, I said yes to this and was then presented with an error about it being a read only disk. I've never had this before. A quick run of dmesg in terminal had a line in it about "write cache: disabled". Unfortunately I didn't keep the output and it is no longer there after several reboots.
At this stage a "sudo fdisk -l" showed the device as dev/sdd. I edited the /etc/fstab file to include a line to mount dev/sdd to /media/disk and rebooted. Still no luck.

I have since deleted the line from fstab and tried the card in a different PCMCIA slot. Several more reboots.

Now the situation has changed. The SD card doesn't mount at all anymore.

dmesg | tail shows:
```
[  450.396000] pcmcia: registering new device pcmcia1.0
[  450.688000] scsi2 : pata_pcmcia
[  450.688000] ata3: PATA max PIO0 cmd 0x00010100 ctl 0x0001010e bmdma 0x00000000 irq 3
[  480.852000] ata3.00: qc timeout (cmd 0x91)
[  480.852000] ata3.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x4)
[  511.520000] ata3.00: qc timeout (cmd 0x91)
[  511.520000] ata3.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x4)
[  511.520000] ata3.00: limiting speed to UDMA7:PIO5
[  542.188000] ata3.00: qc timeout (cmd 0x91)
[  542.188000] ata3.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x4)

```

The device no longer  shows up when doing a sudo fdisk -l.
It does show in System > Preferences > Hardware Information

Any ideas?

---

### Post by blackgoose on 2008-02-28
Have researched this as I'm in the same situation. Apparently it's an upstream kernel problem - it also afflicts Fedora 7 & 8 systems I have kicking around. I tried upgrading Gutsy's kernel to 2.6.24 (i.e. Hardy's kernel). Still broken.

Apparently it was broken after 2.6.20. I'm keeping an eye on kernel mailing lists to see if a fix has been found. Didn't look like there was a patch in 2.6.24 but thought I'd try it anyway. No dice. :(

---

