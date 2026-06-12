---
title: "one external HD extremely slow"
date: 2022-03-12
forum: Hardware
---

### Post by dieter-erich on 2022-03-12
Hi,
   I have a number of external hard disks formatted as xfs attached to my ubuntu mate box via USB3 connectors. All but one have reasonable read times e.g.:

```
sudo hdparm -Tt /dev/sdj

/dev/sdj:
 Timing cached reads:   20550 MB in  1.99 seconds = 10327.68 MB/sec
 Timing buffered disk reads: 608 MB in  3.00 seconds = 202.56 MB/sec
```

[B]However one is extremely slow:
[/B]
```
sudo hdparm -Tt /dev/sdk

/dev/sdk:
 Timing cached reads:     2 MB in 551.93 seconds =   3.71 kB/sec
 Timing buffered disk reads:   2 MB in 519.24 seconds =   3.94 kB/sec"
``` 


what might be the reason?
Thanks, D-E

---

### Post by DuckHook on 2022-03-13
[LIST=1]
[*]First and foremost, back up everything that's important. Your disk may be dying.
[*]The first diagnostic step I can think of would be to swap ports. This is a simple initial step that starts the process of elimination—in this case, a bad USB port.
[*]I'm not familiar with xfs, but does the disk behave this way if it is unplugged during boot and then plugged in post boot?
[*]Checking your logs is always advantageous when it comes to such issues. Something like this would likely show up near the start, during the boot process.
[*]If behaviour persists after hot mounting, then a variant of the above would be to plug in the disk post boot, note the time carefully, then check your logs for that specific time.
[*]If nothing stands out from the logs, try installing the HDD internally, then use the diagnostic features of hdparm and/or smartctl (you probably know that these tools have a limited feature set through USB).
[*]Then, let's see more info with:```
sudo smartctl -a /dev/sdk
``` If you haven't done so, you may first have to install smartmontools. Output may be lengthy so please post results between [noparse]```

```[/noparse] tags to preserve format and for easier readability.
[/LIST]
That's all I can think of so far, but it's a start.

---

### Post by TheFu on 2022-03-13
Another idea. Are all the external drives also externally powered?  USB-only power is often marginal and if they are sharing the same USB bus of the computer, 3 devices may not get sufficient power.

For external spinning disks, I always use external power supplies too. This avoids the extra slow performance that happens when USB power isn't sufficient.  For SSD and flash-based USB storage, this usually isn't an issue.

---

