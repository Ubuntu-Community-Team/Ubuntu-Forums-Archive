---
title: "Printer not connecting?"
date: 2008-06-18
forum: Hardware
---

### Post by LeeM on 2008-06-18
Hi!
Several days ago, I lost the ability to print! I am running 8.04 Kubuntu. No changes in that since the printer was running ok. The printer is a Canon IP3000. Printer jobs stack up, and KJobViewer says the job at the top of the stack is "Processing", but nothing ever happens. It also says:
Device: usb://canon/iP3000
Model: Canon PIXMA ip3000 - CUPS+Gutenprintv5.0.2 Simplified

When I look at the job report on the "processing" job on Printer System Settings I see:

Attribute
Values
job-more-info  ipp://localhost:631/jobs/2158
job-printer-up-time  Wed Jun 18 21:07:56 2008
job-state-reasons  job-printing
job-uri  ipp://localhost:631/jobs/2158
printer-uri  ipp://localhost/printers/iP3000
job-originating-user-name  lee
job-name  recomma.plx
document-format  text/plain
media  Letter
sides  one-sided
finishings  0x3
copies  1
job-hold-until  no-hold
job-priority  50
number-up  1
job-sheets none none
job-uuid  urn:uuid:b72fac19-4571-34a2-5c57-348f245404b1
job-originating-host-name  localhost
time-at-creation  Wed Jun 18 21:06:41 2008
time-at-processing  Wed Jun 18 21:07:40 2008
time-at-completed 
job-id  2158
job-state  0x5
job-media-sheets-completed  0
job-printer-uri  ipp://lee-desktop:631/printers/iP3000
job-name  recomma.plx
job-k-octets  1
job-printer-state-message  Gutenprint Ready to print.
job-printer-state-reasons  connecting-to-device



Could someone clue me in to what else to look at, to pin down the problem?

Thanks!

---

### Post by editrix on 2008-06-19
I found your post because I can't even install my ["]HP Deskjet 3847]("http://ubuntuforums.org/showthread.php?t=834212[/URL).

So while I can't help, I can at least bump, and maybe whoever answers you will help me, too. 

You say "no changes" but if you updated the kernel, that may have done it.

---

### Post by eudemus on 2009-06-16
I have just this issue .... what has happened?

---

