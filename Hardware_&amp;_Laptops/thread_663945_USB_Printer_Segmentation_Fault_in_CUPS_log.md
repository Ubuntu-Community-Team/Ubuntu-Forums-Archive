---
title: "USB Printer: Segmentation Fault in CUPS log"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by lwi on 2008-01-10
I have a Brother PT-9500PC label printer that I'm trying to get to work with linux.  I'm using the drivers provided by Brother.  The printer is installed and correctly detected by CUPS, i can see it in localhost:631, everything *looks* fine.

But when I try to print anything, nothing happens.  I put the LogLevel et 'debug' in cupsd.conf and here is what I get for a single job:

```


D [10/Jan/2008:16:35:56 -0500] cupsdAcceptClient: 8 from localhost (Domain)
D [10/Jan/2008:16:35:56 -0500] cupsdReadClient: 8 POST / HTTP/1.1
D [10/Jan/2008:16:35:56 -0500] cupsdAuthorize: No authentication data provided.
D [10/Jan/2008:16:35:56 -0500] CUPS-Get-Default
D [10/Jan/2008:16:35:56 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [10/Jan/2008:16:35:56 -0500] cupsdAcceptClient: 10 from localhost (Domain)
D [10/Jan/2008:16:35:56 -0500] cupsdCloseClient: 8
D [10/Jan/2008:16:35:56 -0500] cupsdReadClient: 10 POST / HTTP/1.1
D [10/Jan/2008:16:35:56 -0500] cupsdAuthorize: No authentication data provided.
D [10/Jan/2008:16:35:56 -0500] CUPS-Get-Printers
D [10/Jan/2008:16:35:56 -0500] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)
D [10/Jan/2008:16:35:56 -0500] cupsdAcceptClient: 8 from localhost:631 (IPv4)
D [10/Jan/2008:16:35:56 -0500] cupsdCloseClient: 10
D [10/Jan/2008:16:35:56 -0500] cupsdReadClient: 8 GET /printers/PT-9500PC.ppd HTTP/1.1
D [10/Jan/2008:16:35:56 -0500] cupsdAuthorize: No authentication data provided.
D [10/Jan/2008:16:35:57 -0500] cupsdCloseClient: 8
D [10/Jan/2008:16:35:59 -0500] cupsdAcceptClient: 8 from localhost (Domain)
D [10/Jan/2008:16:36:01 -0500] Closing client 7 after 300 seconds of inactivity...
D [10/Jan/2008:16:36:01 -0500] cupsdCloseClient: 7
D [10/Jan/2008:16:36:02 -0500] cupsdReadClient: 8 POST /printers/PT-9500PC HTTP/1.1
D [10/Jan/2008:16:36:02 -0500] cupsdAuthorize: No authentication data provided.
D [10/Jan/2008:16:36:02 -0500] Print-Job ipp://localhost:631/printers/PT-9500PC
D [10/Jan/2008:16:36:02 -0500] print_job: auto-typing file...
D [10/Jan/2008:16:36:02 -0500] add_job: requesting-user-name="zack"
I [10/Jan/2008:16:36:02 -0500] [Job 13] Adding start banner page "none".
D [10/Jan/2008:16:36:02 -0500] Discarding unused job-created event...
I [10/Jan/2008:16:36:02 -0500] [Job 13] Adding job file of type application/postscript.
I [10/Jan/2008:16:36:02 -0500] [Job 13] Adding end banner page "none".
I [10/Jan/2008:16:36:02 -0500] [Job 13] Queued on "PT-9500PC" by "zack".
D [10/Jan/2008:16:36:02 -0500] [Job 13] hold_until = 0
D [10/Jan/2008:16:36:02 -0500] Discarding unused printer-state-changed event...
D [10/Jan/2008:16:36:02 -0500] [Job 13] job-sheets=none,none
D [10/Jan/2008:16:36:02 -0500] [Job 13] banner_page = 0
D [10/Jan/2008:16:36:02 -0500] [Job 13] argv[0]="PT-9500PC"
D [10/Jan/2008:16:36:02 -0500] [Job 13] argv[1]="13"
D [10/Jan/2008:16:36:02 -0500] [Job 13] argv[2]="zack"
D [10/Jan/2008:16:36:02 -0500] [Job 13] argv[3]="evince-print"
D [10/Jan/2008:16:36:02 -0500] [Job 13] argv[4]="1"
D [10/Jan/2008:16:36:02 -0500] [Job 13] argv[5]="BrBrightness=0 PageSize=Letter BrChain=OFF BrHalftonePattern=ErrorDiffusion BrAutoTapeCut=OFF BrMirror=OFF BrHalfCut=ON BrMargin=1 number-up=1 BrContrast=0 job-uuid=urn:uuid:8a9068a3-a3f3-3eff-6564-137e463c72d1"
D [10/Jan/2008:16:36:02 -0500] [Job 13] argv[6]="/var/spool/cups/d00013-001"
D [10/Jan/2008:16:36:02 -0500] [Job 13] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [10/Jan/2008:16:36:02 -0500] [Job 13] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [10/Jan/2008:16:36:02 -0500] [Job 13] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [10/Jan/2008:16:36:02 -0500] [Job 13] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [10/Jan/2008:16:36:02 -0500] [Job 13] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [10/Jan/2008:16:36:02 -0500] [Job 13] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [10/Jan/2008:16:36:02 -0500] [Job 13] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [10/Jan/2008:16:36:02 -0500] [Job 13] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [10/Jan/2008:16:36:02 -0500] [Job 13] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [10/Jan/2008:16:36:02 -0500] [Job 13] envp[9]="SERVER_ADMIN=root@zit"
D [10/Jan/2008:16:36:02 -0500] [Job 13] envp[10]="SOFTWARE=CUPS/1.3.2"
D [10/Jan/2008:16:36:02 -0500] [Job 13] envp[11]="TMPDIR=/var/spool/cups/tmp"
D [10/Jan/2008:16:36:02 -0500] [Job 13] envp[12]="TZ=America/Montreal"
D [10/Jan/2008:16:36:02 -0500] [Job 13] envp[13]="USER=root"
D [10/Jan/2008:16:36:02 -0500] [Job 13] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [10/Jan/2008:16:36:02 -0500] [Job 13] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [10/Jan/2008:16:36:02 -0500] [Job 13] envp[16]="IPP_PORT=631"
D [10/Jan/2008:16:36:02 -0500] [Job 13] envp[17]="CHARSET=utf-8"
D [10/Jan/2008:16:36:02 -0500] [Job 13] envp[18]="LANG=en_CA"
D [10/Jan/2008:16:36:02 -0500] [Job 13] envp[19]="PPD=/etc/cups/ppd/PT-9500PC.ppd"
D [10/Jan/2008:16:36:02 -0500] [Job 13] envp[20]="RIP_MAX_CACHE=8m"
D [10/Jan/2008:16:36:02 -0500] [Job 13] envp[21]="CONTENT_TYPE=application/postscript"
D [10/Jan/2008:16:36:02 -0500] [Job 13] envp[22]="DEVICE_URI=brusb_pt9500pc:/dev/usb"
D [10/Jan/2008:16:36:02 -0500] [Job 13] envp[23]="PRINTER=PT-9500PC"
D [10/Jan/2008:16:36:02 -0500] [Job 13] envp[24]="FINAL_CONTENT_TYPE=printer/PT-9500PC"
I [10/Jan/2008:16:36:02 -0500] [Job 13] Started filter /usr/lib/cups/filter/pstops (PID 11916)
I [10/Jan/2008:16:36:02 -0500] [Job 13] Started filter /usr/lib/cups/filter/brlpdwrapperpt9500pc (PID 11917)
I [10/Jan/2008:16:36:02 -0500] [Job 13] Started backend /usr/lib/cups/backend/brusb_pt9500pc (PID 11918)
D [10/Jan/2008:16:36:02 -0500] Discarding unused job-state event...
D [10/Jan/2008:16:36:02 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [10/Jan/2008:16:36:02 -0500] [Job 13] Page = 77x283; 0,3 to 77,280
D [10/Jan/2008:16:36:02 -0500] [Job 13] slow_collate=0, slow_duplex=0, slow_order=0
D [10/Jan/2008:16:36:02 -0500] [Job 13] Before copy_comments - %!PS-Adobe-3.0
D [10/Jan/2008:16:36:02 -0500] [Job 13] %!PS-Adobe-3.0
D [10/Jan/2008:16:36:02 -0500] [Job 13] %%Creator: cairo 1.4.10 (http://cairographics.org)
D [10/Jan/2008:16:36:02 -0500] [Job 13] %%CreationDate: Thu Jan 10 16:35:59 2008
D [10/Jan/2008:16:36:02 -0500] [Job 13] %%Pages: 1
D [10/Jan/2008:16:36:02 -0500] [Job 13] %%BoundingBox: 0 0 612 792
D [10/Jan/2008:16:36:02 -0500] [Job 13] %%DocumentData: Clean7Bit
D [10/Jan/2008:16:36:02 -0500] [Job 13] %%LanguageLevel: 2
D [10/Jan/2008:16:36:02 -0500] [Job 13] %%EndComments
D [10/Jan/2008:16:36:02 -0500] [Job 13] Before copy_prolog - %%BeginProlog
D [10/Jan/2008:16:36:02 -0500] [Job 13] Before copy_setup - % _cairo_ps_surface_emit_font_subsets
D [10/Jan/2008:16:36:02 -0500] [Job 13] Before page loop - %%Page: 1 1
D [10/Jan/2008:16:36:02 -0500] [Job 13] Copying page 1...
D [10/Jan/2008:16:36:02 -0500] [Job 13] pagew = 76.8, pagel = 277.6
D [10/Jan/2008:16:36:02 -0500] [Job 13] bboxw = 76, bboxl = 283
D [10/Jan/2008:16:36:02 -0500] [Job 13] PageLeft = 0.0, PageRight = 76.8
D [10/Jan/2008:16:36:02 -0500] [Job 13] PageTop = 280.5, PageBottom = 2.9
D [10/Jan/2008:16:36:02 -0500] [Job 13] PageWidth = 76.8, PageLength = 283.4
D [10/Jan/2008:16:36:02 -0500] [Job 13] Wrote 1 pages...
D [10/Jan/2008:16:36:02 -0500] PID 11916 (/usr/lib/cups/filter/pstops) exited with no errors.
D [10/Jan/2008:16:36:02 -0500] cupsdCloseClient: 8
D [10/Jan/2008:16:36:02 -0500] cupsdAcceptClient: 7 from localhost (Domain)
D [10/Jan/2008:16:36:02 -0500] cupsdReadClient: 7 POST / HTTP/1.1
D [10/Jan/2008:16:36:02 -0500] cupsdAuthorize: No authentication data provided.
D [10/Jan/2008:16:36:02 -0500] Get-Jobs ipp://localhost/jobs/
D [10/Jan/2008:16:36:02 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [10/Jan/2008:16:36:02 -0500] cupsdReadClient: 7 POST / HTTP/1.1
D [10/Jan/2008:16:36:02 -0500] cupsdAuthorize: No authentication data provided.
D [10/Jan/2008:16:36:02 -0500] CUPS-Get-Printers
D [10/Jan/2008:16:36:02 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [10/Jan/2008:16:36:02 -0500] cupsdCloseClient: 7
**_D [10/Jan/2008:16:36:02 -0500] [Job 13] Segmentation fault (core dumped)_**
E [10/Jan/2008:16:36:02 -0500] [Job 13] Empty print file!
D [10/Jan/2008:16:36:02 -0500] Discarding unused printer-state-changed event...
D [10/Jan/2008:16:36:03 -0500] cupsdAcceptClient: 7 from localhost (Domain)
D [10/Jan/2008:16:36:03 -0500] cupsdReadClient: 7 POST / HTTP/1.1
D [10/Jan/2008:16:36:03 -0500] cupsdAuthorize: No authentication data provided.
D [10/Jan/2008:16:36:03 -0500] Get-Jobs ipp://localhost/jobs/
D [10/Jan/2008:16:36:03 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [10/Jan/2008:16:36:03 -0500] cupsdReadClient: 7 POST / HTTP/1.1
D [10/Jan/2008:16:36:03 -0500] cupsdAuthorize: No authentication data provided.
D [10/Jan/2008:16:36:03 -0500] CUPS-Get-Printers
D [10/Jan/2008:16:36:03 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [10/Jan/2008:16:36:03 -0500] cupsdCloseClient: 7
E [10/Jan/2008:16:36:03 -0500] [Job 13] No pages found!
D [10/Jan/2008:16:36:03 -0500] Discarding unused printer-state-changed event...
D [10/Jan/2008:16:36:03 -0500] PID 11917 (/usr/lib/cups/filter/brlpdwrapperpt9500pc) exited with no errors.
D [10/Jan/2008:16:36:04 -0500] cupsdAcceptClient: 7 from localhost (Domain)
D [10/Jan/2008:16:36:04 -0500] cupsdReadClient: 7 POST / HTTP/1.1
D [10/Jan/2008:16:36:04 -0500] cupsdAuthorize: No authentication data provided.
D [10/Jan/2008:16:36:04 -0500] Get-Jobs ipp://localhost/jobs/
D [10/Jan/2008:16:36:04 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [10/Jan/2008:16:36:04 -0500] cupsdReadClient: 7 POST / HTTP/1.1
D [10/Jan/2008:16:36:04 -0500] cupsdAuthorize: No authentication data provided.
D [10/Jan/2008:16:36:04 -0500] CUPS-Get-Printers
D [10/Jan/2008:16:36:04 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [10/Jan/2008:16:36:04 -0500] cupsdCloseClient: 7
D [10/Jan/2008:16:36:04 -0500] PID 11918 (/usr/lib/cups/backend/brusb_pt9500pc) exited with no errors.
D [10/Jan/2008:16:36:04 -0500] [Job 13] File 0 is complete.
I [10/Jan/2008:16:36:04 -0500] [Job 13] Completed successfully.
D [10/Jan/2008:16:36:04 -0500] Discarding unused printer-state-changed event...
D [10/Jan/2008:16:36:04 -0500] Discarding unused job-completed event...
D [10/Jan/2008:16:36:05 -0500] cupsdAcceptClient: 7 from localhost (Domain)
D [10/Jan/2008:16:36:05 -0500] [Job 13] Unloading...
D [10/Jan/2008:16:36:05 -0500] cupsdReadClient: 7 POST / HTTP/1.1
D [10/Jan/2008:16:36:05 -0500] cupsdAuthorize: No authentication data provided.
D [10/Jan/2008:16:36:05 -0500] Get-Jobs ipp://localhost/jobs/
D [10/Jan/2008:16:36:05 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [10/Jan/2008:16:36:05 -0500] cupsdReadClient: 7 POST / HTTP/1.1
D [10/Jan/2008:16:36:05 -0500] cupsdAuthorize: No authentication data provided.
D [10/Jan/2008:16:36:05 -0500] CUPS-Get-Printers
D [10/Jan/2008:16:36:05 -0500] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [10/Jan/2008:16:36:05 -0500] cupsdCloseClient: 7



```


as you can see in bold, there is a segmentation fault occuring in the process, but I have no idea what does it.

help me forum! you're my only hope!

Lwi

---

### Post by lwi on 2008-01-11
sorry to do this, but i really need to *bump*

---

