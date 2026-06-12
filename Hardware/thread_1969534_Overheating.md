---
title: "Overheating"
date: 2012-04-30
forum: Hardware
---

### Post by Atadam on 2012-04-30
To say first things first!
Do not reply and tell me i have dust inside my Laptop an shall clean it.
Do not reply and tell me about any Hardware issues because it is not.

Since autumnn last year my laptop is overheating and since nobody has found a solution i might just try it here once more.

The reason why the Laptop is overheating is very simple:
All Linux(ubuntu,lubuntu,linux mint, fedora)distributions i have installed do the same thing and shut the fan down at 70°C instead of 48°C.
The possible reason for this is probably the thermal.h procedure beacuse the values my laptop uses for lowest fan speed and emergency shut-down are defined by hwmon and only used with thermal.h

With maverick i had a time where the fan worked as it was supposed to do and i made the mistake to upgrade to 11.04.
Since i had no backup for the kernel i downloaded a version of maverick and despite my efforts to find the right kernel i still use a overheating laptop.
(I baught it because it was sold as Linux Laptop)

What ever Linux i put on the laptop now all shut off the fan at 70°C.

To all my research i can say it is not a Bios problem because bios only provides the trip points and leaves all other control to OS.
It is not a trouble caused by any settings inside the Bios or a Hardware related sorrow.
I remind, everything worked fine until last autumn.

I can say that Ubuntu 10.10, 11.04(i386), Lubuntu 11.10amd64,12.04amd64; Fedora 16amd64; Linux Mint (Gnu amd64)
and several other maverick kernels i gave a try do all the same on my laptop and shut down the fan at 70°C.

I would appreciate any solution or a place where i could find an old maverick kernel without patches i might use.

The fan trip points as used by all of the above mentioned distributions are
70°C for lowest fan speed
75°C increaseing fan speed
84°C give a little more
95°C shut the whole thing down

The trip ponts that should be used are 48, 57, 69, 75, 84, 92 and ahut down at 100°C
cpu throttle values (hwmon) are 70°C and 95°C

Has anybody a suggestion or much better a clue how to alter the kernel to get the fan work at the correct trip points.

I have 15 days left for a solution because after that it will be too hot to use the Laptop at all (at least for Linux).

with best regards M.Peters

---

### Post by suryak on 2012-04-30
I really don't know about it. All I can say is that, try "askubuntu" on stackexchange. you might get answers quickly.

---

