---
title: "Help on how to install Ubuntu 8.04 in a laptop with Vista preinstalled?"
date: 2008-05-04
forum: Hardware
---

### Post by Gunn3r on 2008-05-04
Hello and greetings to all.
I bet that you have already answered this simple questions but I couldn't find the right answers for me yet.
I bought a new laptop this week, with Vista preinstalled, a Toshiba A200-21T with the following specs:

- Intel Core 2 Duo T8300 2.4 ghz 45nm 800mhz FSB 3mb L2
- 3 GB DDR2-667
- 1GB Intel Turbo Memory
- ATI HD2600 256/1GB Turbocache
- HDD 250GB 5400 rpm
- Chipset 965
- 15,4 lcd

I already ran the Ubuntu 8.04 LiveCD on it and seems to run fine, the only thing it didn't ran was Compiz because somehow the restricted drivers menu wasn't showing. I tried a Mandriva 2008.1 Live cd afterwards and it ran Compiz fine, so i guess it's just the lack of drivers in the Ubuntu CD.

Well, as the title says, I want to install Ubuntu on it. The main problem is... I want to keep the Vista recovery partition, which is in the 1st partition and dual-boot with Vista that is on the 2nd partition. The laptop has yet another partition for data that I wanted to keep, despite lowering it's size.

So, How can I do it?
I know that it's possible to use Vista Boot Manager afterwards instead of GRUB and if that is simpler for me to use I'd like to use it that way since I may need to erase Ubuntu if the laptop needs to go for repair (in my country it's demanded by Toshiba that the warranty implies that the Vista recovery partition must be in perfect shape and Vista booting up as 1st OS or they just don't repair under warranty),

I have already the Gparted Live CD but I noticed that Vista has a builtin tool to resize partitions? will it be better for Vista "health" to use it instead of Gparted?
We already know how M$ products tend to be allergic to another OS...

Thanks for all the help and if someone knows a step by step "Install Ubuntu along with Vista" tutorial for dummies on laptops (my 1st one) please let me know.

---

### Post by capnkyle on 2008-05-04
[_APC's guide_](http://apc.simbient.com.au/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm) is the one I am planning to follow pretty soon, and looks like it is pretty thorough.

edit:
I just followed it through, and I had no problems what so ever.

---

### Post by Gunn3r on 2008-05-06
ok, thanks, I'll take a look at it

---

### Post by hamideh on 2008-07-26
Hi!
I can not understand? you have solved the problem of uncompelete windows during the installation of ubuntu 8.0.4 or yours ws adifferent one? I can not install ubuntu on my laptop because the windows are not showing compeletely, for example the windows for determining the time zone and location and all behind it are not available! If you know something about it, I would appriciate you telling me about it. It will be a great help.
Thanks.

---

### Post by argosreality on 2008-07-26
You can easily shrink the Vista partition to save some space (Right Click My Computer, Select Manage, click on Disk Management in the left hand column and then right click on the partition you want to shrink and choose Shrink Volume) at that point you can use the GRUB bootloader without any issues to boot to the recovery partition, Vista partition or Linux

---

