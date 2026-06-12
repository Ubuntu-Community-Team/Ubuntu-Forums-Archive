---
title: "boot loader help with new install"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by gordong11 on 2009-10-01
I'm building a new PC and I want to use this configuration:

1. 64GB SATA SSD -For Ubuntu 9.04 install
2. 2TB SATA HDD - Ubuntu and Windows Split Storage
3. 64GB SATA SSD - For Windows Vista install

IS this config OK? or should I use 2 single 1TB drives(1 for each OS) for storage to make things easier? Any ideas? can someone point me to instructions for this kind of install with Grub?

Thanks so much

I'm guessing I'd install windows to SSD and HDD, then ubuntu to other SSD, then use Live CD partition editor to format HDD somehow?

---

### Post by zvacet on 2009-10-01
You can do it that way.Install Vista first on first drive (Windows like it that way) and Ubuntu on third.Windows file format NTFS Ubuntu ext3 (or ext4 because it will be default format soon) and storafe fileformat NTFS  so both OS can read/write.Maybe someone else have better solution.

---

