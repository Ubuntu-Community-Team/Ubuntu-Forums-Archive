---
title: "how to open ports for amule?"
date: 2008-09-20
forum: General Help
---

### Post by StOoZ on 2008-09-20
how do I open certain TCP/UDP ports for amule?

will it risk my computer?

---

### Post by jonian_g on 2008-09-20
No it's not a risk. It is if you open many ports.

If you connect to the internet through a router then take a look on router's manual about port forwarding.

If you don't, I think, you will need a firewall application like firestarter (in the repos) or gufw ( [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html) ).

---

### Post by bruce2000 on 2008-09-20
They port should be opened when you run amule; by default Ubuntu allows access to all open ports. No it's not a risk.

---

### Post by StOoZ on 2008-09-20
first of all thanks , secondly , Gufw is basically a GUI front-end for iptables right?

---

### Post by bruce2000 on 2008-09-20
Yes it is

---

### Post by gaiterin on 2008-09-24
Hi.
Gufw can read your amule configuration and allow the ports according ;) (Tab Preconfigured).
Gufw isn't a GUI for iptables, it's a GUI for ufw.
Best regards.

---

### Post by bruce2000 on 2008-09-24
I thought it went without saying that Gufw is a gui for Ufw...
But it ultimately modifies the iptables rules

---

### Post by altkon on 2009-02-10
> **bruce2000 said:**
> The port should be opened when you run amule; by default Ubuntu allows access to all open ports. No it's not a risk.

By the same talken can I assume that when I run "Transmission Bit Torrent Client" I dont have to open any TCP or UDP Ports for the sake of Higher ID Speed...Presently my download speeds  differ from 1 to appx 120 Kib/s..

Is my performance to be considered normal or should I do something to increase it.:confused:
Thanks a lot
altkon

---

### Post by Yashiro on 2009-02-10
Nothing is blocked on Ubuntu by default. So unless you have ran ufw, iptables or applied some other firewall the only blockage is from your router.

---

### Post by altkon on 2009-02-10
Should I therefore proceed to reset my Router from Dynamic to Static IP and open the TCP4662 and UDP 4672 ports in order to obtain higher ID on aMule because for "Transmission Bit Torrent client" I dont know how to do it and I guess my speeds are already satisfactory.:?:

---

### Post by Yashiro on 2009-02-10
If your router and the application support Upnp or NAT-PmP then just enable that. If they don't have those features, or the implementation is buggy, you will need to open a port on your router and forward it to your computers IP.

The shields up link here [http://www.grc.com/default.htm](http://www.grc.com/default.htm) can tell you when/if your ports are open.

---

