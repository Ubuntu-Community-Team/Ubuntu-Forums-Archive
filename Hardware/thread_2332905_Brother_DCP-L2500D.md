---
title: "Brother DCP-L2500D"
date: 2016-08-05
forum: Hardware
---

### Post by pema01 on 2016-08-05
Hi,
I've bought a new printer All-in-one Brother DCP-L2500D. After the installation of drivers, it prints well and scans well from PC, too. However, when I'm trying to scan from printer button - I click "scan" then the display says, that it is connecting with PC, but nothing is happening on my PC.

Here is some report of the command ```
dpkg -l | grep -i brother
```
```
ii  brgenml1cupswrapper:i386                    3.1.0-1                                    i386         Brother BrGenML1 CUPS wrapper driverii  brgenml1lpr:i386                            3.1.0-1                                    i386         Brother BrGenML1 LPR driver
ii  brother-udev-rule-type1                     1.0.0-1                                    all          Brother udev rule type 1
ii  brscan-skey                                 0.2.4-1                                    amd64        Brother Linux scanner S-KEY tool
ii  brscan4                                     0.4.3-3                                    amd64        Brother Scanner Driver
ii  dcpl2500dcupswrapper:i386                   3.2.0-1                                    i386         Brother DCP-L2500D CUPS wrapper driver
ii  dcpl2500dlpr:i386                           3.2.0-1                                    i386         Brother DCP-L2500D LPR driver
ii  printer-driver-brlaser                      3-5~ubuntu1                                amd64        printer driver for (some) Brother laser printers
ii  printer-driver-ptouch                       1.4-1                                      amd64        printer driver Brother P-touch label printers



```

Thank you.

---

### Post by kurt18947 on 2016-08-05
I know nothing about using the 'scan' key beyond brscan-skey must be installed which you appear to have. I just tried my Brother MFD and it scanned placing the image in /home/brscan. I find gscan2pdf more useful for my purposes. I don't know if you will find this of use or not:

[http://support.brother.com/g/s/id/linux/en/instruction_scn4.html?c=us_ot&lang=en&comple=on&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_scn4.html?c=us_ot&lang=en&comple=on&redirect=on)

---

### Post by Bucky Ball on 2016-08-05
I use Simple Scan. It's in the repositories. Might work for you.

---

### Post by pema01 on 2016-08-05
Ok, I'm glad it works from PC, so I'll use XSane or gscan2pdf. Thanks

---

