---
title: "pentium 4-m voltage?"
date: 2010-01-28
forum: Hardware
---

### Post by blackmuel on 2010-01-28
ok kinda an old setup but heres the deal! i put a 1.6ghz p4-m in my dell gx270 as sort of a low power pc but i want to know if the voltage is still 1.3v because i know that when  you put a p4-m in a desktop board it will run at 1.2ghz but i cant remember if thats to compensate for the higher voltage on a desktop board. so what im wondering is, is there a program for linux that will show the current voltage of the cpu kinda like cpuid? i used to have windows on this box and cpuid didnt show the voltage of the cpu...

---

### Post by cascade9 on 2010-01-28
The voltage should be 1.3 volts. 

As for 1.2Ghz problem, here is the reason- 

> Where the two processors differ is that the mobile P4-M makes use of Enhanced Intel SpeedStep technology, which is designed to reduce the clock speed of the processor when not under heavy use, thus preserving a laptop's battery. This basically involves reducing the default bus speed multiplier (17 in the case of a 1.7 GHz Mobile P4-M) to 12, resulting in a clock speed of 1.2 GHz. When placed in a desktop motherboard which doesn't understand SpeedStep technology, the processors run at the default 12 multiplier with a bus speed of 100 MHz (1.2 GHz). I'm unaware of any consumer orientated motherboards with support for SpeedStep.


 Now you may think this SpeedStep technology is a bad thing for anyone wanting to use these processors in a desktop. However, by simply increasing the FSB (Front Side Bus) from 100 MHz to 200 MHz the cpu will easily run at 2.4 GHz and benefit from a substantially faster bus speed.


[http://dashwood.me.uk/intel-mobile-pentium-4-m-exploration](http://dashwood.me.uk/intel-mobile-pentium-4-m-exploration)

Really, its best to check your voltage in the BIOS..but being a %&$^*% dell you probably cant. You probably also cant overclock the CPU as well :| Damned dells. 

lm_sensors should check your voltage though.

---

### Post by ajgreeny on 2010-01-28
**mbmon** may do what you want, though the output from it is a bit difficult to understand in detail.

---

