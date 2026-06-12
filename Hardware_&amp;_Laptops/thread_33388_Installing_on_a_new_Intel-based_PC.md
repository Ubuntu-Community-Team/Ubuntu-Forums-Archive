---
title: "Installing on a new Intel-based PC?"
date: 2005-05-10
forum: Hardware &amp; Laptops
---

### Post by PCM2 on 2005-05-10
I suspect I know what the answer is, but I'll try here anyway. I have a fairly new Intel-based PC. I don't have it here to tell you exactly what the specs on the chipsets are, but it's a Sony VAIO RA830G with an Intel Pentium 4 550J processor and (if I'm not mistaken) and Intel Matrix Storage Hub chipset for the drives.

My experience trying to install Linux on it is as follows, so far:
* Ubuntu Warty: Boots to the installer, when detecting drives it says I have no CD-ROM drive. (It's sort of true; I have a DVD-RW and a DVD-ROM. Booting off either one has the same effect.)
* Ubuntu Hoary: Boots to the text scroll. The kernel gets as far as detecting all the card readers on the USB bus and then hangs up. Never makes it to the installer.
* Xandros Linux Desktop: Boots to a Lilo prompt, hangs.
* Novell Linux Desktop: Boots to a very nice installer, but when it gets to the point of partitioning it tells me (quite sanely, I thought) that I have no hard drives.

I think the last example is the key to the problem here. My machine came with two SATA hard drives in a RAID 0 configuration. I got rid of the RAID and reformatted, but to no avail. I just don't think Linux can understand my chipset. Does anyone have any advice to the contrary?

---

