---
title: "openssh on Asus EeePC900 not permitting connections despite very valid config"
date: 2009-05-28
forum: Hardware
---

### Post by jabo969 on 2009-05-28
Please let me know if you are finding the same issue and any workarounds.

What I can tell you.

Fresh install of UNR 9.04 into Asus EeePC900  with partitions of / and /boot only, no swap.
sshd_config setup properly and sshd daemon running.
ssh listener visible using 'netstat-an' on 0.0.0.0:22 so implied listening on all interfaces.
iptables configured with no rules so effectively no limits ( all three tables are empty I,O,F).
ssh reachable when connecting from same machine on any reachable interface.
when trying to connect from remote, other machines are reachable inside same network via ssh through internet router so no apparent isp problems with blocking ports.
/etc/services properly confirms 22/tcp and 22/udp to ensure inetd server assigning proper ports.
DSL connection configured and PPPoE automatically engages over DHCP ethernet link.
Despite all of this, any connection attempt made from 'outside' is dropped with Connection refused.

From the local ethernet, before DSL setup, the machine is reachable via ssh, so ssh is functioning.

Is there anything in the default configuration that would block non local IPs from connecting?
Is there any need to modify the routing tables? default routes?

Please let me know if you have learned anything about this issue.

Thanks.

---

### Post by dmizer on 2009-05-28
Are you testing this from within your network or outside your network?

---

### Post by jabo969 on 2009-05-28
Testing from both.
From behind the DSL modem, on the local ethernet there are no issues.
Only when coming from a remote IP, does this issue occur.
When the same attempt is made to another computer inside the network connecting from outside, than runs openssh, I am successful.

---

### Post by alecz20 on 2010-08-25
I have a similar problem:

two computers behind the network, one is reachable, the other isn't:

- Ubuntu 9.04 server edition: reachable from anywhere via port 22

- Ubuntu 9.10 desktop, reachable only inside network via port 2222

Using a website to check if the port is open, it says port 2222 is open at my home ip.

Did you find a solution to this?


EDIT:

It just occured to me that I have always been trying to connect from work, and it is possible that the system there is blocking any port besides 22, hence the reason I can only connect to the computer that is using port 22.

---

