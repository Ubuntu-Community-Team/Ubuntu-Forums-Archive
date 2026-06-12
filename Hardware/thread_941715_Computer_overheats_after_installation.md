---
title: "Computer overheats after installation"
date: 2008-10-08
forum: Hardware
---

### Post by Simscape on 2008-10-08
Alright, I've been trying to work out this problem for weeks, but nobody will help, and I can't figure anything out.

I'll summarize my problem -
I installed Ubuntu, shortly after, my CPU fan shut off, this never happened in Windows... I thought nothing of it, it should kick back on anytime... I waited, while working on certain things, then *BEEP* down goes the whole computer... "AHH! WHAT HAPPENED??? DID IT CRASH???" See, this is the first time it has happened to me.
I quickly turned the computer back on to see if it ws all still there, everything was fine... Relieved I went back to doing what ever... Then *BEEP* "Oh crap, its happening again..." I took a look  on the inside of my computer, and what do you know.. I almost got burned on the CPU heat sink...
So, this problem will never leave me... WHAT DO I DO???
And now, after about 20 minutes of running, the fan will shut off, and the CPU will overheat.

I have a re-built eMachines W2646, replaced everything but the fans, motherboard, and CPU.
845G Chipset I believe and Intel Celeron CPU.

If I can't fix this anytime soon, I'll be forced to switch back to Windows..

---

### Post by pelle.k on 2008-10-08
The sad truth is that far from every piece of hardare equipment is designed with something else than windows in mind. What they often do is throw together a mainboard with specs that is unknown to driver developers, BIOS:es that are made with windows XP/Vista in mind, and DSDT:s that compile and run with XP/Vista. ACPI specifications are not met, but as long as "it works with windows", they don't bother fixing those issues.
In short, buy linux friendly hardware, if you would like to run something more exotic than Windows on your machine.

So, since that is out of the question now, let's try to figure out if we can do something about it;
Are you running the latest BIOS?
Is the fan module loaded? (lsmod | grep fan)
Is the kernel aware about it? (dmesg | grep cooling)

Last of all, check api errors (paste this in CODE tags please)
dmesg | grep acpi

Also, try to set up lm-sensors, and control the fan using this guide;
[http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)

EDIT; i guess you'll have to it in 15-20 min sessions. Good luck.

---

