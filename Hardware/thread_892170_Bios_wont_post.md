---
title: "Bios wont post"
date: 2008-08-16
forum: Hardware
---

### Post by erkz on 2008-08-16
Alright, I happily had Ubuntu 7.10 installed on an old computer of mine, but it was prone to random restarts every 60-70 minutes. 

I figured it was the ram, so I got some new ram, tried it out, and it still happened.

I then figured, why not try reseting my bios? So I removed my cmos, then put it back in, and my computer monitor came up with some "Reset bios" screen. After that, it turned off, and now it will no longer even post. I have tried resetting the bios again but it has had no  effect..

I have even bought a new motherboard, and set it all up...and still, no post. Only sign of life I get from the motherboard is a green light...  (The cpu fan doesn't even start up!!)And I have tried three sticks of ram (though I did get them for free from a charity computer store but I'm pretty sure ONE would work... I still have a few more I could try), so I am sure that it can't be the issue...

Any ideas? I really want to get my computer working again..Thanks in advance!

I am seriously stumped here..so please help :( I don't know what else could be wrong, since the new mobo also had a new cpu and a new bios.. So I'm really, really confused.

-Erkz

---

### Post by Naatan on 2008-08-16
Not exactly a Ubuntu problem but whatever.

You say you've tried a different motherboard and different ram with the same results, that leaves 2 possibilities, the Power Supply or, more likely.. your Processor.. 

It's possible that your Power Supply breaks down when the plug you use isn't properly grounded, I've had it before and it gave me random reboots.

Anyway, try replacing those 2 parts, if it still doesn't work I'll be baffled..

---

### Post by pytheas22 on 2008-08-16
Are any fans turning on when you try to boot the computer?  Generally fans would at least turn on unless there's a problem with the PSU or the power connections to the motherboard, so check those things, and try using a PSU that you know works if possible.  If you're not seeing any action at all--no beeps or fans--besides the light, then I'd suspect some kind of power connection problem.

If you replaced the motherboard and the machine still won't turn on, then the problem has to lie somewhere other than the BIOS.  Are you sure that all the cables are connected properly, including the auxiliary power cord?  Double-check them all, because some cables can look alike and seem to fit in places where they're not supposed to go.  Also make sure that no part of the motherboard is touching metal, which could be shorting it out.

You can also try jumping the motherboard manually to make the machine turn on.  There are two pins somewhere on the board (probably currently connected to your case's power button) that you can touch with a screwdriver, and machine should start.

If you're still not getting anything, try removing everything from the motherboard except the CPU, RAM and power supply and see if that helps.  If not, you should try swapping a different CPU and PSU to see if they help.

If you do ever manage to get the machine to boot and it still arbitrarily reboots itself, you should look at the Linux syslog to see why.

---

