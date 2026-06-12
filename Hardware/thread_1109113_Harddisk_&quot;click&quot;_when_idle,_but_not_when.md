---
title: "Harddisk &quot;click&quot; when idle, but not when busy"
date: 2009-03-28
forum: Hardware
---

### Post by afeasfaerw23231233 on 2009-03-28
I heard so many clicks sound from the harddisk when running Ubuntu. I searched around the forum and many people said this problem solved by enabling "laptop mode". But I don't feel any difference. 
Interestingly I find out that when the harddisk is busy, there's no click sound. When the disk is idle, the harddisk clicks every ten seconds or so.
It is absolutely true for my notebook. I have verified it by the 
```

sudo smartctl -a /dev/sda | grep 193

``` command. 
The more busy the harddisk is, the fewer clicks it produces. 
I installed an auto-reload plugin for firefox. If I set reloading pages every 1 second, the load cycle count doesn't increase for 1 hour. 

It is good for the harddisk but not for the battery

Any idea?

EDIT: I notice there is no click sound when the notebook is on AC. 
EDIT2: The APM level of harddisk is 254 in AC but 128 on battery. If I set it as 254 when it is on battery it produces no click sound too, but the discharge rate increase by ~5W ! In windows XP I hear no click sound no matter it is on AC or battery. UBUNTU is either killing the harddisk or the battery!

---

