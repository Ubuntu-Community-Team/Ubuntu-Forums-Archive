---
title: "problems with SCSI harddisk"
date: 2005-04-04
forum: Hardware &amp; Laptops
---

### Post by dukeleto on 2005-04-04
Hi all,
I recently installed ubuntu on my workstation, as an upgrade to the aging redhat 7.3 that it used to run on. 
Since then, I've had a number of harddisk errors, which I've noticed because by default Ubuntu mounts the / with "errors=ro" . 
Looking at /var/log/dmesg, I see stuff like : 

[FONT=Fixedsys]Linux agpgart interface v0.100 (c) Dave Jones
SCSI error : <0 0 0 0> return code = 0x8000002
Info fld=0x18be4dd, Current sda: sense key Medium Error
Additional sense: Read retries exhausted
end_request: I/O error, dev sda, sector 25945250
[/FONT]

for various disk sectors, does that mean there are bad sectors?
In /var/log/syslog I get stuff like 

[FONT=Fixedsys] kernel: EXT3-fs error (device sda 7) in start_transaction: Journal has aborted
Apr  3 07:37:40 bruxelles last message repeated 23 times
[/FONT]

Any suggestions? Do I need to change the disk  :confused: 
Thanks,
Olivier

---

### Post by alastair on 2005-04-04
Could be the disk going bad - but perhaps only cabling. With SCSI, always check the cables and any termination first. Perhaps try a new cable?

---

### Post by dukeleto on 2005-04-05
Thanks, I'll try and move the wires, see whether that improves anything

---

