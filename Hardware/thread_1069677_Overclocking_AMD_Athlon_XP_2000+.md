---
title: "Overclocking AMD Athlon XP 2000+"
date: 2009-02-14
forum: Hardware
---

### Post by crazyfuturamanoob on 2009-02-14
I got a very old machine running AMD Athlon XP 2000+ (1667MHz). It is 7 years old now.

There is a thich layer of dust inside. I couldn't clean it all, and I'm a total noob with computer hardware, so I can't just disassemble all parts and clean them one by one.


How much can I overclock without breaking it or getting too much heat to light up the dust? I'm a bit worried, if the 7 years old dust lights up even without overclocking?

There's 5 fans in it though, and they make a lot noice. Actually my ears become numb if I use it many hours, so loud the noice is.


Can I overclock it up to 2GHz without overheating or breaking? And I'm not buying any extra fans or cooling systems.


Thanks for your time.

---

### Post by al_capone on 2009-02-14
hi

I overclockt my athlon years ago and achieved some nice results but before you start please do the following or you will roast your cpu. The dust won't burn but the cpu will :P

So disconnect the powersupply. Earth your self. Open the casing and disconnect the fans. Then and only then should you start to undust your system. Every time a significant amount of dust (1 mm is too much) builds up repeat the abve procedure. More often is better.

If your mainboard has many options you should easily be able to bring your 1.6 GHz CPU to 2GHz without changes in fsb and voltage. As it is an old Cpu proceed with caution and ensure you know how to reset the bios. Usually removing the battery for 10+ seconds. 

Good luck

---

### Post by crazyfuturamanoob on 2009-02-14
> **al_capone said:**
> hi

I overclockt my athlon years ago and achieved some nice results but before you start please do the following or you will roast your cpu. The dust won't burn but the cpu will :P

So disconnect the powersupply. Earth your self. Open the casing and disconnect the fans. Then and only then should you start to undust your system. Every time a significant amount of dust (1 mm is too much) builds up repeat the abve procedure. More often is better.

If your mainboard has many options you should easily be able to bring your 1.6 GHz CPU to 2GHz without changes in fsb and voltage. As it is an old Cpu proceed with caution and ensure you know how to reset the bios. Usually removing the battery for 10+ seconds. 

Good luck

I used this computer frequently for ~6 years, at least 5 hours a day, without cleaning it during that time. I bet there is at least 50mm dust.


And the place where I connect power cable, that is a box, with warnings on its side. The warnings say, I shouldn't absolutely open it.

But I can see the box is filled with dust trough the hole of its fan. How can I clean it from inside, and what is it?

---

### Post by 00b00nt00 on 2009-02-15
As you are a NOOB, I really recommend you refer to the computer's handbook. Maybe that will contain instructions for opening the case - usually all you have to do undo a few screws around the base of the box and shake it a little. Without knowing more about your system its hard to say (it is a tower or does the box sit under the monitor? Manufacturer? Model?).

Check the manufacturer's web site for the handbook.

As you have never opened the machine, I assume it has not been upgraded in any way. While you have the case open, you could upgrade the RAM, say to 2GB, if it's supported. Upgrading RAM is safer than overclocking and will probably offer more 'real world' performance. I mean, even if you overclock the CPU, you still can't watch a DVD any faster, can you? ;)

---

### Post by hridyagati on 2009-02-15
HI
Most of the older machines have this kind of problems......

---

### Post by crazyfuturamanoob on 2009-02-15
Here's the specs I remember:
> 
256Mb RAM
NVIDIA GeForce Ti4200, 64Mb
Amd Athlon XP 2000+, 1667MHz
80Gb hard disk

I don't want to put any money into it anymore, because I just bought a new powerful laptop.

Maybe I can get it more useful without money if I just overclock it a bit, and install a very lightweight Linux distro (U-Lite)?

---

### Post by 00b00nt00 on 2009-02-15
Well... What exactly do you need the computer for?

You say you have already bought a powerful laptop, and don't want to spend any more money, so why don't you just dust the innards, do a fresh install of (X)Ubuntu and leave it at that?

At least then you'll have a machine you can sell and offset some of the cost of your new computer.

---

### Post by paulisdead on 2009-02-15
Honestly, if you're too n00b to open the case and spray some canned air in there, you probably shouldn't be overclocking.  If it's a computer from an OEM, like dell, HP, etc, it probably won't have any options to overclock, anyways.

I've been doing overclocking for a long time, and I remember what it was like back in those days, and it was a lot harder than it is today.  How'd you like to hose the data on your hard drive?  That can happen when overclocking those old machines, since the IDE controller is controlled by the PCI bus, which goes up as you raise the front side bus.  So you have to juggle more busses than you do today, since on modern motherboards the PCI, PCIE-E, or AGP busses are all locked at the correct speed and not based off the front side bus.

Those Athlon XPs didn't overclock much at all anyways.  I doubt you'd notice any difference, at all.

You would see far more of a performance boost by putting in more RAM, if it's only got the 256MBs you say it does.

If you're going to do it, you need to test the machine thoroughly.  Run prime95 and memtest or something on it overnight before saying the overclock is stable.

---

