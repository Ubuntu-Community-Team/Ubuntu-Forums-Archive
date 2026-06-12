---
title: "NO APIC error"
date: 2008-11-04
forum: General Help
---

### Post by zirun292 on 2008-11-04
Hey can anybody help me about the NO-APIC error, it's driving me crazy. It started since my staff partner always taking that PC everywhere and suddenly when we open the PC on that unlucky day, it gives us the error of something to do about " MP-BIOS bug " or something after it enters the GRUB menu. The error shows this:-


Starting up . . .
[    17.981709] ..MP-BIOS bug: 8254 timer not connected to IO-APIC


and then it just hang.
I've been looking through the Internet to solve this problem but still i can't find, there are some way's but it's not working.

I think there are some way. Can you guys fix that for me?

I'm not forcing you, but if you some solution just post it in this thread.

):P

---

### Post by SuperTeece on 2008-11-04
Heya!

At the menu after the CD boots, hit F6 and enter 
```
noapic nolapic vga=771
```

See how that works for you.

credit goes here: [http://ubuntuforums.org/showthread.php?t=959041&highlight=timer+not+connected](http://ubuntuforums.org/showthread.php?t=959041&highlight=timer+not+connected)


> **zirun292 said:**
> Hey can anybody help me about the NO-APIC error, it's driving me crazy. It started since my staff partner always taking that PC everywhere and suddenly when we open the PC on that unlucky day, it gives us the error of something to do about " MP-BIOS bug " or something after it enters the GRUB menu. The error shows this:-


Starting up . . .
[    17.981709] ..MP-BIOS bug: 8254 timer not connected to IO-APIC


and then it just hang.
I've been looking through the Internet to solve this problem but still i can't find, there are some way's but it's not working.

I think there are some way. Can you guys fix that for me?

I'm not forcing you, but if you some solution just post it in this thread.

):P

---

### Post by zirun292 on 2008-11-04
Thanks dude!
Now it's working and thanks again!!!

I really, really owe you one!

---

