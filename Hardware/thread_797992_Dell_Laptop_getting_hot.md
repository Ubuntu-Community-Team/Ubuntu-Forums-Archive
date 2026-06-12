---
title: "Dell Laptop getting hot"
date: 2008-05-17
forum: Hardware
---

### Post by vitorgatti on 2008-05-17
Hi,

I'm using Ubuntu 8.04 in a Dell Inspiron 6000
(Centrino 1.6Ghz, 512MB Ram, HD 40GB)

I'm using also the package **computertemp** to monitor the temperature of the processor and HD

Processor starts at 39°C and goes to 89°C (yeah, you read that right, a laptop processor at 89°C)
HD starts at 21°C and reaches 45°C

I don't know what to do.
I've opened the laptop and saw (after breaking the keyboard's sensible flat cable and now I have to use USB-Keyboard) that the cooler wasn't spinning all time (while the system on). It spins, and stops, and spins some more, like it only spins when it's necessary (I think laptops' fan behavior are like that), but I think the laptop doesn't know anymore when to spin, because it stops spinning when the temperature is 75°C... there is no sense on that.
I unmounted the laptop and made a deep clean in the cooler (it wasn't dirty, but, anyway), but nothing has changed.

I've already updated BIOS and HD firmware to their lastest versions.

I've tried to install **i8kutils** to change configuration of the cooler, but when I try to start the command "i8kfan" as root, it shows an error "can't open /proc/i8k: no such file or directory".

I have this laptop since 2005.

Thanks in advance and please help me, because I don't know what to do....

---

### Post by tomdirac on 2008-05-18
did you load the i8k module?

> sudo modprobe i8k

---

### Post by vitorgatti on 2008-05-18
Thanks for the help
This worked!

But I still have the problem
I run the command **i8kctl fan 2 2** (to set high speed to both cooler - there is only one, but ok), and the cooler just try to spin, but does nothing at all.
I keep running this command many times, and it returns:
-1 1
I didn't understand quite well... and I don't know now it the cooler not spinning is a Linux bug or a hardware problem...

Any ideas?

---

