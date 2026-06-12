---
title: "RAM missing"
date: 2010-01-15
forum: Hardware
---

### Post by lsutiger on 2010-01-15
I built a new system, specs in signature.
Only 3276MB of the RAM is being acknowledged out of 4GB. The board is equipped for 16GB. 

Any ideas?

---

### Post by Revolutionary101 on 2010-01-15
Some of the RAM is reserved for the graphics card.

---

### Post by Fire_Chief on 2010-01-15
Odds are you installed a 32-bit version of Ubuntu. This is limited to addressing a systemwide total of 4 GB of memory. This includes system RAM and video RAM.
If you have 4 GB of system RAM and a 1GB video card, then a 32-bit OS will report 3 GB usable of system RAM.

The 64-bit version of Ubuntu (or any other OS) is not limited to this and can address more than 4 GB of memory.

Cheers!

---

### Post by lsutiger on 2010-01-15
It is the limits on 32 bit OS's. I forgot about that.

The video card has it's own memory on the video card, and I disabled the video on the mother board.

Awww shucks. How are the 64 bit apps and Ubuntu out there these days? I remember having 64 bit installed a few years back and it was awful (windows), and I tried 64 bit ubuntu, but do not remember liking it much.

---

### Post by shadysamir on 2010-01-15
I just installed 64bit karmic and I'm very pleases with the performance. Check the list of apps that you use most and that are important to you and see if they provide 64bit versions. I just found out that Gizmo does not provide 64bit version for example :(

You will also have to install flash plugin from adobe labs for 64bit

---

### Post by Fire_Chief on 2010-01-18
Recent reading from 64-bit Ubuntu users suggests it is very stable now and nearly everything works. The holdup for myself includes no 64-bit version of Adobe Air Framework (yeah, I know it's a dog anyway but I love Tweetdeck).
The other note is to install the latest beta of the Adobe flash client to get top notch performance out of flash on 64-bit.

Cheers!

---

### Post by Kevbert on 2010-01-18
It's a historical problem in hardware (no-one will ever need that much memory). I'm using 64 bit Ubuntu on two different make/model PCs and it's fine. If you need to use 32 bit use the Ubuntu Server Edition as that supports [[COLOR="Red"]PAE.[/COLOR]]("http://en.wikipedia.org/wiki/Physical_Address_Extension")

---

