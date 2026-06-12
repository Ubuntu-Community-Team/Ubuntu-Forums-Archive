---
title: "Kubuntu 13.04 Geforce GT 650M driver question"
date: 2013-07-07
forum: Hardware
---

### Post by zer010 on 2013-07-07
First, a little background info.  I had gotten this laptop without realizing it had the infamous Optimus tech.  I installed Lubuntu 12.10 and when I tried to find "Additional Drivers", there were none.  This is when I realized what I had.  So I looked around and found the bumblebee project.  I installed it and it seemed to work ok.  
   
Now, I just installed Kubuntu 13.04 and to my surprise, the "Additional Drivers" application is populated with NVIDIA drivers.  Does this mean that I won't have to use bumblebee or am I just getting my hopes up?  

Also, if I were to use one of the listed drivers, which one would I use?  There's not much info given that differentiates them, except for the readme locations (that don't exist).  

If anyone could give me a tip or pointer, I'd be very appreciative.

The readme location text is as follows and is relative to the driver list in the screenshot:

```
See /usr/share/doc/nvidia-310-updates/README.txt.gz for a complete listof supported GPUs and PCIIDs

See /usr/share/doc/nvidia-313-updates/README.txt.gz for a complete listof supported GPUs and PCIIDs

See /usr/share/doc/nvidia-304/README.txt.gz for a complete listof supported GPUs and PCIIDs

See /usr/share/doc/nvidia-310/README.txt.gz for a complete listof supported GPUs and PCIIDs

See /usr/share/doc/nvidia-304-updates/README.txt.gz for a complete listof supported GPUs and PCIIDs
```

---

### Post by 2F4U on 2013-07-07
From what I read here

[http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html](http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html)

the newest nVidia drivers support Optimus, but if you want GPU switching, you need bumblebee.

---

### Post by zer010 on 2013-07-07
So essentially, the newest proprietary drivers support the chip, but only the nvidia chip will be in use, thus quickly sapping battery power.  Unless something has changed, there's no automatic GPU switching in bumblebee, it must be specified upon application launch with "optirun".  

Do I understand this correctly?

---

### Post by Yellow Pasque on 2013-07-07
> Do I understand this correctly?
Yes

---

### Post by zer010 on 2013-07-07
> **Temüjin said:**
> Yes

Thanks.  

Perhaps in another year or so, the proprietary drivers will catch up to what it should be...

---

