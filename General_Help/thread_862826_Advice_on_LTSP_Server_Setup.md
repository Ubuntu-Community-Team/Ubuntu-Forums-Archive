---
title: "Advice on LTSP Server Setup"
date: 2008-07-17
forum: General Help
---

### Post by cjkeeme on 2008-07-17
Here is what I am trying to do:

[LIST]
[*]Install a LTSP server in my exisiting network
[*]Do not disturb other full client workstations on the network
[*]Have the LTSP gain an IP from the existing DHCP server
[*]Have the terminal clients boot of the LTSP server on current network setup
[/LIST]

I have about 20 workstations on the network already and now I want to add 10 thin clients.  The image below gives an example of what I am looking to accomplish. 

Can I get some suggestions on how I should set this up?  I am a little lost at this point.


[IMG]http://www.keeme.net/images/LTSP.jpg[/IMG]

---

### Post by cariboo on 2008-07-17
Have you had a look here:

[http://wiki.ltsp.org/twiki/bin/view/Ltsp/Documentation](http://wiki.ltsp.org/twiki/bin/view/Ltsp/Documentation)

The documentation is quite good, I tried it several years ago when I was fairly new to Linux. I got thinks to work very easily.

Jim

---

### Post by cjkeeme on 2008-07-18
I took a look at that documentation and it seems incomplete is some areas.  I'm not sure what to do in order to accomplish the above setup correctly.  

Can anyone help me out?  

I want to connect my LTSP server to my current switch and connect thin clients to that same switch and have it work.  There will also be full workstations on this switch.  There is a router already handing out DHCP leases, so the LTSP DHCP server is switched off.

---

### Post by Aearenda on 2008-07-18
Typical router DHCP settings do not allow you to specify the 'next-server' DHCP option that is needed to get the thin clients to boot from the LTSP server.

The key to this setup used to be the ability of the old-style LTSP (version 4.2 and before) to use a different port for client DHCP requests. The LTSP server had a DHCP service running that would respond only to clients broadcasting to this port.

Unfortunately, the LTSP setup in Ubuntu does not have an easy way to use a different port. This process required special settings on the clients as well, of course.

Why don't you turn off the router DHCP, and turn on DHCP on the LTSP server instead? You could make it all work then.

PS: The thin clients need the LTSP server to have a static address for them to use anyway.

---

### Post by cjkeeme on 2008-07-28
Okay, well that is unfortunate that I can not utilize LTSP they way I want it, but I could relay the LTSP server off of the current switch and have a second NIC broadcast the DHCP server needed by the thin clients, right?

Take a look at the diagram below and let me know if this is viable.   

[IMG]http://www.keeme.net/imgs/LTSP.jpg[/IMG]

---

### Post by Aearenda on 2008-07-28
Yes, what you have here will work - it is "as designed". You can also have your full computers on the same network as the thin clients, doing away with the need for the switch between the cable modem and the LTSP server, so long as you turn on NAT in the LTSP server.

```

                                               //==>Full computers
Internet<==>Cable Modem<==>LTSP Server<==>Switch
                                               \\==>Thin Clients

```

The code to allow this is:
```

iptables -A POSTROUTING -t nat -o $EXTIF -d 0/0 \
         -j SNAT --to-source $EXTADDR

echo 1 > /proc/sys/net/ipv4/ip_forward

```
Here I am using SNAT since my LTSP Server's address given by the Cable Modem is essentially static. $EXTIF is the external interface (eg eth0) and $EXTADDR is the static address for eth0.

The 'echo' command turns on routing in the kernel.

This isn't necessarily the best way, but it works for me. In practice this iptables command is one of many used to set up my firewall.

Also, as I said in my previous post, you could have your original setup working if you turn off DHCP in your router and have the LTSP server do all the DHCP serving.

---

