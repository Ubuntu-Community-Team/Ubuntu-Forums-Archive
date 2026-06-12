---
title: "DVD (scd0) I/O errors (exacerbated after Suspend (ACPI))"
date: 2006-08-24
forum: Hardware &amp; Laptops
---

### Post by ultranet on 2006-08-24
Questions:
when one suspends several times, does that in any way change configuration files, such as making ACPI services that weren't running before run, or trying to enable ACPI modes of certain devices? Could that damage the hardware if ACPI software is sub-par, as i think it may be on Linux at this time?

Background:
I'm currently on a trip, and have only 2 DVDs. The one that started giving me errors, like:
[17188296.888000] sr 1:0:0:0: SCSI error: return code = 0x8000002
[17188296.888000] sr0: Current: sense key: Medium Error
[17188296.888000]     Additional sense: No seek complete
[17188296.888000] Info fld=0x0
[17188296.888000] end_request: I/O error, dev sr0, sector 0
[17188296.888000] Buffer I/O error on device sr0, logical block 0
worked fine a couple of days ago. It's a new U.S.-made DVD i bought in Canada. Before this DVD became unusable, i watched part of it cleanly, and another part of it, when it was giving me noise after every 10 minutes or so since xine/mplayer run: so i had to restart the media player every 10 minutes. Then i tried ACPI (Suspend), several times, and Hibernate several times, which i've made an effort not to use in the past. I hoped to try Suspend and Hibernate on another partition, but eventually decided to just try it on my main one.

The errors looks similar to:
[http://www.tutorialsall.com/GENTOO/SATAproblems/](http://www.tutorialsall.com/GENTOO/SATAproblems/)

However, i have another mini-DVD which works just fine. 
I will buy another DVD to hopefully rule out optical disk issues, however, the DVD that became unplayable plays just fine on Windows.

TODO:
I'll try to smart diagnostic tools suggested in thread above, but i'd appreciate any feedback on this.
I'll also try to disable acpi, once i find the syntax to do that: hopefully just for the CD/DVD disk.

---

### Post by ultranet on 2006-08-24
It doesn't look like one can use smartctl on CD/DVD drives:
root@tizosto:~# smartctl /dev/scd0
smartctl version 5.34 [i686-pc-linux-gnu] Copyright (C) 2002-5 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

root@tizosto:~# smartctl -a /dev/scd0
smartctl version 5.34 [i686-pc-linux-gnu] Copyright (C) 2002-5 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Device: TSSTcorp CDRW/DVD TSL462C Version: DE01
scsiModePageOffset: response length too short, resp_len=1 offset=4 bd_len=0
>> Terminate command early due to bad response to IEC mode page
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
root@tizosto:~# smartctl -a -T permissive /dev/scd0
smartctl version 5.34 [i686-pc-linux-gnu] Copyright (C) 2002-5 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Device: TSSTcorp CDRW/DVD TSL462C Version: DE01
scsiModePageOffset: response length too short, resp_len=1 offset=4 bd_len=0
>> Terminate command early due to bad response to IEC mode page

Error Counter logging not supported
Device does not support Self Test logging

root@tizosto:~# smartctl -d scsi -T permissive /dev/scd0
smartctl version 5.34 [i686-pc-linux-gnu] Copyright (C) 2002-5 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

---

### Post by ultranet on 2006-08-25
I've been running 
/usr/bin/time badblocks -b 512 -s -v /dev/scd0
for a couple of hours, and it appears to be stuck at:
7911792 7911792/       15452160
7911912 7911912/       15452160
        7912032/       15452160

Does that mean there's a bad block at 7912032?

---

### Post by ultranet on 2006-08-25
badblocks process is now continuously in 
uninterruptible sleep
status. Looks like i'm gonna have to kill it in an hour or so, as it's probably waiting for some IO that's never gonna go thru.

---

### Post by ultranet on 2006-08-26
For now i conclude that it's just a damaged DVD. But the fact that it plays on Window$ probably means that something could be improved on Linux, probably in the driver.

---

