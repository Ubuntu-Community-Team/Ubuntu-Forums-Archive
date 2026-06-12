---
title: "Eee box's JMicron NIC driver on 9.10 server"
date: 2010-01-31
forum: Hardware
---

### Post by Jello53 on 2010-01-31
Hi everyone,

I've been trying to get Ubuntu 9.10 server to run on a Atom N270 EEE Box. I've successfully installed it but fail at getting the NIC to work.

lspci:
01:00:0 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 11)

This forum discussion ([https://bugs.launchpad.net/ubuntu/+bug/400297](https://bugs.launchpad.net/ubuntu/+bug/400297)) tells me the driver should be included with in the Karmic 9.10 Alpha 2.6.31 kernel but I've had no success.

uname -r:
2.6.31-14-generic-pae

Any help would be greatly appreciated.

---

### Post by go-yoshimura on 2010-02-04
Hi!

- I got similar problem.
  In my own case, latest driver is the answer.
- Visit support site and get latest driver from here[FONT=monospace]
[/FONT]   [ftp://driver.jmicron.com.tw/jmc2xx/Linux/](ftp://driver.jmicron.com.tw/jmc2xx/Linux/)
- [ftp://driver.jmicron.com.tw/jmc2xx/Linux/Readme.txt](ftp://driver.jmicron.com.tw/jmc2xx/Linux/Readme.txt) is helpful 
  build-essential are required as [FONT=monospace]"2. Compiler"
[/FONT]  linux-headers-*,linux-source(I'm nore sure which is the one) are required as "kernel source HEAD" 
Before
root@yoshi-i5:~# ethtool -i eth0
driver: jme
version: 1.0.4
firmware-version: 
bus-info: 0000:07:00.5

After
root@yoshi-i5:~# ethtool -i eth0
driver: jme
version: 1.0.5
firmware-version: 

Linux yoshi-i5 2.6.31-18-server #55-Ubuntu SMP Fri Jan 8 15:51:55 UTC 2010 x86_64 GNU/Linux
root@yoshi-i5:~# lspci | grep JMC250
07:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
root@yoshi-i5:~# grep model /proc/cpuinfo | sort --unique
model		: 37
model name	: Intel(R) Core(TM) i5 CPU       M 540  @ 2.53GHz

thank you

---

