---
title: "Ubuntu 10.4 does no boots"
date: 2010-08-12
forum: Hardware
---

### Post by abhijit1206 on 2010-08-12
Hi, 
I am using toshiba satellite c650
i have installed ubuntu 10.4 but it does not boot normally.
i read in the forms and set acpi=off
but every time i nedd to boot ubuntu i have to do this so can any one please tell me a permenanent solution for this .
Also ubuntu does not detect my wired network
please help????

---

### Post by Unknown-Demon on 2010-08-12
What error message do you get when you boot?

---

### Post by Narendran95 on 2010-12-01
hey i have this same problem...

My friend bought a brand new TOSHIBA Satellite c650 laptop and told him about ubuntu and asked him to try it. When he saw it on my lap, he liked it .I have customized and made the ubuntu in my laptop amazing so I was planning to clone the hard disk. I once cloned the ubuntu in my Ext HDD into my laptop and it worked well. But when I try to boot it from Ext HDD on his Laptop, there's a lot of code running and it get's stuck with :
" Kernel_thread_helper_0x7-" and something like that. It also mentioned a lot about:
" acpi-init" and " acpi-fail" and stuff like that. So on the grub menu, I typed "e" and edited the options. I added "acpi=off noapic" and it booted fine. But that happens only once as the config is not saved. So I edited the "/etc/grub.d/40_custom" file and added these options to the grub boot menu. 

Now, whenever he boots his laptop, the grub menu is automatically skipped and the "kernel_thread_helper" error reappears. But when I remove the battery, put it back in (to remove power supply to turn it off) and THEN boot (this is almost like every even time we boot), the grub menu appears and if we select the last option (custom menu we createrd with acpi=off, then it boot's normally.

Please HELP!

---

