---
title: "missing /sys/class/scsi_host/host0/link_power_management_policy"
date: 2008-05-15
forum: Hardware
---

### Post by tejunekim on 2008-05-15
hi! i've been trying to tweak my laptop's battery life by automating powertop's suggestions. in the process of doing this, i discovered that
```
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
``` 
would confuse my laptop when its coming back from suspension. i tried to get around this by editing /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux so that the policy is reverted to max_performance right before going to suspension and then go back to whatever state it was.

the trouble is, i did something wrong in that script and i can no longer find /sys/class/scsi_host/host0/link_power_management_policy... :(

```
$ cat /sys/class/scsi_host/host0/link_power_management_policy 
cat: /sys/class/scsi_host/host0/link_power_management_policy: No such file or directory
```

is there a way to get the "file" back?

thanks in advance

---

### Post by tejunekim on 2008-05-18
nevermind... it came back! (i thought it didn't come back after the first reboot...)

---

