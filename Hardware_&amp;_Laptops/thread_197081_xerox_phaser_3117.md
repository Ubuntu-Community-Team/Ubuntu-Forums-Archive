---
title: "xerox phaser 3117"
date: 2006-06-15
forum: Hardware &amp; Laptops
---

### Post by drtvasudevan on 2006-06-15
my printer is xerox phaser 3117
tried to set it up.
there is no 3117 ppd as such
what is there is 3115 which is supposed to work.
[http://ubuntuforums.org/showthread.php?p=1140571#post1140571](http://ubuntuforums.org/showthread.php?p=1140571#post1140571)

tried setting up through system admin printer add printer.
now a printer is recognised (of course it searched and found xerox phaser 3117 correctly) and named xerox 3115.
test page wont print.

looked at the printer.conf
here it is

> # Printer configuration file for CUPS v1.2.0
# Written by cupsd on 2006-06-15 15:23
<Printer Xerox-Phaser-3115>
Info ganesa
Location local
DeviceURI usb://Xerox/Phaser%203117
State Stopped
StateMessage Filter "ppmtospl2" for printer "Xerox-Phaser-3115" not available: No such file or directory
StateTime 1150365225
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy stop-printer
</Printer>

what has happened?
what can i do?

---

