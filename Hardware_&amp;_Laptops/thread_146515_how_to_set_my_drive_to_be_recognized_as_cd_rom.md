---
title: "how to set my drive to be recognized as cd rom"
date: 2006-03-18
forum: Hardware &amp; Laptops
---

### Post by sulien on 2006-03-18
finn@ubuntu:/etc$ dmesg | grep hdc
[4294674.012000]     ide1: BM-DMA at 0x10a8-0x10af, BIOS settings: hdc: pio, hdd: DMA
[4294675.261000] hdc: , ATAPI cdrom or floppy?, assuming FLOPPY drive
[4294732.613000] ide-floppy: hdc: not supported by this version of ide-floppy

for some reason it sees it as a floppy how can i change that? also it seems not to recognize a filesystem type and says it's not specified. Help? :-k

---

