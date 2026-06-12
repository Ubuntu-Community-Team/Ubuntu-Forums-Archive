---
title: "Slow resume from suspend caused by dhclient"
date: 2008-12-19
forum: Hardware
---

### Post by anton_mellit on 2008-12-19
I am not sure if this is the right place to post because I already solved the problem for myself.

I experienced extremely slow wakeup from suspend (almost 1 minute) and the reason was that I have two (apart from 'lo') network interfaces 'ath0' and 'eth0' marked as "auto", both dhcp, in '/etc/network/interfaces'. Now when pm-utils wakes me up in '/usr/lib/pm-utils/sleep.d/50modules' it does the following line:

invoke-rc.d networking restart

I think this line should return immediately, but it does not. It calls "ifup -a" which in its turn calls 'dhclient', and the last one does not return until it has tried long enough to get dhcp working on all interfaces. Naturally I do not always have both ethernet and wireless connections available therefore it takes too long.

Workaround:

add '&' at the end of the line above to make it like:

invoke-rc.d networking restart &

This causes it to run in the background, therefore resume works fast (5 sec)

I do not think this is a right solution. Actually the same problem causes my laptop to boot much longer than it should, actually, more than twice longer. I think it would be right if starting/restarting service 'networking' was fast, and this should be done somehow by making all dhcp initialization to be done in the background. However I do not know how to do it. Should I post about it somewhere?

Anton

---

### Post by sdennie on 2008-12-19
Another option would be to comment out the networking interface that you are not using from /etc/network/interfaces or use something like NetworkManager to manage your interfaces for you (in which case you'd only have the loopback interface in /etc/network/interfaces).  Your fix seems ok but, commenting out the unused interface or using NetworkManager would also fix the problem at bootup time.

---

### Post by anton_mellit on 2008-12-19
> **vor said:**
> Another option would be to comment out the networking interface that you are not using from /etc/network/interfaces or use something like NetworkManager to manage your interfaces for you (in which case you'd only have the loopback interface in /etc/network/interfaces).  Your fix seems ok but, commenting out the unused interface or using NetworkManager would also fix the problem at bootup time.

Well, the problem with commenting out interface (or removing 'auto' keyword) is that it stops to work automatically. At home I use wireless, at work I use ethernet, I want them both to work without my intrusion. So I really want dhclient to try to connect, I just do not want to wait, when I open my laptop I want to start using it immediately. May be NetworkManager is a solution, never tried it.

---

