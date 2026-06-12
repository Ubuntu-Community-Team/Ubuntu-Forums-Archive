---
title: "Laptop won't boot after suspend mode."
date: 2011-06-02
forum: Hardware
---

### Post by tigull on 2011-06-02
Hello, Compaq Presario CQ-56 (not even a month old) running Natty. A few hours ago I closed the lid to put the computer in suspend mode. When I tried to "wake it up" the screen would be blank and there would be no sign of hard drive activity. I held down the power button and restarted the computer, but even though the keyboard lights are on, there would be no BIOS starting up (so I can't even boot from USB and wipe the whole thing), let alone Grub. The CD drive makes noises though, but after that it's again a pitch black screen with no sign of hard drive activity. I did suspend before without problems, and I rebooted 5-6 times with no success. Any help welcome and thanks for your time.

---

### Post by DanneStrat on 2011-06-05
> **tigull said:**
> Hello, Compaq Presario CQ-56 (not even a month old) running Natty. A few hours ago I closed the lid to put the computer in suspend mode. When I tried to "wake it up" the screen would be blank and there would be no sign of hard drive activity. I held down the power button and restarted the computer, but even though the keyboard lights are on, there would be no BIOS starting up (so I can't even boot from USB and wipe the whole thing), let alone Grub. The CD drive makes noises though, but after that it's again a pitch black screen with no sign of hard drive activity. I did suspend before without problems, and I rebooted 5-6 times with no success. Any help welcome and thanks for your time.

Seeing, as you posted this thread 2 days ago, did you get it fixed?

If not, can you get into the OS at all?

When a computer goes into suspend or hibernate, the normal behaviour

of the computer is to hide the boot splash screen with setup and boot 

devices etc. so that you can't boot from another media or make any other 

changes until the operating system has restored from it's previous state.

But in case something goes wrong with suspending, then this functionality 

can be a pain.


Try to turn the computer off, then pull the plug from the 

wall outlet and wait for a while (15 minutes maybe) to drain the cmos battery.

Then plug it in and power it on and see if you get any progress.

---

### Post by tigull on 2011-07-01
Sorry I haven't checked this in a while...it was definitely a hardware issue, because everything went back to normal when I remove the battery while the laptop was on (with a blank screen and even without loading the BIOS as I said before). This even happened again a couple times but this "hard fix" solved it.

---

