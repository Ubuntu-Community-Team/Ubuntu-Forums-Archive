---
title: "Intrepid slow boot"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by samthurston on 2008-12-08
I've seen a few posts about slow boot but nothing like I'm experiencing.  I tried upgrading from 8.04 to 8.10 and had so many problems that I wound up giving up and starting over... I backed up /home/ and installed 64 bit desktop.

Both on upgrade, and fresh install, I experience this:

```

[    0.605572] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.606180] TCP: Hash tables configured (established 131072 bind 65536)
[    0.606182] TCP reno registered
[    0.616194] NET: Registered protocol family 1
[    0.616302] checking if image is initramfs... it is
[  508.433097] Clocksource tsc unstable (delta = 299971248228 ns)
[  508.596654] Freeing initrd memory: 8465k freed
[  508.601543] audit: initializing netlink socket (disabled)
[  508.601571] type=2000 audit(1228744789.600:1): initialized
[  508.606963] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[  508.609256] VFS: Disk quotas dquot_6.5.1

```

What the heck? I can't find any useful information on this clocksource error other than that it's "common" and "harmless."

 Here are some other useful dmesg greps:
```

sam@kestrel:~$ dmesg | grep error
[  510.945083] usb 5-2: device not accepting address 2, error -71
sam@kestrel:~$ dmesg | grep warning
[  523.743601] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
sam@kestrel:~$ dmesg | grep fail
[  512.887072] PM: Resume from disk failed.

```

---

