---
title: "Printer Configuration lost after reboot"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by bumpkin on 2009-06-12
Just installed Kubuntu 9.04. I add a printer and it works fine. Then after a reboot it is gone.  

lpoptions in my .cups directory has 

"default HP_laserjet_1100"


Where is a good place to start looking for the cause?


Here is my printers.conf file 

# Printer configuration file for CUPS v1.3.9
# Written by cupsd on 2009-06-11 22:04
<DefaultPrinter HP_LaserJet_1100>
Info HP_laserjet_1100
Location quirky
DeviceURI parallel:/dev/lp0
State Idle
StateTime 1243747942
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

Here is the error.log

E [11/Jun/2009:18:34:42 -0700] Syntax error on line 11 of printers.conf.
E [11/Jun/2009:20:29:16 -0700] Syntax error on line 11 of printers.conf.
E [11/Jun/2009:21:27:46 -0700] [CGI] Unable to scan "@LOCAL"!
E [11/Jun/2009:21:28:20 -0700] PID 5590 (/usr/lib/cups/daemon/cups-driverd) crashed on signal 9!
E [11/Jun/2009:21:28:51 -0700] [CGI] Unable to scan "@LOCAL"!
E [11/Jun/2009:21:36:51 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [11/Jun/2009:21:41:44 -0700] Syntax error on line 11 of printers.conf.
E [11/Jun/2009:22:02:16 -0700] [CGI] Unable to scan "@LOCAL"!
E [11/Jun/2009:22:04:23 -0700] CUPS-Add-Modify-Printer: Unauthorized

Anyone have suggestions on how to fix this?

---

### Post by mdlueck on 2010-10-29
I, as a work around, command line script attach to the printer(s) at boot-up. Please see the following blog post: [http://www.lueckdatasystems.com/HOW-TO_Command_Line_Connect_to_a_CUPS_Network_Printer_for_Ubuntu_Linux](http://www.lueckdatasystems.com/HOW-TO_Command_Line_Connect_to_a_CUPS_Network_Printer_for_Ubuntu_Linux)

---

