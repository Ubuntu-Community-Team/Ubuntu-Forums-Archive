---
title: "Convert FAT32 to Ext2/3 no data loss?"
date: 2006-07-13
forum: Hardware &amp; Laptops
---

### Post by ironfistchamp on 2006-07-13
Is it possible with some program out there to convert my FAT32 to Ext2 or 3 without the loss of the data on it. I will nopt be able to back up all the data on it if not as there is too much.

Any help appreciated.

Thanks

Ironfistchamp

---

### Post by Radioactive Fellow on 2006-07-13
These filesystem are completely diferent so I dont think there is some software that does this. You will have to back up all you can and format the Fat32 partition if you want to convert it.

for ext2 ==> mkefs /partition/to/format
for ext3 ==> mkefs -j /partition/to/format

---

### Post by krazykirk on 2006-07-13
Yeah I don't think that's even possible.. your most likely option is to backup all your files somewhere and format to ext3

---

### Post by ironfistchamp on 2006-07-13
Dang I shall just hav to pick the most important files. Thanks anyway.

---

