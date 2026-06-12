---
title: "DVDs and CDs not recognized"
date: 2011-05-06
forum: Hardware
---

### Post by Ginosal on 2011-05-06
Hi. My computer had always read cds and dvds, but now it doesn't anymore. When I put a cd or dvd into the drive, it just makes the usual noise, the LED blinks, but nothing happens.

*dmesg | grep CD-ROM* gives me nothing

*sudo lshw -C disk* gives me
```
[sudo] password for ginosal: 
  *-disk                  
       description: ATA Disk
       product: Hitachi HTS54503
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: PB3O
       serial: 100915PBNC04EYK6YDPR
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=75878572
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
```

The kernel version is 2.6.35-28-generic

*cdrecord -scanbus* shows:```

wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.
```

What can I do? Please, help me. Thanks in advance

---

### Post by ajgreeny on 2011-05-06
Sounds like a hardware fault.  Can you run a live USB of ubuntu or another distro and then try a CD in the drive.

If that works then the drive itself is OK, if not then get a new CD drive; they're not expensive these days.

---

### Post by Ginosal on 2011-05-07
> **ajgreeny said:**
> Sounds like a hardware fault.  Can you run a live USB of ubuntu or another distro and then try a CD in the drive.

If that works then the drive itself is OK, if not then get a new CD drive; they're not expensive these days.

Hi. First of all thanks for your answer. I wanted to say that I tried to see if it worked on Windows 7 and it didn't, but on the next reboot Windows 7 has made 20 updates. Probably one of them was the update for the firmware of the cd/dvd drive, because everything worked fine after the reboot, in Linux as in Windows.

---

### Post by ajgreeny on 2011-05-07
Can you therefore please mark this thread as solved from the **Thread Tools** menu at the top right.

---

