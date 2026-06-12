---
title: "Argh my ears! Sound problems"
date: 2008-11-21
forum: General Help
---

### Post by Monotoko on 2008-11-21
Hiya, i have just today recieved my Intrepid Ibex disk in the post after requesting free delivery. I decided to see how it worked, and booted into LiceCD mode to have a little look around.

I like it, seems to finally like my wireless without disconnecting every 10 minutes like it did in Hardy.

I'm just having one problem, and its to do with my sound, anything that comes from it, whether it be my speakers, or my headphones, sounds grainy and horrible, and is unlistenable, what the heck could have caused this?? It works fine in 8.04 :confused:

Thinking it mightve been my disk, i put it in my old PC (256 ram, has windows 98 installed :lolflag:) and the sound from that worked awesomely.

So i thought id try Kubuntu 8.10 as 8.04 worked on me before now. It gave the same results, awful, grainy sound, yet 8.04 worked.

Finally i tried the new (testing) linux Mint, which is based off Intrepid Ibex, and again it gave the same result.

The laptop in question is a Fujitsu Siemens Esprimo Mobile V5055
Sound works on 8.04 but sounds awful in 8.10, any ideas?

---

### Post by Monotoko on 2008-11-21
Anyone? Im in a linux forum and no-one has any ideas at all?? :confused:

---

### Post by Monotoko on 2008-11-21
can i at least have a command or something that would diagnose my sound issue?

EDIT: It also plays sound even though the volume is muted, can someone please help me?

---

### Post by Monotoko on 2008-11-21
I appear to have found the problem, when i right-click the volume icon in the task bar then click "Open volume control" it shows me 3 bars, master, PCM and ext-mic.


After fiddling with the master and finding there wasnt much differance, i tried messing with the PCM bar, PCM appears to be the problem, if i turn that right down to a really low level, all the sound seems perfect (just too damn quiet) if i turn it up, everything sounds grainy and horrible.

Whats PCM and why is it doing this? :confused:

---

### Post by TransitMan on 2008-11-21
From [http://en.wikipedia.org/wiki/Pulse-code_modulation](http://en.wikipedia.org/wiki/Pulse-code_modulation) ,

Pulse-code modulation (PCM) is a digital representation of an analog signal where the magnitude of the signal is sampled regularly at uniform intervals, then quantized to a series of symbols in a numeric (usually binary) code. PCM has been used in digital telephone systems and 1980s-era electronic musical keyboards. It is also the standard form for digital audio in computers and the compact disc "red book" format. It is also standard in digital video, for example, using ITU-R BT.601. However, uncompressed PCM is not typically used for video in standard definition consumer applications such as DVD or DVR because the bit rate required is far too high.

---

