---
title: "can not write power saving file - link_power_management_policy"
date: 2008-09-09
forum: Hardware
---

### Post by jhp-dk on 2008-09-09
I cannot get permission to write link_power_management_policy file to /sys/class/scsi_host/host0  dir. why?

```

jimmy@laptop:/sys/class/scsi_host/host0$ sudo cp ./unique_id ./link_power_management_policy
cp: cannot create regular file `./link_power_management_policy': No such file or directory

```I need to create the file in order to lower my power consuming
[http://ubuntuforums.org/showthread.php?t=729644&highlight=dell+power+save](http://ubuntuforums.org/showthread.php?t=729644&highlight=dell+power+save)

---

