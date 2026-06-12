---
title: "Unexpected memory size on Asire Timeline 3820tg, ubuntu 10.04"
date: 2011-08-05
forum: Hardware
---

### Post by lizar on 2011-08-05
I have two RAM cards by 2GB(4GB at all), on my Acer Aspire Timeline laptop. 

But Ubuntu 10.04 32bit says I only have like 2.3GB of RAM. Windows 7 says i have all 4GB. 

```
$ sudo lshw -C memory | grep -A 50 -i "system memory"
       description: System Memory
       physical id: d
       slot: System board or motherboard
       size: 4GiB
     *-bank:0
          description: SODIMM Synchronous 1066 MHz (0.9 ns)
          product: HMT125S6TFR8C-G7
          vendor: 80AD
          physical id: 0
          serial: 00538765
          slot: M1
          size: 2GiB
          width: 64 bits
          clock: 1066MHz (0.9ns)
     *-bank:1
          description: SODIMM Synchronous 1066 MHz (0.9 ns)
          product: HMT125S6TFR8C-G7
          vendor: 80AD
          physical id: 1
          serial: 00538767
          slot: M2
          size: 2GiB
          width: 64 bits
          clock: 1066MHz (0.9ns)
     *-bank:2
          description: SODIMM Synchronous [empty]
          physical id: 2
          slot: M3
     *-bank:3
          description: SODIMM Synchronous [empty]
          physical id: 3
          slot: M4
```

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          2318       2077        240          0         44        787
-/+ buffers/cache:       1245       1073
Swap:         1929         49       1880
```


```
$ uname -a
Linux alex-laptop 2.6.32-33-generic #71-Ubuntu SMP Wed Jul 20 17:30:40 UTC 2011 i686 GNU/Linux
```







What it can be?

---

### Post by Mr. Shannon on 2011-08-05
32bit operating systems have a ceiling on how much memory they support.  Actually 64bit operating systems have a ceiling as well, but it's high enough not to worry about.  The memory which is shown seems a little low so there may be other problems, but first make it so Ubuntu can support all 4GB of memory.  To do that, follow the instructions at the link below to install PAE (Phisical Address Extension) or install the 64bit version of Ubuntu.

[https://help.ubuntu.com/community/EnablingPAE]("https://help.ubuntu.com/community/EnablingPAE")

The link below is the first set of instructions I found but I decided to replace it with the one above.

[http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/]("http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/")

---

### Post by lizar on 2011-08-05
> **Mr. Shannon said:**
> 32bit operating systems have a ceiling on how much memory they support.  Actually 64bit operating systems have a ceiling as well, but it's high enough not to worry about.  The memory which is shown seems a little low so there may be other problems, but first make it so Ubuntu can support all 4GB of memory.  To do that, follow the instructions at the link below to install PAE (Phisical Adress Extension) or install the 64bit version of Ubuntu.

[https://help.ubuntu.com/community/EnablingPAE]("https://help.ubuntu.com/community/EnablingPAE")

The link below is the first set of instructions I found but I decided to replace it with the one above.

[http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/]("http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/")

Thank you very much, I has installed PAE, it helped. Now i can keep all my pron in tmpfs for really quick access.:D

---

