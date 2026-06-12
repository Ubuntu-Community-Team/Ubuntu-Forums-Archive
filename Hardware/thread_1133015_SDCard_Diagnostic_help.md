---
title: "SDCard Diagnostic help"
date: 2009-04-22
forum: Hardware
---

### Post by Roger E Critchlow Jr on 2009-04-22
My laptop has an memory card slot which is bootable so I've been trying to make an Ubuntu installation on an SDCard.  I'm putting a native linux filesystem on the card along with grub.  I'm using a 16G Toshiba SDHC memory card.  What I've read says that it should work just fine for the first 10-50K writes to the card.

What's happened a few times now is that I get the initial system installed, boot into it, go to do an update, using apt-get or synaptic, and end up with corrupted files.  In one case, apt-get began getting segmentation faults.  In another case, the tar's extracted from a deb file were identified as corrupted.

So the obvious conclusion is that the SDCard is defective.  But mkfs(8) with the -c flag found no problems with the card.  And badblocks(8)  with multiple write patterns found no problems.

So what do I try next?

Is this memory card defective?  Or is my use of it defective?

-- rec --

---

