---
title: "apple keyboard stopped working after update; works in UEFI"
date: 2021-01-12
forum: Hardware
---

### Post by ds6477 on 2021-01-12
Today I updated and rebooted my 2020.04 LTS Ubuntu server, and when it came back up, the usb wired Apple keyboard that is normally connected to it won't work. There were over 200 packages updated, so it wouldn't surprise me if one of those updates is the culprit.

I have found that the keyboard does still work in the UEFI screen. I can successfully enter the UEFI screen with the required keypresses upon initial boot-up and navigate the UEFI settings. I have also found that another keyboard works in the server, and that the Apple keyboard works on other computers I have access to. So, the keyboard itself still seems like it is ok. The Apple keyboard does have usb ports that can still power other devices such as mice (and even another keyboard).

I was able to find posts about keyboards suddenly stopping working, but most of those seem to be around "slow press" settings and the like. Since another keyboard works, I don't feel that is the underlying issue (nor do the solutions seem to make a difference). Could this be a driver problem? I wouldn't have thought that an Apple keyboard would take a special driver, but then again, it is Apple hardware. Is there something else I can look at as to why the keyboard isn't working?

Thanks!

---

### Post by ds6477 on 2021-01-16
Looks like the issue is with the running kernel. Before the update, the machine was running kernel version 5.4.0-62-generic. After the update, the running kernel is 5.8.0-36-generic. When I boot the machine with the 5.4 kernel, the keyboard works. Incidentally, the onboard audio controller no longer has a driver in the 5.8 kernel (according to `inxi -SMA` output), and thus audio doesn't work either. Audio does work in the 5.4 kernel. I just didn't find that out until I had done more troubleshooting after my original post.

---

### Post by ds6477 on 2021-01-16
Where would be the best place to get help with hardware driver support in the kernel?

---

### Post by ds6477 on 2021-01-22
Turns out the missing drivers were in the linux-modules-extra package, which wasn't installed during the update. I'm not sure why it wasn't pulled in at the same time the main linux-modules package was installed; maybe just unlucky timing. The linux-modules-extra package was installed under the old kernel.

---

