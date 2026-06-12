---
title: "Ubuntu 17.10 Budgie and Canon Imageclass MF229dw Printer"
date: 2017-10-19
forum: Hardware
---

### Post by bobpok on 2017-10-19
I just did a clean install of Ubuntu 17.10 Budgie desktop.  I am unable to print to a Canon Imageclass MF229dw.  Installed the latest Canon drivers available &#8211; &#8220;linux-UFRII-drv-v340-uken&#8221; which includes the following two driver files &#8211;&#8220;cndrvcups-common_3.80-1_amd64.deb&#8221; and&#8220;cndrvcups-ufr2-uk_3.40-1_amd64.deb&#8221;.  When I attempt to print a file, nothing prints &#8211; no error messages.  In fact, an information message is issued by Ubuntu implying that the file was successfully printed.  There are no pending files in the print queue.  I defined the printer via the CUPS localhost:631 interface (as I have always done in the past).

I attempted to configure the printer several different connection typesto get it to work, but all were unsuccessful:

[LIST]
[*]connection:     socket://xxx.xxx.xxx.xxx
[*]connection:     dnssd://Canon%20MF220._ipp._tcp.local/?uuid=xxxxxxx
[*]connection:     ipp://Canon-MF229dw.local:631/ipp/print
[/LIST]

I also attempted each of the above connection types with two different drivers (actually, one &#8220;driverless&#8221;):

[LIST]
[*]Canon    MF220 Series (gray scale, 2-sided printing)&#8221;  - the driver I    installed
[*]CNMF220    Series, driverless, cups-filters 1.17.9&#8221;     - &#8220;driverless&#8221;
[/LIST]

I had no success with any of these variations.
I have used the same version of these driver files on my SolydX (Debian9 Stretch) system to the same printer and it works fine &#8211; i.e., it prints.

Any suggestions are appreciated.

---

### Post by pdc on 2017-10-20
the only comment I could make at this stage is that I had understood that from 17.04, that ubuntu was implementing airprint support; and checking the list the MF229DW is airprint-compatible (APC) [https://support.apple.com/en-nz/HT201311](https://support.apple.com/en-nz/HT201311) and I had understood the hope was that would mean the user would not need to install drivers;  and so I was wondering if that explained the > “CNMF220 Series, driverless, cups-filters 1.17.9” - “driverless”

I wondered if you had filed a bug report to Ubuntu on this

---

### Post by bobpok on 2017-10-20
Thank you for the tips.  I was unaware of the support of air-print in Ubuntu.  Before going down that path, I checked out one 
additional site –[https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems) and focused on the “Network Printer” section.  I installed 
the“system-config-printer” package and configured the printer using that application.

I configured the printer using the following connection:  
[COLOR=#000000][FONT=Liberation Serif]dnssd://Canon%20MF220._ipp._tcp.local/?uuid=xxxxxxxxxxxxxxxxxx[/FONT][/COLOR]

[COLOR=#000000][FONT=Liberation Serif]I selected the following driver – not the drivers from the Canon driver package:[/FONT][/COLOR]
[COLOR=#000000][FONT=Liberation Serif]CNMF220Series, driverless, cups-filters 1.17.9 (grayscale, 2-sided printing)[/FONT][/COLOR]

[COLOR=#000000][FONT=Liberation Serif]I was pleasantly surprised when I was able to print on the first attempt.  I have not done any additional investigation as to why the 
Canon-supplied drivers are not working. [/FONT][/COLOR]

---

### Post by pdc on 2017-10-20
thanks; glad to hear the printer is working; looks like a very nice machine; I am guessing it is set up using airprint: the hope is that will do the work for everyone as many recent printers are compatible; so it gets labelled as driverless

the 3.4 version of Canon's driver was issued 14th July this year; so Canon are doing their best to keep up; and I have guided others on how to use that 3.4; and they have been happy: using 16.04 versions I think; did you use the install script that comes with the package?

what does ```
dpkg -l cndrvcups*
``` give please?

---

### Post by bobpok on 2017-10-21
As requested, the output of the "dpkg -l cndrvcups*" command is:

```

bob@TP-X1C3-Ubuntu:~$ dpkg -l cndrvcups*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  cndrvcups-capt <none>       <none>       (no description available)
ii  cndrvcups-comm 3.80-1       amd64        Canon Printer Driver Common Modul
un  cndrvcups-lips <none>       <none>       (no description available)
un  cndrvcups-lips <none>       <none>       (no description available)
un  cndrvcups-ps3- <none>       <none>       (no description available)
un  cndrvcups-ufr2 <none>       <none>       (no description available)
ii  cndrvcups-ufr2 3.40-1       amd64        Canon UFR2 Printer Driver for Lin
bob@TP-X1C3-Ubuntu:~$


```

---

