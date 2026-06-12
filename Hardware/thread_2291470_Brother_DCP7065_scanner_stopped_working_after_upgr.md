---
title: "Brother DCP7065 scanner stopped working after upgrade to 15.04"
date: 2015-08-20
forum: Hardware
---

### Post by mollie4168 on 2015-08-20
Hello,

My scanner stopped working after I upgraded.  I'm not sure whether I should go back to the original installation instructions I used and start over, or is there a package I should update?  I saw that other people were having this problem with other scanners.  The printer is still working.

Thanks.

---

### Post by mollie4168 on 2015-08-20
I went back over the steps I took to originally install it, and it looked like all the packages were up to date.  I deleted the printer and re-added it from the Printers menu.  Still can't scan.  The error message I get when I try to open gscan2pdf is: Error opening device: Invalid argument

---

### Post by mollie4168 on 2015-08-24
I went to the Brother website and followed their instructions to install the scanner driver, but I still get the same error message.  

Does the following give any clues about what's going on?

[HTML]$ dpkg -l | grep Brother
ii  brscan-skey                                          0.2.4-1                                    amd64        Brother Linux scanner S-KEY tool
ii  brscan4                                              0.4.3-2                                    amd64        Brother Scanner Driver
ii  cupswrapperdcp7065dn                                 2.0.4-2                                    i386         Brother DCP7065DN CUPS wrapper driver
ii  dcp7065dnlpr                                         2.1.0-1                                    i386         Brother DCP-7065DN LPR driver
ii  printer-driver-brlaser                               3-3                                        amd64        printer driver for (some) Brother laser printers
ii  printer-driver-ptouch                                1.3-8ubuntu1                               amd64        printer driver Brother P-touch label printers[/HTML]

---

### Post by mollie4168 on 2015-09-24
Bump.

Anything?  It would be very useful to have my scanner back.  I appreciate any help that people can provide.  I tried re-installing it again, and that's clearly not the issue.  I don't know enough, and I can find any posts to help me beyond that.

---

