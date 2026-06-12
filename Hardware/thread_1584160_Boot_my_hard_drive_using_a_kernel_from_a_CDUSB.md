---
title: "Boot my hard drive using a kernel from a CD/USB"
date: 2010-09-28
forum: Hardware
---

### Post by noamr on 2010-09-28
Hello,

Is there a way to boot into my system using a kernel on an installation CD/USB? I see instructions over the internet that say to use "boot: rescue" from the boot prompt and follow the instructinos, but it seems that this feature has been dropped. It's even not available in the "ubuntu rescue remix"!

An apology: I think that that's what I need to solve my problem that I posted about an hour ago (and got no answer). I think that the new title better describes what I need.

Thanks,
Noam

---

### Post by noamr on 2010-09-29
Ok, I finally managed to do that.

I copied the initrd.lz and vmlinuz files from the /cdrom/casper directory to the hard drive, and edited the GRUB lines to use these files instead of the installed kernel.

I really wish there have been an easier way.

---

