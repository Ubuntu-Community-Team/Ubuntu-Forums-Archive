---
title: "Webmin Firewall setup frustrations"
date: 2008-08-29
forum: General Help
---

### Post by Zeroangel on 2008-08-29
OK, so i've been following this guide:
[http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html)

And its a little vague, and doesnt mention a few small details, but I think I have set up my firewall properly. The problem is, while my machine can assign DHCP on Eth2 (my external network AKA internet modem), it does not seem to properly do any NAT on eth1 (the internal network). How do I know it can talk to my server?

Well, it assigns an IP, and I can access my Ubuntu webserver by typing in its IP address (192.168.0.1) on the internal network.

My setting in webmin look as follows:
[IMG]http://zeroangel.overminddl1.com/misc_images/firewallcfg1.gif[/IMG]
----------
And my NAT page...
[IMG]http://zeroangel.overminddl1.com/misc_images/firewallcfg2.gif[/IMG]

This is correct, right?

Additionally, I have a script set to run on boot up:
```
    echo Enabling IP Forwarding
    /bin/echo 1 > /proc/sys/net/ipv4/ip_forward
    echo Restoring IPTables settings
    /sbin/iptables-restore /etc/webmin/firewall/iptables.save
    echo Done
```I have run it several times for good measure. Doing it the console way doesnt print any errors.

I am tearing out my hair trying to get this to work. Please help!

---

### Post by Zeroangel on 2008-08-29
*bump*

---

