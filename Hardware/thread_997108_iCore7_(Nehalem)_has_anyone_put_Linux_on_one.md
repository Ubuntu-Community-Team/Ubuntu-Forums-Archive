---
title: "iCore7 (Nehalem) has anyone put Linux on one?"
date: 2008-11-29
forum: Hardware
---

### Post by bjrosen on 2008-11-29
I'm thinking about building an iCore7 system, has anyone put any flavor of Linux on one? Which motherboard did you use? The MSI X58 Platinum looks reasonably priced (as far as X58 boards go) so I'm leaning towards that but I'm open to suggestions. The most important thing is Linux compatibility.

---

### Post by starfry on 2008-12-03
Hi, I am going to buy a new rig also and am interested in any thoughts about boards, graphics cards, etc.

I am thinking of the Asus board along with the Extreme CPU and 12Gb  Ram - i want to run several virtual machines.

---

### Post by loomsen on 2008-12-03
Intel provides a tool to update microcode after startup, overriding the one in your BIOS.

**sudo apt-get install intel-microcode microcode.ctl**

Hence the code is implemented after initial boot you'll have to write a startup script. 
run
**man microcode_ctl**
for more info

---

### Post by starfry on 2008-12-17
I've been speaking to a vendor about a new system and they commented that linux won't have drivers for the new chipset. Is this bull or is there any truth in it?

If I am going to spend upwards of £2000 on a system I expect to be able to run a 64 bit Ubuntu system flawlessly.

Can anyone report on successes/failures with the X58 core i7 ?

---

### Post by Sillywombat on 2009-01-07
Im guessing that no one has really tried and tested this yet.
We probably have to wait another week or two until the i7 & chipset stats come out for Ubuntu.

Hopefully it will be soon, Im also looking into a i7 machine (940CPU w/ ASUS P6T), but there seems to be lacking any info about it and any other i7 setup at the current time.

---

### Post by SunnyRabbiera on 2009-01-07
I am more then sure that linux will work on it, it probably will work best with a 64bit version.
But to be sure I would try out x86 on it too, the i7 doesnt seem to need anything special though (its not like its sparc or PPC)

---

