---
title: "Toshiba fan control"
date: 2011-03-31
forum: Hardware
---

### Post by WU8V on 2011-03-31
Just picked up a Toshiba Satellite L675D
dual booting with WUBI.

I had to turn ACPI=OFF to get the thing to boot

But....

There seems to be no fan control, and 

The machine will not shut off when using software shutdown.

it just tells me "system halted"

at that point the pwr button will shut it off.

I have tried the ACPI modifiers that I know and sometimes it will get to the line
[ 0.365797 NET:Registered protocal family 1

I everything else SEEMS to be working ok I think, but I need to know if anyone can tell me what else is affected, and if there is a way to get the fan control back with some other ACPI setting??/

Thanks so much

---

### Post by Yellow Pasque on 2011-03-31
No ACPI = no fan. What happens when you try to boot with ACPI?
Do you have the latest BIOS? [http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=2681588&rpn=PSK3JU&modelFilter=L675D-S7022&selCategory=2756709&selFamily=1073768663](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=2681588&rpn=PSK3JU&modelFilter=L675D-S7022&selCategory=2756709&selFamily=1073768663)

---

### Post by WU8V on 2011-03-31
When I try to boot with ACPI It just goes to black screen flashing cursor.

I will need to figure out the bios, I am not sure it is the latest

Thanks

---

### Post by bcbc on 2011-03-31
Try acpi=copy_dsdt (as well as the bios)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/647358](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/647358)

---

### Post by WU8V on 2011-04-01
thanks for the replies so far, but still no joy.

I have updated the BIOS, and I have perused the logs, and I have found that the next line after it hangs (after the "protocal family 1") is to boot the video. 

The video seems to work ok when I run ACPI=off, but when I use =force, or =ht or =copy_dsdt it gets to that point and hangs.

The video driver that I am using was scanned by the machine and  is the ATI/AMD proprietary FGLRX graphics driver

Thanks again for any suggestions.

---

### Post by Moldjelly on 2011-04-01
This was almost doing my head in.
Thought about having to run Windows or sell my new laptop.
Same fan problems with Fedora, PClinuxOS
Here is what works for me. Toshiba L500. 64bit Ubuntu 10.04

first. sudo apt-get install sensors-applet
next. sudo sensors-detect

next. answer yes to everything.

exit then restart computer.

next. sudo gedit /etc/default/grub and then change

GRUB_CMLINE_LINUX_DEFAULT="quiet splash"

to read

..."quiet splash acpi_osi="

next. sudo update-grub to update /boot/grub/grub.cfg

exit then restart computer.
"Add the following to your /etc/modules: (sudo gedit /etc/modules)
battery
ac
thermal
processor
acpi-cpufreq
cpufreq-userspace
Restart after adding."

---

### Post by WU8V on 2011-04-01
Thanks MJ, 

everything seems to go well until changing away from acpi=off

soo as that changes, the machine hangs on trying to boot

regards,
Kurt

---

