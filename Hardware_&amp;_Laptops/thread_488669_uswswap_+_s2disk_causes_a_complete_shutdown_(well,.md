---
title: "uswswap + s2disk causes a complete shutdown (well, sort of)"
date: 2007-06-30
forum: Hardware &amp; Laptops
---

### Post by stoned_ninja on 2007-06-30
I'm using uswswap on Feisty because "reboot" is the only power-management feature that currently works. Kernel hibernate left a few unsettling messages on the screen before turning off the power completely. It seemed to resume where it left off upon the next boot but with even more error messages in the console (mostly regarding USB management).

uswswap's s2disk seems to work flawlessly with no obvious errors, but it also completely shuts down the machine. I have to press the power switch to wake it up and suffer through the whole BIOS POST messages, Grub selection menu, etc. Once it gets back into Feisty though, it resumes almost perfectly where it left off (ethernet connection loss is the only minor annoyance).

Are other people experiencing a similar problem with suspend/hibernate?


Hardware Info:
Mainboard = Asus P5GDC-V 
CPU = P4 530 (3.0GHz)
Graphics = Intel 915G onboard

---

### Post by DagMan on 2007-07-01
s2disk is supposed to do that.
s2ram is another thing to try which is supplied by the same program.
[http://en.opensuse.org/S2ram#s2ram_-_Getting_suspend_to_RAM_to_work_out_of_the_box](http://en.opensuse.org/S2ram#s2ram_-_Getting_suspend_to_RAM_to_work_out_of_the_box)

---

