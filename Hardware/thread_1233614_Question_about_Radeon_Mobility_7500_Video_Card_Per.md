---
title: "Question about Radeon Mobility 7500 Video Card Performance"
date: 2009-08-06
forum: Hardware
---

### Post by murderslastcrow on 2009-08-06
Well, after I upgraded to Jaunty, I started using my compiz to a fuller potential. However, it was having a few slow-downs when using AWN and the desktop-changer applet. Like, wouldn't show transitions and the desktop would momentarily freeze.

I fixed that by reverting to XAA acceleration in xorg.conf, and adding a few more options, listed here.

[I]Section "Device"
	Identifier	"Configured Video Device"
	Option "AGPMode" "4"
	Option "AGPFastWrite" "on"
	Option "EnablePageFlip" "on"
	Option "DynamicClocks" "on"
	Option "AccelMethod" "XAA
EndSection[/I]

So, I'm pretty well satisfied, except that I'm on a machine with a 1.6 Ghz processor and 1 GB of RAM, and I recently installed Ubuntu on a computer with a 800 Mhz Processor with 300 MB of RAM and its graphics card seems to react better with some things (like maximizing/minimizing windows snappier). So I know it's something with the video card drivers or something that provides me with a somewhat less snappy compiz experience.

I just wanna' get the most of my video card, you know?

However, it seems that ATI doesn't release drivers for this model on their website. I have done some research, and it seems that most of these issues with be resolved when we get the 2.6.30 kernel in Karmic, and the newer Xorg-server, but I just don't wanna' wait.

When I go to hardware drivers, there's nothing listed, so I'm assuming I'm using the open source drivers for this card. I wouldn't mind going proprietary for the next few months, though. So does anyone know of any extra options for xorg I could use or a different driver that could provide me with better results? If not, I guess I can wait until October.

---

### Post by gradinaruvasile on 2009-08-06
There are no proprietary drivers for that card. And i dont know if it ever will be any improvement cause its an old model and all of its features (AFAIK) all supported already. I have one too. But i dont use compiz on it (it works well though).
I would suggest replacing AWN with cairo-dock. AWN seems to me to be a real resource hog... I use cairo-dock without opengl rendering (-c command line switch) and works excellent, low cpu and ram usage.
And might try the newer radeon drivers from

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

---

### Post by murderslastcrow on 2009-08-06
Thanks. I'll definitely get that PPA going in a few minutes to see if there are any improvements. Also, I noticed cairo-dock is a lot snappier, so I hope I can get around all of the extra features and understand the configuration wizard a bit better, because it seems like a better choice.

I'll report back with my findings.

---

### Post by gradinaruvasile on 2009-08-06
Dont forget to launch it with the -c switch. While the default opengl mode is flashier, it uses lots of memory.

---

### Post by murderslastcrow on 2009-08-07
It kinda' helped, to get the new drivers. But eh... I think I should be satisfied, since it's faster enough. XD

I'm getting another 2GB or more PC soon, anyway, so this'll do for now. :3 I love milking my computer for all it's worth (my favorite part of using Linux, despite the freedom and amazing applications).

---

