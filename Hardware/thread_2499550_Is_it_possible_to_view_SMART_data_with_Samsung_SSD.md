---
title: "Is it possible to view SMART data with Samsung SSD 990 PRO?"
date: 2024-07-31
forum: Hardware
---

### Post by KenUBF on 2024-07-31
I am running the latest version of Ubuntu and have recently installed the Samsung SSD 990 PRO. When I went to the Disks app I noticed that the SMART Data & Self Tests were greyed out. Looking into it I installed the cli tool smartmontools and that provides some information that is helpful, but it looks like it doesn't support SMART Data reporting according to the smartctl output. My question is if there is a way to somehow activate it or access the SMART Data in some other way? The Samsung Magic tool for that purpose isn't supported in Linux. This is my first SSD so I am very new to all of this. Thanks for your help!

---

### Post by deadflowr on 2024-07-31
i think that's an nvme drive so install and use the nvme-cli package.
```
sudo apt install nvme-cli
```
See: [https://nvmexpress.org/open-source-nvme-management-utility-nvme-command-line-interface-nvme-cli/](https://nvmexpress.org/open-source-nvme-management-utility-nvme-command-line-interface-nvme-cli/)
for howto use the commands for it.

---

### Post by oldfred on 2024-07-31
Samsung has ISO with updates for firmware.
Each ISO is only for one model & one version of firmware.

Compare to vendors support site
sudo dmidecode -s bios-version
udisksctl status

or
sudo apt install nvme-cli
sudo nvme list

Look under firmware, not Magician.
Shows ISO by model & firmware versio.
[https://semiconductor.samsung.com/consumer-storage/support/tools/](https://semiconductor.samsung.com/consumer-storage/support/tools/)
And then download ISO & create bootable flash drive. (I booted with grub loopmount and was surprised it worked with loopmount as not all ISO work).

---

### Post by KenUBF on 2024-08-01
Thank you all for your advice! I'm now able to see my drive status and health.

---

