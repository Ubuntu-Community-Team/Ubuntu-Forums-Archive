---
title: "Keyboard, touchpad not detected at startup"
date: 2007-11-25
forum: Hardware &amp; Laptops
---

### Post by aashay on 2007-11-25
My laptops touchpad and keyboard are sometimes not detected at startup. The system boots up, shows the login, but then I cant do anything and have to press the power button to shut down the system (yes, the power button works even on a single tap, as opposed to a prolonged press). The strange thing is, the problem seems to be related to the kernel and not to xorg. If I remove splash and quiet from the boot options, if the keyboard is detected properly, i can type while all the bootup messages are shown, else not. 
Now heres the strange part. The laptop came preloaded with Vista. If i start vista, restart and then boot ubuntu, the keyboard and touchpad work almost everytime. Even while restarting through ubuntu, theres a good chance of getting stuff to work.
One of the solutions i've seen is enabling legacy usb support in the BIOS. This was already enabled. Even disabling it does no good.
Btw, its a Lenovo laptop.

---

### Post by aashay on 2007-11-26
anyone? It's coming to a point where it is almost unusable. Please dont tell me i've to use vista
EDIT: I found this suggestion after much googling
In order to get back a working keyboard you should not load the ac, battery, thermal modules. In the kernel ACPI configuration page choose 'M' (module) for the relative AC adapter, battery and CPU thermal controller.
Can anyone atleast tell me how to do this?

---

### Post by aashay on 2007-11-27
3 posts in a row without anyone else replying..

After much reading, I've found the problem related to acpi and the 8042 interrupt controller conflicts. Is anyone aware of a kernel patch that might fix this?

---

### Post by rmsrohan on 2007-12-23
had the same prob but after lots of googlin found that adding 

locale=fr_FR i8042.reset to your kernel line solves the problem with no error on sound or others


eg: 

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,7)
kernel /boot/vmlinuz-2.6.22-14-generic ro quiet splash locale=fr_FR i8042.reset
initrd /boot/initrd.img-2.6.22-14-generic
quiet

---

### Post by kyerme on 2008-01-04
I had the same problem on my Lenovo Y500, and the acpi=off setting while it did work... caused it to not detect a lot of of my hardware.

The **locale=fr_FR** parameter is actually for setting language (French) and location so I suppose you can leave it off and simply apply **i8042.reset** as a boot parameter on the live CD, which seemed to work for me for the most part. Now moving to installation.

Thank you!

---

### Post by tajmzr on 2008-02-10
I am beginner with linux, I had same problem on my lenovo Y500, I cannot understand what was I do regard above  posts please describe step by step direction to solve this problem.:confused:

thanks

---

### Post by aashay on 2008-03-12
edit your grub menu file:
sudo gedit /boot/grub/menu.lst
Find the line which says
# defoptions=
add i8042.reset at the end of this line
# defoptions=i8042.reset
(do not remove any other parameters already present, just add i8042 at the end)
save the file, reboot
Imp: do not uncomment the defoptions line. Leave the # as it is

---

