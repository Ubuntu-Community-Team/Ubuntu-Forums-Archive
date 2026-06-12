---
title: "Format External HDD for mac and Ubuntu use"
date: 2015-12-27
forum: Hardware
---

### Post by St_Vi on 2015-12-27
Hi There!

I Have an External HDD (2gig) and need it to transfer data fome one pc to the other (mac and Ubuntu).
I tried formatting it to NTFS on Ubuntu, but it keeps telling me it only as Read privileges.

My question is "how can i tur this Drive into a almigthy Drive that i can use with all my computers?"

I looked at the properties

Owner is Me
access; create and delete

Grope:  "my name"
Access: Create and Delete

other:  is blanc
Access: Create and delete
But when i look at the Change Permission for enclosed files, other is Read only????? and changing it does nothing????


Thanks in advance

---

### Post by weatherman2 on 2015-12-27
FAT32, not NTFS, would work anywhere, read and write.  Downside: no files larger than about 4.1GB can be stored, and no journaling.  FAT32 is now quite old too.

NTFS will work read and write on Ubuntu (unless you are using an old, unsupported version) but read-only on a Mac as I recall, unless you find a way to tweak it.

ext2 - older native Linux format - will also work on a Mac if you install something for it.  ext4, the last time I tried, was not supported anywhere on a Mac at least not easily.  ext2 is a decent filesytem but it does not have any journaling (which can help protect the filsystem from corruption in case of an accidental shut down or something).

There may also be a way to use Mac format - easily readable in Ubuntu but last time I tried it was hard to get writing to work (at least, I gave up after trying some of the easier suggestions I found).

I think if I were doing it now I'd go with ext2 after making sure I could install the driver on a Mac and that that worked.

---

### Post by St_Vi on 2015-12-27
Thank you for the speedy reply.

What baffles me is i have a second HDD that i use, when i look at it from my mac and Ubuntu, it looks identical to the one im trying to use now, but i can write and read on both systems.

mac says it's Ntfs (and i can write on it same with Ubuntu
???

---

