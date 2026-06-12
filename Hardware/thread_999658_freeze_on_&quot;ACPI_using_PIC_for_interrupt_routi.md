---
title: "freeze on &quot;ACPI: using PIC for interrupt routing&quot; at startup"
date: 2008-12-02
forum: Hardware
---

### Post by hfgfdhrtjtyjtykjtjd on 2008-12-02
Can anybody help me with the following problem: I have installed Ubuntu on my ASUS L4500R laptop. I have kept my old windows XP system on another partition as well. Selection of operating system is done with the default method ("GRUB"?). When "arriving" at GRUB from a restart of either windows XP or ubuntu, I can select and start the 2.6.24-22-generic Ubuntu without problems. However, when starting "cold" (from a turned off computer) it hangs forever at "Starting up...". When removing splash screen and quiet options I can see that the last printout is "ACPI: Using PIC for interrupt routing". Any suggestions?

---

### Post by caljohnsmith on 2008-12-02
Sounds like it might be some sort of BIOS issue; have you checked how the HDD is configured in BIOS? Also, does your BIOS have any ACPI related settings? In the meantime, as a workaround you could try pressing Ctrl + Alt + Delete on start up after you get the Grub menu; I think that would have the same effect as a restart, so you might be able to boot Ubuntu right after that.

---

### Post by hfgfdhrtjtyjtykjtjd on 2008-12-08
Thanks for the quick answer, and sorry for the slow response from here. Thought I subscribed to the thread.
So the ctrl-alt-delete from Grub menu doesn't work (same symptoms)
The BIOS setup doesn't contain any references to ACPI. There are some pretty coarse controls for battery control (Dim screen on battery yes/no, power save CPU on battery yes/no), and they don't change anything in terms of succesfull startups.
So no luck.

Any other ways to trick Ubuntu into thinking that it is starting from a restart rather than a turned-off computer?

---

