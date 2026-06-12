---
title: "GPL Ghostscript 9.05: Unrecoverable error on MF4370dn"
date: 2012-05-12
forum: Hardware
---

### Post by paul2 on 2012-05-12
Hi, 

I am running 64-bit Ubuntu 12.04 "precise" and I managed to install drivers for my multi-functional Canon ImageClass MF4370DN (USB) following the instructions at 

[http://ubuntuforums.org/showpost.php?p=11871878&postcount=80](http://ubuntuforums.org/showpost.php?p=11871878&postcount=80)

Everything looks ok, I could install printers and fax and something devoce that looks like scanner, but even basic printing silently does not work. The job seems to go to the queue, then is removed silently. 

I tried Printing|Help|Troubleshoot and did not receive a specific advice but was able to set debug mode and receive an error log that I am attaching as troubleshoot.txt.gz (gzipped because otherwise it exceeds 19K limit). 

The only suspicious line seems to be:

'D [12/May/2012:19:36:03 -0400] [Job 31] GPL Ghostscript 9.05: Unrecoverable error, exit code 1',

but maybe I just do not see something else. Any advice on how to fix the issue? 

TIA

---

### Post by paul2 on 2012-05-13
Problem solved, at least with printing (I have to try scanning and faxing yet) -- thanks to this, seemingly irrelevant to the issue, advice:

[http://ubuntuforums.org/showpost.php?p=11912737&postcount=93](http://ubuntuforums.org/showpost.php?p=11912737&postcount=93)

I also found a seemingly more informative error message in the log: 

'E [12/May/2012:19:36:03 -0400] [Job 31] src = libcanon_pdlwrapper.c,  line = 514, err = 0\xc2\xa5nDEBUG: PID 2405 (gs) exited with no  errors.',

Of course, there is no indication that installation of a bunch of 32-bit libraries onto 64-bit system can solve the issue (for 64-bit driver!); but maybe this will help to someone else.. 

Maybe somehow the packages created by alias miss the dependencies on those 32-bit libraries on debian and they somehow always present on rpm-based 64-bit systems?

---

