---
title: "Two problems in 8.04"
date: 2008-04-26
forum: Hardware
---

### Post by grefa on 2008-04-26
1. I have optical fiber net access and the connection is made over pppoe. When I start pppoeconf, I get a "Bogus pppoe length field" error. Strangely, this worked just fine in 7.10.

2. The picture on my LCD display isn't completely centered (i.e. 
the picture is cut off on the right and there is a black stripe on the left. I used xvidtune to align the picture and then clicked
apply and show to get the modeline:

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Sony"
	Modelname	"Sony SDM-S71"
	Horizsync	28.0-65.0
	Vertrefresh	48.0-65.0
  modeline "1280x1024"   108.00   1280 1344 1456 1688   1024 1025 1028 1066 +hsync +vsync
	   
	Gamma	1.0
EndSection 

However, the picture is misaligned again when I restart X. What gives?

---

