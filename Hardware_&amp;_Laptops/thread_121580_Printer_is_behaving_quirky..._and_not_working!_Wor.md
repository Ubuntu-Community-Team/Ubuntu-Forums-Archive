---
title: "Printer is behaving quirky... and not working! Worked a few days ago."
date: 2006-01-25
forum: Hardware &amp; Laptops
---

### Post by sept00 on 2006-01-25
Since I updated some packages a few days ago, my printer will not print anything. I have tried most of the stuff recommended on this board, including chmod'ing /dev/lp0 and have edited the cupsd.conf and other files extensively. To no avail. But here's what I did step by step:

I'm running Kubuntu Breezy Badger. When I opened up the print manager, I could see my printer (HP LaserJet 5L), which has been installed correctly and was working until a few days ago. I can also look at the numerous print-jobs waiting to start, but my printer has this red "X" marked on him.

This is what happened in the cups error log when I sent something to the printer:

```
 tail -f /var/log/cups/error_log
I [25/Jan/2006:19:22:12 +0100] Adding start banner page "none" to job 20.
I [25/Jan/2006:19:22:12 +0100] Adding end banner page "none" to job 20.
I [25/Jan/2006:19:22:12 +0100] Job 20 queued on 'HPLaserjet5L' by 'thomas'.
I [25/Jan/2006:19:22:12 +0100] Started filter /usr/lib/cups/filter/pstops (PID 8055) for job 20.
I [25/Jan/2006:19:22:12 +0100] Started filter /usr/lib/cups/filter/foomatic-rip (PID 8056) for job 20.
I [25/Jan/2006:19:22:12 +0100] Started backend /usr/lib/cups/backend/parallel (PID 8057) for job 20.
E [25/Jan/2006:19:22:12 +0100] PID 8057 stopped with status 1!
I [25/Jan/2006:19:22:12 +0100] Hint: Try setting the LogLevel to "debug" to find out more.
E [25/Jan/2006:19:22:12 +0100] [Job 20] Unable to open parallel port device file "/dev/lp0": Permission denied
E [25/Jan/2006:19:22:13 +0100] PID 8056 stopped with status 9!
I [25/Jan/2006:19:22:13 +0100] Hint: Try setting the LogLevel to "debug" to find out more.
I [25/Jan/2006:19:22:13 +0100] Saving printers.conf...

```

So I did this: sudo chmod 777 /dev/lp0

When I try to print something now, it displays in the queue for like a second and then dissapears. When I echo text to the lp0 the printer's lights will blink and after that, nothing happens. But get this: When I try to print from a KDE printing dialog, my printer prints the previous echo-string. And this shows up in the cups error_log:

```
I [25/Jan/2006:19:29:02 +0100] Adding start banner page "none" to job 22.
I [25/Jan/2006:19:29:02 +0100] Adding end banner page "none" to job 22.
I [25/Jan/2006:19:29:02 +0100] Job 22 queued on 'HPLaserjet5L' by 'thomas'.
I [25/Jan/2006:19:29:02 +0100] Started filter /usr/lib/cups/filter/pstops (PID 8294) for job 22.
I [25/Jan/2006:19:29:02 +0100] Started filter /usr/lib/cups/filter/foomatic-rip (PID 8295) for job 22.
I [25/Jan/2006:19:29:02 +0100] Started backend /usr/lib/cups/backend/parallel (PID 8296) for job 22.

```

I hope I've made myself clear. I'd love some help from you folks, its a hard life without a printer... I'd really appreciate any suggestions how I can get this problem out of the way once and for all.

I.e. how can I completely reinstall the printing sub-system from scratch? That would rock.

Thanks a bunch!

---

### Post by sept00 on 2006-01-26
This printer issue hasn't really been resolved. No hints at all?

---

### Post by sept00 on 2006-01-30
Sorry everybody, this is the last time I bump this post. If nobody replies this time, I will either hacksaw my printer or sic Chuck Norris on it.

---

### Post by squelchwelly on 2006-03-04
I had the same problem. My Epson stylus color 740 suddenly stopped working and I have no idea why.
I solved it by using System -> administration -> printers to install one of the other drivers offered in the choice box. The printer printed very badly. Then I used the same commands but re-installed the original, recommended driver. The printer works now. Hope this helps.

---

### Post by 11hjpphty76lkjj on 2006-03-06
Edit the cupsd.conf change the line "loglevel" to debug.  Exit, Save, restart cups, (sudo /etc/init.d/cupsys restart) open the cups log, sudo tail -f /var/log/cups/error_log , try printing, post the cups error log.

Aaron

---

### Post by sept00 on 2006-03-13
Hi Aaron, thanks for the reply. Did what you recommended, and here it is, the beast of a cupslog:

```
D [13/Mar/2006:21:16:52 +0100] AcceptClient: 4 from localhost:631.
D [13/Mar/2006:21:16:52 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Mar/2006:21:16:52 +0100] ProcessIPPRequest: 4 status_code=1
D [13/Mar/2006:21:16:52 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Mar/2006:21:16:52 +0100] ProcessIPPRequest: 4 status_code=1
D [13/Mar/2006:21:16:52 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Mar/2006:21:16:52 +0100] ProcessIPPRequest: 4 status_code=0
D [13/Mar/2006:21:16:52 +0100] AcceptClient: 5 from localhost:631.
D [13/Mar/2006:21:16:52 +0100] CloseClient: 4
D [13/Mar/2006:21:16:52 +0100] ReadClient: 5 POST / HTTP/1.1
D [13/Mar/2006:21:16:52 +0100] ProcessIPPRequest: 5 status_code=1
D [13/Mar/2006:21:16:52 +0100] ReadClient: 5 POST / HTTP/1.1
D [13/Mar/2006:21:16:52 +0100] ProcessIPPRequest: 5 status_code=1
D [13/Mar/2006:21:16:52 +0100] ReadClient: 5 POST / HTTP/1.1
D [13/Mar/2006:21:16:52 +0100] ProcessIPPRequest: 5 status_code=0
D [13/Mar/2006:21:16:52 +0100] CloseClient: 5
D [13/Mar/2006:21:16:53 +0100] AcceptClient: 4 from localhost:631.
D [13/Mar/2006:21:16:53 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Mar/2006:21:16:53 +0100] ProcessIPPRequest: 4 status_code=1
D [13/Mar/2006:21:16:53 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Mar/2006:21:16:53 +0100] ProcessIPPRequest: 4 status_code=1
D [13/Mar/2006:21:16:53 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Mar/2006:21:16:53 +0100] ProcessIPPRequest: 4 status_code=0
D [13/Mar/2006:21:16:53 +0100] CloseClient: 4
D [13/Mar/2006:21:16:54 +0100] AcceptClient: 4 from localhost:631.
D [13/Mar/2006:21:16:54 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Mar/2006:21:16:54 +0100] ProcessIPPRequest: 4 status_code=1
D [13/Mar/2006:21:16:54 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Mar/2006:21:16:54 +0100] ProcessIPPRequest: 4 status_code=1
D [13/Mar/2006:21:16:54 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Mar/2006:21:16:54 +0100] ProcessIPPRequest: 4 status_code=0
D [13/Mar/2006:21:16:54 +0100] CloseClient: 4
D [13/Mar/2006:21:16:57 +0100] AcceptClient: 4 from localhost:631.
D [13/Mar/2006:21:16:57 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Mar/2006:21:16:57 +0100] ProcessIPPRequest: 4 status_code=1
D [13/Mar/2006:21:16:57 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Mar/2006:21:16:57 +0100] ProcessIPPRequest: 4 status_code=1
D [13/Mar/2006:21:16:58 +0100] ReadClient: 4 POST / HTTP/1.1
D [13/Mar/2006:21:16:58 +0100] ProcessIPPRequest: 4 status_code=0
D [13/Mar/2006:21:16:58 +0100] CloseClient: 4
D [13/Mar/2006:21:16:58 +0100] AcceptClient: 4 from localhost:631.
D [13/Mar/2006:21:16:58 +0100] ReadClient: 4 POST /printers/HP%20LaserJet%205L HTTP/1.1
D [13/Mar/2006:21:16:58 +0100] print_job: auto-typing file...
D [13/Mar/2006:21:16:58 +0100] print_job: request file type is application/postscript.
D [13/Mar/2006:21:16:58 +0100] check_quotas: requesting-user-name = 'thomas'
D [13/Mar/2006:21:16:58 +0100] print_job: requesting-user-name = 'thomas'
I [13/Mar/2006:21:16:58 +0100] Adding start banner page "none" to job 2.
I [13/Mar/2006:21:16:58 +0100] Adding end banner page "none" to job 2.
I [13/Mar/2006:21:16:58 +0100] Job 2 queued on 'HP LaserJet 5L' by 'thomas'.
D [13/Mar/2006:21:16:58 +0100] Job 2 hold_until = 0
D [13/Mar/2006:21:16:58 +0100] StartJob(2, 0x8096968)
D [13/Mar/2006:21:16:58 +0100] StartJob() id = 2, file = 0/1
D [13/Mar/2006:21:16:58 +0100] job-sheets=none,none
D [13/Mar/2006:21:16:58 +0100] banner_page = 0
D [13/Mar/2006:21:16:58 +0100] StartJob: argv = "HP LaserJet 5L","2","thomas","(stdin)","1","PreFilter=Level1","/var/spool/cups/d00002-001"
D [13/Mar/2006:21:16:58 +0100] StartJob: envp[0]="PATH=/usr/lib/cups/filter:/bin:/usr/bin"
D [13/Mar/2006:21:16:58 +0100] StartJob: envp[1]="SOFTWARE=CUPS/1.1"
D [13/Mar/2006:21:16:58 +0100] StartJob: envp[2]="USER=root"
D [13/Mar/2006:21:16:58 +0100] StartJob: envp[3]="CHARSET=utf-8"
D [13/Mar/2006:21:16:58 +0100] StartJob: envp[4]="LANG=de"
D [13/Mar/2006:21:16:58 +0100] StartJob: envp[5]="TZ=Europe/Berlin"
D [13/Mar/2006:21:16:58 +0100] StartJob: envp[6]="PPD=/etc/cups/ppd/HP LaserJet 5L.ppd"
D [13/Mar/2006:21:16:58 +0100] StartJob: envp[7]="CUPS_SERVERROOT=/etc/cups"
D [13/Mar/2006:21:16:58 +0100] StartJob: envp[8]="RIP_MAX_CACHE=8m"
D [13/Mar/2006:21:16:58 +0100] StartJob: envp[9]="TMPDIR=/var/spool/cups/tmp"
D [13/Mar/2006:21:16:58 +0100] StartJob: envp[10]="CONTENT_TYPE=application/postscript"
D [13/Mar/2006:21:16:58 +0100] StartJob: envp[11]="DEVICE_URI=parallel:/dev/lp0"
D [13/Mar/2006:21:16:58 +0100] StartJob: envp[12]="PRINTER=HP LaserJet 5L"
D [13/Mar/2006:21:16:58 +0100] StartJob: envp[13]="CUPS_DATADIR=/usr/share/cups"
D [13/Mar/2006:21:16:58 +0100] StartJob: envp[14]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [13/Mar/2006:21:16:58 +0100] StartJob: envp[15]="CUPS_SERVER=localhost"
D [13/Mar/2006:21:16:58 +0100] StartJob: envp[16]="IPP_PORT=631"
D [13/Mar/2006:21:16:58 +0100] StartJob: statusfds = [ 5 6 ]
D [13/Mar/2006:21:16:58 +0100] StartJob: filterfds[1] = [ 7 -1 ]
D [13/Mar/2006:21:16:58 +0100] StartJob: filter = "/usr/lib/cups/filter/pstops"
D [13/Mar/2006:21:16:58 +0100] StartJob: filterfds[0] = [ 8 9 ]
D [13/Mar/2006:21:16:58 +0100] start_process("/usr/lib/cups/filter/pstops", 0xbf8d5640, 0xbf8d4bb8, 7, 9, 6)
I [13/Mar/2006:21:16:58 +0100] Started filter /usr/lib/cups/filter/pstops (PID 9676) for job 2.
D [13/Mar/2006:21:16:58 +0100] StartJob: filter = "/usr/lib/cups/filter/foomatic-rip"
D [13/Mar/2006:21:16:58 +0100] StartJob: filterfds[1] = [ 7 10 ]
D [13/Mar/2006:21:16:58 +0100] start_process("/usr/lib/cups/filter/foomatic-rip", 0xbf8d5640, 0xbf8d4bb8, 8, 10, 6)
I [13/Mar/2006:21:16:58 +0100] Started filter /usr/lib/cups/filter/foomatic-rip (PID 9677) for job 2.
D [13/Mar/2006:21:16:58 +0100] StartJob: backend = "/usr/lib/cups/backend/parallel"
D [13/Mar/2006:21:16:58 +0100] StartJob: filterfds[0] = [ -1 8 ]
D [13/Mar/2006:21:16:58 +0100] start_process("/usr/lib/cups/backend/parallel", 0xbf8d5640, 0xbf8d4bb8, 7, 8, 6)
I [13/Mar/2006:21:16:58 +0100] Started backend /usr/lib/cups/backend/parallel (PID 9678) for job 2.
D [13/Mar/2006:21:16:58 +0100] ProcessIPPRequest: 4 status_code=0
D [13/Mar/2006:21:16:58 +0100] CloseClient: 4
D [13/Mar/2006:21:16:58 +0100] [Job 2] Page = 612x792; 0,0 to 612,792
D [13/Mar/2006:21:16:58 +0100] [Job 2] slowcollate=0, slowduplex=0, sloworder=0
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%BoundingBox: 0 0 612 792
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Creator: Mozilla PostScript module (rv:1.7.12/2005101015)
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%DocumentData: Clean8Bit
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%DocumentPaperSizes: Letter
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Orientation: Portrait
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Pages: (atend)
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%PageOrder: Ascend
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%EndComments
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%BeginProlog
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%EndProlog
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%DocumentNeededResources: procset CIDInit
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%IncludeResource: procset CIDInit
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%BeginResource: CMap Bitstream_Vera_Sans.Bold.0.0_cmap
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Title: (Bitstream_Vera_Sans.Bold.0.0_cmap mozilla_printout SorWAu0usxonqFW3Edx6X2VXxPQ= 0)
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Version : 1
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%EndResource
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%DocumentNeededResources: procset CIDInit
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%IncludeResource: procset CIDInit
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%BeginResource: CIDFont Bitstream_Vera_Sans.Bold.0.0
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Title: (Bitstream_Vera_Sans.Bold.0.0 mozilla_printout SorWAu0usxonqFW3Edx6X2VXxPQ= 0)
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Version: 1
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%BeginData: 15659 Binary Bytes
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%EndData
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%EndResource
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%DocumentNeededResources: procset CIDInit
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%IncludeResource: procset CIDInit
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%BeginResource: CMap Baekmuk_Dotum.Regular.0.0_cmap
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Title: (Baekmuk_Dotum.Regular.0.0_cmap mozilla_printout jQ9F5GhCAA+yGSQDbYj39ZmvqIc= 0)
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Version : 1
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%EndResource
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%DocumentNeededResources: procset CIDInit
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%IncludeResource: procset CIDInit
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%BeginResource: CIDFont Baekmuk_Dotum.Regular.0.0
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Title: (Baekmuk_Dotum.Regular.0.0 mozilla_printout jQ9F5GhCAA+yGSQDbYj39ZmvqIc= 0)
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Version: 1
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%BeginData: 910 Binary Bytes
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%EndData
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%EndResource
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%DocumentNeededResources: procset CIDInit
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%IncludeResource: procset CIDInit
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%BeginResource: CMap FreeSans.Medium.0.0_cmap
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Title: (FreeSans.Medium.0.0_cmap mozilla_printout MRlwH5BCSpy+3Vsu3L+O6p2aWag= 0)
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Version : 1
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%EndResource
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%DocumentNeededResources: procset CIDInit
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%IncludeResource: procset CIDInit
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%BeginResource: CIDFont FreeSans.Medium.0.0
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Title: (FreeSans.Medium.0.0 mozilla_printout MRlwH5BCSpy+3Vsu3L+O6p2aWag= 0)
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Version: 1
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%BeginData: 1316 Binary Bytes
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%EndData
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%EndResource
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%DocumentNeededResources: procset CIDInit
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%IncludeResource: procset CIDInit
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%BeginResource: CMap Bitstream_Vera_Sans.Roman.0.0_cmap
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Title: (Bitstream_Vera_Sans.Roman.0.0_cmap mozilla_printout 4aQjRRcfcV607wXImUegBs1vCOI= 0)
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Version : 1
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%EndResource
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%DocumentNeededResources: procset CIDInit
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%IncludeResource: procset CIDInit
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%BeginResource: CIDFont Bitstream_Vera_Sans.Roman.0.0
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Title: (Bitstream_Vera_Sans.Roman.0.0 mozilla_printout 4aQjRRcfcV607wXImUegBs1vCOI= 0)
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Version: 1
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%BeginData: 18899 Binary Bytes
D [13/Mar/2006:21:16:58 +0100] [Job 2] perl: warning: Setting locale failed.
D [13/Mar/2006:21:16:58 +0100] [Job 2] perl: warning: Please check that your locale settings:
D [13/Mar/2006:21:16:58 +0100] [Job 2] LANGUAGE = (unset),
D [13/Mar/2006:21:16:58 +0100] [Job 2] LC_ALL = (unset),
D [13/Mar/2006:21:16:58 +0100] [Job 2] LANG = "de"
D [13/Mar/2006:21:16:58 +0100] [Job 2] are supported and installed on your system.
D [13/Mar/2006:21:16:58 +0100] [Job 2] perl: warning: Falling back to the standard locale ("C").
D [13/Mar/2006:21:16:58 +0100] [Job 2] foomatic-rip version $Revision: 3.43.2.11 $ running...
D [13/Mar/2006:21:16:58 +0100] [Job 2] Parsing PPD file ...
D [13/Mar/2006:21:16:58 +0100] [Job 2] *cupsFilter: "application/vnd.cups-postscript 0 foomatic-rip"
D [13/Mar/2006:21:16:58 +0100] [Job 2] Added option ColorSpace
D [13/Mar/2006:21:16:58 +0100] [Job 2] Added option PageSize
D [13/Mar/2006:21:16:58 +0100] [Job 2] Added option PageRegion
D [13/Mar/2006:21:16:58 +0100] [Job 2] Added option ImageableArea
D [13/Mar/2006:21:16:58 +0100] [Job 2] Added option PaperDimension
D [13/Mar/2006:21:16:58 +0100] [Job 2] Added option InputSlot
D [13/Mar/2006:21:16:58 +0100] [Job 2] Added option Manualfeed
D [13/Mar/2006:21:16:58 +0100] [Job 2] Added option Resolution
D [13/Mar/2006:21:16:58 +0100] [Job 2] Added option Economode
D [13/Mar/2006:21:16:58 +0100] [Job 2] Added option Dithering
D [13/Mar/2006:21:16:58 +0100] [Job 2] Added option Copies
D [13/Mar/2006:21:16:58 +0100] [Job 2] Added option HalftoningAlgorithm
D [13/Mar/2006:21:16:58 +0100] [Job 2] Added option REt
D [13/Mar/2006:21:16:58 +0100] [Job 2] Added option TonerDensity
D [13/Mar/2006:21:16:58 +0100] [Job 2] Added option MPTray
D [13/Mar/2006:21:16:58 +0100] [Job 2] Added option Font
D [13/Mar/2006:21:16:58 +0100] [Job 2]
D [13/Mar/2006:21:16:58 +0100] [Job 2] Parameter Summary
D [13/Mar/2006:21:16:58 +0100] [Job 2] -----------------
D [13/Mar/2006:21:16:58 +0100] [Job 2]
D [13/Mar/2006:21:16:58 +0100] [Job 2] Spooler: cups
D [13/Mar/2006:21:16:58 +0100] [Job 2] Printer: HP LaserJet 5L
D [13/Mar/2006:21:16:58 +0100] [Job 2] PPD file: /etc/cups/ppd/HP LaserJet 5L.ppd
D [13/Mar/2006:21:16:58 +0100] [Job 2] Printer model: HP LaserJet 5L Foomatic/ljet4 (recommended)
D [13/Mar/2006:21:16:58 +0100] [Job 2] Job title: stdin
D [13/Mar/2006:21:16:58 +0100] [Job 2] File(s) to be printed:
D [13/Mar/2006:21:16:58 +0100] [Job 2] <STDIN>
D [13/Mar/2006:21:16:58 +0100] [Job 2]
D [13/Mar/2006:21:16:58 +0100] [Job 2] GhostScript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [13/Mar/2006:21:16:58 +0100] [Job 2] Pondering option 'PreFilter=Level1'
D [13/Mar/2006:21:16:58 +0100] [Job 2] Unknown option PreFilter=Level1.
D [13/Mar/2006:21:16:58 +0100] [Job 2]
D [13/Mar/2006:21:16:58 +0100] [Job 2] ================================================
D [13/Mar/2006:21:16:58 +0100] [Job 2]
D [13/Mar/2006:21:16:58 +0100] [Job 2] File: <STDIN>
D [13/Mar/2006:21:16:58 +0100] [Job 2]
D [13/Mar/2006:21:16:58 +0100] [Job 2] ================================================
D [13/Mar/2006:21:16:58 +0100] [Job 2]
D [13/Mar/2006:21:16:58 +0100] [Job 2] Reading PostScript input ...
D [13/Mar/2006:21:16:58 +0100] [Job 2] --> This document is DSC-conforming!
D [13/Mar/2006:21:16:58 +0100] [Job 2]
D [13/Mar/2006:21:16:58 +0100] [Job 2] -----------
D [13/Mar/2006:21:16:58 +0100] [Job 2] Found: %%BeginProlog
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%EndData
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%EndResource
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%DocumentNeededResources: procset CIDInit
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%IncludeResource: procset CIDInit
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%BeginResource: CMap Kochi_Gothic.Regular.0.0_cmap
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Title: (Kochi_Gothic.Regular.0.0_cmap mozilla_printout OfCzyEQqi2qDQn54lq5LsfW4Bmk= 0)
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Version : 1
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%EndResource
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%DocumentNeededResources: procset CIDInit
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%IncludeResource: procset CIDInit
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%BeginResource: CIDFont Kochi_Gothic.Regular.0.0
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Title: (Kochi_Gothic.Regular.0.0 mozilla_printout OfCzyEQqi2qDQn54lq5LsfW4Bmk= 0)
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Version: 1
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%BeginData: 4619 Binary Bytes
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%EndData
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%EndResource
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Page: 1 1
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Page: 1 1
D [13/Mar/2006:21:16:58 +0100] [Job 2] pw = 612.0, pl = 792.0
D [13/Mar/2006:21:16:58 +0100] [Job 2] PageLeft = 0.0, PageRight = 612.0
D [13/Mar/2006:21:16:58 +0100] [Job 2] PageTop = 792.0, PageBottom = 0.0
D [13/Mar/2006:21:16:58 +0100] [Job 2] PageWidth = 612.0, PageLength = 792.0
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%BeginPageSetup
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%EndPageSetup
D [13/Mar/2006:21:16:58 +0100] [Job 2] Found: %%EndProlog
D [13/Mar/2006:21:16:58 +0100] [Job 2] This job seems not to be DSC-conforming, DSC-comment for next section not found, stopping to parse the rest, passing it directly to the renderer.
D [13/Mar/2006:21:16:58 +0100] [Job 2] "Setup" section is missing, inserting it.
D [13/Mar/2006:21:16:58 +0100] [Job 2] Inserting PostScript code for CUPS' page accounting
D [13/Mar/2006:21:16:58 +0100] [Job 2] "PageSetup" section is missing, inserting it.
D [13/Mar/2006:21:16:58 +0100] [Job 2] Inserting option code into "PageSetup" section.
D [13/Mar/2006:21:16:58 +0100] [Job 2] Stopped parsing the PostScript data, sending rest directly to renderer.
D [13/Mar/2006:21:16:58 +0100] [Job 2]
D [13/Mar/2006:21:16:58 +0100] [Job 2] Starting renderer
D [13/Mar/2006:21:16:58 +0100] [Job 2] JCL: 12345X@PJL
D [13/Mar/2006:21:16:58 +0100] [Job 2] @PJL SET MANUALFEED=OFF
D [13/Mar/2006:21:16:58 +0100] [Job 2] @PJL SET ECONOMODE=OFF
D [13/Mar/2006:21:16:58 +0100] [Job 2] @PJL SET COPIES=1
D [13/Mar/2006:21:16:58 +0100] [Job 2] @PJL SET RET=MEDIUM
D [13/Mar/2006:21:16:58 +0100] [Job 2] @PJL SET DENSITY=3
D [13/Mar/2006:21:16:58 +0100] [Job 2] @PJL SET MPTRAY=FIRST
D [13/Mar/2006:21:16:58 +0100] [Job 2] <job data>
D [13/Mar/2006:21:16:58 +0100] [Job 2] 12345X@PJL RESET
D [13/Mar/2006:21:16:58 +0100] [Job 2]
D [13/Mar/2006:21:16:58 +0100] [Job 2] renderer PID kid4=9681
D [13/Mar/2006:21:16:58 +0100] [Job 2] renderer command: gs -q -dBATCH -dPARANOIDSAFER -dNOPAUSE -sDEVICE=ljet4 -sOutputFile=- - | perl -p -0033 -e " s/^&l\d+[aA]/$&/; "
D [13/Mar/2006:21:16:58 +0100] [Job 2] perl: warning: Setting locale failed.
D [13/Mar/2006:21:16:58 +0100] [Job 2] perl: warning: Please check that your locale settings:
D [13/Mar/2006:21:16:58 +0100] [Job 2] LANGUAGE = (unset),
D [13/Mar/2006:21:16:58 +0100] [Job 2] LC_ALL = (unset),
D [13/Mar/2006:21:16:58 +0100] [Job 2] LANG = "de"
D [13/Mar/2006:21:16:58 +0100] [Job 2] are supported and installed on your system.
D [13/Mar/2006:21:16:58 +0100] [Job 2] perl: warning: Falling back to the standard locale ("C").
D [13/Mar/2006:21:16:58 +0100] [Job 2] foomatic-gswrapper: gs '-dBATCH' '-dPARANOIDSAFER' '-dNOPAUSE' '-sDEVICE=ljet4' '-sOutputFile=/dev/fd/3' '/dev/fd/0' 3>&1 1>&2
D [13/Mar/2006:21:16:58 +0100] [Job 2] sh: gs: command not found
D [13/Mar/2006:21:16:58 +0100] [Job 2] perl: warning: Setting locale failed.
D [13/Mar/2006:21:16:58 +0100] [Job 2] perl: warning: Please check that your locale settings:
D [13/Mar/2006:21:16:58 +0100] [Job 2] LANGUAGE = (unset),
D [13/Mar/2006:21:16:58 +0100] [Job 2] LC_ALL = (unset),
D [13/Mar/2006:21:16:58 +0100] [Job 2] LANG = "de"
D [13/Mar/2006:21:16:58 +0100] [Job 2] are supported and installed on your system.
D [13/Mar/2006:21:16:58 +0100] [Job 2] perl: warning: Falling back to the standard locale ("C").
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Page: 2 2
D [13/Mar/2006:21:16:58 +0100] [Job 2] pw = 612.0, pl = 792.0
D [13/Mar/2006:21:16:58 +0100] [Job 2] PageLeft = 0.0, PageRight = 612.0
D [13/Mar/2006:21:16:58 +0100] [Job 2] PageTop = 792.0, PageBottom = 0.0
D [13/Mar/2006:21:16:58 +0100] [Job 2] PageWidth = 612.0, PageLength = 792.0
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%BeginPageSetup
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%EndPageSetup
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Page: 3 3
D [13/Mar/2006:21:16:58 +0100] [Job 2] pw = 612.0, pl = 792.0
D [13/Mar/2006:21:16:58 +0100] [Job 2] PageLeft = 0.0, PageRight = 612.0
D [13/Mar/2006:21:16:58 +0100] [Job 2] PageTop = 792.0, PageBottom = 0.0
D [13/Mar/2006:21:16:58 +0100] [Job 2] PageWidth = 612.0, PageLength = 792.0
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%BeginPageSetup
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%EndPageSetup
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Page: 4 4
D [13/Mar/2006:21:16:58 +0100] [Job 2] pw = 612.0, pl = 792.0
D [13/Mar/2006:21:16:58 +0100] [Job 2] PageLeft = 0.0, PageRight = 612.0
D [13/Mar/2006:21:16:58 +0100] [Job 2] PageTop = 792.0, PageBottom = 0.0
D [13/Mar/2006:21:16:58 +0100] [Job 2] PageWidth = 612.0, PageLength = 792.0
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%BeginPageSetup
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%EndPageSetup
D [13/Mar/2006:21:16:58 +0100] [Job 2] 0 %%Trailer
D [13/Mar/2006:21:16:58 +0100] [Job 2] Saw Trailer!
D [13/Mar/2006:21:16:58 +0100] [Job 2] Saw EOF!
D [13/Mar/2006:21:16:58 +0100] [Job 2]
D [13/Mar/2006:21:16:58 +0100] [Job 2] Closing renderer
D [13/Mar/2006:21:16:58 +0100] [Job 2] KID3 exited with status 0
D [13/Mar/2006:21:16:58 +0100] [Job 2] tail process done writing data to STDOUT
D [13/Mar/2006:21:16:58 +0100] [Job 2] KID4 finished
D [13/Mar/2006:21:16:58 +0100] [Job 2] KID4 exited with status 0
D [13/Mar/2006:21:16:58 +0100] [Job 2] Renderer exit stat: 0
D [13/Mar/2006:21:16:58 +0100] [Job 2] KID3 finished
D [13/Mar/2006:21:16:58 +0100] [Job 2] Renderer process finished
D [13/Mar/2006:21:16:58 +0100] [Job 2]
D [13/Mar/2006:21:16:58 +0100] [Job 2] Closing foomatic-rip.
D [13/Mar/2006:21:16:58 +0100] UpdateJob: job 2, file 0 is complete.
D [13/Mar/2006:21:16:58 +0100] CancelJob: id = 2
D [13/Mar/2006:21:16:58 +0100] StopJob: id = 2, force = 0
D [13/Mar/2006:21:16:58 +0100] StopJob: printer state is 3
```

I guess things start getting fishy when perl isn't finding the locale, but what do I know. I'd be glad about all the help I can get! Thanks again!

Thomas

---

