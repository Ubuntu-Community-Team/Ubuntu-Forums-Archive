---
title: "Ubuntu Freezes Instantly for no reason"
date: 2008-09-29
forum: General Help
---

### Post by Axerthon on 2008-09-29
As the title says, I made a system update a few days ago...

And it crashes VERY VERY often... For example.. I let the computer opened all the night, when I get back to it, instant freeze, I can move only the mouse... The rest is destroyed... I stay on Pidgin & browse the web... again sometimes freezes that way..

When I copy paste to my MP4 Player, and in general when I copy-paste files anywhere..Also when I plug the MP4 Player after ~10-15 seconds, complete freeze and the only solution is reset from the button..


Any help please? I am getting mad... Thanks a lot :(

---

### Post by phidia on 2008-09-29
Try booting into a previous kernel and see if that solves the freezing.
If it does you may need to file a bug report. If you still have a problem when booted with the previous kernel you should boot in recovery mode and look at System > Administration > System Log and/or /var/log/messages.

---

### Post by Axerthon on 2008-09-29
Wait, I am newb... How can I boot in a previous Kernel? And I boot in a previous kernel after the crash happens and I reset?

---

### Post by Axerthon on 2008-09-29
Okay, here's the log:

---

### Post by Tijl on 2008-09-29
Hello, I was about to post on this forum when i read this thread. I have exactly the same problem as the starter of this topic. Ubuntu freezes for no reason. Very often. I've just started using linux since a week so my installation is really fresh. I have the freezes only since today. 
Thanks in advance

---

### Post by Glucklich on 2008-09-29
> **phidia said:**
> Try booting into a previous kernel and see if that solves the freezing.
If it does you may need to file a bug report. If you still have a problem when booted with the previous kernel you should boot in recovery mode and look at System > Administration > System Log and/or /var/log/messages.

I did what you recommended and this is what I got. No matter what kernel I use, the message is always the same.

Sep 29 19:14:27 computer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Sep 29 19:14:27 computer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Sep 29 19:14:27 computer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Sep 29 19:14:27 computer dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu
Sep 29 19:32:29 computer -- MARK --

What kind of problem is this? Wireless problem? How can this be solved?
Turning off the wireless is not an option since I use it to connect to the Internet.

---

### Post by Axerthon on 2008-09-29
> **Tijl said:**
> Hello, I was about to post on this forum when i read this thread. I have exactly the same problem as the starter of this topic. Ubuntu freezes for no reason. Very often. I've just started using linux since a week so my installation is really fresh. I have the freezes only since today. 
Thanks in advance
Yes, and a friend just installed Ubuntu and has the same problems... It's getting very annoying.

BTW welcome on the forums :p

---

### Post by Glucklich on 2008-09-29
I'm sorry, seems like I've double posted.

---

### Post by Axerthon on 2008-09-29
I searched over Google.. nothing returns to describe this problem as it is.

---

### Post by Tijl on 2008-09-29
I've done some searching and it seems to be caused by various problems with drivers/hardware. People say it can be solved by installing an older kernel version or an alpha version of the new one. I'm not sure how I would have to do that or where to get those as I'm really new to this.
But the problem is widely known as far as that bugreport goes

---

### Post by phidia on 2008-09-29
There are a few hits on the error messages and perhaps a related thread [here]("http://ubuntuforums.org/showthread.php?t=880732"). 

I don't know if the solution there will work for your situation but we can keep trying to find one.

---

### Post by Glucklich on 2008-09-29
Well. Guess I have to wait until the definitive release comes. My ethernet is affected by a bug they describe as hardware damaging. And I have too much work data that I wouldn't like to see erased due to a test version. Anyway, it's good to know the Wireless issue is taken care of.

---

### Post by Iwannakillyou on 2008-09-29
I have been waiting for about 5 days now but the shipping times are 10-19 days. As soon as I get them I will let you know. I have not seen you on that forum for a long time now and I was wondering where you are? How did it go with the collection that you got? Here is the link to the beads again [http://www.liangdianup.com/beadscrafts_1.htm](http://www.liangdianup.com/beadscrafts_1.htm) and here is the link to the Swarovski beads [http://www.liangdianup.com/inventory/900020.htm](http://www.liangdianup.com/inventory/900020.htm) if those links don't work then you can goto [www.lducompany.com](www.lducompany.com) and click on the beads picture, that should take you right there. I hope you see this message and get back to me cause I miss talking to you :)

---

### Post by Axerthon on 2008-09-30
lol.

[https://edge.launchpad.net/~kernel-ppa/+archive](https://edge.launchpad.net/~kernel-ppa/+archive)

I put the sources in my sources.list file, do apt-get update... And there is no new kernel to update to...

---

### Post by Axerthon on 2008-10-01
bump....

---

### Post by eldenico on 2008-10-01
Well, 

I have:

Aspire 5570z
Intel pentium dual core T2080
120 GB HD
Intel GMA 950 (Video)
1 GB RAM

Kubuntu Hardy Heron

OK, For several weeks kubuntu (Gutsy Gibon) has been freezing with no reason, last week I upgraded to Hardy Heron to solve my problem but it didn't worked. Before that I thought Ktorrent was the problem, but I turned it off, and now I got the same problem. Suddenly it freezes, no mouse, no keyboard, no ALT+TAB, nothing at all and after five minutes it works again. I think this is a very serious bug. I can't wait for five minutes every 15 minutes for Linux to work again. Can anyone suggest me any other Linux that works fine?

Thanks

---

### Post by Axerthon on 2008-10-01
Ubuntu is good, but this bug is very very annoying...

---

