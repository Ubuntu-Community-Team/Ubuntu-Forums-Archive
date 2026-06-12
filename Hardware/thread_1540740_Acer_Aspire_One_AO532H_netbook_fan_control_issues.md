---
title: "Acer Aspire One AO532H netbook fan control issues"
date: 2010-07-28
forum: Hardware
---

### Post by fzhou on 2010-07-28
Hello, all
 It seems that my netbook's fan just does not stop. According to some forum posts, I could use acerhdf module to fix this problem. However, when I did ```
sudo modprobe acerhdf
```, I got the following error (from dmesg):
```

[  121.266045] acerhdf: Acer Aspire One Fan driver, v.0.5.20
[  121.266066] acerhdf: unknown (unsupported) BIOS version Acer            /AO532h          /V1.21, please report, aborting!

``` 
My kernel version is: ```
2.6.32-24-generic #38-Ubuntu SMP
```. My ```
/etc/modprobe.d/acerhdf.conf
``` is:
```

options acerhdf interval=5 fanon=65000 fanoff=55000 kernelmode=1

```
though I don't think this file is the cause of the problem. Thanks.

---

### Post by anglican on 2010-07-28
> **fzhou said:**
> Hello, all
 It seems that my netbook's fan just does not stop. According to some forum posts, I could use acerhdf module to fix this problem. However, when I did ```
sudo modprobe acerhdf
```, I got the following error (from dmesg):
```

[  121.266045] acerhdf: Acer Aspire One Fan driver, v.0.5.20
[  121.266066] acerhdf: unknown (unsupported) BIOS version Acer            /AO532h          /V1.21, please report, aborting!

```My kernel version is: ```
2.6.32-24-generic #38-Ubuntu SMP
```. My ```
/etc/modprobe.d/acerhdf.conf
``` is:
```

options acerhdf interval=5 fanon=65000 fanoff=55000 kernelmode=1

```though I don't think this file is the cause of the problem. Thanks.
The 532h is not currently supported for acerhdf, so when the module finds that BIOS version it quits. You can, **very much at your own risk**, force it to run anyway by adding "force_bios=v1.3303" (without the quotes) to your /etc/modprobe.d/acerhdf.conf file. There isn't (as there is for some models) a bios update that is OK with acerhdf, the 532h model just isn't on the list for acerhdf. This doesn't mean that it won't work necessarily but, as I've already said you over-ride the bios check **at your own risk**. I've noticed that they do add new BIOS versions to the acerhdf module from time to time so I wouldn't be surprised if some future kernel update fixes this for the 532h.

H

---

