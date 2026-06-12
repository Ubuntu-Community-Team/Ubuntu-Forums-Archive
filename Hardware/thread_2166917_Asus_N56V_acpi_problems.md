---
title: "Asus N56V acpi problems"
date: 2013-08-11
forum: Hardware
---

### Post by hawak2 on 2013-08-11
Hello!

I'm fairly new to ubuntu and installed ubuntu 13.04 alongside windows 8 on my asus n56v laptop and everything went fine after turning off safe boot and all that new crap that comes with windows 8 laptops, however when i started using ubuntu on it i couldn't log off, reboot or shut down correctly.

once i choosed to do either of them it started logging off or rebooting/shutting down as intended but just a few seconds after i kept getting a black console with alot of text and some error text that i now have forgotten what it said. anyways i googled a bit and got recommended to try disabling acpi in grub (wrote acpi_osi in and after the linux quiet splash line in grub settings) this solved the logging off, rebooting and shutting down problems but instead added new problems like to my battery and its indicator while having ubuntu os running.

 in ubuntu the battery indicator doesn't work, or it does sometimes but it gives false data and acts completely random (giving different readouts all the time, one minute the indicator may say the battery is full, the other minute its empty and sometimes its charging and sometimes its draining and has anything to 30 minutes to 2 hours of battery life left) this even happens when i know the battery should be fully charged (left the laptop on all night+day with charger in and double checked when windows 8 is loaded that battery is at at least 95%+ in battery life.) 

With that backstory my question really is, how am i supposed to get acpi working with my asus n56v laptop while running ubuntu, is it possible to fix the battery indicator problem while having acpi turned off or is there any way to fix my first problem without turning off acpi off at all? i'm not really an professional with computers, but some googling about acpi made me understand that its a computer/laptops power management and should be kept on as it drives the shutdown, reboot, charging and all that of a computer. 

side note: if my thread is difficult to understand please let me know and i will try to re-write or try to answer if there is anything that is unclear with my problem.

---

