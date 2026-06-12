---
title: "PC won't power up"
date: 2013-11-03
forum: Hardware
---

### Post by grahamw799 on 2013-11-03
I just installed latest version of Ubuntu I am basically a brand new user. I had been having problems with windows vista and a friend suggested I joined the Ubuntu community.  With nothing to lose I installed Ubuntu 12.10.  Everything was going well I was using the system listening to music feeling like I had anew computer.  A message popped up asking did I want to update the version I was using so I did.  When my computer restarted it switched off during the reboot and now that's what happens when I switch it on I don't even get the chance to enter setup by pressing F2 as I would have with windows.
any advice.
graham

---

### Post by ian-weisser on 2013-11-03
> **grahamw799 said:**
> I don't even get the chance to enter setup by pressing F2 as I would have with windows

If you are not reaching BIOS, then the system is failing POST (poweron self-test). You have a hardware problem, not an Ubuntu problem.
Is your system blinking any lights in patterns? Sounding any beep patterns? Does the fan start?

---

### Post by mkmanifesto on 2013-11-03
Is anything displaying on your monitor after you power it on? If not power off the computer and pull the power.

A few thing you can try is too remove the memory and unplug the power from your hard drive. At that point plug the power back in and try turning the computer back on. That should result in a beep code because your don't have any system memory installed. Assuming you did get a beep code unplug the power again. Insert just one of your memory sticks and again try to power on your computer. Hopefully your computer will post. If it works repeat the process one at a time until all your memory is installed and power is plugged back into your hard drive.

Another thing you can do as well is remove the battery from your mobo for a few minutes to see if resetting the BIOS fixes your problem.

---

### Post by grahamw799 on 2013-11-04
Thanks guys appreciate the advice will try tonight.

---

### Post by grahamw799 on 2013-11-04
The fan does start.  Not sure I can see much of a pattern. Press power switch PC comes on (Power switch lit, the hard drive light flashes a few times, after about 12 seconds power switch blinks off then on, hard drive light comes on for another 10 seconds or so then all switches off).  Nothing even appears on screen....not looking good:(

---

### Post by ian-weisser on 2013-11-04
Count the number of regular flashes by each light, and note the sequence.
Use a search engine to look up the error codes of your system model. Those codes (expressed by fleshes or beeps) are how the system tells you what the problem is.

On a properly-running Ubuntu install, the drive light goes on once for several seconds while the ureadahead software reads an entire section of the disk once containing most of the system files (and organizes what it read in RAM - much faster than reading file-by-file from the disk), and starts flashing and reading file-by-file only after software needed to boot and start the system is loaded.

---

### Post by grahamw799 on 2013-11-05
Thanks Ian and mk luckily for me as a novice taking the battery out and putting it back in again worked!
I suppose that should have been a no brainer even for a novice.  Anyway other advice noted too, feel like I have a new laptop again!!!!

---

### Post by ian-weisser on 2013-11-05
Problems like that are only simple when looking back, only after the experience.
Congratulations on the easy fix!

---

