---
title: "gpsd: GPS device /dev/ttyUSB0 nonexistent or can't be read"
date: 2007-02-05
forum: Hardware &amp; Laptops
---

### Post by aseneca on 2007-02-05
Hey All..


Anyone have any luck with gpsd on edgy?  I used to be able to use mine on Dapper but it doesnt seem to work on edgy.  I get these errors from gpsd.

aseneca@aseneca-laptop:~$ gpsd -N -D 6 /dev/ttyUSB0 
gpsd: launching (Version 2.33)
gpsd: listening on port gpsd
gpsd: successfully connected to the DBUS system bus
gpsd: running with effective group ID 1000
gpsd: running with effective user ID 1000
gpsd: opening GPS data source at '/dev/ttyUSB0'
gpsd: device open failed: No such file or directory
gpsd: GPS device /dev/ttyUSB0 nonexistent or can't be read

aseneca@aseneca-laptop:~$ gpsd
gpsd: can't run with neither control socket nor devices


Any thoughts?

Thanks in advance!

Jason:guitar:

---

