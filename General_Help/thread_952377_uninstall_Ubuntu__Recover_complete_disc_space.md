---
title: "uninstall Ubuntu / Recover complete disc space"
date: 2008-10-19
forum: General Help
---

### Post by wordlife on 2008-10-19
I had installed Ubuntu over 20 GB HDD partition on my 120 GB HDD. Then installed Windows Vista on another 20 GB partition. Now after installing that displays only 100 GB. Even when I try to partition using the Ubuntu disc, it doesn't display the missing 20 GB either. I now want to completely format and recover my additional 20 GB HDD Space. What do I need to do to uninstall Ubuntu / Grub? I want it to again display me 120 GB Free disc space completely.

---

### Post by geirha on 2008-10-19
It sounds like you already got all space available for windows now. It is common that the reported drive capacity (120 GB in your case), is higher than reported in windows and linux. This is because harddrive manufacturers measure size in decimal units, while operating systems prefer binary units. [http://en.wikipedia.org/wiki/SI_prefixes#Computing](http://en.wikipedia.org/wiki/SI_prefixes#Computing)

---

### Post by wordlife on 2008-10-19
> **geirha said:**
> It sounds like you already got all space available for windows now. It is common that the reported drive capacity (120 GB in your case), is higher than reported in windows and linux. This is because harddrive manufacturers measure size in decimal units, while operating systems prefer binary units. [http://en.wikipedia.org/wiki/SI_prefixes#Computing](http://en.wikipedia.org/wiki/SI_prefixes#Computing)

No actually to be clear on being precise there was some 5 GB less from 120 GB... I am discussing as from the previous state as that was around some 115+ GB but after installing even that space has got blocked. Now there is some 90s GB.
Please note, I have installed Vista without Uninstalling Ubuntu so Ubuntu actually still remains. The partitioning was done using EasyBCD and now the GRUB boot loader is never detected.

---

### Post by geirha on 2008-10-19
Ah, and you are wondering why the ubuntu partition isn't showing up in windows? Ubuntu is using ext3 filesystem, which windows doesn't support. You can install a driver to be able to access it though. However, if you're not going to be using ubuntu, you might as well remove that partition and resize your windows partition. I'm not very familiar with partitioning software for windows, but if you still have your ubuntu cd, boot it and run System -> Administration -> Partition editor to remove the ubuntu partition(s), and either resize your windows partition, or create a new windows partition. From what I understand, EasyBCD does not do parititoning, it just edits windows's boot manager.

---

