---
title: "HOWTO: D-Link DSL-G624T with Ubuntu"
date: 2006-09-11
forum: Hardware &amp; Laptops
---

### Post by Jackster on 2006-09-11
I had a lot of problems getting my D-Link DSL-G624T ADSL Router to work with Ubuntu. It took me a while to discover this, but to fix the problem you have to do the following in a terminal:

```

cd /etc/
sudo gedit resolv.conf
*<root password>*
```

Then in the GEdit window replace its contents with:

```

nameserver 208.67.222.222
nameserver 208.67.220.220
```

Then save the file and hopefully you should be online!

---

### Post by Mordred on 2006-12-21
I use the same fix but by using this with DHCP I have to edit that file every half an hour.
I have tried to make this file read only but this seems to be overridden...
Is there a more permanent solution?

Thanks

---

### Post by mark65 on 2007-01-01
Had same problem with system resetting the DHCP Address every few mins.
But I've fixed this with...
Go to Routers web admin page (192.168.1.1 in my case) and to the DHCP button on the Home tab.
Change the DNS mode from auto to manual and enter your ISPs DNS addresses.
This seems to work for me (at the moment!!) and dunno why - all seems like magic. I guess the router is continuously updating ubuntu with the default 192.168.1.1 address but this forces it to tell it our manual address.

Still cant get the wireless stuff working though - only have wired access at the moment!

later...

---

### Post by liamjames91 on 2007-03-02
my netgear router wasnt playing ball, so i went out and got this router (with the dongle which im eventually guna try get working in edgy or may wait for feisty, its detected but i feel probably needs some tinkering!) im having to use windoze to try and work out why i cant get internet in ubuntu wireless or other to work with this pain in the *** router!! at leat the netgear worked well when it did! grrrr, another thing to give me a headache!! haha, ill post back if i find out.:confused:

---

### Post by liamjamesbooth on 2007-03-06
got it working fine on my laptop (ubuntu edgy, intel centrino wireless chipset) but for some reason cannot get it to work on my desktop running dapper using a netgear wg111t wireless adapter working with ndiswrapper, it connected fine to my old wireless router !! :confused:

---

### Post by dudous on 2007-07-22
"I use the same fix but by using this with DHCP I have to edit that file every half an hour.
I have tried to make this file read only but this seems to be overridden...
Is there a more permanent solution?"


I solved this problem with a firmware update.
Here is the firmware that i've used :

[ftp://ftp.dlink.it/Adsl/DSL-G624T/Firmware/V3.00B01T02.EU-A.20060720](ftp://ftp.dlink.it/Adsl/DSL-G624T/Firmware/V3.00B01T02.EU-A.20060720)

---

### Post by mango.muncher on 2007-09-08
> **mark65 said:**
> Had same problem with system resetting the DHCP Address every few mins.
But I've fixed this with...
Go to Routers web admin page (192.168.1.1 in my case) and to the DHCP button on the Home tab.
Change the DNS mode from auto to manual and enter your ISPs DNS addresses.


Thanks Mark, I'm using a D-link 502T, I entered admin page address 10.1.1.1, selected manual and entered ISP ip address, hey presto, no more resetting DNS.

---

### Post by blackdiamond on 2007-09-25
Hi everybody! I have the same problem.. Tomorrow i'll follow your suggest and i hope that it works..

btw I also had done some weeks ago a bug report at:

[https://bugs.launchpad.net/ubuntu/+bug/129264]("https://bugs.launchpad.net/ubuntu/+bug/129264")

so maybe is not a bug..but if you want to give more suggestions here is the link..
thanks and bye from italy

---

### Post by chappell101 on 2007-12-22
If this helps anyone it all works fine including the wireless under hardy heron alpha 2! It just saved me buying a new router!:)

---

