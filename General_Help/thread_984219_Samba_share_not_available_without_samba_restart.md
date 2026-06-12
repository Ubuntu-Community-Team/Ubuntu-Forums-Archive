---
title: "Samba share not available without samba restart"
date: 2008-11-16
forum: General Help
---

### Post by g0l3m on 2008-11-16
Hello all,

I'm having a weird problem with my samba configuration.
I boot my ubuntu box but when I try to access my samba share from another box I get "x.x.x.x is not accessible". 

However, if I go into my ubuntu box and do
sudo /etc/init.d/samba restart
then everything works fine!

I've looked at my services and "Folder sharing service (samba)" is enabled.
I've no idea why this restart is needed before samba starts working!
Any ideas?

cheers,
g.

---

### Post by cmnorton on 2008-11-16
Look in your logs (/var/log...) and see if there is something going wrong when you first boot. How soon after boot are you expecting these shares to be active?

---

### Post by bab1 on 2008-11-16
Check to see it the Samba daemons are running when you first boot.  After a fresh boot up, try this from the CLI:```
ps -ef | grep nmd 
```

You should get something like the following:
```
bruce@malibu:~>ps -ef | grep mbd
root      4432     1  0 09:37 ?        00:00:00 /usr/sbin/nmbd -D
root      4434     1  0 09:37 ?        00:00:00 /usr/sbin/smbd -D
root      4476  4434  0 09:37 ?        00:00:00 /usr/sbin/smbd -D
bruce     5907  5885  0 12:04 pts/0    00:00:00 grep --color=auto mbd

```

---

### Post by g0l3m on 2008-11-18
Samba daemons running fine.
Logs show normal startup.

log.smbd:
```

[2008/11/18 19:38:30,  0] smbd/server.c:main(1213)
  smbd version 3.2.3 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008

```

HOWEVER, log.nmdb:

```

[2008/11/18 19:38:40,  0] nmbd/nmbd_subnetdb.c:create_subnets(277)
  create_subnets: Unable to create any subnet from given interfaces. Is your interface line in smb.conf correct ?

[2008/11/18 19:48:57,  0] libsmb/nmblib.c:send_udp(839)
  Packet send failed to 192.168.0.255(138) ERRNO=Invalid argument

```

My samba.conf has
```

 interfaces = 127.0.0.0/8 eth0

```

But my network/interfaces has
```

auto lo
iface lo inet loopback

```

and no mention of eth0...Is this normal?

Here's something else that may be relevant...When I reboot, my network manager forces itself to "Auto eth0", with DHCP settings that don't work. Every time I have to click and select my custom static IP setup for networking to work. Could this be why after a samba restart things are working normally?  Is there a way for the network manager to default to my static configuration? Even when I delete Auto eht0, it goes and creates one.

---

