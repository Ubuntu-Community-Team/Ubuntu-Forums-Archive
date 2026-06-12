---
title: "How to enable dual core?"
date: 2010-08-18
forum: Hardware
---

### Post by opto09 on 2010-08-18
I've recently realised that my laptop (Dell Inspiron 640m) which should come with a dual core, doesn't actually run like one on Ubuntu. For example when I look at the system monitor, I see only one CPU trace and when I click on system it says I have the Intel Core 2 CPU T5500@1.66 GHz. 

Now I know I have a dual core. The sticker on the chassis says it should have an Intel Centrino Duo. Question is, how do I get the dual core functionality back? Please help!

I'm using Lucid 10.04 LTS.

---

### Post by Fafler on 2010-08-18
Open a terminal and type uname -a If the next word after the version number is SMP, you are already running a SMP kernel and thus using both cores. You could also do a cat /proc/cpuinfo | grep name If it lists two CPU's, you have SMP enabled.

---

### Post by opto09 on 2010-08-18
I'll try this at home tonight but I don't think it will solve my problem. At work where I know I also have a dual core, the system manager shows me two traces - 1 for each CPU. At home, it only shows me one. Also I ran dmesg last night and it said something like:
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs

Edited: Ok I've managed to try the commands you mentioned above

```
uname -a
Linux mycomp 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux

cat /proc/cpuinfo | grep name
model name	: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
```

So how do I know if I've got multi-core enabled?

---

### Post by Kangarooo on 2012-12-14
Yes i also want to be sure Dual and for future Quad and Sexi core to be working.

---

### Post by Bucky Ball on 2012-12-14
Are you using the 32bit or 64bit version of Ubuntu? 64bit for dual-core. Probably not your problem but just mentioning ...

---

### Post by Bashing-om on 2012-12-14
opto09; Hi !

dmidecode, amongst bunches of info, will show the processor status. Terminal code:
```
sudo dmidecode | less
``` pipes the output to less for paging through the output, and "q" to quite the utility.
[INDENT][INDENT]my 2 pennies worth < == BDQ

[/INDENT][/INDENT]

---

### Post by tgalati4 on 2012-12-14
A Core2 Duo would be a dual-CPU processor.  A Core2 CPU would imply a single processor.  A centrino duo is just a sticker.  It's just marketing to get you to buy the thing.

```
dmesg | more
or
more /var/log/kern.log

```

Spacebar to page though it and q to quit.  You should see BogoMIPs rating for both cpu's.



For a dual PentiumD it would look like:

Dec 11 12:13:51 aopen-mint14 kernel: [    0.084069] Brought up 2 CPUs
Dec 11 12:13:51 aopen-mint14 kernel: [    0.084074] Total of 2 processors activated (11788.29 BogoMIPS).

It quite clearly shows 2 processors and twice the BoboMIPs of each processor separately--which is also shown in the file.

---

