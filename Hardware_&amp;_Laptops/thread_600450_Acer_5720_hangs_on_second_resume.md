---
title: "Acer 5720 hangs on *second* resume"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by ris8_allo_zen0 on 2007-11-02
Hello everybody,
this is my first post. Until now, I managed to solve all my problems by searching in these forums and finding the solution almost everytime :)
But I can't still find anything about this issue: my brand new Acer 5720 goes correctly in suspend mode, then resume, then suspend again, then hangs!
The power Led turns from blinking orange to green, the screen remains completely off, I can hear the hard drive turning on but nothing else. I can only turn off the machine.
I've tried adding ec_intr=0 to the kernel command line, I tried adding the DSDT for my laptop model: nothing changed.

I also have some trouble using the correct keywords describing my problem (second time suspend hang?)...

Any help?

Thanks in advance!!
RAZ

---

### Post by ris8_allo_zen0 on 2007-11-06
These are the attempts made so far, which led to absolutely no change:

- booting without X (single) and always using /etc/acpi/sleep.sh sleep
toggling the following flags in /etc/default/acpi-support:
- ACPI_SLEEP_MODE (the script stops and says "No such device" writing 'standby' to /sys/power/state)
- SAVE_VBE_STATE
- POST_VIDEO
- USE_DPMS
- DISABLE_DMA
- RESET_DRIVE
- ENABLE_LAPTOP_MODE
- DOUBLE_CONSOLE_SW
- disabling all services in /etc/rcS.d, then killing most of the processes, then removing most of the modules


These ones, instead, make the laptop hang at first resume:
- booting with "noapic nolapic"
- changing flags like in [this page](http://de.wikibooks.org/wiki/Asus_W3N-Kompendium:_Ubuntu_Suspend_to_Ram) (I know it's not my laptop model, but I found it and tried it)


I suppose something in the ACPI status doesn't return to its original state before and after the first suspend. Is there a way to get a dump of such configuration?
Tried "find /proc | xargs cat > dumpN.txt" and diff'ing each dump, but nothing useful appears.
Tried the same with /sys but its output is pretty much above my knowledge. Maybe you can take a look?

---

### Post by ris8_allo_zen0 on 2007-11-07
Tried adding "pci=routeirq" -> nothing changes
Tried changing SATA emulation in Bios from AHCI to PATA -> the screen can't wake up from first standby but the rest of the system is alive, I can (blindly) retype the suspend command but it doesn't resume, as always.

Into Windows Vista and XP, I can standby and resume any number of times I want without troubles.

I'm attaching dmesg, lspci and dmidecode.

---

### Post by ris8_allo_zen0 on 2007-11-07
This problem is [filed as a bug](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/160763).

---

### Post by Lumo on 2007-11-27
This problem is really bugging me too - I hope there is a fix soon.

---

### Post by Itried on 2007-11-27
This problem also affects me too. I have a custom desktop (G'byte-P35 m/b, Core 2 Duo E6550 processor and Nvidia 8400GS graphics).

---

