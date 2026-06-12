---
title: "Ubuntu 20.04 NVMe not suspending"
date: 2021-07-24
forum: Hardware
---

### Post by aoxa on 2021-07-24
Hi!, up until yesterday I had ubuntu 20 installed in a sata ssd and suspend was working fine. 
I installed a new nvme ssd and a fresh ubuntu install and when I try to suspend, it works, for a second. It shuts all off, fans and led lights and then brings the whole system back up. I was checking on the logs and see no error, in fact it is as if it successfully suspended and was unsuspended intentionally. 
following you can see part of the log. Any input will be greatly appreciated.
Thanks!
Aoxa.

eidt: I am on kernel 5.11.1-051101-generic Had to upgrade because the temp was not being registered by the sensors in the kernel that came with the installation

```
Jul 24 13:12:39 piero-pc kernel: [  181.577422] rfkill: input handler disabledJul 24 13:12:40 piero-pc kernel: [  182.384565] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 24 13:12:40 piero-pc kernel: [  182.578171] ata2.00: configured for UDMA/133
Jul 24 13:12:40 piero-pc systemd-sleep[3469]: /dev/sda:
Jul 24 13:12:40 piero-pc systemd-sleep[3469]:  setting Advanced Power Management level to 0xfe (254)
Jul 24 13:12:40 piero-pc systemd-sleep[3469]:  APM_level#011= 254
Jul 24 13:12:40 piero-pc systemd-sleep[3511]: /dev/sdb:
Jul 24 13:12:40 piero-pc systemd-sleep[3511]:  setting Advanced Power Management level to 0xfe (254)
Jul 24 13:12:40 piero-pc systemd-sleep[3511]:  APM_level#011= 254
Jul 24 13:12:40 piero-pc systemd[1]: systemd-suspend.service: Succeeded.
Jul 24 13:12:40 piero-pc systemd[1]: Finished Suspend.
Jul 24 13:12:40 piero-pc systemd[1]: Stopped target Sleep.
Jul 24 13:12:40 piero-pc systemd[1]: Reached target Suspend.
Jul 24 13:12:40 piero-pc NetworkManager[966]: <info>  [1627143160.4294] manager: sleep: wake requested (sleeping: yes  enabled: yes)
Jul 24 13:12:40 piero-pc NetworkManager[966]: <info>  [1627143160.4295] device (enp5s0): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'managed')
Jul 24 13:12:40 piero-pc systemd[1]: Starting NVIDIA system resume actions...
Jul 24 13:12:40 piero-pc systemd[1]: Stopped target Suspend.
Jul 24 13:12:40 piero-pc suspend: nvidia-resume.service
Jul 24 13:12:40 piero-pc logger[3579]: <13>Jul 24 13:12:40 suspend: nvidia-resume.service
Jul 24 13:12:40 piero-pc systemd[1]: nvidia-resume.service: Succeeded.
Jul 24 13:12:40 piero-pc systemd[1]: Finished NVIDIA system resume actions.
Jul 24 13:12:40 piero-pc kernel: [  182.680324] Generic FE-GE Realtek PHY r8169-500:00: attached PHY driver [Generic FE-GE Realtek PHY] (mii_bus:phy_addr=r8169-500:00, irq=IGNORE)
Jul 24 13:12:40 piero-pc kernel: [  182.876710] r8169 0000:05:00.0 enp5s0: Link is Down
```

---

