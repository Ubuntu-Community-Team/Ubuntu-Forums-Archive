---
title: "Computer sees Brother printer, sends job, but does not print"
date: 2015-04-20
forum: Hardware
---

### Post by marcia2 on 2015-04-20
I have tried for hours to get my new Brother HL-L2340D printer to print.  I know the printer works because my son, who has Windows, can print to it via our network.  My computer sees the printer, it will send the job to the printer, but the printer will not work.  I've tried adding the drivers via the Brother website, but I'm a newbie and don't know what else to try.  Can anyone help?

---

### Post by Merrattic on 2015-04-20
run

dpkg -l | grep Brother

in a terminal, what comes back?

---

### Post by marcia2 on 2015-04-20
ii  brgenml1cupswrapper                                   3.1.0-1                                             i386         Brother BrGenML1 CUPS wrapper driver
ii  brgenml1lpr                                           3.1.0-1                                             i386         Brother BrGenML1 LPR driver
ii  hll2340dcupswrapper                                   3.2.0-1                                             i386         Brother HL-L2340D CUPS wrapper driver
ii  hll2340dlpr                                           3.2.0-1                                             i386         Brother HL-L2340D LPR driver
ii  printer-driver-ptouch                                 1.3-8                                               amd64        printer driver Brother P-touch label printers

---

