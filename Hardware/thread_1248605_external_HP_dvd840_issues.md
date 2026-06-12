---
title: "external HP dvd840 issues"
date: 2009-08-24
forum: Hardware
---

### Post by kyoha on 2009-08-24
I just installed Ubuntu 9.04 on my HP Pavillion Entertainment Notebook (bought in 2005) and I am trying to use an external HP dvd840 to read dvds since my laptop's dvd drive stopped working 3 years ago. I am very new to Linux, and I'm very unfamiliar with how it works.  

When I plug the dvd drive in, nothing happens on the screen, but the dvd drive makes all kinds of whirling noises and will not eject the dvd when i hit the button.  When i unplug the USB, a window comes on the screen and says that it was unable to mount.  Is this a compatability issue, or is there something I can do to make this work?

Thanks so much!

---

### Post by cariboo on 2009-08-24
Open an Applications-->Accessories-->Terminal and type:

```
dmesg | tail -n15
```

After you have plugged in your external drive in, wait about 15 seconds, then type the above command. you should get something that looks like this:

```
scsi 0:0:0:0: Direct-Access     WDC WD80 0JB-00JJC0       0811 PQ: 0 ANSI: 0
sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
sd 0:0:0:0: [sda] Test WP failed, assume Write Enabled
sd 0:0:0:0: [sda] Assuming drive cache: write through
sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
sd 0:0:0:0: [sda] Test WP failed, assume Write Enabled
sd 0:0:0:0: [sda] Assuming drive cache: write through
 sda: sda1
sd 0:0:0:0: [sda] Attached SCSI disk
sd 0:0:0:0: Attached scsi generic sg0 type 0
```

The above output is for an external hard drive but the output should be similar, note what the device drive label is, in the above example it is /dev/sda1, for a cdrom/dvd drive it should be something like /dev/scd0.

Once you know the drive label, you can mount it by typing in the same terminal;

```
sudo /dev/sdc0 /media/cdrom
```

Chnage the above drive label to the reult you get. Don't worry about the cdrom part as Linux sees a dvd or cdrom as the same device.

---

