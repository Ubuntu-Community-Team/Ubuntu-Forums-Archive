---
title: "Is there a linux equivalent to DUMeter or Netmeter?"
date: 2005-11-16
forum: General Help
---

### Post by shewbox on 2005-11-16
I've been looking at/experimenting with various system monitoring programs such as Gkrellm, and some other netmonitoring plugins for gdesklets, but I have yet to come across a program such as netmeter that shows current network throughput as well as how much bandwidth I've used daily,weekly,monthly, etc.  Does anyone have any recommendations?

---

### Post by AsteriskNix on 2005-11-16
right click on the top bar anywhere you want the monitor:

Add to Panel > Network Monitor and System Monitor are both great throughput plugins similar to DUMETER.

Its a gnome-applet.

I prefer the system monitor version for network utilization, just double click on the second "screen" from the left to tune it.

HTH

---

### Post by d00msay3r3 on 2008-02-03
This is a little late at this point, but for others like myself who may run across this thread.....
You CAN run netmeter in wine under Ubuntu.

---

### Post by sonrock3 on 2008-03-07
Yeah, wine netmeter works!
(in ubuntu-gutsy gnome)

But I have yet to find a similar native package that includes traffic history (daily, weekly, monthly totals + total since user-chosen date).  Lots of bandwidth / speed packages found, but without (it seems?) what I want.
knome + gkrellm fail to produce any menu items or any signs of bing installed - no doubt because not designed for gnome desktop?  (I don't want to try KDE yet).

Any suggestions?

Stephen

---

### Post by vikrant82 on 2008-03-10
I was having a similar discussion in this thread, [http://ubuntuforums.org/showthread.php?t=720255]("http://ubuntuforums.org/showthread.php?t=720255"). 

iptables work fine, just that I can't do weeks and months with this. Moreover I have to write init-scripts to persist bandwidth data accross reboots.

There seem to be lot of tools but most of them lose, their bandwidth data across reboots. 

vnstat seems to do the job, but it suffers from bug, where it adds bogus bandwidth when interface goes down and up. 

Even Dumeter works fine under wine, But I am too looking for some native tool. If you are looking to manage a particular session data then darkstat,bandwidthd seem to do good jobs. But again they seem to lose the data when I reboot.

---

### Post by Vergo on 2008-03-18
> **vikrant82 said:**
> vnstat seems to do the job, but it suffers from bug, where it adds bogus bandwidth when interface goes down and up.
As far as I know, vnStat doesn't have that kind of bug. It just requires to be configured properly in order to work correctly and not all distributions do that by default. It needs to be signalled about interfaces going down and up (for example from /etc/network/if-up.d and if-down.d) since it uses cron and can't therefore track the interface status by it's own. Alternatively with version 1.6 you can configure your maximum bandwidth and vnStat will try to guess possible interface resets using that information.

---

