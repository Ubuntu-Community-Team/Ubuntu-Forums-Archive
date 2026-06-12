---
title: "Wifi Card Issue"
date: 2009-11-17
forum: Hardware
---

### Post by lvalen18 on 2009-11-17
I have a 3DSP PCI WiFi Card. It installs Just find on Ubuntu 9.04.. But I did come across an issue that when 9.04 is updated the Kernel Version is not supported and to fix this issue I go into the .sh install file and add the new kernel version and rename one of the Driver Kernel Folder to the new one and It installs just find... But with 9.10 I do the Same all the Programs Install but the PCI Card is not detected.. Do the Drivers go into a Different Folder on 9.10 then they do on 9.04?

[B]I was thinking Can I just Copy ALL the Files the Install Copies into the Harddrive in the Same directories in 9.04 to 9.10... 

Example Let Say I run the Install It copies a file into the /lib/ directory in 9.04... Then I grab the File from 9.04 and Copy it to the /lib/ directory in 9.10 would that Fix My Issue?[/B]

---

### Post by madengineer on 2009-11-17
Probably not...there are almost certainly changes being made to other files to point to the driver involved.

---

