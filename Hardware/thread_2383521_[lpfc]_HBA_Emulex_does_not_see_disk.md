---
title: "[lpfc] HBA Emulex does not see disk"
date: 2018-01-26
forum: Hardware
---

### Post by komspr on 2018-01-26
Hi.

I have problem with HBS Emulex Fibre channel adapter. It doesn't see disk.

                ```
description: Fibre Channel
product: Saturn-X: LightPulse Fibre Channel Host Adapter
vendor: Emulex Corporation
```

```
[    4.015493] lpfc 0000:04:00.0: 0:1303 Link Up Event x1 received Data: x1 x1 x10 x2 x0 x0 0
[    4.015570] lpfc 0000:04:00.0: 0:1309 Link Up Event npiv not supported in loop topology
[    4.016671] lpfc 0000:04:00.0: 0:([IMG]https://forum.proxmox.com/styles/default/xenforo/clear.png[/IMG]0):2858 FLOGI failure Status:x3/x18 TMO:x0 Data x1000 x0
[    4.017627] lpfc 0000:04:00.0: 0[IMG]https://forum.proxmox.com/styles/default/xenforo/clear.png[/IMG]:(0):2858 FLOGI failure Status:x3/x18 TMO:x0 Data x1000 x0
[    4.018561] lpfc 0000:04:00.0: 0[IMG]https://forum.proxmox.com/styles/default/xenforo/clear.png[/IMG]:(0):2858 FLOGI failure Status:x3/x18 TMO:x0 Data x1000 x0
[    4.018636] lpfc 0000:04:00.0: 0[IMG]https://forum.proxmox.com/styles/default/xenforo/clear.png[/IMG]:(0):0100 FLOGI failure Status:x3/x18 TMO:x0
[    4.019713] lpfc 0000:04:00.0: 0[IMG]https://forum.proxmox.com/styles/default/xenforo/clear.png[/IMG]:(0):0266 Issue NameServer Req x117 err 1 Data: x80000 x0
```

I have made a little investigation.

Ubuntu 16.04.3 LTS, kernel 4.10.0-28, lpfc 11.2.0.2 - no issue.
Ubuntu 17.10.1, kernel 4.13.0-21, lpfc 11.4.0.1 - issue.
Debian 9.3, kernel 4.9.0-4, lpfc 11.2.0.0 - no issue.
Fedora 27, kernel 4.13.9-300, lpfc 11.4.0.1 - issue.
Proxmox 5.0, kernel 4.10.15-1, lpfc 11.2.0.2 - no issue.
Proxmox 5.1, kernel 4.13.13-5, lpfc 11.4.0.1 - issue.

So I think it's either kernel 4.13, or lpfc 11.4 problem...

Thanks.

(Related link: [https://forum.proxmox.com/threads/proxmox-5-1-lpfc-hba-emulex-lpe12000-error.39179/](https://forum.proxmox.com/threads/proxmox-5-1-lpfc-hba-emulex-lpe12000-error.39179/))

---

