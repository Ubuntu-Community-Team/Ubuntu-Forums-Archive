---
title: "CUPS Cannot Print"
date: 2020-06-19
forum: Hardware
---

### Post by databoy2k on 2020-06-19
Hey All. I'm now up to Ubuntu 20.04, with CUPS 2.3.1 running. I have a Samsung SCX-4521f running on the Samsung Unified Drivers. Note that this exact setup just worked on 18.04, and I've purged cups. 

Here is my CUPS error log:
```
E [19/Jun/2020:07:02:21 -0600] [cups-driverd] Skipping \"/usr/share/ppd/uld-samsung\": loop detected!
W [19/Jun/2020:07:02:32 -0600] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id \'SCX_4521f-Gray..\' already exists
E [19/Jun/2020:07:02:37 -0600] [Job 1] Unable to open raster stream - : Broken pipe
E [19/Jun/2020:07:02:45 -0600] [Job 1] Job stopped due to filter errors; please consult the /var/log/cups/error_log file for details.
D [19/Jun/2020:07:02:45 -0600] [Job 1] The following messages were recorded from 07:02:36 AM to 07:02:45 AM
D [19/Jun/2020:07:02:45 -0600] [Job 1] Applying default options...
D [19/Jun/2020:07:02:45 -0600] [Job 1] Adding start banner page "none".
D [19/Jun/2020:07:02:45 -0600] [Job 1] Adding end banner page "none".
D [19/Jun/2020:07:02:45 -0600] [Job 1] File of type application/vnd.cups-pdf-banner queued by "server".
D [19/Jun/2020:07:02:45 -0600] [Job 1] hold_until=0
D [19/Jun/2020:07:02:45 -0600] [Job 1] Queued on "SCX_4521f" by "server".
D [19/Jun/2020:07:02:45 -0600] [Job 1] time-at-processing=1592571756
D [19/Jun/2020:07:02:45 -0600] [Job 1] 4 filters for job:
D [19/Jun/2020:07:02:45 -0600] [Job 1] bannertopdf (application/vnd.cups-pdf-banner to application/pdf, cost 32)
D [19/Jun/2020:07:02:45 -0600] [Job 1] pdftopdf (application/pdf to application/vnd.cups-pdf, cost 66)
D [19/Jun/2020:07:02:45 -0600] [Job 1] gstoraster (application/vnd.cups-pdf to application/vnd.cups-raster, cost 99)
D [19/Jun/2020:07:02:45 -0600] [Job 1] rastertospl (application/vnd.cups-raster to printer/SCX_4521f, cost 0)
D [19/Jun/2020:07:02:45 -0600] [Job 1] job-sheets=none,none
D [19/Jun/2020:07:02:45 -0600] [Job 1] argv[0]="SCX_4521f"
D [19/Jun/2020:07:02:45 -0600] [Job 1] argv[1]="1"
D [19/Jun/2020:07:02:45 -0600] [Job 1] argv[2]="server"
D [19/Jun/2020:07:02:45 -0600] [Job 1] argv[3]="Test Page"
D [19/Jun/2020:07:02:45 -0600] [Job 1] argv[4]="1"
D [19/Jun/2020:07:02:45 -0600] [Job 1] argv[5]="job-uuid=urn:uuid:2855d522-f9df-3aad-5b46-fe74f84519f5 job-originating-host-name=localhost date-time-at-creation= date-time-at-processing= time-at-creation=1592571756 time-at-processing=1592571756"
D [19/Jun/2020:07:02:45 -0600] [Job 1] argv[6]="/var/spool/cups/d00001-001"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[7]="CUPS_STATEDIR=/run/cups"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[8]="HOME=/var/spool/cups/tmp"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[10]="SERVER_ADMIN=root@WTM-Srv"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[11]="SOFTWARE=CUPS/2.3.1"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[13]="USER=root"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[14]="CUPS_MAX_MESSAGE=2047"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[15]="CUPS_SERVER=/run/cups/cups.sock"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[17]="IPP_PORT=631"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[18]="CHARSET=utf-8"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[19]="LANG=en_CA.UTF-8"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[20]="PPD=/etc/cups/ppd/SCX_4521f.ppd"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[21]="RIP_MAX_CACHE=128m"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[22]="CONTENT_TYPE=application/vnd.cups-pdf-banner"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[23]="DEVICE_URI=usb://Samsung/SCX-4x21%20Series?serial=9461BAJQA00284F.&interface=1"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[24]="PRINTER_INFO=Samsung SCX-4x21 Series"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[25]="PRINTER_LOCATION=Office"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[26]="PRINTER=SCX_4521f"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[27]="PRINTER_STATE_REASONS=none"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[28]="CUPS_FILETYPE=document"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[29]="FINAL_CONTENT_TYPE=application/vnd.cups-raster"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[30]="AUTH_I****"
D [19/Jun/2020:07:02:45 -0600] [Job 1] Started filter /usr/lib/cups/filter/bannertopdf (PID 9004)
D [19/Jun/2020:07:02:45 -0600] [Job 1] Started filter /usr/lib/cups/filter/pdftopdf (PID 9005)
D [19/Jun/2020:07:02:45 -0600] [Job 1] Started filter /usr/lib/cups/filter/gstoraster (PID 9006)
D [19/Jun/2020:07:02:45 -0600] [Job 1] Started filter /usr/lib/cups/filter/rastertospl (PID 9007)
D [19/Jun/2020:07:02:45 -0600] [Job 1] Started backend /usr/lib/cups/backend/usb (PID 9008)
D [19/Jun/2020:07:02:45 -0600] [Job 1] Loading USB quirks from \"/usr/share/cups/usb\".
D [19/Jun/2020:07:02:45 -0600] [Job 1] Loaded 95 quirks.
D [19/Jun/2020:07:02:45 -0600] [Job 1] Printing on printer with URI: usb://Samsung/SCX-4x21%20Series?serial=9461BAJQA00284F.&interface=1
D [19/Jun/2020:07:02:45 -0600] [Job 1] libusb_get_device_list=11
D [19/Jun/2020:07:02:45 -0600] [Job 1] STATE: +connecting-to-device
D [19/Jun/2020:07:02:45 -0600] [Job 1] STATE: -connecting-to-device
D [19/Jun/2020:07:02:45 -0600] [Job 1] Printer found with device ID: MFG:Samsung;CMD:GDI;MDL:SCX-4x21 Series;CLS:PRINTER;MODE:PCL,FAX;STATUS:IDLE;PCD:@SCX-4521F_VE; Device URI: usb://Samsung/SCX-4x21%20Series?serial=9461BAJQA00284F.&interface=1
D [19/Jun/2020:07:02:45 -0600] [Job 1] Device protocol: 2
D [19/Jun/2020:07:02:45 -0600] [Job 1] Sending data to printer.
D [19/Jun/2020:07:02:45 -0600] [Job 1] Set job-printer-state-message to "Sending data to printer.", current level=INFO
D [19/Jun/2020:07:02:45 -0600] [Job 1] SCX_4521f: error while loading shared libraries: libcupsimage.so.2: cannot open shared object file: No such file or directory
D [19/Jun/2020:07:02:45 -0600] [Job 1] Sent 0 bytes...
D [19/Jun/2020:07:02:45 -0600] [Job 1] PID 9007 (/usr/lib/cups/filter/rastertospl) stopped with status 127 (File too large)
D [19/Jun/2020:07:02:45 -0600] [Job 1] Hint: Try setting the LogLevel to "debug" to find out more.
D [19/Jun/2020:07:02:45 -0600] [Job 1] pdftopdf: Last filter determined by the PPD: rastertospl; FINAL_CONTENT_TYPE: application/vnd.cups-raster => pdftopdf will not log pages in page_log.
D [19/Jun/2020:07:02:45 -0600] [Job 1] OUTFORMAT=\"(null)\", so output format will be CUPS/PWG Raster
D [19/Jun/2020:07:02:45 -0600] [Job 1] PDF template file doesn\'t have form. It\'s okay.
D [19/Jun/2020:07:02:45 -0600] [Job 1] PID 9004 (/usr/lib/cups/filter/bannertopdf) exited with no errors.
D [19/Jun/2020:07:02:45 -0600] [Job 1] PDF interactive form and annotation flattening done via QPDF
D [19/Jun/2020:07:02:45 -0600] [Job 1] PID 9005 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [19/Jun/2020:07:02:45 -0600] [Job 1] Color Manager: Calibration Mode/Off
D [19/Jun/2020:07:02:45 -0600] [Job 1] Calling FindDeviceById(cups-SCX_4521f)
D [19/Jun/2020:07:02:45 -0600] [Job 1] Found device /org/freedesktop/ColorManager/devices/cups_SCX_4521f
D [19/Jun/2020:07:02:45 -0600] [Job 1] Calling org.freedesktop.ColorManager.Device.Get(ProfilingInhibitors)
D [19/Jun/2020:07:02:45 -0600] [Job 1] Calling FindDeviceById(cups-SCX_4521f)
D [19/Jun/2020:07:02:45 -0600] [Job 1] Found device /org/freedesktop/ColorManager/devices/cups_SCX_4521f
D [19/Jun/2020:07:02:45 -0600] [Job 1] Calling GetProfileForQualifiers(Gray.Off.600dpi...)
D [19/Jun/2020:07:02:45 -0600] [Job 1] Failed to send: org.freedesktop.ColorManager.Device.NothingMatched:nothing matched expression \'Gray.Off.600dpi,Gray.Off.*,Gray.*.600dpi,Gray.*.*,*\'
D [19/Jun/2020:07:02:45 -0600] [Job 1] Failed to get profile filename for cups-SCX_4521f
D [19/Jun/2020:07:02:45 -0600] [Job 1] Color Manager: no profiles specified in PPD
D [19/Jun/2020:07:02:45 -0600] [Job 1] Color Manager: ICC Profile: None
D [19/Jun/2020:07:02:45 -0600] [Job 1] Ghostscript using Any-Part-of-Pixel method to fill paths.
D [19/Jun/2020:07:02:45 -0600] [Job 1] Ghostscript command line: gs -dQUIET -dSAFER -dNOPAUSE -dBATCH -dNOINTERPOLATE -dNOMEDIAATTRS -dShowAcroForm -sstdout=%stderr -sOutputFile=%stdout -sDEVICE=cups -r600x600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dcupsBitsPerColor=8 -dcupsColorOrder=0 -dcupsColorSpace=0 -scupsPageSizeName=Letter -I/usr/share/cups/fonts -c \'<</.HWMargins[12.500000 12.500000 12.500000 12.500000] /Margins[0 0]>>setpagedevice\' -f -_
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[0]=\"CUPS_CACHEDIR=/var/cache/cups\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[1]=\"CUPS_DATADIR=/usr/share/cups\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[2]=\"CUPS_DOCROOT=/usr/share/cups/doc-root\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[3]=\"CUPS_FONTPATH=/usr/share/cups/fonts\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[4]=\"CUPS_REQUESTROOT=/var/spool/cups\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[5]=\"CUPS_SERVERBIN=/usr/lib/cups\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[6]=\"CUPS_SERVERROOT=/etc/cups\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[7]=\"CUPS_STATEDIR=/run/cups\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[8]=\"HOME=/var/spool/cups/tmp\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[9]=\"PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[10]=\"SERVER_ADMIN=root@WTM-Srv\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[11]=\"SOFTWARE=CUPS/2.3.1\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[12]=\"USER=root\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[13]=\"CUPS_MAX_MESSAGE=2047\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[14]=\"CUPS_SERVER=/run/cups/cups.sock\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[15]=\"CUPS_ENCRYPTION=IfRequested\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[16]=\"IPP_PORT=631\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[17]=\"CHARSET=utf-8\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[18]=\"LANG=en_CA.UTF-8\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[19]=\"PPD=/etc/cups/ppd/SCX_4521f.ppd\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[20]=\"RIP_MAX_CACHE=128m\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[21]=\"CONTENT_TYPE=application/vnd.cups-pdf-banner\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[22]=\"DEVICE_URI=usb://Samsung/SCX-4x21%20Series?serial=9461BAJQA00284F.&interface=1\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[23]=\"PRINTER_INFO=Samsung SCX-4x21 Series\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[24]=\"PRINTER_LOCATION=Office\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[25]=\"PRINTER=SCX_4521f\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[26]=\"PRINTER_STATE_REASONS=none\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[27]=\"CUPS_FILETYPE=document\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[28]=\"FINAL_CONTENT_TYPE=application/vnd.cups-raster\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] envp[29]=\"AUTH_INFO_REQUIRED=none\"
D [19/Jun/2020:07:02:45 -0600] [Job 1] Start rendering...
D [19/Jun/2020:07:02:45 -0600] [Job 1] Processing page 1...
D [19/Jun/2020:07:02:45 -0600] [Job 1] Waiting for read thread to exit...
D [19/Jun/2020:07:02:45 -0600] [Job 1] Error: /ioerror in --showpage--
D [19/Jun/2020:07:02:45 -0600] [Job 1] Operand stack:
D [19/Jun/2020:07:02:45 -0600] [Job 1] true   (/tmp/gs_3k1vIJ)   --nostringval--   1   true
D [19/Jun/2020:07:02:45 -0600] [Job 1] Execution stack:
D [19/Jun/2020:07:02:45 -0600] [Job 1] %interp_exit   .runexec2   --nostringval--   showpage   --nostringval--   2   %stopped_push   --nostringval--   showpage   showpage   false   1   %stopped_push   1990   2   3   %oparray_pop   1989   2   3   %oparray_pop   1977   2   3   %oparray_pop   showpage   1978   4   3   %oparray_pop   showpage   showpage   2   1   1   showpage   %for_pos_int_continue   1981   4   7   %oparray_pop   showpage   showpage   1840   3   9   %oparray_pop   showpage   showpage
D [19/Jun/2020:07:02:45 -0600] [Job 1] Dictionary stack:
D [19/Jun/2020:07:02:45 -0600] [Job 1] --dict:738/1123(ro)(G)--   --dict:1/20(G)--   --dict:80/200(L)--   --dict:80/200(L)--   --dict:135/256(ro)(G)--   --dict:315/325(ro)(G)--   --dict:33/64(L)--   --dict:6/9(L)--   --dict:7/20(L)--
D [19/Jun/2020:07:02:45 -0600] [Job 1] Current allocation mode is local
D [19/Jun/2020:07:02:45 -0600] [Job 1] Last OS error: Broken pipe
D [19/Jun/2020:07:02:45 -0600] [Job 1] GPL Ghostscript 9.50: Unrecoverable error, exit code 1
D [19/Jun/2020:07:02:45 -0600] [Job 1] Rendering completed
D [19/Jun/2020:07:02:45 -0600] [Job 1] PID 9006 (/usr/lib/cups/filter/gstoraster) stopped with status 1.
D [19/Jun/2020:07:02:45 -0600] [Job 1] Hint: Try setting the LogLevel to "debug" to find out more.
D [19/Jun/2020:07:02:45 -0600] [Job 1] Read thread still active, aborting the pending read...
D [19/Jun/2020:07:02:45 -0600] [Job 1] Resetting printer.
D [19/Jun/2020:07:02:45 -0600] [Job 1] PID 9008 (/usr/lib/cups/backend/usb) exited with no errors.
D [19/Jun/2020:07:02:45 -0600] [Job 1] End of messages
D [19/Jun/2020:07:02:45 -0600] [Job 1] printer-state=3(idle)
D [19/Jun/2020:07:02:45 -0600] [Job 1] printer-state-message="Rendering completed"
D [19/Jun/2020:07:02:45 -0600] [Job 1] printer-state-reasons=none

```

I see an issue with the shared library - is that my problem?

Troubleshooting tips greatly appreciated.

---

### Post by databoy2k on 2020-06-19
Solution: 

```
sudo apt install libcupsimage2
```

---

