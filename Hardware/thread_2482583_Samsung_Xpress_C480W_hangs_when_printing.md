---
title: "Samsung Xpress C480W hangs when printing"
date: 2023-01-04
forum: Hardware
---

### Post by hnpilot on 2023-01-04
When I try to print my C480W printer Ubuntu (CUPS) seems to print but printer LCD shows Printing (until eternity).

I have installed printer driver from Samsung (version uld_V1.00.39_01.17) and run the install-printer.sh-command.

The printer is in my local network and it works fine from Windows computers.

Scanning works just fine from Ubuntu.

My lpinfo -v gives the following info:

network beh
network ipp
file cups-brf:/
network https
network http
network ipps
network socket
network lpd
serial serial:/dev/ttyS0?baud=115200
direct hp
direct hpfax
network socket://192.168.200.111
network ipp://192.168.200.111
network dnssd://Samsung%20C48x%20Series%20(SEC84251901AC4A)._printer._tcp.local/
network socket://192.168.200.111
network ipp://Samsung%20C48x%20Series%20(SEC84251901AC4A)._ipp._tcp.local/

Any help would be very much appreciated

---

