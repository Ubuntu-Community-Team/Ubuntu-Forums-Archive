---
title: "cups rasterizes output on Brother printer"
date: 2018-11-05
forum: Hardware
---

### Post by mike-g2 on 2018-11-05
I have a Brother HL-4570CDW printer that often rasterizes text in PDF files, especially if they are on a page with a figure or two.  It does not do this from the same file if I print the PDF file directly from a usb key plugged into the printer.

I have purged and reinstalled the drivers using a script downloaded from Brother, linux-brprinter-installer-2.2.1-1, which downloaded and installed

   4570cdwlpr-1.1.1-5.i386.deb
   hl4570cdwcupswrapper-1.1.1-5.i386.deb

The packages install and I can print, but again the text is rasterized even though it looks perfect on the screen.
I believe this is a cups issue because if I print to a file, the text in the resulting file is similarly degraded (see attached).

I believe the relevant section from my /var/log/cups/error_log file is

```
D [05/Nov/2018:18:03:14 -0500] [Job 131] 3 filters for job:
D [05/Nov/2018:18:03:14 -0500] [Job 131] pdftopdf (application/pdf to application/vnd.cups-pdf, cost 66)
D [05/Nov/2018:18:03:14 -0500] [Job 131] pdftops (application/vnd.cups-pdf to application/vnd.cups-postscript, cost 100)
D [05/Nov/2018:18:03:14 -0500] [Job 131] brlpdwrapperhl4570cdw (application/vnd.cups-postscript to printer/HL4570CDW, cost 0)
D [05/Nov/2018:18:03:14 -0500] [Job 131] job-sheets=none,none
D [05/Nov/2018:18:03:14 -0500] [Job 131] argv[0]="HL4570CDW"
D [05/Nov/2018:18:03:14 -0500] [Job 131] argv[1]="131"
D [05/Nov/2018:18:03:14 -0500] [Job 131] argv[2]="mikeg"
D [05/Nov/2018:18:03:14 -0500] [Job 131] argv[3]="original.pdf"
D [05/Nov/2018:18:03:14 -0500] [Job 131] argv[4]="1"
D [05/Nov/2018:18:03:14 -0500] [Job 131] argv[5]="BRSkipBlank=OFF BREnhanceBlkPrt=OFF BRMonoColor=Auto BRInputSlot=AutoSelect number-up=1 BRDuplex=DuplexNoTumble noCollate PageSize=Letter BRColorMatching=None BRReverse=OFF BRBlue=0 BRContrast=0 BRBrightness=0 BRMediaType=Plain BRGreen=0 BRSaturation=0 BRImproveOutput=OFF BRResolution=600dpi BRGray=ON BRRed=0 BRTonerSaveMode=OFF job-uuid=urn:uuid:a7354681-f655-316e-5a6a-e30f9355f498 job-originating-host-name=localhost date-time-at-creation= date-time-at-processing= time-at-creation=1541458994 time-at-processing=1541458994"
D [05/Nov/2018:18:03:14 -0500] [Job 131] argv[6]="/var/spool/cups/d00131-001"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[7]="CUPS_STATEDIR=/run/cups"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[8]="HOME=/var/spool/cups/tmp"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[10]="SERVER_ADMIN=root@elkmont"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[11]="SOFTWARE=CUPS/2.2.7"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[13]="USER=root"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[14]="CUPS_MAX_MESSAGE=2047"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[17]="IPP_PORT=631"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[18]="CHARSET=utf-8"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[19]="LANG=en_US.UTF-8"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[20]="PPD=/etc/cups/ppd/HL4570CDW.ppd"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[21]="RIP_MAX_CACHE=128m"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[22]="CONTENT_TYPE=application/pdf"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[23]="DEVICE_URI=usb://Brother/HL-4570CDW%20series?serial=U62500M0J147352"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[24]="PRINTER_INFO=HL4570CDW"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[25]="PRINTER_LOCATION="
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[26]="PRINTER=HL4570CDW"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[27]="PRINTER_STATE_REASONS=none"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[28]="CUPS_FILETYPE=document"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[29]="FINAL_CONTENT_TYPE=application/vnd.cups-postscript"
D [05/Nov/2018:18:03:14 -0500] [Job 131] envp[30]="AUTH_I****"
I [05/Nov/2018:18:03:14 -0500] [Job 131] Started filter /usr/lib/cups/filter/pdftopdf (PID 15336)
I [05/Nov/2018:18:03:14 -0500] [Job 131] Started filter /usr/lib/cups/filter/pdftops (PID 15337)
I [05/Nov/2018:18:03:14 -0500] [Job 131] Started filter /usr/lib/cups/filter/brlpdwrapperhl4570cdw (PID 15338)
I [05/Nov/2018:18:03:14 -0500] [Job 131] Started backend /usr/lib/cups/backend/usb (PID 15339)
D [05/Nov/2018:18:03:14 -0500] cupsdMarkDirty(----S)
D [05/Nov/2018:18:03:14 -0500] cupsdSetBusyState: newbusy="Active clients, printing jobs, and dirty files", busy="Active clients and dirty files"
D [05/Nov/2018:18:03:14 -0500] [Client 85] Returning IPP successful-ok for Print-Job (ipp://localhost:631/printers/HL4570CDW) from localhost
D [05/Nov/2018:18:03:14 -0500] [Client 85] Content-Length: 193
D [05/Nov/2018:18:03:14 -0500] [Client 85] cupsdSendHeader: code=200, type="application/ipp", auth_type=0
D [05/Nov/2018:18:03:14 -0500] [Client 85] con->http=0x563f7fe9f030
D [05/Nov/2018:18:03:14 -0500] [Client 85] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=193, response=0x563f7fe91910(IPP_STATE_IDLE), pipe_pid=0, file=-1
D [05/Nov/2018:18:03:14 -0500] [Client 85] Writing IPP response, ipp_state=IPP_STATE_DATA, old wused=0, new wused=0
D [05/Nov/2018:18:03:14 -0500] [Client 85] bytes=0, http_state=0, data_remaining=193

```
I've also attached a fuller version.

If someone could help me trouble shoot this, I'd be very grateful.

Mike

---

### Post by him610 on 2018-11-06
Please show the results of ...
```
dpkg -l | grep Brother
```

---

### Post by mike-g2 on 2018-11-06
I get,
```

[elkmont ~/Current/(3)/Readings]$ dpkg -l |grep Brother                                                      
ii  hl4570cdwcupswrapper:i386                                        1.1.1-5                                     i386         Brother CUPS Laser Printer Definitions
ii  hl4570cdwlpr:i386                                                1.1.1-5                                     i386         Brother lpr Laser Printer Definitions
ii  printer-driver-brlaser                                           4-1                                         amd64        printer driver for (some) Brother laser printers
ii  printer-driver-ptouch                                            1.4.2-3                                     amd64        printer driver Brother P-touch label printers

```

I spent a while today trying to see if it was related to gs rastering things due to 'transparent' layers in the pdf, but removing those layers didn't solve the problem.

---

### Post by him610 on 2018-11-08
Just a thought, if you go into Settings > Printers > Printer Options, what Resolution do you have selected? On mine, a Brother MFC-7360n, it is set to 600 dpi (default.) I have never experienced any issues with rasterization. 

I can not even compare my error log with yours - mine has no errors. Other than that, I am out of ideas.

---

### Post by mike-g2 on 2018-11-08
Note that cups' 'error_log' is actually just a log.  It resides in /var/log/cups and is generally off by default.  You can activate it  with the command
     cupsctl LogLevel=debug

Regarding my printer settings, I've gone from 600dpi to 2400dpi (really 2400x600) and see little improvement.

I appreciate your attempts to help.

---

### Post by mike-g2 on 2018-11-09
I have spent a fair amount of time trying to fix this.  My best solution so far is to add the following line to the printer's .ppd file
```

*DefaultResolution: 2400dpi

```

and then use the options
```

 lpr -o pdftops-renderer=gs  <FILE.PDF>

```

---

