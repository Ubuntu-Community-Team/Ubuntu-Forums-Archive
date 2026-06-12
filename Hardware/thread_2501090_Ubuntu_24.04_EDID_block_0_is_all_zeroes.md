---
title: "Ubuntu 24.04: EDID block 0 is all zeroes"
date: 2024-09-22
forum: Hardware
---

### Post by avoigt3 on 2024-09-22
Hi all,

since the upgrade from 22.04 to 24.04, the syslog of my headless server is flooded with the following kernel message:

EDID block 0 is all zeroes

```
Sep 22 19:41:23 s01 kernel: EDID block 0 is all zeroes
Sep 22 19:41:46 s01 kernel: message repeated 7 times: [ EDID block 0 is all zeroes]
Sep 22 19:42:09 s01 kernel: EDID block 0 is all zeroes
Sep 22 19:42:09 s01 kernel: message repeated 3 times: [ EDID block 0 is all zeroes]
Sep 22 19:42:32 s01 kernel: EDID block 0 is all zeroes
Sep 22 19:42:55 s01 kernel: message repeated 7 times: [ EDID block 0 is all zeroes]
Sep 22 19:43:18 s01 kernel: EDID block 0 is all zeroes
Sep 22 19:43:41 s01 kernel: message repeated 7 times: [ EDID block 0 is all zeroes]
Sep 22 19:44:04 s01 kernel: EDID block 0 is all zeroes
Sep 22 19:44:04 s01 kernel: message repeated 3 times: [ EDID block 0 is all zeroes]
Sep 22 19:44:27 s01 kernel: EDID block 0 is all zeroes
Sep 22 19:44:50 s01 kernel: message repeated 7 times: [ EDID block 0 is all zeroes]
Sep 22 19:45:13 s01 kernel: EDID block 0 is all zeroes

```

 It seems to be a kernel bug related to the module i915, which is active in my system:

[https://forums.debian.net/viewtopic.php?t=154804](https://forums.debian.net/viewtopic.php?t=154804)

Does anybody know how to stop this message without unloading the module as described in the Debian forum?

Kind regards

---

### Post by 1fallen on 2024-09-22
> **avoigt3 said:**
> 
Does anybody know how to stop this message without unloading the module as described in the Debian forum?

Kind regards

Will you show your current values:
```
[FONT=monospace][COLOR=#000000]cat /proc/sys/kernel/printk[/COLOR]

```



[/FONT]

---

### Post by avoigt3 on 2024-09-22
[FONT=monospace]```

root@s01:/home/xxxxx# cat /proc/sys/kernel/printk
4    4    1    7

```
[/FONT]

---

### Post by 1fallen on 2024-09-22
here is why you see low level spam:
Index:
```
                     CUR  DEF  MIN  BTDEF
0 - emergency        x              x                        
1 - alert            x         x    x
2 - critical         x              x
3 - error            x              x
4 - warning          x    x         x
5 - notice           x              x
6 - informational    V              V
7 - debug           

```
This is too noisy, I just want critical and up (no errors). Unlabeled messages should be regarded as warning,
I'll use this for mine:
```
[FONT=monospace][COLOR=#000000]sudo sysctl -w kernel.printk="3 4 1 3"[/COLOR]
[/FONT]
```
Proof
```
[FONT=monospace][COLOR=#000000] cat /proc/sys/kernel/printk [/COLOR]
1       4       1       3
[/FONT]
```
Or
```
[FONT=monospace][COLOR=#000000]sysctl kernel.printk [/COLOR]
kernel.printk = 1       4       1       3
[/FONT]
```
Maybe give that a go.

---

### Post by avoigt3 on 2024-09-23
I have uncommented the relevant setting in /etc/sysctl.conf and rebooted the server. 

```
# Uncomment the following to stop low-level messages on console
kernel.printk = 3 4 1 3
```

Unfortunately, this has not changed anything, the messages are still coming up again and again. :(

---

### Post by 1fallen on 2024-09-23
> **avoigt3 said:**
> I have uncommented the relevant setting in /etc/sysctl.conf and rebooted the server. 

```
# Uncomment the following to stop low-level messages on console
kernel.printk = 3 4 1 3
```

Unfortunately, this has not changed anything, the messages are still coming up again and again. :(

I'll take this as you had a monitor connected at install time right?

Outside of blocking it at the kernel level will prove to be difficult at best.

I see bugs related to this with kernel 6.11, but have no idea what kernel your currently using.

---

### Post by avoigt3 on 2024-09-23
I'm using the default ubuntu kernel:

```

Linux s01 6.8.0-45-generic #45-Ubuntu SMP PREEMPT_DYNAMIC Fri Aug 30 12:02:04 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux

```

Now, I have also blacklisted the i915 module because I have not found a way to block these messages completely. I had 100000 messages in a few hours telling me that my monitor was not connected. Very useful. After blocking the module, the messages are gone. With kernel 5.x under Ubuntu 22.04, the same module had no issues with identical hardware. The server is running headless in multiuser target, so I do not need any graphical output.XRDP is running fine without the module.

---

### Post by 1fallen on 2024-09-23
Thanks for the update.

---

### Post by Yellow Pasque on 2024-09-24
[https://forums.truenas.com/t/intel-igpu-causes-log-spam/10181/6](https://forums.truenas.com/t/intel-igpu-causes-log-spam/10181/6)

---

### Post by 1fallen on 2024-09-25
> **Yellow Pasque said:**
> [https://forums.truenas.com/t/intel-igpu-causes-log-spam/10181/6](https://forums.truenas.com/t/intel-igpu-causes-log-spam/10181/6)

That probably is the best route to take, "i915.disable_display=1" kernel line

---

### Post by avoigt3 on 2024-09-26
An update of the Linux firmware package for Ubuntu 24.04 was released yesterday 

```

https://launchpad.net/ubuntu/+source/linux-firmware/20240318.git3b128b60-0ubuntu2.4

...
* Missing DMC firmware for Xe driver for Intel BattleMage (LP: #2080214) 
    - i915: Add BMG DMC v2.06
...


```

I installed it today and reactivated the Modul i915. After a restart, the module is loaded and the kernel messages have disappeared completely. I think that the bug was unconsciously fixed as well with this update.

---

### Post by Yellow Pasque on 2024-09-26
Intel "BattleMage" GPU's haven't been released yet. I doubt that fixed your issue.

---

### Post by avoigt3 on 2024-09-26
> **Yellow Pasque said:**
> Intel "BattleMage" GPU's haven't been released yet. I doubt that fixed your issue.

I have not said, that I have this GPU. I said, that the issue is gone with the release of the linux firmare package, which was released yesterday.

---

### Post by Yellow Pasque on 2024-09-26
> **avoigt3 said:**
> I have not said, that I have this GPU.

But you quoted that specific changelog entry about i915, like it was relevant to your situation..

> I said, that the issue is gone with the release of the linux firmware package

And I'm telling you it was probably a coincidence. I'm glad it's solved, though. Please mark this thread solved (thread tools menu above first post).

---

