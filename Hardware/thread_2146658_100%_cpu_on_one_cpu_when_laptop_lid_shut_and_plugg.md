---
title: "100% cpu on one cpu when laptop lid shut and plugged in."
date: 2013-05-19
forum: Hardware
---

### Post by rabaggett on 2013-05-19
My Pavillion G7 goes to 100% cpu load on a random cpu (but usually number 4) when the lid is shut and on AC power. also understandably gets very hot. I have discovered the 100% cpu by leaving system monitor running while closing the lid, waiting a while, then opening it and checking the graph.

Any ideas? what should I check?

---

### Post by 2F4U on 2013-05-19
Can you give more details about your hardware? What graphics card and driver do you use? Since your machine is getting hot, a first guess would be the graphics card, but it could also be dust inside the laptop case or something else blocking the fan.

---

### Post by rabaggett on 2013-06-06
AMD A6-3420M APU with Radeon HD x4 graphics. Vesa SUMO
3,3 G memory, 500 G HD
The heat is not the main problem. After I open the screen, and the CPU returns to normal, it cools right down. In the time it took me to look up the forum and write this, it has gone from blistering to just warm. There is no blockage. this thing is like a heat gun when the lid is closed, or I do something else processor intensive like rip video or do a G-code depth map.

---

### Post by Cvxcvgg on 2013-06-06
Could it have something to do with suspension? I've never really seen this, but maybe the computer uses its CPU to remember where you left off in some way. My guess is that it's your CPU either way, since it also gets very hot during more intensive processes. Let's see what 2F4U thinks, though.

---

### Post by rabaggett on 2013-06-06
I suspect it does. When the laptop is unplugged, closing the lid will trigger a normal suspend.

---

### Post by rabaggett on 2013-06-09
Just upgraded to 13.04. Problem GONE!

---

