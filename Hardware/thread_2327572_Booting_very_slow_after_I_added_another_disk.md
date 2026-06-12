---
title: "Booting very slow after I added another disk"
date: 2016-06-12
forum: Hardware
---

### Post by luski on 2016-06-12
After I added another SSD disk my Ubuntu boots very slow. Here are logs with the timeout error:
```

Jun 12 15:45:38 localhost systemd[1]: dev-disk-by\x2duuid-c326712c\x2d3c56\x2d4060\x2d8c3c\x2db7c4cfb27e5d.device: Job dev-disk-by\x2duuid-c326712c\x2d3c56\x2d4060\x2d8c3c\x2db7c4cfb27e5d.device/start timed out.
Jun 12 15:45:38 localhost systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-c326712c\x2d3c56\x2d4060\x2d8c3c\x2db7c4cfb27e5d.device.
Jun 12 15:45:38 localhost systemd[1]: Dependency failed for Cryptography Setup for cryptswap1.
Jun 12 15:45:38 localhost systemd[1]: Dependency failed for dev-mapper-cryptswap1.device.
Jun 12 15:45:38 localhost systemd[1]: Dependency failed for /dev/mapper/cryptswap1.
Jun 12 15:45:38 localhost systemd[1]: dev-mapper-cryptswap1.swap: Job dev-mapper-cryptswap1.swap/start failed with result 'dependency'.
Jun 12 15:45:38 localhost systemd[1]: Startup finished in 7.342s (kernel) + 3min 569ms (userspace) = 3min 23.283s.
Jun 12 15:45:38 localhost systemd[1]: dev-mapper-cryptswap1.device: Job dev-mapper-cryptswap1.device/start failed with result 'dependency'.
Jun 12 15:45:38 localhost systemd[1]: [EMAIL="systemd-cryptsetup@cryptswap1.servic"]systemd-cryptsetup@cryptswap1.servic[/EMAIL]e: Job [EMAIL="systemd-cryptsetup@cryptswap1.servic"]systemd-cryptsetup@cryptswap1.servic[/EMAIL]e/start failed with result 'dependency'.
Jun 12 15:45:38 localhost systemd[1]: dev-disk-by\x2duuid-c326712c\x2d3c56\x2d4060\x2d8c3c\x2db7c4cfb27e5d.device: Job dev-disk-by\x2duuid-c326712c\x2d3c56\x2d4060\x2d8c3c\x2db7c4cfb27e5d.device/start failed with result 'timeout'.

```

How can I solve it?

---

