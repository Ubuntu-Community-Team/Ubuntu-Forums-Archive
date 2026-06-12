---
title: "HD image backup: what if I CUT the UPPER portion?"
date: 2010-12-03
forum: Hardware
---

### Post by spamhog on 2010-12-03
I normally back up my notebook's WHOLE 100GB HD.
I just use "dd" and it works marvelously.
No compression, no special imaging software etc..
[I FULLY KNOW THEY EXISTS AND THEIR ADVANTAGES]

Now I am moving to a 160GB HD, but imagine I'd like to keep backups to 100GB.

I think I could do this, e.g.:
dd if=/dev/sdx bs=100M count=1000 of=<path><image-filename>


When restoring a 100 gig image to a 160 gig HD, I think this would happen:

- MBR and partition table get restored, and the OSs know where partitions should be

- over 100 gig there'll be nothing or random FS structures

- any totally missing partition will be seen as unformatted, and each OS will be capable of formatting its own

[- if a partition is restored only partially, it's all chance depending on the filesystem etc.: it will be seen as borked, or unformatted or inconsistent but partly recoverable]

- the new UUIDs of reformatted partitions will have to be read and entered into fstab, if it is based on UUIDs


Thus, I could put all the temporary or noncritical stuff up above 100GB:

- Linux swap

- Windows partitions with the main virtual memory file and all the various temporary files folders

- any disposable data

- any mirrored data that can be easily restored, imap mirrors etc.



Is this correct?  I want to learn!

:confused:

---

