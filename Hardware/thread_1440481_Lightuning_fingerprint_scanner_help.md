---
title: "Lightuning fingerprint scanner help?"
date: 2010-03-27
forum: Hardware
---

### Post by tennvolsmb on 2010-03-27
So I just built this new laptop in this kit I received for going to this computer science camp. Anyways, it came built in with a fingerprint scanner and after running ```
lsusb
``` it returns ```
Bus 002 Device 002: ID 1c7a:0801 LighTuning Technology Inc. 

``` and I have searched all over this forum and google and can not seem to find what to do with it. I have tried thinkfinger and a couple of other readers, but when i get to the point to scan my finger it declares "No devices connected". Any tips would be greatly appreciated as to what to do. Thanks!

---

### Post by tennvolsmb on 2010-03-27
bump

---

### Post by frumple on 2010-07-14
Sadly EgisTech, which is the company behind the Lightuning fingerprint scanners, haven't released a Linux driver, even though they have a Linux Biometric Suite ([http://www.egistec.com/en/products/bioexcess-linux.aspx](http://www.egistec.com/en/products/bioexcess-linux.aspx)).

I have the same problem (Acer Aspire 5940g), right now the only options are to help the folks from fprint to develop a driver for this device and/or contact EngisTech enquiring about a driver release, if everybody that uses Linux and have this fingerprint scanner put a little pressure, they might do it. 

By the way, does your fingerprint reader stays hot while the notebook is in use?

Regards,
Eduardo

---

