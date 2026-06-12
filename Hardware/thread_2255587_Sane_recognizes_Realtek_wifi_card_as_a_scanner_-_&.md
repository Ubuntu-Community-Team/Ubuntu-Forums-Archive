---
title: "Sane recognizes Realtek wifi card as a scanner - &quot;floating point exception&quot;"
date: 2014-12-06
forum: Hardware
---

### Post by krzysiekkarolak1 on 2014-12-06
Hello,

I am using Ubuntu on my ARMv7 device and I have a problem with configuring HP scanner with sane. It's recognized via "sane-find-scanner" command, here is the output:
```
found USB scanner (vendor=0x0bda [Realtek], product=0x8176 [802.11n WLAN Adapter]) at libusb:004:002
found USB scanner (vendor=0x03f0 [HP], product=0x7811 [Deskjet Ink Advant K209a-z]) at libusb:001:003

```
As you can see it recognizes Realtek WiFi card as a scanner. Output of "scanimage -L" and "xsane" commands is always "Floating point exception".
I think that the problem is with wifi card wrongly recognized as a scanner. Can I blacklist it in Sane in any way?

My device is Allwinner A10 with Ubuntu 12.04 installed.

Thanks.

---

### Post by pqwoerituytrueiwoq on 2014-12-09
can you try a newer version of scanimage? like what ever version is in 14.10
i have had so many crashes with scanimage on 12.04-14.04, it worked fine on 10.04 and 14.10
i put 14.10s scanimage on 14.04 and it works now
if you can get these installed it should work, unless your wifi card is to blame (even then that may be fixed in the new version)
* libsane_1.0.24-1.1
* sane-utils_1.0.24-1.1
* libsane-common_1.0.24-1.1
not sure if it will install on 12.04 though

if you temparally remove your wifi card you can see if it works without it

---

### Post by krzysiekkarolak1 on 2014-12-11
Thank You! After updating packages to 1.0.24 it still recognizes wifi card as a scanner but "Floating point exception" error gone and HP scanner works.

---

