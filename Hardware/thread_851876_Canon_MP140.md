---
title: "Canon MP140"
date: 2008-07-07
forum: Hardware
---

### Post by Eijin on 2008-07-07
Hi all, i need to install my Canon MP140 anyone can tell my how i can do this?:(

---

### Post by abhilashkumar on 2008-07-07
> **Eijin said:**
> Hi all, i need to install my Canon MP140 anyone can tell my how i can do this?:(

TRY THIS

1. install alien Symaptic Package Managerunder System, Administration.
2. Go to [HTTP://www.canon.com](HTTP://www.canon.com), Support and get the 4 required Linux Drivers. cuijfilter common and cuijfilter MP140 series, scangearmp common and scangearmp 140 series drivers. Download them to your desktop. Get the .rpm version only for this to work.
3. These files are in the .rpm format and they need to be converted to .deb.
4. use the terminal window. cd ~/Desktop. That will put you in the desktop.
5. Convert the files to .deb by using sudo alien --scripts scangearmp-common-1.10-1.i386.rpm and sudo alien --scripts cuijfilter-common-2.80-0.i386.rpm. These are only examples and you need to be exact or it will not work.
6. Double Click the .deb files and they will be installed. Install the common files first then the 140 series next.
7. Reboot the computer and the scanner will show up in the GIMP Image Editor, File, Qcquire, Scangearmp.
8. You then need to go to System, Administration, Printing and configure the MP 145. It is called the MP 140 series and Make and model is a Canon PIXMA MP150 CUPS ..........

---

### Post by Eijin on 2008-07-07
Can you give me some direct link of the files i need? Because i can't find themç_ç

---

### Post by abhilashkumar on 2008-07-07
> **Eijin said:**
> Can you give me some direct link of the files i need? Because i can't find themç_ç

[http://support-asia.canon-asia.com/EN/search?v%3aproject=AZZ-EN&binning-state=model%3d%3dPIXMA%20MP145%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&](http://support-asia.canon-asia.com/EN/search?v%3aproject=AZZ-EN&binning-state=model%3d%3dPIXMA%20MP145%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&)

---

### Post by Eijin on 2008-07-07
After i've installe the 4 drivers...i try to print the test page, but the system returns this error: «client-error-document-format-not-supported».
How can i resolve this?

---

### Post by abhilashkumar on 2008-07-08
My test page printed just fine. Try printing from within an application like Openoffice writer of similar and see if you still get the error. If CUPS cant resolve the document type then maybe the application will have the filter for it.

[See this link]("http://www.linux.com/base/ldp/howto/Debian-and-Windows-Shared-Printing/getting_started.html")

---

### Post by Eijin on 2008-07-08
Thank you a lot i resolved my problem:guitar:

---

### Post by Ickam on 2009-03-01
I've tried these drivers but it didn't work. My system is 64-bit but I used ```
--force-architecture
``` and it seemed to be installed but didn't work though. I keep getting
```
client-error-document-format-not-supported.
``` and I don't know what to do. I want this printer to be local so what's the point?
Any ideas?

---

### Post by danellisuk on 2009-06-04
:D *Thanks to abhilashkumar for his instructions.  This is how I installed the MP140 on Ubuntu 9.04 (x86).*

Go to [http://software.canon-europe.com/products/0010525.asp]("http://software.canon-europe.com/products/0010525.asp")

Then select Linux from the dropdown and click submit.  Download the following two files:-

[LIST]
[*]Printer Driver for Linux (debian) (2.80)
[*]ScanGear MP for Linux (2.80)
[/LIST]

**_Printer_**
My first attempt failed because a dependency was not met.  I do not know why the dependency was not automatically installed, but all I had to do to get it working was to run the following command in a terminal window (and I entered my password when prompted):

```
sudo apt-get install libcupsys2
```

Then I got the printer installed by opening the **MP140_debian.tar** file.  Then installed the following two files by double clicking on them, then clicking **Install Package**:-

[LIST=1]
[*]cnijfilter-common_2.80-1_i386.deb
[*]cnijfilter-mp140series_2.80-1_i386.deb
[/LIST]

Then I restarted the computer.  After the computer had restarted the printer appeared in ***System -> Administration -> Printing***.  I printed a test page by right clicking on the **MP140-series** printer and selecting **Properties**, then clicking **Print Test Page**.

**_Scanner_**
Installing the scanner portion was a little more tricky because the .deb files seemed to be corrupt. This is what happened when I tried to install the .deb file:-

```
sudo dpkg -i scangearmp-common_1.10-1_i386.deb 
dpkg-deb: `scangearmp-common_1.10-1_i386.deb' is not a debian format archive
```

So I used abhilashkumar's recommendation of converting the rpm files using alien.  This worked. For convenience I have uploaded the deb files that were created to my site:-

[scangearmp-common_1.10-2_i386.deb]("http://www.danellis.co.uk/downloads/scangearmp-common_1.10-2_i386.deb")
[scangearmp-mp140series_1.10-2_i386.deb]("http://www.danellis.co.uk/downloads/scangearmp-mp140series_1.10-2_i386.deb")

I installed these the same way as I installed the printer deb files (note that you must install them in the order shown just above).  Then I restarted the machine.

To test the scanner I opened xsane from *Applications -> Graphics -> XSane Image scanning program*.  I was able to scan by clicking **Acquire Preview**, then finally the **Scan** button.

I then installed **Scanner Utility** via **Add/Remove Applications** which I found to be a much simpler interface for scanning.

This worked very well, and for me this has been the easiest Canon printer to get working, but I would still buy HP for Linux support!

---

### Post by bizmeds on 2009-06-21
Yes, I have Jaunty 9.04 netbook install I followed the advice downloaded and installed the drivers, installed scanner but when i tried to print a have an error pstocanonij write error, 32.

Is this a corrupt driver?

---

### Post by bizmeds on 2009-06-22
Hello, I have failed the printer test. Below, is the documentation

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest MP140-series (default)>,
 'cups_instance': None,
 'cups_queue': 'MP140-series',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Canon/MP140%20series',
                       'printer-info': u'Canon MP140 series',
                       'printer-is-shared': True,
                       'printer-location': u'paul',
                       'printer-make-and-model': u'Canon MP140 series Ver.2.80',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167948,
                       'printer-uri-supported': u'ipp://localhost:631/printers/MP140-series'},
 'cups_printer_remote': False,
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'ColorModel': u'rgb',
                                            u'InputSlot': u'asf',
                                            u'MediaType': u'plain',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'Resolution': u'600'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:Canon;CMD:BJL,BJRaster3,BSCCe,PLI;SOJ:TXT01;MDL:MP140 series;CLS:PRINTER;DES:Canon MP140 series;VER:1.04;STA:10;HRI:PAM;F\x01',
                      'device-info': u'Canon MP140 series USB #1',
                      'device-make-and-model': u'Canon MP140 series'}}
Page 7 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '1',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '1',
                          '_share_printers': '1',
                          '_user_cancel_any': '1'},
 'error_log_checkpoint': 269274L}
Page 8 (Print test page):
{'test_page_attempted': '22/Jun/2009:09:49:31 +0000',
 'test_page_completions': [(6, u'Job completed.')],
 'test_page_job_id': [6],
 'test_page_job_status': [(True,
                           6,
                           'MP140-series',
                           'Test Page',
                           'Completed',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 6,
                            'job-k-octets': 17,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/6',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'paul',
                            'job-preserved': False,
                            'job-printer-state-message': u'',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1245682182,
                            'job-printer-uri': u'ipp://paul:631/printers/MP140-series',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 9,
                            'job-state-reasons': u'job-completed-successfully',
                            'job-uri': u'ipp://localhost:631/jobs/6',
                            'job-uuid': u'urn:uuid:b5c102bb-9a3a-36e8-6198-48f80bdd6237',
                            'printer-uri': u'ipp://localhost/printers/MP140-series',
                            'time-at-completed': 1245682174,
                            'time-at-creation': 1245682171,
                            'time-at-processing': 1245682171})],
 'test_page_successful': False}
Page 9 (Error log fetch):
{'error_log': ['D [22/Jun/2009:09:49:21 -0500] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [22/Jun/2009:09:49:21 -0500] cupsdAuthorize: No authentication data provided.',
               'D [22/Jun/2009:09:49:21 -0500] Get-Jobs ipp://localhost/printers/',
               'D [22/Jun/2009:09:49:21 -0500] cupsdProcessIPPRequest: 16 status_code=0 (successful-ok)',
               'D [22/Jun/2009:09:49:21 -0500] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [22/Jun/2009:09:49:21 -0500] cupsdAuthorize: No authentication data provided.',
               'D [22/Jun/2009:09:49:21 -0500] Get-Jobs ipp://localhost/printers/',
               'D [22/Jun/2009:09:49:21 -0500] [Job 2] Loading attributes...',
               'D [22/Jun/2009:09:49:21 -0500] [Job 3] Loading attributes...',
               'D [22/Jun/2009:09:49:21 -0500] [Job 4] Loading attributes...',
               'D [22/Jun/2009:09:49:21 -0500] [Job 5] Loading attributes...',
               'D [22/Jun/2009:09:49:21 -0500] cupsdProcessIPPRequest: 16 status_code=0 (successful-ok)',
               'D [22/Jun/2009:09:49:21 -0500] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [22/Jun/2009:09:49:21 -0500] cupsdAuthorize: No authentication data provided.',
               'D [22/Jun/2009:09:49:21 -0500] Create-Printer-Subscription /',
               'D [22/Jun/2009:09:49:21 -0500] cupsdCreateSubscription(con=0xb9a40f00(16), uri="/")',
               'D [22/Jun/2009:09:49:21 -0500] pullmethod="ippget"',
               'D [22/Jun/2009:09:49:21 -0500] notify-lease-duration=86400',
               'D [22/Jun/2009:09:49:21 -0500] notify-time-interval=0',
               'D [22/Jun/2009:09:49:21 -0500] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [22/Jun/2009:09:49:21 -0500] Added subscription 12 for server',
               'I [22/Jun/2009:09:49:21 -0500] Saving subscriptions.conf...',
               'D [22/Jun/2009:09:49:21 -0500] cupsdProcessIPPRequest: 16 status_code=0 (successful-ok)',
               'D [22/Jun/2009:09:49:22 -0500] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [22/Jun/2009:09:49:22 -0500] cupsdAuthorize: No authentication data provided.',
               'D [22/Jun/2009:09:49:22 -0500] Get-Notifications /',
               'D [22/Jun/2009:09:49:22 -0500] cupsdIsAuthorized: requesting-user-name="paul"',
               'D [22/Jun/2009:09:49:22 -0500] cupsdProcessIPPRequest: 16 status_code=0 (successful-ok)',
               'D [22/Jun/2009:09:49:31 -0500] cupsdNetIFUpdate: "lo" = localhost:631',
               'D [22/Jun/2009:09:49:31 -0500] cupsdNetIFUpdate: "eth0" = 192.168.1.33:631',
               'D [22/Jun/2009:09:49:31 -0500] cupsdNetIFUpdate: "lo" = localhost:631',
               'D [22/Jun/2009:09:49:31 -0500] cupsdNetIFUpdate: "eth0" = fe80::221:85ff:fe48:a76c%eth0:631',
               'D [22/Jun/2009:09:49:31 -0500] Report: clients=7',
               'D [22/Jun/2009:09:49:31 -0500] Report: jobs=4',
               'D [22/Jun/2009:09:49:31 -0500] Report: jobs-active=0',
               'D [22/Jun/2009:09:49:31 -0500] Report: printers=2',
               'D [22/Jun/2009:09:49:31 -0500] Report: printers-implicit=0',
               'D [22/Jun/2009:09:49:31 -0500] Report: stringpool-string-count=1649',
               'D [22/Jun/2009:09:49:31 -0500] Report: stringpool-alloc-bytes=9064',
               'D [22/Jun/2009:09:49:31 -0500] Report: stringpool-total-bytes=34136',
               'D [22/Jun/2009:09:49:31 -0500] cupsdAcceptClient: 23 from localhost (Domain)',
               'D [22/Jun/2009:09:49:31 -0500] cupsdReadClient: 23 POST /printers/MP140-series HTTP/1.1',
               'D [22/Jun/2009:09:49:31 -0500] cupsdAuthorize: No authentication data provided.',
               'D [22/Jun/2009:09:49:31 -0500] Print-Job ipp://localhost/printers/MP140-series',
               'D [22/Jun/2009:09:49:31 -0500] [Job ???] Auto-typing file...',
               'I [22/Jun/2009:09:49:31 -0500] [Job ???] Request file type is application/postscript.',
               'D [22/Jun/2009:09:49:31 -0500] add_job: requesting-user-name="paul"',
               'D [22/Jun/2009:09:49:31 -0500] Adding default job-sheets values "none,none"...',
               'I [22/Jun/2009:09:49:31 -0500] [Job 6] Adding start banner page "none".',
               'I [22/Jun/2009:09:49:31 -0500] Saving subscriptions.conf...',
               'I [22/Jun/2009:09:49:31 -0500] [Job 6] Adding end banner page "none".',
               'I [22/Jun/2009:09:49:31 -0500] [Job 6] File of type application/postscript queued by "paul".',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] hold_until=0',
               'I [22/Jun/2009:09:49:31 -0500] [Job 6] Queued on "MP140-series" by "paul".',
               'I [22/Jun/2009:09:49:31 -0500] Saving subscriptions.conf...',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] job-sheets=none,none',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] banner_page = 0',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] argv[0]="MP140-series"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] argv[1]="6"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] argv[2]="paul"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] argv[3]="Test Page"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] argv[4]="1"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] argv[5]="job-uuid=urn:uuid:b5c102bb-9a3a-36e8-6198-48f80bdd6237"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] argv[6]="/var/spool/cups/d00006-001"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] envp[9]="SERVER_ADMIN=root@paul"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] envp[10]="SOFTWARE=CUPS/1.3.9"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] envp[11]="TMPDIR=/var/spool/cups/tmp"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] envp[12]="TZ=America/Panama"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] envp[13]="USER=root"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] envp[16]="IPP_PORT=631"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] envp[17]="CHARSET=utf-8"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] envp[18]="LANG=en_US.UTF8"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] envp[19]="PPD=/etc/cups/ppd/MP140-series.ppd"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] envp[20]="RIP_MAX_CACHE=8m"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] envp[21]="CONTENT_TYPE=application/postscript"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] envp[22]="DEVICE_URI=usb://Canon/MP140%20series"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] envp[23]="PRINTER=MP140-series"',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] envp[24]="FINAL_CONTENT_TYPE=printer/MP140-series"',
               'I [22/Jun/2009:09:49:31 -0500] [Job 6] Started filter /usr/lib/cups/filter/pstopdf (PID 4516)',
               'I [22/Jun/2009:09:49:31 -0500] [Job 6] Started filter /usr/lib/cups/filter/pdftopdf (PID 4517)',
               'I [22/Jun/2009:09:49:31 -0500] [Job 6] Started filter /usr/lib/cups/filter/cpdftocps (PID 4518)',
               'I [22/Jun/2009:09:49:31 -0500] [Job 6] Started filter /usr/lib/cups/filter/pstocanonij (PID 4519)',
               'I [22/Jun/2009:09:49:31 -0500] [Job 6] Started backend /usr/lib/cups/backend/usb (PID 4523)',
               'I [22/Jun/2009:09:49:31 -0500] Saving subscriptions.conf...',
               'D [22/Jun/2009:09:49:31 -0500] cupsdProcessIPPRequest: 23 status_code=0 (successful-ok)',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] pstopdf 6 args: 6 paul Test Page 1 job-uuid=urn:uuid:b5c102bb-9a3a-36e8-6198-48f80bdd6237 /var/spool/cups/d00006-001',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] PPD: /etc/cups/ppd/MP140-series.ppd',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] pstocanonij start.',
               'I [22/Jun/2009:09:49:31 -0500] Saving subscriptions.conf...',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] Printer using device file "/dev/usblp0"...',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] backendRunLoop(print_fd=0, device_fd=7, use_bc=0, side_cb=0xb7f9ea80)',
               'I [22/Jun/2009:09:49:31 -0500] Saving subscriptions.conf...',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] Resolution: 600',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] Page size: Letter',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] Width: , height: , absolute margins: , , ,',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] Relative margins: , , ,',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] PPD options: -r600',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] PostScript to be injected:',
               'D [22/Jun/2009:09:49:31 -0500] [Job 6] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                -dDoNumCopies -dPDFSETTINGS=/printer -r600 - -',
               'D [22/Jun/2009:09:49:31 -0500] cupsdAcceptClient: 24 from localhost (Domain)',
               'D [22/Jun/2009:09:49:31 -0500] cupsdReadClient: 24 POST / HTTP/1.1',
               'D [22/Jun/2009:09:49:31 -0500] cupsdAuthorize: No authentication data provided.',
               'D [22/Jun/2009:09:49:31 -0500] Get-Notifications /',
               'D [22/Jun/2009:09:49:31 -0500] cupsdIsAuthorized: requesting-user-name="paul"',
               'D [22/Jun/2009:09:49:31 -0500] cupsdProcessIPPRequest: 24 status_code=0 (successful-ok)',
               'D [22/Jun/2009:09:49:31 -0500] cupsdAcceptClient: 25 from localhost (Domain)',
               'D [22/Jun/2009:09:49:31 -0500] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [22/Jun/2009:09:49:31 -0500] cupsdAuthorize: No authentication data provided.',
               'D [22/Jun/2009:09:49:31 -0500] Get-Notifications /',
               'D [22/Jun/2009:09:49:31 -0500] cupsdIsAuthorized: requesting-user-name="paul"',
               'D [22/Jun/2009:09:49:31 -0500] cupsdProcessIPPRequest: 25 status_code=0 (successful-ok)',
               'D [22/Jun/2009:09:49:31 -0500] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [22/Jun/2009:09:49:31 -0500] cupsdAuthorize: No authentication data provided.',
               'D [22/Jun/2009:09:49:31 -0500] Get-Job-Attributes ipp://localhost/jobs/6',
               'D [22/Jun/2009:09:49:31 -0500] cupsdProcessIPPRequest: 25 status_code=0 (successful-ok)',
               'D [22/Jun/2009:09:49:31 -0500] cupsdCloseClient: 24',
               'D [22/Jun/2009:09:49:31 -0500] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [22/Jun/2009:09:49:31 -0500] cupsdAuthorize: No authentication data provided.',
               'D [22/Jun/2009:09:49:31 -0500] Get-Notifications /',
               'D [22/Jun/2009:09:49:31 -0500] cupsdIsAuthorized: requesting-user-name="paul"',
               'D [22/Jun/2009:09:49:31 -0500] cupsdProcessIPPRequest: 16 status_code=0 (successful-ok)',
               'D [22/Jun/2009:09:49:32 -0500] cupsdCloseClient: 25',
               'D [22/Jun/2009:09:49:32 -0500] [Job 6] GPL Ghostscript 8.64: Set UseCIEColor for UseDeviceIndependentColor to work properly.',
               'D [22/Jun/2009:09:49:32 -0500] PID 4516 (/usr/lib/cups/filter/pstopdf) exited with no errors.',
               'D [22/Jun/2009:09:49:32 -0500] PID 4517 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [22/Jun/2009:09:49:32 -0500] [Job 6] Device copies: 1; device collate:',
               'D [22/Jun/2009:09:49:32 -0500] [Job 6] pdftops - copying to temp print file "/tmp/4a3f99fcbea81"',
               'D [22/Jun/2009:09:49:33 -0500] [Job 6] Page = 612x792; 18,14 to 594,784',
               'D [22/Jun/2009:09:49:33 -0500] [Job 6] slow_collate=0, slow_duplex=0, slow_order=0',
               'D [22/Jun/2009:09:49:33 -0500] [Job 6] Before copy_comments - %!PS-Adobe-3.0',
               'D [22/Jun/2009:09:49:33 -0500] [Job 6] %!PS-Adobe-3.0',
               'D [22/Jun/2009:09:49:33 -0500] [Job 6] %%Pages: (atend)',
               'D [22/Jun/2009:09:49:33 -0500] [Job 6] %%BoundingBox: (atend)',
               'D [22/Jun/2009:09:49:33 -0500] [Job 6] %%HiResBoundingBox: (atend)',
               'D [22/Jun/2009:09:49:33 -0500] [Job 6] %%Creator: GPL Ghostscript 864 (pswrite)',
               'D [22/Jun/2009:09:49:33 -0500] [Job 6] %%CreationDate: 2009/06/22 09:49:33',
               'D [22/Jun/2009:09:49:33 -0500] [Job 6] %%DocumentData: Clean7Bit',
               'D [22/Jun/2009:09:49:33 -0500] [Job 6] %%LanguageLevel: 3',
               'D [22/Jun/2009:09:49:33 -0500] [Job 6] %%EndComments',
               'D [22/Jun/2009:09:49:33 -0500] [Job 6] Before copy_prolog - %%BeginProlog',
               'D [22/Jun/2009:09:49:33 -0500] [Job 6] Before copy_setup - %%Page: 1 1',
               'D [22/Jun/2009:09:49:33 -0500] [Job 6] Before page loop - %%Page: 1 1',
               'D [22/Jun/2009:09:49:33 -0500] [Job 6] Copying page 1...',
               'D [22/Jun/2009:09:49:33 -0500] [Job 6] pagew = 576.0, pagel = 769.3',
               'D [22/Jun/2009:09:49:33 -0500] [Job 6] bboxx = 0, bboxy = 0, bboxw = 612, bboxl = 792',
               'D [22/Jun/2009:09:49:33 -0500] [Job 6] PageLeft = 18.1, PageRight = 594.1',
               'D [22/Jun/2009:09:49:33 -0500] [Job 6] PageTop = 783.5, PageBottom = 14.2',
               'D [22/Jun/2009:09:49:33 -0500] [Job 6] PageWidth = 612.0, PageLength = 792.0',
               'D [22/Jun/2009:09:49:33 -0500] [Job 6] pstocanonij: /usr/bin/gs -r600 -g5100x6600 -q -dNOPROMPT -dSAFER -sDEVICE=ppmraw -sOutputFile=- -| /usr/local/bin/cifmp140 --imageres 600 --papersize letter --media plain --paperload asf --bbox 18,14,594,784',
               'D [22/Jun/2009:09:49:33 -0500] [Job 6] /usr/local/bin/cifmp140: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory',
               'D [22/Jun/2009:09:49:33 -0500] [Job 6] Wrote 1 pages...',
               'D [22/Jun/2009:09:49:33 -0500] PID 4518 (/usr/lib/cups/filter/cpdftocps) exited with no errors.',
               'D [22/Jun/2009:09:49:34 -0500] [Job 6] GPL Ghostscript 8.64: Unrecoverable error, exit code 1',
               'D [22/Jun/2009:09:49:34 -0500] PID 4519 (/usr/lib/cups/filter/pstocanonij) exited with no errors.',
               'D [22/Jun/2009:09:49:34 -0500] PID 4523 (/usr/lib/cups/backend/usb) exited with no errors.',
               'D [22/Jun/2009:09:49:34 -0500] [Job 6] File 0 is complete.',
               'I [22/Jun/2009:09:49:34 -0500] [Job 6] Completed successfully.',
               'I [22/Jun/2009:09:49:34 -0500] Saving subscriptions.conf...',
               'I [22/Jun/2009:09:49:34 -0500] Saving subscriptions.conf...',
               'D [22/Jun/2009:09:49:34 -0500] cupsdAcceptClient: 24 from localhost (Domain)',
               'D [22/Jun/2009:09:49:34 -0500] cupsdAcceptClient: 25 from localhost (Domain)',
               'D [22/Jun/2009:09:49:34 -0500] cupsdReadClient: 24 POST / HTTP/1.1',
               'D [22/Jun/2009:09:49:34 -0500] cupsdAuthorize: No authentication data provided.',
               'D [22/Jun/2009:09:49:34 -0500] Get-Notifications /',
               'D [22/Jun/2009:09:49:34 -0500] cupsdIsAuthorized: requesting-user-name="paul"',
               'D [22/Jun/2009:09:49:34 -0500] cupsdProcessIPPRequest: 24 status_code=0 (successful-ok)',
               'D [22/Jun/2009:09:49:34 -0500] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [22/Jun/2009:09:49:34 -0500] cupsdAuthorize: No authentication data provided.',
               'D [22/Jun/2009:09:49:34 -0500] Get-Notifications /',
               'D [22/Jun/2009:09:49:34 -0500] cupsdIsAuthorized: requesting-user-name="paul"',
               'D [22/Jun/2009:09:49:34 -0500] cupsdProcessIPPRequest: 25 status_code=0 (successful-ok)',
               'D [22/Jun/2009:09:49:34 -0500] cupsdCloseClient: 25',
               'D [22/Jun/2009:09:49:34 -0500] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [22/Jun/2009:09:49:34 -0500] cupsdAuthorize: No authentication data provided.',
               'D [22/Jun/2009:09:49:34 -0500] Get-Notifications /',
               'D [22/Jun/2009:09:49:34 -0500] cupsdIsAuthorized: requesting-user-name="paul"',
               'D [22/Jun/2009:09:49:34 -0500] cupsdProcessIPPRequest: 16 status_code=0 (successful-ok)',
               'D [22/Jun/2009:09:49:34 -0500] cupsdCloseClient: 24',
               'D [22/Jun/2009:09:49:35 -0500] [Job 6] Unloading...',
               'D [22/Jun/2009:09:49:42 -0500] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [22/Jun/2009:09:49:42 -0500] cupsdAuthorize: No authentication data provided.',
               'D [22/Jun/2009:09:49:42 -0500] Get-Job-Attributes ipp://localhost/jobs/6',
               'D [22/Jun/2009:09:49:42 -0500] [Job 6] Loading attributes...',
               'D [22/Jun/2009:09:49:42 -0500] cupsdProcessIPPRequest: 16 status_code=0 (successful-ok)',
               'D [22/Jun/2009:09:49:42 -0500] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [22/Jun/2009:09:49:42 -0500] cupsdAuthorize: No authentication data provided.',
               'D [22/Jun/2009:09:49:42 -0500] Cancel-Subscription /',
               'D [22/Jun/2009:09:49:42 -0500] cupsdIsAuthorized: requesting-user-name="paul"',
               'I [22/Jun/2009:09:49:42 -0500] Saving subscriptions.conf...',
               'D [22/Jun/2009:09:49:42 -0500] cupsdProcessIPPRequest: 16 status_code=0 (successful-ok)',
               'D [22/Jun/2009:09:49:42 -0500] cupsdAcceptClient: 24 from localhost (Domain)',
               'D [22/Jun/2009:09:49:42 -0500] cupsdReadClient: 24 GET /admin/log/error_log HTTP/1.1',
               'D [22/Jun/2009:09:49:42 -0500] cupsdAuthorize: No authentication data provided.']}
Page 10 (Locale issues):
{'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}

---

### Post by bizmeds on 2009-06-22
I found the problem! Yea... after some thinking I came to the conclusion that the driver wasn't being recognized I then double checked and found it was not pointing to MP-150 driver once I pointed it toward there the test page ran well.

---

### Post by neglect on 2009-08-22
Just bought it today, I'm on 9.04 and the same goes here:
plug it in, point to the MP150 drivers and everything works out of the box. Test page printed fine and scanning is working fine as well through xsane.

---

### Post by jano2 on 2009-11-09
hi, tested yesterday with karmic koala, and dpkg complained about libcupsys2 dépendancy. 
 I needed to modify the cnijfilter-common_2.80-1_i386.deb and cnijfilter-mp140series_2.80-1_i386.deb, changing the dependancy libcupsys2 with libcups2.
 I didn't install the scan stuff, xsane working is enough for me. 

#mkdir modified-deb  
#dpkg -x cnijfilter-common_2.80-1_i386.deb modified-deb/cnijfilter-common_2.80-1_i386
#dpkg -e cnijfilter-common_2.80-1_i386.deb modified-deb/cnijfilter-common_2.80-1_i386/DEBIAN

 then edit modified-deb/cnijfilter-common_2.80-1_i386/DEBIAN/control and replace licupsys2 with libcups2.
 and finally :

#cd modified-deb
#dpkg -b cnijfilter-common_2.80-1_i386

 next the same for cnijfilter-mp140series_2.80-1_i386.deb. and after installing new created packages, all was fine for me.

 jano2

---

### Post by augustoschwartz on 2011-06-27
Hello everybody!
Today I faced the same problem ... Canon's site sends you to a map where you choose regions like Brazil, which is where I live, there comes the option of Linux driver; '(
\ o / I chose Europe, France, worked.
Here is the direct link to download the driver from the Canon site: [http://www.canon.fr/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/PIXMA_MP140.aspx?DLtcmuri=tcm:79-738153&page=1&type](http://www.canon.fr/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/PIXMA_MP140.aspx?DLtcmuri=tcm:79-738153&page=1&type) = download
Or this alternative for Debian and RPM: [http://www.4shared.com/file/oIyuwCJ7/MP140_debian.html](http://www.4shared.com/file/oIyuwCJ7/MP140_debian.html)

[http://www.4shared.com/file/OSyGeCg3/MP140_rpm.html](http://www.4shared.com/file/OSyGeCg3/MP140_rpm.html)

---

