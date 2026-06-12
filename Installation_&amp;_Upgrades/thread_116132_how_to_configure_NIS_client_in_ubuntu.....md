---
title: "how to configure NIS client in ubuntu...."
date: 2006-01-12
forum: Installation &amp; Upgrades
---

### Post by arunkumar on 2006-01-12
hi 
    i am new to ubuntu, i am tryint to configure nis client in ubuntu , my server (NIS) is fedora core 2 . is anyone there who knows how to configure nis on ubuntu please tell me..... 

thanx

-arun

---

### Post by amohanty on 2006-01-12
[http://doc.gwos.org/index.php/HoaryNIS](http://doc.gwos.org/index.php/HoaryNIS)

Its for hoary but should work for breezy too.

For a more detailed manual setup:
[http://www.tldp.org/HOWTO/NIS-HOWTO/settingup_client.html](http://www.tldp.org/HOWTO/NIS-HOWTO/settingup_client.html)

AM

---

### Post by Rene_Merida on 2006-01-12
Hello,

First, I'd like to request excuse me for my english, it's not very well.

Second: I did the instruction of these Internet directions but when I like start NIS services in Ubuntu 5.10, the system show me the following messages:

# starting NIS services: ypbind  [binding to YP server ..... backgrounded]

and never start the NIS server.

In one of internet directions talk me that ypbind must to be version 2.0, then how to know  the ypbind version?

Thanks,

Rene_Merida
Venezuela

---

### Post by amohanty on 2006-01-12
I believe the instructions are for an NIS _client_ not an NIS server. To setup an NIS server you need to do more stuff. Some good links:

[http://www.debian-administration.org/articles/36](http://www.debian-administration.org/articles/36)
[http://www.section6.net/wiki/index.php/Configuring_NIS_Services_in_Linux](http://www.section6.net/wiki/index.php/Configuring_NIS_Services_in_Linux)

HTH
AM

---

### Post by Rene_Merida on 2006-01-13
Ok amohanty.

But I refered about of NIS client. This message that I show you is when I intented start NIS client service. (/etc/init.d/nis restart)

The NIS server already it's configured but I can't connect me as CLIENT.

Specially thanks,

Rene_Merida
Venezuela

---

### Post by amohanty on 2006-01-13
So let me get this straight:

1. You setup a machine A as NIS server
2. From the same machine A you are trying to connect as the client

Is that correct?

AM

---

### Post by Rene_Merida on 2006-01-17
OK, already resolve the problem.
Thanks by help me. I read all pages refered this topic and in a chat a friend say me: "Edit /etc/init.d/nis and to write IP number of Server NIS in NISSERVER=192.168.1.1 and BINGO !!  my PC has conecction.

Specially thanks !!

Rene_Merida
Venezuela

---

### Post by Surdge on 2006-03-02
i followed various guides on configuring a NIS client on Ubuntu but still i did not succeed on configuring it right.

```

Setting NIS domainname to: mydomain.local
Starting NIS services: ypbind [binding to YP server .......... backgrounded]

```

This is where i'm stuck. My NIS server should be a NITIX server located @ 192.168.1.1 when i ping my NITIX it aswers and also when i ping mydomain.local it answers correctly
Nitix Webconfigdemo wil give you an idea of how simple it is to enable NIS in Nitix
[http://www.nitix.com/~demo/index.cgi?page=local&save=local&localnet-form=foo&hostname=weaver&domain=net-itech.com&show_status_page=1&rsync-server=1&dns-server=0&snmp-server=0&snmp-community=public&nis-server=1&icsa-compat=0&ntp-server=1&timezone=GMT-5&localtime=0](http://www.nitix.com/~demo/index.cgi?page=local&save=local&localnet-form=foo&hostname=weaver&domain=net-itech.com&show_status_page=1&rsync-server=1&dns-server=0&snmp-server=0&snmp-community=public&nis-server=1&icsa-compat=0&ntp-server=1&timezone=GMT-5&localtime=0)

My Question now is how can i be 100 % sure that my NitixBox is correctly functioning as a NIS server

---

### Post by cajetanus on 2006-10-18
> **Surdge said:**
> i followed various guides on configuring a NIS client on Ubuntu but still i did not succeed on configuring it right.

```

Setting NIS domainname to: mydomain.local
Starting NIS services: ypbind [binding to YP server .......... backgrounded]

```

This is where i'm stuck. My NIS server should be a NITIX server located @ 192.168.1.1 when i ping my NITIX it aswers and also when i ping mydomain.local it answers correctly
Nitix Webconfigdemo wil give you an idea of how simple it is to enable NIS in Nitix
[http://www.nitix.com/~demo/index.cgi?page=local&save=local&localnet-form=foo&hostname=weaver&domain=net-itech.com&show_status_page=1&rsync-server=1&dns-server=0&snmp-server=0&snmp-community=public&nis-server=1&icsa-compat=0&ntp-server=1&timezone=GMT-5&localtime=0](http://www.nitix.com/~demo/index.cgi?page=local&save=local&localnet-form=foo&hostname=weaver&domain=net-itech.com&show_status_page=1&rsync-server=1&dns-server=0&snmp-server=0&snmp-community=public&nis-server=1&icsa-compat=0&ntp-server=1&timezone=GMT-5&localtime=0)

My Question now is how can i be 100 % sure that my NitixBox is correctly functioning as a NIS server

I have exactly the same problem - ](*,) 

The client works on the nis server - if you run ```
ypserv -p
``` I see the connections from localhost as client.

However no other machine can connect, always the same error :

```
Test 1: domainname
Configured domainname is "nsserver.homenet"

Test 2: ypbind
can't yp_bind: Reason: Domain not bound
```

ypbind -p even says that the server is not responding.

However, ping, http, nfs, samba are all connecting to the server. Iptables flushed. Nothing I can think of can make it work. 

Is NIS broken in debian ?

---

