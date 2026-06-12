---
title: "ram upgrade"
date: 2011-04-05
forum: Hardware
---

### Post by ilrovato on 2011-04-05
Hello
 I upgraded the ram of an Acer Aspire one (model-AO751H 52bk) to 2 GB (1GB Factory)

 The BIOS and Windows Vista will detect 2GB, while Ubuntu Netbook Remix has been stopped before the upgrade to 1GB (cat / proc / meminfo about 800000MB).

 Solutions?

Linked file "report_ram.txt" with the output of various commands:
df -h>  /tmp/report_ram.txt
echo>>  /tmp/report_ram.txt
dmesg>>  /tmp/report_ram.txt
echo>>  /tmp/report_ram.txt
dmidecode>>  /tmp/report_ram.txt
echo>>  /tmp/report_ram.txt
uname -a>>  /tmp/report_ram.txt
lsb_release -a>>  /tmp/report_ram.txt

[http://www.informaticalombarda.it/nl/report_ram.txt](http://www.informaticalombarda.it/nl/report_ram.txt)

 Thanks Paolo

---

### Post by ilrovato on 2011-04-05
Problem solved

 In the configuration of grub (the boot parameters of the kernel) was added to the option mem = 896MB.
 After I remove it from the file /etc/default/grub and launched the update-grub, rebooted and everything works.

 2GB of ram are now active.

 Thanks, Paolo

---

