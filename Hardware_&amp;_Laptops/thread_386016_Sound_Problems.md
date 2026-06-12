---
title: "Sound Problems"
date: 2007-03-16
forum: Hardware &amp; Laptops
---

### Post by tylersontag on 2007-03-16
I've gone around these forums a few times 3 months ago when i first got my laptop and did some tinkering but not with much results.  So i figured living with my sound problem was less of a hastle than fixing it.  but i'm getting sick of my laptops sound problems so i'm gonna go back out on a limb.

There are 2 problems, potentially stemming from the same root.  The most annoying is my sound mixer not working, i can't hear more than one sound at the same time from different programs.  so if firefox is playing away andi start up kaffiene its says "Xine Player not found".  Close firefox, restart kafifene, works.

The other problem is sound simply won't work about 1/8th of the times i start up and almost every time i return from hibernation.

could i need some new sound drivers?

I'm runnign an 82801G Intel sound card.

my .asound file contains the following 

```
pcm.!default {
	type plug
	slave.pcm "dmixer"
    }

 
    pcm.dmixer  {
	type dmix
	ipc_key 1024
	slave {
	    pcm "hw:1,0"
	    period_time 0
	    period_size 1024
	    buffer_size 4096
	    rate 44100
	}
	bindings {
	    0 0
	    1 1
	}
    }
 
    ctl.dmixer {
	type hw
	card 0
    }

```

Any finger towards a good resource or help at all would be greatly appreciated.

---

### Post by Scunizi on 2007-03-16
I'm not sure if this applies, but when I have Gizmo loaded NOTHING else will play a note.  I have to close Gizmo and then killall esd before anthing will work correctly.  I'm on dapper.

---

