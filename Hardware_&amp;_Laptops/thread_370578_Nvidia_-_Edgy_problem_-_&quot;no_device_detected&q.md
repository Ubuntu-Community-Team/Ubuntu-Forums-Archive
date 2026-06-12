---
title: "Nvidia - Edgy problem - &quot;no device detected&quot;???"
date: 2007-02-25
forum: Hardware &amp; Laptops
---

### Post by tiger.woods on 2007-02-25
I had a working Nvidia installation on my Edgy box and somehow messed it up and can't get it going again... just getting the error "No devices Detected" when starting X.

Anyone have any ideas or suggestion on how to fix this?

Thanks,

---

### Post by dcstar on 2007-02-26
> **tiger.woods said:**
> I had a working Nvidia installation on my Edgy box and somehow messed it up and can't get it going again... just getting the error "No devices Detected" when starting X.

Anyone have any ideas or suggestion on how to fix this?

Thanks,

```
sudo dpkg-reconfigure xserver-xorg
```
then
```
sudo /etc/init.d/gdm restart
```

Try the nvidia driver, if it's still go good do it again and use the nv driver to get a basic system up and going.

---

### Post by tiger.woods on 2007-02-26
No, still no go getting the same error message.

When the system reboots I get the Ubuntu logo screen, it flashes like its booting, then I get it again like it failed logging in the first time after which I get the CL?

TW,

---

### Post by tiger.woods on 2007-02-26
Anyone else have any suggestions?? I'm running Kubuntu and followed these directions ([https://help.ubuntu.com/community/MythTV_Edgy_hardware](https://help.ubuntu.com/community/MythTV_Edgy_hardware)) for install NVIDIA...

Restoring an older Xorg.conf file allowed me to start X,  looking through the Xorg.conf file I see in the Device section "Vesa" instead of NVIDIA... If I change it to NVIDIA and restart I get a CL for a login... so I'm guessing it hassomethingto do with the NVIDIA drivers or lack there of???

TW,

---

