---
title: "Very very slow laptop"
date: 2012-06-05
forum: Hardware
---

### Post by bobipod on 2012-06-05
I have ubuntu 12.04 on both my pc and my laptop.

Both normally work without delay and are touch responsive with minimal fuss.  My pc is running fine but my laptop is incredibly slow.

The laptop is used more than the pc but they have a similar amount of data on the drives.

The laptop normally runs superb on ubuntu, it did on previous installation and did when i first installed 12.04 as a sole os.

Recently, last two weeks, it has gone incredibly slow.  The internet espescially.  I've had the tech guys from my isp check the service and all is fine.  My pc is running superbly on the internet.  All the wifi devices are working fine.  

It seems to be only my laptop that has suddenly gone super slow.  Any ideas?

---

### Post by ahallubuntu on 2012-06-05
Check the hard drive, CPU fan/heat, and the RAM.

In Ubuntu you can install GSmartControl (a graphical interface to the smartctl utility) to check S.M.A.R.T. status of the drive.  Hard drives fail all the time, sometimes gradually, and when failing they can make a computer really slow as they die.  Look at the Attributes tab in GSmartControl, and look for any Attributes highlighted in Red - those are the ones you should look carefully at.

Laptop CPUs can overheat if their cooling system isn't working properly.  Inside, there should be a heat sink to draw heat from the CPU and a fan to cool the heat sink.  The fan can stop working and the heat sink (and the fan) can get clogged over time with dirt and dust.  Typically computers will simply shut off when they overheat, but I have seen computers that just get really, really slow when the CPU overheats.  CPUs generate heat when in use; sometimes the computer will "throttle" the CPU (greatly slow it down) to reduce heat.  I once saw an old Dell laptop that NEVER shut off but was running far slower than spec - and it was because of this overheating!  Cleaned it out and the CPU temp dropped over 20C and speed increased back to normal.

Cleaning out the CPU heat sink and fan area is a wise idea on any old laptop, anyway, once in a while.

Also check to see how much RAM you have.  I have seen RAM SO-DIMMs ("RAM sticks") come loose from a laptop.  If you had, say, 2 512MB sticks before and one came loose, you'd have only 512MB and that could make the computer really slow.   You can also run Memtest by rebooting, holding down the Shift key, and choosing Memtest from the Grub menu.  If Memtest doesn't fail in the first 30 seconds it's probably OK. I can't imagine you have a bad RAM chip if you are able to boot Ubuntu but you never know.  Easy to test and rule out.

---

### Post by bobipod on 2012-06-06
I've carried out all of the above tests gsmart all seems fine, no faults found.  The cpu fan is working really well it never gets what i would call too hot and i can feel the cooling air being blown out of the side of the machine.

The only thing i have yet to do is the memtest.

---

### Post by mastablasta on 2012-06-07
what are the laptop specs?

---

