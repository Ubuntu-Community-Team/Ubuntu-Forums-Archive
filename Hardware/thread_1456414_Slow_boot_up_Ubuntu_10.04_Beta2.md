---
title: "Slow boot up Ubuntu 10.04 Beta2"
date: 2010-04-17
forum: Hardware
---

### Post by web1star on 2010-04-17
[SIZE=4]Hi everyone,[SIZE=2]
Since I've upgraded from Ubuntu 9.10 Desktop to Ubuntu 10.04 Beta2 my boot up time has increased dramatically. I have read numerous posts regarding this issue and found only one solution to this problem: 

Reboot and go to BIOS / F2 or Del/
Change SATA mode from **ANCI** to [B][I]compatibility mode
[/I][/B][/SIZE][/SIZE][I][SIZE=2]I hope this will work just as fine as it did for me
*Regards*[/SIZE]
[/I]

---

### Post by MetroPietro on 2010-04-30
Thanks, your fix worked. Just installed 10.04 Lucid LTS release on Toshiba Netbook NB 205. The first time it would not boot further than the GRUB menu; it dropped my to a shell and started initramfs.
After resetting SATA from ANCI to Compatibility mode in the BIOS, the first time I rebooted it did a hard drive check (which took 20 minutes), but now it reboots from cold start to login pane in 35 seconds. Thanks.

---

### Post by carlomejia on 2010-05-02
Thank you very much, I was freaking out with the lucid, my nb205 now boots.
Im in Colombia southamerica, and a linux fan since the eeepc xandros.

---

### Post by albafar on 2010-05-02
I have the same issue on my Thinkpad T41. Just cannot figure out how to change the SATA mode. Even when entering BIOS I cannot see where to do the changes. Any suggestions?

---

### Post by scc4fun on 2010-05-04
I believe the ThinkPad T41 uses IDE (PATA) drives--not SATA drives. Not sure what would help further but plan on testing soon.

---

