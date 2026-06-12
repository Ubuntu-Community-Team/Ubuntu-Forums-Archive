---
title: "Printer problems"
date: 2019-11-26
forum: Hardware
---

### Post by Gnigma on 2019-11-26
This new printer is giving me fits. It's a Pantum P2502W. Works fine when I boot into Windows 10. I've got Ubuntu 18.04.3. I've gone through the install, loaded the driver, and all I get is "Job stopped." Nothing in the troubleshooting log. Oh, I'm on an Asus 52 laptop. Ideas?

---

### Post by brian_p on 2019-11-26
Give the output of ```
driverless
``` when the device is on the network.

---

### Post by Gnigma on 2019-11-26
That gives me nothing. I'm down to just trying to get the POS to work off the USB cable, and I still get nothing.

---

### Post by brian_p on 2019-11-26
On 18.04 it *has* to give you something when the Pantum is on the network. What do you get for ```
avahi-browse -rt _ipp._tcp
``` and ```
avahi-browse -rt _uscan._tcp
```

---

### Post by brian_p on 2019-11-26
Forget about the second command.

---

### Post by Gnigma on 2019-11-26
I put both in and still get nothing.

---

### Post by brian_p on 2019-11-27
> **Gnigma said:**
> I put both in and still get nothing.

According to [https://support.apple.com/en-gb/HT201311](https://support.apple.com/en-gb/HT201311) the Pantum P2502W is an AirPrint device, but your data shows no sign that it is. Either AirPrint is not activated or the Pantum is not on the network.  Not being activated is a possibility, as indicated by [https://global.pantum.com/global/airprint-support/](https://global.pantum.com/global/airprint-support/). A firmware upgrade would give you the capability of not using Pantum drivers.

Anyway, upgrading is up to you. For now, we'll take a look at your present situation.

You should have a PPD for the printer in */etc/cups/ppd*. Execute this command ```
sudo cupsfilter -p /etc/cups/ppd/<the_PPD_name> -m printer/foo -e --list-filters /etc/nsswitch.conf
``` and post the output. Do not type the angle brackets.

Now do ```
sudo cupsfilter -p /etc/cups/ppd/<the_PPD_name> -m printer/foo -e /etc/nsswitch.conf > out.dat 2>log
```

 Look at *log* and say whether any of the filters fail.

---

### Post by Gnigma on 2019-11-28
OK, output from the first line is:

cupsfilter: File "/usr/lib/cups/filter/pt2500Filter" permissions OK (040755/uid=0/gid=o)
texttopdf
pdftopdf
gstoraster
pt2500Filter

The second line had no results.

---

### Post by brian_p on 2019-11-28
> **Gnigma said:**
> OK, output from the first line is:

cupsfilter: File "/usr/lib/cups/filter/pt2500Filter" permissions OK (040755/uid=0/gid=o)
texttopdf
pdftopdf
gstoraster
pt2500Filter

That is what I would expect.

> 
The second line had no results.

There isn't any output to the screen; the output goes into the file *log*. You can see it with ```
less log
```

We want to know if all the filters above run successfully. Also give the output of ```
ls -l out.dat
```

---

### Post by Gnigma on 2019-11-28
The site keeps telling me I don't have permission to post replies now.

---

### Post by Gnigma on 2019-11-28
ls -l out.dat gives me:

-rw-rw-r-- 1 jim jim 0 Nov 28 8:43 out.dat

---

### Post by Gnigma on 2019-11-28
I think the error log file is too big.

---

### Post by Gnigma on 2019-11-28
Yeah. Converted to text, it's 1198 pages!

---

### Post by brian_p on 2019-11-28
> **Gnigma said:**
> Yeah. Converted to text, it's 1198 pages!

I have no idea what you are on about. However, out.dat has zero size. That is not good. How about ```
ls -l log
```

---

### Post by Gnigma on 2019-11-29
-rw-rw-r-- 1 jim jim 4532 Nov 28 08:43 log

---

### Post by brian_p on 2019-11-29
> **Gnigma said:**
> -rw-rw-r-- 1 jim jim 4532 Nov 28 08:43 log

A small file. Compress it with ```
gzip log
``` and post log.gz as an attachment.

---

### Post by Gnigma on 2019-11-30
Latest one:

---

### Post by brian_p on 2019-11-30
Your error_log.2 shows > GPL Ghostscript 9.26: Unrecoverable error, exit code 1 This indicates a problem with your Ghostscript installation. You could try updating the system or reinstalling Ghostscript.

---

### Post by Gnigma on 2019-11-30
I've uninstalled and reinstalled Ghostscript. It still stops the job before printing.

---

### Post by brian_p on 2019-12-01
All I can think of is directly testing the gstoraster filter, which uses Ghostscript:

```
cupsfilter -m application/vnd.cups-raster /etc/nsswitch.conf out.ras 2>LOGFILE 
```

Have a look at LOGFILE yourself and also send it here as an attachment.

---

### Post by Gnigma on 2019-12-01
LOGFILE just said:  cupsfilter: Only one filename can be specified.

The zip file from earlier is still on the attachment window, and it won't let me remove it, nor will it let me add another attachment. Here is the troubleshoot-logs.text file:


```
-- Logs begin at Sun 2019-06-02 06:21:08 CDT, end at Thu 2019-11-28 14:35:51 CST. --
Nov 25 00:08:17 jim-K52F systemd[1]: Stopping CUPS Scheduler...
Nov 25 00:08:17 jim-K52F systemd[1]: Stopped CUPS Scheduler.
Nov 25 00:08:17 jim-K52F systemd[1]: Started CUPS Scheduler.
Nov 25 15:20:04 jim-K52F systemd[1]: Stopping CUPS Scheduler...
Nov 25 15:20:13 jim-K52F systemd[1]: Stopped CUPS Scheduler.
-- Reboot --
Nov 25 16:55:32 jim-K52F systemd[1]: Started CUPS Scheduler.
Nov 25 19:24:45 jim-K52F systemd[1]: cups.service: Main process exited, code=exited, status=1/FAILURE
Nov 25 19:24:45 jim-K52F systemd[1]: cups.service: Failed with result 'exit-code'.
Nov 25 19:24:45 jim-K52F systemd[1]: cups.service: Service hold-off time over, scheduling restart.
Nov 25 19:24:45 jim-K52F systemd[1]: cups.service: Scheduled restart job, restart counter is at 1.
Nov 25 19:24:45 jim-K52F systemd[1]: Stopped CUPS Scheduler.
Nov 25 19:24:45 jim-K52F systemd[1]: Started CUPS Scheduler.
Nov 25 19:24:51 jim-K52F /hpfax[7722]: [7722]: error: Failed to create /var/spool/cups/tmp/.hplip
Nov 25 19:26:23 jim-K52F systemd[1]: Stopping CUPS Scheduler...
Nov 25 19:26:26 jim-K52F systemd[1]: Stopped CUPS Scheduler.
-- Reboot --
Nov 25 19:29:11 jim-K52F systemd[1]: Started CUPS Scheduler.
Nov 25 19:29:21 jim-K52F /hpfax[1523]: [1523]: error: Failed to create /var/spool/cups/tmp/.hplip
Nov 25 19:35:59 jim-K52F systemd[1]: cups.service: Main process exited, code=exited, status=1/FAILURE
Nov 25 19:35:59 jim-K52F systemd[1]: cups.service: Failed with result 'exit-code'.
Nov 25 19:35:59 jim-K52F systemd[1]: cups.service: Service hold-off time over, scheduling restart.
Nov 25 19:35:59 jim-K52F systemd[1]: cups.service: Scheduled restart job, restart counter is at 1.
Nov 25 19:35:59 jim-K52F systemd[1]: Stopped CUPS Scheduler.
Nov 25 19:35:59 jim-K52F systemd[1]: Started CUPS Scheduler.
Nov 25 19:36:23 jim-K52F /hpfax[3167]: [3167]: error: Failed to create /var/spool/cups/tmp/.hplip
Nov 25 19:54:05 jim-K52F systemd[1]: Stopping CUPS Scheduler...
Nov 25 19:54:07 jim-K52F systemd[1]: Stopped CUPS Scheduler.
-- Reboot --
Nov 25 19:56:47 jim-K52F systemd[1]: Started CUPS Scheduler.
Nov 25 19:56:57 jim-K52F /hpfax[1570]: [1570]: error: Failed to create /var/spool/cups/tmp/.hplip
Nov 25 20:25:58 jim-K52F systemd[1]: cups.service: Main process exited, code=exited, status=1/FAILURE
Nov 25 20:25:58 jim-K52F systemd[1]: cups.service: Failed with result 'exit-code'.
Nov 25 20:25:59 jim-K52F systemd[1]: cups.service: Service hold-off time over, scheduling restart.
Nov 25 20:25:59 jim-K52F systemd[1]: cups.service: Scheduled restart job, restart counter is at 1.
Nov 25 20:25:59 jim-K52F systemd[1]: Stopped CUPS Scheduler.
Nov 25 20:25:59 jim-K52F systemd[1]: Started CUPS Scheduler.
Nov 25 20:54:52 jim-K52F systemd[1]: Stopping CUPS Scheduler...
Nov 25 20:54:53 jim-K52F systemd[1]: Stopped CUPS Scheduler.
-- Reboot --
Nov 25 20:57:30 jim-K52F systemd[1]: Started CUPS Scheduler.
Nov 25 20:57:40 jim-K52F /hpfax[1487]: [1487]: error: Failed to create /var/spool/cups/tmp/.hplip
Nov 26 00:09:34 jim-K52F systemd[1]: Stopping CUPS Scheduler...
Nov 26 00:09:34 jim-K52F systemd[1]: Stopped CUPS Scheduler.
Nov 26 00:09:34 jim-K52F systemd[1]: Started CUPS Scheduler.
Nov 26 12:11:20 jim-K52F systemd[1]: cups.service: Main process exited, code=exited, status=1/FAILURE
Nov 26 12:11:20 jim-K52F systemd[1]: cups.service: Failed with result 'exit-code'.
Nov 26 12:11:20 jim-K52F systemd[1]: cups.service: Service hold-off time over, scheduling restart.
Nov 26 12:11:20 jim-K52F systemd[1]: cups.service: Scheduled restart job, restart counter is at 1.
Nov 26 12:11:20 jim-K52F systemd[1]: Stopped CUPS Scheduler.
Nov 26 12:11:20 jim-K52F systemd[1]: Started CUPS Scheduler.
Nov 26 12:53:15 jim-K52F systemd[1]: Stopping CUPS Scheduler...
Nov 26 12:53:17 jim-K52F systemd[1]: Stopped CUPS Scheduler.
-- Reboot --
Nov 26 12:55:55 jim-K52F systemd[1]: Started CUPS Scheduler.
Nov 26 13:04:59 jim-K52F /hpfax[10065]: [10065]: error: Failed to create /var/spool/cups/tmp/.hplip
Nov 26 13:10:31 jim-K52F systemd[1]: cups.service: Main process exited, code=exited, status=1/FAILURE
Nov 26 13:10:31 jim-K52F systemd[1]: cups.service: Failed with result 'exit-code'.
Nov 26 13:10:31 jim-K52F systemd[1]: cups.service: Service hold-off time over, scheduling restart.
Nov 26 13:10:31 jim-K52F systemd[1]: cups.service: Scheduled restart job, restart counter is at 1.
Nov 26 13:10:31 jim-K52F systemd[1]: Stopped CUPS Scheduler.
Nov 26 13:10:32 jim-K52F systemd[1]: Started CUPS Scheduler.
Nov 26 13:10:37 jim-K52F /hpfax[10350]: [10350]: error: Failed to create /var/spool/cups/tmp/.hplip
Nov 26 13:27:54 jim-K52F systemd[1]: cups.service: Main process exited, code=exited, status=1/FAILURE
Nov 26 13:27:54 jim-K52F systemd[1]: cups.service: Failed with result 'exit-code'.
Nov 26 13:27:55 jim-K52F systemd[1]: cups.service: Service hold-off time over, scheduling restart.
Nov 26 13:27:55 jim-K52F systemd[1]: cups.service: Scheduled restart job, restart counter is at 2.
Nov 26 13:27:55 jim-K52F systemd[1]: Stopped CUPS Scheduler.
Nov 26 13:27:55 jim-K52F systemd[1]: Started CUPS Scheduler.
Nov 26 13:28:00 jim-K52F /hpfax[10840]: [10840]: error: Failed to create /var/spool/cups/tmp/.hplip
Nov 26 13:48:39 jim-K52F systemd[1]: cups.service: Main process exited, code=exited, status=1/FAILURE
Nov 26 13:48:39 jim-K52F systemd[1]: cups.service: Failed with result 'exit-code'.
Nov 26 13:48:40 jim-K52F systemd[1]: cups.service: Service hold-off time over, scheduling restart.
Nov 26 13:48:40 jim-K52F systemd[1]: cups.service: Scheduled restart job, restart counter is at 3.
Nov 26 13:48:40 jim-K52F systemd[1]: Stopped CUPS Scheduler.
Nov 26 13:48:40 jim-K52F systemd[1]: Started CUPS Scheduler.
Nov 26 13:48:45 jim-K52F /hpfax[11281]: [11281]: error: Failed to create /var/spool/cups/tmp/.hplip
Nov 26 13:56:50 jim-K52F systemd[1]: cups.service: Main process exited, code=exited, status=1/FAILURE
Nov 26 13:56:50 jim-K52F systemd[1]: cups.service: Failed with result 'exit-code'.
Nov 26 13:56:50 jim-K52F systemd[1]: cups.service: Service hold-off time over, scheduling restart.
Nov 26 13:56:50 jim-K52F systemd[1]: cups.service: Scheduled restart job, restart counter is at 4.
Nov 26 13:56:50 jim-K52F systemd[1]: Stopped CUPS Scheduler.
Nov 26 13:56:51 jim-K52F systemd[1]: Started CUPS Scheduler.
Nov 26 13:56:56 jim-K52F /hpfax[11682]: [11682]: error: Failed to create /var/spool/cups/tmp/.hplip
Nov 26 13:57:48 jim-K52F systemd[1]: cups.service: Main process exited, code=exited, status=1/FAILURE
Nov 26 13:57:48 jim-K52F systemd[1]: cups.service: Failed with result 'exit-code'.
Nov 26 13:57:48 jim-K52F systemd[1]: cups.service: Service hold-off time over, scheduling restart.
Nov 26 13:57:48 jim-K52F systemd[1]: cups.service: Scheduled restart job, restart counter is at 5.
Nov 26 13:57:48 jim-K52F systemd[1]: Stopped CUPS Scheduler.
Nov 26 13:57:48 jim-K52F systemd[1]: Started CUPS Scheduler.
Nov 26 14:01:46 jim-K52F /hpfax[12992]: [12992]: error: Failed to create /var/spool/cups/tmp/.hplip
Nov 26 16:09:56 jim-K52F systemd[1]: cups.service: Main process exited, code=exited, status=1/FAILURE
Nov 26 16:09:56 jim-K52F systemd[1]: cups.service: Failed with result 'exit-code'.
Nov 26 16:09:56 jim-K52F systemd[1]: cups.service: Service hold-off time over, scheduling restart.
Nov 26 16:09:56 jim-K52F systemd[1]: cups.service: Scheduled restart job, restart counter is at 6.
Nov 26 16:09:56 jim-K52F systemd[1]: Stopped CUPS Scheduler.
Nov 26 16:09:56 jim-K52F systemd[1]: Started CUPS Scheduler.
Nov 26 16:10:44 jim-K52F systemd[1]: Stopping CUPS Scheduler...
Nov 26 16:10:52 jim-K52F systemd[1]: Stopped CUPS Scheduler.
-- Reboot --
Nov 26 16:13:35 jim-K52F systemd[1]: Started CUPS Scheduler.
Nov 26 16:13:45 jim-K52F /hpfax[1576]: [1576]: error: Failed to create /var/spool/cups/tmp/.hplip
Nov 26 18:18:58 jim-K52F systemd[1]: cups.service: Main process exited, code=exited, status=1/FAILURE
Nov 26 18:18:58 jim-K52F systemd[1]: cups.service: Failed with result 'exit-code'.
Nov 26 18:18:59 jim-K52F systemd[1]: cups.service: Service hold-off time over, scheduling restart.
Nov 26 18:18:59 jim-K52F systemd[1]: cups.service: Scheduled restart job, restart counter is at 1.
Nov 26 18:18:59 jim-K52F systemd[1]: Stopped CUPS Scheduler.
Nov 26 18:18:59 jim-K52F systemd[1]: Started CUPS Scheduler.
Nov 26 18:19:23 jim-K52F /hpfax[6331]: [6331]: error: Failed to create /var/spool/cups/tmp/.hplip
Nov 26 18:20:11 jim-K52F systemd[1]: cups.service: Main process exited, code=exited, status=1/FAILURE
Nov 26 18:20:11 jim-K52F systemd[1]: cups.service: Failed with result 'exit-code'.
Nov 26 18:20:11 jim-K52F systemd[1]: cups.service: Service hold-off time over, scheduling restart.
Nov 26 18:20:11 jim-K52F systemd[1]: cups.service: Scheduled restart job, restart counter is at 2.
Nov 26 18:20:11 jim-K52F systemd[1]: Stopped CUPS Scheduler.
Nov 26 18:20:11 jim-K52F systemd[1]: Started CUPS Scheduler.
Nov 26 18:31:48 jim-K52F /hpfax[7308]: [7308]: error: Failed to create /var/spool/cups/tmp/.hplip
Nov 26 18:34:08 jim-K52F cupsd[6409]: pam_unix(cups:auth): check pass; user unknown
Nov 26 18:34:08 jim-K52F cupsd[6409]: pam_unix(cups:auth): authentication failure; logname= uid=0 euid=0 tty=cups ruser= rhost=localhost
Nov 26 18:37:44 jim-K52F systemd[1]: cups.service: Main process exited, code=exited, status=1/FAILURE
Nov 26 18:37:44 jim-K52F systemd[1]: cups.service: Failed with result 'exit-code'.
Nov 26 18:37:45 jim-K52F systemd[1]: cups.service: Service hold-off time over, scheduling restart.
Nov 26 18:37:45 jim-K52F systemd[1]: cups.service: Scheduled restart job, restart counter is at 3.
Nov 26 18:37:45 jim-K52F systemd[1]: Stopped CUPS Scheduler.
Nov 26 18:37:45 jim-K52F systemd[1]: Started CUPS Scheduler.
Nov 26 18:38:42 jim-K52F systemd[1]: Stopping CUPS Scheduler...
Nov 26 18:38:49 jim-K52F systemd[1]: Stopped CUPS Scheduler.
-- Reboot --
Nov 26 18:41:32 jim-K52F systemd[1]: Started CUPS Scheduler.
Nov 26 18:41:42 jim-K52F /hpfax[1583]: [1583]: error: Failed to create /var/spool/cups/tmp/.hplip
Nov 27 00:07:59 jim-K52F systemd[1]: Stopping CUPS Scheduler...
Nov 27 00:07:59 jim-K52F systemd[1]: Stopped CUPS Scheduler.
Nov 27 00:07:59 jim-K52F systemd[1]: Started CUPS Scheduler.
Nov 28 00:10:01 jim-K52F systemd[1]: Stopping CUPS Scheduler...
Nov 28 00:10:01 jim-K52F systemd[1]: Stopped CUPS Scheduler.
Nov 28 00:10:01 jim-K52F systemd[1]: Started CUPS Scheduler.
Nov 28 07:53:57 jim-K52F /hpfax[26168]: [26168]: error: Failed to create /var/spool/cups/tmp/.hplip
```

I don't know where the "hpfax" is coming from...

---

### Post by brian_p on 2019-12-01
> **Gnigma said:**
> LOGFILE just said:  cupsfilter: Only one filename can be specified.

An attempt at correcting my typo would have been appreciated. :)

```
cupsfilter -m application/vnd.cups-raster /etc/nsswitch.conf > out.ras 2>LOGFILE
```

---

### Post by brian_p on 2019-12-01
> The zip file from earlier is still on the attachment window, and it won't let me remove it, nor will it let me add another attachment.

Just send it inline as you did with the troubleshoot-logs file. It is not very large.

---

### Post by Gnigma on 2019-12-01
Still can't erase the zip file, but here's LOGFILE output.


```
DEBUG: argv[0]="cupsfilter"
DEBUG: argv[1]="1"
DEBUG: argv[2]="root"
DEBUG: argv[3]="nsswitch.conf"
DEBUG: argv[4]="1"
DEBUG: argv[5]=""
DEBUG: argv[6]="/etc/nsswitch.conf"
DEBUG: envp[0]="<CFProcessPath>"
DEBUG: envp[1]="CONTENT_TYPE=text/plain"
DEBUG: envp[2]="CUPS_DATADIR=/usr/share/cups"
DEBUG: envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
DEBUG: envp[4]="CUPS_SERVERBIN=/usr/lib/cups"
DEBUG: envp[5]="CUPS_SERVERROOT=/etc/cups"
DEBUG: envp[6]="LANG=en_US.UTF8"
DEBUG: envp[7]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
DEBUG: envp[8]="PPD=/usr/share/cups/model/laserjet.ppd"
DEBUG: envp[9]="PRINTER_INFO=cupsfilter"
DEBUG: envp[10]="PRINTER_LOCATION=Unknown"
DEBUG: envp[11]="PRINTER=cupsfilter"
DEBUG: envp[12]="RIP_MAX_CACHE=128m"
DEBUG: envp[13]="USER=root"
DEBUG: envp[14]="CHARSET=utf-8"
DEBUG: envp[15]="FINAL_CONTENT_TYPE=application/vnd.cups-raster"
INFO: texttopdf (PID 16917) started.
INFO: pdftopdf (PID 16918) started.
INFO: gstoraster (PID 16919) started.
DEBUG: pdftopdf: No PPD file specified, could not determine whether to log pages or not, so turned off page logging.
DEBUG: OUTFORMAT="(null)", so output format will be CUPS/PWG Raster
ERROR: Failed to open PPD: /usr/share/cups/model/laserjet.ppd
INFO: texttopdf (PID 16917) exited with no errors.
INFO: pdftopdf (PID 16918) exited with no errors.
DEBUG: Color Manager: Calibration Mode/Off
DEBUG: Calling FindDeviceById(cups-cupsfilter)
DEBUG: Failed to send: org.freedesktop.ColorManager.NotFound:device id 'cups-cupsfilter' does not exist
DEBUG: Failed to get find device cups-cupsfilter
DEBUG: Calling FindDeviceById(cups-cupsfilter)
DEBUG: Failed to send: org.freedesktop.ColorManager.NotFound:device id 'cups-cupsfilter' does not exist
DEBUG: Failed to get device cups-cupsfilter
DEBUG: Color Manager: ICC Profile: None
DEBUG: Ghostscript using Any-Part-of-Pixel method to fill paths.
DEBUG: Ghostscript command line: gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -dNOINTERPOLATE -dNOMEDIAATTRS -dShowAcroForm -sstdout=%stderr -sOutputFile=%stdout -sDEVICE=cups -sMediaClass=PwgRaster -sOutputType=Automatic -r600x600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dcupsBitsPerColor=1 -dcupsColorOrder=0 -dcupsColorSpace=3 -dcupsBorderlessScalingFactor=0.0000 -dcupsInteger1=1 -dcupsInteger2=1 -scupsPageSizeName=na_letter_8.5x11in -I/usr/share/cups/fonts -c -f -_
DEBUG: envp[0]="<CFProcessPath>"
DEBUG: envp[1]="CONTENT_TYPE=text/plain"
DEBUG: envp[2]="CUPS_DATADIR=/usr/share/cups"
DEBUG: envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
DEBUG: envp[4]="CUPS_SERVERBIN=/usr/lib/cups"
DEBUG: envp[5]="CUPS_SERVERROOT=/etc/cups"
DEBUG: envp[6]="LANG=en_US.UTF8"
DEBUG: envp[7]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
DEBUG: envp[8]="PPD=/usr/share/cups/model/laserjet.ppd"
DEBUG: envp[9]="PRINTER_INFO=cupsfilter"
DEBUG: envp[10]="PRINTER_LOCATION=Unknown"
DEBUG: envp[11]="PRINTER=cupsfilter"
DEBUG: envp[12]="RIP_MAX_CACHE=128m"
DEBUG: envp[13]="USER=root"
DEBUG: envp[14]="CHARSET=utf-8"
DEBUG: envp[15]="FINAL_CONTENT_TYPE=application/vnd.cups-raster"
INFO: Start rendering...
INFO: Processing page 1...
INFO: Processing page 2...
INFO: Rendering completed
INFO: gstoraster (PID 16919) exited with no errors.
```

---

### Post by brian_p on 2019-12-01
> **Gnigma said:**
> Still can't erase the zip file, but here's LOGFILE output.


Never mind about the zip file. This output is what was needed. It shows

> INFO: gstoraster (PID 16919) exited with no errors.

In other words - Ghostscript ran correctly without any problem.

Now do again exactly what you have done here but post what you get for this command:

```
cupsfilter -p /etc/cups/ppd/P2500W.ppd -m application/vnd.cups-raster > /etc/nsswitch.conf out.ras 2>NEWLOGFILE
```

amd post NEWLOGFILE.

---

### Post by Gnigma on 2019-12-02
```
DEBUG: argv[0]="cupsfilter"
DEBUG: argv[1]="1"
DEBUG: argv[2]="root"
DEBUG: argv[3]="out.ras"
DEBUG: argv[4]="1"
DEBUG: argv[5]=""
DEBUG: argv[6]="out.ras"
DEBUG: envp[0]="<CFProcessPath>"
DEBUG: envp[1]="CONTENT_TYPE=image/pwg-raster"
DEBUG: envp[2]="CUPS_DATADIR=/usr/share/cups"
DEBUG: envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
DEBUG: envp[4]="CUPS_SERVERBIN=/usr/lib/cups"
DEBUG: envp[5]="CUPS_SERVERROOT=/etc/cups"
DEBUG: envp[6]="LANG=en_US.UTF8"
DEBUG: envp[7]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
DEBUG: envp[8]="PPD=/etc/cups/ppd/P2500W.ppd"
DEBUG: envp[9]="PRINTER_INFO=cupsfilter"
DEBUG: envp[10]="PRINTER_LOCATION=Unknown"
DEBUG: envp[11]="PRINTER=cupsfilter"
DEBUG: envp[12]="RIP_MAX_CACHE=128m"
DEBUG: envp[13]="USER=root"
DEBUG: envp[14]="CHARSET=utf-8"
DEBUG: envp[15]="FINAL_CONTENT_TYPE=application/vnd.cups-raster"
INFO: rastertopdf (PID 4147) started.
INFO: pdftopdf (PID 4148) started.
INFO: gstoraster (PID 4149) started.
DEBUG: pdftopdf: No PPD file specified, could not determine whether to log pages or not, so turned off page logging.
DEBUG: OUTFORMAT="(null)", so output format will be CUPS/PWG Raster
ERROR: Failed to open PPD: /etc/cups/ppd/P2500W.ppd
DEBUG: OUTFORMAT="(null)", output format will be PDF
DEBUG: Color Manager: Calibration Mode/Off
DEBUG: Calling FindDeviceById(cups-cupsfilter)
DEBUG: Failed to send: org.freedesktop.ColorManager.NotFound:device id 'cups-cupsfilter' does not exist
DEBUG: Failed to get find device cups-cupsfilter
DEBUG: The PPD file could not be opened.
DEBUG: Unable to open PPD file on line 0.
INFO: Starting page 1.
INFO: rastertopdf (PID 4147) exited with no errors.
DEBUG: Color Manager: Calibration Mode/Off
INFO: pdftopdf (PID 4148) exited with no errors.
DEBUG: Calling FindDeviceById(cups-cupsfilter)
DEBUG: Failed to send: org.freedesktop.ColorManager.NotFound:device id 'cups-cupsfilter' does not exist
DEBUG: Failed to get find device cups-cupsfilter
DEBUG: Calling FindDeviceById(cups-cupsfilter)
DEBUG: Failed to send: org.freedesktop.ColorManager.NotFound:device id 'cups-cupsfilter' does not exist
DEBUG: Failed to get device cups-cupsfilter
DEBUG: Color Manager: ICC Profile: None
DEBUG: Ghostscript using Any-Part-of-Pixel method to fill paths.
DEBUG: Ghostscript command line: gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -dNOINTERPOLATE -dNOMEDIAATTRS -dShowAcroForm -sstdout=%stderr -sOutputFile=%stdout -sDEVICE=cups -sMediaClass=PwgRaster -sOutputType=Automatic -r600x600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dcupsBitsPerColor=1 -dcupsColorOrder=0 -dcupsColorSpace=3 -dcupsBorderlessScalingFactor=0.0000 -dcupsInteger1=1 -dcupsInteger2=1 -scupsPageSizeName=na_letter_8.5x11in -I/usr/share/cups/fonts -c -f -_
DEBUG: envp[0]="<CFProcessPath>"
DEBUG: envp[1]="CONTENT_TYPE=image/pwg-raster"
DEBUG: envp[2]="CUPS_DATADIR=/usr/share/cups"
DEBUG: envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
DEBUG: envp[4]="CUPS_SERVERBIN=/usr/lib/cups"
DEBUG: envp[5]="CUPS_SERVERROOT=/etc/cups"
DEBUG: envp[6]="LANG=en_US.UTF8"
DEBUG: envp[7]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
DEBUG: envp[8]="PPD=/etc/cups/ppd/P2500W.ppd"
DEBUG: envp[9]="PRINTER_INFO=cupsfilter"
DEBUG: envp[10]="PRINTER_LOCATION=Unknown"
DEBUG: envp[11]="PRINTER=cupsfilter"
DEBUG: envp[12]="RIP_MAX_CACHE=128m"
DEBUG: envp[13]="USER=root"
DEBUG: envp[14]="CHARSET=utf-8"
DEBUG: envp[15]="FINAL_CONTENT_TYPE=application/vnd.cups-raster"
INFO: Start rendering...
INFO: Processing page 1...
INFO: Processing page 2...
INFO: Rendering completed
INFO: gstoraster (PID 4149) exited with no errors.
```

---

### Post by Gnigma on 2019-12-02
OK, update. Obviously, the line "no ppd file specified" was the clue. I was able to locate an older install package, which said to first run the install without the usb cable connected to the printer. (?!!) I deleted all the previous files related to the printer before I did that, and it failed, then I connected the cable and ran the install package again. It worked. So, the printer is up and running, but I still don't understand why the PPD didn't load from the newer package. Maybe it's a glitch in the newer install program? Anyway, I really appreciate your time and help, Brian. I was beginning to think I was going to have to print everything through WINE!

---

### Post by brian_p on 2019-12-03
A splendid outcome! Well-done for sticking with it and being patient. Sometimes, all that is required is time to reflect.

For future readers I'd like to point out a mistake of mine. The *cupsfilter* commands I gave should have been prefaced by *sudo.*. That is, ```
sudo cupsfilter.......
```

---

### Post by Gnigma on 2019-12-03
Oh, yeah. I was doing that from the first, when it said "you don't have permission."  ;)

---

