---
title: "flickering screen with Karmic &amp; sis mirage graphic card"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by alicemoon on 2009-11-01
I have had this problem before with Hardy and solved it by editing the xorg conf file - with upgrades to ibex and jaunty the problem did not reoccur but a fresh install of karmic brought the lines back.
Having looked through the forums I found karmic does not have an xorg conf file but you can create one - for anyone suffering the same problem here is what I did

in terminal type

sudo nano /etc/X11/xorg.conf

in the file type

Section "Device"
	Identifier	"Configured Video Device"
driver "vesa"
Endsection

save the file.
close everything down and reboot and hopefuly like me you will get a nice clean screen.

---

