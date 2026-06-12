---
title: "Dell 5100 External monitor"
date: 2005-12-28
forum: Hardware &amp; Laptops
---

### Post by sarmadzhiev on 2005-12-28
Hi all, 
I have an ugly problem. 
Setup:
Dell Inspiron 5100 
internal monitor max 1024x768
video is ati M7 (Radeon 7500)

I switch external monitor and after reboot its become the first one.

in xorg.conf I put the spec for it as only monitor 
 
Section "Device"
         Identifier "RADEON M7"
         Driver "ati"
EndSection


Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

I edit the modes as well and left is only 1280x768 for depth 24 and 16 and also put the default one to be 24

Still the X is only in 1024x768 mode. 

I want to mention it is going through KVM but the other machines seems OK and could handle 1280x1024

Any ideas what can I do, because the monitor is little fuzzy at 1024x768 and I hope it will be more stable at 1280x1024

---

