---
title: "fujitsu siemens amilo d1845"
date: 2010-07-24
forum: Hardware
---

### Post by davetheraveni on 2010-07-24
can any body help me i have a  fujitsu siemens amilo d1845 and trying to get 10.4 on to it, do i need to install the netbook version of 10.4 to get it to work. Cause when i put the desktop one in the mouse pad and the keyboard does not work


many thanks 

dave

---

### Post by LSenf on 2010-07-25
I recently had the same problem.

For me, using the bootoption acpi=off solved all the problems.

When booting the live cd, you can press any key before it starts the actual boot process to enter the full live-cd menu. there you can set additional boot options (by pressing F6 or so), just activate acpi=off.

After the installation, you have to add acpi=off to the boot options, so it will always use it. For the first step, you probably need to use an external keyboard and mouse to avoid the freeze occurring when pressing a key of the built-in keyboard.

After logging in, type in terminal:
```
sudo gedit /etc/default/grub
```
to edit the bootloaders' setting.
In that file, add acpi=off to the line
```
GRUB_CMDLINE_LINUX_DEFAULT
```
if i remember correctly, it should look like
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
```
afterwards.
save the file, execute in terminal:
```
sudo update-grub2
```
to tell the bootloader to use the new settings.
Afterwards, you should be able to use the build-in keyboard without a freeze.

I hope that also works for you,

LSenf

EDIT: btw, you don't need to use the netbook edition ;) actually it is surprising that the netbook edition works better for you - however, the keyboard problems did not always appear when i booted the live cd, maybe it only occurs randomly.
if the problems don't stop even with acpi=off, you could try to create a new live cd... maybe your cd is damaged (had a mouse freeze problem once with a cd i made using a less reliable drive)

---

### Post by sonytony on 2010-08-17
I have the exact same machine, and was struggling with the same problem all day, so thanks for the solution. I'm just wondering if there are any other problems i should be aware of when using 10.04 on this machine?

---

