---
title: "odd problem"
date: 2006-01-08
forum: Hardware &amp; Laptops
---

### Post by Brando569 on 2006-01-08
first off i hope this is in the right section, now to my problem. it seems whenever i overclock my 3.2 ghz p4 processor above 10% kubuntu gives me one of these two messages when its uncompressing the kernel:

uncompressing linux....

incomplete literal tree (or invalid compressed format (err=1)  )

---system halted---

yet i never had this problem when i had it overclocked at 10% i wanted to try higher speeds cuz i wanted to see what the processor/mobo could handle without going crazy. if this is fixable that'd be great although its nothing to lose sleep over. idk if this matters but i tried it on a smp 686 kernel a 686 kernel and a 386 kernel and got the same thing on all three of them.

also i just noticed that in my /var/log/dmesg log it says CPU: Hyper-Threading is disabled but yet its enabled in the BIOS and im using a SMP kernel. but then again it recognizes 2 processors CPU0 and CPU1 :confused: anyway to fix this also?

---

### Post by mcduck on 2006-01-09
[QUOTE=Brando569]first off i hope this is in the right section, now to my problem. it seems whenever i overclock my 3.2 ghz p4 processor above 10% kubuntu gives me one of these two messages when its uncompressing the kernel:

uncompressing linux....

incomplete literal tree (or invalid compressed format (err=1)  )

---system halted---

yet i never had this problem when i had it overclocked at 10% i wanted to try higher speeds cuz i wanted to see what the processor/mobo could handle without going crazy. if this is fixable that'd be great although its nothing to lose sleep over. idk if this matters but i tried it on a smp 686 kernel a 686 kernel and a 386 kernel and got the same thing on all three of them.

also i just noticed that in my /var/log/dmesg log it says CPU: Hyper-Threading is disabled but yet its enabled in the BIOS and im using a SMP kernel. but then again it recognizes 2 processors CPU0 and CPU1 :confused: anyway to fix this also?[/QUOTE]
Most likely you have already reached the max speed with your current settings.

Are you raising CPU multiplier or FSB? If FSB, your RAM may also be the problem.. You can check that by running memtest for couple of hours. If you get any errors your memory can't handle that high speeds.

To overclock CPU more than that you'll most likely need to increase core voltage to make your CPU stable again. And that would require improved cooling. If you choose to try this, raise volts in BIOS in small steps until your system is stable again. And keep your eye on temperatures, you should install lm-sensors if you haven't done that already. And do all this on your own responsibility, too high core voltage with bad cooling _will_ burn your CPU.

---

### Post by Brando569 on 2006-01-09
i guess im changing the FSB idk its not the multiplyer cuz thats locked at 16, whats even stranger is for about a week or two i had it overclocked 10% from 3.2 to 3.51 with no problems. then it went screwey, im thinkin maybe its the bios upgrade that i did. which im still trying to fix :mad:

---

