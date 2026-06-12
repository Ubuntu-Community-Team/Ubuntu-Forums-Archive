---
title: "long kernel boot time xubuntu 16.04"
date: 2017-07-04
forum: Hardware
---

### Post by robert129 on 2017-07-04
My system is backing off for a long period attempting and re-attempting ata2: softreset failed. How can I fix this slow boot?

analyze
rob@orion:~$ systemd-analyze


Startup finished in 35.811s (firmware) + 4.664s (loader) + **1min 12.950s (kernel) **+ 17.347s (userspace) = 2min 10.773s
rob@orion:~$ 

[HTML]system info[/HTML]
Jul 04 05:58:19 orion kernel: Linux version 4.8.0-58-generic (buildd@lgw01-21) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.4) ) #63~16.04.1-Ubuntu SMP Mon Jun 26 18:08:51 UTC 2017 (Ubuntu 4.8.0-58.63~16.04.1-generic 4.8.17)


[HTML]journalctl[/HTML]This is where the problem occurs in the boot log:

Jul 04 05:58:19 orion kernel: ata2: softreset failed (1st FIS failed)
Jul 04 05:58:19 orion kernel: ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 04 05:58:19 orion kernel: ata2.00: link online but device misclassified
Jul 04 05:58:19 orion kernel: ata2: link online but 1 devices misclassified, retrying
Jul 04 05:58:19 orion kernel: ata2: reset failed (errno=-11), retrying in 5 secs
Jul 04 05:58:19 orion kernel: ata2: softreset failed (1st FIS failed)
Jul 04 05:58:19 orion kernel: ata2: limiting SATA link speed to 1.5 Gbps
Jul 04 05:58:19 orion kernel: ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jul 04 05:58:19 orion kernel: ata2.00: link online but device misclassified
Jul 04 05:58:19 orion kernel: ata2: link online but 1 devices misclassified, device detection might fail
Jul 04 05:58:19 orion kernel: EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
Jul 04 05:58:19 orion kernel: random: crng init done

---

### Post by Autodave on 2017-07-04
Did this happen all of a sudden? After an upgrade?  What are the specs of the machine?

---

