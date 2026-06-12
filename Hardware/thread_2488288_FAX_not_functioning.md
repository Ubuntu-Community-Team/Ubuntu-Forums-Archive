---
title: "FAX not functioning"
date: 2023-06-29
forum: Hardware
---

### Post by csae2608 on 2023-06-29
Hello ,


i have received a complete printer with FAX function;

however, i don§t seem to get the FAX function working under linux.



it is a Epson Ecotank printer (ET-5170) and there are some dedicated drivers for Ubuntu, however, i do get error when installing those;
in addition, there is a socalled "driverless" package, but those seem to function worse.


please help if possible,




```
sudo dpkg -i eps*.deb
(Reading database ... 314000 files and directories currently installed.)
Preparing to unpack epson-inkjet-printer-escpr2_1.1.62-1lsb3.2_amd64(1).deb ...
Unpacking epson-inkjet-printer-escpr2 (1.1.62-1lsb3.2) over (1.1.62-1lsb3.2) ...
Preparing to unpack epson-inkjet-printer-escpr2_1.1.62-1lsb3.2_amd64.deb ...
Unpacking epson-inkjet-printer-escpr2 (1.1.62-1lsb3.2) over (1.1.62-1lsb3.2) ...
Preparing to unpack epson-pc-fax_1.0.0-1lsb3.2_amd64 (1).deb ...
Unpacking epson-pc-fax (1.0.0-1lsb3.2) over (1.0.0-1lsb3.2) ...
Preparing to unpack epson-pc-fax_1.0.0-1lsb3.2_amd64.deb ...
Unpacking epson-pc-fax (1.0.0-1lsb3.2) over (1.0.0-1lsb3.2) ...
Preparing to unpack epson-printer-utility_1.1.1-1lsb3.2_amd64.deb ...
Unpacking epson-printer-utility (1.1.1-1lsb3.2) over (1.1.1-1lsb3.2) ...
More than one copy of package epson-inkjet-printer-escpr2 has been unpacked
 in this run !  Only configuring it once.
More than one copy of package epson-pc-fax has been unpacked
 in this run !  Only configuring it once.
Setting up epson-inkjet-printer-escpr2 (1.1.62-1lsb3.2) ...
Setting up epson-pc-fax (1.0.0-1lsb3.2) ...
&#9675; cups.service - CUPS Scheduler
     Loaded: loaded (/lib/systemd/system/cups.service; enabled; vendor preset: enabled)
     Active: inactive (dead) since Thu 2023-06-29 22:49:35 CEST; 3ms ago
TriggeredBy: × cups.socket
             × cups.path
       Docs: man:cupsd(8)
    Process: 9596 ExecStart=/usr/sbin/cupsd -l (code=exited, status=0/SUCCESS)
   Main PID: 9596 (code=exited, status=0/SUCCESS)
     Status: "Scheduler is running..."
        CPU: 14ms

giu 29 22:49:35 rich-MS-7A38 systemd[1]: Starting CUPS Scheduler...
giu 29 22:49:35 rich-MS-7A38 systemd[1]: Started CUPS Scheduler.
giu 29 22:49:35 rich-MS-7A38 systemd[1]: Stopping CUPS Scheduler...
giu 29 22:49:35 rich-MS-7A38 systemd[1]: cups.service: Deactivated successfully.
giu 29 22:49:35 rich-MS-7A38 systemd[1]: Stopped CUPS Scheduler.
giu 29 22:49:35 rich-MS-7A38 systemd[1]: Dependency failed for CUPS Scheduler.
giu 29 22:49:35 rich-MS-7A38 systemd[1]: cups.service: Job cups.service/start failed with result 'dependency'.
Setting up epson-printer-utility (1.1.1-1lsb3.2) ...
Install Message > Start /usr/lib/epson-backend/setup to change setup.
Processing triggers for libc-bin (2.35-0ubuntu3.1) ...

```


when i then click "print test page" nothing happens for Epson PC FAX.


Ubuntu is version 22.04 LTS, maybe thats the issue?


Thank you very much.


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292432&stc=1[/IMG]

---

