---
title: "Input/output error"
date: 2017-10-04
forum: Hardware
---

### Post by villas-vidvei on 2017-10-04
Hi.
When I plug in my WD Ultra Passport hard drive i get this:
[ATTACH=CONFIG]276969[/ATTACH]
As I'm quite new to Ubuntu, I was wondering what to do.
My plan is to back up my entire system and do an update from 14.10 to 17.10. I appreciate tips on how to do the back up (with no loss in file quality and to be sure to get everything) when I get the hard drive to work.

Thank you.

---

### Post by Autodave on 2017-10-04
You may want to reconsider jumping to 17.10.

Every 2 years, a long term service release is made. These LTSs have a service life of 5 years: security and software updates are available for 5 years after the release.  The last LTS was 16.04. 16 stands for the year of the release, 04 stands for the month (April). The next LTS will be 18.04. Releases in the interim will be 6 month releases and only supported until the next release.

I stick with only the LTSs and even then I usually wait a month after their release before installing them. Further, I do not upgrade to them but completely install the new release after copying all files that I need to save to an external HD.

---

### Post by ian-weisser on 2017-10-04
An 'input/output error' means that the system cannot reliably communicate with the external device.
This might be due to many different possible hardware problems - motherboard controller, cable, device controller, broken motor or platter. Like a good detective, you must weed out the innocent so you can focus on the guilty.
Does the Passport work properly when plugged into different hardware?
Do other external disks work properly when plugged into this system?

---

### Post by efflandt on 2017-10-04
Is the drive connected to USB 2.0 or are you connecting it to a laptop? Portable drives often include a USB cable with 2 USB connectors because USB 2.0 is only required to supply 500 mA and a drive might need as much as 1 amp (1000 mA). USB 3.0 should supply 900 mA. Some laptops have 1 USB port up to 2 amps for devices that need more power for charging. I never had any trouble with (4) WD Passport drives, but they are older USB 2.0 drives in the 160 to 500 GB range.

See what shows up about the drive in dmesg when connected (easier to read doing **dmesg | less**) or in /var/log/syslog.

---

