---
title: "Cups stopped working AGAIN"
date: 2011-06-24
forum: Hardware
---

### Post by dargaud on 2011-06-24
Hello all,
printers have always been a major pain to use, with all those tiny mechanical parts and all. But here it's pure software. The 11.04 upgrade broke cups for the Nth time since I started using Ubuntu couple years ago, but I thought I'd [solved that]("http://ubuntuforums.org/showthread.php?t=1768181"), but today it's broken again. I can print a test page fine from the cups web interface, I can print from a virtualbox XP session, but if I print something else (from firefox or gimp), the job just hangs, no error:
```
EPSON_Stylus_Photo_R1800-148  	Img.png  	dargaud  	7588k  	Unknown  	pending since Fri 24 Jun 2011 11:22:29 PM CEST
EPSON_Stylus_Photo_R1800-147  	VTT  	dargaud  	205k  	Unknown  	processing since Fri 24 Jun 2011 11:21:22 PM CEST
```
There are no errors in the logs:
```
localhost - - [24/Jun/2011:23:21:08 +0200] "POST /printers/EPSON_Stylus_Photo_R1800 HTTP/1.1" 200 211820 Print-Job successful-ok
localhost - - [24/Jun/2011:23:22:29 +0200] "POST /printers/EPSON_Stylus_Photo_R1800 HTTP/1.1" 200 7772011 Print-Job successful-ok

```
```
I [24/Jun/2011:23:30:48 +0200] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=27262)
I [24/Jun/2011:23:30:52 +0200] Scheduler shutting down normally.
I [24/Jun/2011:23:30:52 +0200] Saving job cache file "/var/cache/cups/job.cache"...
I [24/Jun/2011:23:30:52 +0200] Listening to 0.0.0.0:631 (IPv4)
I [24/Jun/2011:23:30:52 +0200] Listening to [v1.::]:631 (IPv6)
I [24/Jun/2011:23:30:52 +0200] Listening to /var/run/cups/cups.sock (Domain)
W [24/Jun/2011:23:30:52 +0200] No limit for Validate-Job defined in policy authenticated - using Print-Job's policy
I [24/Jun/2011:23:30:52 +0200] Remote access is enabled.
I [24/Jun/2011:23:30:52 +0200] Loaded configuration file "/etc/cups/cupsd.conf"
I [24/Jun/2011:23:30:52 +0200] Using default TempDir of /var/spool/cups/tmp...
I [24/Jun/2011:23:30:52 +0200] Configured for up to 100 clients.
I [24/Jun/2011:23:30:52 +0200] Allowing up to 100 client connections per host.
I [24/Jun/2011:23:30:52 +0200] Using policy "default" as the default!
I [24/Jun/2011:23:30:52 +0200] Full reload is required.
I [24/Jun/2011:23:30:52 +0200] Loaded MIME database from "/usr/share/cups/mime" and "/etc/cups": 38 types, 77 filters...
I [24/Jun/2011:23:30:52 +0200] Loading job cache file "/var/cache/cups/job.cache"...
I [24/Jun/2011:23:30:52 +0200] Full reload complete.
I [24/Jun/2011:23:30:52 +0200] Cleaning out old files in "/var/spool/cups/tmp"...
I [24/Jun/2011:23:30:52 +0200] Cleaning out old files in "/var/cache/cups"...
I [24/Jun/2011:23:30:52 +0200] Listening to 0.0.0.0:631 on fd 6...
I [24/Jun/2011:23:30:52 +0200] Listening to [v1.::]:631 on fd 7...
I [24/Jun/2011:23:30:52 +0200] Listening to /var/run/cups/cups.sock on fd 8...
I [24/Jun/2011:23:30:52 +0200] Resuming new connection processing...
I [24/Jun/2011:23:30:59 +0200] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=27289)

```
Any idea at all ?!?

---

### Post by dargaud on 2011-06-27
No taker ?
What I find strange is that test pages print fine while self-test pages do not. I'd expect the opposite (or none at all).
I've removed/reinstalled the printer, I've removed/reinstalled cups: no difference.

---

### Post by dargaud on 2011-07-05
I removed the printer again and reinstalled it under a different name and now it works. Go figure... I'm dubious as to whether to mark this thread as 'solved'...

---

