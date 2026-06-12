---
title: "Firefox HANGS during pages loading"
date: 2005-11-16
forum: General Help
---

### Post by MiddleBrooker on 2005-11-16
Hi,
I'm posting for an help request regarding my Ubuntu Breezy AMD64 system that is very slow to open web pages.

I've tried both default firefox optimized for AMD64 systems and the new firefox-1.5rc2 32bit that I've downloaded from the mozilla website.

Both browsers and Epiphany HANGS dramatically and randomly during pages loading so I have to press enter on the address bar to reload web pages.

Initially I've thinked that the problem should be due to the Marvell Gigabit Ethernet card built in into my system and the sk98ln or the skge drivers, but now I'm using a D-Link USB ethernet adapter with skge and sk98lin modules blacklisted via hotplug and the problem is already here.

Not on the same page, but randomly on various pages I get the blank or a page loaded for 50%!!!

I've edited the /etc/modprobe.d/aliases file with alias net-pf-10 off and I've edited the config of firefox via about:config - network.http.pipelining network.http.proxy.pipelining network.http.pipelining.maxrequests .

Unfortunately nothis is change, I get always blak pages, pleasecan anybody help me to fix this amazing problem?
I can't understand what happen during this firefox hangs because the dmesg don't tell anything about!!

Thanks for all the help.
Regards
MB

---

### Post by curtis on 2005-11-16
I get the exact same problem.
Have been trying to find out what is causing it as well.

---

### Post by MiddleBrooker on 2005-11-17
[QUOTE=curtis]I get the exact same problem.
Have been trying to find out what is causing it as well.[/QUOTE]


Thanks for the reply, I've already tried to change DNS settings or Firefox settings but the problem is with any browser!!!

Maybe is an xorg problem?

Any help for our problem will be very appreciated.

Thankksss

---

### Post by Colosus on 2005-12-06
Has anyone found a solution or a cause for this? I run a website and my users are reporting the problem. The code is fully XHTML 1.0 transitional compliant. I was able to reproduce it briefly on my Ubuntu box, but it then disappeared after no changes. Others are still reporting issues. I'm at a loss.

---

### Post by kevin_hill54 on 2005-12-10
This is happening to me on Mozilla as well. It is embarrising as my son goes to his XP computer because mine is tooooo slooow.

It seems to be on ebay's main search page nearly every time. Hope someone can sort this out.

Thanks everyone.

Kevin

---

### Post by ChuckL on 2007-10-11
If you haven't checked out this thread I would suggest that you do. 

[http://ubuntuforums.org/showthread.php?t=502514&highlight=firefox+hangs+loading+pages](http://ubuntuforums.org/showthread.php?t=502514&highlight=firefox+hangs+loading+pages) 

I had this problem and was tearing my hair out trying all the various solutions, etc. Nothing worked. The problem appears to be with faulty routers and firewalls that are erroneously changing the TCP Window scaling. Current Linux Kernels (2.6.17 and later) enabled TCP Window Scaling by default. Google TCP Window Scaling for more information on this. 

You can run the following which will reset the values that are supported by virtually everything:

    echo 4096 65536 65536 > /proc/sys/net/ipv4/tcp_rmem
    echo 4096 65536 65536 > /proc/sys/net/ipv4/tcp_wmem

To  make these changes last over a reboot add these entries to the end of the /etc/sysctl.conf file:

    net.ipv4.tcp_rmem = 4096 65536 65536
    net.ipv4.tcp_wmem = 4096 65536 65536

Regards,

Chuck

---

