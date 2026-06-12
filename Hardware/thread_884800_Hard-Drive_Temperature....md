---
title: "Hard-Drive Temperature..."
date: 2008-08-09
forum: Hardware
---

### Post by TenPlus1 on 2008-08-09
Did you know that hard-drive temperatures above 45 degrees celcius can corrupt your data ? (unless otherwise stated by manufacturer)...

What is your HDD temperature ?

Mines is a Maxtor 6L160P0 running at 33oC

----

sudo apt-get install hddtemp  <-- you dont need to have it running as a service btw.

sudo hddtemp /dev/hda

or

sudo apt-get install smartmontools  <-- reads S.M.A.R.T info from drive (smartctl -s on /dev/hda  to enable)

sudo smartctl --all /dev/hda |grep Temperature_Celsius

---

### Post by ThaRabbit on 2008-08-09
Just to calm some people down: 

Yes, increased temperatures above drive spec can (will) decrease HDD lifetime, but 45 degrees is within the typical hard drive operating spec. 

Most manufacturers spec their drives to +5 to +50 / 55 degrees centigrade. Newer drives are specc'd to 60.

If you're worried, simply check your hard drive's manufacturer's website, all of them offer data sheets listing the operating temperatures to which they are specc'd.

For convenience you might choose to run hddtemp as a service and install the sensors-applet package. This can read-out drive temperature live, though I would urge you to set the refresh rate a little higher than the default 2 seconds.

As a benchmark, you could let your system to an intensive task (copy a big file from folder to folder on the same drive) for roughly 10 minutes, polling drive temperature while you're doing so. This should give you an indication of your drive's temps under high load.

---

