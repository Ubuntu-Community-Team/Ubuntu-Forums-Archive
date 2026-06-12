---
title: "&quot;No boot device detected&quot;"
date: 2014-03-11
forum: Hardware
---

### Post by alexfitzelgard on 2014-03-11
Hey everyone.
First of all, I don't know if this is the right category to post on. Sorry if it isn't
Ok, so here it goes:
When I boot my computer (that has UBuntu 13.10 on it), it displays "No boot device detected" but... when I insert my WIndows 8 installation disk and when I wait for the "Press any key to boot with CD or DVD" part to pass and not press any key, it just boots back into Ubuntu.
I have made tests and my hdd is failing. Also I think it's something to do with the boot order in the Bios.
Thanks

---

### Post by florinfinaru on 2014-03-11
Hi Alex,
Access bios menu by pressing the assigned key at the post screen. Go to Boot, every bios should have this tab, and make sure your primary boot device is set to the hard disk.

---

### Post by alexfitzelgard on 2014-03-11
thanks
yes the primary boot device is set to the hard disk, still the same problem

---

### Post by alexfitzelgard on 2014-03-14
help ???

---

### Post by oldfred on 2014-03-14
If Smart Status in Disks or Disk Utility show disk is failing, there may not be much you can do.
If drive will mount from Ubuntu live installer backup any data you have not backed up.

Why are you trying to boot a Windows installer? It will not see Linux partitions and unless you have a NTFS partition that has the boot flag, it will not see anything.
But if you do have NTFS partition you should try running chkdsk on it.

---

