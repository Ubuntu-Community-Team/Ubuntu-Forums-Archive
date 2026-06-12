---
title: "suspend2ram ibm thinkpad r50e"
date: 2005-05-10
forum: Hardware &amp; Laptops
---

### Post by kaltertee on 2005-05-10
Hey
generouly everythink works, I only don't get standby to work.
I used 'echo 3 > /proc/acpi/sleep', and my TP goes down. 'Everything fine' I thought but it did not wake up again. I pressed Fn, and it startet to resume but just the Displaylight came back. You see 'stopping Tasks =====|' but nothing else. It's also unpossible to ping it. so I believe it is not able to resume. 
I tryed to BootParameter: acpi_sleep=s3_bios but it does not help.
Anyone an Idea how to get standby?? suspend2disk works fine!
THX for reading simon

---

### Post by hyperboloid on 2005-06-06
I'm having the same problem with a Thinkpad T41. It's driving me crazy.  I've tried everything I can find on these forums, to no avail.  ](*,)  Thinking of switching back to Gentoo. Seems like Ubuntu has a ways to go yet for laptop support.

All I can suggest is to file a bug report. Unless people report bugs, they don't get fixed. I think this is a bug in Ubuntu/ACPI/Thinkpad interaction. 

Good luck. Let me know if you solve it...

---

### Post by kaltertee on 2006-03-05
in /etc/acpi/sleep.sh
```
..
..
 echo -n $ACPI_SLEEP_MODE >/sys/power/state
..
..
```
 durch
```
..
..
 ## R50e get state
 cat /proc/bus/pci/00/02.0 > /var/cache/video.config
 echo -n $ACPI_SLEEP_MODE >/sys/power/state
 ## R50e write state back
 cat /var/cache/video.config > /proc/bus/pci/00/02.0
 ## R50e clean up
 rm -rf /var/cache/video.config
..
..
```
ersetzen

---

