---
title: "probably an acpi problem"
date: 2005-04-11
forum: Hardware &amp; Laptops
---

### Post by mac_hack on 2005-04-11
Hi ubuntu community , and thank you for your great distro  :wink: 

I experienced many crashes with my old computer , who work with ubuntu hoary final .. I have already experienced the same problem in the past , with mandrake 10 ... It was an acpi problem , who was fixed by a bios update ! I think it's also an acpi problem , but by disabling acpi in the bios , and in the kernel boot ( acpi=off ) , the problem is always here ... ( sorry if you don't understand what i want to say , i speak very bad english lol ...  :-P ) 
all my peripherals freez ( usb , keyboard , mouse ... )  if i don't disable acpi , and if i disable acpi , everything freez , except my mouse lol ... strange  :???: ...

A short list of my peripherals :

amd atlhon 900
Motherboard : via apollo kt133
sound chipset : c-media cmi8738
classic mouse and keyboard ...
384mo of sdram ( good ram )

Hope you will can help me  [-o< , and thank you again for your work , Ubuntu linux is the GREATEST linux distribution , except for acpi management lol   :-#

---

### Post by alastair on 2005-04-11
It might be ACPI but could also be a broken fan (for instance) e.g. check CPU, disk fans etc. Maybe even bad RAM (? check with "memtest" overnight from the boot menu).

The best idea to look at the boot messages in :

/var/log/syslog

and see if there are warnings/errors printed.

---

### Post by mac_hack on 2005-04-12
Thank you for your answer ! I have checked my fans , and they work very well , the temperature is normal ( 48° Celcius for the cpu , and nearly 45° for HD and graphic card ... ) . I have also made a memtest , who was succesful  :-P !

in /var/log/syslog , i found a problem ( about acpi ) :

Apr 11 19:23:44 localhost kernel: shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
Apr 11 19:23:44 localhost kernel: shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
Apr 11 19:23:44 localhost kernel: pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
Apr 11 19:23:44 localhost kernel: pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5

Help ... i need somebody ... help  ;-)

---

### Post by mac_hack on 2005-04-12
no idea ? 
please  [-o<

---

### Post by luca_linux on 2005-04-12
Try to pass "nolapic" as kernel parameter at boot.

---

### Post by mac_hack on 2005-04-13
Thank you ! I try to see if it crash now ... i wait  :wink: 

But i have a question : how we can save the boot parameter ? because when i edit the boot line ( button "e" ) , i press "B" to boot with , but after rebooting the computer , the boot line is without "nolapic" ...

---

### Post by luca_linux on 2005-04-13
> sudo gedit /boot/grub/menu.lst
And add the parameter to the respective item.

---

### Post by mac_hack on 2005-04-20
Thank you again for your help !

But it doesn't solved the problem ...

I think this bug was caused by APM ( Advanced Power Management ) , because i have disabled it on the boot ( sudo update-rc.d -f apmd remove ) and it doesn't freez until now ... I will confirm if it was really the problem !

---

