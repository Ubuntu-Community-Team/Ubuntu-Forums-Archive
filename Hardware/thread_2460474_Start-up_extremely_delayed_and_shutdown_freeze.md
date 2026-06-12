---
title: "Start-up extremely delayed and shutdown freeze"
date: 2021-04-11
forum: Hardware
---

### Post by voodoo81people on 2021-04-11
Hi,
I have a Lenovo IdeaCentre 510A-15ARR and I installed Ubuntu 20.04.2 LTS on a Samsung SSD, keeping some other data in the other hard disk. Previously there was a Windows 10 installation that gave me a lot of BSOD (probably due to an unidentified update).
Since I experienced some crashes (Google Chrome tabs, WebStorm), I switched from gnome shell to KDE installing the required and latest packages and now everything seems to be stable.
However, some issues still persist:
[LIST]
[*]the system can boot only with kernel 5.8.0-43-generic after some minutes, the 5.8.0-48-generic leaves me with a black screen.
[*]the shutdown freezes at a certain point, same thing for the reboot.
[/LIST]

I should have the latest BIOS version, with secure boot disabled, and CSM enabled. 
Here is the journalctl lines regarding the shutdown: [https://paste.ubuntu.com/p/4bCCcBvPFc/](https://paste.ubuntu.com/p/4bCCcBvPFc/) and the logs for the start up: [https://paste.ubuntu.com/p/g74xPMWPvr/](https://paste.ubuntu.com/p/g74xPMWPvr/).
Thanks for any advice!

---

### Post by voodoo81people on 2021-04-11
For me the solution is the following:
[LIST=1]
[*]install the [Radeon™ Software for Linux® 20.50]("https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-50"): you'll find an archive for Ubuntu 20.04
[*][Copy some missing firmwares as explained here]("https://askubuntu.com/questions/1124253/missing-firmware-for-amdgpu") to avoid some APT warnings (optional)
[/LIST]

This solves both the delayed startup and the shutdown freeze. If you still have issues, consider using al older kernel version. ):P

---

