---
title: "hdparm doesn't load hdparm.conf"
date: 2008-05-19
forum: Hardware
---

### Post by KOTAPAKA on 2008-05-19
Hi
I have hdparm installed. I opened /etc/hdparm.conf and uncommented some options to activate the functions as the files says. For instance I have uncommented the -B apm management option but it obviously doesn't take effect even after reboot so I have to do hdparm -B 255 /dev/sda manually. How can I make hdparm load the settings from /etc/hdparm.conf. When I installed hdparm I assumed it is automatically started by the system so I haven't made any configurations to to it apart from the hdparm.conf file.

---

### Post by suriro on 2008-05-19
uncommenting options is not enough, you also have to define block device.

---

