---
title: "Some Epson printers dont work."
date: 2005-10-15
forum: Hardware &amp; Laptops
---

### Post by cwestpha on 2005-10-15
Now that its a final release I am moving the problem here since it was never addressed. here is the original URL:
[http://www.ubuntuforums.org/showthread.php?t=73766&highlight=epson+870](http://www.ubuntuforums.org/showthread.php?t=73766&highlight=epson+870)

Symptoms:
- Durring boot if I plug it in my boot will slow to a crawl and WLAN (wont bring up) and USB mouse (like someone cut the refreash rate down to half of normal) acts funny once X starts.
- Detects fine but once you use it to print it will just spit out nothing. The green power light may blink, but it doesnt do anything beyond that. This is even true of printing over SMB to a windows machine.
- Likewise with latest TurboPrint.

Well I looked at [http://www.linuxprinting.org/show_pr...ylus_Photo_870](http://www.linuxprinting.org/show_pr...ylus_Photo_870)

says my printer works perfectly with Linux. Double checked and Ubuntu is using the proper drivers and everything. Also the printer works with different Distros (Xandros, SuSe, etc) and Windows. That means someone doing coding for Ubuntu broke support for my printer.

Debug log results:

```
I [09/Oct/2005:12:33:30 -0500] Listening to 7f000001:631
I [09/Oct/2005:12:33:30 -0500] Loaded configuration file "/etc/cups/cupsd.conf"
I [09/Oct/2005:12:33:30 -0500] Configured for up to 100 clients.
I [09/Oct/2005:12:33:30 -0500] Allowing up to 100 client connections per host.
I [09/Oct/2005:12:33:30 -0500] Full reload is required.
E [09/Oct/2005:12:33:30 -0500] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
I [09/Oct/2005:12:33:31 -0500] LoadPPDs: Read "/etc/cups/ppds.dat", 4104 PPDs...
I [09/Oct/2005:12:33:31 -0500] LoadPPDs: No new or changed PPDs...
I [09/Oct/2005:12:33:31 -0500] Full reload complete.
I [09/Oct/2005:13:57:32 -0500] Scheduler shutting down normally.
I [09/Oct/2005:17:48:56 -0500] Listening to 7f000001:631
I [09/Oct/2005:17:48:56 -0500] Loaded configuration file "/etc/cups/cupsd.conf"
I [09/Oct/2005:17:48:57 -0500] Configured for up to 100 clients.
I [09/Oct/2005:17:48:57 -0500] Allowing up to 100 client connections per host.
I [09/Oct/2005:17:48:57 -0500] Full reload is required.
E [09/Oct/2005:17:48:57 -0500] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
I [09/Oct/2005:17:49:00 -0500] LoadPPDs: Read "/etc/cups/ppds.dat", 4104 PPDs...
I [09/Oct/2005:17:49:06 -0500] LoadPPDs: No new or changed PPDs...
I [09/Oct/2005:17:49:06 -0500] Full reload complete.
I [09/Oct/2005:18:00:27 -0500] Scheduler shutting down normally.
I [09/Oct/2005:18:02:24 -0500] Listening to 7f000001:631
I [09/Oct/2005:18:02:24 -0500] Loaded configuration file "/etc/cups/cupsd.conf"
I [09/Oct/2005:18:02:24 -0500] Configured for up to 100 clients.
I [09/Oct/2005:18:02:24 -0500] Allowing up to 100 client connections per host.
I [09/Oct/2005:18:02:24 -0500] Full reload is required.
E [09/Oct/2005:18:02:25 -0500] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
I [09/Oct/2005:18:02:30 -0500] LoadPPDs: Read "/etc/cups/ppds.dat", 4104 PPDs...
I [09/Oct/2005:18:02:33 -0500] LoadPPDs: No new or changed PPDs...
I [09/Oct/2005:18:02:33 -0500] Full reload complete.
I [09/Oct/2005:20:06:45 -0500] Scheduler shutting down normally.
I [09/Oct/2005:20:47:04 -0500] Listening to 7f000001:631
I [09/Oct/2005:20:47:05 -0500] Loaded configuration file "/etc/cups/cupsd.conf"
I [09/Oct/2005:20:47:05 -0500] Configured for up to 100 clients.
I [09/Oct/2005:20:47:05 -0500] Allowing up to 100 client connections per host.
I [09/Oct/2005:20:47:05 -0500] Full reload is required.
E [09/Oct/2005:20:47:06 -0500] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
I [09/Oct/2005:20:47:10 -0500] LoadPPDs: Read "/etc/cups/ppds.dat", 4104 PPDs...
I [09/Oct/2005:20:47:14 -0500] LoadPPDs: No new or changed PPDs...
I [09/Oct/2005:20:47:14 -0500] Full reload complete.
I [09/Oct/2005:23:21:49 -0500] Job 5 was cancelled by 'root'.
I [09/Oct/2005:23:22:35 -0500] Printer 'Stylus-Photo-870' deleted by 'root'.
I [09/Oct/2005:23:22:35 -0500] Saving printers.conf...
I [09/Oct/2005:23:24:24 -0500] Setting Stylus-Photo-870 device-uri to "smb://ATHIRNE/EpsonSty" (was "file:/dev/null".)
I [09/Oct/2005:23:24:24 -0500] Setting Stylus-Photo-870 printer-is-accepting-jobs to 1 (was 0.)
I [09/Oct/2005:23:24:24 -0500] Setting Stylus-Photo-870 printer-state to 3 (was 5.)
I [09/Oct/2005:23:24:24 -0500] Saving printers.conf...
I [09/Oct/2005:23:24:24 -0500] New printer 'Stylus-Photo-870' added by 'root'.
I [09/Oct/2005:23:24:51 -0500] Adding start banner page "none" to job 6.
I [09/Oct/2005:23:24:51 -0500] Adding end banner page "none" to job 6.
I [09/Oct/2005:23:24:51 -0500] Job 6 queued on 'Stylus-Photo-870' by 'cwestpha'.
I [09/Oct/2005:23:24:51 -0500] Started filter /usr/lib/cups/filter/pstops (PID 12772) for job 6.
I [09/Oct/2005:23:24:51 -0500] Started filter /usr/lib/cups/filter/foomatic-rip (PID 12773) for job 6.
I [09/Oct/2005:23:24:51 -0500] Started backend /usr/lib/cups/backend/smb (PID 12774) for job 6.
I [09/Oct/2005:23:33:56 -0500] Adding start banner page "none" to job 7.
I [09/Oct/2005:23:33:56 -0500] Adding end banner page "none" to job 7.
I [09/Oct/2005:23:33:56 -0500] Job 7 queued on 'Stylus-Photo-870' by 'cwestpha'.
I [09/Oct/2005:23:33:56 -0500] Started filter /usr/lib/cups/filter/pstops (PID 13153) for job 7.
I [09/Oct/2005:23:33:56 -0500] Started filter /usr/lib/cups/filter/foomatic-rip (PID 13154) for job 7.
I [09/Oct/2005:23:33:56 -0500] Started backend /usr/lib/cups/backend/smb (PID 13155) for job 7.
I [09/Oct/2005:23:38:04 -0500] Saving printers.conf...
I [09/Oct/2005:23:38:04 -0500] Printer 'Stylus-Photo-870' modified by 'root'.
I [09/Oct/2005:23:38:37 -0500] Printer 'Stylus-Photo-870' deleted by 'root'.
I [09/Oct/2005:23:38:37 -0500] Saving printers.conf...
I [09/Oct/2005:23:42:45 -0500] Scheduler shutting down normally.
I [09/Oct/2005:23:42:45 -0500] Listening to 7f000001:631
I [09/Oct/2005:23:42:45 -0500] Loaded configuration file "/etc/cups/cupsd.conf"
I [09/Oct/2005:23:42:45 -0500] Configured for up to 100 clients.
I [09/Oct/2005:23:42:45 -0500] Allowing up to 100 client connections per host.
I [09/Oct/2005:23:42:45 -0500] Full reload is required.
E [09/Oct/2005:23:42:46 -0500] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
I [09/Oct/2005:23:42:47 -0500] LoadPPDs: Read "/etc/cups/ppds.dat", 4104 PPDs...
I [09/Oct/2005:23:42:50 -0500] LoadPPDs: Wrote "/etc/cups/ppds.dat", 4351 PPDs...
I [09/Oct/2005:23:42:50 -0500] Full reload complete.
E [09/Oct/2005:23:43:51 -0500] get_printer_attrs: resource name '/printers/tp0' no good!
E [09/Oct/2005:23:43:51 -0500] get_jobs: resource name '/printers/tp0' no good!
I [09/Oct/2005:23:43:53 -0500] Saving printers.conf...
I [09/Oct/2005:23:43:53 -0500] New printer 'tp0' added by 'root'.
I [09/Oct/2005:23:43:53 -0500] Saving printers.conf...
I [09/Oct/2005:23:43:53 -0500] Printer 'tp0' modified by 'root'.
I [09/Oct/2005:23:43:53 -0500] Setting tp0 device-uri to "usb://EPSON/Stylus%20Photo%20870" (was "file:/dev/null".)
I [09/Oct/2005:23:43:53 -0500] Saving printers.conf...
I [09/Oct/2005:23:43:53 -0500] Printer 'tp0' modified by 'root'.
I [09/Oct/2005:23:43:53 -0500] Saving printers.conf...
I [09/Oct/2005:23:43:53 -0500] Printer 'tp0' now accepting jobs ('root').
I [09/Oct/2005:23:43:53 -0500] Saving printers.conf...
I [09/Oct/2005:23:43:53 -0500] Printer 'tp0' started by 'root'.
I [09/Oct/2005:23:43:54 -0500] Saving printers.conf...
E [09/Oct/2005:23:43:54 -0500] Unable to backup classes.conf - No such file or directory
I [09/Oct/2005:23:43:54 -0500] Saving classes.conf...
I [09/Oct/2005:23:43:54 -0500] Default destination set to 'tp0' by 'root'.
I [09/Oct/2005:23:43:54 -0500] Adding start banner page "none" to job 1.
I [09/Oct/2005:23:43:54 -0500] Adding end banner page "none" to job 1.
I [09/Oct/2005:23:43:54 -0500] Job 1 queued on 'tp0' by 'root'.
I [09/Oct/2005:23:43:54 -0500] Started filter /usr/lib/cups/filter/pstops (PID 13783) for job 1.
I [09/Oct/2005:23:43:54 -0500] Started filter /usr/lib/cups/filter/pstoturboprint (PID 13784) for job 1.
I [09/Oct/2005:23:43:54 -0500] Started backend /usr/lib/cups/backend/usb (PID 13786) for job 1.
W [09/Oct/2005:23:43:54 -0500] [Job 1] Printer fault!
I [09/Oct/2005:23:43:57 -0500] Printer 'tp0' started by 'root'.
I [09/Oct/2005:23:46:38 -0500] Job 1 was cancelled by 'root'.
I [09/Oct/2005:23:46:42 -0500] Saving printers.conf...
I [09/Oct/2005:23:46:42 -0500] Printer 'tp0' modified by 'root'.
I [09/Oct/2005:23:46:42 -0500] Saving printers.conf...
I [09/Oct/2005:23:46:42 -0500] Printer 'tp0' modified by 'root'.
I [09/Oct/2005:23:46:42 -0500] Setting tp0 device-uri to "usb://EPSON/Stylus%20Photo%20870" (was "usb://EPSON/Stylus%20Photo%20870".)
I [09/Oct/2005:23:46:42 -0500] Saving printers.conf...
I [09/Oct/2005:23:46:42 -0500] Printer 'tp0' modified by 'root'.
I [09/Oct/2005:23:46:43 -0500] Saving printers.conf...
I [09/Oct/2005:23:46:43 -0500] Saving classes.conf...
I [09/Oct/2005:23:46:43 -0500] Default destination set to 'tp0' by 'root'.
I [09/Oct/2005:23:46:43 -0500] Adding start banner page "none" to job 2.
I [09/Oct/2005:23:46:43 -0500] Adding end banner page "none" to job 2.
I [09/Oct/2005:23:46:43 -0500] Job 2 queued on 'tp0' by 'root'.
I [09/Oct/2005:23:46:43 -0500] Started filter /usr/lib/cups/filter/pstops (PID 13950) for job 2.
I [09/Oct/2005:23:46:43 -0500] Started filter /usr/lib/cups/filter/pstoturboprint (PID 13951) for job 2.
I [09/Oct/2005:23:46:43 -0500] Started backend /usr/lib/cups/backend/usb (PID 13952) for job 2.
W [09/Oct/2005:23:46:43 -0500] [Job 2] Printer fault!
I [09/Oct/2005:23:50:44 -0500] Job 2 was cancelled by 'root'.
I [09/Oct/2005:23:50:47 -0500] Adding start banner page "none" to job 3.
I [09/Oct/2005:23:50:47 -0500] Adding end banner page "none" to job 3.
I [09/Oct/2005:23:50:47 -0500] Job 3 queued on 'tp0' by 'cwestpha'.
I [09/Oct/2005:23:50:47 -0500] Started filter /usr/lib/cups/filter/pstops (PID 14149) for job 3.
I [09/Oct/2005:23:50:47 -0500] Started filter /usr/lib/cups/filter/pstoturboprint (PID 14150) for job 3.
I [09/Oct/2005:23:50:47 -0500] Started backend /usr/lib/cups/backend/usb (PID 14151) for job 3.
```

p.s. this is a freash install with final breezy.

---

### Post by cwestpha on 2005-10-16
Yes found the problem.
Some printers give warnings back about ink levels or other situations that these drivers dont support. Low ink, no ink, no papper, etc dont apear to be properly implemented for these printers.
So make sure your ink leves are fine and that everything else is ok before printing. If the printer is sending signals to its own PC side software that there is a problem and it is not handled by the open source drivers your printer can cease to signal because it keeps on trying to signal there is a problem.

yay!

---

