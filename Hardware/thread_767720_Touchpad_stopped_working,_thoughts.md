---
title: "Touchpad stopped working, thoughts?"
date: 2008-04-25
forum: Hardware
---

### Post by tylersontag on 2008-04-25
I just upgraded to the final release version of Hardy Hareon from 7.10 on my Dell ubuntu Inspirion 1525n and i was all set. The compiz team fixed it so i could watch movies and have my cube, had everything working perfect. I even was able to turn on a screensaver, since the video problem had made that impossible.

So the first time it kicks into screensaver mode i look over, i have it on "Flocks" and its running smooth and looking amazing it had been running a while but i was so mesmerized i just stared for a few seconds talking to a friend of mine. Then the screen locked up with in a multicolor static. I tried switching to terminal 1 or 2, couldn't system was completely locked up so i had no choice but to cold boot it.

When i turned it back on, the touchpad would not work, everything else seems fine, i plugged in my USB mouse and it works. The buttons on the touch pad work, just not the pad itself. I don't understand what could have broken it. Any ideas?

heres hte pertaining lines of my xorg file


```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
```

---

### Post by |{urse on 2008-04-25
if you had a muticolored glitch beforehand i'd say something either fried or came loose and x crashed. try finding a disassembly manual for your laptop model and make sure the small ribbon for your touchpad is securely in its zif socket.

---

### Post by tylersontag on 2008-04-26
i stand here as it is now. I had shut down my laptop and went to the bars. when i came back my touchpad worked and i was ecstatic. i had shut down and left my laptop off a few times to see if it fixed it, but not.  As  im puzzled that a 4 hour binge fixes my problem.  but apparently 4 hours was enough to reorient my touchpad to work again.  that is all i can say as far as my fix.  and im sorry i brought this situation to everyones attention when all it needed was a rest.  

however, for future reference i might like to bring this to the attention of the devs.  though im currently a senior in CS, im puzzled as to the reason for my problem.  it seemed like a hardware problem but could only have been a software problem. we had a crach -> cold boot: that led to a failure of the touchpad. i would have logged it had i knew it was coming, but hindsight is 20/20.  Is there any stack logs or something comparable i could send to some devs? also, is there anyone with a specific task to monitor such bugs?

Thanks.

---

### Post by |{urse on 2008-04-28
great! Glad things are working again, Sometimes we get lucky. :guitar:

---

