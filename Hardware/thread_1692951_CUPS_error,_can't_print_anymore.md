---
title: "CUPS error, can't print anymore"
date: 2011-02-22
forum: Hardware
---

### Post by fubar65 on 2011-02-22
I have 2 laptops here with Ubuntu on them, both are 10.10, one is 32 bit, the other is 64 bit.

I have wireless working fine and they were both printing, until about a week ago when my wife's laptop stopped printing (the 32 bit one)

I have an edimax PS-3205U print server with 2 printers hooked up to it, a laserjet 4l and a deskjet 1220c.
both were working fine using lpr for over 6 months, then my wifes laptop wont connect to it anymore, yet mine will.

hers had some issues anyway so I reinstalled 10.10 and now when I go to setup the printer it wont let me use lpr, it gives me the following error
> CUPS server error
There was an error during the CUPS operation: 'client-error-not-possible'

I have tried lpd, ipp, samba, nothing else seems to work, although I am not sure if I am setting them up properly..

I would just like her to be able to print again..

why can't I use lpr anymore on her laptop and why can I on mine?
thanks for any thoughts or advice.

---

### Post by deragon on 2011-02-22
Is the firewall up on the laptop?  You can disabled it by stopping the service or run as root:

iptables -F
iptables -X
iptables -P INPUT   ACCEPT
iptables -P OUTPUT  ACCEPT
iptables -P FORWARD ACCEPT
iptables -t nat -A POSTROUTING -j MASQUERADE
iptables -A FORWARD

Have you checked the logs under /var/log/cups?  Can you check on your printer server if it received the request from the laptop?

Try to telnet to port 631 of your printer server to see if the problem is network related or not.

---

### Post by fubar65 on 2011-02-22
I think we're headed in different directions..

it was printing fine, now all of a sudden I can't use lpr and I don't know why. It's not even an option on this one, it is on the other laptop though.
I just want her to be able to print, I don't care what protocol or package I need to install..
both laptops have had 10.10 installed on them since Saturday, the 64 bit one is fine, this one isn't for some reason..


the print server is not a computer, it is an actual print server box, it's about the size of an 8 port network switch.

as for the logs, they don't tell me much but I will post them.

error_log
> 
E [21/Feb/2011:17:07:44 -0400] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [21/Feb/2011:17:07:55 -0400] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [21/Feb/2011:17:08:21 -0400] Returning IPP client-error-not-possible for CUPS-Add-Modify-Printer (ipp://localhost/printers/HP-LaserJet-4L) from localhost
D [21/Feb/2011:17:48:08 -0400] [Job 1] The following messages were recorded from 17:48:06 to 17:48:08
D [21/Feb/2011:17:48:08 -0400] [Job 1] Adding start banner page "none".
D [21/Feb/2011:17:48:08 -0400] [Job 1] Adding end banner page "none".
D [21/Feb/2011:17:48:08 -0400] [Job 1] File of type application/postscript queued by "kim".
D [21/Feb/2011:17:48:08 -0400] [Job 1] hold_until=0
D [21/Feb/2011:17:48:08 -0400] [Job 1] Queued on "HP-LaserJet-4L" by "kim".
D [21/Feb/2011:17:48:08 -0400] [Job 1] job-sheets=none,none
D [21/Feb/2011:17:48:08 -0400] [Job 1] argv[0]="HP-LaserJet-4L"
D [21/Feb/2011:17:48:08 -0400] [Job 1] argv[1]="1"
D [21/Feb/2011:17:48:08 -0400] [Job 1] argv[2]="kim"
D [21/Feb/2011:17:48:08 -0400] [Job 1] argv[3]="Test Page"
D [21/Feb/2011:17:48:08 -0400] [Job 1] argv[4]="1"
D [21/Feb/2011:17:48:08 -0400] [Job 1] argv[5]="PageSize=Letter job-uuid=urn:uuid:cebd8607-8d6e-3742-5ddb-a0c68de405d0 job-originating-host-name=localhost"
D [21/Feb/2011:17:48:08 -0400] [Job 1] argv[6]="/var/spool/cups/d00001-001"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[8]="HOME=/var/spool/cups/tmp"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[10]="SERVER_ADMIN=root@Latitude-D610"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[11]="SOFTWARE=CUPS/1.4.4"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[13]="USER=root"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[16]="IPP_PORT=631"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[17]="CHARSET=utf-8"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[18]="LANG=en_CA.UTF-8"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[19]="PPD=/etc/cups/ppd/HP-LaserJet-4L.ppd"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[20]="RIP_MAX_CACHE=auto"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[21]="CONTENT_TYPE=application/postscript"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[22]="DEVICE_URI=lpd://192.168.2.199/PASSTHRU"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[23]="PRINTER_INFO=HP LaserJet 4L"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[24]="PRINTER_LOCATION="
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[25]="PRINTER=HP-LaserJet-4L"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[26]="CUPS_FILETYPE=document"
D [21/Feb/2011:17:48:08 -0400] [Job 1] envp[27]="FINAL_CONTENT_TYPE=printer/HP-LaserJet-4L"
D [21/Feb/2011:17:48:08 -0400] [Job 1] Started filter /usr/lib/cups/filter/pstopdf (PID 30916)
D [21/Feb/2011:17:48:08 -0400] [Job 1] Started filter /usr/lib/cups/filter/pdftopdf (PID 30917)
D [21/Feb/2011:17:48:08 -0400] [Job 1] Started filter /usr/lib/cups/filter/foomatic-rip (PID 30918)
D [21/Feb/2011:17:48:08 -0400] [Job 1] Started backend /usr/lib/cups/backend/lpd (PID 30919)
D [21/Feb/2011:17:48:08 -0400] [Job 1] STATE: +connecting-to-device
D [21/Feb/2011:17:48:08 -0400] [Job 1] Looking up "192.168.2.199"...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Copying print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] backendRunLoop(print_fd=-1, device_fd=6, snmp_fd=5, addr=0x20c29064, use_bc=0, side_cb=0x5eed30)
D [21/Feb/2011:17:48:08 -0400] [Job 1] Getting input from file
D [21/Feb/2011:17:48:08 -0400] [Job 1] foomatic-rip version 4.0.5.223 running...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Parsing PPD file ...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Added option PageSize
D [21/Feb/2011:17:48:08 -0400] [Job 1] Added option ImageableArea
D [21/Feb/2011:17:48:08 -0400] [Job 1] Added option PaperDimension
D [21/Feb/2011:17:48:08 -0400] [Job 1] Added option InputSlot
D [21/Feb/2011:17:48:08 -0400] [Job 1] Added option Manualfeed
D [21/Feb/2011:17:48:08 -0400] [Job 1] Added option Economode
D [21/Feb/2011:17:48:08 -0400] [Job 1] Added option Copies
D [21/Feb/2011:17:48:08 -0400] [Job 1] pstopdf 6 args: 1 kim Test Page 1 PageSize=Letter job-uuid=urn:uuid:cebd8607-8d6e-3742-5ddb-a0c68de405d0 job-originating-host-name=localhost /var/spool/cups/d00001-001
D [21/Feb/2011:17:48:08 -0400] [Job 1] PPD: /etc/cups/ppd/HP-LaserJet-4L.ppd
D [21/Feb/2011:17:48:08 -0400] [Job 1] Added option Resolution
D [21/Feb/2011:17:48:08 -0400] [Job 1] Added option REt
D [21/Feb/2011:17:48:08 -0400] [Job 1] Added option TonerDensity
D [21/Feb/2011:17:48:08 -0400] [Job 1] Added option HalftoningAlgorithm
D [21/Feb/2011:17:48:08 -0400] [Job 1] Added option Font
D [21/Feb/2011:17:48:08 -0400] [Job 1]
D [21/Feb/2011:17:48:08 -0400] [Job 1] Parameter Summary
D [21/Feb/2011:17:48:08 -0400] [Job 1] -----------------
D [21/Feb/2011:17:48:08 -0400] [Job 1]
D [21/Feb/2011:17:48:08 -0400] [Job 1] Spooler: cups
D [21/Feb/2011:17:48:08 -0400] [Job 1] Printer: HP-LaserJet-4L
D [21/Feb/2011:17:48:08 -0400] [Job 1] Shell: /bin/bash
D [21/Feb/2011:17:48:08 -0400] [Job 1] PPD file: /etc/cups/ppd/HP-LaserJet-4L.ppd
D [21/Feb/2011:17:48:08 -0400] [Job 1] ATTR file:
D [21/Feb/2011:17:48:08 -0400] [Job 1] Printer model: HP LaserJet 4L Foomatic/ljet4 (recommended)
D [21/Feb/2011:17:48:08 -0400] [Job 1] Job title: Test Page
D [21/Feb/2011:17:48:08 -0400] [Job 1] File(s) to be printed:
D [21/Feb/2011:17:48:08 -0400] [Job 1] <STDIN>
D [21/Feb/2011:17:48:08 -0400] [Job 1]
D [21/Feb/2011:17:48:08 -0400] [Job 1] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [21/Feb/2011:17:48:08 -0400] [Job 1] Printing system options:
D [21/Feb/2011:17:48:08 -0400] [Job 1] Pondering option 'job-uuid=urn:uuid:cebd8607-8d6e-3742-5ddb-a0c68de405d0'
D [21/Feb/2011:17:48:08 -0400] [Job 1] Unknown option job-uuid=urn:uuid:cebd8607-8d6e-3742-5ddb-a0c68de405d0.
D [21/Feb/2011:17:48:08 -0400] [Job 1] Pondering option 'job-originating-host-name=localhost'
D [21/Feb/2011:17:48:08 -0400] [Job 1] Unknown option job-originating-host-name=localhost.
D [21/Feb/2011:17:48:08 -0400] [Job 1] Options from the PPD file:
D [21/Feb/2011:17:48:08 -0400] [Job 1] Pondering option 'PageSize=Letter'
D [21/Feb/2011:17:48:08 -0400] [Job 1]
D [21/Feb/2011:17:48:08 -0400] [Job 1] ================================================
D [21/Feb/2011:17:48:08 -0400] [Job 1]
D [21/Feb/2011:17:48:08 -0400] [Job 1] File: <STDIN>
D [21/Feb/2011:17:48:08 -0400] [Job 1]
D [21/Feb/2011:17:48:08 -0400] [Job 1] ================================================
D [21/Feb/2011:17:48:08 -0400] [Job 1]
D [21/Feb/2011:17:48:08 -0400] [Job 1] Resolution: 300x300
D [21/Feb/2011:17:48:08 -0400] [Job 1] Page size: Letter
D [21/Feb/2011:17:48:08 -0400] [Job 1] Width: 612, height: 792, absolute margins: 18, 36, 594, 756
D [21/Feb/2011:17:48:08 -0400] [Job 1] Relative margins: 18, 36, 18, 36
D [21/Feb/2011:17:48:08 -0400] [Job 1] PPD options: -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [21/Feb/2011:17:48:08 -0400] [Job 1] PostScript to be injected:
D [21/Feb/2011:17:48:08 -0400] [Job 1] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sOutputFile=-  -c .setpdfwrite -f -
D [21/Feb/2011:17:48:08 -0400] [Job 1] Filetype: PDF
D [21/Feb/2011:17:48:08 -0400] [Job 1] Storing temporary files in /var/spool/cups/tmp
D [21/Feb/2011:17:48:08 -0400] [Job 1] File contains 1 pages
D [21/Feb/2011:17:48:08 -0400] [Job 1] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dNOPAUSE -sDEVICE=ljet4 -dMediaPosition=0 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -r300x300 -sOutputFile=- -f   /var/spool/cups/tmp/foomatic-8PtmHq
D [21/Feb/2011:17:48:08 -0400] [Job 1] Starting process "kid3" (generation 1)
D [21/Feb/2011:17:48:08 -0400] [Job 1] Starting process "kid4" (generation 2)
D [21/Feb/2011:17:48:08 -0400] [Job 1] Starting process "renderer" (generation 2)
D [21/Feb/2011:17:48:08 -0400] [Job 1] JCL: %-12345X@PJL
D [21/Feb/2011:17:48:08 -0400] [Job 1] @PJL SET DENSITY=3
D [21/Feb/2011:17:48:08 -0400] [Job 1] @PJL SET RET=MEDIUM
D [21/Feb/2011:17:48:08 -0400] [Job 1] @PJL SET COPIES=1
D [21/Feb/2011:17:48:08 -0400] [Job 1] @PJL SET ECONOMODE=OFF
D [21/Feb/2011:17:48:08 -0400] [Job 1] @PJL SET MANUALFEED=OFF
D [21/Feb/2011:17:48:08 -0400] [Job 1] <job data> %-12345X@PJL RESET
D [21/Feb/2011:17:48:08 -0400] [Job 1]
D [21/Feb/2011:17:48:08 -0400] [Job 1]
D [21/Feb/2011:17:48:08 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] hrDeviceDesc="Unknown"
D [21/Feb/2011:17:48:08 -0400] [Job 1] prtGeneralCurrentLocalization type is 5, expected 2!
D [21/Feb/2011:17:48:08 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] renderer exited with status 0
D [21/Feb/2011:17:48:08 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Read 2075 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Wrote 2075 bytes of print data...
D [21/Feb/2011:17:48:08 -0400] [Job 1] kid4 exited with status 0
D [21/Feb/2011:17:48:08 -0400] [Job 1] kid3 finished
D [21/Feb/2011:17:48:08 -0400] [Job 1] Kid3 exit status: 0
D [21/Feb/2011:17:48:08 -0400] [Job 1]
D [21/Feb/2011:17:48:08 -0400] [Job 1] Closing foomatic-rip.
D [21/Feb/2011:17:48:08 -0400] [Job 1] STATE: +connecting-to-device
D [21/Feb/2011:17:48:08 -0400] [Job 1] Looking up "192.168.2.199"...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Connecting to 192.168.2.199:515 for printer PASSTHRU
D [21/Feb/2011:17:48:08 -0400] [Job 1] Connecting to printer...
D [21/Feb/2011:17:48:08 -0400] [Job 1] STATE: -connecting-to-device
D [21/Feb/2011:17:48:08 -0400] [Job 1] Connected to printer...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Connected to 192.168.2.199:515 (IPv4) (local port 1023)...
D [21/Feb/2011:17:48:08 -0400] [Job 1] lpd_command 02 PASSTHRU
D [21/Feb/2011:17:48:08 -0400] [Job 1] Sending command string (10 bytes)...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Reading command status...
D [21/Feb/2011:17:48:08 -0400] [Job 1] lpd_command returning 0
D [21/Feb/2011:17:48:08 -0400] [Job 1] Control file is:
D [21/Feb/2011:17:48:08 -0400] [Job 1] HLatitude-D610
D [21/Feb/2011:17:48:08 -0400] [Job 1] Pkim
D [21/Feb/2011:17:48:08 -0400] [Job 1] JTest Page
D [21/Feb/2011:17:48:08 -0400] [Job 1] ldfA919Latitude-D610
D [21/Feb/2011:17:48:08 -0400] [Job 1] UdfA919Latitude-D610
D [21/Feb/2011:17:48:08 -0400] [Job 1] NTest Page
D [21/Feb/2011:17:48:08 -0400] [Job 1] lpd_command 02 84 cfA919Latitude-D610
D [21/Feb/2011:17:48:08 -0400] [Job 1] Sending command string (24 bytes)...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Reading command status...
D [21/Feb/2011:17:48:08 -0400] [Job 1] lpd_command returning 0
D [21/Feb/2011:17:48:08 -0400] [Job 1] Sending control file (84 bytes)
D [21/Feb/2011:17:48:08 -0400] [Job 1] Control file sent successfully
D [21/Feb/2011:17:48:08 -0400] [Job 1] lpd_command 03 157723 dfA919Latitude-D610
D [21/Feb/2011:17:48:08 -0400] [Job 1] Sending command string (28 bytes)...
D [21/Feb/2011:17:48:08 -0400] [Job 1] Reading command status...
D [21/Feb/2011:17:48:08 -0400] [Job 1] lpd_command returning 1
D [21/Feb/2011:17:48:08 -0400] [Job 1] Backend returned status 1 (failed)
D [21/Feb/2011:17:48:08 -0400] [Job 1] End of messages
D [21/Feb/2011:17:48:08 -0400] [Job 1] printer-state=3(idle)
D [21/Feb/2011:17:48:08 -0400] [Job 1] printer-state-message="/usr/lib/cups/backend/lpd failed"
D [21/Feb/2011:17:48:08 -0400] [Job 1] printer-state-reasons=none
D [21/Feb/2011:17:53:17 -0400] [Job 1] The following messages were recorded from 17:53:16 to 17:53:17
D [21/Feb/2011:17:53:17 -0400] [Job 1] Job submission timed out.
D [21/Feb/2011:17:53:17 -0400] [Job 1] job-sheets=none,none
D [21/Feb/2011:17:53:17 -0400] [Job 1] argv[0]="HP-LaserJet-4L"
D [21/Feb/2011:17:53:17 -0400] [Job 1] argv[1]="1"
D [21/Feb/2011:17:53:17 -0400] [Job 1] argv[2]="kim"
D [21/Feb/2011:17:53:17 -0400] [Job 1] argv[3]="Test Page"
D [21/Feb/2011:17:53:17 -0400] [Job 1] argv[4]="1"
D [21/Feb/2011:17:53:17 -0400] [Job 1] argv[5]="PageSize=Letter job-uuid=urn:uuid:cebd8607-8d6e-3742-5ddb-a0c68de405d0 job-originating-host-name=localhost"
D [21/Feb/2011:17:53:17 -0400] [Job 1] argv[6]="/var/spool/cups/d00001-001"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[8]="HOME=/var/spool/cups/tmp"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[10]="SERVER_ADMIN=root@Latitude-D610"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[11]="SOFTWARE=CUPS/1.4.4"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[13]="USER=root"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[16]="IPP_PORT=631"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[17]="CHARSET=utf-8"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[18]="LANG=en_CA.UTF-8"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[19]="PPD=/etc/cups/ppd/HP-LaserJet-4L.ppd"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[20]="RIP_MAX_CACHE=auto"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[21]="CONTENT_TYPE=application/postscript"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[22]="DEVICE_URI=lpd://192.168.2.199/PASSTHRU"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[23]="PRINTER_INFO=HP LaserJet 4L"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[24]="PRINTER_LOCATION="
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[25]="PRINTER=HP-LaserJet-4L"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[26]="CUPS_FILETYPE=document"
D [21/Feb/2011:17:53:17 -0400] [Job 1] envp[27]="FINAL_CONTENT_TYPE=printer/HP-LaserJet-4L"
D [21/Feb/2011:17:53:17 -0400] [Job 1] Started filter /usr/lib/cups/filter/pstopdf (PID 30954)
D [21/Feb/2011:17:53:17 -0400] [Job 1] Started filter /usr/lib/cups/filter/pdftopdf (PID 30955)
D [21/Feb/2011:17:53:17 -0400] [Job 1] Started filter /usr/lib/cups/filter/foomatic-rip (PID 30956)
D [21/Feb/2011:17:53:17 -0400] [Job 1] Started backend /usr/lib/cups/backend/lpd (PID 30957)
D [21/Feb/2011:17:53:17 -0400] [Job 1] pstopdf 6 args: 1 kim Test Page 1 PageSize=Letter job-uuid=urn:uuid:cebd8607-8d6e-3742-5ddb-a0c68de405d0 job-originating-host-name=localhost /var/spool/cups/d00001-001
D [21/Feb/2011:17:53:17 -0400] [Job 1] Getting input from file
D [21/Feb/2011:17:53:17 -0400] [Job 1] STATE: +connecting-to-device
D [21/Feb/2011:17:53:17 -0400] [Job 1] foomatic-rip version 4.0.5.223 running...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Parsing PPD file ...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Added option PageSize
D [21/Feb/2011:17:53:17 -0400] [Job 1] Added option ImageableArea
D [21/Feb/2011:17:53:17 -0400] [Job 1] Added option PaperDimension
D [21/Feb/2011:17:53:17 -0400] [Job 1] Added option InputSlot
D [21/Feb/2011:17:53:17 -0400] [Job 1] PPD: /etc/cups/ppd/HP-LaserJet-4L.ppd
D [21/Feb/2011:17:53:17 -0400] [Job 1] Looking up "192.168.2.199"...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Copying print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] backendRunLoop(print_fd=-1, device_fd=6, snmp_fd=5, addr=0x2265b064, use_bc=0, side_cb=0xabfd30)
D [21/Feb/2011:17:53:17 -0400] [Job 1] Added option Manualfeed
D [21/Feb/2011:17:53:17 -0400] [Job 1] Added option Economode
D [21/Feb/2011:17:53:17 -0400] [Job 1] Added option Copies
D [21/Feb/2011:17:53:17 -0400] [Job 1] Added option Resolution
D [21/Feb/2011:17:53:17 -0400] [Job 1] Added option REt
D [21/Feb/2011:17:53:17 -0400] [Job 1] Added option TonerDensity
D [21/Feb/2011:17:53:17 -0400] [Job 1] Added option HalftoningAlgorithm
D [21/Feb/2011:17:53:17 -0400] [Job 1] Added option Font
D [21/Feb/2011:17:53:17 -0400] [Job 1]
D [21/Feb/2011:17:53:17 -0400] [Job 1] Parameter Summary
D [21/Feb/2011:17:53:17 -0400] [Job 1] -----------------
D [21/Feb/2011:17:53:17 -0400] [Job 1]
D [21/Feb/2011:17:53:17 -0400] [Job 1] Spooler: cups
D [21/Feb/2011:17:53:17 -0400] [Job 1] Printer: HP-LaserJet-4L
D [21/Feb/2011:17:53:17 -0400] [Job 1] Shell: /bin/bash
D [21/Feb/2011:17:53:17 -0400] [Job 1] PPD file: /etc/cups/ppd/HP-LaserJet-4L.ppd
D [21/Feb/2011:17:53:17 -0400] [Job 1] ATTR file:
D [21/Feb/2011:17:53:17 -0400] [Job 1] Printer model: HP LaserJet 4L Foomatic/ljet4 (recommended)
D [21/Feb/2011:17:53:17 -0400] [Job 1] Job title: Test Page
D [21/Feb/2011:17:53:17 -0400] [Job 1] File(s) to be printed:
D [21/Feb/2011:17:53:17 -0400] [Job 1] <STDIN>
D [21/Feb/2011:17:53:17 -0400] [Job 1]
D [21/Feb/2011:17:53:17 -0400] [Job 1] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [21/Feb/2011:17:53:17 -0400] [Job 1] Printing system options:
D [21/Feb/2011:17:53:17 -0400] [Job 1] Pondering option 'job-uuid=urn:uuid:cebd8607-8d6e-3742-5ddb-a0c68de405d0'
D [21/Feb/2011:17:53:17 -0400] [Job 1] Unknown option job-uuid=urn:uuid:cebd8607-8d6e-3742-5ddb-a0c68de405d0.
D [21/Feb/2011:17:53:17 -0400] [Job 1] Pondering option 'job-originating-host-name=localhost'
D [21/Feb/2011:17:53:17 -0400] [Job 1] Unknown option job-originating-host-name=localhost.
D [21/Feb/2011:17:53:17 -0400] [Job 1] Options from the PPD file:
D [21/Feb/2011:17:53:17 -0400] [Job 1] Pondering option 'PageSize=Letter'
D [21/Feb/2011:17:53:17 -0400] [Job 1]
D [21/Feb/2011:17:53:17 -0400] [Job 1] ================================================
D [21/Feb/2011:17:53:17 -0400] [Job 1]
D [21/Feb/2011:17:53:17 -0400] [Job 1] File: <STDIN>
D [21/Feb/2011:17:53:17 -0400] [Job 1]
D [21/Feb/2011:17:53:17 -0400] [Job 1] ================================================
D [21/Feb/2011:17:53:17 -0400] [Job 1]
D [21/Feb/2011:17:53:17 -0400] [Job 1] Resolution: 300x300
D [21/Feb/2011:17:53:17 -0400] [Job 1] Page size: Letter
D [21/Feb/2011:17:53:17 -0400] [Job 1] Width: 612, height: 792, absolute margins: 18, 36, 594, 756
D [21/Feb/2011:17:53:17 -0400] [Job 1] Relative margins: 18, 36, 18, 36
D [21/Feb/2011:17:53:17 -0400] [Job 1] PPD options: -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [21/Feb/2011:17:53:17 -0400] [Job 1] PostScript to be injected:
D [21/Feb/2011:17:53:17 -0400] [Job 1] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sOutputFile=-  -c .setpdfwrite -f -
D [21/Feb/2011:17:53:17 -0400] [Job 1] Filetype: PDF
D [21/Feb/2011:17:53:17 -0400] [Job 1] Storing temporary files in /var/spool/cups/tmp
D [21/Feb/2011:17:53:17 -0400] [Job 1] File contains 1 pages
D [21/Feb/2011:17:53:17 -0400] [Job 1] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dNOPAUSE -sDEVICE=ljet4 -dMediaPosition=0 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -r300x300 -sOutputFile=- -f   /var/spool/cups/tmp/foomatic-RAwWfd
D [21/Feb/2011:17:53:17 -0400] [Job 1] Starting process "kid3" (generation 1)
D [21/Feb/2011:17:53:17 -0400] [Job 1] Starting process "kid4" (generation 2)
D [21/Feb/2011:17:53:17 -0400] [Job 1] Starting process "renderer" (generation 2)
D [21/Feb/2011:17:53:17 -0400] [Job 1] JCL: %-12345X@PJL
D [21/Feb/2011:17:53:17 -0400] [Job 1] @PJL SET DENSITY=3
D [21/Feb/2011:17:53:17 -0400] [Job 1] @PJL SET RET=MEDIUM
D [21/Feb/2011:17:53:17 -0400] [Job 1] @PJL SET COPIES=1
D [21/Feb/2011:17:53:17 -0400] [Job 1] @PJL SET ECONOMODE=OFF
D [21/Feb/2011:17:53:17 -0400] [Job 1] @PJL SET MANUALFEED=OFF
D [21/Feb/2011:17:53:17 -0400] [Job 1] <job data> %-12345X@PJL RESET
D [21/Feb/2011:17:53:17 -0400] [Job 1]
D [21/Feb/2011:17:53:17 -0400] [Job 1]
D [21/Feb/2011:17:53:17 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] hrDeviceDesc="Unknown"
D [21/Feb/2011:17:53:17 -0400] [Job 1] prtGeneralCurrentLocalization type is 5, expected 2!
D [21/Feb/2011:17:53:17 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] renderer exited with status 0
D [21/Feb/2011:17:53:17 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Read 2075 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Wrote 2075 bytes of print data...
D [21/Feb/2011:17:53:17 -0400] [Job 1] kid4 exited with status 0
D [21/Feb/2011:17:53:17 -0400] [Job 1] kid3 finished
D [21/Feb/2011:17:53:17 -0400] [Job 1] Kid3 exit status: 0
D [21/Feb/2011:17:53:17 -0400] [Job 1]
D [21/Feb/2011:17:53:17 -0400] [Job 1] Closing foomatic-rip.
D [21/Feb/2011:17:53:17 -0400] [Job 1] STATE: +connecting-to-device
D [21/Feb/2011:17:53:17 -0400] [Job 1] Looking up "192.168.2.199"...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Connecting to 192.168.2.199:515 for printer PASSTHRU
D [21/Feb/2011:17:53:17 -0400] [Job 1] Connecting to printer...
D [21/Feb/2011:17:53:17 -0400] [Job 1] STATE: -connecting-to-device
D [21/Feb/2011:17:53:17 -0400] [Job 1] Connected to printer...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Connected to 192.168.2.199:515 (IPv4) (local port 1023)...
D [21/Feb/2011:17:53:17 -0400] [Job 1] lpd_command 02 PASSTHRU
D [21/Feb/2011:17:53:17 -0400] [Job 1] Sending command string (10 bytes)...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Reading command status...
D [21/Feb/2011:17:53:17 -0400] [Job 1] lpd_command returning 0
D [21/Feb/2011:17:53:17 -0400] [Job 1] Control file is:
D [21/Feb/2011:17:53:17 -0400] [Job 1] HLatitude-D610
D [21/Feb/2011:17:53:17 -0400] [Job 1] Pkim
D [21/Feb/2011:17:53:17 -0400] [Job 1] JTest Page
D [21/Feb/2011:17:53:17 -0400] [Job 1] ldfA957Latitude-D610
D [21/Feb/2011:17:53:17 -0400] [Job 1] UdfA957Latitude-D610
D [21/Feb/2011:17:53:17 -0400] [Job 1] NTest Page
D [21/Feb/2011:17:53:17 -0400] [Job 1] lpd_command 02 84 cfA957Latitude-D610
D [21/Feb/2011:17:53:17 -0400] [Job 1] Sending command string (24 bytes)...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Reading command status...
D [21/Feb/2011:17:53:17 -0400] [Job 1] lpd_command returning 0
D [21/Feb/2011:17:53:17 -0400] [Job 1] Sending control file (84 bytes)
D [21/Feb/2011:17:53:17 -0400] [Job 1] Control file sent successfully
D [21/Feb/2011:17:53:17 -0400] [Job 1] lpd_command 03 157723 dfA957Latitude-D610
D [21/Feb/2011:17:53:17 -0400] [Job 1] Sending command string (28 bytes)...
D [21/Feb/2011:17:53:17 -0400] [Job 1] Reading command status...
D [21/Feb/2011:17:53:17 -0400] [Job 1] lpd_command returning 1
D [21/Feb/2011:17:53:17 -0400] [Job 1] Backend returned status 1 (failed)
D [21/Feb/2011:17:53:17 -0400] [Job 1] End of messages
D [21/Feb/2011:17:53:17 -0400] [Job 1] printer-state=3(idle)
D [21/Feb/2011:17:53:17 -0400] [Job 1] printer-state-message="/usr/lib/cups/backend/lpd failed"
D [21/Feb/2011:17:53:17 -0400] [Job 1] printer-state-reasons=none
D [21/Feb/2011:17:58:20 -0400] [Job 1] The following messages were recorded from 17:58:18 to 17:58:20
D [21/Feb/2011:17:58:20 -0400] [Job 1] Job submission timed out.
D [21/Feb/2011:17:58:20 -0400] [Job 1] job-sheets=none,none
D [21/Feb/2011:17:58:20 -0400] [Job 1] argv[0]="HP-LaserJet-4L"
D [21/Feb/2011:17:58:20 -0400] [Job 1] argv[1]="1"
D [21/Feb/2011:17:58:20 -0400] [Job 1] argv[2]="kim"
D [21/Feb/2011:17:58:20 -0400] [Job 1] argv[3]="Test Page"
D [21/Feb/2011:17:58:20 -0400] [Job 1] argv[4]="1"
D [21/Feb/2011:17:58:20 -0400] [Job 1] argv[5]="PageSize=Letter job-uuid=urn:uuid:cebd8607-8d6e-3742-5ddb-a0c68de405d0 job-originating-host-name=localhost"
D [21/Feb/2011:17:58:20 -0400] [Job 1] argv[6]="/var/spool/cups/d00001-001"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[8]="HOME=/var/spool/cups/tmp"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[10]="SERVER_ADMIN=root@Latitude-D610"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[11]="SOFTWARE=CUPS/1.4.4"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[13]="USER=root"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[16]="IPP_PORT=631"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[17]="CHARSET=utf-8"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[18]="LANG=en_CA.UTF-8"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[19]="PPD=/etc/cups/ppd/HP-LaserJet-4L.ppd"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[20]="RIP_MAX_CACHE=auto"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[21]="CONTENT_TYPE=application/postscript"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[22]="DEVICE_URI=lpd://192.168.2.199/PASSTHRU"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[23]="PRINTER_INFO=HP LaserJet 4L"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[24]="PRINTER_LOCATION="
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[25]="PRINTER=HP-LaserJet-4L"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[26]="CUPS_FILETYPE=document"
D [21/Feb/2011:17:58:20 -0400] [Job 1] envp[27]="FINAL_CONTENT_TYPE=printer/HP-LaserJet-4L"
D [21/Feb/2011:17:58:20 -0400] [Job 1] Started filter /usr/lib/cups/filter/pstopdf (PID 30995)
D [21/Feb/2011:17:58:20 -0400] [Job 1] Started filter /usr/lib/cups/filter/pdftopdf (PID 30996)
D [21/Feb/2011:17:58:20 -0400] [Job 1] Started filter /usr/lib/cups/filter/foomatic-rip (PID 30997)
D [21/Feb/2011:17:58:20 -0400] [Job 1] Started backend /usr/lib/cups/backend/lpd (PID 30998)
D [21/Feb/2011:17:58:20 -0400] [Job 1] pstopdf 6 args: 1 kim Test Page 1 PageSize=Letter job-uuid=urn:uuid:cebd8607-8d6e-3742-5ddb-a0c68de405d0 job-originating-host-name=localhost /var/spool/cups/d00001-001
D [21/Feb/2011:17:58:20 -0400] [Job 1] Getting input from file
D [21/Feb/2011:17:58:20 -0400] [Job 1] STATE: +connecting-to-device
D [21/Feb/2011:17:58:20 -0400] [Job 1] Looking up "192.168.2.199"...
D [21/Feb/2011:17:58:20 -0400] [Job 1] foomatic-rip version 4.0.5.223 running...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Parsing PPD file ...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Added option PageSize
D [21/Feb/2011:17:58:20 -0400] [Job 1] Added option ImageableArea
D [21/Feb/2011:17:58:20 -0400] [Job 1] Added option PaperDimension
D [21/Feb/2011:17:58:20 -0400] [Job 1] PPD: /etc/cups/ppd/HP-LaserJet-4L.ppd
D [21/Feb/2011:17:58:20 -0400] [Job 1] Copying print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] backendRunLoop(print_fd=-1, device_fd=6, snmp_fd=5, addr=0x20e69064, use_bc=0, side_cb=0x8e1d30)
D [21/Feb/2011:17:58:20 -0400] [Job 1] Added option InputSlot
D [21/Feb/2011:17:58:20 -0400] [Job 1] Added option Manualfeed
D [21/Feb/2011:17:58:20 -0400] [Job 1] Added option Economode
D [21/Feb/2011:17:58:20 -0400] [Job 1] Added option Copies
D [21/Feb/2011:17:58:20 -0400] [Job 1] Added option Resolution
D [21/Feb/2011:17:58:20 -0400] [Job 1] Added option REt
D [21/Feb/2011:17:58:20 -0400] [Job 1] Added option TonerDensity
D [21/Feb/2011:17:58:20 -0400] [Job 1] Added option HalftoningAlgorithm
D [21/Feb/2011:17:58:20 -0400] [Job 1] Added option Font
D [21/Feb/2011:17:58:20 -0400] [Job 1]
D [21/Feb/2011:17:58:20 -0400] [Job 1] Parameter Summary
D [21/Feb/2011:17:58:20 -0400] [Job 1] -----------------
D [21/Feb/2011:17:58:20 -0400] [Job 1]
D [21/Feb/2011:17:58:20 -0400] [Job 1] Spooler: cups
D [21/Feb/2011:17:58:20 -0400] [Job 1] Printer: HP-LaserJet-4L
D [21/Feb/2011:17:58:20 -0400] [Job 1] Shell: /bin/bash
D [21/Feb/2011:17:58:20 -0400] [Job 1] PPD file: /etc/cups/ppd/HP-LaserJet-4L.ppd
D [21/Feb/2011:17:58:20 -0400] [Job 1] ATTR file:
D [21/Feb/2011:17:58:20 -0400] [Job 1] Printer model: HP LaserJet 4L Foomatic/ljet4 (recommended)
D [21/Feb/2011:17:58:20 -0400] [Job 1] Job title: Test Page
D [21/Feb/2011:17:58:20 -0400] [Job 1] File(s) to be printed:
D [21/Feb/2011:17:58:20 -0400] [Job 1] <STDIN>
D [21/Feb/2011:17:58:20 -0400] [Job 1]
D [21/Feb/2011:17:58:20 -0400] [Job 1] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [21/Feb/2011:17:58:20 -0400] [Job 1] Printing system options:
D [21/Feb/2011:17:58:20 -0400] [Job 1] Pondering option 'job-uuid=urn:uuid:cebd8607-8d6e-3742-5ddb-a0c68de405d0'
D [21/Feb/2011:17:58:20 -0400] [Job 1] Unknown option job-uuid=urn:uuid:cebd8607-8d6e-3742-5ddb-a0c68de405d0.
D [21/Feb/2011:17:58:20 -0400] [Job 1] Pondering option 'job-originating-host-name=localhost'
D [21/Feb/2011:17:58:20 -0400] [Job 1] Unknown option job-originating-host-name=localhost.
D [21/Feb/2011:17:58:20 -0400] [Job 1] Options from the PPD file:
D [21/Feb/2011:17:58:20 -0400] [Job 1] Pondering option 'PageSize=Letter'
D [21/Feb/2011:17:58:20 -0400] [Job 1]
D [21/Feb/2011:17:58:20 -0400] [Job 1] ================================================
D [21/Feb/2011:17:58:20 -0400] [Job 1]
D [21/Feb/2011:17:58:20 -0400] [Job 1] File: <STDIN>
D [21/Feb/2011:17:58:20 -0400] [Job 1]
D [21/Feb/2011:17:58:20 -0400] [Job 1] ================================================
D [21/Feb/2011:17:58:20 -0400] [Job 1]
D [21/Feb/2011:17:58:20 -0400] [Job 1] Resolution: 300x300
D [21/Feb/2011:17:58:20 -0400] [Job 1] Page size: Letter
D [21/Feb/2011:17:58:20 -0400] [Job 1] Width: 612, height: 792, absolute margins: 18, 36, 594, 756
D [21/Feb/2011:17:58:20 -0400] [Job 1] Relative margins: 18, 36, 18, 36
D [21/Feb/2011:17:58:20 -0400] [Job 1] PPD options: -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [21/Feb/2011:17:58:20 -0400] [Job 1] PostScript to be injected:
D [21/Feb/2011:17:58:20 -0400] [Job 1] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sOutputFile=-  -c .setpdfwrite -f -
D [21/Feb/2011:17:58:20 -0400] [Job 1] Filetype: PDF
D [21/Feb/2011:17:58:20 -0400] [Job 1] Storing temporary files in /var/spool/cups/tmp
D [21/Feb/2011:17:58:20 -0400] [Job 1] File contains 1 pages
D [21/Feb/2011:17:58:20 -0400] [Job 1] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dNOPAUSE -sDEVICE=ljet4 -dMediaPosition=0 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -r300x300 -sOutputFile=- -f   /var/spool/cups/tmp/foomatic-yvaVx9
D [21/Feb/2011:17:58:20 -0400] [Job 1] Starting process "kid3" (generation 1)
D [21/Feb/2011:17:58:20 -0400] [Job 1] Starting process "kid4" (generation 2)
D [21/Feb/2011:17:58:20 -0400] [Job 1] Starting process "renderer" (generation 2)
D [21/Feb/2011:17:58:20 -0400] [Job 1] JCL: %-12345X@PJL
D [21/Feb/2011:17:58:20 -0400] [Job 1] @PJL SET DENSITY=3
D [21/Feb/2011:17:58:20 -0400] [Job 1] @PJL SET RET=MEDIUM
D [21/Feb/2011:17:58:20 -0400] [Job 1] @PJL SET COPIES=1
D [21/Feb/2011:17:58:20 -0400] [Job 1] @PJL SET ECONOMODE=OFF
D [21/Feb/2011:17:58:20 -0400] [Job 1] @PJL SET MANUALFEED=OFF
D [21/Feb/2011:17:58:20 -0400] [Job 1] <job data> %-12345X@PJL RESET
D [21/Feb/2011:17:58:20 -0400] [Job 1]
D [21/Feb/2011:17:58:20 -0400] [Job 1]
D [21/Feb/2011:17:58:20 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] hrDeviceDesc="Unknown"
D [21/Feb/2011:17:58:20 -0400] [Job 1] prtGeneralCurrentLocalization type is 5, expected 2!
D [21/Feb/2011:17:58:20 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] renderer exited with status 0
D [21/Feb/2011:17:58:20 -0400] [Job 1] Read 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Wrote 8192 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Read 2075 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Wrote 2075 bytes of print data...
D [21/Feb/2011:17:58:20 -0400] [Job 1] kid4 exited with status 0
D [21/Feb/2011:17:58:20 -0400] [Job 1] kid3 finished
D [21/Feb/2011:17:58:20 -0400] [Job 1] Kid3 exit status: 0
D [21/Feb/2011:17:58:20 -0400] [Job 1]
D [21/Feb/2011:17:58:20 -0400] [Job 1] Closing foomatic-rip.
D [21/Feb/2011:17:58:20 -0400] [Job 1] STATE: +connecting-to-device
D [21/Feb/2011:17:58:20 -0400] [Job 1] Looking up "192.168.2.199"...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Connecting to 192.168.2.199:515 for printer PASSTHRU
D [21/Feb/2011:17:58:20 -0400] [Job 1] Connecting to printer...
D [21/Feb/2011:17:58:20 -0400] [Job 1] STATE: -connecting-to-device
D [21/Feb/2011:17:58:20 -0400] [Job 1] Connected to printer...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Connected to 192.168.2.199:515 (IPv4) (local port 1023)...
D [21/Feb/2011:17:58:20 -0400] [Job 1] lpd_command 02 PASSTHRU
D [21/Feb/2011:17:58:20 -0400] [Job 1] Sending command string (10 bytes)...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Reading command status...
D [21/Feb/2011:17:58:20 -0400] [Job 1] lpd_command returning 0
D [21/Feb/2011:17:58:20 -0400] [Job 1] Control file is:
D [21/Feb/2011:17:58:20 -0400] [Job 1] HLatitude-D610
D [21/Feb/2011:17:58:20 -0400] [Job 1] Pkim
D [21/Feb/2011:17:58:20 -0400] [Job 1] JTest Page
D [21/Feb/2011:17:58:20 -0400] [Job 1] ldfA998Latitude-D610
D [21/Feb/2011:17:58:20 -0400] [Job 1] UdfA998Latitude-D610
D [21/Feb/2011:17:58:20 -0400] [Job 1] NTest Page
D [21/Feb/2011:17:58:20 -0400] [Job 1] lpd_command 02 84 cfA998Latitude-D610
D [21/Feb/2011:17:58:20 -0400] [Job 1] Sending command string (24 bytes)...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Reading command status...
D [21/Feb/2011:17:58:20 -0400] [Job 1] lpd_command returning 0
D [21/Feb/2011:17:58:20 -0400] [Job 1] Sending control file (84 bytes)
D [21/Feb/2011:17:58:20 -0400] [Job 1] Control file sent successfully
D [21/Feb/2011:17:58:20 -0400] [Job 1] lpd_command 03 157723 dfA998Latitude-D610
D [21/Feb/2011:17:58:20 -0400] [Job 1] Sending command string (28 bytes)...
D [21/Feb/2011:17:58:20 -0400] [Job 1] Reading command status...
D [21/Feb/2011:17:58:20 -0400] [Job 1] lpd_command returning 1
D [21/Feb/2011:17:58:20 -0400] [Job 1] Backend returned status 1 (failed)
D [21/Feb/2011:17:58:20 -0400] [Job 1] End of messages
D [21/Feb/2011:17:58:20 -0400] [Job 1] printer-state=3(idle)
D [21/Feb/2011:17:58:20 -0400] [Job 1] printer-state-message="/usr/lib/cups/backend/lpd failed"
D [21/Feb/2011:17:58:20 -0400] [Job 1] printer-state-reasons=none
E [21/Feb/2011:18:23:49 -0400] [Job 2] Aborting job because it has no files.
E [21/Feb/2011:18:24:00 -0400] [Job 3] Unable to locate printer 'PrintServer'!
D [21/Feb/2011:18:24:01 -0400] [Job 3] The following messages were recorded from 18:24:00 to 18:24:01
D [21/Feb/2011:18:24:01 -0400] [Job 3] Adding start banner page "none".
D [21/Feb/2011:18:24:01 -0400] [Job 3] Adding end banner page "none".
D [21/Feb/2011:18:24:01 -0400] [Job 3] File of type application/vnd.cups-banner queued by "kim".
D [21/Feb/2011:18:24:01 -0400] [Job 3] hold_until=0
D [21/Feb/2011:18:24:01 -0400] [Job 3] Queued on "HP-LaserJet-4L" by "kim".
D [21/Feb/2011:18:24:01 -0400] [Job 3] job-sheets=none,none
D [21/Feb/2011:18:24:01 -0400] [Job 3] argv[0]="HP-LaserJet-4L"
D [21/Feb/2011:18:24:01 -0400] [Job 3] argv[1]="3"
D [21/Feb/2011:18:24:01 -0400] [Job 3] argv[2]="kim"
D [21/Feb/2011:18:24:01 -0400] [Job 3] argv[3]="Test Page"
D [21/Feb/2011:18:24:01 -0400] [Job 3] argv[4]="1"
D [21/Feb/2011:18:24:01 -0400] [Job 3] argv[5]="job-uuid=urn:uuid:9f1ebf9b-7f49-3869-65fc-cb10610a50b4 job-originating-host-name=localhost"
D [21/Feb/2011:18:24:01 -0400] [Job 3] argv[6]="/var/spool/cups/d00003-001"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[8]="HOME=/var/spool/cups/tmp"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[10]="SERVER_ADMIN=root@Latitude-D610"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[11]="SOFTWARE=CUPS/1.4.4"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[13]="USER=root"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[16]="IPP_PORT=631"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[17]="CHARSET=utf-8"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[18]="LANG=en_US.UTF-8"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[19]="PPD=/etc/cups/ppd/HP-LaserJet-4L.ppd"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[20]="RIP_MAX_CACHE=auto"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[21]="CONTENT_TYPE=application/vnd.cups-banner"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[22]="DEVICE_URI=socket://PrintServer:9100/lpt1"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[23]="PRINTER_INFO=HP LaserJet 4L"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[24]="PRINTER_LOCATION="
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[25]="PRINTER=HP-LaserJet-4L"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[26]="CUPS_FILETYPE=document"
D [21/Feb/2011:18:24:01 -0400] [Job 3] envp[27]="FINAL_CONTENT_TYPE=printer/HP-LaserJet-4L"
D [21/Feb/2011:18:24:01 -0400] [Job 3] Started filter /usr/lib/cups/filter/bannertops (PID 2042)
D [21/Feb/2011:18:24:01 -0400] [Job 3] Started filter /usr/lib/cups/filter/pstopdf (PID 2043)
D [21/Feb/2011:18:24:01 -0400] [Job 3] Started filter /usr/lib/cups/filter/pdftopdf (PID 2044)
D [21/Feb/2011:18:24:01 -0400] [Job 3] Started filter /usr/lib/cups/filter/foomatic-rip (PID 2045)
D [21/Feb/2011:18:24:01 -0400] [Job 3] Started backend /usr/lib/cups/backend/socket (PID 2046)
D [21/Feb/2011:18:24:01 -0400] [Job 3] load_banner(filename="/var/spool/cups/d00003-001")
D [21/Feb/2011:18:24:01 -0400] [Job 3] pstopdf 5 args: 3 kim Test Page 1 job-uuid=urn:uuid:9f1ebf9b-7f49-3869-65fc-cb10610a50b4 job-originating-host-name=localhost
D [21/Feb/2011:18:24:01 -0400] [Job 3] PPD: /etc/cups/ppd/HP-LaserJet-4L.ppd
D [21/Feb/2011:18:24:01 -0400] [Job 3] Getting input from file
D [21/Feb/2011:18:24:01 -0400] [Job 3] STATE: +connecting-to-device
D [21/Feb/2011:18:24:01 -0400] [Job 3] foomatic-rip version 4.0.5.223 running...
D [21/Feb/2011:18:24:01 -0400] [Job 3] Parsing PPD file ...
D [21/Feb/2011:18:24:01 -0400] [Job 3] Added option PageSize
D [21/Feb/2011:18:24:01 -0400] [Job 3] Added option ImageableArea
D [21/Feb/2011:18:24:01 -0400] [Job 3] Added option PaperDimension
D [21/Feb/2011:18:24:01 -0400] [Job 3] Added option InputSlot
D [21/Feb/2011:18:24:01 -0400] [Job 3] Looking up "PrintServer"...
D [21/Feb/2011:18:24:01 -0400] [Job 3] Page = 612x792; 18,36 to 594,756
D [21/Feb/2011:18:24:01 -0400] [Job 3] Added option Manualfeed
D [21/Feb/2011:18:24:01 -0400] [Job 3] Added option Economode
D [21/Feb/2011:18:24:01 -0400] [Job 3] Added option Copies
D [21/Feb/2011:18:24:01 -0400] [Job 3] Added option Resolution
D [21/Feb/2011:18:24:01 -0400] [Job 3] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)
D [21/Feb/2011:18:24:01 -0400] [Job 3] PNG image: 192x128x8, color_type=2 (RGB)
D [21/Feb/2011:18:24:01 -0400] [Job 3] Added option REt
D [21/Feb/2011:18:24:01 -0400] [Job 3] Added option TonerDensity
D [21/Feb/2011:18:24:01 -0400] [Job 3] Added option HalftoningAlgorithm
D [21/Feb/2011:18:24:01 -0400] [Job 3] Added option Font
D [21/Feb/2011:18:24:01 -0400] [Job 3]
D [21/Feb/2011:18:24:01 -0400] [Job 3] Parameter Summary
D [21/Feb/2011:18:24:01 -0400] [Job 3] -----------------
D [21/Feb/2011:18:24:01 -0400] [Job 3]
D [21/Feb/2011:18:24:01 -0400] [Job 3] Spooler: cups
D [21/Feb/2011:18:24:01 -0400] [Job 3] Printer: HP-LaserJet-4L
D [21/Feb/2011:18:24:01 -0400] [Job 3] Shell: /bin/bash
D [21/Feb/2011:18:24:01 -0400] [Job 3] PPD file: /etc/cups/ppd/HP-LaserJet-4L.ppd
D [21/Feb/2011:18:24:01 -0400] [Job 3] ATTR file:
D [21/Feb/2011:18:24:01 -0400] [Job 3] Printer model: HP LaserJet 4L Foomatic/ljet4 (recommended)
D [21/Feb/2011:18:24:01 -0400] [Job 3] Job title: Test Page
D [21/Feb/2011:18:24:01 -0400] [Job 3] File(s) to be printed:
D [21/Feb/2011:18:24:01 -0400] [Job 3] <STDIN>
D [21/Feb/2011:18:24:01 -0400] [Job 3]
D [21/Feb/2011:18:24:01 -0400] [Job 3] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [21/Feb/2011:18:24:01 -0400] [Job 3] Printing system options:
D [21/Feb/2011:18:24:01 -0400] [Job 3] Pondering option 'job-uuid=urn:uuid:9f1ebf9b-7f49-3869-65fc-cb10610a50b4'
D [21/Feb/2011:18:24:01 -0400] [Job 3] Unknown option job-uuid=urn:uuid:9f1ebf9b-7f49-3869-65fc-cb10610a50b4.
D [21/Feb/2011:18:24:01 -0400] [Job 3] Pondering option 'job-originating-host-name=localhost'
D [21/Feb/2011:18:24:01 -0400] [Job 3] Unknown option job-originating-host-name=localhost.
D [21/Feb/2011:18:24:01 -0400] [Job 3] Options from the PPD file:
D [21/Feb/2011:18:24:01 -0400] [Job 3]
D [21/Feb/2011:18:24:01 -0400] [Job 3] ================================================
D [21/Feb/2011:18:24:01 -0400] [Job 3]
D [21/Feb/2011:18:24:01 -0400] [Job 3] File: <STDIN>
D [21/Feb/2011:18:24:01 -0400] [Job 3]
D [21/Feb/2011:18:24:01 -0400] [Job 3] ================================================
D [21/Feb/2011:18:24:01 -0400] [Job 3]
D [21/Feb/2011:18:24:01 -0400] [Job 3] Set job-printer-state-message to "Unable to locate printer 'PrintServer'!", current level=ERROR
D [21/Feb/2011:18:24:01 -0400] [Job 3] Resolution: 300x300
D [21/Feb/2011:18:24:01 -0400] [Job 3] Page size: Letter
D [21/Feb/2011:18:24:01 -0400] [Job 3] Width: 612, height: 792, absolute margins: 18, 36, 594, 756
D [21/Feb/2011:18:24:01 -0400] [Job 3] Relative margins: 18, 36, 18, 36
D [21/Feb/2011:18:24:01 -0400] [Job 3] PPD options: -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [21/Feb/2011:18:24:01 -0400] [Job 3] PostScript to be injected:
D [21/Feb/2011:18:24:01 -0400] [Job 3] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sOutputFile=-  -c .setpdfwrite -f -
D [21/Feb/2011:18:24:01 -0400] [Job 3] Filetype: PDF
D [21/Feb/2011:18:24:01 -0400] [Job 3] Storing temporary files in /var/spool/cups/tmp
D [21/Feb/2011:18:24:01 -0400] [Job 3] File contains 1 pages
D [21/Feb/2011:18:24:01 -0400] [Job 3] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dNOPAUSE -sDEVICE=ljet4 -dMediaPosition=0 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -r300x300 -sOutputFile=- -f   /var/spool/cups/tmp/foomatic-ERU5aF
D [21/Feb/2011:18:24:01 -0400] [Job 3] Starting process "kid3" (generation 1)
D [21/Feb/2011:18:24:01 -0400] [Job 3] Starting process "kid4" (generation 2)
D [21/Feb/2011:18:24:01 -0400] [Job 3] Starting process "renderer" (generation 2)
D [21/Feb/2011:18:24:01 -0400] [Job 3] JCL: %-12345X@PJL
D [21/Feb/2011:18:24:01 -0400] [Job 3] @PJL SET DENSITY=3
D [21/Feb/2011:18:24:01 -0400] [Job 3] @PJL SET RET=MEDIUM
D [21/Feb/2011:18:24:01 -0400] [Job 3] @PJL SET COPIES=1
D [21/Feb/2011:18:24:01 -0400] [Job 3] @PJL SET ECONOMODE=OFF
D [21/Feb/2011:18:24:01 -0400] [Job 3] @PJL SET MANUALFEED=OFF
D [21/Feb/2011:18:24:01 -0400] [Job 3] <job data> %-12345X@PJL RESET
D [21/Feb/2011:18:24:01 -0400] [Job 3]
D [21/Feb/2011:18:24:01 -0400] [Job 3]
D [21/Feb/2011:18:24:01 -0400] [Job 3] renderer received signal 13
D [21/Feb/2011:18:24:01 -0400] [Job 3] Kid3 exit status: 1
D [21/Feb/2011:18:24:01 -0400] [Job 3] Backend returned status 4 (stop printer)
D [21/Feb/2011:18:24:01 -0400] [Job 3] Printer stopped due to backend errors; please consult the error_log file for details.
D [21/Feb/2011:18:24:01 -0400] [Job 3] End of messages
D [21/Feb/2011:18:24:01 -0400] [Job 3] printer-state=5(stopped)
D [21/Feb/2011:18:24:01 -0400] [Job 3] printer-state-message="Unable to locate printer 'PrintServer'!"
D [21/Feb/2011:18:24:01 -0400] [Job 3] printer-state-reasons=paused
E [21/Feb/2011:18:29:58 -0400] Returning IPP client-error-not-possible for CUPS-Add-Modify-Printer (ipp://localhost/printers/HP-LaserJet-4L) from localhost
E [21/Feb/2011:18:43:50 -0400] [Job 4] Unable to locate printer 'PRINTSERVER'!
D [21/Feb/2011:18:43:50 -0400] [Job 4] The following messages were recorded from 18:43:50 to 18:43:50
D [21/Feb/2011:18:43:50 -0400] [Job 4] Adding start banner page "none".
D [21/Feb/2011:18:43:50 -0400] [Job 4] Queued on "HP-Laserjet-4L" by "kim".
D [21/Feb/2011:18:43:50 -0400] [Job 4] File of type application/vnd.cups-command queued by "kim".
D [21/Feb/2011:18:43:50 -0400] [Job 4] Adding end banner page "none".
D [21/Feb/2011:18:43:50 -0400] [Job 4] job-sheets=none,none
D [21/Feb/2011:18:43:50 -0400] [Job 4] argv[0]="HP-Laserjet-4L"
D [21/Feb/2011:18:43:50 -0400] [Job 4] argv[1]="4"
D [21/Feb/2011:18:43:50 -0400] [Job 4] argv[2]="kim"
D [21/Feb/2011:18:43:50 -0400] [Job 4] argv[3]="Set Default Options"
D [21/Feb/2011:18:43:50 -0400] [Job 4] argv[4]="1"
D [21/Feb/2011:18:43:50 -0400] [Job 4] argv[5]="job-uuid=urn:uuid:f1df343a-5e4e-311b-43f5-0dcbded77123 job-originating-host-name=localhost"
D [21/Feb/2011:18:43:50 -0400] [Job 4] argv[6]="/var/spool/cups/d00004-001"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[8]="HOME=/var/spool/cups/tmp"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[10]="SERVER_ADMIN=root@Latitude-D610"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[11]="SOFTWARE=CUPS/1.4.4"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[13]="USER=root"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[16]="IPP_PORT=631"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[17]="CHARSET=utf-8"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[18]="LANG=en_US.UTF-8"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[19]="PPD=/etc/cups/ppd/HP-Laserjet-4L.ppd"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[20]="RIP_MAX_CACHE=auto"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[21]="CONTENT_TYPE=application/vnd.cups-command"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[22]="DEVICE_URI=ipp://PRINTSERVER/ipp/port1"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[23]="PRINTER_INFO=HP Laserjet 4L"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[24]="PRINTER_LOCATION="
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[25]="PRINTER=HP-Laserjet-4L"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[26]="CUPS_FILETYPE=document"
D [21/Feb/2011:18:43:50 -0400] [Job 4] envp[27]="FINAL_CONTENT_TYPE=printer/HP-Laserjet-4L"
D [21/Feb/2011:18:43:50 -0400] [Job 4] Started filter /usr/lib/cups/filter/commandtops (PID 2366)
D [21/Feb/2011:18:43:50 -0400] [Job 4] Started backend /usr/lib/cups/backend/ipp (PID 2367)
D [21/Feb/2011:18:43:50 -0400] [Job 4] STATE: +connecting-to-device
D [21/Feb/2011:18:43:50 -0400] [Job 4] Looking up "PRINTSERVER"...
D [21/Feb/2011:18:43:50 -0400] [Job 4] Set job-printer-state-message to "Unable to locate printer 'PRINTSERVER'!", current level=ERROR
D [21/Feb/2011:18:43:50 -0400] [Job 4] Unable to auto-configure PostScript Printer - no bidirectional I/O available!
D [21/Feb/2011:18:43:50 -0400] [Job 4] Backend returned status 4 (stop printer)
D [21/Feb/2011:18:43:50 -0400] [Job 4] Printer stopped due to backend errors; please consult the error_log file for details.
D [21/Feb/2011:18:43:50 -0400] [Job 4] End of messages
D [21/Feb/2011:18:43:50 -0400] [Job 4] printer-state=5(stopped)
D [21/Feb/2011:18:43:50 -0400] [Job 4] printer-state-message="Unable to locate printer 'PRINTSERVER'!"
D [21/Feb/2011:18:43:50 -0400] [Job 4] printer-state-reasons=paused
E [21/Feb/2011:18:45:15 -0400] [Job 4] Empty print file!
D [21/Feb/2011:18:45:15 -0400] [Job 4] The following messages were recorded from 18:45:15 to 18:45:15
D [21/Feb/2011:18:45:15 -0400] [Job 4] job-sheets=none,none
D [21/Feb/2011:18:45:15 -0400] [Job 4] argv[0]="HP-Laserjet-4L"
D [21/Feb/2011:18:45:15 -0400] [Job 4] argv[1]="4"
D [21/Feb/2011:18:45:15 -0400] [Job 4] argv[2]="kim"
D [21/Feb/2011:18:45:15 -0400] [Job 4] argv[3]="Set Default Options"
D [21/Feb/2011:18:45:15 -0400] [Job 4] argv[4]="1"
D [21/Feb/2011:18:45:15 -0400] [Job 4] argv[5]="job-uuid=urn:uuid:f1df343a-5e4e-311b-43f5-0dcbded77123 job-originating-host-name=localhost"
D [21/Feb/2011:18:45:15 -0400] [Job 4] argv[6]="/var/spool/cups/d00004-001"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[8]="HOME=/var/spool/cups/tmp"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[10]="SERVER_ADMIN=root@Latitude-D610"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[11]="SOFTWARE=CUPS/1.4.4"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[13]="USER=root"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[16]="IPP_PORT=631"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[17]="CHARSET=utf-8"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[18]="LANG=en_US.UTF-8"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[19]="PPD=/etc/cups/ppd/HP-Laserjet-4L.ppd"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[20]="RIP_MAX_CACHE=auto"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[21]="CONTENT_TYPE=application/vnd.cups-command"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[22]="DEVICE_URI=ipp://192.168.2.199/ipp/port1"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[23]="PRINTER_INFO=HP Laserjet 4L"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[24]="PRINTER_LOCATION="
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[25]="PRINTER=HP-Laserjet-4L"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[26]="CUPS_FILETYPE=document"
D [21/Feb/2011:18:45:15 -0400] [Job 4] envp[27]="FINAL_CONTENT_TYPE=printer/HP-Laserjet-4L"
D [21/Feb/2011:18:45:15 -0400] [Job 4] Started filter /usr/lib/cups/filter/commandtops (PID 2409)
D [21/Feb/2011:18:45:15 -0400] [Job 4] Started backend /usr/lib/cups/backend/ipp (PID 2410)
D [21/Feb/2011:18:45:15 -0400] [Job 4] STATE: +connecting-to-device
D [21/Feb/2011:18:45:15 -0400] [Job 4] Looking up "192.168.2.199"...
D [21/Feb/2011:18:45:15 -0400] [Job 4] Copying print data...
D [21/Feb/2011:18:45:15 -0400] [Job 4] backendRunLoop(print_fd=-1, device_fd=6, snmp_fd=5, addr=0x20927064, use_bc=0, side_cb=0x6cf2a0)
D [21/Feb/2011:18:45:15 -0400] [Job 4] Unable to auto-configure PostScript Printer - no bidirectional I/O available!
D [21/Feb/2011:18:45:15 -0400] [Job 4] Set job-printer-state-message to "Empty print file!", current level=ERROR
D [21/Feb/2011:18:45:15 -0400] [Job 4] Backend returned status 1 (failed)
D [21/Feb/2011:18:45:15 -0400] [Job 4] End of messages
D [21/Feb/2011:18:45:15 -0400] [Job 4] printer-state=3(idle)
D [21/Feb/2011:18:45:15 -0400] [Job 4] printer-state-message="Empty print file!"
D [21/Feb/2011:18:45:15 -0400] [Job 4] printer-state-reasons=none
E [21/Feb/2011:18:45:32 -0400] [Job 5] Destination printer does not exist!
D [21/Feb/2011:18:45:32 -0400] [Job 5] The following messages were recorded from 18:45:30 to 18:45:32
D [21/Feb/2011:18:45:32 -0400] [Job 5] Adding start banner page "none".
D [21/Feb/2011:18:45:32 -0400] [Job 5] Adding end banner page "none".
D [21/Feb/2011:18:45:32 -0400] [Job 5] File of type application/vnd.cups-banner queued by "kim".
D [21/Feb/2011:18:45:32 -0400] [Job 5] hold_until=0
D [21/Feb/2011:18:45:32 -0400] [Job 5] Queued on "HP-Laserjet-4L" by "kim".
D [21/Feb/2011:18:45:32 -0400] [Job 5] job-sheets=none,none
D [21/Feb/2011:18:45:32 -0400] [Job 5] argv[0]="HP-Laserjet-4L"
D [21/Feb/2011:18:45:32 -0400] [Job 5] argv[1]="5"
D [21/Feb/2011:18:45:32 -0400] [Job 5] argv[2]="kim"
D [21/Feb/2011:18:45:32 -0400] [Job 5] argv[3]="Test Page"
D [21/Feb/2011:18:45:32 -0400] [Job 5] argv[4]="1"
D [21/Feb/2011:18:45:32 -0400] [Job 5] argv[5]="job-uuid=urn:uuid:fd6dc7e5-e377-3610-6acd-009625711227 job-originating-host-name=localhost"
D [21/Feb/2011:18:45:32 -0400] [Job 5] argv[6]="/var/spool/cups/d00005-001"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[8]="HOME=/var/spool/cups/tmp"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[10]="SERVER_ADMIN=root@Latitude-D610"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[11]="SOFTWARE=CUPS/1.4.4"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[13]="USER=root"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[16]="IPP_PORT=631"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[17]="CHARSET=utf-8"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[18]="LANG=en_US.UTF-8"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[19]="PPD=/etc/cups/ppd/HP-Laserjet-4L.ppd"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[20]="RIP_MAX_CACHE=auto"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[21]="CONTENT_TYPE=application/vnd.cups-banner"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[22]="DEVICE_URI=ipp://192.168.2.199/ipp/port1"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[23]="PRINTER_INFO=HP Laserjet 4L"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[24]="PRINTER_LOCATION="
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[25]="PRINTER=HP-Laserjet-4L"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[26]="CUPS_FILETYPE=document"
D [21/Feb/2011:18:45:32 -0400] [Job 5] envp[27]="FINAL_CONTENT_TYPE=printer/HP-Laserjet-4L"
D [21/Feb/2011:18:45:32 -0400] [Job 5] Started filter /usr/lib/cups/filter/bannertops (PID 2416)
D [21/Feb/2011:18:45:32 -0400] [Job 5] Started filter /usr/lib/cups/filter/pstopdf (PID 2417)
D [21/Feb/2011:18:45:32 -0400] [Job 5] Started filter /usr/lib/cups/filter/pdftopdf (PID 2418)
D [21/Feb/2011:18:45:32 -0400] [Job 5] Started filter /usr/lib/cups/filter/foomatic-rip (PID 2419)
D [21/Feb/2011:18:45:32 -0400] [Job 5] Started backend /usr/lib/cups/backend/ipp (PID 2420)
D [21/Feb/2011:18:45:32 -0400] [Job 5] load_banner(filename="/var/spool/cups/d00005-001")
D [21/Feb/2011:18:45:32 -0400] [Job 5] pstopdf 5 args: 5 kim Test Page 1 job-uuid=urn:uuid:fd6dc7e5-e377-3610-6acd-009625711227 job-originating-host-name=localhost
D [21/Feb/2011:18:45:32 -0400] [Job 5] PPD: /etc/cups/ppd/HP-Laserjet-4L.ppd
D [21/Feb/2011:18:45:32 -0400] [Job 5] Getting input from file
D [21/Feb/2011:18:45:32 -0400] [Job 5] STATE: +connecting-to-device
D [21/Feb/2011:18:45:32 -0400] [Job 5] foomatic-rip version 4.0.5.223 running...
D [21/Feb/2011:18:45:32 -0400] [Job 5] Parsing PPD file ...
D [21/Feb/2011:18:45:32 -0400] [Job 5] Added option PageSize
D [21/Feb/2011:18:45:32 -0400] [Job 5] Added option ImageableArea
D [21/Feb/2011:18:45:32 -0400] [Job 5] Added option PaperDimension
D [21/Feb/2011:18:45:32 -0400] [Job 5] Added option InputSlot
D [21/Feb/2011:18:45:32 -0400] [Job 5] Looking up "192.168.2.199"...
D [21/Feb/2011:18:45:32 -0400] [Job 5] Copying print data...
D [21/Feb/2011:18:45:32 -0400] [Job 5] backendRunLoop(print_fd=-1, device_fd=6, snmp_fd=5, addr=0x222f5064, use_bc=0, side_cb=0x8cf2a0)
D [21/Feb/2011:18:45:32 -0400] [Job 5] Page = 612x792; 18,36 to 594,756
D [21/Feb/2011:18:45:32 -0400] [Job 5] Added option Manualfeed
D [21/Feb/2011:18:45:32 -0400] [Job 5] Added option Economode
D [21/Feb/2011:18:45:32 -0400] [Job 5] Added option Copies
D [21/Feb/2011:18:45:32 -0400] [Job 5] Added option Resolution
D [21/Feb/2011:18:45:32 -0400] [Job 5] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)
D [21/Feb/2011:18:45:32 -0400] [Job 5] PNG image: 192x128x8, color_type=2 (RGB)
D [21/Feb/2011:18:45:32 -0400] [Job 5] Added option REt
D [21/Feb/2011:18:45:32 -0400] [Job 5] Added option TonerDensity
D [21/Feb/2011:18:45:32 -0400] [Job 5] Added option HalftoningAlgorithm
D [21/Feb/2011:18:45:32 -0400] [Job 5] Added option Font
D [21/Feb/2011:18:45:32 -0400] [Job 5]
D [21/Feb/2011:18:45:32 -0400] [Job 5] Parameter Summary
D [21/Feb/2011:18:45:32 -0400] [Job 5] -----------------
D [21/Feb/2011:18:45:32 -0400] [Job 5]
D [21/Feb/2011:18:45:32 -0400] [Job 5] Spooler: cups
D [21/Feb/2011:18:45:32 -0400] [Job 5] Printer: HP-Laserjet-4L
D [21/Feb/2011:18:45:32 -0400] [Job 5] Shell: /bin/bash
D [21/Feb/2011:18:45:32 -0400] [Job 5] PPD file: /etc/cups/ppd/HP-Laserjet-4L.ppd
D [21/Feb/2011:18:45:32 -0400] [Job 5] ATTR file:
D [21/Feb/2011:18:45:32 -0400] [Job 5] Printer model: HP LaserJet 4L Foomatic/ljet4 (recommended)
D [21/Feb/2011:18:45:32 -0400] [Job 5] Job title: Test Page
D [21/Feb/2011:18:45:32 -0400] [Job 5] File(s) to be printed:
D [21/Feb/2011:18:45:32 -0400] [Job 5] <STDIN>
D [21/Feb/2011:18:45:32 -0400] [Job 5]
D [21/Feb/2011:18:45:32 -0400] [Job 5] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [21/Feb/2011:18:45:32 -0400] [Job 5] Printing system options:
D [21/Feb/2011:18:45:32 -0400] [Job 5] Pondering option 'job-uuid=urn:uuid:fd6dc7e5-e377-3610-6acd-009625711227'
D [21/Feb/2011:18:45:32 -0400] [Job 5] Unknown option job-uuid=urn:uuid:fd6dc7e5-e377-3610-6acd-009625711227.
D [21/Feb/2011:18:45:32 -0400] [Job 5] Pondering option 'job-originating-host-name=localhost'
D [21/Feb/2011:18:45:32 -0400] [Job 5] Unknown option job-originating-host-name=localhost.
D [21/Feb/2011:18:45:32 -0400] [Job 5] Options from the PPD file:
D [21/Feb/2011:18:45:32 -0400] [Job 5]
D [21/Feb/2011:18:45:32 -0400] [Job 5] ================================================
D [21/Feb/2011:18:45:32 -0400] [Job 5]
D [21/Feb/2011:18:45:32 -0400] [Job 5] File: <STDIN>
D [21/Feb/2011:18:45:32 -0400] [Job 5]
D [21/Feb/2011:18:45:32 -0400] [Job 5] ================================================
D [21/Feb/2011:18:45:32 -0400] [Job 5]
D [21/Feb/2011:18:45:32 -0400] [Job 5] Resolution: 300x300
D [21/Feb/2011:18:45:32 -0400] [Job 5] Page size: Letter
D [21/Feb/2011:18:45:32 -0400] [Job 5] Width: 612, height: 792, absolute margins: 18, 36, 594, 756
D [21/Feb/2011:18:45:32 -0400] [Job 5] Relative margins: 18, 36, 18, 36
D [21/Feb/2011:18:45:32 -0400] [Job 5] PPD options: -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [21/Feb/2011:18:45:32 -0400] [Job 5] PostScript to be injected:
D [21/Feb/2011:18:45:32 -0400] [Job 5] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sOutputFile=-  -c .setpdfwrite -f -
D [21/Feb/2011:18:45:32 -0400] [Job 5] Filetype: PDF
D [21/Feb/2011:18:45:32 -0400] [Job 5] Storing temporary files in /var/spool/cups/tmp
D [21/Feb/2011:18:45:32 -0400] [Job 5] File contains 1 pages
D [21/Feb/2011:18:45:32 -0400] [Job 5] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dNOPAUSE -sDEVICE=ljet4 -dMediaPosition=0 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -r300x300 -sOutputFile=- -f   /var/spool/cups/tmp/foomatic-KM5lL9
D [21/Feb/2011:18:45:32 -0400] [Job 5] Starting process "kid3" (generation 1)
D [21/Feb/2011:18:45:32 -0400] [Job 5] Starting process "kid4" (generation 2)
D [21/Feb/2011:18:45:32 -0400] [Job 5] Starting process "renderer" (generation 2)
D [21/Feb/2011:18:45:32 -0400] [Job 5] JCL: %-12345X@PJL
D [21/Feb/2011:18:45:32 -0400] [Job 5] @PJL SET DENSITY=3
D [21/Feb/2011:18:45:32 -0400] [Job 5] @PJL SET RET=MEDIUM
D [21/Feb/2011:18:45:32 -0400] [Job 5] @PJL SET COPIES=1
D [21/Feb/2011:18:45:32 -0400] [Job 5] @PJL SET ECONOMODE=OFF
D [21/Feb/2011:18:45:32 -0400] [Job 5] @PJL SET MANUALFEED=OFF
D [21/Feb/2011:18:45:32 -0400] [Job 5] <job data> %-12345X@PJL RESET
D [21/Feb/2011:18:45:32 -0400] [Job 5]
D [21/Feb/2011:18:45:32 -0400] [Job 5]
D [21/Feb/2011:18:45:32 -0400] [Job 5] Read 8192 bytes of print data...
D [21/Feb/2011:18:45:32 -0400] [Job 5] hrDeviceDesc="Unknown"
D [21/Feb/2011:18:45:32 -0400] [Job 5] prtGeneralCurrentLocalization type is 5, expected 2!
D [21/Feb/2011:18:45:32 -0400] [Job 5] Wrote 8192 bytes of print data...
D [21/Feb/2011:18:45:32 -0400] [Job 5] Read 8192 bytes of print data...
D [21/Feb/2011:18:45:32 -0400] [Job 5] Wrote 8192 bytes of print data...
D [21/Feb/2011:18:45:32 -0400] [Job 5] Read 8192 bytes of print data...
D [21/Feb/2011:18:45:32 -0400] [Job 5] Wrote 8192 bytes of print data...
D [21/Feb/2011:18:45:32 -0400] [Job 5] Read 8192 bytes of print data...
D [21/Feb/2011:18:45:32 -0400] [Job 5] Wrote 8192 bytes of print data...
D [21/Feb/2011:18:45:32 -0400] [Job 5] Read 8192 bytes of print data...
D [21/Feb/2011:18:45:32 -0400] [Job 5] Wrote 8192 bytes of print data...
D [21/Feb/2011:18:45:32 -0400] [Job 5] renderer exited with status 0
D [21/Feb/2011:18:45:32 -0400] [Job 5] Read 5032 bytes of print data...
D [21/Feb/2011:18:45:32 -0400] [Job 5] Wrote 5032 bytes of print data...
D [21/Feb/2011:18:45:32 -0400] [Job 5] kid4 exited with status 0
D [21/Feb/2011:18:45:32 -0400] [Job 5] kid3 finished
D [21/Feb/2011:18:45:32 -0400] [Job 5] Kid3 exit status: 0
D [21/Feb/2011:18:45:32 -0400] [Job 5]
D [21/Feb/2011:18:45:32 -0400] [Job 5] Closing foomatic-rip.
D [21/Feb/2011:18:45:32 -0400] [Job 5] 1 files to send in job...
D [21/Feb/2011:18:45:32 -0400] [Job 5] STATE: +connecting-to-device
D [21/Feb/2011:18:45:32 -0400] [Job 5] Connecting to 192.168.2.199:631
D [21/Feb/2011:18:45:32 -0400] [Job 5] Connecting to printer...
D [21/Feb/2011:18:45:32 -0400] [Job 5] STATE: -connecting-to-device
D [21/Feb/2011:18:45:32 -0400] [Job 5] Connected to printer...
D [21/Feb/2011:18:45:32 -0400] [Job 5] Connected to 192.168.2.199:631 (IPv4)...
D [21/Feb/2011:18:45:32 -0400] [Job 5] Getting supported attributes...
D [21/Feb/2011:18:45:32 -0400] [Job 5] Set job-printer-state-message to "Destination printer does not exist!", current level=ERROR
D [21/Feb/2011:18:45:32 -0400] [Job 5] Backend returned status 4 (stop printer)
D [21/Feb/2011:18:45:32 -0400] [Job 5] Printer stopped due to backend errors; please consult the error_log file for details.
D [21/Feb/2011:18:45:32 -0400] [Job 5] End of messages
D [21/Feb/2011:18:45:32 -0400] [Job 5] printer-state=5(stopped)
D [21/Feb/2011:18:45:32 -0400] [Job 5] printer-state-message="Destination printer does not exist!"
D [21/Feb/2011:18:45:32 -0400] [Job 5] printer-state-reasons=paused
E [21/Feb/2011:18:46:05 -0400] Returning IPP client-error-not-possible for Cancel-Job (ipp://localhost/jobs/5) from localhost


---

### Post by fubar65 on 2011-02-22
even if someone could tell me the proper syntax for setting up my printers on ipp, socket, lpd, smb, etc I would be extremely grateful.

I actually have the laserjet working now using socket://192.168.2.199:9100/lpt1

when I add the deskjet, it gets added but the test page prints on the laserjet prints but it's many many pages of garbage..

---

### Post by fubar65 on 2011-02-24
okay, I have the laserjet working on the socket and the deskjet sort of works on ipp, however the deskjet thinks it is timing out and giving me an error on the desktop, yet the test print completed just fine..

does anyone have any input?

again, I don't know why lpr isn't an option on this laptop but so long as she can print that would be fine.

Thanks

---

