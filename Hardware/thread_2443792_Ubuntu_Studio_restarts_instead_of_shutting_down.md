---
title: "Ubuntu Studio restarts instead of shutting down"
date: 2020-05-20
forum: Hardware
---

### Post by linuxliker2 on 2020-05-20
Hello - 
I just installed Ubuntu Studio 20.04 on a HP ZBook15 on Sunday. The OS  seems to be working fine except when I go to shut down. The system shuts  down but within 10 seconds, (probably more like 5 seconds), it  re-starts. I've been using the power button to shut down but I'd rather  not do that. 
I read some answers on another forum which suggest using terminal commands to  shut the computer down and they all act the same way -- computer shuts  down for a few seconds, then powers up again. 
I'd appreciate suggestions to help me with this problem.

Thanks.

---

### Post by Vtwin on 2020-05-26
I had a similar problem but on Linux Mint. The solution was to use an older kernel. As you've just installed the OS you may only have the one kernel. You can type **dpkg --list | grep linux-image** into the terminal to see what kernels you have installed.

---

