---
title: "ACPI issues for HP Desltop Pavilion and others"
date: 2022-10-30
forum: Hardware
---

### Post by pwabrahams2 on 2022-10-30
In order to install Kubuntu 22.04.1 on my HP Pavilion Desktop, I had to edit the specification **acpi=off** into the grub load line (next to **quiet**). With that change, the installation succeeded. Without this change, the installation simply hangs mysteriously on the initial choice.  I've also encountered this situation when installing OpenSuse Leap.

My question is whether I can avoid making this modification, most likely with a BIOS setting. I emphasize that I do have a working system; I want  to improve the installation procedure.  I don't know how generally this is a problem for HP machines.

---

### Post by Bashing-om on 2022-10-31
pwabrahams2; Hello

There could be good results with swapping DSDT (Differentiated Services Description Table)
> 
ACPI == Advanced Configuration and Power Interface. It provides a way for the PC firmware (UEFI/BIOS) to declare to an Operating System how to control its platform-specific hardware.  ACPI provides several in-firmware 'tables'.


See: [http://iam.tj/prototype/enhancements/Windows-acpi_osi.html](http://iam.tj/prototype/enhancements/Windows-acpi_osi.html)
For the details and how-to :D

[INDENT]all the help there is
[/INDENT]

---

### Post by pwabrahams2 on 2022-11-01
Since I *can* install Linux by editing the installation commands with **acpi=off**, a true solution is necessarily a BIOS setting.  I know of nothing else that will persist from one clean installation to the next.

---

### Post by pwabrahams2 on 2022-11-01
Since I *can* install Linux by editing the installation commands with **acpi=off**, a true solution is necessarily a BIOS setting.  I know of nothing else that will persist from one clean installation to the next.

---

