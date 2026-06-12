---
title: "SCSI Tape Drive not recognized"
date: 2008-08-25
forum: Hardware
---

### Post by UncleAelfrich on 2008-08-25
I am running ubuntu 8.04 (Xubuntu) and have installed a Quantum DLT-V4 tape drive connected to a LSI 20160 PCI to SCSI HBA. The tape drive is not being recognized. I also don't think the kernel module driver for the SCSI card is being loaded.

However, when I run lshw, it shows that the LSI card is recognized there are scsi0.

I did install mpt-status, but it says that a module is missing. I also installed mt-st,and used the Quantum recommended stinit.def file.

Can anyone help me out so that I can get my linux box to recognize this tape drive (and SCSI card)?

---

### Post by prince_of_hackers on 2008-12-28
I was considering buying one of these cards to use with an external SCSI RAID array that is currently running on a Symbios Sym53c875 chipset - the chipset supports 40 MB/s, but the 2.6 kernel driver is broken, and for some reason won't run past 20 MB/s. In any case, while researching the issue of whether there was kernel support for the LSI 20160, I discovered that the chipset on the card (LSI53C1000) is supported by two different kernel modules - which aren't located in the standard .../kernel/drivers/scsi directory. Instead, the files that are used are mptbase.ko and mptscsih.ko in the .../kernel/drivers/message/fusion directory. Try doing an lsmod to see if those modules are loaded, and if not, try doing this:
```
sudo modprobe mptbase
sudo modprobe mptscsih
tail /var/log/messages
```
If you don't get any error messages after the modprobe lines, the output at the end of the messages log file should show if the card and attached devices were recognized. Post back if this works, or if you encounter any further issues.

---

### Post by UncleAelfrich on 2008-12-28
I was an idiot. The cable from the drive to the LSI card had become disconnected. Once I made sure the cable stayed connected, the computer saw the car.

I have almost decided I have learned about all I want to learn about linux. I'm trying to get either Bacula or Amanda or BackupPC working for a home server, and I have been banging my head against the wall repeating, "I don't want to know this much about linux; I don't want to know this much about Linux."

---

