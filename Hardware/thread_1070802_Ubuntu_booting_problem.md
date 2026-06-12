---
title: "Ubuntu booting problem"
date: 2009-02-15
forum: Hardware
---

### Post by spirit8 on 2009-02-15
Hi i want to install linux on my laptop and get rid of any other OS, 
i tried Fedora 10 but i doesn't boot correctly to even let me install, 
so i decided to try ubuntu and it doesn't work well too but at least it install, 
my laptop is a HP Pavilion DV6707US(AMD Athlon 64X2) and the problem 
is annoying because every time i power up the computer at the point 
where a small orange bar is supposed to slide  right and left it stops 
and i have to press enter and maintain pressed until the orange bar 
changes to begin fill itself i tried to boot on recovery mode to see 
what happens(i am a begginer so i don't understood the output) but 
it first stopped at something like an irq 20(sorry for the poor information, 
if you could guide me on how to gather helpful information) can any 
one help me on how to solve this, because i don't want to make this 
every time i boot the computer. Thanks.

---

### Post by utnubuuser on 2009-02-15
Hi - You could check your log files (they are all time-stamped) to see at which point the boot is hanging (System>>Administration>>logs)

You could also try a generic > sudo dpkg --configure -ain a terminal to see if helps straighten out any misconfigured files.

---

### Post by spirit8 on 2009-02-15
my install don't boot correctly right after an install so i think that couldn't be a configuration problem, but i will try to see the logs and post them here.

---

### Post by spirit8 on 2009-02-15
i watched the messages while it was booting and the first time it freezed the last message shown was that

[2.982311] chci_hcd 0000:00:02.1: irq 22, 10mem 0xf6489000

---

### Post by spirit8 on 2009-02-16
some body know what that means?

---

