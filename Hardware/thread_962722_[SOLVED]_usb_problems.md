---
title: "[SOLVED] usb problems"
date: 2008-10-29
forum: Hardware
---

### Post by banana jama on 2008-10-29
hi so far the forums has help me solve 2 out of 3 problems lets see if that can turn into 3 out of 4.

       i have a hp pavilion dv6000 and i notice that my usb ports aren't working properly. what do i mean? when i put in my flash drive ubuntu doesn't discover it. its a 4gb U3 thumb drive. also it does.t discover my mp3 player. what can i do to solve this.

---

### Post by ddrichardson on 2008-10-30
LoL mine did this to - if you boot with a USB device attached it is recognised, the problem is with HAL and the HP USB subsystem.

You will need to add this to the kernel on boot by adding them to the relevent kernel line in /boot/grub/menu.lst:
```
acpi_irq_balance irqfixup irqdebug pci=biosirq pci=nomsi acpi_osi=&#8221;!Linux&#8221; acpi_os_name=&#8220;Windows 2006&#8221; noirqdebug
```

There is a guide to altering this file [here]("http://https://help.ubuntu.com/community/GrubHowto#Modifying%20boot%20options%20in%20GRUB").

You might need to add noapic to the start of this but seeing as you haven't said your screen is blank on boot I'm guessing you've either already done this or you don't need it.

---

### Post by banana jama on 2008-10-30
> **ddrichardson said:**
> LoL mine did this to - if you boot with a USB device attached it is recognised, the problem is with HAL and the HP USB subsystem.

You will need to add this to the kernel on boot by adding them to the relevent kernel line in /boot/grub/menu.lst:
```
acpi_irq_balance irqfixup irqdebug pci=biosirq pci=nomsi acpi_osi=&#8221;!Linux&#8221; acpi_os_name=&#8220;Windows 2006&#8221; noirqdebug
```

There is a guide to altering this file [here]("http://https://help.ubuntu.com/community/GrubHowto#Modifying%20boot%20options%20in%20GRUB").

You might need to add noapic to the start of this but seeing as you haven't said your screen is blank on boot I'm guessing you've either already done this or you don't need it.

so i just put this code in terminal also your link doesn't work.

---

### Post by ddrichardson on 2008-10-31
No you need to put it in grub's menu.lst file. There's an extra bit in the link, it should be [this]("https://help.ubuntu.com/community/GrubHowto#Modifying%20boot%20options%20in%20GRUB").

---

### Post by banana jama on 2008-10-31
thanks it worked. but mp3 player still doesn't work. i found out that creative mp3 players don't work on ubuntu with out a driver from there website only one thing though that site no longer exist. thanks anyhow at least my usb ports are working.

---

### Post by carmy on 2008-10-31
Hi friend,
            Sometime your pendrive or flash drive was virus infected so your usb port is not working properly.The solution is reinstall the usb driver through your cd or device manager.

---

### Post by banana jama on 2008-10-31
but i formatted my flash drive so shouldn't the viruses should of been erase right. plus i've read that there are no viruses for ubuntu currently.

---

### Post by ddrichardson on 2008-11-01
There hasn't been a widespread Linux virus, [Wikipedia]("http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses") has quite a good article on it. If there were and you formatted (unless it had an extra little partition emulating a floppy - which you'd notice) then its gone.

The majority of viruses under other OS that I've seen spread through USB recently aren't very sophisticated, exploiting the autorun feature and require nothing more complicated than unhiding an inf file and deleting what it points to.

You don't need a driver for a USB mass storage device, even Windows has one preinstalled from XP onwards. The problem was HPs odd USB/ACPI implementation. I like mine but more for Windows use, the BIOS has had six upgrades this year alone all adressing power management issues.

---

### Post by banana jama on 2008-11-01
o i didn't know that. hey i have one more problem can you look at this forum and see if you can help.[http://ubuntuforums.org/showthread.php?t=965685]("http://ubuntuforums.org/showthread.php?t=965685") thanks for your help.

---

