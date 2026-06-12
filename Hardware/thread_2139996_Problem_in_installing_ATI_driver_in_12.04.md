---
title: "Problem in installing ATI driver in 12.04"
date: 2013-04-28
forum: Hardware
---

### Post by shaaraddalvi on 2013-04-28
I have HP pavilion g6 laptop and I want to install ATI/AMD proprietary FGLRX graphics driver. I tried installing both the driver and the post release updates but both gave some error while the download was in progress at round 47% as :
> 
........<many download progress messages here...>
2013-04-28 20:03:01,346 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 95.5205512013-04-28 20:03:01,347 ERROR: Package fetching failed: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-i386_2.15-0ubuntu10.3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-i386_2.15-0ubuntu10.3_amd64.deb) 404  Not Found [IP: 91.189.91.15 80]


2013-04-28 20:03:01,573 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates


2013-04-28 20:03:01,574 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2013-04-28 20:03:01,574 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2013-04-28 20:03:01,584 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2013-04-28 20:03:01,689 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2013-04-28 20:03:01,689 DEBUG: fglrx_updates is not the alternative in use


Can anyone give me a solution please?

---

### Post by SeijiSensei on 2013-04-28
Usually the best method is to run the "Additional Drivers" application found in the menus.  What method are you using?

---

### Post by shaaraddalvi on 2013-04-28
Thanks a lot! :)
same...the driver is first in the list of drivers there....btw, I followed steps from 
[http://ubuntuforums.org/archive/index.php/t-1866589.html](http://ubuntuforums.org/archive/index.php/t-1866589.html)
and got the drivers installed, but all the effects like wobbly windows are disabled. they are not working after reenabling them. any idea?

---

### Post by SeijiSensei on 2013-04-28
You'll have to ask others about desktop effects.  I avoid them.

---

### Post by Yellow Pasque on 2013-04-28
What graphic card do you have?
```
sudo update-pciids
lspci | grep VGA
```

---

### Post by shaaraddalvi on 2013-04-28
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series]

---

