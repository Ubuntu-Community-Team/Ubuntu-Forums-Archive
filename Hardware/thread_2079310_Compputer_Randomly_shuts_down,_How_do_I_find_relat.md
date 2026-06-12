---
title: "Compputer Randomly shuts down, How do I find related error logs?"
date: 2012-11-01
forum: Hardware
---

### Post by djoberan on 2012-11-01
I just built a computer from spare parts I had lying around, I can get specs if anyone really wants them. 

The computer sporadically shuts itself down after its been on for a while(max it has been running for about 3 hours), and when I go to restart it right after, it only runs for about 5 min, and each time immediately following the initial shutdown I restart it, it stays on for less amount of time. To me this sounds like a overheating issue, but I have 3 120mm fans in the case, and a 80mm on the video card, with a normal heat-sink on a AMD processor. It is not overclocked and I am not a heavy gamer. From what I feel it is not overheating, at least from what I can tell.
The computer doesn't crash and go to a black screen, it literally just powers itself off, instantly no matter what I was doing.

The current OS is linux mint 13 maya edition, and i know this isn't a mint forum, but since mint is based off of ubuntu. I was hoping someone could tell  me where to start looking for error logs that might tell me why my computer is shutting down randomly. Feel free to ask me for more information if needed. I appreciate all input

---

### Post by ahallubuntu on 2012-11-01
It definitely sounds like an overheating issue.  That doesn't mean it's the CPU overheating, although that's possible.

It is remotely possible that the CPU is overheating because of a driver not loaded for it.  I have seen a case where an AMD CPU would overheat in Windows Safe Mode because the correct driver was not loaded for it.  You can rule that out in your case in a number of ways.  One, after the computer overheats the first time (and you think it will then happen about every five minutes), try powering up and leaving the computer in BIOS Setup for a while and see if it ever shuts down.  Also, the BIOS Setup may show you CPU temperatures.

The CPU fan is important, but the heat sink on the CPU is more important.  It must make a solid connection to the top of the CPU.  If there are four screws and one of them is not secure, that might make a poor connection to the CPU package.  Or, if you didn't put new thermal paste on (or clean off the old, burned  paste) from the CPU package or the top of the heat sink, that could also cause the issue.

It could also be a bad power supply - very easily.  Can you try another one?  Power supplies fail all the time in unpredictable ways.

It could also be some other component on the motherboard.  The chipset chips may have heat sinks on them, too (maybe not fans).  Are all of those secure?  Are you sure none of the heat sinks that were supposed to be on the other chips came off?

---

### Post by Parker32 on 2012-11-02
Hello, first thing I would do would be to open the case and make sure that your cooler fan and also the power supply fan are free of dust/dust bunnies.  You can get a can of compressed air and clean it.  Also make sure that your cooler fan is working.  Sometimes due to wear and/or mechanical malfunction the cooler dies.  Make sure that your cooler fan is working.

---

