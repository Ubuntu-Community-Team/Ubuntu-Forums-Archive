---
title: "Ubuntu hardware database"
date: 2018-10-26
forum: Hardware
---

### Post by andrey-ponomarenko on 2018-10-26
Hi,

The Linux-Hardware.org database has been divided recently into a set of databases, one per each Linux distro.

The Ubuntu database is available at: [https://linux-hardware.org/?d=Ubuntu](https://linux-hardware.org/?d=Ubuntu)

Everyone can contribute to the database by [https://github.com/linuxhw/hw-probe](https://github.com/linuxhw/hw-probe) (various packages are available: native Deb, AppImage, Docker, Snap, Flatpak, etc.). The tool is intended to simplify collecting of logs necessary for investigating hardware related problems. You need to execute only one simple command to collect all system logs at once:

```
sudo hw-probe -all -upload
```

Hardware failures are highlighted in the collected logs (smartctl, dmesg, xorg.log). Also it's handy to search for particular hardware configurations in the community and review logs for errors to check operability of devices on board (for some devices this is done automatically by hw-probe — see statuses of devices in a probe).

Enjoy!

---

