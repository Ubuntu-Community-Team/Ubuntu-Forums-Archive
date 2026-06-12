---
title: "HP DeskJet 722C not printing - fresh Dapper install"
date: 2006-06-18
forum: Hardware &amp; Laptops
---

### Post by klytu on 2006-06-18
I have a HP DeskJet 722C parallel port printer. It is connected to a Canon FB620P parallel port scanner which is connected to the only parallel port my computer has. 

On a separate Ubuntu installation on the same computer and different hard drive, both the scanner and printer work OK. This installation started out as Hoary and was upgraded to Breezy. I wanted to try a clean Dapper installation and test it before upgrading this working installation to Dapper.

I haven't been able to get either the scanner or the printer working when I do a clean Dapper installation (I mentioned the scanner because the issue may be related, but I wanted to tackle each issue separately). When I add the HP printer with the new printer wizard it is detected, but when I try to print a test page nothing happens. When I try to print and open the print queue, at first it indicates the job is printing, but then it indicates the job stopped. I have tried removing and reinstalling the HP printer, tried editing /etc/cups/printers.conf to match the  /etc/cups/printers.conf on the working installation, and have looked at various logs but I haven't been able to find any clues as to why the printer is not printing on the new installation.  

I could post any logs that would be necessary to diagnose, but I haven't seen any problems. The only thing that seems odd is that when I do  tail -f /var/log/cups/error_log  I get the following repeated over and over (have to ctrl-z to stop the terminal output):

D [18/Jun/2006:06:45:42 -0400] Get-Printer-Attributes ipp://localhost/printers/D eskJet-720C
D [18/Jun/2006:06:45:42 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successf ul-ok)
D [18/Jun/2006:06:45:47 -0400] cupsdReadClient: 6 POST / HTTP/1.1
D [18/Jun/2006:06:45:47 -0400] cupsdAuthorize: No authentication data provided.
D [18/Jun/2006:06:45:47 -0400] CUPS-Get-Printers
D [18/Jun/2006:06:45:47 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successf ul-ok)
D [18/Jun/2006:06:45:47 -0400] cupsdReadClient: 6 POST / HTTP/1.1
D [18/Jun/2006:06:45:47 -0400] cupsdAuthorize: No authentication data provided.

I don't know if it's normal for that repeated message to keep occurring. Tried installing HP Linux and Imaging Printing System as well.  But it doesn't appear to work with this printer on either this installation or the installation that prints with no difficulty. On the fresh Dapper installation hp-toolbox spits out 

 HP Linux Imaging and Printing System (ver. 0.9.7)
 HP Device Manager ver. 6.0

 Copyright (c) 2003-5 Hewlett-Packard Development Company, LP
 This software comes with ABSOLUTELY NO WARRANTY.
 This is free software, and you are welcome to distribute it
 under certain conditions. See COPYING file for more details.

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Traceback (most recent call last):
  File "/usr/lib/hplip/ui/devmgr4.py", line 820, in ContinueDeviceListRefresh
    self.UpdateDevice()
  File "/usr/lib/hplip/ui/devmgr4.py", line 721, in UpdateDevice
    self.UpdateTabs()
  File "/usr/lib/hplip/ui/devmgr4.py", line 937, in UpdateTabs
    self.UpdateStatusTab()
  File "/usr/lib/hplip/ui/devmgr4.py", line 1030, in UpdateStatusTab
    if d.tech_type in (TECH_TYPE_COLOR_INK, TECH_TYPE_MONO_INK):
AttributeError: 'Device' object has no attribute 'tech_type'

Then the HP Device Manager GUI appears with most setting grayed out. Status tab indicates unsupported printer model.

Don't want to ramble on too much longer. Any suggestions appreciated!

---

### Post by klytu on 2006-06-18
Oddly enough, when I look at the logs of the ***working*** installation there appear to be problems! For example /usr/lib/cups/backend/hp yields:

direct hp:/no_device_found "Unknown" "hp no_device_found"

And  dpkg --list 'hplip*' on the working installation yields:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  hplip          0.9.5-2ubuntu2 HP Linux Printing and Imaging System (hplip)
ii  hplip-base     0.9.5-2ubuntu2 HP Linux Printing and Imaging System - base
ii  hplip-data     0.9.5-2ubuntu2 HP Linux Printing and Imaging - data files
ii  hplip-ppds     0.9.5-2ubuntu2 HP Linux Printing and Imaging - PPD files

Nevertheless, printing works without difficulty. Here is output of tail -f /var/log/cups/error_log from the working installation just before and through the time a print job runs and completes successfully:

D [18/Jun/2006:08:33:46 -0400] AcceptClient: 5 from localhost:631.
D [18/Jun/2006:08:33:46 -0400] ReadClient: 5 POST /printers/DeskJet-722C HTTP/1.1
D [18/Jun/2006:08:33:46 -0400] print_job: auto-typing file...
D [18/Jun/2006:08:33:46 -0400] print_job: request file type is application/postscript.
D [18/Jun/2006:08:33:46 -0400] check_quotas: requesting-user-name = 'jeffry'
D [18/Jun/2006:08:33:46 -0400] print_job: requesting-user-name = 'jeffry'
I [18/Jun/2006:08:33:46 -0400] Adding start banner page "none" to job 32.
I [18/Jun/2006:08:33:46 -0400] Adding end banner page "none" to job 32.
I [18/Jun/2006:08:33:46 -0400] Job 32 queued on 'DeskJet-722C' by 'jeffry'.
D [18/Jun/2006:08:33:46 -0400] Job 32 hold_until = 0
D [18/Jun/2006:08:33:46 -0400] StartJob(32, 0x8096c30)
D [18/Jun/2006:08:33:46 -0400] StartJob() id = 32, file = 0/1
D [18/Jun/2006:08:33:46 -0400] job-sheets=none,none
D [18/Jun/2006:08:33:46 -0400] banner_page = 0
D [18/Jun/2006:08:33:46 -0400] StartJob: argv = "DeskJet-722C","32","jeffry","My HP Printer Stopped Printing - Ubuntu Forums","1","PageSize=A4 PageRegion=Letter EconoFast=On ColorMode=Grayscale","/var/spool/cups/d00032-001"
D [18/Jun/2006:08:33:46 -0400] StartJob: envp[0]="PATH=/usr/lib/cups/filter:/bin:/usr/bin"
D [18/Jun/2006:08:33:46 -0400] StartJob: envp[1]="SOFTWARE=CUPS/1.1"
D [18/Jun/2006:08:33:46 -0400] StartJob: envp[2]="USER=root"
D [18/Jun/2006:08:33:46 -0400] StartJob: envp[3]="CHARSET=utf-8"
D [18/Jun/2006:08:33:46 -0400] StartJob: envp[4]="LANG=en_US"
D [18/Jun/2006:08:33:46 -0400] StartJob: envp[5]="TZ=America/New_York"
D [18/Jun/2006:08:33:46 -0400] StartJob: envp[6]="PPD=/etc/cups/ppd/DeskJet-722C.ppd"
D [18/Jun/2006:08:33:46 -0400] StartJob: envp[7]="CUPS_SERVERROOT=/etc/cups"
D [18/Jun/2006:08:33:46 -0400] StartJob: envp[8]="RIP_MAX_CACHE=8m"
D [18/Jun/2006:08:33:46 -0400] StartJob: envp[9]="TMPDIR=/var/spool/cups/tmp"
D [18/Jun/2006:08:33:46 -0400] StartJob: envp[10]="CONTENT_TYPE=application/postscript"
D [18/Jun/2006:08:33:46 -0400] StartJob: envp[11]="DEVICE_URI=parallel:/dev/lp0"D [18/Jun/2006:08:33:46 -0400] StartJob: envp[12]="PRINTER=DeskJet-722C"
D [18/Jun/2006:08:33:46 -0400] StartJob: envp[13]="CUPS_DATADIR=/usr/share/cups"D [18/Jun/2006:08:33:46 -0400] StartJob: envp[14]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [18/Jun/2006:08:33:46 -0400] StartJob: envp[15]="CUPS_SERVER=localhost"
D [18/Jun/2006:08:33:46 -0400] StartJob: envp[16]="IPP_PORT=631"
D [18/Jun/2006:08:33:46 -0400] StartJob: statusfds = [ 6 7 ]
D [18/Jun/2006:08:33:46 -0400] StartJob: filterfds[1] = [ 8 -1 ]
D [18/Jun/2006:08:33:46 -0400] StartJob: filter = "/usr/lib/cups/filter/pstops"
D [18/Jun/2006:08:33:46 -0400] StartJob: filterfds[0] = [ 9 10 ]
D [18/Jun/2006:08:33:46 -0400] start_process("/usr/lib/cups/filter/pstops", 0xbf9739a0, 0xbf972f18, 8, 10, 7)
I [18/Jun/2006:08:33:46 -0400] Started filter /usr/lib/cups/filter/pstops (PID 8962) for job 32.
D [18/Jun/2006:08:33:46 -0400] StartJob: filter = "/usr/lib/cups/filter/foomatic-rip"
D [18/Jun/2006:08:33:46 -0400] StartJob: filterfds[1] = [ 8 11 ]
D [18/Jun/2006:08:33:46 -0400] start_process("/usr/lib/cups/filter/foomatic-rip", 0xbf9739a0, 0xbf972f18, 9, 11, 7)
I [18/Jun/2006:08:33:46 -0400] Started filter /usr/lib/cups/filter/foomatic-rip (PID 8963) for job 32.
D [18/Jun/2006:08:33:46 -0400] StartJob: backend = "/usr/lib/cups/backend/parallel"
D [18/Jun/2006:08:33:46 -0400] StartJob: filterfds[0] = [ -1 9 ]
D [18/Jun/2006:08:33:46 -0400] start_process("/usr/lib/cups/backend/parallel", 0xbf9739a0, 0xbf972f18, 8, 9, 7)
I [18/Jun/2006:08:33:46 -0400] Started backend /usr/lib/cups/backend/parallel (PID 8964) for job 32.
D [18/Jun/2006:08:33:46 -0400] ProcessIPPRequest: 5 status_code=0
D [18/Jun/2006:08:33:47 -0400] [Job 32] Page = 612x792; 0,0 to 612,792
D [18/Jun/2006:08:33:47 -0400] [Job 32] slowcollate=0, slowduplex=0, sloworder=0D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%BoundingBox: 0 0 612 792
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%HiResBoundingBox: 0 0 612 792
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%Creator: Mozilla PostScript module (rv:1.8.0.1/2006012415)
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%DocumentData: Clean8Bit
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%DocumentPaperSizes: Letter
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%Orientation: Portrait
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%Pages: 1
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%PageOrder: Ascend
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%EndComments
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%BeginProlog
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%EndProlog
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%BeginResource: font Verdana.Regular.0.0.Set0
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%Creator: Mozilla Freetype2 Printing code 2.0
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%Title: Verdana.Regular.0.0.Set0
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%Pages: 0
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%EndComments
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%EndResource
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%BeginResource: font Bitstream_Vera_Serif.Roman.0.0.Set0
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%Creator: Mozilla Freetype2 Printing code 2.0
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%Title: Bitstream_Vera_Serif.Roman.0.0.Set0
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%Pages: 0
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%EndComments
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%EndResource
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%BeginResource: font Bitstream_Vera_Sans.Roman.0.0.Set0
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%Creator: Mozilla Freetype2 Printing code 2.0
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%Title: Bitstream_Vera_Sans.Roman.0.0.Set0
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%Pages: 0
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%EndComments
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%EndResource
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%BeginResource: font Verdana.Bold.0.0.Set0
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%Creator: Mozilla Freetype2 Printing code 2.0
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%Title: Verdana.Bold.0.0.Set0
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%Pages: 0
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%EndComments
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%EndResource
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%BeginResource: font Arial.Bold.0.0.Set0
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%Creator: Mozilla Freetype2 Printing code 2.0
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%Title: Arial.Bold.0.0.Set0
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%Pages: 0
D [18/Jun/2006:08:33:47 -0400] [Job 32] 0 %%EndComments
D [18/Jun/2006:08:33:47 -0400] [Job 32] perl: warning: Setting locale failed.
D [18/Jun/2006:08:33:47 -0400] [Job 32] perl: warning: Please check that your locale settings:
D [18/Jun/2006:08:33:47 -0400] [Job 32] LANGUAGE = (unset),
D [18/Jun/2006:08:33:47 -0400] [Job 32] LC_ALL = (unset),
D [18/Jun/2006:08:33:47 -0400] [Job 32] LANG = "en_US"
D [18/Jun/2006:08:33:47 -0400] [Job 32] are supported and installed on your system.
D [18/Jun/2006:08:33:47 -0400] [Job 32] perl: warning: Falling back to the standard locale ("C").
D [18/Jun/2006:08:33:47 -0400] [Job 32] foomatic-rip version $Revision: 3.43.2.11 $ running...
D [18/Jun/2006:08:33:47 -0400] [Job 32] Parsing PPD file ...
D [18/Jun/2006:08:33:47 -0400] [Job 32] *cupsFilter: "application/vnd.cups-postscript 0 foomatic-rip"
D [18/Jun/2006:08:33:47 -0400] [Job 32] Added option ColorSpace
D [18/Jun/2006:08:33:47 -0400] [Job 32] Added option Resolution
D [18/Jun/2006:08:33:47 -0400] [Job 32] Added option PageSize
D [18/Jun/2006:08:33:47 -0400] [Job 32] Added option PageRegion
D [18/Jun/2006:08:33:47 -0400] [Job 32] Added option ImageableArea
D [18/Jun/2006:08:33:47 -0400] [Job 32] Added option PaperDimension
D [18/Jun/2006:08:33:47 -0400] [Job 32] Added option EconoFast
D [18/Jun/2006:08:33:47 -0400] [Job 32] Added option ColorMode
D [18/Jun/2006:08:33:47 -0400] [Job 32] Added option Dither
D [18/Jun/2006:08:33:47 -0400] [Job 32] Added option Bidirectional
D [18/Jun/2006:08:33:48 -0400] [Job 32] Added option Blackness
D [18/Jun/2006:08:33:48 -0400] [Job 32] Added option BottomMargin
D [18/Jun/2006:08:33:48 -0400] [Job 32] Added option LeftMargin
D [18/Jun/2006:08:33:48 -0400] [Job 32] Added option RightMargin
D [18/Jun/2006:08:33:48 -0400] [Job 32] Added option TopMargin
D [18/Jun/2006:08:33:48 -0400] [Job 32] Added option XOffset
D [18/Jun/2006:08:33:48 -0400] [Job 32] Added option YOffset
D [18/Jun/2006:08:33:48 -0400] [Job 32] Added option Model
D [18/Jun/2006:08:33:48 -0400] [Job 32] Added option GammaFile
D [18/Jun/2006:08:33:48 -0400] [Job 32] Added option pnmFormat
D [18/Jun/2006:08:33:48 -0400] [Job 32] Added option Font
D [18/Jun/2006:08:33:48 -0400] [Job 32]
D [18/Jun/2006:08:33:48 -0400] [Job 32] Parameter Summary
D [18/Jun/2006:08:33:48 -0400] [Job 32] -----------------
D [18/Jun/2006:08:33:48 -0400] [Job 32]
D [18/Jun/2006:08:33:48 -0400] [Job 32] Spooler: cups
D [18/Jun/2006:08:33:48 -0400] [Job 32] Printer: DeskJet-722C
D [18/Jun/2006:08:33:48 -0400] [Job 32] PPD file: /etc/cups/ppd/DeskJet-722C.ppdD [18/Jun/2006:08:33:48 -0400] [Job 32] Printer model: HP DeskJet 722C Foomatic/pnm2ppa (recommended)
D [18/Jun/2006:08:33:48 -0400] [Job 32] Job title: My HP Printer Stopped Printing - Ubuntu Forums
D [18/Jun/2006:08:33:48 -0400] [Job 32] File(s) to be printed:
D [18/Jun/2006:08:33:48 -0400] [Job 32] <STDIN>
D [18/Jun/2006:08:33:48 -0400] [Job 32]
D [18/Jun/2006:08:33:48 -0400] [Job 32] GhostScript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [18/Jun/2006:08:33:48 -0400] [Job 32] Pondering option 'PageSize=A4'
D [18/Jun/2006:08:33:48 -0400] [Job 32] Pondering option 'PageRegion=Letter'
D [18/Jun/2006:08:33:48 -0400] [Job 32] Pondering option 'EconoFast=On'
D [18/Jun/2006:08:33:48 -0400] [Job 32] Pondering option 'ColorMode=Grayscale'
D [18/Jun/2006:08:33:48 -0400] [Job 32]
D [18/Jun/2006:08:33:48 -0400] [Job 32] ================================================
D [18/Jun/2006:08:33:48 -0400] [Job 32]
D [18/Jun/2006:08:33:48 -0400] [Job 32] File: <STDIN>
D [18/Jun/2006:08:33:48 -0400] [Job 32]
D [18/Jun/2006:08:33:48 -0400] [Job 32] ================================================
D [18/Jun/2006:08:33:48 -0400] [Job 32]
D [18/Jun/2006:08:33:48 -0400] [Job 32] Reading PostScript input ...
D [18/Jun/2006:08:33:48 -0400] [Job 32] --> This document is DSC-conforming!
D [18/Jun/2006:08:33:48 -0400] [Job 32]
D [18/Jun/2006:08:33:48 -0400] [Job 32] -----------
D [18/Jun/2006:08:33:48 -0400] [Job 32] Found: %%BeginProlog
D [18/Jun/2006:08:33:48 -0400] [Job 32] Found: %%EndProlog
D [18/Jun/2006:08:33:48 -0400] [Job 32] 0 %%EndResource
D [18/Jun/2006:08:33:48 -0400] [Job 32] 0 %%Page: 1 1
D [18/Jun/2006:08:33:48 -0400] [Job 32] 0 %%Page: 1 1
D [18/Jun/2006:08:33:48 -0400] [Job 32] pw = 612.0, pl = 792.0
D [18/Jun/2006:08:33:48 -0400] [Job 32] PageLeft = 0.0, PageRight = 612.0
D [18/Jun/2006:08:33:48 -0400] [Job 32] PageTop = 792.0, PageBottom = 0.0
D [18/Jun/2006:08:33:48 -0400] [Job 32] PageWidth = 612.0, PageLength = 792.0
D [18/Jun/2006:08:33:48 -0400] [Job 32] 0 %%BeginPageSetup
D [18/Jun/2006:08:33:48 -0400] [Job 32] 0 %%EndPageSetup
D [18/Jun/2006:08:33:48 -0400] ReadClient: 4 POST / HTTP/1.1
D [18/Jun/2006:08:33:48 -0400] ProcessIPPRequest: 4 status_code=0
D [18/Jun/2006:08:33:48 -0400] [Job 32] This job seems not to be DSC-conforming, DSC-comment for next section not found, stopping to parse the rest, passing it directly to the renderer.
D [18/Jun/2006:08:33:48 -0400] [Job 32] "Setup" section is missing, inserting it.
D [18/Jun/2006:08:33:48 -0400] [Job 32] Inserting PostScript code for CUPS' page accounting
D [18/Jun/2006:08:33:48 -0400] [Job 32] "PageSetup" section is missing, inserting it.
D [18/Jun/2006:08:33:48 -0400] [Job 32] Inserting option code into "PageSetup" section.
D [18/Jun/2006:08:33:48 -0400] ReadClient: 4 POST / HTTP/1.1
D [18/Jun/2006:08:33:48 -0400] ProcessIPPRequest: 4 status_code=1
D [18/Jun/2006:08:33:48 -0400] [Job 32] Stopped parsing the PostScript data, sending rest directly to renderer.
D [18/Jun/2006:08:33:48 -0400] [Job 32]
D [18/Jun/2006:08:33:48 -0400] [Job 32] Starting renderer
D [18/Jun/2006:08:33:48 -0400] [Job 32] JCL: <job data>
D [18/Jun/2006:08:33:48 -0400] [Job 32]
D [18/Jun/2006:08:33:48 -0400] [Job 32] renderer PID kid4=8967
D [18/Jun/2006:08:33:48 -0400] [Job 32] renderer command: gs -q -dNOPAUSE -dPARANOIDSAFER -dBATCH -r600 -sDEVICE=ppmraw  -sOutputFile=- - | pnm2ppa -v 722  --bw --eco -B 2 -t 10 -b 150 -l 10 -r 10 -x 160 -y 50 -i - -o -
D [18/Jun/2006:08:33:48 -0400] [Job 32] perl: warning: Setting locale failed.
D [18/Jun/2006:08:33:48 -0400] [Job 32] perl: warning: Please check that your locale settings:
D [18/Jun/2006:08:33:48 -0400] [Job 32] LANGUAGE = (unset),
D [18/Jun/2006:08:33:48 -0400] [Job 32] LC_ALL = (unset),
D [18/Jun/2006:08:33:48 -0400] [Job 32] LANG = "en_US"
D [18/Jun/2006:08:33:48 -0400] [Job 32] are supported and installed on your system.
D [18/Jun/2006:08:33:48 -0400] [Job 32] perl: warning: Falling back to the standard locale ("C").
D [18/Jun/2006:08:33:48 -0400] [Job 32] foomatic-gswrapper: gs '-dNOPAUSE' '-dPARANOIDSAFER' '-dBATCH' '-r600' '-sDEVICE=ppmraw' '-sOutputFile=/dev/fd/3' '/dev/fd/0' 3>&1 1>&2
D [18/Jun/2006:08:33:49 -0400] [Job 32] ESP Ghostscript 7.07 (2003-07-12)
D [18/Jun/2006:08:33:49 -0400] [Job 32] Copyright 2003 artofcode LLC and Easy Software Products, all rights reserved.
D [18/Jun/2006:08:33:49 -0400] [Job 32] This software comes with NO WARRANTY: see the file PUBLIC for details.
D [18/Jun/2006:08:33:50 -0400] [Job 32] 0 %%Trailer
D [18/Jun/2006:08:33:50 -0400] [Job 32] Saw Trailer!
D [18/Jun/2006:08:33:50 -0400] [Job 32] Saw EOF!
D [18/Jun/2006:08:33:50 -0400] [Job 32]
D [18/Jun/2006:08:33:50 -0400] [Job 32] Closing renderer
D [18/Jun/2006:08:33:53 -0400] ReadClient: 4 POST / HTTP/1.1
D [18/Jun/2006:08:33:53 -0400] ProcessIPPRequest: 4 status_code=0
D [18/Jun/2006:08:33:53 -0400] ReadClient: 4 POST / HTTP/1.1
D [18/Jun/2006:08:33:53 -0400] ProcessIPPRequest: 4 status_code=1
D [18/Jun/2006:08:33:58 -0400] ReadClient: 4 POST / HTTP/1.1
D [18/Jun/2006:08:33:58 -0400] ProcessIPPRequest: 4 status_code=0
D [18/Jun/2006:08:33:58 -0400] ReadClient: 4 POST / HTTP/1.1
D [18/Jun/2006:08:33:58 -0400] ProcessIPPRequest: 4 status_code=1
D [18/Jun/2006:08:34:01 -0400] [Job 32] tail process done writing data to STDOUTD [18/Jun/2006:08:34:01 -0400] [Job 32] KID4 finished
D [18/Jun/2006:08:34:01 -0400] [Job 32] KID3 finished
D [18/Jun/2006:08:34:01 -0400] [Job 32] KID4 exited with status 0
D [18/Jun/2006:08:34:01 -0400] [Job 32] KID3 exited with status 0
D [18/Jun/2006:08:34:01 -0400] [Job 32] Renderer exit stat: 0
D [18/Jun/2006:08:34:01 -0400] [Job 32] Renderer process finished
D [18/Jun/2006:08:34:01 -0400] [Job 32]
D [18/Jun/2006:08:34:01 -0400] [Job 32] Closing foomatic-rip.
D [18/Jun/2006:08:34:03 -0400] ReadClient: 4 POST / HTTP/1.1
D [18/Jun/2006:08:34:03 -0400] ProcessIPPRequest: 4 status_code=0
D [18/Jun/2006:08:34:03 -0400] ReadClient: 4 POST / HTTP/1.1
D [18/Jun/2006:08:34:03 -0400] ProcessIPPRequest: 4 status_code=1
D [18/Jun/2006:08:34:08 -0400] ReadClient: 4 POST / HTTP/1.1
D [18/Jun/2006:08:34:08 -0400] ProcessIPPRequest: 4 status_code=0
D [18/Jun/2006:08:34:08 -0400] ReadClient: 4 POST / HTTP/1.1
D [18/Jun/2006:08:34:08 -0400] ProcessIPPRequest: 4 status_code=1
D [18/Jun/2006:08:34:13 -0400] ReadClient: 4 POST / HTTP/1.1
D [18/Jun/2006:08:34:13 -0400] ProcessIPPRequest: 4 status_code=0
D [18/Jun/2006:08:34:13 -0400] ReadClient: 4 POST / HTTP/1.1
D [18/Jun/2006:08:34:13 -0400] ProcessIPPRequest: 4 status_code=1
D [18/Jun/2006:08:34:18 -0400] ReadClient: 4 POST / HTTP/1.1
D [18/Jun/2006:08:34:18 -0400] ProcessIPPRequest: 4 status_code=0
D [18/Jun/2006:08:34:18 -0400] ReadClient: 4 POST / HTTP/1.1
D [18/Jun/2006:08:34:18 -0400] ProcessIPPRequest: 4 status_code=1
D [18/Jun/2006:08:34:23 -0400] ReadClient: 4 POST / HTTP/1.1
D [18/Jun/2006:08:34:23 -0400] ProcessIPPRequest: 4 status_code=0
D [18/Jun/2006:08:34:23 -0400] ReadClient: 4 POST / HTTP/1.1
D [18/Jun/2006:08:34:23 -0400] ProcessIPPRequest: 4 status_code=1
D [18/Jun/2006:08:34:23 -0400] UpdateJob: job 32, file 0 is complete.
D [18/Jun/2006:08:34:23 -0400] CancelJob: id = 32
D [18/Jun/2006:08:34:23 -0400] StopJob: id = 32, force = 0
D [18/Jun/2006:08:34:23 -0400] StopJob: printer state is 3
D [18/Jun/2006:08:34:28 -0400] ReadClient: 4 POST / HTTP/1.1
D [18/Jun/2006:08:34:28 -0400] ProcessIPPRequest: 4 status_code=0
D [18/Jun/2006:08:34:28 -0400] ReadClient: 4 POST / HTTP/1.1
D [18/Jun/2006:08:34:28 -0400] ProcessIPPRequest: 4 status_code=1
D [18/Jun/2006:08:34:33 -0400] ReadClient: 4 POST / HTTP/1.1
D [18/Jun/2006:08:34:33 -0400] ProcessIPPRequest: 4 status_code=0
D [18/Jun/2006:08:34:33 -0400] ReadClient: 4 POST / HTTP/1.1
D [18/Jun/2006:08:34:33 -0400] ProcessIPPRequest: 4 status_code=1
D [18/Jun/2006:08:34:38 -0400] ReadClient: 4 POST / HTTP/1.1
D [18/Jun/2006:08:34:38 -0400] ProcessIPPRequest: 4 status_code=0
D [18/Jun/2006:08:34:38 -0400] ReadClient: 4 POST / HTTP/1.1
D [18/Jun/2006:08:34:38 -0400] ProcessIPPRequest: 4 status_code=1

[1]+  Stopped                 tail -f /var/log/cups/error_log

---

### Post by klytu on 2006-06-18
OK. A closer look at  tail -f /var/log/cups/error_log from the fresh Dapper installation after a failed print shows a problem here:


D [18/Jun/2006:10:04:11 -0400] Get-Printer-Attributes ipp://localhost/printers/DeskJet-720C
D [18/Jun/2006:10:04:11 -0400] cupsdProcessIPPRequest: 6 status_code=0 (successful-ok)
D [18/Jun/2006:10:04:12 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [18/Jun/2006:10:04:12 -0400] cupsdAuthorize: No authentication data provided.
D [18/Jun/2006:10:04:12 -0400] CUPS-Get-Printers
D [18/Jun/2006:10:04:12 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [18/Jun/2006:10:04:12 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [18/Jun/2006:10:04:12 -0400] cupsdAuthorize: No authentication data provided.
D [18/Jun/2006:10:04:12 -0400] Get-Printer-Attributes ipp://localhost/printers/DeskJet-720C
D [18/Jun/2006:10:04:12 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
E [18/Jun/2006:10:04:13 -0400] [Job 22] /ioerror in --.outputpage--
D [18/Jun/2006:10:04:13 -0400] [Job 22] Operand stack:
D [18/Jun/2006:10:04:13 -0400] [Job 22] 1   true
D [18/Jun/2006:10:04:13 -0400] [Job 22] Execution stack:
D [18/Jun/2006:10:04:13 -0400] [Job 22] %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1   3   %oparray_pop   1   3   %oparray_pop   1   3   %oparray_pop   1   3   %oparray_pop  .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   0   4   %oparray_pop   --nostringval--   --nostringval--
D [18/Jun/2006:10:04:13 -0400] [Job 22] Dictionary stack:
D [18/Jun/2006:10:04:13 -0400] [Job 22] --dict:1123/1686(ro)(G)--   --dict:0/20(G)--   --dict:84/200(L)--   --dict:0/10(L)--
D [18/Jun/2006:10:04:13 -0400] [Job 22] Current allocation mode is local
D [18/Jun/2006:10:04:13 -0400] [Job 22] Last OS error: 32
D [18/Jun/2006:10:04:13 -0400] [Job 22] ESP Ghostscript 815.02: Unrecoverable error, exit code 1
D [18/Jun/2006:10:04:13 -0400] [Job 22] renderer return value: 1
D [18/Jun/2006:10:04:13 -0400] [Job 22] renderer received signal: 1
D [18/Jun/2006:10:04:13 -0400] [Job 22] Process dying with "Possible error on renderer command line or PostScript error. Check options.", exit stat: 3
D [18/Jun/2006:10:04:13 -0400] [Job 22] error: Illegal seek (29)
D [18/Jun/2006:10:04:13 -0400] [Job 22] Possible error on renderer command line or PostScript error. Check options.
D [18/Jun/2006:10:04:13 -0400] [Job 22] KID3 exited with status 3
D [18/Jun/2006:10:04:13 -0400] [Job 22] Renderer exit stat: 3
D [18/Jun/2006:10:04:13 -0400] [Job 22] Renderer process finished
D [18/Jun/2006:10:04:13 -0400] [Job 22] Killing process 6675 (KID3)
D [18/Jun/2006:10:04:13 -0400] [Job 22] Process dying with "Error closing renderer", exit stat: 3
D [18/Jun/2006:10:04:13 -0400] [Job 22] error: Bad file descriptor (9)
D [18/Jun/2006:10:04:13 -0400] [Job 22] Error closing renderer
E [18/Jun/2006:10:04:13 -0400] PID 6669 (/usr/lib/cups/filter/foomatic-rip) stopped with status 3!
D [18/Jun/2006:10:04:13 -0400] cupsdReadClient: 10 POST / HTTP/1.1
D [18/Jun/2006:10:04:13 -0400] cupsdAuthorize: No authentication data provided.
D [18/Jun/2006:10:04:13 -0400] Get-Jobs ipp://localhost/jobs
D [18/Jun/2006:10:04:13 -0400] cupsdProcessIPPRequest: 10 status_code=0 (successful-ok)


Looks like an error in the Ghostscript renderer? Any suggestions?

---

### Post by klytu on 2006-06-23
Solved problem by suggestion in this thread:

[http://ubuntuforums.org/showthread.php?t=64876](http://ubuntuforums.org/showthread.php?t=64876)

sudo gedit /etc/pnm2ppa.conf

In the section beginning with version, changed from this:

version  
#version  710 # 710, 712, 722 also acceptable
#version  820
#version 1000

to this:

#version  
version  722	
#version  820
#version 1000

Saved file and now can print normally. 

This situation was quite frustrating, but led me to learn a lot about how CUPS works, about how PostScript files are generated, and about how GhostScript "rasterizes" PostScript files before sending them to the HP parallel printers. This was all very interesting and informative, but had nothing to do with why this printer wasn't working. On my current working set up I never had to edit pnm2ppa.conf. This should probably be noted in a "HowTo" somewhere for future reference.

---

