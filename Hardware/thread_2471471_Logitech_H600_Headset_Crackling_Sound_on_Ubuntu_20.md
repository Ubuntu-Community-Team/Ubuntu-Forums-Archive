---
title: "Logitech H600 Headset Crackling Sound on Ubuntu 20.04"
date: 2022-01-31
forum: Hardware
---

### Post by Tsela on 2022-01-31
Hi everyone,

I hope someone can help me this time, as this problem is infuriating.

So two years ago I posted [this issue]("https://ubuntuforums.org/showthread.php?t=2436224") with my Logitech H600 headset. At the time, I was running Ubuntu 19.04 on my desktop computer, so I got no help besides a request to upgrade. I eventually upgraded to Ubuntu 20.04, and that somehow made the problem go away. Except that the very same problem has reappeared since last week.

Basically, for the past two years I had been using my Logitech H600 headset with my desktop computer without a problem, and suddenly since last week when I use it the sound keeps crackling and breaking. It is worst with online videos and especially Youtube, which is basically unwatchable. Local videos have crackling as well, though slightly less than online ones. Music and Steam games are the least hit by the problem, although the sound does crackle with those as well, just less often.

I've looked online (again) for a solution for that problem, but once again I cannot find anything that helps me. I run Ubuntu 20.04 LTS fully updated on my desktop computer. I use the H600 on my work laptop as well, where it works fine, with no sound issues at all, so I know it's not a hardware issue with the headset itself. I've tried plugging the nano receiver from the headset to a different USB slot, to no avail. I've switched the output to the headset from Digital Out to Analog Out in the Sound Settings, which reduced the crackling a bit but only marginally. I've tested the sound from my Ubuntu computer on the two other outputs it has available (a Line-Out with a 9mm connector and a screen connected via HDMI to the GTX 1050Ti graphical card). Both give a perfectly good sound with no issues at all (but I can't use them -I have to keep it quiet here so I can't use the sound from the screen, and the only headset I have with a 9mm connector has too short a cable, I had to kneel in front of my computer tower to be able to test the Line-Out). So I know the problem isn't inherent to my desktop computer either.

So the headset works perfectly fine when plugged in another computer, and my Ubuntu desktop produces perfectly fine sound when using a different output. It's only when my headset is plugged in to my desktop that the crackling happens. And that after nearly two years of working perfectly fine!

Anyone has any idea what the problem might be, or at least how I can diagnose what's going on? It's really annoying, the crackling is noisy enough to hurt my ears sometimes, and the worst of it is the randomness of it all, happening suddenly without warning after two years without issues.

Thanks in advance!

---

### Post by schachschal on 2022-04-01
I have a very very similar issue with a Jabra Evolve 75 headset (connected directly or via Jabra Link 370) on Ubuntu 20.04. Since about a week it suddenly started crackling whenever the microphone gets activated. Everything is fine, e.g. when watching youtube video, but as soon as some application activates the micro, sound starts crackling. And it's already enough to start pavucontrol which activates micro.
First I assumed the device itself is broken. But unfortunately it's working fine at another windows machine. I also tried same headset model from colleague on my machine, and it also has same crackling there. A different wired headset is working completely fine.
I already tried several suggestion from what you can find on internet (reset pulseaudio, reset alsa, reinstall kernel, ...) without success.
Has there been some changes in kernel or audio packages just recently?

Edit:
For me it turned out to be caused by kernel 5.13.0-37. Also some other people have [similar issues]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1967995"). With previous kernel 5.13.0-35 everything is fine.

---

