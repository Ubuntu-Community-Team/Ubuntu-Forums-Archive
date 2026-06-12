---
title: "There is a missing print filter for Printer HP LaserJet P4014 not working"
date: 2018-10-22
forum: Hardware
---

### Post by evilchip on 2018-10-22
Hello everyone. After the last update of Ubuntu the office's printer stopped working. 
It says Warning: HP-LaserJet-P4012 opc-life-over

If I type ```
dpkg -l | grep cups
```

I obtain

```
ii  bluez-cups                                    5.48-0ubuntu3.1                             amd64        Bluetooth printer driver for CUPS
ii  cups                                          2.2.7-1ubuntu2.1                            amd64        Common UNIX Printing System(tm) - PPD/driver support, web interface
ii  cups-browsed                                  1.20.2-0ubuntu3                             amd64        OpenPrinting CUPS Filters - cups-browsed
ii  cups-bsd                                      2.2.7-1ubuntu2.1                            amd64        Common UNIX Printing System(tm) - BSD commands
ii  cups-client                                   2.2.7-1ubuntu2.1                            amd64        Common UNIX Printing System(tm) - client programs (SysV)
ii  cups-common                                   2.2.7-1ubuntu2.1                            all          Common UNIX Printing System(tm) - common files
ii  cups-core-drivers                             2.2.7-1ubuntu2.1                            amd64        Common UNIX Printing System(tm) - driverless printing
ii  cups-daemon                                   2.2.7-1ubuntu2.1                            amd64        Common UNIX Printing System(tm) - daemon
ii  cups-filters                                  1.20.2-0ubuntu3                             amd64        OpenPrinting CUPS Filters - Main Package
ii  cups-filters-core-drivers                     1.20.2-0ubuntu3                             amd64        OpenPrinting CUPS Filters - Driverless printing
ii  cups-ipp-utils                                2.2.7-1ubuntu2.1                            amd64        Common UNIX Printing System(tm) - IPP developer/admin utilities
ii  cups-pk-helper                                0.2.6-1ubuntu1.2                            amd64        PolicyKit helper to configure cups with fine-grained privileges
ii  cups-ppdc                                     2.2.7-1ubuntu2.1                            amd64        Common UNIX Printing System(tm) - PPD manipulation utilities
ii  cups-server-common                            2.2.7-1ubuntu2.1                            all          Common UNIX Printing System(tm) - server common files
ii  libcups2:amd64                                2.2.7-1ubuntu2.1                            amd64        Common UNIX Printing System(tm) - Core library
ii  libcups2:i386                                 2.2.7-1ubuntu2.1                            i386         Common UNIX Printing System(tm) - Core library
ii  libcupscgi1:amd64                             2.2.7-1ubuntu2.1                            amd64        Common UNIX Printing System(tm) - CGI library
ii  libcupsfilters1:amd64                         1.20.2-0ubuntu3                             amd64        OpenPrinting CUPS Filters - Shared library
ii  libcupsimage2:amd64                           2.2.7-1ubuntu2.1                            amd64        Common UNIX Printing System(tm) - Raster image library
ii  libcupsmime1:amd64                            2.2.7-1ubuntu2.1                            amd64        Common UNIX Printing System(tm) - MIME library
ii  libcupsppdc1:amd64                            2.2.7-1ubuntu2.1                            amd64        Common UNIX Printing System(tm) - PPD manipulation library
ii  printer-driver-hpcups                         3.17.10+repack0-5                           amd64        HP Linux Printing and Imaging - CUPS Raster driver (hpcups)
ii  python3-cups                                  1.9.73-2                                    amd64        Python3 bindings for CUPS
ii  python3-cupshelpers                           1.5.11-1ubuntu2                             all          Python utility modules around the CUPS printing system
```

Using ```
lpstat -t


```
  I get

```
scheduler is running
system default destination: HP-LaserJet-P4014
device for HP-LaserJet-P4014: socket://192.168.9.19
HP-LaserJet-P4014 accepting requests since lun. 22 oct. 2018 14:18:33 CEST
printer HP-LaserJet-P4014 is idle.  enabled since lun. 22 oct. 2018 14:18:33 CEST
    Filter failed
```
The error log ```

sudo cat /var/log/cups/error_log
```
 
gets me
 
```

E [22/Oct/2018:00:09:41 +0200] HP-LaserJet-P4014: File \"/usr/lib/cups/filter/foomatic-rip-hplip\" not available: No such file or directory
E [22/Oct/2018:00:09:41 +0200] HP-LaserJet-P4014: File \"/usr/lib/cups/filter/foomatic-rip-hplip\" not available: No such file or directory
E [22/Oct/2018:00:09:41 +0200] HP-LaserJet-P4014: File \"/usr/lib/cups/filter/foomatic-rip-hplip\" not available: No such file or directory
E [22/Oct/2018:00:09:41 +0200] HP-LaserJet-P4014: File \"/usr/lib/cups/filter/foomatic-rip-hplip\" not available: No such file or directory
W [22/Oct/2018:00:09:41 +0200] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id \'HP-LaserJet-P4014-Gray..\' already exists
W [22/Oct/2018:00:09:41 +0200] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id \'HP-LaserJet-P4014-RGB..\' already exists
E [22/Oct/2018:14:08:52 +0200] [Job 111] Job stopped due to filter errors; please consult the error_log file for details.
D [22/Oct/2018:14:08:52 +0200] [Job 111] The following messages were recorded from 14:08:52 to 14:08:52
D [22/Oct/2018:14:08:52 +0200] [Job 111] Applying default options...
D [22/Oct/2018:14:08:52 +0200] [Job 111] Adding start banner page "none".
D [22/Oct/2018:14:08:52 +0200] [Job 111] Adding end banner page "none".
D [22/Oct/2018:14:08:52 +0200] [Job 111] File of type application/vnd.cups-pdf-banner queued by "icb".
D [22/Oct/2018:14:08:52 +0200] [Job 111] hold_until=0
D [22/Oct/2018:14:08:52 +0200] [Job 111] Queued on "HP-LaserJet-P4014" by "icb".
D [22/Oct/2018:14:08:52 +0200] [Job 111] time-at-processing=1540210132
D [22/Oct/2018:14:08:52 +0200] [Job 111] 3 filters for job:
D [22/Oct/2018:14:08:52 +0200] [Job 111] bannertopdf (application/vnd.cups-pdf-banner to application/pdf, cost 32)
D [22/Oct/2018:14:08:52 +0200] [Job 111] pdftopdf (application/pdf to application/vnd.cups-pdf, cost 66)
D [22/Oct/2018:14:08:52 +0200] [Job 111] foomatic-rip-hplip (application/vnd.cups-pdf to printer/HP-LaserJet-P4014, cost 0)
D [22/Oct/2018:14:08:52 +0200] [Job 111] job-sheets=none,none
D [22/Oct/2018:14:08:52 +0200] [Job 111] argv[0]="HP-LaserJet-P4014"
D [22/Oct/2018:14:08:52 +0200] [Job 111] argv[1]="111"
D [22/Oct/2018:14:08:52 +0200] [Job 111] argv[2]="icb"
D [22/Oct/2018:14:08:52 +0200] [Job 111] argv[3]="Test Page"
D [22/Oct/2018:14:08:52 +0200] [Job 111] argv[4]="1"
D [22/Oct/2018:14:08:52 +0200] [Job 111] argv[5]="job-uuid=urn:uuid:2a3b4c43-5cfc-3523-632e-e5b19ee2781f job-originating-host-name=localhost date-time-at-creation= date-time-at-processing= time-at-creation=1540210132 time-at-processing=1540210132"
D [22/Oct/2018:14:08:52 +0200] [Job 111] argv[6]="/var/spool/cups/d00111-001"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[7]="CUPS_STATEDIR=/run/cups"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[8]="HOME=/var/spool/cups/tmp"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[10]="SERVER_ADMIN=root@icb-OptiPlex-7050"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[11]="SOFTWARE=CUPS/2.2.7"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[13]="USER=root"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[14]="CUPS_MAX_MESSAGE=2047"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[17]="IPP_PORT=631"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[18]="CHARSET=utf-8"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[19]="LANG=en_US.UTF-8"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[20]="PPD=/etc/cups/ppd/HP-LaserJet-P4014.ppd"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[21]="RIP_MAX_CACHE=128m"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[22]="CONTENT_TYPE=application/vnd.cups-pdf-banner"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[23]="DEVICE_URI=socket://192.168.9.19"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[24]="PRINTER_INFO=HP LaserJet P4014"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[25]="PRINTER_LOCATION="
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[26]="PRINTER=HP-LaserJet-P4014"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[27]="PRINTER_STATE_REASONS=none"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[28]="CUPS_FILETYPE=document"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[29]="FINAL_CONTENT_TYPE=application/vnd.cups-pdf"
D [22/Oct/2018:14:08:52 +0200] [Job 111] envp[30]="AUTH_I****"
D [22/Oct/2018:14:08:52 +0200] [Job 111] Started filter /usr/lib/cups/filter/bannertopdf (PID 13656)
D [22/Oct/2018:14:08:52 +0200] [Job 111] Started filter /usr/lib/cups/filter/pdftopdf (PID 13657)
D [22/Oct/2018:14:08:52 +0200] [Job 111] Started filter /usr/lib/cups/filter/foomatic-rip-hplip (PID 13658)
D [22/Oct/2018:14:08:52 +0200] [Job 111] Started backend /usr/lib/cups/backend/socket (PID 13659)
D [22/Oct/2018:14:08:52 +0200] [Job 111] pdftopdf: Last filter determined by the PPD: foomatic-rip-hplip; FINAL_CONTENT_TYPE: application/vnd.cups-pdf => pdftopdf will not log pages in page_log.
D [22/Oct/2018:14:08:52 +0200] [Job 111] Calling FindDeviceById(cups-HP-LaserJet-P4014)
D [22/Oct/2018:14:08:52 +0200] [Job 111] Found device /org/freedesktop/ColorManager/devices/cups_HP_LaserJet_P4014
D [22/Oct/2018:14:08:52 +0200] [Job 111] Calling org.freedesktop.ColorManager.Device.Get(ProfilingInhibitors)
D [22/Oct/2018:14:08:52 +0200] [Job 111] \'CM Color Calibration\' Mode in SPOOLER-LESS: Off
D [22/Oct/2018:14:08:52 +0200] [Job 111] Getting input from file 
D [22/Oct/2018:14:08:52 +0200] [Job 111] foomatic-rip version 1.20.2 running...
D [22/Oct/2018:14:08:52 +0200] [Job 111] Parsing PPD file ...
D [22/Oct/2018:14:08:52 +0200] [Job 111] Added option ColorSpace
D [22/Oct/2018:14:08:52 +0200] [Job 111] Added option Resolution
D [22/Oct/2018:14:08:52 +0200] [Job 111] Added option PageSize
D [22/Oct/2018:14:08:52 +0200] [Job 111] Added option Model
D [22/Oct/2018:14:08:52 +0200] [Job 111] Added option PrintoutMode
D [22/Oct/2018:14:08:52 +0200] [Job 111] Added option InputSlot
D [22/Oct/2018:14:08:52 +0200] [Job 111] STATE: +connecting-to-device
D [22/Oct/2018:14:08:52 +0200] [Job 111] Looking up \"192.168.9.19\"...
D [22/Oct/2018:14:08:52 +0200] [Job 111] STATE: -connecting-to-device
D [22/Oct/2018:14:08:52 +0200] [Job 111] 192.168.9.19=192.168.9.19
D [22/Oct/2018:14:08:52 +0200] [Job 111] PDF template file doesn\'t have form. It\'s okay.
D [22/Oct/2018:14:08:52 +0200] [Job 111] Added option Duplex
D [22/Oct/2018:14:08:52 +0200] [Job 111] Added option Quality
D [22/Oct/2018:14:08:52 +0200] [Job 111] Added option ImageableArea
D [22/Oct/2018:14:08:52 +0200] [Job 111] Added option PaperDimension
D [22/Oct/2018:14:08:52 +0200] [Job 111] Added option Font
D [22/Oct/2018:14:08:52 +0200] [Job 111] Parameter Summary
D [22/Oct/2018:14:08:52 +0200] [Job 111] -----------------
D [22/Oct/2018:14:08:52 +0200] [Job 111] Spooler: cups
D [22/Oct/2018:14:08:52 +0200] [Job 111] Printer: HP-LaserJet-P4014
D [22/Oct/2018:14:08:52 +0200] [Job 111] Shell: /bin/sh
D [22/Oct/2018:14:08:52 +0200] [Job 111] PPD file: /etc/cups/ppd/HP-LaserJet-P4014.ppd
D [22/Oct/2018:14:08:52 +0200] [Job 111] ATTR file: 
D [22/Oct/2018:14:08:52 +0200] [Job 111] Printer model: HP LaserJet p4014 hpijs, 3.17.10
D [22/Oct/2018:14:08:52 +0200] [Job 111] Job title: Test Page
D [22/Oct/2018:14:08:52 +0200] [Job 111] File(s) to be printed:
D [22/Oct/2018:14:08:52 +0200] [Job 111] <STDIN>
D [22/Oct/2018:14:08:52 +0200] [Job 111] Ghostscript extra search path (\'GS_LIB\'): /usr/share/cups/fonts
D [22/Oct/2018:14:08:52 +0200] [Job 111] Printing system options:
D [22/Oct/2018:14:08:52 +0200] [Job 111] Pondering option \'job-uuid=urn:uuid:2a3b4c43-5cfc-3523-632e-e5b19ee2781f\'
D [22/Oct/2018:14:08:52 +0200] [Job 111] Unknown option job-uuid=urn:uuid:2a3b4c43-5cfc-3523-632e-e5b19ee2781f.
D [22/Oct/2018:14:08:52 +0200] [Job 111] Pondering option \'job-originating-host-name=localhost\'
D [22/Oct/2018:14:08:52 +0200] [Job 111] Unknown option job-originating-host-name=localhost.
D [22/Oct/2018:14:08:52 +0200] [Job 111] Pondering option \'date-time-at-creation=\'
D [22/Oct/2018:14:08:52 +0200] [Job 111] Unknown option date-time-at-creation=.
D [22/Oct/2018:14:08:52 +0200] [Job 111] Pondering option \'date-time-at-processing=\'
D [22/Oct/2018:14:08:52 +0200] [Job 111] Unknown option date-time-at-processing=.
D [22/Oct/2018:14:08:52 +0200] [Job 111] Pondering option \'time-at-creation=1540210132\'
D [22/Oct/2018:14:08:52 +0200] [Job 111] Unknown option time-at-creation=1540210132.
D [22/Oct/2018:14:08:52 +0200] [Job 111] Pondering option \'time-at-processing=1540210132\'
D [22/Oct/2018:14:08:52 +0200] [Job 111] Unknown option time-at-processing=1540210132.
D [22/Oct/2018:14:08:52 +0200] [Job 111] CM Color Calibration Mode in CUPS: Off
D [22/Oct/2018:14:08:52 +0200] [Job 111] Options from the PPD file:
D [22/Oct/2018:14:08:52 +0200] [Job 111] ================================================
D [22/Oct/2018:14:08:52 +0200] [Job 111] File: <STDIN>
D [22/Oct/2018:14:08:52 +0200] [Job 111] ================================================
D [22/Oct/2018:14:08:52 +0200] [Job 111] PID 13656 (/usr/lib/cups/filter/bannertopdf) exited with no errors.
D [22/Oct/2018:14:08:52 +0200] [Job 111] Filetype: PDF
D [22/Oct/2018:14:08:52 +0200] [Job 111] Storing temporary files in /tmp
D [22/Oct/2018:14:08:52 +0200] [Job 111] PID 13657 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [22/Oct/2018:14:08:52 +0200] [Job 111] hrDeviceDesc=\"HP LaserJet P4014\"
D [22/Oct/2018:14:08:52 +0200] [Job 111] prtMarkerColorantValue.1.1 = \"black\"
D [22/Oct/2018:14:08:52 +0200] [Job 111] ATTR: marker-colors=#000000,none
D [22/Oct/2018:14:08:52 +0200] [Job 111] ATTR: marker-names=\'\"Black Cartridge HP CC364A\"\',\'\"Maintenance Kit HP 110V-CB388A, 220V-CB389A\"\'
D [22/Oct/2018:14:08:52 +0200] [Job 111] ATTR: marker-types=toner-cartridge,fuser
D [22/Oct/2018:14:08:52 +0200] [Job 111] ATTR: marker-levels=100,0
D [22/Oct/2018:14:08:52 +0200] [Job 111] new_supply_state=20, change_state=ffff
D [22/Oct/2018:14:08:52 +0200] [Job 111] STATE: -developer-low-report
D [22/Oct/2018:14:08:52 +0200] [Job 111] STATE: -developer-empty-warning
D [22/Oct/2018:14:08:52 +0200] [Job 111] STATE: -marker-supply-low-report
D [22/Oct/2018:14:08:52 +0200] [Job 111] STATE: -marker-supply-empty-warning
D [22/Oct/2018:14:08:52 +0200] [Job 111] STATE: -opc-near-eol-report
D [22/Oct/2018:14:08:52 +0200] [Job 111] STATE: +opc-life-over-warning
D [22/Oct/2018:14:08:52 +0200] [Job 111] STATE: -toner-low-report
D [22/Oct/2018:14:08:52 +0200] [Job 111] STATE: -toner-empty-warning
D [22/Oct/2018:14:08:52 +0200] [Job 111] STATE: -waste-receptacle-almost-full-report
D [22/Oct/2018:14:08:52 +0200] [Job 111] STATE: -waste-receptacle-full-warning
D [22/Oct/2018:14:08:52 +0200] [Job 111] STATE: -cleaner-life-almost-over-report
D [22/Oct/2018:14:08:52 +0200] [Job 111] STATE: -cleaner-life-over-warning
D [22/Oct/2018:14:08:52 +0200] [Job 111] ./base/gsicc_manage.c:1244: gsicc_open_search(): Could not find default_gray.icc 
D [22/Oct/2018:14:08:52 +0200] [Job 111] | ./base/gsicc_manage.c:2261: gsicc_init_iccmanager(): cannot find default icc profile
D [22/Oct/2018:14:08:52 +0200] [Job 111] ./base/gsicc_manage.c:1244: gsicc_open_search(): Could not find default_gray.icc 
D [22/Oct/2018:14:08:52 +0200] [Job 111] | ./base/gsicc_manage.c:2025: gsicc_set_device_profile(): cannot find device profile
D [22/Oct/2018:14:08:52 +0200] [Job 111] **** Unable to open the initial device, quitting.
D [22/Oct/2018:14:08:52 +0200] [Job 111] Process is dying with \"Unable to determine number of pages, page count: -1
D [22/Oct/2018:14:08:52 +0200] [Job 111] \", exit stat 3
D [22/Oct/2018:14:08:52 +0200] [Job 111] Cleaning up...
D [22/Oct/2018:14:08:52 +0200] [Job 111] PID 13658 (/usr/lib/cups/filter/foomatic-rip-hplip) stopped with status 3.
D [22/Oct/2018:14:08:52 +0200] [Job 111] Hint: Try setting the LogLevel to "debug" to find out more.
D [22/Oct/2018:14:08:52 +0200] [Job 111] new_state=3000, change_state=ffff
D [22/Oct/2018:14:08:52 +0200] [Job 111] STATE: -media-empty-warning
D [22/Oct/2018:14:08:52 +0200] [Job 111] STATE: -door-open-report
D [22/Oct/2018:14:08:52 +0200] [Job 111] STATE: -media-jam-warning
D [22/Oct/2018:14:08:52 +0200] [Job 111] STATE: -input-tray-missing-warning
D [22/Oct/2018:14:08:52 +0200] [Job 111] STATE: -output-tray-missing-warning
D [22/Oct/2018:14:08:52 +0200] [Job 111] STATE: -marker-supply-missing-warning
D [22/Oct/2018:14:08:52 +0200] [Job 111] STATE: -output-area-almost-full-report
D [22/Oct/2018:14:08:52 +0200] [Job 111] STATE: -output-area-full-warning
D [22/Oct/2018:14:08:52 +0200] [Job 111] backendWaitLoop(snmp_fd=5, addr=0x55ee8f194148, side_cb=0x55ee8e515360)
D [22/Oct/2018:14:08:52 +0200] [Job 111] PID 13659 (/usr/lib/cups/backend/socket) exited with no errors.
D [22/Oct/2018:14:08:52 +0200] [Job 111] End of messages
D [22/Oct/2018:14:08:52 +0200] [Job 111] printer-state=3(idle)
D [22/Oct/2018:14:08:52 +0200] [Job 111] printer-state-message="Filter failed"
D [22/Oct/2018:14:08:52 +0200] [Job 111] printer-state-reasons=opc-life-over-warning
E [22/Oct/2018:14:18:33 +0200] [Job 112] Job stopped due to filter errors; please consult the error_log file for details.
D [22/Oct/2018:14:18:33 +0200] [Job 112] The following messages were recorded from 14:18:33 to 14:18:33
D [22/Oct/2018:14:18:33 +0200] [Job 112] Applying default options...
D [22/Oct/2018:14:18:33 +0200] [Job 112] Adding start banner page "none".
D [22/Oct/2018:14:18:33 +0200] [Job 112] Adding end banner page "none".
D [22/Oct/2018:14:18:33 +0200] [Job 112] File of type application/vnd.cups-pdf-banner queued by "icb".
D [22/Oct/2018:14:18:33 +0200] [Job 112] hold_until=0
D [22/Oct/2018:14:18:33 +0200] [Job 112] Queued on "HP-LaserJet-P4014" by "icb".
D [22/Oct/2018:14:18:33 +0200] [Job 112] time-at-processing=1540210713
D [22/Oct/2018:14:18:33 +0200] [Job 112] 3 filters for job:
D [22/Oct/2018:14:18:33 +0200] [Job 112] bannertopdf (application/vnd.cups-pdf-banner to application/pdf, cost 32)
D [22/Oct/2018:14:18:33 +0200] [Job 112] pdftopdf (application/pdf to application/vnd.cups-pdf, cost 66)
D [22/Oct/2018:14:18:33 +0200] [Job 112] foomatic-rip-hplip (application/vnd.cups-pdf to printer/HP-LaserJet-P4014, cost 0)
D [22/Oct/2018:14:18:33 +0200] [Job 112] job-sheets=none,none
D [22/Oct/2018:14:18:33 +0200] [Job 112] argv[0]="HP-LaserJet-P4014"
D [22/Oct/2018:14:18:33 +0200] [Job 112] argv[1]="112"
D [22/Oct/2018:14:18:33 +0200] [Job 112] argv[2]="icb"
D [22/Oct/2018:14:18:33 +0200] [Job 112] argv[3]="Test Page"
D [22/Oct/2018:14:18:33 +0200] [Job 112] argv[4]="1"
D [22/Oct/2018:14:18:33 +0200] [Job 112] argv[5]="job-uuid=urn:uuid:0626a944-a85c-33ea-6b5d-5ee7f0c3d74c job-originating-host-name=localhost date-time-at-creation= date-time-at-processing= time-at-creation=1540210713 time-at-processing=1540210713"
D [22/Oct/2018:14:18:33 +0200] [Job 112] argv[6]="/var/spool/cups/d00112-001"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[7]="CUPS_STATEDIR=/run/cups"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[8]="HOME=/var/spool/cups/tmp"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[10]="SERVER_ADMIN=root@icb-OptiPlex-7050"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[11]="SOFTWARE=CUPS/2.2.7"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[13]="USER=root"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[14]="CUPS_MAX_MESSAGE=2047"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[17]="IPP_PORT=631"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[18]="CHARSET=utf-8"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[19]="LANG=en_US.UTF-8"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[20]="PPD=/etc/cups/ppd/HP-LaserJet-P4014.ppd"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[21]="RIP_MAX_CACHE=128m"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[22]="CONTENT_TYPE=application/vnd.cups-pdf-banner"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[23]="DEVICE_URI=socket://192.168.9.19"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[24]="PRINTER_INFO=HP LaserJet P4014"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[25]="PRINTER_LOCATION="
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[26]="PRINTER=HP-LaserJet-P4014"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[27]="PRINTER_STATE_REASONS=opc-life-over-warning"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[28]="CUPS_FILETYPE=document"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[29]="FINAL_CONTENT_TYPE=application/vnd.cups-pdf"
D [22/Oct/2018:14:18:33 +0200] [Job 112] envp[30]="AUTH_I****"
D [22/Oct/2018:14:18:33 +0200] [Job 112] Started filter /usr/lib/cups/filter/bannertopdf (PID 16674)
D [22/Oct/2018:14:18:33 +0200] [Job 112] Started filter /usr/lib/cups/filter/pdftopdf (PID 16675)
D [22/Oct/2018:14:18:33 +0200] [Job 112] Started filter /usr/lib/cups/filter/foomatic-rip-hplip (PID 16676)
D [22/Oct/2018:14:18:33 +0200] [Job 112] Started backend /usr/lib/cups/backend/socket (PID 16677)
D [22/Oct/2018:14:18:33 +0200] [Job 112] pdftopdf: Last filter determined by the PPD: foomatic-rip-hplip; FINAL_CONTENT_TYPE: application/vnd.cups-pdf => pdftopdf will not log pages in page_log.
D [22/Oct/2018:14:18:33 +0200] [Job 112] STATE: +connecting-to-device
D [22/Oct/2018:14:18:33 +0200] [Job 112] Looking up \"192.168.9.19\"...
D [22/Oct/2018:14:18:33 +0200] [Job 112] STATE: -connecting-to-device
D [22/Oct/2018:14:18:33 +0200] [Job 112] 192.168.9.19=192.168.9.19
D [22/Oct/2018:14:18:33 +0200] [Job 112] Calling FindDeviceById(cups-HP-LaserJet-P4014)
D [22/Oct/2018:14:18:33 +0200] [Job 112] Found device /org/freedesktop/ColorManager/devices/cups_HP_LaserJet_P4014
D [22/Oct/2018:14:18:33 +0200] [Job 112] Calling org.freedesktop.ColorManager.Device.Get(ProfilingInhibitors)
D [22/Oct/2018:14:18:33 +0200] [Job 112] \'CM Color Calibration\' Mode in SPOOLER-LESS: Off
D [22/Oct/2018:14:18:33 +0200] [Job 112] Getting input from file 
D [22/Oct/2018:14:18:33 +0200] [Job 112] foomatic-rip version 1.20.2 running...
D [22/Oct/2018:14:18:33 +0200] [Job 112] Parsing PPD file ...
D [22/Oct/2018:14:18:33 +0200] [Job 112] Added option ColorSpace
D [22/Oct/2018:14:18:33 +0200] [Job 112] Added option Resolution
D [22/Oct/2018:14:18:33 +0200] [Job 112] Added option PageSize
D [22/Oct/2018:14:18:33 +0200] [Job 112] Added option Model
D [22/Oct/2018:14:18:33 +0200] [Job 112] Added option PrintoutMode
D [22/Oct/2018:14:18:33 +0200] [Job 112] Added option InputSlot
D [22/Oct/2018:14:18:33 +0200] [Job 112] PDF template file doesn\'t have form. It\'s okay.
D [22/Oct/2018:14:18:33 +0200] [Job 112] Added option Duplex
D [22/Oct/2018:14:18:33 +0200] [Job 112] Added option Quality
D [22/Oct/2018:14:18:33 +0200] [Job 112] Added option ImageableArea
D [22/Oct/2018:14:18:33 +0200] [Job 112] Added option PaperDimension
D [22/Oct/2018:14:18:33 +0200] [Job 112] Added option Font
D [22/Oct/2018:14:18:33 +0200] [Job 112] Parameter Summary
D [22/Oct/2018:14:18:33 +0200] [Job 112] -----------------
D [22/Oct/2018:14:18:33 +0200] [Job 112] Spooler: cups
D [22/Oct/2018:14:18:33 +0200] [Job 112] Printer: HP-LaserJet-P4014
D [22/Oct/2018:14:18:33 +0200] [Job 112] Shell: /bin/sh
D [22/Oct/2018:14:18:33 +0200] [Job 112] PPD file: /etc/cups/ppd/HP-LaserJet-P4014.ppd
D [22/Oct/2018:14:18:33 +0200] [Job 112] ATTR file: 
D [22/Oct/2018:14:18:33 +0200] [Job 112] Printer model: HP LaserJet p4014 hpijs, 3.17.10
D [22/Oct/2018:14:18:33 +0200] [Job 112] Job title: Test Page
D [22/Oct/2018:14:18:33 +0200] [Job 112] File(s) to be printed:
D [22/Oct/2018:14:18:33 +0200] [Job 112] <STDIN>
D [22/Oct/2018:14:18:33 +0200] [Job 112] Ghostscript extra search path (\'GS_LIB\'): /usr/share/cups/fonts
D [22/Oct/2018:14:18:33 +0200] [Job 112] Printing system options:
D [22/Oct/2018:14:18:33 +0200] [Job 112] Pondering option \'job-uuid=urn:uuid:0626a944-a85c-33ea-6b5d-5ee7f0c3d74c\'
D [22/Oct/2018:14:18:33 +0200] [Job 112] Unknown option job-uuid=urn:uuid:0626a944-a85c-33ea-6b5d-5ee7f0c3d74c.
D [22/Oct/2018:14:18:33 +0200] [Job 112] Pondering option \'job-originating-host-name=localhost\'
D [22/Oct/2018:14:18:33 +0200] [Job 112] Unknown option job-originating-host-name=localhost.
D [22/Oct/2018:14:18:33 +0200] [Job 112] Pondering option \'date-time-at-creation=\'
D [22/Oct/2018:14:18:33 +0200] [Job 112] Unknown option date-time-at-creation=.
D [22/Oct/2018:14:18:33 +0200] [Job 112] Pondering option \'date-time-at-processing=\'
D [22/Oct/2018:14:18:33 +0200] [Job 112] Unknown option date-time-at-processing=.
D [22/Oct/2018:14:18:33 +0200] [Job 112] Pondering option \'time-at-creation=1540210713\'
D [22/Oct/2018:14:18:33 +0200] [Job 112] Unknown option time-at-creation=1540210713.
D [22/Oct/2018:14:18:33 +0200] [Job 112] Pondering option \'time-at-processing=1540210713\'
D [22/Oct/2018:14:18:33 +0200] [Job 112] Unknown option time-at-processing=1540210713.
D [22/Oct/2018:14:18:33 +0200] [Job 112] CM Color Calibration Mode in CUPS: Off
D [22/Oct/2018:14:18:33 +0200] [Job 112] Options from the PPD file:
D [22/Oct/2018:14:18:33 +0200] [Job 112] ================================================
D [22/Oct/2018:14:18:33 +0200] [Job 112] File: <STDIN>
D [22/Oct/2018:14:18:33 +0200] [Job 112] ================================================
D [22/Oct/2018:14:18:33 +0200] [Job 112] PID 16674 (/usr/lib/cups/filter/bannertopdf) exited with no errors.
D [22/Oct/2018:14:18:33 +0200] [Job 112] hrDeviceDesc=\"HP LaserJet P4014\"
D [22/Oct/2018:14:18:33 +0200] [Job 112] Filetype: PDF
D [22/Oct/2018:14:18:33 +0200] [Job 112] Storing temporary files in /tmp
D [22/Oct/2018:14:18:33 +0200] [Job 112] PID 16675 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [22/Oct/2018:14:18:33 +0200] [Job 112] prtMarkerColorantValue.1.1 = \"black\"
D [22/Oct/2018:14:18:33 +0200] [Job 112] ATTR: marker-colors=#000000,none
D [22/Oct/2018:14:18:33 +0200] [Job 112] ATTR: marker-names=\'\"Black Cartridge HP CC364A\"\',\'\"Maintenance Kit HP 110V-CB388A, 220V-CB389A\"\'
D [22/Oct/2018:14:18:33 +0200] [Job 112] ATTR: marker-types=toner-cartridge,fuser
D [22/Oct/2018:14:18:33 +0200] [Job 112] ATTR: marker-levels=100,0
D [22/Oct/2018:14:18:33 +0200] [Job 112] new_supply_state=20, change_state=ffff
D [22/Oct/2018:14:18:33 +0200] [Job 112] STATE: -developer-low-report
D [22/Oct/2018:14:18:33 +0200] [Job 112] STATE: -developer-empty-warning
D [22/Oct/2018:14:18:33 +0200] [Job 112] STATE: -marker-supply-low-report
D [22/Oct/2018:14:18:33 +0200] [Job 112] STATE: -marker-supply-empty-warning
D [22/Oct/2018:14:18:33 +0200] [Job 112] STATE: -opc-near-eol-report
D [22/Oct/2018:14:18:33 +0200] [Job 112] STATE: +opc-life-over-warning
D [22/Oct/2018:14:18:33 +0200] [Job 112] STATE: -toner-low-report
D [22/Oct/2018:14:18:33 +0200] [Job 112] STATE: -toner-empty-warning
D [22/Oct/2018:14:18:33 +0200] [Job 112] STATE: -waste-receptacle-almost-full-report
D [22/Oct/2018:14:18:33 +0200] [Job 112] STATE: -waste-receptacle-full-warning
D [22/Oct/2018:14:18:33 +0200] [Job 112] STATE: -cleaner-life-almost-over-report
D [22/Oct/2018:14:18:33 +0200] [Job 112] STATE: -cleaner-life-over-warning
D [22/Oct/2018:14:18:33 +0200] [Job 112] ./base/gsicc_manage.c:1244: gsicc_open_search(): Could not find default_gray.icc 
D [22/Oct/2018:14:18:33 +0200] [Job 112] | ./base/gsicc_manage.c:2261: gsicc_init_iccmanager(): cannot find default icc profile
D [22/Oct/2018:14:18:33 +0200] [Job 112] ./base/gsicc_manage.c:1244: gsicc_open_search(): Could not find default_gray.icc 
D [22/Oct/2018:14:18:33 +0200] [Job 112] | ./base/gsicc_manage.c:2025: gsicc_set_device_profile(): cannot find device profile
D [22/Oct/2018:14:18:33 +0200] [Job 112] **** Unable to open the initial device, quitting.
D [22/Oct/2018:14:18:33 +0200] [Job 112] new_state=3000, change_state=ffff
D [22/Oct/2018:14:18:33 +0200] [Job 112] STATE: -media-empty-warning
D [22/Oct/2018:14:18:33 +0200] [Job 112] STATE: -door-open-report
D [22/Oct/2018:14:18:33 +0200] [Job 112] STATE: -media-jam-warning
D [22/Oct/2018:14:18:33 +0200] [Job 112] STATE: -input-tray-missing-warning
D [22/Oct/2018:14:18:33 +0200] [Job 112] STATE: -output-tray-missing-warning
D [22/Oct/2018:14:18:33 +0200] [Job 112] STATE: -marker-supply-missing-warning
D [22/Oct/2018:14:18:33 +0200] [Job 112] STATE: -output-area-almost-full-report
D [22/Oct/2018:14:18:33 +0200] [Job 112] STATE: -output-area-full-warning
D [22/Oct/2018:14:18:33 +0200] [Job 112] Process is dying with \"Unable to determine number of pages, page count: -1
D [22/Oct/2018:14:18:33 +0200] [Job 112] \", exit stat 3
D [22/Oct/2018:14:18:33 +0200] [Job 112] Cleaning up...
D [22/Oct/2018:14:18:33 +0200] [Job 112] PID 16676 (/usr/lib/cups/filter/foomatic-rip-hplip) stopped with status 3.
D [22/Oct/2018:14:18:33 +0200] [Job 112] Hint: Try setting the LogLevel to "debug" to find out more.
D [22/Oct/2018:14:18:33 +0200] [Job 112] backendWaitLoop(snmp_fd=5, addr=0x55aaa0e3f148, side_cb=0x55aa9f47a360)
D [22/Oct/2018:14:18:33 +0200] [Job 112] PID 16677 (/usr/lib/cups/backend/socket) exited with no errors.
D [22/Oct/2018:14:18:33 +0200] [Job 112] End of messages
D [22/Oct/2018:14:18:33 +0200] [Job 112] printer-state=3(idle)
D [22/Oct/2018:14:18:33 +0200] [Job 112] printer-state-message="Filter failed"
D [22/Oct/2018:14:18:33 +0200] [Job 112] printer-state-reasons=opc-life-over-warning

```

```

sudo cat /etc/cups/cupsd.conf
```
```

#
# Configuration file for the CUPS scheduler.  See "man cupsd.conf" for a
# complete description of this file.
#

# Log general information in error_log - change "warn" to "debug"
# for troubleshooting...
LogLevel warn
PageLogFormat

# Deactivate CUPS' internal logrotating, as we provide a better one, especially
# LogLevel debug2 gets usable now
MaxLogSize 0

# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing Off
BrowseLocalProtocols dnssd

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Web interface setting...
WebInterface Yes

# Restrict access to the server...
<Location />
  Order allow,deny
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
</Location>

# Restrict access to log files...
<Location /admin/log>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job/subscription privacy...
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default

  # Job-related operations must be done by the owner or an administrator...
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    Order deny,allow
  </Limit>

  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

# Set the authenticated printer/job policies...
<Policy authenticated>
  # Job/subscription privacy...
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default

  # Job-related operations must be done by the owner or an administrator...
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    AuthType Default
    Order deny,allow
  </Limit>

  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
```

And finally

```
sudo cat /etc/cups/printers.conf
```

gives me

```
# Printer configuration file for CUPS v2.2.7
# Written by cupsd
# DO NOT EDIT THIS FILE WHEN CUPSD IS RUNNING
<DefaultPrinter HP-LaserJet-P4014>
UUID urn:uuid:c02d93cd-f5e0-39fa-62d8-09ef042d0663
Info HP LaserJet P4014
MakeModel HP LaserJet p4014 hpijs, 3.17.10
DeviceURI socket://192.168.9.19
State Idle
StateTime 1540210713
ConfigTime 1539876594
Reason opc-life-over-warning
Type 8425500
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy abort-job
Attribute marker-colors \#000000,none
Attribute marker-levels 100,0
Attribute marker-names Black Cartridge HP CC364A,Maintenance Kit HP 110V-CB388A, 220V-CB389A
Attribute marker-types toner-cartridge,fuser
Attribute marker-change-time 1540210713
</DefaultPrinter>
```


I do not understand the problem, because everybody in the office is available to print, except for me.

---

### Post by dino99 on 2018-10-22
There is a icc profile error at the beginning, but might not be blamed for that issue i think (not sure anyway)

./base/gsicc_manage.c:2261: gsicc_init_iccmanager(): cannot find default icc profile
[https://askubuntu.com/questions/1080720/printer-filter-failed](https://askubuntu.com/questions/1080720/printer-filter-failed)

Hint: Try setting the LogLevel to "debug" to find out more.

[https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

---

