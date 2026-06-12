---
title: "Did anyone managed to switch off the discrete graphic card  on Asus k53 k53sj ?"
date: 2011-05-27
forum: Hardware
---

### Post by JorgeABC on 2011-05-27
I tried to to use the ACPI call method ( _[http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html) )_ using 'echo '\_SB.PCI0.PEGR.GFX0._OFF' > /proc/acpi/call'.

As it has been reported, this works in switching off the graphic card but 10 seconds later the laptop fan starts spinning at full speed.

Also I'm not savvy enough to get 'asus switcheroo' to work...

Some fellow proprietary help, please ;)

---

### Post by JorgeABC on 2011-06-25
Ok. Based on this [https://lists.launchpad.net/hybrid-graphics-linux/msg01535.html](https://lists.launchpad.net/hybrid-graphics-linux/msg01535.html) the following acpi calls seem to turn of the discrete graphic card: 

echo '\_SB.PCI0.LPCB.EC0.TSDS' > /proc/acpi/call
echo '\_SB.PCI0.PEGR.GFX0.DOFF' > /proc/acpi/call

BUT I'M NO EXPERT!
Power went down form 1800mA to 1200mA
Temperature went down from 54º to 47º
Fan is working at normal speed

---

### Post by djkamal on 2011-10-16
#With Comands

#Turn OFF GPU
echo '\_SB.PCI0.PEGR.GFX0._OFF' > /proc/acpi/call

#and 

#Turn ON GPU
echo '\_SB.PCI0.PEGR.GFX0._ON' > /proc/acpi/call


# Tested in my computer is a  K53SJ with Nvidia-Intel Hybrid Grapics

lspci -v -nk | grep -v Capabilities | grep -v Memory | more
#Results

01:00.0 0300: 10de:1050 (rev a1) (prog-if 00 [VGA controller])
	Subsystem: 1043:1682
	Kernel driver in use: nvidia

00:02.0 0300: 8086:0116 (rev 09) (prog-if 00 [VGA controller])
	Subsystem: 1043:1682
	Kernel driver in use: i915

Note:* Require loaded module acpi_call

---

### Post by JorgeABC on 2011-10-16
Just updated to ubuntu oneiric and this methods stoped working. Anyone has a clue why?

---

