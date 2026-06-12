---
title: "cannot print from Brother MFC 7860DW after upgrading to 18.04"
date: 2018-11-01
forum: Hardware
---

### Post by Howard Cheng on 2018-11-01
I have CUPS set up to print on my MFC 7860DW printer since 16.04.  After  upgrading to 18.04 it no longer works.  Reinstalling the drivers (from  Brother's web site) does not help.  But scanning still works.

When  I printed, CUPS thinks everything was successful.  There are no error  messages in any log files.  The printer wakes up and says "Receiving  data..." but then stops and nothing gets printed.  The printer still  works from Windows, and only stopped working after the upgrade.

Since there is no error message, I have no idea where to start with the troubleshooting.  Any ideas?

---

### Post by slickymaster on 2018-11-01
*Thread moved to **Hardware**.*

---

### Post by him610 on 2018-11-02
Please show the results, between the code tags, of this command... ```
dpkg -l | grep Brother
```

---

### Post by Howard Cheng on 2018-11-02
```

ii  brother-cups-wrapper-common                                      1.0.0-10-0ubuntu7                           amd64        Common files for Brother cups wrapper packages
ii  brother-cups-wrapper-extra                                       1.2.1-0ubuntu4                              amd64        Cups Wrapper drivers for extra brother printers
ii  brother-lpr-drivers-common                                       1.0.0-4-0ubuntu3                            amd64        Common files for brother-lpr-drivers packages
ii  brother-lpr-drivers-extra                                        1.2.0-2-0ubuntu5                            amd64        LPR drivers for extra brother printers

```

---

### Post by edadasiewicz on 2018-11-02
I don't have the same printer as you but I am running a Brother MFC 7820N.  When I run the dpkg command I get the following:

```

ii  brmfc7820nlpr:i386                              2.0.1-1                                     i386         Brother MFC-7820N LPR driver
ii  brscan-skey                                     0.2.4-1                                     amd64        Brother Linux scanner S-KEY tool
ii  brscan2                                         0.2.5-1                                     amd64        Brother Scanner Driver
ii  cupswrappermfc7820n:i386                        2.0.1-2                                     i386         Brother MFC7820N CUPS wrapper driver
ii  printer-driver-brlaser                          4-1                                         amd64        printer driver for (some) Brother laser printers
ii  printer-driver-ptouch                           1.4.2-3                                     amd64        printer driver Brother P-touch label printers

```

You may need to download some more software from Brother's website.  If I googled for your printer and went to Brother's site I noticed mfc7860dwlpr-2.1.0-1.i386.deb which is similar to my brmfc7820nlpr-2.0.1-1.i386.deb.

---

### Post by Howard Cheng on 2018-11-04
I did download the install script from them but for some reason running the script produced the deb files but did not install them.  After I installed the deb files everything works. Thanks!

---

