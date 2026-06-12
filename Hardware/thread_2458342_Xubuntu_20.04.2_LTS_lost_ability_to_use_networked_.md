---
title: "Xubuntu 20.04.2 LTS lost ability to use networked HP OfficeJet 8600 Plus"
date: 2021-02-22
forum: Hardware
---

### Post by sorceror171 on 2021-02-22
I've been happily using an HP OfficeJet 8600 Plus for over a year now with no troubles. I know I've printed things fine from my Xubuntu box a couple weeks ago without issue.

Then, this morning, I wanted to print a form for my kids to take to school, and... the printer dialog listed no available printers. I tried to re-add the printer, and it failed with "**CUPS server error:** There was an error during the CUPS operation: 'server-error-internal-error'." I had to email the document to my work MacBook - on the same wired network with the printer - and it had no trouble printing the form.

I've checked and my software is up-to-date, all current updates applied. I know of no relevant changes, and as noted other computers on the same network can print to it just fine. I looked at the "DebuggingPrintingProblems" Ubuntu wiki, and there doesn't seem to be an obvious issue. But the CUPS error log is unhappy:

```
$ cat /var/log/cups/error_log
E [22/Feb/2021:07:04:39 -0500] [CGI] Unable to create PPD file: Could not poll sufficient capability info from the printer (ipp://Officejet%20Pro%208600%20%5BCD4675%5D._ipp._tcp.local/, ipp://HPA0D3C1CD4675.local:631/ipp/printer) via IPP!
E [22/Feb/2021:07:05:17 -0500] [CGI] Unable to create PPD file: Could not poll sufficient capability info from the printer (ipp://Officejet%20Pro%208600%20%5BCD4675%5D._ipp._tcp.local/, ipp://HPA0D3C1CD4675.local:631/ipp/printer) via IPP!
E [22/Feb/2021:07:05:17 -0500] copy_model: empty PPD file
E [22/Feb/2021:07:05:17 -0500] [Client 648] Returning IPP server-error-internal-error for CUPS-Add-Modify-Printer (ipp://localhost/printers/HP_OfficeJet_8600) from localhost.
E [22/Feb/2021:07:05:20 -0500] [CGI] Unable to create PPD file: Could not poll sufficient capability info from the printer (ipp://Officejet%20Pro%208600%20%5BCD4675%5D._ipp._tcp.local/, ipp://HPA0D3C1CD4675.local:631/ipp/printer) via IPP!
E [22/Feb/2021:07:05:20 -0500] copy_model: empty PPD file
E [22/Feb/2021:07:05:20 -0500] [Client 651] Returning IPP server-error-internal-error for CUPS-Add-Modify-Printer (ipp://localhost/printers/HP%5FOfficeJet%5F8600) from localhost.
E [22/Feb/2021:07:07:38 -0500] [CGI] Unable to create PPD file: Could not poll sufficient capability info from the printer (ipp://Officejet%20Pro%208600%20%5BCD4675%5D._ipp._tcp.local/, ipp://HPA0D3C1CD4675.local:631/ipp/printer) via IPP!
E [22/Feb/2021:07:08:13 -0500] [CGI] Unable to create PPD file: Could not poll sufficient capability info from the printer (ipp://Officejet%20Pro%208600%20%5BCD4675%5D._ipp._tcp.local/, ipp://HPA0D3C1CD4675.local:631/ipp/printer) via IPP!
E [22/Feb/2021:07:08:13 -0500] copy_model: empty PPD file
E [22/Feb/2021:07:08:13 -0500] [Client 18] Returning IPP server-error-internal-error for CUPS-Add-Modify-Printer (ipp://localhost/printers/OfficeJet_8600) from localhost.
E [22/Feb/2021:07:08:16 -0500] [CGI] Unable to create PPD file: Could not poll sufficient capability info from the printer (ipp://Officejet%20Pro%208600%20%5BCD4675%5D._ipp._tcp.local/, ipp://HPA0D3C1CD4675.local:631/ipp/printer) via IPP!
E [22/Feb/2021:07:08:16 -0500] copy_model: empty PPD file
E [22/Feb/2021:07:08:16 -0500] [Client 21] Returning IPP server-error-internal-error for CUPS-Add-Modify-Printer (ipp://localhost/printers/OfficeJet%5F8600) from localhost.
E [22/Feb/2021:08:08:58 -0500] [CGI] Unable to create PPD file: Could not poll sufficient capability info from the printer (ipp://Officejet%20Pro%208600%20%5BCD4675%5D._ipp._tcp.local/, ipp://HPA0D3C1CD4675.local:631/ipp/printer) via IPP!
E [22/Feb/2021:08:09:26 -0500] [CGI] Unable to create PPD file: Could not poll sufficient capability info from the printer (ipp://Officejet%20Pro%208600%20%5BCD4675%5D._ipp._tcp.local/, ipp://HPA0D3C1CD4675.local:631/ipp/printer) via IPP!
E [22/Feb/2021:08:09:26 -0500] copy_model: empty PPD file
E [22/Feb/2021:08:09:26 -0500] [Client 51] Returning IPP server-error-internal-error for CUPS-Add-Modify-Printer (ipp://localhost/printers/HP_OfficeJet_8600) from localhost.
E [22/Feb/2021:08:09:29 -0500] [CGI] Unable to create PPD file: Could not poll sufficient capability info from the printer (ipp://Officejet%20Pro%208600%20%5BCD4675%5D._ipp._tcp.local/, ipp://HPA0D3C1CD4675.local:631/ipp/printer) via IPP!
E [22/Feb/2021:08:09:29 -0500] copy_model: empty PPD file
E [22/Feb/2021:08:09:29 -0500] [Client 54] Returning IPP server-error-internal-error for CUPS-Add-Modify-Printer (ipp://localhost/printers/HP%5FOfficeJet%5F8600) from localhost.
```

Some relevant debug output:

```
$sudo /usr/lib/cups/backend/dnssd
DEBUG: Querying "Officejet\032Pro\0328600\032\091CD4675\093._ipp._tcp.local"...
DEBUG: Querying "Officejet\032Pro\0328600\032\091CD4675\093._pdl-datastream._tcp.local"...
DEBUG: Querying "Officejet\032Pro\0328600\032\091CD4675\093._printer._tcp.local"...
DEBUG: sent=0, count=3
DEBUG2: query_callback(browser=0x558efb644ec0, interfaceIndex=3, protocol=1, event=0, fullName="Officejet\032Pro\0328600\032\091CD4675\093._ipp._tcp.local", rrclass=1, rrtype=16, rdata=0x558efb6465d0, rdlen=438, flags=5, context=0x558efb644180)
DEBUG2: query_callback: "txtvers=1".
DEBUG2: query_callback: "qtotal=1".
DEBUG2: query_callback: "pdl=application/vnd.hp-PCL,image/jpeg,application/PCLm,image/urf".
DEBUG2: query_callback: "rp=ipp/printer".
DEBUG2: query_callback: "URF=CP1,MT1-2-8-9-10-11,OB9,OFU0,PQ3-4-5,RS300-600,SRGB24,W8,DEVW8,DEVRGB24-48,ADOBERGB24-48,DM3,IS1-2".
DEBUG2: query_callback: "ty=Officejet Pro 8600".
DEBUG2: query_callback: "product=(HP Officejet Pro 8600)".
DEBUG2: query_callback: "usb_MFG=HP".
DEBUG2: query_callback: "usb_MDL=Officejet Pro 8600".
DEBUG2: query_callback: "priority=20".
DEBUG2: query_callback: "mac=a0:d3:c1:cd:46:75".
DEBUG2: query_callback: "adminurl=http://HPA0D3C1CD4675.local.".
DEBUG2: query_callback: "note=".
DEBUG2: query_callback: "UUID=1c852a4d-b800-1f08-abcd-a0d3c1cd4675".
DEBUG2: query_callback: "Color=T".
DEBUG2: query_callback: "Duplex=T".
DEBUG2: query_callback: "Scan=T".
DEBUG2: query_callback(browser=0x558efb644ec0, interfaceIndex=-1, protocol=-1, event=2, fullName="Officejet\032Pro\0328600\032\091CD4675\093._ipp._tcp.local", rrclass=1, rrtype=16, rdata=(nil), rdlen=0, flags=0, context=0x558efb644180)
DEBUG2: query_callback(browser=0x558efb644680, interfaceIndex=3, protocol=1, event=0, fullName="Officejet\032Pro\0328600\032\091CD4675\093._pdl-datastream._tcp.local", rrclass=1, rrtype=16, rdata=0x558efb6468bc, rdlen=320, flags=5, context=0x558efb644000)
DEBUG2: query_callback: "txtvers=1".
DEBUG2: query_callback: "qtotal=1".
DEBUG2: query_callback: "pdl=application/vnd.hp-PCL,image/jpeg,application/PCLm,image/urf".
DEBUG2: query_callback: "ty=Officejet Pro 8600".
DEBUG2: query_callback: "product=(HP Officejet Pro 8600)".
DEBUG2: query_callback: "usb_MFG=HP".
DEBUG2: query_callback: "usb_MDL=Officejet Pro 8600".
DEBUG2: query_callback: "priority=40".
DEBUG2: query_callback: "mac=a0:d3:c1:cd:46:75".
DEBUG2: query_callback: "adminurl=http://HPA0D3C1CD4675.local.".
DEBUG2: query_callback: "note=".
DEBUG2: query_callback: "UUID=1c852a4d-b800-1f08-abcd-a0d3c1cd4675".
DEBUG2: query_callback: "Color=T".
DEBUG2: query_callback: "Duplex=T".
DEBUG2: query_callback: "Scan=T".
DEBUG2: query_callback(browser=0x558efb644680, interfaceIndex=-1, protocol=-1, event=2, fullName="Officejet\032Pro\0328600\032\091CD4675\093._pdl-datastream._tcp.local", rrclass=1, rrtype=16, rdata=(nil), rdlen=0, flags=0, context=0x558efb644000)
DEBUG2: query_callback(browser=0x558efb6460a0, interfaceIndex=3, protocol=1, event=0, fullName="Officejet\032Pro\0328600\032\091CD4675\093._printer._tcp.local", rrclass=1, rrtype=16, rdata=0x558efb646cf4, rdlen=327, flags=5, context=0x558efb644560)
DEBUG2: query_callback: "txtvers=1".
DEBUG2: query_callback: "qtotal=1".
DEBUG2: query_callback: "rp=RAW".
DEBUG2: query_callback: "pdl=application/vnd.hp-PCL,image/jpeg,application/PCLm,image/urf".
DEBUG2: query_callback: "ty=Officejet Pro 8600".
DEBUG2: query_callback: "product=(HP Officejet Pro 8600)".
DEBUG2: query_callback: "usb_MFG=HP".
DEBUG2: query_callback: "usb_MDL=Officejet Pro 8600".
DEBUG2: query_callback: "priority=52".
DEBUG2: query_callback: "mac=a0:d3:c1:cd:46:75".
DEBUG2: query_callback: "adminurl=http://HPA0D3C1CD4675.local.".
DEBUG2: query_callback: "note=".
DEBUG2: query_callback: "UUID=1c852a4d-b800-1f08-abcd-a0d3c1cd4675".
DEBUG2: query_callback: "Color=T".
DEBUG2: query_callback: "Duplex=T".
DEBUG2: query_callback: "Scan=T".
DEBUG2: query_callback(browser=0x558efb6460a0, interfaceIndex=-1, protocol=-1, event=2, fullName="Officejet\032Pro\0328600\032\091CD4675\093._printer._tcp.local", rrclass=1, rrtype=16, rdata=(nil), rdlen=0, flags=0, context=0x558efb644560)
network dnssd://Officejet%20Pro%208600%20%5BCD4675%5D._ipp._tcp.local/?uuid=1c852a4d-b800-1f08-abcd-a0d3c1cd4675 "HP Officejet Pro 8600" "Officejet Pro 8600 [CD4675]" "MFG:HP;MDL:Officejet Pro 8600;CMD:PCL,JPEG,URF;" ""
DEBUG: sent=3, count=3
DEBUG: sent=3, count=0
DEBUG: sent=3, count=0
DEBUG: sent=3, count=0
```

```
$lpinfo -v
file cups-brf:/
network beh
network https
serial serial:/dev/ttyS0?baud=115200
network ipps
network socket
network lpd
network http
direct hp
network ipp
direct hpfax
network dnssd://Officejet%20Pro%208600%20%5BCD4675%5D._ipp._tcp.local/?uuid=1c852a4d-b800-1f08-abcd-a0d3c1cd4675
network ipp://Officejet%20Pro%208600%20%5BCD4675%5D._ipp._tcp.local/
```

Any suggestions?

---

### Post by sorceror171 on 2021-02-25
Anyone else having problems where a printer that worked just fine suddenly disappears from the printer list and can't be re-added?

---

### Post by brian_p on 2021-02-26
> Could not poll sufficient capability info from the printer...

comes from cups-filters, not CUPS. The printer is queried for its capabilities and apparently is not providing enough to allow a PPD to be created. I have no idea what the cause is. A malfuncioning printer? A bug in cups-filters? A network problem?

Fortunately, you can use CUPS instead of cups-browsed to set up a print queue:

```
lpadmin -p testq -v "ipp://Officejet%20Pro%208600%20%5BCD4675%5D._ipp._tcp.local/" -E -m everywhere
```

Test printing with ```
lp -d testq /etc/nsswitch.conf
```

---

### Post by sorceror171 on 2021-03-01
Well, even that didn't work.

```
lpadmin -p testq -v "ipp://Officejet%20Pro%208600%20%5BCD4675%5D._ipp._tcp.local/" -E -m everywhere
lpadmin: Unable to connect to "HPA0D3C1CD4675.local:631": Operation now in progress
```

However, if even something at *that* level was having problems... I power-cycled the printer, physically disconnecting the power. And when it came back up, the printer again appeared in the "Printers" settings. Not sure why my Linux box was upset with it, when Mac and Windows could print to it. But it works now.

Thanks for pointing me in the right direction!

---

