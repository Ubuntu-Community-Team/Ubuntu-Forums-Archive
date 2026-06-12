---
title: "webmin issue"
date: 2008-12-01
forum: General Help
---

### Post by MikeL1227 on 2008-12-01
I've got what I think is a simple script running to check for the existence of a process.  Essentially it greps for the process redirecting the results then does a wc to count the lines in the output.  There should be two; the grep and the process, if all is fine.  When I run the script manually I get 'two' but when it runs via cron within webmin it returns a '5'.  It also occasionally returns a '4'.  In each case there are really only two lines in the output from the grep.  The job is below...

#!/bin/csh
cd /home/mike/cfmcmgmt
setenv DATE `date +%Y%m%d`
setenv TIME `date +%k%M`

ps aux | grep -n /cfmc/cfmc81/go/stdysrvr >t2
set a=`more t2 | wc -l` 

if $a == "5" then
else
 echo "*** $a - 8.1 processes found on $DATE at $TIME" >> log81
 ps aux | grep -n /cfmc/cfmc81/go/stdysrvr >>log81
 tail log81 > latest81
 mutt "to@location.com" -i latest81 -s "8.1 stdysrvr is down!" <blankfile
endif

---

