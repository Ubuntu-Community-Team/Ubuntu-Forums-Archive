---
title: "speed up booting!"
date: 2008-09-28
forum: General Help
---

### Post by cowboyup6983 on 2008-09-28
Is there a way to disable this from when booting up:

Grub Loading State 1.5

Grub loading, please wait

Press 'ESC' to enter the menu....



its like a countdown for something, if there is a way to disable this so it boots right into Ubuntu. I don't dual-boot so no need to see this screen...

Thanks I hope everyone knows what I am even talking about

---

### Post by mikewhatever on 2008-09-28
Yes, I think the default value is 10, right?

> sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
gksudo gedit /boot/grub/menu.lst

Now, find the following section near the top and change the timeout to 3.

> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3


---

### Post by cowboyup6983 on 2008-09-28
> **mikewhatever said:**
> Yes, I think the default value is 10, right?



Now, find the following section near the top and change the timeout to 3.

was already at 3,,, so i just changed to 0

now it just says Grub Loading, State 1.5

Grub loading, please wait

and then skips third option and starts to boot, so i guess i gain 3 seconds in speed, lol, oh well thanks for helping

---

### Post by jonian_g on 2008-09-28
That's the best you can do now.
The new version, ubuntu 8.10, will boot faster, so just wait for it.

---

### Post by cowboyup6983 on 2008-09-28
> **jonian_g said:**
> That's the best you can do now.
The new version, ubuntu 8.10, will boot faster, so just wait for it.

whens that, im expecting in november to get my a new labtop, u know when all the sales come like day after thanksgiving, i'll be one of those idots waitin in line like always day before. i want to power my pc also, so looking to upgrade my motherboard and definitely cpu. those new wolfdales look cool, something like 3.0ghz dual core. not sure those quad core are really efficient yet since most apps cant even take advantage of the full 4 cores.

---

### Post by jonian_g on 2008-09-29
October 30

---

### Post by frankleeee on 2008-09-29
Startup manager in add remove allows you to change the wait time for the described boot and the kernel you want to automatically run and how many kernels on that screen when you hit escape and several other processes.

---

