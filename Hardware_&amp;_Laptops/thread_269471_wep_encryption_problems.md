---
title: "wep encryption problems"
date: 2006-10-01
forum: Hardware &amp; Laptops
---

### Post by jj05y on 2006-10-01
Hey, i have a problem connecting to my wireless router when wep is enabled, 
but if i disactive wep then i can connect fine, i am using an ascii passphrase, ne one got ne idea's??

---

### Post by Mr Frosti on 2006-10-01
Is this using the Network monitor tool, or something else? If you are having issues connecting, what error are you receiving (if any)? Try pasting the results of the following command below:

```
tail /var/log/dmesg
```

---

### Post by jj05y on 2006-10-01
its wen i go in2 network settings, clik onmy wirless connection, select the connection, n type in the network key, if i enable wep, it just times out, n goes bak 2 wat the settings were b4 i hit ok, 
if wep is disabled then afta bout 2 seconds it connects fine,


here;s wat that code givies me,

jj05y@bill:~$ tail /var/log/dmesg
[17179597.652000] sd 3:0:0:1: Attached scsi generic sg2 type 0
[17179597.656000]   Vendor: GENERIC   Model: USB Storage-SMC   Rev: 019A
[17179597.656000]   Type:   Direct-Access                      ANSI SCSI revisio n: 00
[17179597.656000] sd 3:0:0:2: Attached scsi removable disk sdd
[17179597.656000] sd 3:0:0:2: Attached scsi generic sg3 type 0
[17179597.656000]   Vendor: GENERIC   Model: USB Storage-MSC   Rev: 019A
[17179597.656000]   Type:   Direct-Access                      ANSI SCSI revisio n: 00
[17179597.660000] sd 3:0:0:3: Attached scsi removable disk sde
[17179597.660000] sd 3:0:0:3: Attached scsi generic sg4 type 0
[17179597.660000] usb-storage: device scan complete
jj05y@bill:~$

---

### Post by Monkus on 2006-10-01
I had the same problem. I was using 40-bit encryption and found that I needed my acsii password to be 5 or 13 characters. You may want to try that out.

---

### Post by jj05y on 2006-10-02
no banana's, if the passphrase is 5 charatcers long its for 40 bit encrytion, its its 13 characters long its for 128 encrytion, i've tried both o these, no joy, grr, is there ne one who has it workin?  am i missing something??](*,) ](*,) ](*,) ](*,)

---

