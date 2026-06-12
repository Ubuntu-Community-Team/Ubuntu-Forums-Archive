---
title: "APIC error on CPU0: 40(40)"
date: 2009-03-08
forum: Hardware
---

### Post by T3kG33k on 2009-03-08
Hello all.  I have an issue that has been bugging me for some time and I've done some research on google and the forums but I have been unable to find a solution.
I'm running an Alienware Area 51m 766 and I keep getting this re-occurring error in my system log 
Mar  8 21:57:30 nick-laptop kernel: [ 8470.345107] APIC error on CPU0: 40(40)
I tried entering the irqpoll command in my kernal boot parameters but it just locked up boot process cold.
Any thoughts?

---

### Post by T3kG33k on 2009-03-09
Okay.  I was able to resolve the error by running the noapic option at boot but now several other errors show up in the system logs.  After some more checking I've found that this appears to be a SiS chipset issue.  Can anyone confirm that?

---

### Post by jamesy on 2009-03-31
I get exactly the same error in my system log and have no idea what it is...can someone tell me? My computer works fine but would love to know if it could work better!

---

