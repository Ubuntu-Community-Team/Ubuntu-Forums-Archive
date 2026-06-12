---
title: "ati driver on ubuntu 11.10"
date: 2011-10-27
forum: Hardware
---

### Post by eslam on 2011-10-27
hi, 
i have ubuntu oneiric x64 installed on my lenovo G570 laptop
and i have a problem in ati drivers installation 
basically when my laptop was holding ubuntu 11.04 x64 , the ati driver has no effect on it 

on oneiric i found new driver "post-release updates" when i tried to activate it i get those messages from log file 
/var/log/jockey.log
> 2011-10-27 17:33:12,909 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-27 17:33:12,910 DEBUG: fglrx_updates is not the alternative in use
2011-10-27 17:33:12,971 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-27 17:33:12,972 DEBUG: fglrx_updates is not the alternative in use
2011-10-27 17:33:13,334 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2011-10-27 17:33:13,434 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2011-10-27 17:33:13,543 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-27 17:33:13,543 DEBUG: fglrx_updates is not the alternative in use
2011-10-27 17:33:13,592 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-27 17:33:13,593 DEBUG: fglrx_updates is not the alternative in use
2011-10-27 17:33:15,217 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-27 17:33:15,218 DEBUG: fglrx_updates is not the alternative in use
2011-10-27 17:33:15,277 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-27 17:33:15,278 DEBUG: fglrx_updates is not the alternative in use
2011-10-27 17:33:15,372 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-27 17:33:15,373 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-27 17:33:15,557 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-27 17:33:15,558 DEBUG: fglrx_updates is not the alternative in use
2011-10-27 17:33:15,618 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-27 17:33:15,619 DEBUG: fglrx_updates is not the alternative in use
2011-10-27 17:33:15,712 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-27 17:33:15,713 DEBUG: fglrx_updates is not the alternative in use
2011-10-27 17:33:15,775 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-27 17:33:15,776 DEBUG: fglrx_updates is not the alternative in use
2011-10-27 17:33:15,863 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-27 17:33:15,864 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking

```
lspci | grep -i vga

```

> 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: ATI Technologies Inc Robson CE [AMD Radeon HD 6300 Series]
so if any recommendations regarding this issue would be great
Thanks in advance

---

### Post by ansiktsburk on 2011-11-07
Did you solve the problem?

---

### Post by BillyBoa on 2011-11-07
You have to read this:
[ubuntu] ati fgrlrx grafics driver(post-release updates) issue/question?
[http://ubuntuforums.org/showthread.php?p=11413368](http://ubuntuforums.org/showthread.php?p=11413368)

---

### Post by BillyBoa on 2011-11-07
And this as well:
[all variants] fglrx alternatives problem refuses to install
[http://ubuntuforums.org/showthread.php?p=11385354#post11385354](http://ubuntuforums.org/showthread.php?p=11385354#post11385354)

---

### Post by sundman on 2011-11-07
It seems that jockey won't (ever) reconize the driver.

To get the latest driver, install the packages
```

aptitude install fglrx-updates fglrx-amdcccle-updates

```

I can be necessary to configure the driver
```

dpkg-reconfigure fglrx-updates

```

---

### Post by iondoarion on 2011-12-05
I am using ATI Radeon 6370 M

This link worked for me:

 [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx) 

Hope it helps you as well.

TYVM to the person/s that made the guide.

---

