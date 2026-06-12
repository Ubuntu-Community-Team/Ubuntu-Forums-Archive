---
title: "Uknown Monitor for Samsung SyncMaster 997DF"
date: 2009-08-28
forum: Hardware
---

### Post by maimoon on 2009-08-28
I have a 19" Samsung SyncMaster 997DF when I installed a fresh copy of ubuntu 9.04 I got "unknown monitor" message with a pink background. I tried everything modify the identifier to Samsung SyncMaster 997DF modifying the identifier to..

Section "Monitor"
	Identifier "Monitor0"
	VendorName "Samsung"
	ModelName "SyncMaster 997DF"
	#HorizSync 30-66
	#VertRefresh 56-85
	HorizSync 30-96
	VertRefresh 56-160
EndSection

I also tried formating it in a ext3 type but it was of no use.

---

### Post by zach4618 on 2009-09-11
I am having the same problem with a Benq FP747 monitor. The highest resolution I can achieve is 640x480. Not sure what I can do at this point...

---

