---
title: "How to know if a RAID adapter is supported?"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by dupa on 2007-01-11
I just put the Ubuntu 6.06 Desktop on a old server machine with RAID device with 2 connected disks.

X server doesn't start for some problems..
So I'm in a console mode.

I am absolutely not expert about RAID devices.. how can I know if it can "see" the raid partitions?

I tried with a
```
df
```

But seems that there is not any large disk in that list.
So can you suggest me some commands to issue to get know if linux can see the raid discs?
Thanks

---

### Post by hal10000 on 2007-01-11
Can you give a little more information about your system?

e.g. which raid controller do you use (manufacturer, scsi, ide, or sata) ?
which raid level ( raid 0, 1 5 or whatever)

Is your raid controller onboad or is it a (pci or isa) card?

Did you verify that your BIOS is set up correctly to recognize the raid
Some raid controllers have an own BIOS and own tools (independant from the operting system) to set up controller and disks,which are to be run by typing a special key at boot time.

You should post as much information as you can, even about the mainboard and chipsets etc.

---

