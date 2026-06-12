---
title: "CanoScan2700F"
date: 2007-01-08
forum: Hardware &amp; Laptops
---

### Post by alarikus on 2007-01-08
My OS is ubuntu 6.06 LTS Dapper Drake.
I use an USB multifunction printer/scanner Canon PIXMA MP170
and a SCSI 35mm film scanner Canon CanoScan 2700F.
PIXMA MP170 works fine under TurboPrint 1.95-1 (as printer)
and under Wittawat Yamwong's driver mp150-0.12.2 (as scanner).
Coming to CanoScan 2700F, I installed Sane backends v1.0.18.
Just after installation all works, but if I reboot the film scanner 
stops with working, as if something had automatically 
changed during the startup.


I uncommented the line /dev/sg0 in /etc/sane.d/canon.conf
and set up the permissions with chmod +rwx sg0 sdb. 


The output of the command cat /proc/scsi/scsi is:

Attached devices:
Host: scsi0 Channel: 00 Id: 05 Lun: 00
  Vendor: CANON    Model: IX-27015C        Rev: 1.17
  Type:   Scanner                          ANSI SCSI revision: 02
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: USB 2.0  Model: Flash Disk       Rev: 3000
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: Canon    Model: MP170Storage     Rev: 0108
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi3 Channel: 00 Id: 00 Lun: 00
  Vendor: Initio   Model: 6L250R0          Rev: 1.11
  Type:   Direct-Access                    ANSI SCSI revision: 02

meaning, I suppose, that both the AVA2904 SCSI adapter and the film scanner 
are phisically detected by the system.


The output of the command sane-find-scanner is:
...
found SCSI scanner "CANON IX-27015C 1.17" at /dev/sg0
...
found USB scanner (vendor=0x04a9 [Canon], product=0x170a [MP170]) at libusb:006:004
  # ... Try scanimage -L and read the backend's manpage.
...

meaning, I suppose, that both the scanners are logically detected by the OS.


The command ls -l issued in /dev answers:
...
brwxrwxr-x 1 root scanner  8, 16 2007-01-07 13:26 sdb 	[PIXMA MP170]
crwxrwxr-x 1 root scanner 21,  0 2007-01-07 13:26 sg0 	[CanoScan 2700F]
...

while the command scanimage -L answers:
...  
device `pixma:04A9170A_B3AF11' is a CANON Canon PIXMA MP170 multi-function peripheral
...

The film scanner is missing. After having reinstalled all the gear from the scratch I got the same result.
Is there anybody out there in the outback willing to help me?
Thanks a (big) lot.

alarikus ](*,) 
[email]sergiodaltio@hotmail.com[/email]

---

