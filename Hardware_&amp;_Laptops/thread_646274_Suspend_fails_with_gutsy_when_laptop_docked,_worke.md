---
title: "Suspend fails with gutsy when laptop docked, worked with feisty"
date: 2007-12-21
forum: Hardware &amp; Laptops
---

### Post by pegranka on 2007-12-21
I have a Compaq nx6125 running Kubuntu x86_64. 
With feisty suspend and hibernate usually worked, whether docked or un-docked. 
Now I have done an upgrade to gutsy I can only suspend when the laptop is NOT in the docking station.
The suspend seems to start normally when I press the suspend keyboard button (the moon), but after blanking the screen the system just waits for ever. Caps lock and Num lock still work, and Alt-Fn-Sysrq can be used to do an emergency disk sync and shut down the machine, but nothing else works (eg ctrl-alt-del, ctrl-alt-F1)
I have tried both the fglrx and ati video drivers, and tried changing HIBERNATE_MODE to "platform" in /etc/default/acpi-support. I am using "nolapic" in the kernel boot line, to get rid of "APIC error on CPU0: 40(40)", which I also needed for feisty. 
Where can I look to see what is causes the suspend to hang?

---

