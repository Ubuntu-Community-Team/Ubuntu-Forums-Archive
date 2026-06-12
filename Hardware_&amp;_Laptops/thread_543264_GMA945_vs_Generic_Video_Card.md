---
title: "GMA945 vs Generic Video Card"
date: 2007-09-04
forum: Hardware &amp; Laptops
---

### Post by norrafi on 2007-09-04
I'm using Compaq nx6310 & just installed ubuntustudio. My problem is, I cannot changing  resolution other than "1024x768". Just followed this forum: [http://ubuntuforums.org/showthread.php?t=417220](http://ubuntuforums.org/showthread.php?t=417220) , but not lucky at all. 

Why my xorg.conf state "Generic Video Card" instead of "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller".?

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24

---

### Post by softtower on 2007-09-05
You need to get GMA945 driver and configure xorg.conf to use it. I do not have that card and cannot give you more detailed instructions. Try searching google. 

Good luck

---

