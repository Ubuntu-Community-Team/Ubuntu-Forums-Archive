---
title: "[refind][nvidia]Change boot to 1080p"
date: 2016-10-02
forum: Hardware
---

### Post by pnvlarsen on 2016-10-02
So I just changed monitors from a 1600x900 to a proper 1080p monitor, and I've realised that the computer doesn't boot in 1080 - i confirmed this with
```
dmesg | grep -i EFI
```
I'm using refind and the EFI stub to boot, and so i changed my refind.conf file to use 1920*1080, but that just gives me an error message saying its unsupported. 

For the record, I'm using a gtx1070 as my graphics card, and using the latest nvidia drivers, if that helps.

---

### Post by Bucky Ball on 2016-10-03
Welcome. Which 'latest NVidia driver' are you using and which release of Ubuntu?

>  For the record, I'm using a gtx1070 as my graphics card, and using the latest nvidia drivers, if that helps. 

As your support request is about a graphics issue, yes, this not only helps, it is probably the most important information you posted. :)

---

