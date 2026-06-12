---
title: "FAT32 mount problem"
date: 2005-10-18
forum: Hardware &amp; Laptops
---

### Post by ohzopants on 2005-10-18
This is not really a laptop specific issue but I didn't know where else to post this, so here goes:

I dual boot Ubuntu 5.04 and Windows XP and have a big fat32 partition that I share between the two.  Sometimes when I save a file to this partition from within firefox I end up with 0 byte files, other times it works just fine.  Here is the appropriate line from my fstab:

/dev/hda6       /Stuff          vfat    iocharset=utf8,umask=000  0     0

Other programs, such as Azureus and Limewire, have no problems whatsoever downloading to this partition.

Any help is appreciated.  If you need more info just ask.

Thanks in advance,
Graham

---

### Post by Leif on 2005-10-18
have you tried doing it without the iocharset=utf8 ? the rest looks just like mine

---

### Post by mlomker on 2005-10-18
That's odd.  [Here is what I use]("http://ubuntuforums.org/showpost.php?p=355988&postcount=8"), but it's strange that it's only Firefox.

---

### Post by ohzopants on 2005-10-18
thanks guys...

mlomker i used your fstab example, but now I get 2 zero byte files ?? this is just getting weird.  I doesn't happen for images, torrents or pdfs, but it does happen for zips, tars, debs and some other files (I haven't thoroughly catalogued which extensions cause problems yet...)

thanks again

---

