---
title: "Computer freezing and resetting at random"
date: 2009-10-22
forum: Hardware
---

### Post by rogeriovinhal on 2009-10-22
Hi, this may not be related to Ubuntu, but someone might know something that can help me.

Starting two weeks ago my computer started freezing and rebooting completely at random. Sometimes at boot, sometimes before loading kernel, sometimes 20 minutes after boot, sometimes 2 hours... It just froze everything, ssh cant come in and keyboard leds flashing like in a kernel panic.

I tried to boot in an older version of Ubuntu, but the same thing happened again, also happens in Windows.

Today I've tried a lot of times, but now it seems to reset a lot earlier than usual, the last weekend I spent 2 days without a freeze, but now before I can open a page in Firefox it just reboots. Sometimes when it reboots, it loops in checking the IDE devices and doesn't even show video output.

This is quite an old machine, but it never had any problems like this.

Configuration:
Athlon 64 3500+
Gigabyte GA-K8NSC-939
Seagate 250GB Sata II HD (set to Sata 1 for compatibility with the MB)
1 GB DDR 400 Corsair Value (512x2)
ATI Radeon 9600XT 128MB with modded cooler
Seventeam 420W PS
IDE CDRW and DVDR

I already tried:
1- change the videocard
2- take off one of the memory cards (tried both of them)
3- clean all contacts and re-insert cards
4- Ubuntu Memory-test
5- verified temperatures and voltages
6- boot from live CD and fsck on HD partitions

Nothing except the last one gave any clue to the problem. Booting from Live CD seems to work fine, but the fsck didn't find any problems at the HD.

This problem doesn't sound at all a HD problem, never seen HD lock and reset the machine. It is also strange to be a MB problem, beacuse of its randomness and not happening with the live CD.
What you think it might be?

---

### Post by Dark_Stang on 2009-10-22
Run your hard drive manufacturer's diagnostic tests. Segate's tests are called "Seatools." They should be freely available from their website. Also run your motherboard manufacturer's diagnostics if they are posted. I just diagnosed a machine have very similar issues last week, it was a bad motherboard. Fortunately the unit was under a warranty so I just boxed it up and sent it to HP.

---

### Post by Insightfill on 2009-10-23
> **rogeriovinhal said:**
> Configuration:
Athlon 64 3500+
Gigabyte GA-K8NSC-939
Seagate 250GB Sata II HD (set to Sata 1 for compatibility with the MB)
1 GB DDR 400 Corsair Value (512x2)
ATI Radeon 9600XT 128MB with modded cooler
Seventeam 420W PS
IDE CDRW and DVDR
You mention a modded cooler.  Is the CPU or the video card overclocked?  Stability can be a fickle thing to 'measure', so the live CD session may be less stable than you think.

---

### Post by rogeriovinhal on 2009-10-26
Now I have suspicions of the motherboard and the power supply only.

I don't overclock the CPU neither the GPU, the GPU cooler is modded because the original one stopped spinning and I broke somthing in it trying to put some lubricant.

I've installed lm-sensors in the Live-CD and the +5V keeps varying from 2V to 6V. I found that a little strange, maybe it is a measure error from the sensor because that is a very high range for a PS voltage. The +12V is solid in 12.35 - 12.4, so it is not a problem.

I will get a borrowed SATA power adapter so I can test an older PS I have just to make sure it is the motherboard.

---

