---
title: "Grub error 18 on new machine"
date: 2007-01-06
forum: Hardware &amp; Laptops
---

### Post by urinetrouble on 2007-01-06
Hello.

I'm getting a grub error 18 on boot with my Ubuntu Dapper
installation. No idea why, and it's starting to get to me... The thing
with error 18 is that it usually refers to the fact that you're
dealing with an older motherboard and that the BIOS can't handle a
larger drive. However, this error popped up out of nowhere on my IBM
thinkpad G41 from 2005, which makes no sense... Why would GRUB have
issues loading the kernel from a drive that the BIOS can read just
fine? Why would this error happen at all on a newer machine? I can't
even boot to the hard drive because the grub menu won't pop up.
Sometimes it boots into the network card's PXE instead for some weird reason. The only
solutions listed for this error that I can find refer to ancient computers, but not this one. There's another fellow with a thinkpad T something or other that never had his problem adressed.

My partition table from memory looks something like this:

```

/dev/hda1 - NTFS, 30gigs
/dev/hda2 - ext3, 60 gigs or so
/dev/hda3 - Swap space.

```

What can I do? I hope my drive isn't blitzed :-k

edit: well, that post rendered weirdly. Sorry for all the whitespace :|

---

