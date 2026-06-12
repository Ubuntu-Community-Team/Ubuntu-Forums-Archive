---
title: "PXE boot failing with Jaunty"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by stulove on 2009-09-21
I am trying to convert an existing Jaunty install to a PXE boot configuration.  I went through the steps at this website:

[https://help.ubuntu.com/community/DisklessUbuntuHowto]("https://help.ubuntu.com/community/DisklessUbuntuHowto")

but the client does not get very far in the boot process.  I had the same setup running with Hardy and the server configuration has not changed, so I'm pretty sure it's a problem with the client.

When I boot, I get the following errors.  I believe this indicates that something is going wrong with ethernet just before the NFS root filesystem is mounted, but I'm not sure what or even if this is the case.  Any help would be appreciated.  Just let me know if you need to see any config files on the client or server.  Thanks in advance.

```

usbcore: registered new interface driver usbhid
usbhid: v2.6:USB HID core driver
Done.
RCP: Registered udp transport module.
RPC: Registered tcp transport module.
IP-Config: eth0 hardware address 00:50:8d:b2:d6:cd mtu 1500 DHCP
eth0: no link during initialization.
ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
IP-Config: no response after 60 secs - giving up
/init: .: line 1: can't open /tmp/net-eth0.conf
Kernel panic - not syncing: Attempted to kill init!
Dumping ftrace buffer:
   (ftrace buffer empty)
```

---

