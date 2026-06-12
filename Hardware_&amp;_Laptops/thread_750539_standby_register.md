---
title: "standby register?"
date: 2008-04-09
forum: Hardware &amp; Laptops
---

### Post by ayu on 2008-04-09
Hi, not Ubuntu related, but I don't know where else to ask. When you put the machine to suspend/hibernate, where does it store this state? Is it in the bios, the mbr of the harddrive, or after the OS loads? Thanks in advance!

---

### Post by Green Tree Python on 2008-04-09
Ayu:

In hibernation/standby everything is saved 2 the hard drive,with certain components left active. In hibernation the monitors turned off but the hard drive and mouse are in a low power state.

Later,

GTP

---

### Post by ayu on 2008-04-16
Hello,

Thanks for the reply. Perhaps you did answer my question, but I would like to clarify: When you hit the power button on a computer while it is off, it does a POST, then reads the bios, which then tells the computer to read the mbr and then whatever is loaded from there. When you hit the power button while the machine is in hibernation/suspend, does it still "post" or read the bios, or is it still considered "on"? In hibernation, there is no power, so it can't be considered "on". It must read a register, somewhere, to know not to do a regular boot but to resume from hibernation. My question is where is this state stored; ie when does it know not to do a regular boot but to do a resume; does it know this while loading bios, or after loading something from the harddrive? Thanks!

---

### Post by ayu on 2008-04-25
Could somebody please point me to a forum where I can ask this question, or any other resource? Thanks in advance!

---

### Post by TriDeka on 2008-04-27
what GTP said about hibernation/standby is not fully true. Standby turns off the monitor, hard drive and peripherals (depends on settings) but runs power to the ram in order to keep the memory state.

Hibernation dumps all the data from the ram onto the hard rive then turns off the computer completely. When you resume from hibernation you're actually turning the computer back on. So the BIOS will start and do a POST check then look for a mbr, but when it finds the mbr there's a flag telling to load the memory dump on the HD to the RAM, essentially restoring the previous RAM state.

I hope that cleared up a few things.

---

### Post by ayu on 2008-04-30
> **TriDeka said:**
> what GTP said about hibernation/standby is not fully true. Standby turns off the monitor, hard drive and peripherals (depends on settings) but runs power to the ram in order to keep the memory state.

Hibernation dumps all the data from the ram onto the hard rive then turns off the computer completely. When you resume from hibernation you're actually turning the computer back on. So the BIOS will start and do a POST check then look for a mbr, but when it finds the mbr there's a flag telling to load the memory dump on the HD to the RAM, essentially restoring the previous RAM state.

I hope that cleared up a few things.

Hello, Are you absolutely certain the computer doesn't know to resume from hibernation until after bios/post when it reads the mbr? Is this also true for suspends? I don't recall seeing the bios screen when I resume from suspends.

---

