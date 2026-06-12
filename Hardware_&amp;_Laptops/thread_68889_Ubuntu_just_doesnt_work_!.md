---
title: "Ubuntu just doesnt work ?!"
date: 2005-09-24
forum: Hardware &amp; Laptops
---

### Post by jvictor on 2005-09-24
Hi guys

This is my machine config

AMD 64 3000+
2x 512-M DDR@400MHz(Kingston)
Gigabyte mobo
80G barracuda HDD
VIA/S3 Unichrome pro IGP Display adapter (onboard)
Realtek 8139 (onboard) Lan card
PS2 mouse, K/board

My ordeal started ever since i decided to go for ubuntu

I tried downloading the AMD64 iso from different sites multiple times but none of the ISOs worked. Surprisingly the MD5 sum is ok .. but the isos dont give a clean install.

I ordered for ship-it cds, but havent received them yet.

Finally i got hold of 4.10 x86 (32 bit) and installed it, hoping that i'll upgrade the distro; but X and network doesnt work.

X says cant find device !
I tried using dpkg-reconfigure xserver-xfree86 , but no use.

Coming to Network , the system can communiacte with the adsl router connected via ethernet cable but I cant even ping other sites like google/yahoo; ( i'm able to ping the router , which means eth0 is active).

Any clue how to get these things right ?

Please keep in mind that i have only a bash prompt left to sort out this.

Is it possible to upgrade to 64 bit from 32 bit Warty?

I'm new to ubuntu , so having big probs with the commands also :(

Any help will be appreciated.

---

### Post by jvictor on 2005-09-24
Update: 

I've just modified the XF86Config-4 file and made X to work by specifying a vesa driver @ 16 bits depth. 

Does anyone have any hint on how to get the networking part working ?

I use a Dlink 502-T adsl router. I am able to communicate with the router , and do nslookup, ping the router; but am not able to go beyond the router.

pinging my ISPs DNS server even fails.

---

### Post by mlomker on 2005-09-24
> 
I tried downloading the AMD64 iso from different sites multiple times but none of the ISOs worked. Surprisingly the MD5 sum is ok .. but the isos dont give a clean install.


Hoary or Breezy?

> 
Coming to Network , the system can communiacte with the adsl router connected via ethernet cable but I cant even ping other sites like google/yahoo; ( i'm able to ping the router , which means eth0 is active).


Are you using DHCP or did you put in a static address?  Look at the output of **route -n**.  Do you have a line with a flag of UG?  If not then you could try typing this in with your router's IP address.

```

route add -net default gw xxx.xxx.xxx.xxx

```

> 
Is it possible to upgrade to 64 bit from 32 bit Warty?


I'm not sure...I've never tried that.  I know you could upgrade to one of the newer 32-bit versions by doing a dist-upgrade over the Internet.

---

### Post by jvictor on 2005-09-24
Well, I tried hoary. But the isos dint just work :(

I'm gng to try route add :) .. thanks for ur help.

If it works will try to upgrade to 64 bit ;)

---

### Post by jvictor on 2005-09-24
Yes i just checked route -n the kernel routing table has

192.168.1.0   0.0.0.0           255.255.255.0   U .....................

0.0.0.0           192.168.1.1   0.0.0.0               UG...................



I use DHCP (the router acts as a DHCP server).

---

### Post by mlomker on 2005-09-24
Were you trying to ping by name or number?

**ping 128.101.101.101**

If by name, then check the contents of /etc/resolv.conf for the correct DNS server IP addresses.

---

### Post by jvictor on 2005-09-24
yes, i was pinging by ip add..

/etc/resolv.conf has 192.168.1.1 which is the ip add of my adsl router,
it has an entry 

nameserver 192.168.1.1

no clue why it happens.this is really frustrating   ](*,)

---

### Post by mlomker on 2005-09-24
> no clue why it happens.this is really frustrating   ](*,)

Lots of routers do that...they act as a proxy for your DNS lookup.  That's not really a problem.  If you can't ping by IP then you have a bigger problem.  What is the output of **ifconfig**?  Is your subnet mask correct?  I'm running out of ideas...

---

### Post by Vidar on 2005-09-24
The ISO's should work, try setting your CD-burning software to a really low speed (somthing like 2x or 4x) and burning it again, this usually is the problem (bad cd-r and slobby cd-burner). :)

---

### Post by jvictor on 2005-09-25
Compounding the problem  the ISP guys came and did some stuff. i'm able to ping  google , yahoo etc. but cant connect from Mozilla or do apt get..  how do we get that right ?!!

Well I tried burning at 4x . Its actually a DVD writer, a new Sony DVD RW. So chances of slobby burning are thin.

---

### Post by Pinkydead on 2005-09-27
I had problem with that resolv.conf (it containing the IP address of the router) - it not that I couldn't connect to Mozilla etc or the apt-get it just took so long to resolve the names, that it didn't actually work.

The solution I found was to replace the router's ip address with my ISPs DNS addresses in /etc/resolv.conf

If this works, then there is a script you have to modify in /etc/network somewhere that creates resolv.conf on startup.

---

### Post by mlomker on 2005-09-27
> If this works, then there is a script you have to modify in /etc/network somewhere that creates resolv.conf on startup.

I don't think that's their problem because they can ping by name.  The best way to deal with resolv.conf is to install the **resolvconf** package and then you can add a line in your /etc/network/interfaces to over-ride the DNS settings from DHCP.

---

### Post by Pinkydead on 2005-09-28
The name resolution still works even if the router address is used for DNS, it's just much slower from browser or apt-get, presumably because it has to resolve the ISPs DNS first - result is a time out.

I am looking forward to trying out that resolvconf.

---

