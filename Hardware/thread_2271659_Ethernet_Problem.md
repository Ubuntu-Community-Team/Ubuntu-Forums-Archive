---
title: "Ethernet Problem"
date: 2015-03-31
forum: Hardware
---

### Post by Ronco Pizatto on 2015-03-31
There are known issues with the Gigabyte 970A-DS3P motherboard running Ubuntu 14.04 when it comes to ethernet support. It seems to be a drivr problem but I'm not too savy about drivers and system mods.

 I want a quick fix to this. Can I just buy an ethernet card, plug it in and fix the problem?

---

### Post by Bashing-om on 2015-03-31
Ronco Pizatto; Hello;

Short answer:
```

sysop@1404mini:~$ lspci | grep Ethernet
00:08.0 Bridge: NVIDIA Corporation MCP55 Ethernet (rev a2)
00:09.0 Bridge: NVIDIA Corporation MCP55 Ethernet (rev a2)
01:09.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
sysop@1404mini:~$

```
Yes.
where " Accton Technology Corporation " is the PCI card I am running in place of the 2 on-board interfaces, with no problems.
I would expect your results to be similar.

[INDENT][INDENT]it's a thang
[/INDENT][/INDENT]

---

### Post by churchnilled on 2015-03-31
Hi,

I also use the same board and adding in another older but known working pci lan card still gave me the same problem, but i got both working, only thing is i am not sure which of the things i did fixed it as i was getting so frustrated after hours of reading and trying all sorts rebooting etc i neglected to reboot after the two following items but on reboot it did work so it is one or the other that worked.

1st was to follow these instructions at the bottom of the page [http://unix.stackexchange.com/questions/108952/realtek-r8169-not-working-in-centos-6-5](http://unix.stackexchange.com/questions/108952/realtek-r8169-not-working-in-centos-6-5)  
2nd was i changed a setting in the bios, from installing the motherboard all bios settings for me i left at default and the only item i changed which was also one of two things i did that got the lan working is change "Other PCI Device ROM Priority" to "Legacy OpROM" the default was "UEFI OpROM"

---

