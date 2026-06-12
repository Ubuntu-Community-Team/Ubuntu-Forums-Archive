---
title: "[SOLVED] Windows Boot Loader Always Defaults to Windows"
date: 2008-07-23
forum: General Help
---

### Post by saltandwoodsmoke on 2008-07-23
I have Wubi running on a box with Windows 2000. Currently, when the machine boots, I get to choose Windows or Ubuntu. The default is Windows 2000.

Is there a way to make the default Ubuntu?

I have edited my boot.ini to include:
 default=c:\wubi.mbr

but this doesn't appear to work. I have also edited it such that Ubuntu is first in the list of OSes to choose from. But that makes no difference either. I still have to manually select Ubuntu.

Is there a way around this?

TVM.

---

### Post by nwubie on 2008-07-23
Hi saltandwoodsmoke !

Not sure since I'm using Wubi on XP and it's possible that there's a difference between the XP and the Win2K installation but shouldn't it be **c:\wubildr.mbr** instead of c:\wubi.mbr ?

Make sure you replaced 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
by 
default=c:\wubildr.mbr
under the [boot loader] section. You can only have one default entry.

---

### Post by saltandwoodsmoke on 2008-07-24
> **nwubie said:**
> Hi saltandwoodsmoke !

Not sure since I'm using Wubi on XP and it's possible that there's a difference between the XP and the Win2K installation but shouldn't it be **c:\wubildr.mbr** instead of c:\wubi.mbr ?


Yes, that's probably what I wrote. Sorry, I wrote that from memory as I have powered down that machine. I used the same path that is listed later on in the boot.ini

---

### Post by ago on 2008-07-24
[https://wiki.ubuntu.com/WubiGuide#head-c205c4f58cdcc9bcbdc1bcdb17c1e7ca0eb79756](https://wiki.ubuntu.com/WubiGuide#head-c205c4f58cdcc9bcbdc1bcdb17c1e7ca0eb79756)

---

### Post by nwubie on 2008-07-24
Going through the startup and recovery settings to change the Default Operating System is exactly the same as editing the boot.ini file manually. Here's what your boot.ini file should look like : ```
[boot loader]
timeout=15
default=c:\wubildr.mbr
[operating systems]
c:\wubildr.mbr="Ubuntu"
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
```

---

### Post by saltandwoodsmoke on 2008-08-02
Thanks for the help. Either eidting the boot.ini or chaning the settings via computer properties did the job. Thanks very much

---

### Post by AlanInVancouverBC on 2008-08-02
> **ago said:**
> [https://wiki.ubuntu.com/WubiGuide#head-c205c4f58cdcc9bcbdc1bcdb17c1e7ca0eb79756](https://wiki.ubuntu.com/WubiGuide#head-c205c4f58cdcc9bcbdc1bcdb17c1e7ca0eb79756)

Thank you, Ago. It's so ironic that I use Windows (XP) to get Ubuntu to load first instead of XP. Another way to say goodbye to XP!:)

---

