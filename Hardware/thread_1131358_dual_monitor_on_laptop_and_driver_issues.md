---
title: "dual monitor on laptop and driver issues"
date: 2009-04-20
forum: Hardware
---

### Post by plroit on 2009-04-20
Dear all,
Just a couple of days ago I have installed k/ubuntu on my laptop
so I'm kinda of an advanced noob, I'm studying CS in university
and we interact with Linux all the time in the computer labs.
I do have many unresolved issues though.
My laptop is a Thinkpad T60, model 1952DU7.
Its supposed to come with the Intel 945 Express chipset and
950 graphic accelerator (I'm sure about the numbers, I may have a missing G or GM appended to the number, as in 950GM, Lenovo site doesn't provide too many details about the model).

I also own a second monitor, a Samsung syncMaster 2253BW
Its native resolution is 1680x1050

However, for starters, I think my k/Ubuntu version 8.10 doesn't recognize neither of them.
here's all my Xorg.conf file:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2384 768
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

As you can see, all very standard, very default identifiers.
my first problem is to install the correct drivers,
my second problem is to make my dual display settings work!

I attach a link of a related thread (related to the second problem, only with slightly different params.. however, no driver problems)
[Second problem advisory]("http://ubuntuforums.org/showthread.php?t=451719")

Thanks!

---

