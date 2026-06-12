---
title: "ubuntu on asus' m2r32-mvp?"
date: 2007-06-25
forum: Hardware &amp; Laptops
---

### Post by fusionisthefuture on 2007-06-25
hi e'rebody, im trying to install linux on a dual boot machine with a (you guessed it) m3r32-mvp motherboard by asus.  i usually go about this by running a live cd and using gparted to format my HD like i want it, because im a bit unfamiliar with the cli yet, and then i put in an alt cd and install feisty that way.  so im trying my edgy live cd, and it gets nowhere.  when i run it normal with just splash turned off it says this: 

booting the kernel. 

..MP-BIOS bug: 8254 timer not connected to IO-APIC

busybox v1.01 (debian 1:1.01-4ubuntu3) built-in shell (ash) 
enter 'help' for a list of built-in commands.

/bin/sh: cant access tty; job control turned off 

then if i try to boot with noapic its says:

booting the kernel. 

busybox v1.01 (debian 1:1.01-4ubuntu3) built-in shell (ash) 
enter 'help' for a list of built-in commands.

/bin/sh: cant access tty; job control turned off 

if i try to boot with noapic, acpi=off i get:

booting the kernel. 

udevplug[985] : make_queue unable to create /dev/.udev/queue: no such file or directory

busybox v1.01 (debian 1:1.01-4ubuntu3) built-in shell (ash) 
enter 'help' for a list of built-in commands.

/bin/sh: cant access tty; job control turned off 

also one time i tried it with noapic and acpi=off i got some "1-1 usb cant set config #1" message

does anyone think this might be resolved when using a fawn boot cd?
ty very much 
-arne

---

### Post by giorgiopm1 on 2008-02-18
May be I am wrong, but I feel wee have tos stay on Windows for a while:
this motherboard is not in the list of the UBUNTU supported ones.

---

