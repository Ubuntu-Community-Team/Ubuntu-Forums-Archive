---
title: "Can't print from new Ubuntu machine, printer works fine from other computers"
date: 2008-02-29
forum: Hardware &amp; Laptops
---

### Post by elfprince13 on 2008-02-29
My mom's iMac G3 is starting to experience hard drive failure, so I've almost completely migrated her to a Dell with Ubuntu installed. The biggest hitch left is that our old Personal LaserWriter 320 is a Localtalk printer. We have it connected to the ethernet network via an AsanteTalk bridge, and all the computers in the house can print to it (the G3, my dad's macbook, even my Toshiba laptop running XP can usually print a page or 2 to it), except the new Ubuntu machine. I configured it according to the instructions here: [https://help.ubuntu.com/community/AppleTalk](https://help.ubuntu.com/community/AppleTalk)

nbplkup returns the following:

> administrator@Mirkwood:~$ nbplkup
                       Mirkwood:AFPServer                          65280.208:128
                       Mirkwood:netatalk                           65280.208:4
                       Mirkwood:Workstation                        65280.208:4
                      Rivendell:Darwin                             20.252:128
                      Rivendell:AFPServer                          20.252:129
           AsantéTalk 94B806A9:                Arwen Dickerson:LaserWriter                        65438.136:128


I set up my /etc/cups/printers.conf file up as according to the tutorial (with pap://*/Arwen Dickerson/LaserWriter), and went to the cups web interface to print a test page

I got the following message:
> ArwenDickerson "/usr/lib/cups/backend/pap failed"

I was a little annoyed by this, so I went back and ran /usr/lib/cups/backend/pap with no arguments to make sure I had typed my URI correctly and got the following:
> administrator@Mirkwood:~$ /usr/lib/cups/backend/pap
network pap "Unknown" "AppleTalk Devices via pap"
atp_rresp: Connection timed out
/usr/lib/cups/backend/pap: 1: /usr/bin/timeout: not found
-e network pap://%2a/Arwen%20Dickerson/LaserWriter "Unknown" "Arwen Dickerson@* (pap)"


I decided it must have been a simple case of the tutorial not mentioning that my URI should have the special characters escaped, and updated the printer accordingly via the Cups web interface. I also googled around for the correct .ppd file, and installed that to make sure all the settings were tweaked to match our printer hardware.

Same error.
Getting frustrated now, I went back onto our iMac and copied the configuration out of the os x printers.conf (just a change in URI, this time to pap://*/Arwen%20Dickerson/LaserWriter). Still nothing. unfortunately the OS X pap backend is a binary file, not a shell script so I can't try that, but if anyone could give me a hand that would be great.

my current printers.conf
> # Printer configuration file for CUPS v1.3.2
# Written by cupsd on 2008-02-29 21:23
<Printer ArwenDickerson>
Info Personal LaserWriter 320
Location Local zone
DeviceURI pap://*/Arwen%20Dickerson/LaserWriter
State Idle
StateTime 1204315449
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>



[edit]

I GOT IT WORKING. I'm gonna go fix the wiki now.

---

