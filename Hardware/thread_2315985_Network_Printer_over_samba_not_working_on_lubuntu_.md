---
title: "Network Printer over samba not working on lubuntu 15.10"
date: 2016-03-04
forum: Hardware
---

### Post by Mrinmoy_Dey on 2016-03-04
The printer always returns with 'filter failed' error. I have tried re-installing it several times. Even tried with different version of hplip (3.15.7, 3.15.11 & 3.16.2) but still problem persists.
Here is the error log from /var/log/CUPS/error_log
```
E [04/Mar/2016:14:30:51 +0530] [Job 28] Job stopped due to filter errors; please consult the error_log file for details.

D [04/Mar/2016:14:30:51 +0530] [Job 28] envp[22]="DEVICE_URI=smb://MSHOME/DEEPIKA/HPLaserJ.5" 
D [04/Mar/2016:14:30:51 +0530] [Job 28] envp[23]="PRINTER_INFO=HP LaserJet 1020" 
D [04/Mar/2016:14:30:51 +0530] [Job 28] envp[24]="PRINTER_LOCATION=" 
D [04/Mar/2016:14:30:51 +0530] [Job 28] envp[25]="PRINTER=HP-LaserJet-1020" 
D [04/Mar/2016:14:30:51 +0530] [Job 28] envp[26]="PRINTER_STATE_REASONS=none" 
D [04/Mar/2016:14:30:51 +0530] [Job 28] envp[27]="CUPS_FILETYPE=document" 
D [04/Mar/2016:14:30:51 +0530] [Job 28] envp[28]="FINAL_CONTENT_TYPE=application/vnd.cups-raster" 
D [04/Mar/2016:14:30:51 +0530] [Job 28] envp[29]="AUTH_INFO_REQUIRED=none" 
D [04/Mar/2016:14:30:51 +0530] [Job 28] Start rendering... 
D [04/Mar/2016:14:30:51 +0530] [Job 28] Set job-printer-state-message to "Start rendering...", current level=INFO 
D [04/Mar/2016:14:30:51 +0530] [Job 28] Processing page 1... 
D [04/Mar/2016:14:30:51 +0530] [Job 28] Set job-printer-state-message to "Processing page 1...", current level=INFO 
D [04/Mar/2016:14:30:51 +0530] [Job 28] STATE: +hplip.plugin-error 
D [04/Mar/2016:14:30:51 +0530] [Job 28] prnt/hpcups/HPCupsFilter.cpp 486: m_Job initialization failed with error = 48 
D [04/Mar/2016:14:30:51 +0530] [Job 28] PID 19767 (/usr/lib/cups/filter/hpcups) stopped with status 1. 
D [04/Mar/2016:14:30:51 +0530] [Job 28] Hint: Try setting the LogLevel to "debug" to find out more. 
D [04/Mar/2016:14:30:51 +0530] [Job 28] Processing page 2... 
D [04/Mar/2016:14:30:51 +0530] [Job 28] PID 19768 (/usr/lib/cups/backend/smb) exited with no errors. 
D [04/Mar/2016:14:30:51 +0530] [Job 28] Rendering completed 
D [04/Mar/2016:14:30:51 +0530] [Job 28] PID 19766 (/usr/lib/cups/filter/gstoraster) exited with no errors. 
D [04/Mar/2016:14:30:51 +0530] [Job 28] End of messages 
D [04/Mar/2016:14:30:51 +0530] [Job 28] printer-state=3(idle) 
D [04/Mar/2016:14:30:51 +0530] [Job 28] printer-state-message="Rendering completed" 
D [04/Mar/2016:14:30:51 +0530] [Job 28] printer-state-reasons=hplip.plugin-error
```
I am going nuts :/ Someone please suggest how to solve this.

---

### Post by him610 on 2016-03-04
Don't know if I can help or not, but maybe we can work through this. I have some experience with a couple of network printers that have always worked once they were set up and configured properly. 
Is your printer connected directly to your network? Did you assign it a static IP address?  Can you successfully ping the IP address of the HP1020?
Please provide the specifications for your computer -both hardware and operating system, your printer, and your network.

---

### Post by Mrinmoy_Dey on 2016-03-05
[COLOR=#111111][FONT=Ubuntu]As it turns out, the problem was with hplip plugin itself. Whatever version I have tried seems to be broken/not working with HP LaserJet 1020.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Solved the problem by installing 'foomatic-db' package using synaptic package manager. Don't install 'foomatic-filters'. Earlier I was installing both - since the error was filter failed. Foomatic-filters conflicts with CUPS.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]After installing 'foomatic-db', I re-installed my windows network printer via samba using the foomatic driver instead of hpcups and everything worked fine.[/FONT][/COLOR]

---

