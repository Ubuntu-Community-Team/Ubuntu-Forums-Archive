---
title: "Upgrade to 9.04, console login timeout"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by groverblue on 2009-05-12
I've been having problems with Ubuntu since I upgraded to 9.04.  My primary concern is the time in which it takes to authenticate a login and sudo command.

When logging into Gnome, it takes about 2 minutes to login.  The logon screen appears to freeze, but after a period of time the desktop loads.

Then there is **sudo**.  Running a sudo command can take well over a minute, about the same time as the desktop login.

Finally, there is the console login (Ctrl+Alt+F1).  The is the result every time:

```
MYHOST: user1
passsword:

Login timed out after 60 seconds.

Ubuntu 9.04 MYHOST tty1
```

I timed an **ssh login** from a remote host and it took nearly 2 minutes before it timed out on authentication of my password.  Doing an ssh from the local host (MYHOST) failed as well.  Yes, ssh is running and is accessible.

I'm not sure if it's an issue at the networking/resolution level, so here is some of that info:

This is my **/etc/hosts** file:
```
127.0.0.1	localhost
127.0.1.1	MYHOST
```

This is my routing table:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.11    0.0.0.0         UG    100    0        0 eth0
```

I'm not sure why the virtual bridge (virbr0) is configured.  I removed all bridge definitions from **/etc/network/interfaces**:

```
MYHOST:/$ more /etc/network/interfaces 
auto lo eth0
iface lo inet loopback
iface eth0 inet dhcp

#auto br0
#iface br0 inet dhcp
#        bridge_ports eth0
#        bridge_fd 9
#        bridge_hello 2
#        bridge_maxage 12
#        bridge_stp off
```


Lastly, here is some **dmesg** output:
```

[   13.072543] e1000e 0000:00:19.0: irq 2302 for MSI/MSI-X
[   13.073093] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.549383] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   14.549385] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   14.549860] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   22.406543] Bridge firewalling registered
[   22.614519] virbr0: starting userspace STP failed, starting kernel STP
[   23.078330] ip_tables: (C) 2000-2006 Netfilter Core Team
[   23.753155] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   23.753291] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   23.753292] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   23.753293] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   25.152504] eth0: no IPv6 routers present
[   33.316006] virbr0: no IPv6 routers present

```

I wonder if the bridge has anything to do with it.  Everything was working fine in 8.10.

Any help would be appreciated.

---

### Post by groverblue on 2009-05-13
I was on one of the IRC channels, and someone suggested that it might be a PAM issue.  I'd like to investigate this to find out for sure; unfortunately, I don't have knowledge of PAM.

Can someone point me in the right direction?

---

