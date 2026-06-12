---
title: "Reducing CPU clock speed?"
date: 2013-07-13
forum: Hardware
---

### Post by Derek5272 on 2013-07-13
I have a computer built largely from components received from my uncle when he upgraded his computers, and as it was highly unstable (could not run for more than 10 minutes without freezing) running Windows, I decided to switch it to Ubuntu to see if I could get any more out of it. It does run better, but it is still unstable (usually good for 1-2 hours if I am not multitasking), and I am currently attributing this to the fact that the processor (a 3.2 GHz Intel Pentium D) had been overclocked and is now running at more than 110% (3.53 GHz). I'm trying to find a way to reduce the clock speed or multiplier and hopefully improve stability. I might be able to fix it if I put Windows back on, however it would be a headache trying to get the changes made without it crashing, and I also do not have an ODD in this computer and would need to borrow the drive from my main PC (motherboard does not appear to support booting from USB).

---

### Post by Binary-Synapse on 2013-07-13
Hello.

You should be able to set your correct CPU settings (frequency, voltage, clock multiplier, etc...) by using your BIOS.
Normally there should be an Auto function to correct these settings automatically for you (even if you don't know what they are).

Also check your RAM settings (also in the BIOS).

When everything is in it's standard/normal values, then run some intensive programs to retest your computer stability.

---

### Post by Yellow Pasque on 2013-07-13
> I'm trying to find a way to reduce the clock speed or multiplier and hopefully improve stability.
Reset the BIOS/CMOS. That should put it back to stock speed.

If it still overheats, then you need a better CPU cooler.

---

### Post by Hexxus on 2013-07-13
> **Temüjin said:**
> Reset the BIOS/CMOS. That should put it back to stock speed.

If it still overheats, then you need a better CPU cooler.


+1 on that one. Def. needs the bios reset. 


If you're not sure how to do that or cannot, you could pull the battery on the motherboard let it sit for a few seconds with the power cord un-plugged then put it back in and turn on the computer.

---

### Post by 00b00nt00 on 2013-07-13
Hitting 'Delete' on boot will usually get you into the BIOS. You can reset by selecting 'Optimized defaults' or something similar. Make a note of the motherboard so you can download the manual from the manufacturer's web-site. The manual will explain all the BIOS settings should you need to tweak.

Did you assemble the system yourself? As it is a used system, it may be worth cleaning the fluff out with a can of compressed air and also run the system with the case open to see if the fans are running. If you are sure it is heat related, you could also re-seat the CPU heatsink after cleaning and application of new thermal paste, but this would be a last resort.

However, I suspect this might be a memory problem. Assuming you have re-set the BIOS and that the parts are clean and the fans are running, run memtest on each individual stick one at a time to determine if there are any faults. As your system is very unstable, any faults should appear fairly quickly.

---

### Post by Derek5272 on 2013-07-14
I have already checked for a setting in the BIOS and could not find anything, so I assume it was set using an application in Windows. I did assemble the system myself, CPU fan is working and I cleaned and applied thermal paste at that time. I'll try removing the CMOS battery, I made a half-hearted attempt at it a while ago but I think it was in a slightly awkward place so I gave up rather quickly on that. If that doesn't help I'll try testing the memory, honestly hadn't thought it would be anything else after seeing the CPU speed. Thanks for the suggestions, will work on it in the morning. Hopefully I can get it stabilized then move on to my audio problems and get it running as an HTPC.

EDIT: Clock speed successfully reset after removing CMOS battery, now I just need to wait to see if it crashes still.

---

### Post by 00b00nt00 on 2013-07-15
> **Derek5272 said:**
> I have already checked for a setting in the BIOS and could not find anything, so I assume it was set using an application in Windows.

This is odd. The only kinds BIOS I have seen which don't allow any tweaking of the memory / CPU performance settings are on laptops, and even they have an option to load default values! At least removing the CMOS battery achieved something. While we are on the subject of BIOS, it may be worth downloading the latest version from the manufacturer's website and flashing that - however I would caution to do this only on a stable system. Have you left the system in the BIOS for a few minutes to see if it still crashes? At least that would rule out OS problems.

The reason I thought your problems might be memory related is that the overclock was quite mild, and any difference in temps would really only be seen when the system is under load. Dodgy RAM can hit at any time.

---

