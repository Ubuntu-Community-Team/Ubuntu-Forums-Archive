---
title: "Printer installed but not working - error log attached"
date: 2011-08-14
forum: Hardware
---

### Post by Proxmty on 2011-08-14
I will be so grateful if somebody can interpret this error log file, just any information on what things mean in it will hopefully really help me, even if you can't directly resolve the issue.

The printer is a Canon MX350 and the drivers are installed seemingly fine. Mysteriously, it is known to print every now and then (about 1 in 50 attempts) I can do it and it works, then change nothing, do it again and it doesn't and doesn't and I never know when it will suddenly work again. Anyway, I have the error log from my most recent attempt and would really, really appreciate your feedback, whatever you can say about it to me will be useful, believe me....

I have trouble attaching files to these threads so pasted below...

E [14/Aug/2011:23:26:19 +0100] [Job 110] error occurred while printing
D [14/Aug/2011:23:26:39 +0100] [Job 110] The following messages were recorded from 23:26:12 to 23:26:39
D [14/Aug/2011:23:26:39 +0100] [Job 110] Adding start banner page "none".
D [14/Aug/2011:23:26:39 +0100] [Job 110] Adding end banner page "none".
D [14/Aug/2011:23:26:39 +0100] [Job 110] File of type application/postscript queued by "peter".
D [14/Aug/2011:23:26:39 +0100] [Job 110] hold_until=0
D [14/Aug/2011:23:26:39 +0100] [Job 110] Queued on "Canon-MX350-2" by "peter".
D [14/Aug/2011:23:26:39 +0100] [Job 110] job-sheets=none,none
D [14/Aug/2011:23:26:39 +0100] [Job 110] argv[0]="Canon-MX350-2"
D [14/Aug/2011:23:26:39 +0100] [Job 110] argv[1]="110"
D [14/Aug/2011:23:26:39 +0100] [Job 110] argv[2]="peter"
D [14/Aug/2011:23:26:39 +0100] [Job 110] argv[3]="Test Page"
D [14/Aug/2011:23:26:39 +0100] [Job 110] argv[4]="1"
D [14/Aug/2011:23:26:39 +0100] [Job 110] argv[5]="job-uuid=urn:uuid:282a716d-8a91-349f-41af-2d6bac61e6c2 job-originating-host-name=localhost time-at-creation=1313360772 time-at-processing=1313360772 AP_D_InputSlot="
D [14/Aug/2011:23:26:39 +0100] [Job 110] argv[6]="/var/spool/cups/d00110-001"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[8]="HOME=/var/spool/cups/tmp"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[10]="SERVER_ADMIN=root@ubuntu"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[11]="SOFTWARE=CUPS/1.4.6"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[13]="USER=root"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[16]="IPP_PORT=631"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[17]="CHARSET=utf-8"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[18]="LANG=en_GB.UTF-8"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[19]="PPD=/etc/cups/ppd/Canon-MX350-2.ppd"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[20]="RIP_MAX_CACHE=auto"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[21]="CONTENT_TYPE=application/postscript"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[22]="DEVICE_URI=cnijnet:/00-1E-8F-E2-7F-92"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[23]="PRINTER_INFO=Canon MX350"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[24]="PRINTER_LOCATION="
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[25]="PRINTER=Canon-MX350-2"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[26]="CUPS_FILETYPE=document"
D [14/Aug/2011:23:26:39 +0100] [Job 110] envp[27]="FINAL_CONTENT_TYPE=printer/Canon-MX350-2"
D [14/Aug/2011:23:26:39 +0100] [Job 110] Started filter /usr/lib/cups/filter/pstops (PID 4349)
D [14/Aug/2011:23:26:39 +0100] [Job 110] Started filter /usr/lib/cups/filter/pstocanonij (PID 4350)
D [14/Aug/2011:23:26:39 +0100] [Job 110] Started backend /usr/lib/cups/backend/cnijnet (PID 4351)
D [14/Aug/2011:23:26:39 +0100] [Job 110] Page = 595x842; 10,14 to 586,833
D [14/Aug/2011:23:26:39 +0100] [Job 110] slow_collate=0, slow_duplex=0, slow_order=0
D [14/Aug/2011:23:26:39 +0100] [Job 110] Before copy_comments - %!PS-Adobe-3.0
D [14/Aug/2011:23:26:39 +0100] [Job 110] %!PS-Adobe-3.0
D [14/Aug/2011:23:26:39 +0100] [Job 110] %%Creator: cairo 1.10.2 ([http://cairographics.org](http://cairographics.org))
D [14/Aug/2011:23:26:39 +0100] [Job 110] %%CreationDate: Thu May 19 11:12:44 2011
D [14/Aug/2011:23:26:39 +0100] [Job 110] %%Pages: 1
D [14/Aug/2011:23:26:39 +0100] [Job 110] %%BoundingBox: 0 0 586 833
D [14/Aug/2011:23:26:39 +0100] [Job 110] %%DocumentData: Clean7Bit
D [14/Aug/2011:23:26:39 +0100] [Job 110] %%LanguageLevel: 2
D [14/Aug/2011:23:26:39 +0100] [Job 110] %%DocumentMedia: 207x294mm 586 833 0 () ()
D [14/Aug/2011:23:26:39 +0100] [Job 110] %%EndComments
D [14/Aug/2011:23:26:39 +0100] [Job 110] Before copy_prolog - %%BeginProlog
D [14/Aug/2011:23:26:39 +0100] [Job 110] Before copy_setup - %!PS-AdobeFont-1.0: NimbusSanL-Regu 1.06
D [14/Aug/2011:23:26:39 +0100] [Job 110] 
D [14/Aug/2011:23:26:39 +0100] [Job 110] pstocanonij start.
D [14/Aug/2011:23:26:39 +0100] [Job 110] Before page loop - %%Page: 1 1
D [14/Aug/2011:23:26:39 +0100] [Job 110] Copying page 1...
D [14/Aug/2011:23:26:39 +0100] [Job 110] pagew = 576.0, pagel = 819.2
D [14/Aug/2011:23:26:39 +0100] [Job 110] bboxx = 0, bboxy = 0, bboxw = 595, bboxl = 842
D [14/Aug/2011:23:26:39 +0100] [Job 110] PageLeft = 9.6, PageRight = 585.6
D [14/Aug/2011:23:26:39 +0100] [Job 110] PageTop = 833.4, PageBottom = 14.2
D [14/Aug/2011:23:26:39 +0100] [Job 110] PageWidth = 595.0, PageLength = 842.0
D [14/Aug/2011:23:26:39 +0100] [Job 110] Wrote 1 pages...
D [14/Aug/2011:23:26:39 +0100] [Job 110] 
D [14/Aug/2011:23:26:39 +0100] [Job 110] device_uri=(cnijnet:/00-1E-8F-E2-7F-92)
D [14/Aug/2011:23:26:39 +0100] [Job 110] p_ppd->model_number=(366)
D [14/Aug/2011:23:26:39 +0100] [Job 110] #  p_size->name=A4 , p_size_default->name = A4 #
D [14/Aug/2011:23:26:39 +0100] [Job 110] ### num_opt(lpr optins) = 5 ###
D [14/Aug/2011:23:26:39 +0100] [Job 110] 
D [14/Aug/2011:23:26:39 +0100] [Job 110] # ppdPageSize width=595.000000 height=842.000000 ###
D [14/Aug/2011:23:26:39 +0100] [Job 110] 
D [14/Aug/2011:23:26:39 +0100] [Job 110] (3)Make cif options : p_choice found in p_ppd (p_choice:A4 210.0x297.0mm /  A4)
D [14/Aug/2011:23:26:39 +0100] [Job 110] (3)Make cif options : choice=A4(p_table->ppd_key=PageSize)
D [14/Aug/2011:23:26:39 +0100] [Job 110] (3)Make cif options : p_choice found in p_ppd (p_choice:Plain Paper /  plain)
D [14/Aug/2011:23:26:39 +0100] [Job 110] (3)Make cif options : choice=plain(p_table->ppd_key=MediaType)
D [14/Aug/2011:23:26:39 +0100] [Job 110] (3)Make cif options : InputSlot is not found in p_ppd
D [14/Aug/2011:23:26:39 +0100] [Job 110] (3)Make cif options : CNCartridge is not found in p_ppd
D [14/Aug/2011:23:26:39 +0100] [Job 110] (3)Make cif options : CNQuality is not found in p_ppd
D [14/Aug/2011:23:26:39 +0100] [Job 110] (3)Make cif options : CNHalftoning is not found in p_ppd
D [14/Aug/2011:23:26:39 +0100] [Job 110] (3)Make cif options : CNRenderIntent is not found in p_ppd
D [14/Aug/2011:23:26:39 +0100] [Job 110] (3)Make cif options : CNGamma is not found in p_ppd
D [14/Aug/2011:23:26:39 +0100] [Job 110] (3)Make cif options : CNBalanceC is not found in p_ppd
D [14/Aug/2011:23:26:39 +0100] [Job 110] (3)Make cif options : CNBalanceM is not found in p_ppd
D [14/Aug/2011:23:26:39 +0100] [Job 110] (3)Make cif options : CNBalanceY is not found in p_ppd
D [14/Aug/2011:23:26:39 +0100] [Job 110] (3)Make cif options : CNDensity is not found in p_ppd
D [14/Aug/2011:23:26:39 +0100] [Job 110] (3)Make cif options : CNGrayscale is not found in p_ppd
D [14/Aug/2011:23:26:39 +0100] [Job 110] (3)Make cif options : CNCopies is not found in p_ppd
D [14/Aug/2011:23:26:39 +0100] [Job 110] (3)Make cif options : CNContrast is not found in p_ppd
D [14/Aug/2011:23:26:39 +0100] [Job 110] (3)Make cif options : CNInkCartridgeSettings is not found in p_ppd
D [14/Aug/2011:23:26:39 +0100] [Job 110] (3)Make cif options : p_choice found in p_ppd (p_choice:2 /  2)
D [14/Aug/2011:23:26:39 +0100] [Job 110] (3)Make cif options : choice=2(p_table->ppd_key=CNExtension)
D [14/Aug/2011:23:26:39 +0100] [Job 110] ### lpr optins(4) : AP_D_InputSlot= ###
D [14/Aug/2011:23:26:39 +0100] [Job 110] ### lpr optins(3) : job-originating-host-name=localhost ###
D [14/Aug/2011:23:26:39 +0100] [Job 110] ### lpr optins(2) : job-uuid=urn:uuid:282a716d-8a91-349f-41af-2d6bac61e6c2 ###
D [14/Aug/2011:23:26:39 +0100] [Job 110] ### lpr optins(1) : time-at-creation=1313360772 ###
D [14/Aug/2011:23:26:39 +0100] [Job 110] ### lpr optins(0) : time-at-processing=1313360772 ###
D [14/Aug/2011:23:26:39 +0100] [Job 110] make_filter_param_list: --bidi
D [14/Aug/2011:23:26:39 +0100] [Job 110] make_filter_param_list: --fit
D [14/Aug/2011:23:26:39 +0100] [Job 110] make_filter_param_list: --bbox
D [14/Aug/2011:23:26:39 +0100] [Job 110] make_filter_param_list: --extension
D [14/Aug/2011:23:26:39 +0100] [Job 110] make_filter_param_list: --media
D [14/Aug/2011:23:26:39 +0100] [Job 110] make_filter_param_list: --papersize
D [14/Aug/2011:23:26:39 +0100] [Job 110] pstocanonij: /usr/bin/gs -r600 -g4958x7016 -q -dNOPROMPT -dSAFER -sDEVICE=ppmraw -sOutputFile=- -| /usr/bin/cifmx350 --imageres 600 --papersize a4 --media plain --bbox 9,14,586,834 --fit  --bidi  
D [14/Aug/2011:23:26:39 +0100] [Job 110] 
D [14/Aug/2011:23:26:39 +0100] [Job 110] waiting print data ...
D [14/Aug/2011:23:26:39 +0100] [Job 110] 
D [14/Aug/2011:23:26:39 +0100] [Job 110] Set job-printer-state-message to "error occurred while printing", current level=ERROR
D [14/Aug/2011:23:26:39 +0100] [Job 110] 
D [14/Aug/2011:23:26:39 +0100] [Job 110] Backend returned status 1 (failed)
D [14/Aug/2011:23:26:39 +0100] [Job 110] End of messages
D [14/Aug/2011:23:26:39 +0100] [Job 110] printer-state=3(idle)
D [14/Aug/2011:23:26:39 +0100] [Job 110] printer-state-message=""
D [14/Aug/2011:23:26:39 +0100] [Job 110] printer-state-reasons=none

---

### Post by SoFl W on 2011-08-14
You don't have to attach stuff like that, just click the code "#" key above the editor.

---

