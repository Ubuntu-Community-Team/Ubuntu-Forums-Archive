---
title: "Upgrade problems 9.04- no ethernet"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by vinced on 2009-04-26
I was running Ubuntu Studio 8.10 when I used the Update Manager to upgrade to 9.04.
When the upgrade was complete, I could no longer connect to the internet. It seems that my ethernet connection is no longer recognized. When I try to ping Ubuntu.com I get an error message that the address cannot be found. When I try to configure the ethernet connection from Network Tools I receive a warning that the interface does not exist. 
Prior to the upgrade everything was fine. The ethernet connection works on my laptop running Ubuntu 9.04. It only doesn't work on the d:confused:esktop. I tried to search for an answer in the forums without any luck. Hoping to find a solution to the problem, other than reinstall.
Thanks,
Vince

---

### Post by cariboo on 2009-04-26
Open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network
```

and paste the output in your next post.

---

### Post by vinced on 2009-04-26
Cariboo907 wrote:

sudo lshw -C network

and paste the output in your next post.


 Here is the result:

  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ba:72:dc:1a:f2:d2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes




Thanks,
Vince

---

