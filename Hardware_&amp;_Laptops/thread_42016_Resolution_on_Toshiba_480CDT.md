---
title: "Resolution on Toshiba 480CDT"
date: 2005-06-15
forum: Hardware &amp; Laptops
---

### Post by dippa on 2005-06-15
After installing 5.04 my toshiba only dispalys in 640 x 480
Any ideas how to change it to 800 x 600 16 bit mode?

---

### Post by cowbud on 2006-04-22
This might be a bit late but I solved this one just now.

Section "Monitor"
	Identifier   "Monitor0"
	HorizSync    31.5 - 57.0
	VertRefresh  50.0 - 90.0
	Option       "DPMS"
EndSection

Hey at least it is in the forums now :) 

replace the video vert and horiz sync with those and add "800x600" in front of the "640x480" entry.

Moo

---

