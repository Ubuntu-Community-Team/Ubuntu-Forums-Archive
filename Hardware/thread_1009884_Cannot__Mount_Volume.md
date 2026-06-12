---
title: "Cannot  Mount Volume"
date: 2008-12-13
forum: Hardware
---

### Post by Ferkahhan on 2008-12-13
Okay, I have a Dell Inspiron 1525 and the hard drive recently went Kaput on me.

Got meself a new one and decided to betray the rest of my family and install Ubuntu on there (latest one)

Once installed, I tried putting a disk in the drive, but sadly I get a rather discouraging error message.

[I]**Cannot mount volume.**
Invalid mount option when attenpting to
mount the volume 'UDF Volume'.[/I]

And if left for a short while on there, I get something else.

[I]**Unable to mount UDF Volume**
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive ar reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired or the network connection was broken.[/I]

Maybe it's just my being stupid with Linux (as I've never used it before)... any assistance?

---

### Post by TheGuyWhoGotOn on 2008-12-13
Have you tried a different disk?

Am I correct in assuming that UDF is CD-RW/DVD-RW? Here is a little quote from Wikipedia of why a computer may not mount a UDF file and why I think you should try a different disk:

> 
Why a computer might not read a particular UDF disk

Even if a computer claims to be able to read UDF 1.50, it still may only support the plain build and not necessarily either the VAT or Spared build.

An example is Mac OS X (10.4.5), which claims to support UDF 1.50 (see man mount_udf), yet it can only mount disks of the plain build properly (it cannot mount UDF disks with a VAT at all, see Sony Mavica problem, and while it appears to be able to mount CD-RWs written with a Sparing Table, it does not read its files correctly in the case those files are actually remapped).


Also I know when I burnt a disk on Vista it never worked on my Ubuntu.

---

### Post by Ferkahhan on 2008-12-14
Yeah, I tried a different disk and it seems to work.
Sticking in burned CDs/DVDs doesn't seem to work at all ):

Sad.
Know any remedies for this?

---

### Post by vanadium on 2008-12-14
Vista has introduced new incompatibilities with their UDF support. That is why.

---

