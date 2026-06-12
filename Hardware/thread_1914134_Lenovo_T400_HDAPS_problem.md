---
title: "Lenovo T400 HDAPS problem"
date: 2012-01-23
forum: Hardware
---

### Post by S. Vaden Blue on 2012-01-23
Help! I recently received a Lenovo Thinkpad T400 for Christmas with a clean harddrive(my wife is the bomb) so I immediately installed Ubuntu 11.10 64 bit. Works great except for the Hard Drive Active Protection System isn't working. I installed the proper packages, tp-smapi-dkms and hdapsd and still no luck. 

When I try to start hdapsd via terminal I get the following readout: Mon Jan 23 17:13:08 2012: Starting hdapsd
Mon Jan 23 17:13:08 2012: WARNING: You did not supply any devices to protect, trying autodetection.
Mon Jan 23 17:13:08 2012: Adding autodetected device: sda
Mon Jan 23 17:13:08 2012: Could not find a suitable interface
 
Then when I run sudo modinfo hdaps I get the following: Mon Jan 23 17:13:08 2012: Starting hdapsd
Mon Jan 23 17:13:08 2012: WARNING: You did not supply any devices to protect, trying autodetection.
Mon Jan 23 17:13:08 2012: Adding autodetected device: sda
Mon Jan 23 17:13:08 2012: Could not find a suitable interface

Then I ran sudo modprobe hdaps as instructed via an extensive google search and I get the following: FATAL: Error inserting hdaps (/lib/modules/3.0.0-15-generic/updates/dkms/hdaps.ko): No such device or address

Hmm! And then when I finally run dmesg |grep hdaps I get this crazy readout: [38740.914161] hdaps: inverting axis (3) readings
[38740.914164] hdaps: LENOVO ThinkPad T400 detected
[38740.914166] hdaps: driver init failed (ret=-6)!

Help please. As the hdaps is all that lies between me and a mint condition Lenovo Thinkpad T400. 

Thanks in advance for any help you can offer an ubuntu newbie.

Sincerely,
S. Vaden Blue

---

### Post by searchfgold6789 on 2012-01-24
A helpful thread: [https://bbs.archlinux.org/viewtopic.php?id=82598](https://bbs.archlinux.org/viewtopic.php?id=82598)
One person ran the following script: ```

#!/bin/sh  
path="/lib/modules/$(uname -r)/" 
rm $path/kernel/drivers/hwmon/hdaps.ko 
cp $path/extra/hdaps.ko $path/kernel/drivers/hwmon/ 
/etc/rc.d/hdapsd restart
```Another simply upgraded his BIOS.

---

