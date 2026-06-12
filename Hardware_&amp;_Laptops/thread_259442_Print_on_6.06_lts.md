---
title: "Print on 6.06 lts"
date: 2006-09-17
forum: Hardware &amp; Laptops
---

### Post by dwcasey on 2006-09-17
Canon Pixma MP500, using info from linuxprinting.org.

I believe I have all the files installed correctly, but I am unable to get anything to print with this driver.

I've tried a different drivers in CUPS and have had mixed results...bad/missing color mostly.

Also tried to demo version of TurboPrint and it worked great.

So I went back to try to get the MP500 drivers from the JP Canon site.  This is what lpstat -t is showing me:

dwcasey@apollo:/usr$ lpstat -t
scheduler is running
system default destination: MP500-Ver.2.60
device for MP500-Ver.2.60: cnij_usb:/dev/usblp0
MP500-Ver.2.60 accepting requests since Sun 17 Sep 2006 10:45:43 AM CDT
printer MP500-Ver.2.60 is idle.  enabled since Sun 17 Sep 2006 10:45:43 AM CDT
dwcasey@apollo:/usr$ lpstat -t
scheduler is running
system default destination: MP500-Ver.2.60
device for MP500-Ver.2.60: cnij_usb:/dev/usblp0
MP500-Ver.2.60 accepting requests since Sun 17 Sep 2006 10:46:27 AM CDT
printer MP500-Ver.2.60 disabled since Sun 17 Sep 2006 10:46:27 AM CDT -
        No %%BoundingBox: comment in header!
MP500-Ver.2.60-15       dwcasey         153600   Sun 17 Sep 2006 10:46:16 AM CDT
dwcasey@apollo:/usr$ lpstat -t
scheduler is running
system default destination: MP500-Ver.2.60
device for MP500-Ver.2.60: cnij_usb:/dev/usblp0
MP500-Ver.2.60 accepting requests since Sun 17 Sep 2006 10:46:57 AM CDT
printer MP500-Ver.2.60 disabled since Sun 17 Sep 2006 10:46:57 AM CDT -
        Unable to open USB port device file: No such file or directory
MP500-Ver.2.60-15       dwcasey         153600   Sun 17 Sep 2006 10:46:16 AM CDT

---

