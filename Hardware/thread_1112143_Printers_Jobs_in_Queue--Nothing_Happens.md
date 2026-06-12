---
title: "Printers Jobs in Queue--Nothing Happens"
date: 2009-03-31
forum: Hardware
---

### Post by DavidDee on 2009-03-31
I am new to Linux and am installing Ubuntu 8.10 on a Lenovo 3000 v100 laptop and trying to get a printer to work. I've tried the following three printers that are listed in my  /etc/cups/printers.conf file: (in fact the whole file is at the end of this posting)

<Printer -Photo-AIO-Printer-966> Dell
<Printer A920> Dell
<Printer MX310-series> Canon

Here's what the queue looks like after I click Print with the A920 printer selected:
_________________________________________________
david@david-lenovo:~$ lpq -a
Rank    Owner   Job     File(s)                         Total Size
active  david   7       Bookmarks                       107520 bytes


Why job 7 ?  Following my salutation is output from some other commands. Any tips appreciated. Thanks

David


_________________________________________________
david@david-lenovo:~$ lpinfo -v
network socket
network beh
direct hal:///org/freedesktop/Hal/devices/usb_device_413c_5106_167GS41_if0_printer_noserial
direct usb://Dell%20/A920
direct hpfax
direct hp
network http
network ipp
network lpd
direct scsi
network smb

david@david-lenovo:~$ lpstat -s
no system default destination
device for -Photo-AIO-Printer-966: usb://Dell/%20Photo%20AIO%20Printer%20966
device for A920: usb://Dell%20/A920
device for MX310-series: usb://Canon/MX310%20series
device for MX310-series-FAX: usb://Canon/MX310%20series%20FAX

__________________________________________________
# Printer configuration file for CUPS v1.3.9
# Written by cupsd on 2009-03-31 07:31

<Printer -Photo-AIO-Printer-966>
Info Dell  Photo AIO Printer 966
Location david-lenovo
DeviceURI usb://Dell/%20Photo%20AIO%20Printer%20966
State Stopped
StateMessage Unplugged or turned off
StateTime 1238458961
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

<Printer A920>
Info Dell  A920
Location david-lenovo
DeviceURI usb://Dell%20/A920
State Idle
StateTime 1238509899
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

<Printer MX310-series>
Info Canon MX310 series
Location david-lenovo
DeviceURI usb://Canon/MX310%20series
State Stopped
StateMessage Unplugged or turned off
StateTime 1238502719
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

<Printer MX310-series-FAX>
Info Canon MX310 series FAX
Location david-lenovo
DeviceURI usb://Canon/MX310%20series%20FAX
State Stopped
StateMessage Unplugged or turned off
StateTime 1238502719
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

---

