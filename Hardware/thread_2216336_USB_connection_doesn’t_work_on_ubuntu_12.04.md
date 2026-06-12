---
title: "USB connection doesn’t work on ubuntu 12.04"
date: 2014-04-11
forum: Hardware
---

### Post by assafwww on 2014-04-11
Basically the title of the post summarizes the problem. 
I cannot connect USB devices to my computer (running on ubuntu 12.04). The problems started because of unknown reason, months after ubuntu was installed (had no special problems with Ubuntu before)
Maybe I have a lead to solve the mystery: some USB devices are mounted after opening Startup Disk Creator tool.

Would be grateful for your intelligent advice

---

### Post by varunendra on 2014-04-12
Is this a Gigabyte motherboard? Is there a feature called "IOMMU" in its BIOS? If yes, try turning it "On" in the BIOS.

If not, what do these commands (entered in a terminal, which can be opened with 'Ctrl-Alt-T') show when you plug in some USB devices -
```
lsusb
dmesg | tail -20
```

---

