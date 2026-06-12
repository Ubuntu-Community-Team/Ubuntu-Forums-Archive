---
title: "Dell P990"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by brickbat on 2005-04-10
Hi, my monitor was detected as an "ULTRASCANP99" but it is actually a Dell P990.

I made cnanges to the xorg.conf file.  It looks like this;

Section "Monitor"
	# Identifier	"ULTRASCANP99"
	# Option	"DPMS"
	# HorizSync	30-98
	# VertRefresh	48-120

	Identifier "Dell P990"
	Option "DPMS"
	HorizSync 30-96
	VertRefresh 48-120

Section "Screen"
	Monitor		"Dell P990"

I now don't know if it has accepted it but the problem which is the fact that my screen resolution keeps returning to 1280x1024 is persisting.

HELP PLEASE!

ciao
bb

---

