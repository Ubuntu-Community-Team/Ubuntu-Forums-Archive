---
title: "Wireless not Working - Intel Centrino Advanced-N WiMax AGN 6250"
date: 2010-07-12
forum: Hardware
---

### Post by jseabold on 2010-07-12
[Edit: crossposted in the networking forum [post=9582686]here[/post]]

All,

Haven't been able to get my wireless card working in Ubuntu 10.04.  

$ uname -r
2.6.32-23-generic

It's an Intel Centrino AGN 6250.  

I've installed the Intel 6050 microcode and rebooted from here
[http://intellinuxwireless.org/?n=Downloads](http://intellinuxwireless.org/?n=Downloads)

$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
$ rfkill unblock all
$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

$ sudo ifconfig wlan0 up 
SIOCSIFFLAGS: Unknown error 132

Seems odd.  Any other info I can provide?  Any help would be appreciated.

---

### Post by jseabold on 2010-07-12
Wondering also if all of these should be there?

$ ls -la /lib/firmware/ | grep ucode
-rw-r--r--  1 root root  335056 2010-05-26 12:10 iwlwifi-1000-3.ucode
-rw-r--r--  1 root root  150100 2010-05-26 12:10 iwlwifi-3945-2.ucode
-rw-r--r--  1 root root  187972 2010-05-26 12:10 iwlwifi-4965-2.ucode
-rw-r--r--  1 root root  345008 2010-05-26 12:10 iwlwifi-5000-1.ucode
-rw-r--r--  1 root root  353240 2010-05-26 12:10 iwlwifi-5000-2.ucode
-rw-r--r--  1 root root  337400 2010-05-26 12:10 iwlwifi-5150-2.ucode
-rw-r--r--  1 root root  462280 2010-05-26 12:10 iwlwifi-6000-4.ucode
-rw-r--r--  1 root root  463692 2010-07-11 22:35 iwlwifi-6050-4.ucode

---

### Post by jseabold on 2010-07-13
For posterity, I solved the problem.  I have a dual boot system.  Booted into Windows 7, toggled wireless off and then on, reboot into Ubuntu.  Everything works.

---

### Post by whitethunder922 on 2010-09-08
> **jseabold said:**
> For posterity, I solved the problem.  I have a dual boot system.  Booted into Windows 7, toggled wireless off and then on, reboot into Ubuntu.  Everything works.

I was certain that this solution was too silly to be true, but I was wrong. Never underestimate the power of Windoze. </sarcasm> Thanks jseabold!

---

