---
title: "Laptop Overheating?"
date: 2008-05-28
forum: Hardware
---

### Post by kevo214 on 2008-05-28
This is a problem I've had with windows in the past when I'm gaming and I block the vents, but when I'm in Ubuntu if I use it for too long all of a sudden the screen will go insane and all that's visible is a tan screen with white static lines all over. I believe the problem to be over heating. 

I'm running a Dell XPS M1710, I think it's probably the vido card (an NVIDIA GeForce Go 7950 GTX). I don't hear any fans kick on ever, and I'm having a hard time getting lm-sensors/xsensors working (only the core-temps display when I use sensors command).

Any hints?

---

### Post by kevo214 on 2008-05-28
I'm not so sure it's overheating anymore because it just happened again while I was browsing the forums in firefox. I also had my laptop cooling pad under the laptop, and when I rebooted and check the temp it was only 38C/100C.

Anyone think it's the drivers?

---

### Post by kevo214 on 2008-05-30
Perhaps it's a bad driver?

---

### Post by rony474 on 2008-06-15
check your vga , with FN + power button, you will see a diagnostic .. after that you will know if something is damaged

---

### Post by stoneybridge on 2008-12-20
exact same laptop, exact same problem, anyone sort this? i gave up n went back to the dark side :(

---

### Post by xelxel on 2008-12-20
I was dead convinced it was driver/ACPI related, until i picked the laptop bottom out, and cleaned the CPU Fan. Pulled out an enormous dustrat. That helped alot with the issue, but then the symptom was different. My laptop simply shut itself off.

---

### Post by Dethv on 2008-12-20
Mine does the exact same thing. It will sometimes do it when I just turn the laptop on so I know it's not an issue with overheating. It's really annoying and I have to close the lid to go to a blank screen then open it again for my screen to return to normal. This does not happen under windows under long periods of gaming so I'm assuming its a driver issue. I really wish I could get this sorted, its really annoying.

---

### Post by Dutchmaster on 2008-12-21
My Averatec AV7170 the same. This problem seems to be Ubuntu-specific (and it's siblings).

RPM, most debians, and bsd all seem to run cpu throttling just fine.

powernowd and cpufreq seem to have no effect with the 'buntu's.

---

### Post by galenparker on 2009-01-01
Same laptop as OP and same problem. There is another thread (with no helpful information here: [http://ubuntuforums.org/showthread.php?t=1006396](http://ubuntuforums.org/showthread.php?t=1006396)).

I also don't believe it's a heating problem as the issue can occur shortly after restarting before there has been a decent heat buildup.

Gut feeling says it's a driver issue.

---

