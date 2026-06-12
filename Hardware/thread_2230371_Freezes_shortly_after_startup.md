---
title: "Freezes shortly after startup"
date: 2014-06-18
forum: Hardware
---

### Post by feffer on 2014-06-18
Running a Dell 9100 desktop. Have experienced random glitches shortly after startup for months. Recently, the machine freezes solidly frequently after startup requiring a hard shutdown. Sometimes instead of a freeze the computer will suddenly drop back down to the boot sequence. Pretty sure it is NOT software related. This machine is multiboot and has Ubuntu, Mint and Win7 installed and these problems have happened on every OS. In the past I've replaced the graphics card (Nvidia) and tried a different boot drive. Really don't know what to do anymore. Machine is a few years old, but not ancient and has I-7 Intell CPU. I don't want to replace it, but I'm stuck. What can I do?

---

### Post by Bucky Ball on 2014-06-19
Run the memtest. It is an option on the boot menu when you start the machine. Be prepared, could take awhile. One of the RAM sticks may be dodgy ...

---

### Post by feffer on 2014-06-20
Ran the mem test...no errors. My usual proceedure at the end of the day is to run a series of auto-backup scripts from cron with a shutdown at the end. Then in the morning, I manually boot the machine into a different linux OS than the previous day. Since the freezes happen within a few minutes of a cold boot, I tried leaving the machine on overnight. Then I rebooted from a "warm" machine. No crash, but that's just one day. Tonight, I'll try running a suspend sequence after the back-ups and see how that works. It's very puzzling.

---

