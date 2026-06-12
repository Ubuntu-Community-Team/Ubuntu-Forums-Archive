---
title: "Dell PowerEdge 2850 Hang"
date: 2005-05-18
forum: Hardware &amp; Laptops
---

### Post by Carty on 2005-05-18
I got so excited about ubuntu I installed Hoary 5.04 on the Dell PowerEdge 2850 that we use as our company's firewall(iptables)/websever/(postfix) mail server.

On the average of once a day the box hangs hard, screen is completely blank, can't ping the box, it stops forwarding net traffic, I have to power cycle.

/var/log/messages and syslog just stop cold, no pertinent messages.

I can discern no pattern, happens in the middle of the night or during the day.

I did what research I could on this most excellent forum, figured I'd add pci=noacpi into grub kernel boot line, tried that yesterday, machine hung this morning.

Any ideas about how I can further diagnose the problem or potential fixes I can try would be appreciated.

e.g. is there anything I should look to change in BIOS settings?

I very much appreciate any help and will do my best to contribute back.

-Carty

---

### Post by alastair on 2005-05-18
Is it a "basic" install? i.e. no X windows running etc.? If not, stop X.

Else, on a hang - go to the keyboard and try the "sysrq" buttons i.e.

ALT+SYSRQ+<KEY> - where <KEY> == 

t = dump tasks
m = dump mem

Then you can sync filesystems, remount r/o and reboot :

s - sync
u - remount r/o
b - reboot

Then check the syslog for clues.

Start minimising running processes perhaps and monitor.

---

### Post by Ubuntu Warrior on 2005-11-24
Have you tried Ubuntu Breezy (5.10)? We have been trying unsuccessfully to install Hoary (AMD64 version) on our Dell PowerEdge 2850 server with Xeon processors. The install process cannot 'see' any partitions on which to install.

A post on the Dell forums suggest trying Breezy or reverting to Debian Sarge.

BTW we have successfully installed Breezy onto the Dell PE 2850. No problems so far - viva AMD Opteron processors!!!

---

