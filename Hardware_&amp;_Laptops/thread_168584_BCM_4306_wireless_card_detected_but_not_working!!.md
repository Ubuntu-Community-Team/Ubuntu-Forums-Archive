---
title: "BCM 4306 wireless card detected but not working!!"
date: 2006-04-30
forum: Hardware &amp; Laptops
---

### Post by jcharnin on 2006-04-30
I recently had to format my laptop and place windows on it in order to have my computers hardware serviced. Now that I have my laptop back I want to have Ubuntu Breezy as well. I had everything working fine before but it seems like the instructions in the wiki have changed... Like it is missing the correct steps to enable the radio. 

Anyway, I've installed ndiswrapper and installed the correct drivers.

gridfall@01trip01:~$ ndiswrapper -l
Installed ndis drivers:
bcm4sbxp        driver present, hardware present

The only problems I have run across are these.

gridfall@01trip01:~$ sudo ndiswrapper -m
Password:
modprobe config already contains alias directive

and Dmesg shows this towards the end (which it didn't after the reinstall until I loaded the driver) 

[4294747.870000] Bluetooth: RFCOMM socket layer initialized
[4294747.870000] Bluetooth: RFCOMM TTY layer initialized
[4294764.085000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4294764.330000] ISOFS: changing to secondary root
[4295071.523000] ibm_acpi: ec object not found
[4295568.118000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295568.118000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295568.328000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295568.328000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295575.906000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295575.906000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295576.045000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295576.045000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295583.725000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295583.725000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295584.063000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295584.063000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295584.160000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295584.160000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295584.335000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295584.335000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295692.705000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295692.705000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295692.868000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295692.868000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297969.099000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297969.099000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297969.872000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297969.872000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297975.003000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297975.003000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297975.121000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297975.121000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298042.625000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298042.625000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298042.758000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298042.758000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298046.891000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298046.891000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298047.005000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298047.005000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298048.860000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298048.860000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298048.983000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298048.983000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298050.176000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298050.176000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298050.356000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298050.356000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298300.428000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298300.428000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298300.536000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298300.536000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298424.261000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298424.261000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298424.379000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298424.379000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

If anyone can help or push me in the right direction that would rock! Thank you all!

---

