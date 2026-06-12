---
title: "How to diagnose OS shutdown by unknown trigger?"
date: 2018-03-31
forum: Hardware
---

### Post by stlu on 2018-03-31
I have a used desktop which I installed Ubuntu server edition on.  Since the initial install about 15 days ago, there have been two occurrences of the OS being told to shut down by an unknown source.  it is a fresh install except for the addition of some command line utilities.  I suspect the hardware, which I haven't used before, is the source of the trigger.

Searching the web for answers, I found that this is a difficult issue to find good answers for because of unclear reports.  Many replies are asking for clarification.  Even more replies assumed the wrong scenario and were useless to the OP.  I hope my thread title is clear.

(One of these days maybe there will be common wordings to distinguish between hardware that just shuts off, and cases where the OS began the shutdown process unexpectedly, even if the trigger was hardware-related...)

So far I have exhausted ways to diagnose the system without making changes to flesh out the problem.  I was not logged in to see any "wall" output.  The logs don't indicate a cause for shutdown, just that processes were terminated and the shutdown process ran properly.  I'd rather not mess with the system if I can help it.  (This machine is a training ground for me to learn better ways to do things that I'd need in a job one day)

I am looking for two things:
[LIST=1]
[*]A nice on-line reference listing all the possible triggers that would start OS shutdown.  So far my suspects are CPU overheating or misinterpreted CPU overheating, the power button being pressed by a human or some kind of intermittent short of the power button's circuit.
[*]Ways to narrow down the cause, without hacks like renaming or removing the execute permission on binaries /sbin/shutdown and /sbin/reboot.
[/LIST]


Thanks

---

### Post by TheFu on 2018-03-31
Had something like this happen to me after moving from 14.04 to 16.04 a few months ago.  The system would shutdown about 30 seconds AFTER I logged in.  Traced it back to some perl dependency issues that also helped systemd.  Systemd needs a few more years to be stable enough for production use.  Heck, why would perl dependency issues force a system shutdown?

There are at least many, many ways for a system to decide to shutdown.
Overheating doesn't shutdown stuff that I've seen.  It just slows the CPUs.
ACPI can cause a shutdown.  This is how virtual machine management software asks a guest VM to shutdown nicely.
I'm not certain that shutdown/reboot are used by the system. Those are human interfaces. Probably.

Is "used desktop" about the hardware or did you previously install one of the ubuntu desktop flavors on it first? I'm confused.

---

### Post by cruzer001 on 2018-03-31
Hardware or software?  I don't know, but with kernel headaches going around I would also try a different kernel.

---

### Post by stlu on 2018-03-31
> **TheFu said:**
> ...
why would perl dependency issues force a system shutdown?
...


I bet there's a good joke in there somewhere.


> **TheFu said:**
> ...
Overheating doesn't shutdown stuff that I've seen.  It just slows the CPUs.
ACPI can cause a shutdown.  
...


I have a memory from several years ago involving a machine with heating problems.  I remember seeing text on my monitor that the CPU temperature was too high, and the result was my machine ended up powered off.  I first recalled this as something that happened under Linux on a text console, but now I am not sure - it could have been coming from the BIOS just after the POST screen blanks in preparation to boot.  All I have to go on is the image in my head which would look the same in either case.

I am working on an old iMac G5 17" all-in-one, mostly out of curiousity, and there is some kind of CPU or chassis overtemperature condition, and the Lubuntu Powerpc OS does not react by shutting down, so that confirms what you said.

Back to the system in question, I wouldn't be surprised if it is the power button circuit.  If the mysterious shutdown doesn't happen again in the next 3-4 days, I will try the power button just to see what the logs look like after.  I might go ahead and modify the configuration so that I get confirmation of an ACPI power button event saved to a file.  If this problem continues to a point where there's nothing left for me to learn from it, I'll just scrap the hardware and move on.

> **TheFu said:**
> ...
Is "used desktop" about the hardware or did you previously install one of the ubuntu desktop flavors on it first? I'm confused.


"used desktop" = old hardware that I have not run *anything* on before, therefore more likely the source of a trigger to the OS to shut down.  Well before I did the install, I ran memtest for 10 passes (in February) so I trust the memory and to the extent of finishing the memtest, also somewhat trust the PSU, CPU, and motherboard.

---

### Post by TheFu on 2018-03-31
> **stlu said:**
> "used desktop" = old hardware that I have not run *anything* on before, therefore more likely the source of a trigger to the OS to shut down.  Well before I did the install, I ran memtest for 10 passes (in February) so I trust the memory and to the extent of finishing the memtest, also somewhat trust the PSU, CPU, and motherboard.

When the shutdown is triggered, does it shutdown cleanly or abruptly?   If cleanly, you can grab the log files while it is working to shutdown.  There should be some information there, especially in the kernel log, that says why.  Journalctl supports asking for logs by time, so if you keep track of the time on the system, you can ask for the logs later.
```

journalctl -k -p err
```

---

### Post by stlu on 2018-04-03
It shuts down cleanly, but I haven't found any clues in the logs.  And of course, now that I'm investigating it, the darn thing won't dare do it again :roll:.  It's probably going to wait till I leave the house or something.

---

