---
title: "Scanner part of HP LaserJet quit working after install of Ubuntu 22 lts."
date: 2022-08-02
forum: Hardware
---

### Post by jonfisher on 2022-08-02
Scanner part of HP LaserJet quit working after install of Ubuntu 22 lts.  i've tried several scanner apps, but none of them can get the scanner  part of the printer combo to work again...

Also, some information:

```


Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version         Architecture Description
+++-==============-===============-============-===============================>
ii  hplip          3.21.12+dfsg0-1 amd64        HP Linux Printing and Imaging S>
lines 1-6/6 (END)


```

---

### Post by brian_p on 2022-08-03
Give the exact name of HP model. USB connected or network?

---

### Post by jonfisher on 2022-08-05
> **brian_p said:**
> Give the exact name of HP model. USB connected or network?

LaserJet Pro MFP M127fn
USB connected

---

### Post by jonfisher on 2022-08-08
bump

---

### Post by pqwoerituytrueiwoq on 2022-08-09
take a look at what info we can get on the scanner with these commands

[FONT=courier new]scanimage -L[/FONT]

if it does not show up try

[FONT=courier new]sudo scanimage -L[/FONT]

also run [FONT=courier new]lsusb[/FONT] to be sure the scanner/printer is detected at all (to be sure the usb cable works)

hopefully this will tell us what rabbit hole we go down next

---

