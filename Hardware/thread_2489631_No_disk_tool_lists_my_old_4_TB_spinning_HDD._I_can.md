---
title: "No disk tool lists my old 4 TB spinning HDD. I can't get in contact with it"
date: 2023-08-05
forum: Hardware
---

### Post by lgujvy on 2023-08-05
I've tried to connect it via an esata cable and via USB. It's not listed with fdisk -l.
How can i mount it?

    ```
dmesg | tail -n 100
```

Doesn't list anything about my large disk.
I have just installed Lubuntu 22.04 LTS

    ```
hpelitebook8470p:~# uname -a
Linux hpelitebook8470p 6.2.0-26-generic #26~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Thu Jul 13 16:27:29 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Autodave on 2023-08-05
Do you feel the disk spin up when powered?  Any noises coming from it?  The last time the disk worked, what operating system was on the computer that was running the disk?

---

### Post by lgujvy on 2023-08-05
It spins up fine. It's being auto-mounted in Lubuntu 16.04 LTS. The filesystem is Ext4.

---

### Post by lgujvy on 2023-08-05
[FONT=arial][COLOR=#232629]Thanks for your help! I switched the casing from Akasa to Icy-Box. Now it auto-mounts. Though the spin-up time was about equal.[/COLOR][/FONT]

---

