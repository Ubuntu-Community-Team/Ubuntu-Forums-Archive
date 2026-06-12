---
title: "LG R510 HDD cache and sleep when battery empties."
date: 2013-07-08
forum: Hardware
---

### Post by Cubytus on 2013-07-08
Hello all, 

I have set up an old LG R510 laptop with Ubuntu Server, and would like it to automatically go to sleep or hibernate when battery is empty, and gracefully wake up. I know it may not be typical to use a laptop as a server, but I did like the idea of having dual network interface and an internal battery, much more compact than a traditional tower + UPS, and still less restricting than a Raspberry or similar compact computer.

It is a tri-boot, Windows XP, Ubuntu Desktop, Ubuntu Server. As usual, no problem whatsoever in Windows. In Ubuntu Desktop, it can go to sleep, but fails to recover. In Ubuntu Server, the screen is filled with regular messages:
```
sd 6:0:0:0 [sdb] Asking for cache data failed
sd 6:0:0:0 [sdb] Assuming drive cache: write through
```

From what I could read from a well known search engine, it relates to flash-based drives that don't report anything when asked if they have a cache. I suspect this may be the reason (or a reason) why it fails to recover from sleep. I would like to keep the use of the SD card reader in case, say, I want to dump what my WRT54GL stores on it if it dies.

Is there a way to keep usage of the card reader and recover normal sleeping behaviour?

Besides, I would like the server to go on sleep when it detects a low level on the internal battery.

How can such a behaviour be set as standard?

---

