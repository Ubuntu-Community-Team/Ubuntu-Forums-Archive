---
title: "[SOLVED] Defrag in dual boot?"
date: 2008-08-25
forum: Hardware
---

### Post by LieToPurify3 on 2008-08-25
I'm dual booting 8.04 and winxp.  I know ext3 doesnt need to be defragged, but obviously windows needs to be fixed constantly in some way.  If i defrag when i boot into windows, will it only defrag my ntfs partition, or the whole drive, and should i even do that?

---

### Post by cariboo on 2008-08-26
If you defrag your windows partition, that is the only partition it will affect. Windows can't really see an ext3 formatted partition so it won't defrag you Ubuntu partition.

Jim

---

### Post by LieToPurify3 on 2008-08-27
Oh true, I forgot about that.  Thank you!

---

### Post by s3a on 2008-08-27
You can defrag ANYTHING Linux can see (including your windows partition) INSIDE Ubuntu! It is a command line defragger called pyfragtools. You type sudo defrag _directory_ then follow instructions. Pyfragtools can be found at in my signature and somewhere in these forums if you use the search tool (that's where I got it from initially).

---

