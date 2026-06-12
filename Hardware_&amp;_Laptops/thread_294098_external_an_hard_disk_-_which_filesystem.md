---
title: "external an hard disk - which filesystem?"
date: 2006-11-06
forum: Hardware &amp; Laptops
---

### Post by carlstanford on 2006-11-06
Hi there,
I'm going to buy an external (200 gigs) hard disk for data storage.
I'm trying to understand which filesystem(s) to use, to have it easily be used in Ubuntu and Windows (both read and write).
I need at worse two 100 gigs partitions, mainly used for audio and video editing, hires photo storage, music, etc.
Should I use NTFS? Has Edgy a strong error free support for it?
Should I use Ext3?
How about EXT3 support in windows instead?

Thanks a lot

---

### Post by kidders on 2006-11-06
Hi there,

Personally, I would avoid FAT and NTFS. You can teach Windoze how to read Ext2 and HFS, either of which is a far better alternative.

However, if you want your external drive to work in other peoples' computers, FAT32 is pretty much your only choice :-(

---

### Post by sebastfr on 2006-11-06
If you don't need any fancy permissions on who reads/writes to it, go FAT32!! It's faster than ext2/3, ntfs etc. and any decent OS will support FAT32 natively (and the format has been thoroughly tested after all those years!)

For ext2 support on Windows, it's rather poor, you need a 3rd party driver... and imagine the pain if you need to install this driver any time you plug the drive to one of your friends' machine (assuming they use Windows ;))

go fat!!

Seb

---

### Post by kidders on 2006-11-06
I agree with sebastfr ... for compatibility, FAT is your best choice.

Having said that, it is terribly slow (especially when it fragments) and can make life quite awkward when you want to copy stuff onto it, given all the silly restrictions it places on filenames. If you don't intend to use your hard disk in other people's computers, I would try to avoid it.

If you *are* going to use it, be careful not to let your software give incompatible names to files you may later want to store on FAT. Only the other day, I answered a thread posted by a guy who now has to rename all his MP3s!

---

