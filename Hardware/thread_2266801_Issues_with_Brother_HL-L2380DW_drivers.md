---
title: "Issues with Brother HL-L2380DW drivers"
date: 2015-02-25
forum: Hardware
---

### Post by azile19 on 2015-02-25
I have a desktop, now running 14.10, and a brother HL-L2380DW printer.  Because this was my work computer, I was recently forced to put windows on it and dual boot.  Previously, it was running the Dell-installed Ubuntu 12.04, which I had upgraded to 14.10.  After the wipe, I installed a fresh version of 14.10.  Previously, I was able to print no problem after installing the drivers from the brother website.  I tried using both the drivers they listed specifically for my model, and their generic drivers.  However, now , I appear to have installed the drivers correctly, and the printer appears in my printer list, but when I print anything (a test page or an actual file), nothing happens.  How do I debug this problem?

As a related issue, I have never gotten the scanner working on this machine, but getting the printer working is a bigger priority right now.

Current output of dpkg -l | grep Brother:

```
liz@Faramir:~/Downloads/printer$ dpkg -l | grep Brother
ii  brgenml1cupswrapper                                  3.1.0-1                                  i386         Brother BrGenML1 CUPS wrapper driver
ii  brgenml1lpr                                          3.1.0-1                                  i386         Brother BrGenML1 LPR driver
ii  brscan4                                              0.4.3                                    amd64        Brother Scanner Driver
ii  hll2380dwcupswrapper                                 3.2.0-1                                  i386         Brother HL-L2380DW CUPS wrapper driver
ii  hll2380dwlpr                                         3.2.0-1                                  i386         Brother HL-L2380DW LPR driver
ii  printer-driver-brlaser                               3-3                                      amd64        printer driver for (some) Brother laser printers
ii  printer-driver-ptouch                                1.3-8                                    amd64        printer driver Brother P-touch label printers

```

---

### Post by azile19 on 2015-02-25
Also, the recent stuff from the cups error log, var/log/cups/error_log: 

```

E [25/Feb/2015:11:01:40 -0500] [Client 23] Returning IPP client-error-bad-request for Print-Job (ipp://localhost/printers/Brother-HL-L2380DW-series) from localhost
E [25/Feb/2015:11:55:03 -0500] [Client 19] Returning IPP client-error-bad-request for Print-Job (ipp://localhost/printers/HLL2380DW) from localhost
E [25/Feb/2015:11:55:12 -0500] [Client 19] Returning IPP client-error-bad-request for Print-Job (ipp://localhost/printers/HLL2380DW) from localhost
E [25/Feb/2015:11:56:16 -0500] [Client 19] Returning IPP client-error-bad-request for Print-Job (ipp://localhost/printers/HLL2380DW) from localhost

```

---

### Post by pdc on 2015-02-26
there are some recent cups updates: if you make sure your system is up to date ............

______________

I can only suggest removing the Brother registration you have set up (ie open PRINTERS and delete what is there ..................) and set it up again ..........after the CUPS updates 

______________

a more structured approach would be to follow the Ubuntu wiki [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

-__________________________

 >  Previously, it was running the Dell-installed Ubuntu 12.04, which I had upgraded to 14.10 

I am always intrigued to read such things.............. many 12.04 because it is a LTS (long-term support) so it should be good until April 2017 whereas the upgraded and "improved" 14.10 runs out in six months ......... no support, no updates ............ [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS) and 14.04 (LTS) is good till April 2019 ............ just curious as a new release can have issues that are found by those that install the new release ...........those lagging behind on the LTS gratefully let those going ahead run into issues and trouble-shoot them

---

