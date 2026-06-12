---
title: "ubuntu 16 - nvme pcie ssd - samsung sm961 - display smart data"
date: 2017-11-30
forum: Hardware
---

### Post by AnotherBrian on 2017-11-30
I want to check the age and wear leveling count on an sm961 samsung nmve pcie ssd.  

smartctl always reports /dev/nvme0n1: unable to detect device type. 

Suggestions? Thx

---

### Post by tmancill on 2018-03-04
You can install the nvme-cli package to see some information about your NVMe device similar to smartctl:

```
sudo apt-get install nvme-cli
sudo nvme list
sudo nvme smart-log /dev/nvme0
```

Review the nmve manpage for other commands, and be aware that there are admin commands that are destructive.

---

