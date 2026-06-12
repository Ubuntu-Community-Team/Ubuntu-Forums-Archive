---
title: "Fingerprint reader Validity VFS451 support"
date: 2011-03-27
forum: Hardware
---

### Post by sbrbot on 2011-03-27
I've got **HP 2540p EliteBook** with fingerprint reader **Validity Inc. model VFS451 (ID=138a:0007)** recognised by Ubuntu 10:10 (64bit) as Digital Persona Inc. Has anyone succeeded to install and run it under Ubuntu?

---

### Post by krazyd on 2011-03-27
Work is ongoing:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285089](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285089)
[http://lists.reactivated.net/pipermail/fprint/2011-March/](http://lists.reactivated.net/pipermail/fprint/2011-March/)

---

### Post by sbrbot on 2011-03-28
Some people reported the patched driver works but for 138a:0001 fingerprint reader. I also successfully patched, compiled and installed this driver on my machine but it seems it does not work for my fingerprint reader model 138a:0007.

---

### Post by sbrbot on 2011-03-30
I created new bug report for vfs451:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/745505](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/745505)

---

### Post by ProBook on 2011-06-07
Bug confirmed on HP ProBook 5320m.
```
Bus 001 Device 003: ID 138a:0007 Validity Sensors, Inc. VFS451 Fingeprint Reader
```Following this guide [https://launchpad.net/~fingerprint/+archive/fprint]("https://launchpad.net/%7Efingerprint/+archive/fprint") the application *fprint project demo* shows: "Status: No devices found."

---

### Post by binukavumkal on 2012-07-15
Bug Confirmed in HP ProBook 6450b
Bus 001 Device 004: ID 138a:0007 Validity Sensors, Inc. VFS451 Fingeprint Reader

---

### Post by ppihus on 2013-01-22
> **ProBook said:**
> Bug confirmed on HP ProBook 5320m.
```
Bus 001 Device 003: ID 138a:0007 Validity Sensors, Inc. VFS451 Fingeprint Reader
```Following this guide [https://launchpad.net/~fingerprint/+archive/fprint]("https://launchpad.net/%7Efingerprint/+archive/fprint") the application *fprint project demo* shows: "Status: No devices found."

I wonder if there's any news with this?

---

