---
title: "loading lt_hotswap on boot kills ibm_acpi: Thinkpad T30"
date: 2006-08-14
forum: Hardware &amp; Laptops
---

### Post by kaens on 2006-08-14
Alright, so I have a Thinkpad T30 - and Ubuntu works awfully nice under it. I did notice, however, that the system would freeze if I hotswapped an optical drive for a battery in the Ultra-bay slot.

There is a module called lt_hotswap that monitors the slot, and sends the eject command to ibm_acpi (I do believe) if the release lever is pulled. It works perfectly fine if I load it when my system is already booted.

I'd really like to have this loaded at boot time though - so I added lt_hotswap to /etc/modules, and the one configuration option it has to /etc/modules.d/options as options lt_hotswap auto_eject=1.

That should load the module on boot, right? And it does.

dmesg | grep hotswap produces ```
[17179849.068000] Laptop ultrabay hotswap driver version 0.3.6
[17179849.068000] lt_hotswap: '\_SB.PCI0.LPC.EC.BAT1' found (Hot-Swappable)
[17179849.068000] lt_hotswap: '\_SB.PCI0.IDE0.SCND.MSTR' found (Hot-Swappable)
[17179849.068000] lt_hotswap: '\_SB.PCI0.PCI1.DOCK.IDE1.PRIM.MSTR' found (Non-Swappable)
[17179849.068000] lt_hotswap: '\_SB.PCI0.LPC.FDC.FDD0' found (Hot-Swappable)
[17179849.068000] lt_hotswap: '\_SB.PCI0.PCI1.DOCK' found (Hot-Swappable)

```

However, when it boots, /proc/acpi/ibm is entirely missing. The /dev/ files didn't get made, and dmesg | grep ibm produces: ```
  ibm_acpi: IBM ThinkPad ACPI Extras v0.12a 
ibm_acpi: http://ibm-acpi.sf.net/ 
ibm_acpi: dock device not present
ibm_acpi: acpi_install_notify_handler(bay) failed: 7
```

I found out that lt_hotswap needs to be loaded after all other ACPI modules are loaded, and I suspect that this is the problem. Any confirmation on that? I've also read that udev does not load modules in any specific order - so is there any way around this other than adding something to xinitrc or bashrc (or wherever would be appropriate) or running a script on login? That seems like an ugly solution to me, but I'll do it if I need to - It *does* work seamlessly if it's loaded after boot.

Sigh.

Any feedback would be appreciated.

---

### Post by markgreene on 2006-10-11
I have a Lenovo T60 and I want to know how to make it so that I can swap a battery for the CD/DVD Burner or the battery without any hitch. 

I am a beginner to linux but understand much of it. Can you help me out?

---

### Post by Snargle on 2006-11-20
Hey, my T30 also crashes upon ultrabay removal. I haven't found anyone else with this problem. my only ultrabay device is a combo cdrw/dvd drive.

---

