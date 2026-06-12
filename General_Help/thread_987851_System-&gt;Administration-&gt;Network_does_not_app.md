---
title: "System-&gt;Administration-&gt;Network does not appear in Ubuntu 8.10"
date: 2008-11-19
forum: General Help
---

### Post by FastMady123 on 2008-11-19
System->Administration->Network does not appear in Ubuntu 8.10. I can't find in in the menu. I can only find System->Administration->Network Tools. I want to use this feature so I can rename my computer Is this a bug of Ubuntu 8.10? Did they remove this feature in Ubuntu 8.10? What should I do to have System->Administration->Network in the menu. How can I create it?

---

### Post by plucky on 2008-11-20
> **FastMady123 said:**
> System->Administration->Network does not appear in Ubuntu 8.10. I can't find in in the menu. I can only find System->Administration->Network Tools. I want to use this feature so I can rename my computer Is this a bug of Ubuntu 8.10? Did they remove this feature in Ubuntu 8.10? What should I do to have System->Administration->Network in the menu. How can I create it?

To change computer name manually ```
gksudo gedit /etc/hostname
``` and change the name and save.

You also need to edit the /etc/hosts file and change the name next to the "127.0.1.1" line. ```
gksudo gedit /etc/hosts
```

Good Luck

---

### Post by JpRocks on 2008-11-27
is this not just a band aid to the problem? 

how does one re-build their admin setup, for 'network' support?

---

### Post by coastdweller on 2008-11-27
It's under preferences.

Network Configuration

---

### Post by HereInOz on 2008-11-27
You also may find issues with Network Manager if you are trying to set a static IP and DNS servers.  Network Manager in 8.10 seems to want to go back to a DHCP assigned configuration after each restart.

The way to get around this is to uninstall Network Manager, and set up your network configuration in /etc/network/interfaces for the IP address, and /etc/resolv.conf for the DNS.

Sample files:

/etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address    192.168.0.10
    netmask    255.255.255.0
    network    192.168.0.0
    broadcast  192.168.0.255
    gateway    192.168.0.254
/etc/network/interfaces (END) 

/etc/resolv.conf

nameserver  203.132.54.1
nameserver  203.132.54.132

---

### Post by peterramesh on 2008-12-31
Thanks! It worked.

---

### Post by ton4y on 2009-06-11
I had the same problem, just go to Applications > Add/Remove... switch to 'All available applications', type 'network' in the search field and then install it :)

---

