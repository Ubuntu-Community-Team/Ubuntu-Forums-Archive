---
title: "Brother AIO DCP-7065DN Scanner not working. Printer fine (USB)"
date: 2013-10-18
forum: Hardware
---

### Post by vap1485 on 2013-10-18
[INDENT] 					Greetings. I'm on 12.04 and I went through this process, installed  the correct drivers and the scanner program does recognize my DCP7065DN.
[http://ubuntuforums.org/showthread.php?t=2039840](http://ubuntuforums.org/showthread.php?t=2039840) <---that's the thread I followed, only getting the printer to work

When I hit scan it tells me 


"Failed to scan
Unable to start scan"

Any idea what's happening?


dpkg -l | grep Brother
ii  brother-udev-rule-type1                     1.0.0-1                                 Brother udev rule type 1
ii  brscan-skey                                 0.2.4-1                                 Brother Linux scanner S-KEY tool
ii  brscan4                                     0.4.1-6                                 Brother Scanner Driver
ii  cupswrapperdcp110c:i386                     1.0.2-3                                 Brother DCP110C CUPS wrapper driver
ii  cupswrapperdcp7065dn:i386                   2.0.4-2                                 Brother DCP7065DN CUPS wrapper driver
ii  dcp110clpr:i386                             1.0.2-1                                 Brother lpr Inkjet Printer Definitions
ii  dcp7065dnlpr:i386                           2.1.0-1                                 Brother DCP-7065DN LPR driver
ii  printer-driver-ptouch                       1.3-3ubuntu0.1                           printer driver Brother P-touch label printers

XSANE says
"Failed to start scanner: Invalid argument" 				
[/INDENT]

---

### Post by Jess_Mey on 2014-02-17
Brother DCP-7065dn and Ubuntu 13

Prints only horizontally and I can not scan

jesus@jesus-All-Series:~/Descargas$ dpkg -l | grep Brother 
ii  brother-udev-rule-type1                   1.0.0-1                                       all          Brother udev rule type 1
ii  brscan-skey                               0.2.4-1                                       i386         Brother Linux scanner S-KEY tool
ii  brscan4                                   0.4.2-1                                       i386         Brother Scanner Driver
ii  cupswrapperdcp7065dn                      2.0.4-2                                       i386         Brother DCP7065DN CUPS wrapper driver
ii  dcp7065dnlpr                              2.1.0-1                                       i386         Brother DCP-7065DN LPR driver
ii  printer-driver-ptouch                     1.3-6                                         i386         printer driver Brother P-touch label printers

XSANE says
"Failed to start scanner: Invalid argument"

---

### Post by foresto on 2014-03-11
After finding that Brother's instructions for the DCP-7065DN scanner simply did not work on a 64-bit system, I purged their 32-bit scanner packages and installed their 64-bit ones. That did the trick.

64-bit packages live here:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan4](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan4)

My original post is here:
[http://ubuntuforums.org/showthread.php?t=2039840&page=2&p=12953916#post12953916](http://ubuntuforums.org/showthread.php?t=2039840&page=2&p=12953916#post12953916)

---

### Post by markcgriffiths2 on 2014-05-03
The scanner does not work or me too.  Do I need to change any files?  Like 40-libsane.rules?

Here is some info

```
 dpkg -l | grep Brother
ii  brother-udev-rule-type1                               1.0.0-1                                             all          Brother udev rule type 1
ii  brscan-skey                                           0.2.4-1                                             amd64        Brother Linux scanner S-KEY tool
ii  brscan4                                               0.4.2-1                                             amd64        Brother Scanner Driver
ii  cupswrapperdcp7065dn                                  2.0.4-2                                             i386         Brother DCP7065DN CUPS wrapper driver
ii  dcp7065dnlpr                                          2.1.0-1                                             i386         Brother DCP-7065DN LPR driver
ii  printer-driver-ptouch                                 1.3-8                                               amd64        printer driver Brother P-touch label


```

---

### Post by pdc on 2014-05-04
[http://ubuntuforums.org/showthread.php?t=2221836&p=13012699#post13012699](http://ubuntuforums.org/showthread.php?t=2221836&p=13012699#post13012699)

......seems like it worked for Brad ..........

__________________-

however I notice your list of Brother packages says > [COLOR="#EE82EE"]Brother udev rule type 1[/COLOR]

I think that is the file Brother list here [http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04) and it is [COLOR="#008000"]brother-udev-rule-type1-1.0.0-1.all.deb[/COLOR]

(I am guessing it does what editing the file does, as in the thumbnail I enclose...............so I am wondering if you ran that command ..........and if you did, why it didn't seem to work..............if you open the file with gedit; without having sudo in front, you have read-only powers and have a check if that Brother mention is already there...............

so just to look do > [COLOR="#FF0000"]gedit /lib/udev/rules.d/40-libsane.rules[/COLOR]

.........and if you want to edit the file, close gedit; and then issue this command > [COLOR="#FF0000"]gksudo gedit /lib/udev/rules.d/40-libsane.rules[/COLOR]

---

### Post by markcgriffiths2 on 2014-05-05
Thanks a lot, it works now.

---

