---
title: "newer amd fglrx installation?  4k(SST 60Hz) and 30&quot; Monitors"
date: 2014-08-25
forum: Hardware
---

### Post by ivo-welch on 2014-08-25
I am trying to get both an asus 4k monitor (60Hz, SST, DP1.2) and a 30" DELL monitor (2560x1600) to work together in gubuntu 14.04.1 on the RADEON 7700.  right now, I am running the standard fglrx driver installed from the ubuntu repositories, which is 2:13.350.1-0ubuntu2 .  I can confirm that , either monitor is detected and run correctly.  in particular, the ASUS 28" monitor, after switching it to DP 1.2 in the monitor menu from the default DP 1.1, comes up at 60Hz after boot if it is alone.  (suggestion: in accessibility, use "large fonts".)

the radeon card sees both monitors, but wants to put nonsense on the screens.  When both monitors are on, the Asus displays only half the screen and the DELL is blank.  they can identify well, using the little red number, and both monitors are telling me that they are driven with the right resolutions.  so, it is a software issue.

at this point, I presume the correct thing to try is to update the amd fglrx driver.  on the amd website, they are up to fglrx 14.201.1005 .

what is the recommended way to do this on a system that already has an amd radeon driver from the ubuntu repositories installed?  should I download the AMD binary and run it from the amd website?  (it warns me that I need all prerequisites and then complains that [[ for lokixml.sh is not found although it continues, at which point I panic and abort.)  or is there a newer version on a ubuntu website that I should use?  there are also reports on the web that there are kernel conflicts. 

advice appreciated.

/iaw

---

