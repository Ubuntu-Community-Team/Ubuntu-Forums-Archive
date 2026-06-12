---
title: "Ahci problem with Philips Freevents X60it"
date: 2008-05-08
forum: Hardware
---

### Post by xendros on 2008-05-08
Hi, sorry for my english :(

I have a problem with Ubuntu and my laptop
When I boot the system, the bar freeze for 4-5 seconds and during this time I hear a little noise from the SATA Disk, this is the operation of the system during the freeze:

```
May  5 18:46:15 ubuntu kernel: [   31.993509] ahci 0000:00:1f.2: nr_ports (4) and implemented port map (0x5) don't match, using nr_ports
May  5 18:46:15 ubuntu kernel: [   31.993512] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0xf
```

After that, the system start normally...
This is a problem that can be solved or is a normal process of the system? Thanks

---

### Post by kozimodo on 2008-06-27
I have precisely the same problem.  My laptop is a Fujitsu Lifebook S6240.  Attached is the dmesg output.

---

### Post by moore.bryan on 2008-07-14
i've started a thread with the same problem as you two [here]("http://ubuntuforums.org/showthread.php?t=856235") and NO ONE has responded. :-( it looks like we might be all alone in this world...

---

