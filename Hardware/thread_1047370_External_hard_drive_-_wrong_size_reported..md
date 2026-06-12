---
title: "External hard drive - wrong size reported."
date: 2009-01-22
forum: Hardware
---

### Post by Fedora314 on 2009-01-22
Hello all,

I've just finished reformatting my 1TB Western Digital MyBook USB hard drive into ext3 using a gparted live cd. Everything went fine, and the drive is ready to use - except for one problem - I'm missing some space on the drive.

The output of fdisk is as follows:

```
fedora@Serenity:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

```

Because there are no files on the drive, I would expect there to be about 1TB of free space on the drive. However, gparted reports a drive size of 931.51GB with 7.53BG of that used... Nautilus reports that only 877.4GB are free.

Where is my hard drive space? Any help would be greatly appreciated.

Cheers,
Jeremy

---

### Post by Fedora314 on 2009-01-28
Anyone have any thoughts? 

I thought it might be a base 2, base 10 problem - but would the space actually show up in Nautilus as "used" if that were the case? I figured it should show an empty, but smaller drive.

Cheers,
Jeremy

---

### Post by WakkiTabakki on 2009-03-23
Sorry, this is just another "me too"-post...

Just bought an external Samsung S2 USB disk. 500Gb formatted to ext3 and...
df reports:
/dev/sdb1             459G  199M  435G   1% /media/Samsung
(this in itself is quite interesting... 459Gb - 199Mb = 435Gb???)

Nautilus reports:
435Gb free and 23.5Gb used



Can anyone shed some light?

/N

---

### Post by megamania on 2009-03-23
> **WakkiTabakki said:**
> 
Nautilus reports:
435Gb free and 23.5Gb used

It's probably system-reserved space. **IF that's the problem**, with:

sudo tune2fs -m 0 /dev/hda *(or whatever you drive is)*

you will get this space back. 

Note that the tune2fs man page says that you shouldn't use it on a mounted hd. I used it on a mounted hd and it worked, but do so at your own risk. 

I'm not at home now, so I can't help further. If you check google or the forums for something like "tune2fs reserved space" you should find the answer.

Hope that helps.

---

### Post by WakkiTabakki on 2009-03-26
I just checked the man-page for tune2fs, which states:
> [...]Normally, the default percentage of reserved blocks is 5%

And 5% of 459Gb incidentally is almost exactly 23Gb, so it makes sense. It also says that it keeps this space to avoid fragmentation and stuff, so I'll just leave it reserved I think...

Thanks for the reply!

/N

---

