---
title: "Ubuntu 12.04.4 LTS - iscsi drops because interface goes down / timeoutes"
date: 2014-06-11
forum: Hardware
---

### Post by Don_Pich on 2014-06-11
I have a Drobo 800i that is connected to a HP server via ethernet running 12.04.4 LTS.  It normally runs quite well.

Once a week, the iscsi drops on the server.  What I have found is that it appears as though the interface is dropping.  This happens with both the iscsi interface, and the main network interface:

```
[FONT=Arial]kern.log.1:Jun 6 10:44:14 srv333 kernel: [ 22.392064] bnx2 0000:03:00.1 eth1: NIC Copper[/FONT][FONT=Arial] Link is Down, 1000 Mbps full duplex
kern.log.1:Jun 6 10:44:14 srv333 kernel: [ 22.400851] bnx2 0000:03:00.0 eth0: NIC Copper Link is Down, 1000 Mbps full duplex
[/FONT][FONT=Arial]kern.log.1:Jun 6 10:45:50 srv333 kernel: [ 22.392064] bnx2 0000:03:00.1 eth1: NIC Copper[/FONT][FONT=Arial] Link is Up, 1000 Mbps full duplex
kern.log.1:Jun 6 10:45:50 srv333 kernel: [ 22.400851] bnx2 0000:03:00.0 eth0: NIC Copper Link is Up, 1000 Mbps full duplex[/FONT]
```[FONT=Arial]

I have tried to change the timeout values on the server's iscsi configuration to hopefully prevent the dropped connection.  I simply added 60 seconds to each one of these:

[/FONT]```
node.session.timeo.replacement_timeout = 180node.conn[0].timeo.login_timeout = 75
node.conn[0].timeo.logout_timeout = 75
node.conn[0].timeo.noop_out_interval = 65
node.conn[0].timeo.noop_out_timeout = 65
node.session.err_timeo.abort_timeout = 75
node.session.err_timeo.lu_reset_timeout = 80
```[FONT=Arial]

What is really bothering me is that why the interfaces are dropping in the first place.  I have run through various kernels (3.11.0-18, 3.11.0-20, 3.11.0-23) with no resolution.  I have swapped cables.  Eth0 is connected to a Cisco switch, and I have changed switchports.  Eth1 is directly connected to the Drobo.

I'm running out of ideas.  Anyone have an alternative to what I have been trying?[/FONT]

---

