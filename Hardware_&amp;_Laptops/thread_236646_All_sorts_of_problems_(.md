---
title: "All sorts of problems :("
date: 2006-08-15
forum: Hardware &amp; Laptops
---

### Post by Rainz3 on 2006-08-15
Alright, where to start. I have an acer travelmate 4400. I installed ubuntu without a hitch really. Only 2 problems wireless didnt work and my screen was only 1024x768(should be 1280x800).

I did some research and I edited my /etc/X11/xorg.conf to

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection
```

Now when I start up it loads then gives an error. I will get exactly what it says in a min. I fogot to write it down. Is there a way to change it back to default or fix this so I can have 1280x800?

Wireless, I cannot say much about this as I havnt touched this issue yet but it is a broadcom. It detects the card but thats as far as I have gotten(any advise on getting it to connect?)

and finally I noticed this while I was browsing firefox and other  programs its really laggy. As in my cpu is running at 800mhz not the full amount. Is there a way to check that? If I am right then what can I do about it? Thanks in advance!



[edit]The error it gives is "Failed to start the xserver(your graphical interface)would you like to view the server output)

any clue?

[edit again] Ok I was able to get back into ubuntu using the dpkg-reconfigure xserver-xorg and going through that process. But, still dont know how to get it into 1280x800

---

### Post by spd106 on 2006-08-15
It's worth downloading all the updates to remove any known bugs (download 6.06.1 cd if you can't connect to the servers directly), then perhaps install the graphics card driver (nvidia or ati fglrx), there are many guides for this in the forum, try the howto section.

Are you using the Dapper 64 bit edition? If so there will likely be problems with drivers as not all hardware has 64 bit support yet.

For the network card it's still probably best to use ndiswrapper with broadcom chips. Once again there are plenty of resources on this.

---

### Post by Rainz3 on 2006-08-15
Well I tried to install the ati drivers on ati's website but it starts then gives an error. All it says is "there was an error in installing this driver" And the first thing I did was check for updates. It's all fully updated. No its the 32bit version. Thats atleast the version I thought I downloaded(now I am starting to doubt it. whats the best way to find out? I will work on the network issue now while I take a break from this problem.

---

