---
title: "[SOLVED] Aironet PCMCIA card not detected"
date: 2008-05-21
forum: Hardware
---

### Post by bucky0 on 2008-05-21
Hey all, 

I already had 8.04 installed (upgraded via internet from 7.10) but I wanted to get a fresh install so I installed from the DVD.

My aironet pcmcia wifi card isn't being detected anymore, when I plug it in, some entries come up, but ifconfig doesn't show the interface and the power light on the card doesn't stay on.

What package would I report it under? udev? hald?

thanks for your help,
bucky

syslog:
amelo@amelo-laptop:~$ tail -f /var/log/syslog
May 21 14:52:55 amelo-laptop kernel: [11935.734213] pccard: PCMCIA card inserted into slot 0
May 21 14:52:55 amelo-laptop kernel: [11935.734230] cs: memory probe 0xf4000000-0xfbffffff: excluding 0xf4000000-0xf8ffffff 0xfa000000-0xfbffffff
May 21 14:52:55 amelo-laptop kernel: [11935.735158] pcmcia: registering new device pcmcia0.0
May 21 14:52:56 amelo-laptop kernel: [11936.680065] airo(): Probing for PCI adapters
May 21 14:52:56 amelo-laptop kernel: [11936.680889] airo(): Finished probing for PCI adapters
May 21 14:52:57 amelo-laptop kernel: [11937.733089] airo(): cmd:111 status:7f11 rsp0:2 rsp1:0 rsp2:0
May 21 14:52:57 amelo-laptop kernel: [11937.733106] airo(): Doing fast bap_reads

---

### Post by bucky0 on 2008-05-21
I just double checked my search tab and I mispelled airo. Dumb.

solution found here:

[http://ubuntuforums.org/showthread.php?t=795480&highlight=airo]("http://ubuntuforums.org/showthread.php?t=795480&highlight=airo")

---

