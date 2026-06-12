---
title: "Install Brother MFC-J475DW Driver"
date: 2020-12-16
forum: Hardware
---

### Post by shane_faulkinbury2 on 2020-12-16
I'm trying to install the driver for my Brother MFC-J475DW that I downloaded from Brother.  The installation guide says do this.
> 
[LIST]
[*]Turn on the printer and connect the usb, network or parallel cable.
[*]Go to the directory where the driver is.
[*]Install LPR driver.The install process may take some time. Please wait until it is complete.
**Command  :  dpkg -i --force-all  (lpr-drivername)**
[*]Check if the LPR driver is installed.
**Command  :  dpkg -l  |  grep  Brother**
[/LIST]


This is what I get when doing that.
```
dpkg -i --force-all mfcj425wlpr-3.0.1-1.i386.deb(Reading database ... 208837 files and directories currently installed.)
Preparing to unpack mfcj425wlpr-3.0.1-1.i386.deb ...
Unpacking mfcj425wlpr:i386 (3.0.1-1) over (3.0.1-1) ...
Setting up mfcj425wlpr:i386 (3.0.1-1) ...
mkdir: cannot create directory &#8216;/var/spool/lpd/mfcj425w&#8217;: No such file or directory
chown: cannot access '/var/spool/lpd/mfcj425w': No such file or directory
chgrp: cannot access '/var/spool/lpd/mfcj425w': No such file or directory
chmod: cannot access '/var/spool/lpd/mfcj425w': No such file or directory
```

Apparently the ```
/var/spool/lpd/mfcj425w&#8217;
``` wasn't made.

Can anyone help?

---

### Post by shane_faulkinbury2 on 2020-12-16
Sorry again.  I figured it out.  I had the wrong .deb.  I was supposed to get the .deb for the 475 and I got the one for the 425.  All is fixed now and I'm printing and scanning fine.

---

