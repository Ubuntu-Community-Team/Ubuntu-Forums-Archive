---
title: "process scheduling and timing"
date: 2008-10-13
forum: Hardware
---

### Post by serenissimus on 2008-10-13
Hi,

I am working on an eee PC (due to its low power consumption - its for a remote solar installation) with 8.04 where I need to poll a measuring device over USB every second & do some simple processing with the output (textprocessing & write to file, which should not be time critical). The measuring device is specified to take up to 500 msec of reaction time until the data are available through USB.

Does anyone out there have experience which timing / process scheduling mechanism is best to use ?

I am thinking to do the low level polling as such with a C program, which can be evkoed from a perl script, which does the timing / scheduling and processing of output data. Frankly, being new to that kind of problems I do not know what perl functions to use here for the second intervals.

Or is it better to schedule a compiled C program doing one poll and the processing and schedule this through an ubuntu internal command ? I noted though that cron only counts in minute increments, so what would be a right mechanism for the scheduling here ?

Or finally, do everything in compiled C including the scheduling of the polling - again any idea on the functions to use ?

thanks in advance for creative ideas

s

---

