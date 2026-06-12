---
title: "Lockup of Lubuntu 14.03 LTS"
date: 2015-11-27
forum: Hardware
---

### Post by jan53 on 2015-11-27
I recently experienced several hard lockups/freeze of my PC with Lubuntu 14.03 LTS (mouse and keyboard) when browsing with Firefox, the PC had to be restarted. Here is the output of dmesg:


jan@jan-desktop:~$ dmesg | tail
[    6.010304] init: plymouth-upstart-bridge main process (1131) terminated with status 1
[    6.010327] init: plymouth-upstart-bridge main process ended, respawning
[    6.156912] r8169 0000:04:00.0 eth0: link up
[    6.156932] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[    8.152353] audit_printk_skb: 153 callbacks suppressed
[     8.152359] audit: type=1400 audit(1448352647.733:62):  apparmor="DENIED" operation="exec" profile="/usr/share/hplip/systray.py"  name="/bin/ping" pid=1488 comm="hp-upgrade" requested_mask="x"  denied_mask="x" fsuid=1000 ouid=0
[   16.399218] init: plymouth-stop pre-start process (1901) terminated with status 1
[    34.141381] audit: type=1400 audit(1448352673.716:63):  apparmor="STATUS" operation="profile_replace" profile="unconfined"  name="/usr/lib/cups/backend/cups-pdf" pid=2040 comm="apparmor_parser"
[    34.141397] audit: type=1400 audit(1448352673.716:64):  apparmor="STATUS" operation="profile_replace" profile="unconfined"  name="/usr/sbin/cupsd" pid=2040 comm="apparmor_parser"
[   34.142052]  audit: type=1400 audit(1448352673.716:65): apparmor="STATUS"  operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd"  pid=2040 comm="apparmor_parser"
jan@jan-desktop:~$ 

What can be the reason and how to fix it ?

---

### Post by TheFu on 2015-11-27
That info doesn't seem related.

If this happens, can you ssh in from another machine? It could just be a GUI lockup, not the entire OS.

---

### Post by jan53 on 2015-11-27
It sure could be a GUI lockup but I am not experienced enough to test it. Can you get me an advice ?

---

### Post by TheFu on 2015-11-27
> **jan53 said:**
> It sure could be a GUI lockup but I am not experienced enough to test it. Can you get me an advice ?

Sure.

Use ssh from another machine to remotely connect to the box showing the issue. Of course the ssh-server must be setup in advance for this to work.  I setup ssh-servers on every device that allows it - all my android devices have ssh-servers running  too.
 
There must be 1000 ssh-server setup how-tos.

---

### Post by jan53 on 2015-11-27
I am afraid it is overcomplicated for me. Is there any other way how to find out what actally happened (e.g. some other logs etc.) _

---

### Post by TheFu on 2015-11-27
double-post.

---

### Post by TheFu on 2015-11-27
The logs you need to review are overwritten at boot unless systemd binary logging is used. So probably not. You can look in /var/log/ to see if there is anything interesting happening.
[http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files) tries to explain, but isn't written for beginners.

The logs after a failure should be available and accessible by booting from a different linux OS. Like a flash drive. It can be complicated to explain, but if you use the "Try Ubuntu/Lubuntu/Xubuntu" choice the logs on the installed version should be viewable.

I've seen presentations on the journalctl tool, but have successfully avoided it on my systems. When 16.04 is released, I'll learn some about it. 14.04 does not use systemd, so this isn't any help for you today.

Hope this makes sense.

---

### Post by jan53 on 2015-11-29
OK, it looks I have to wait till 16.04 release. But anyway, the line in dmesg:

init: plymouth-stop pre-start process (1901) terminated with status 1

should mean something ?

---

### Post by jan53 on 2016-01-19
On the more, it often happens that some letters are missing on display. Can it have any connection with the faulty i910 graphic driver and how possibly to re-install i910 driver in my PC ?

---

