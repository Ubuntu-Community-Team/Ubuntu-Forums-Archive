---
title: "PCU Fan hits full speed and PC hangs"
date: 2009-11-02
forum: Hardware
---

### Post by NatalieG on 2009-11-02
Saterday I upgraded from Ubuntu Server 9.04 to 9.10 on my HP/Compaq d330m. When I have the PC placed in my hall closet (a small space, bad ventilated, I know) after 10 minutes the fan goes into full speed and the PC hangs (it doesn't respond on any signal, no terminal, no daemon, nothing).

Anybody an idea???

---

### Post by NatalieG on 2009-11-03
*bump*

---

### Post by jocko on 2009-11-03
> **NatalieG said:**
> Saterday I upgraded from Ubuntu Server 9.04 to 9.10 on my HP/Compaq d330m. When I have the PC placed in my hall closet (a small space, bad ventilated, I know) after 10 minutes the fan goes into full speed and the PC hangs (it doesn't respond on any signal, no terminal, no daemon, nothing).

Anybody an idea???
That's what happens when you overheat the cpu. Move your pc out of the closet, it needs good ventilation.

---

### Post by NatalieG on 2009-11-05
First of all the pc ran fine in that same spot (in the closet) with ubuntu 9.04. Things started to go 'wrong' the moment that it was updated to 9.10.

But, oke, I moved it to the office room, where it ran fine for a day or so. Then I started working on some shells script to make backups of the websites which are hosted on that machine ... the system again did the 100% fan thing with a freeze, 4 times in a row!!! And it was in a room which was very chilled (16C) and it had all the fresh air it could get hold of.

Then I disabled acpi in Grub and now the system is running smooth again (in the closet). So it must be something with the thermal module of acpi (of 9.10) which conflicts with the (bios of) the machine. I would expect the system to shutdown gracefully when critical temperature is detected, not lockup/freeze.

But I really want acpi to be on and I have been looking for a way to disable only the thermal module of acpi. But how does one do that in ubuntu 9.10?

---

