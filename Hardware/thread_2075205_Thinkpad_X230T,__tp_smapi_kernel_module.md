---
title: "Thinkpad X230T,  tp_smapi kernel module"
date: 2012-10-23
forum: Hardware
---

### Post by maxchen on 2012-10-23
OS: Ubuntu X64

check the Battery information
```
cat /proc/acpi/battery/BAT0/info
```Then, I install tp_smapi kernel module
```
sudo apt-get install tp-smapi-dkms
sudo modprobe tp_smapi
```FATAL: *Error* inserting [I]tp_smapi
[/I]
any help?

---

### Post by maxchen on 2012-11-16
start windows 7, set the threshold. 
Back to Ubuntu 12.04, the thresholds are working!

---

### Post by linrunner on 2012-11-17
Hi,

unfortunately tp-smapi doesn't work with Ivy Bridge models. Instead you have to use tpacpi-bat/acpi_call. You may use [TLP]("http://linrunner.de/tlp") to do this.

---

### Post by maxchen on 2012-11-26
thanks!

from  [http://linrunner.de/en/tlp/docs/tlp-configuration.html](http://linrunner.de/en/tlp/docs/tlp-configuration.html) , I found that
"Hint: the charging process is not controlled by software, but by hardware. TLP just writes the thresholds to the hardware registers (via tp-smapi or tpacpi-bat)."

Thus I set the thresholds in win 7 works, I do not need to install TLP or tp-smapi-dkms

---

### Post by linrunner on 2012-11-26
Damn. I shouldn't have written that one into the docs ;).

In case you don't want to optimize power consumption any further from plain vanilla Ubuntu –  then you don't need TLP.

---

### Post by maxchen on 2012-11-26
Thanks for your great work, I really appreciate it.

---

### Post by linrunner on 2012-11-27
You're welcome :).

---

