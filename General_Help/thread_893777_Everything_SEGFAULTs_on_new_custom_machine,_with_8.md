---
title: "Everything SEGFAULTs on new custom machine, with 8.04"
date: 2008-08-18
forum: General Help
---

### Post by goldenfly on 2008-08-18
Hello all:

    I recently built a machine and installed Ubuntu 8.04 on it. However, I have observed the following phenomenons, before and after updating all apps using apt-get:

- Firefox (3.01) would close inexplicably, sometimes even when I'm idling. gdb shows segfaults occurring in libxul, libsqlite3, and libflash

- Synaptic / apt-get would state that 'dpkg returned a Segmentation Fault' during the installation / uninstallation of applications

- most GUI apps (including Eclipse 3.4 and Open Office 2.4) crashes at random times

- while running "Hardware Testing", the internet section stated "Received signal SIGSEGV: Invalid memory reference"

- by running dmesg, I see 'gnome-terminal', 'bluetooth', 'lsb_release', 'internet_test', 'python' and others causing segfaults

     I have re-installed 8.04 numerous times, with identical results. I have yet to try installing an older version of Linux.

     My question is: what would be likely culprits, either software or hardware? The motherboard? The RAM? The HDD? By the way all components are bought new, and memcheck did not return any errors.

     Here's my system configuration:
MOBO: Gigabyte GA-P35-DS3P
CPU:  Intel Core 2 Duo E8400
RAM:  Kingston KVR 800MHz 2048MB Kit
GFX:  Asus PCI-E GeForce 8 EN8500GT
HDD:  Western Digital 500GB, SATA2
DVD:  Pioneer 115D

     Thanks in advance for any and all advices.

     Sincerely;


Goldenfly

P.S.: I've used this hardware configuration on 2 other custom machines (one running XP and 8.04, other running 8.04), and both are working perfectly.

---

### Post by goldenfly on 2008-08-19
Here's another troubling phenomenon that I have observed:

upon reboot, past Grub, I see the following -

Starting up ...
[    30.125613] Kernel panic - not syncing: No init found.   Try passing init= option to kernel.

After a hard restart (i.e. power shutdown), everything boots up fine again...

Any ideas?

---

### Post by fahadsadah on 2008-08-19
This is not good. 

Try using either old release (Gutsy Gibbon/7.10) or future release beta (Intrepid Ibex/8.10)

Gutsy is still supported, Intrepid won't be supported till october when it's released.

---

