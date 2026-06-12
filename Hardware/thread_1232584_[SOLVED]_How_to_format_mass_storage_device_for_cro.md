---
title: "[SOLVED] How to format mass storage device for cross-platform recognition?"
date: 2009-08-05
forum: Hardware
---

### Post by QuizasQuizas on 2009-08-05
Hello, all!

Googling this has proven surprisingly unfruitful, so here I am in the forums - what's the best file system format for cross-platform readability of, say, an external hard drive being used for mass storage? (Assuming cross-platform recognition is even an option; I don't really *need* Mac support, but it'd be nice, if at all possible).

Thanks in advance for your input!

---

### Post by hetx on 2009-08-05
FAT32 is a common choice for cross-platform compatibility.

---

### Post by ugm6hr on 2009-08-05
> **hetx said:**
> FAT32 is a common choice for cross-platform compatibility.

And is the standard for most USB / SD storage devices.

NTFS tends to be default for external HDs, due to its capacity for 4GB+ files (which fat32/vfat lack).  NTFS support is excellent with MS, good with Linux, but I believe read-only on Macs as default (uncertain re: Macs).

---

### Post by QuizasQuizas on 2009-08-05
Alrighty, then. Thanks!

---

