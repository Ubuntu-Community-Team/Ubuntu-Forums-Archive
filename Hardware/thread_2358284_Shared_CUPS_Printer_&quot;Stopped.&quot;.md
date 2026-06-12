---
title: "Shared CUPS Printer &quot;Stopped.&quot;"
date: 2017-04-11
forum: Hardware
---

### Post by Benjamin_Hall on 2017-04-11
We recently got a new USB printer and I have succesfully installed the necessary driver on one of our computers running Ubuntu. Under the printer settings, I've enabled sharing. However, on my other Ubuntu computer, although it recognizes the presence of the printer, it reads "Stopped - The printer configuration is incorrect or the printer no longer exists." Any solutions?

---

### Post by pdc on 2017-04-11
Hi Benjamin;

do give us a little info: which version of ubuntu are the 2 computers running; which printer is it; what printer driver is installed; how is the second computer connected to the first; 

what does ```
lpinfo -v
``` give from both computers; and what does ```
dpkg -l cups*
``` give

_______________-

```
We recently got a new USB printer
```        .........so ............ have you got 2 usb printers now connected to computer 1?

---

### Post by Benjamin_Hall on 2017-04-11
Both computers are running Ubuntu 14.04 LTS and the printer is a Brother HL-L2320D using the driver provided by Brother, running on CUPS. The two computers are only connected through the router (using same network). 
```
lpinfo -v
```  gives:
```
[COLOR=#000000][FONT=Ubuntu]direct usb://Brother/HL-L2320D%20series?serial=U63877L6N234169[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]network ipp[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]network https[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]network ipp14[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]serial serial:/dev/ttyS0?baud=115200[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]network ipps[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]network http[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]network socket[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]direct parallel:/dev/lp0[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]direct hp[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]network smb[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]direct hpfax[/FONT][/COLOR]
``` on computer #1 (printer directly connected)

and gives:

```
network ipp
network https
network ipps
network http
network socket
network lpd
serial serial:/dev/ttyS0?baud=115200
network ipp14
direct parallel:/dev/lp0
network smb
direct hp
direct hpfax
network dnssd://HLL2320D%20%40%20schoolroom-tabea._ipp._tcp.local/cups
``` from computer #2.

```
dpkg -l cups*
``` gives:

```
[COLOR=#000000][FONT=Ubuntu]Desired=Unknown/Install/Remove/Purge/Hold[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]||/ Name                       Version            Architecture       Description[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]+++-==========================-==================-==================-=========================================================[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]ii  cups                       1.7.2-0ubuntu1     amd64              Common UNIX Printing System(tm) - PPD/driver support, web[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]ii  cups-browsed               1.0.52-0ubuntu1    amd64              OpenPrinting CUPS Filters - cups-browsed[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]ii  cups-bsd                   1.7.2-0ubuntu1     amd64              Common UNIX Printing System(tm) - BSD commands[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]ii  cups-client                1.7.2-0ubuntu1     amd64              Common UNIX Printing System(tm) - client programs (SysV)[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]ii  cups-common                1.7.2-0ubuntu1     all                Common UNIX Printing System(tm) - common files[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]ii  cups-core-drivers          1.7.2-0ubuntu1     amd64              Common UNIX Printing System(tm) - PPD-less printing[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]ii  cups-daemon                1.7.2-0ubuntu1     amd64              Common UNIX Printing System(tm) - daemon[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]ii  cups-driver-gutenprint     5.2.10~pre2-0ubunt all                transitional dummy package for gutenprint printer driver[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]ii  cups-filters               1.0.52-0ubuntu1    amd64              OpenPrinting CUPS Filters - Main Package[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]ii  cups-filters-core-drivers  1.0.52-0ubuntu1    amd64              OpenPrinting CUPS Filters - PPD-less printing[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]un  cups-pdf                   <none>             <none>             (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]ii  cups-pk-helper             0.2.5-0ubuntu1     amd64              PolicyKit helper to configure cups with fine-grained priv[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]ii  cups-ppdc                  1.7.2-0ubuntu1     amd64              Common UNIX Printing System(tm) - PPD manipulation utilit[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]ii  cups-server-common         1.7.2-0ubuntu1     all                Common UNIX Printing System(tm) - server common files[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]un  cupsddk                    <none>             <none>             (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]un  cupsomatic-ppd             <none>             <none>             (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]ii  cupswrapperhl2242d         2.0.4-2            i386               Brother HL2242D CUPS wrapper driver[/FONT][/COLOR]
``` on computer #1

and gives:
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  cups           1.7.2-0ubunt amd64        Common UNIX Printing System(tm) -
ii  cups-browsed   1.0.52-0ubun amd64        OpenPrinting CUPS Filters - cups-
ii  cups-bsd       1.7.2-0ubunt amd64        Common UNIX Printing System(tm) -
ii  cups-client    1.7.2-0ubunt amd64        Common UNIX Printing System(tm) -
ii  cups-common    1.7.2-0ubunt all          Common UNIX Printing System(tm) -
ii  cups-core-driv 1.7.2-0ubunt amd64        Common UNIX Printing System(tm) -
ii  cups-daemon    1.7.2-0ubunt amd64        Common UNIX Printing System(tm) -
ii  cups-driver-gu 5.2.10~pre2- all          transitional dummy package for gu
ii  cups-filters   1.0.52-0ubun amd64        OpenPrinting CUPS Filters - Main 
ii  cups-filters-c 1.0.52-0ubun amd64        OpenPrinting CUPS Filters - PPD-l
un  cups-pdf       <none>       <none>       (no description available)
ii  cups-pk-helper 0.2.5-0ubunt amd64        PolicyKit helper to configure cup
ii  cups-ppdc      1.7.2-0ubunt amd64        Common UNIX Printing System(tm) -
ii  cups-server-co 1.7.2-0ubunt all          Common UNIX Printing System(tm) -
un  cupsddk        <none>       <none>       (no description available)
un  cupsomatic-ppd <none>       <none>       (no description available)
``` on computer #2

We only have one printer connected to #2.

---

### Post by Benjamin_Hall on 2017-04-11
I wanted to report that this issue has been solved. I deleted the automatically setup printer, and re-entered the printer information manually, and the error message dissappeared.

---

### Post by pdc on 2017-04-12
well done; glad it is solved; that looks a great printer you have there

---

