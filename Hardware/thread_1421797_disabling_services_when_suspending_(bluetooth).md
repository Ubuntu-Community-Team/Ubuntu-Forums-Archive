---
title: "disabling services when suspending (bluetooth)"
date: 2010-03-04
forum: Hardware
---

### Post by Post Monkeh on 2010-03-04
my laptop suspends and resumes fine, however while suspended, my little bluetooth dongle continues to flash away, and my phone maintains a connection.

not only is the blue flash quite distracting if i'm trying to sleep, it's also a drain on the battery (of my laptop and my phone) to have the bluetooth stay on when i don't need it.

what do i need to edit to get my bluetooth to switch off when i suspend, and preferably switch on again when i resume?

---

### Post by Post Monkeh on 2010-03-05
anyone?

---

### Post by Post Monkeh on 2010-03-07
i must keep asking this at the wrong time

---

### Post by Post Monkeh on 2010-03-12
boing

---

### Post by Post Monkeh on 2010-03-13
are you lonesome tonight, dum dum dum dum :P

---

### Post by shel-hall on 2010-06-01
> **Post Monkeh said:**
> my laptop suspends and resumes fine, however while suspended, my little bluetooth dongle continues to flash away, and my phone maintains a connection.

not only is the blue flash quite distracting if i'm trying to sleep, it's also a drain on the battery (of my laptop and my phone) to have the bluetooth stay on when i don't need it.

what do i need to edit to get my bluetooth to switch off when i suspend, and preferably switch on again when i resume?
This seems related to a problem I had with my Toshiba Portege R100; the battery would go dead in about a day, even when the machine was switched off.

It turned out that Linux (in my case Puppy, but it's a Debian derivative like Ubuntu) was leaving the Ethernet card on when it powered down the machine.

It sounds like it's doing the same thing to your Bluetooth dongle in suspend mode.

Try unloading the driver module before, and reloading it after, suspending.  You can do this through the CLI, using the "modprobe -r modulename" command (to unload), where "modulename" is the name of your bluetooth module.

-Shel

---

