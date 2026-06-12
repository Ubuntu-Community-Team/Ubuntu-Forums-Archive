---
title: "Can not get printing to a network prinserver to work (extensively tested)"
date: 2008-09-15
forum: Hardware
---

### Post by Master One on 2008-09-15
We have a 3-port parallel printserver here, that must have been purchased about 5 years ago, but was not in use until now. The label in the device says "GP303M3CE", the info from the embedded webserver tells "Device Name: PS45CEB0" and "Model: 3P/9E-7.6.33A". The packaging only has a "get Net" label on it. That printserver supports the following modes:

Raw Print: Enable
IPP Print: Enable
LPR Print: Enable
AppleTalk Printing: Enable
Bonjour Printing: Not Supported
NetWare Binary Printing: Enable
SMB: Enable
SNMP: Enable
NETBEUI: Enable

If interested in taking a closer look, please have a look at the **[manual](http://getnetusa.com/copy/download/manual/GP-xx03_M.pdf)** for that device (which explicitly supports Unix/Linux as well).

Nevertheless I just can not get printing from my Ubuntu Hardy 8.04 workstation to work, and it can not be the printserver's fault, because printing from a WinXP machine just works in all relevant modes (SMB / Windows Neighborhood, IPP and LPR). In my tests I always print to the first printer port, which is connected to a Brother HL-1430 laserprinter, that is well supported by foomatic. The hostname and local DNS name of the printserver is PRIVATPRINT (just mentioning that, so that nobody wastes time asking if the printserver is resolved properly, which is the case here).

When trying to print from Ubuntu Hardy 8.04 over

- SMB: The SMB-Browser of the printer dialog does not find the printserver (although it shows up when using Nautilus smb://localnet/), so I enter the correct uri **smb://PRIVATPRINT/P1** manually. Using "Verify" results in "verified - this printer-share can be accessed". Trying to print the testpage does not result in anything on the printer (not even "Ready" and "Data" LEDs light up), the network LED on the printserver flashs some times, and that's it. This is, what /var/log/cups/error_log shows:```
E [15/Sep/2008:16:42:02 +0200] cupsdAuthorize: Local authentication certificate not found!
E [15/Sep/2008:16:42:02 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [15/Sep/2008:16:42:43 +0200] [Job 35] No ticket cache found for userid=0
E [15/Sep/2008:16:42:43 +0200] [Job 35] Can not get the ticket cache for root
E [15/Sep/2008:16:42:54 +0200] [Job 35] Error writing spool: ERRSRV - ERRnosupport (Function not supported.)
E [15/Sep/2008:16:43:07 +0200] PID 5760 (/usr/lib/cups/filter/foomatic-rip) stopped with status 1!
E [15/Sep/2008:16:43:07 +0200] [Job 35] Job stopped due to filter errors.
```

- IPP: The manual of the printserver tells to use an uri in the form of **[http://privatprint:631/lpt1](http://privatprint:631/lpt1)**, but using the add-printer-dialog, I only get a resulting uri of ipp://privatprint/lpt1, and I have no idea, if that is relevant. Entering **privatprint:631** in the field for Host, and using the "Search queue" function, I only get the error message "Not possible - It is not possible to get a list of queues from that host". So I manually enter **/lpt1** in the field for Queue. Using "Verify" results in "verified - this printer-share can be accessed". Trying to print the testpage does not give any results. I can see the network LED of the printserver flash some times, but nothing on the printer, and then the printserver just reboots. Strangely it only gives this in /var/log/cups/error_log:```
E [15/Sep/2008:17:10:49 +0200] cupsdAuthorize: Local authentication certificate not found!
E [15/Sep/2008:17:11:06 +0200] cupsdAuthorize: Local authentication certificate not found!
E [15/Sep/2008:17:11:06 +0200] CUPS-Add-Modify-Printer: Unauthorized
```
Changing the device-uri from ipp://privatprint/lpt1 to [http://privatprint:631/lpt1](http://privatprint:631/lpt1) does not change anything.

- LPR: Entering "privatprint" in the field for Host, and pressing the button "Recognition" makes the network LED on the printserver flash for some times, but nothing else happens, the dropdown for Queue stays empty, so I manually enter "lpt1" in the field for Queue. Trying to print the testpage makes the network LED on the printserver flash, then the printer starts with flashing "Ready" and "Data" LEDs, but then the two printer LEDs just keep being lightened up, and nothing more happens. If I now press the button on the printer's front (it only has one button), it prints a testpage with the Ubuntu label on top, then a Grayscale bar, and grayscale bars for Red/Green/Blue (the testprint only covers less than 1/2 of the page), but afterwards the printserver crashed, the Gnome print-dialog and the status page of the cups-webserver just showed "LPR-Job recording, 34% finished ..." and stayed that way, till I stop and restart the printer directly in cups over the cups-webserver, and pulled to power-plug of the printserver, to regain access to it after power-restore. After that test with the testpage, I tried to print a page from a PDF-document in Evince, but exactly the same happened: LEDs on the printer came on, I had to press the button, it printed less than 1/2 of the page, the printer-dialog and printer page of the cups webserver showed "LPR-Job recording, 19% finished ..." and printerserver was crashed. There is nothing about this in the cups error log:```
E [15/Sep/2008:17:33:35 +0200] cupsdAuthorize: Local authentication certificate not found!
E [15/Sep/2008:17:33:52 +0200] cupsdAuthorize: Local authentication certificate not found!
E [15/Sep/2008:17:33:52 +0200] CUPS-Add-Modify-Printer: Unauthorized
```
Why does it print a part of the page, and then crashes the printserver?

This is driving me nuts!

After all that fiddling around with this printserver, I did another test with a shared printer (HP LaserJet 1100) on a WinXP machine:

Windows Printer via SAMBA: The SMB-Browser of the printer dialog finds the printserver, so I did not have to manually enter the device-uri. I activated "Authentication required" and entered the username and password of my account on that machine. Using "Verify" results in "verified - this printer-share can be accessed". Trying to print the testpage does not give any results, it even does not show a printjob on the cups printer status webpage, nor status or errors. This is all, what /var/log/cups/error_log shows:```
E [15/Sep/2008:18:27:34 +0200] cupsdAuthorize: Local authentication certificate not found!
E [15/Sep/2008:18:27:41 +0200] cupsdAuthorize: Local authentication certificate not found!
E [15/Sep/2008:18:27:41 +0200] CUPS-Add-Modify-Printer: Unauthorized
```

I really do not understand, what the issue here may be. This is totally screwed up, although this is a pretty much virgin Ubuntu Hardy 8.04 x86-64 installation, always kept up to date, with nothing extraordinary changed or configured.

Hopefully someone with more knowledge than I have reads this, and can give some hints, because I am really desperate here.

---

### Post by whizbaby on 2008-09-15
I am working with several printservers and it works fine for me. I have dhcp and dns running, so resolving is done that way. 
1)In the web interface (localhost:631), try putting
```
socket://ip-of-the-printserver
```
as uri. If that doesnt work, try (in the terminal)
```
sudo lpadmin -p name-of-the-printer -v socket://ip-of-the-printserver -P path-to-ppd
```
please replace 'name-of-the-printer' with a name you would like for the printer, 'ip-of-the-printserver' with the actual IP your printserver has and 'path-to-ppd' with the absolute path (starting with /) to the .ppd file of the printer.
I guess you just have to put the URI right, then you should be able to print.
2)whats the output of 
```
host privatprint
```
3)Only if you have configured a printer (meaning it shows up in the webinterface localhost:631/printers) and its not working, please check that
a)theres a name-of-the-printer.ppd file in /etc/cups/ppd
b)post your /etc/cups/printers.conf here

---

### Post by Master One on 2008-09-15
DHCP and DNS are running on our gatway machine (which is a computer running m0n0wall), and this definitely can not be the issue.

1) I do not think, that "AppSocket/HP JetDirect" is the way to go in this case, because that would require an uri of either socket://hostname or socket://hostname:9100, but this printserver does not work that way, since it can only be addressed by SMB, IPP or LPR. I tried your suggestion, but then I had to enter socket://192.168.1.6/lpt1 (otherwise there would be no way, to determine, which of the three printer-ports to use). The printer could be added without problem (adding the printer never was a problem, it always showed up correctly). Then I tried to print the testpage again. cups told "Printer is now connected." and showed the testpage as 1 of 1 active jobs. The printserver's network LED flashed, the printer started and showed flashing "Ready" and "Data" LEDs, then both LEDs stayed lighted up, and nothing else happened. I pressed the button on the printer's front, and it printed about less than 1/3 of a printer test page (but that one is different, it tells "Printer Test Page" in the middle at the top, no Ubuntu logo, and beneath I can see the half of two shaded circles at the left and right, with the half of a vertical shaded bar in the middle; but it should be clear that this testpage is incomplete, at the top and both sides I can see something like a ruler, on the left side the lowest point shows "9", and on the right side "23"). It pretty much looks like the behaviour as described with my LPR test, with the difference, that the printserver did not crash, although the cups printer status page still shows the status of "Printer is now connected." and the printjob of the testpage is still shown as 1 of 1 active jobs (usually a finished job should disappear from that webpage, as well as the status should be cleared). During this test nothing showed up in the cups error_log.

Trying the mentioned lpadmin command would be pointless, since adding the printer in cups is not the issue, it would just lead to the exact same result.

2) The output of "host privatprint" is "privatprint.m.lan has address 192.168.1.6", as expected, because resolving the host is not the issue (otherwise the network LED of the printserver would never have flashed during all my tests).

3) Configuring the printer never was a problem, during all my tests it showed up in the webinterface at [http://localhost:631/printers/](http://localhost:631/printers/) just fine:```
~$ ls -la /etc/cups/ppd
insgesamt 44
drwxr-xr-x 2 root lp    4096 2008-09-15 20:29 .
drwxr-xr-x 4 root lp    4096 2008-09-15 20:29 ..
-rw-r--r-- 1 root root 12168 2008-09-15 20:29 HL-1430.ppd
-rw-r--r-- 1 root root 20900 2008-04-29 13:01 PDF.ppd

~$ sudo cat /etc/cups/printers.conf
# Printer configuration file for CUPS v1.3.7
# Written by cupsd on 2008-09-15 20:29
<Printer HL-1430>
Info privatprint
Location 
DeviceURI socket://192.168.1.6/lpt1
State Idle
StateTime 1221503364
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
<Printer PDF>
Info PDF
DeviceURI cups-pdf:/
State Idle
StateTime 1209466890
Accepting Yes
Shared No
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
```

I appreciate your thoughts and your effort, but still no progress. :(

---

### Post by whizbaby on 2008-09-15
Ah ok, your printserver has multiple outputs? Geez...mine have one connector for ethernet and one for parallel on the other side.
According to the manual of your box the correct URI should be:

ipp://192.168.1.6/lpt1:631

it looks as if you didnt try this one yet^^

---

### Post by Master One on 2008-09-16
Unfortunately that's just an error in the manual, because the port-number always has to follow the hostname/IP-address, so there is no way around ipp://192.168.1.6:631/lpt1 or [http://192.168.1.6:631/lpt1](http://192.168.1.6:631/lpt1). In the meantime I am also in contact with someone from Edimax (the manufacturer of that device), but till now they also have no clue what may be the issue here.

---

### Post by whizbaby on 2008-09-16
Aww k srey that was my last idea.,.if theres a solution plz post here, I would like to see it.

---

### Post by Sef on 2008-09-16
Moved to hardware and laptops.

---

### Post by Master One on 2008-09-16
I don't know, how much more time I am going to invest to get this crappy printserver to work. Normally I'd say, it only can be the printserver's fault, if it does not work in any of the described ways, but since it works when printing from a WinXP machine using either SMB, IPP or LPR, it is just not possible to blame it on the printserver-device.

These issues come totally unexpected, because on one hand according to the manual the Unix/Linux world is explicitly supported, on the other hand, how can it be, that access by SMB, IPP and LPR works from a WinXP workstation, but not from the Ubuntu machine, especially since IPP is supported by CUPS natively.

Fact is, it's not a networking problem (the printserver has a fixed IP, and is registered at our local DNS forwarder), the printserver can indeed be reached by the Ubuntu machine and adding the printer to cups is not the issue (even the verification tests from the Gnome Add-Printer Dialog work, so for example verification with the correct uri smb://printserver/p1 give a positiv result, whereas verifying with a wrong uri like smb://printserver/lpt1 give a negativ result), but printing just does not work.

No idea, what to do now. If the Edimax support also has no new ideas, I think I have to pass on this one, and either connect the three printers to a workstation instead, setup a dedicated Ubuntu printserver machine, or buy another 3-port printserver device.

---

### Post by Master One on 2008-09-18
Well, I've sent that printserver back today, after I've found out, that it is still covered by manufacturer warranty.

Although I assume, that the printserver is the root of all these problems, it is undeniable, that printing from the WinXP machine just worked for all three types of remote-printing (SMB, IPP and LPR), but not from the Ubuntu machine (which even made the printserver crash in some cases). 

The endresult of my extensive experiments is:

[LIST]
[*]Printing from WinXP to the printerserver worked (SMB, IPP & LPR)
[*]Printing from Ubuntu to a shared printer on the WinXP machine worked (via SMB)
[*]Printing from Ubuntu to the printerserver did not work (SMB, IPP & LPR)
[/LIST]
That's just ridiculous!

Now I have to wait. Either they can fix the device, swap it, or do nothing (since it's working with any computer with a crappy M$ OS).

---

### Post by whizbaby on 2008-09-18
That really sounds weird I didnt have any problems with ipp:// and ubuntu. Can it be that the printserver has a really old implementation of ipp? Would be bad to see ubuntu as source of the problem...
If you get this thing back, would you be willing to test on another distro than debian/ubuntu? Redhat or Suse would do the job, but its understandable if you dont want to waste more time in that, too.

By the way, why are we in 'server platforms' all of a sudden, just because printserver contains the string 'server'? The printserver we were talking about is a piece of hardware like a router or modem, so Im a bit astonished, I thought server platforms was for ubuntu-servers.

---

### Post by Master One on 2008-09-18
If it had a really old implementation of IPP, it must have had a really old implementation of SMB and LPR as well, since none of these worked when trying to print from the Ubuntu machine, although it would make sense, to blame it on the implemention / revision of IPP, since connection by IPP was the only one that even crashed the printserver. On the other hand, the oldest of the three available firmwareversions (v66) was from 2003, the latest (v76) from 2006, so it is quite unlikely that the implemention all three types of remote-printing (SMB, IPP & LPR) were outdated. Nevertheless it would make sense, if the actual versions of SAMBA & CUPS use a newer protocol than the printserver could handle, and that printing from WinXP only worked, because it's still using those older protocols (just wondering, if printing from Windows Vista would have worked, but no Vista here...).

Hopefully they exchange the printserver to a newer type, since our device was already phased out some time ago. One it gets back, I done some more testing for sure (if it should not just work with Ubuntu right out of the box).

P.S. I have no idea, why Sef transfered this thread to the subforum "Server Platforms". I already sent him a PM, but no reply.

---

