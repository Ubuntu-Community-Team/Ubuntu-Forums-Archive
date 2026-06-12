---
title: "how to configure squid.conf file for proxy"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by manojpawar on 2009-10-12
hi,
  I have installed squid proxy server on my ubuntu server but when I configure squid.conf file then i am getting 


aclParseIpData: WARNING: Netmask masks away part of the specified IP in '123.238.128.1/24'
2009/10/12 09:38:46| parseConfigFile: squid.conf:462 unrecognized: 'iptables'
2009/10/12 09:38:46| parseConfigFile: squid.conf:463 unrecognized: 'iptables'
squid: ERROR: Could not send signal 1 to process 3878: (3) No such process
   ...done.
                please help me how shoud i configure this file,

---

### Post by x.knight on 2009-12-11
use 255.255.255.255 instead of 24 subnet mask
and you can not use iptables in squid.conf

---

