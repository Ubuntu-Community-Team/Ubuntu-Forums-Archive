---
title: "Printer will only print test page"
date: 2009-06-10
forum: Hardware
---

### Post by litlfrog on 2009-06-10
We've got a printer here that's stumping us. It's an HP Deskjet 2230 connected to an Ubuntu 9.10 system by a parallel cable. The computer can print any one item to the printer correctly, but once it's gone through, no other jobs will print until the computer has rebooted. This system dual boots with Windows 2000; printing in Windows works fine. 

The computer is also set up to share the printer; *my* system (also Ubuntu 9.10) can see the printer and print a test page correctly, but I can't print any other documents--the print queue on my system will say that they printed correctly, but nothing ever prints. The boss would like us to move to an entirely Ubuntu-running office, but we can't do so until we know that shared printing will work correctly. What's the next step in identifying the problem?

---

### Post by litlfrog on 2009-06-11
Bump--anyone?

---

### Post by gradinaruvasile on 2009-06-11
Did you try to change the driver for it? 
Also you might try opening 
[http://localhost:631/admin]("http://localhost:631/admin")
in your browser. Thats the configuration page for the CUPS printing server. See if the **Share published printers connected to this system** option is checked.
You have an error log there, might help.

And its a typo or u are really using the 9.10 Ubuntu?

---

### Post by litlfrog on 2009-06-11
Sorry, Ubuntu 9.04--must have been a brainfart. :)

In CUPS, "Share published printers connected to this system" is indeed checked. Other systems can see it just fine, but the Ubuntu computers can only print a test page. The computer to which the printer is connected printed one job successfully, then right afterward tried to print an e-mail from Evolution. No error messages came up on screen; the display on the printer continues to read "Printing" about ten minutes later. Here's the log from CUPS.

> I [11/Jun/2009:10:54:01 -0400] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=10533)
I [11/Jun/2009:10:56:49 -0400] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=10556)
I [11/Jun/2009:10:56:49 -0400] [Job 76] Adding start banner page "none".
I [11/Jun/2009:10:56:49 -0400] Saving subscriptions.conf...
I [11/Jun/2009:10:56:49 -0400] [Job 76] Adding end banner page "none".
I [11/Jun/2009:10:56:49 -0400] [Job 76] File of type application/postscript queued by "anonymous".
I [11/Jun/2009:10:56:49 -0400] [Job 76] Queued on "OfficePrinter" by "anonymous".
I [11/Jun/2009:10:56:49 -0400] Saving subscriptions.conf...
I [11/Jun/2009:10:56:49 -0400] [Job 76] Started filter /usr/lib/cups/filter/pstopdf (PID 10557)
I [11/Jun/2009:10:56:49 -0400] [Job 76] Started filter /usr/lib/cups/filter/pdftopdf (PID 10558)
I [11/Jun/2009:10:56:49 -0400] [Job 76] Started filter /usr/lib/cups/filter/foomatic-rip (PID 10559)
I [11/Jun/2009:10:56:49 -0400] [Job 76] Started backend /usr/lib/cups/backend/parallel (PID 10560)
I [11/Jun/2009:10:56:49 -0400] Saving subscriptions.conf...
I [11/Jun/2009:10:56:50 -0400] Saving subscriptions.conf...
I [11/Jun/2009:10:56:52 -0400] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=10585)
I [11/Jun/2009:10:56:56 -0400] Saving subscriptions.conf...
I [11/Jun/2009:10:57:04 -0400] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=10593)
I [11/Jun/2009:10:57:15 -0400] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=10594)
I [11/Jun/2009:10:57:26 -0400] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=10595)
I [11/Jun/2009:10:57:29 -0400] [Job 76] Completed successfully.
I [11/Jun/2009:10:57:29 -0400] Saving subscriptions.conf...
I [11/Jun/2009:10:57:29 -0400] Saving subscriptions.conf...
I [11/Jun/2009:10:57:36 -0400] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=10599)
I [11/Jun/2009:10:58:47 -0400] [Job ???] Request file type is application/pdf.
I [11/Jun/2009:10:58:47 -0400] [Job 77] Adding start banner page "none".
I [11/Jun/2009:10:58:47 -0400] Saving subscriptions.conf...
I [11/Jun/2009:10:58:47 -0400] [Job 77] Adding end banner page "none".
I [11/Jun/2009:10:58:47 -0400] [Job 77] File of type application/pdf queued by "pdembro".
I [11/Jun/2009:10:58:47 -0400] [Job 77] Queued on "OfficePrinter" by "pdembro".
I [11/Jun/2009:10:58:47 -0400] Saving subscriptions.conf...
I [11/Jun/2009:10:58:47 -0400] [Job 77] Started filter /usr/lib/cups/filter/pdftopdf (PID 10615)
I [11/Jun/2009:10:58:47 -0400] [Job 77] Started filter /usr/lib/cups/filter/foomatic-rip (PID 10616)
I [11/Jun/2009:10:58:47 -0400] [Job 77] Started backend /usr/lib/cups/backend/parallel (PID 10617)
I [11/Jun/2009:10:58:47 -0400] Saving subscriptions.conf...
I [11/Jun/2009:10:58:47 -0400] Saving subscriptions.conf...
I [11/Jun/2009:10:58:48 -0400] Saving subscriptions.conf...
I [11/Jun/2009:10:58:50 -0400] Saving subscriptions.conf...
I [11/Jun/2009:10:59:25 -0400] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=10625)
I [11/Jun/2009:10:59:34 -0400] Started "/usr/lib/cups/cgi-bin/jobs.cgi" (pid=10631)
I [11/Jun/2009:10:59:57 -0400] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=10633)
I [11/Jun/2009:11:00:02 -0400] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=10800)



---

### Post by litlfrog on 2009-06-11
For the driver, I'm seeing under printer properties "hpijs 3.9.2"--is that the driver version?

---

### Post by gradinaruvasile on 2009-06-11
Yes that is the drivers version.
The print job is successful (from CUPS point of view)? Look at the jobs tab.
What was printed before Evolution (what application)?

---

### Post by litlfrog on 2009-06-11
What was printed before was a test page to the printer from CUPS. I should point out that we've tried this for a couple of weeks. It doesn't matter what application something prints from. The computer attached to that printer can always print one thing successfully, no matter what application it's from. When he tries to send further jobs, they always act like they printed successfully, but nothing will print. If he leaves the printer on and restarts the computer, the print job sent BEFORE the restart will print just fine. Attached below is the log from when the computer restarts.

> I [11/Jun/2009:12:07:48 -0400] Subscription 98 has expired...
I [11/Jun/2009:12:07:48 -0400] Saving subscriptions.conf...
I [11/Jun/2009:12:11:13 -0400] Scheduler shutting down normally.
I [11/Jun/2009:12:11:13 -0400] Saving subscriptions.conf...
I [11/Jun/2009:12:11:13 -0400] Saving job cache file "/var/cache/cups/job.cache"...
I [11/Jun/2009:12:14:16 -0400] Listening to 0.0.0.0:631 (IPv4)
I [11/Jun/2009:12:14:16 -0400] Listening to :::631 (IPv6)
I [11/Jun/2009:12:14:16 -0400] Listening to /var/run/cups/cups.sock (Domain)
I [11/Jun/2009:12:14:16 -0400] Loaded configuration file "/etc/cups/cupsd.conf"
I [11/Jun/2009:12:14:16 -0400] Using default TempDir of /var/spool/cups/tmp...
I [11/Jun/2009:12:14:16 -0400] Configured for up to 100 clients.
I [11/Jun/2009:12:14:16 -0400] Allowing up to 100 client connections per host.
I [11/Jun/2009:12:14:16 -0400] Using policy "default" as the default!
I [11/Jun/2009:12:14:16 -0400] Full reload is required.
I [11/Jun/2009:12:14:16 -0400] Loaded MIME database from "/usr/share/cups/mime" and "/etc/cups": 37 types, 65 filters...
I [11/Jun/2009:12:14:16 -0400] Loading job cache file "/var/cache/cups/job.cache"...
I [11/Jun/2009:12:14:17 -0400] Full reload complete.
I [11/Jun/2009:12:14:17 -0400] Cleaning out old temporary files in "/var/spool/cups/tmp"...
I [11/Jun/2009:12:14:17 -0400] Listening to 0.0.0.0:631 on fd 8...
I [11/Jun/2009:12:14:17 -0400] Listening to :::631 on fd 9...
I [11/Jun/2009:12:14:17 -0400] Listening to /var/run/cups/cups.sock on fd 10...
I [11/Jun/2009:12:14:17 -0400] Resuming new connection processing...
I [11/Jun/2009:12:14:17 -0400] Saving subscriptions.conf...
I [11/Jun/2009:12:14:17 -0400] [Job 77] Started filter /usr/lib/cups/filter/pdftopdf (PID 3975)
I [11/Jun/2009:12:14:17 -0400] [Job 77] Started filter /usr/lib/cups/filter/foomatic-rip (PID 3976)
I [11/Jun/2009:12:14:17 -0400] [Job 77] Started backend /usr/lib/cups/backend/parallel (PID 3977)
I [11/Jun/2009:12:14:17 -0400] Saving subscriptions.conf...
I [11/Jun/2009:12:14:17 -0400] Saving subscriptions.conf...
I [11/Jun/2009:12:22:58 -0400] Saving subscriptions.conf...
I [11/Jun/2009:12:25:08 -0400] [Job ???] Request file type is application/postscript.
I [11/Jun/2009:12:25:08 -0400] [Job 78] Adding start banner page "none".
I [11/Jun/2009:12:25:08 -0400] Saving subscriptions.conf...
I [11/Jun/2009:12:25:08 -0400] [Job 78] Adding end banner page "none".
I [11/Jun/2009:12:25:08 -0400] [Job 78] File of type application/postscript queued by "pdembro".
I [11/Jun/2009:12:25:08 -0400] [Job 78] Queued on "OfficePrinter" by "pdembro".
I [11/Jun/2009:12:26:00 -0400] Started "/usr/lib/cups/cgi-bin/jobs.cgi" (pid=4889)
I [11/Jun/2009:12:27:13 -0400] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=4890)

If, on the other hand, there's a print job in the queue and he only cycles power on the printer, here's what happens. CUPS moves the job from Pending to Processing to done without showing any errors. The printer outputs a few pages of blocky garbage and random characters.

---

### Post by gradinaruvasile on 2009-06-11
Hm. Have you tried restarting the cups server instead of the computer?
sudo service cups restart
What happens then?

---

### Post by litlfrog on 2009-06-11
OK, we've got definite progress here. I tried restarting CUPS on my computer and that at least let me print a job--finally! But for trying to print more than one job, it didn't make any difference. Here's what we DID notice. When the printer is done with a job, it still says "Printing" on the display. We tried sending jobs from two different computers until we had a short print queue ready. Whether or not we restart CUPS while doing that doesn't seem to have any effect. If we cycle power on the printer, it consistently prints the first job in its queue as gibberish, but any subsequent jobs just fine. 

Am I correct in thinking that something between the driver and the printer is not letting go of the print job successfully, since the printer continues to say it's Printing even after a job is complete? We can work around this, but it'd be a waste of ink.

---

