---
title: "Replaced Motherboard, Ethernet doesn't work"
date: 2005-08-02
forum: Hardware &amp; Laptops
---

### Post by Harokey on 2005-08-02
My old motherboard on my secondary (linux Ubuntu) machine went out and I have just replaced it. Everything went well, and linux boots up, however there is no network now.

I replaced with a motherboard with the same chipset, but it looks like it has a slightly differnt ethernet chip.

The Oldmother board was an Epox 8rda+, and the new motherboard is a chaintech 7NJL6.

From doing some quick googleing, I've found that the old motherboard had a Realtek RTL8201 PHY chip, while the new motherboard has a Realtek RTL8101L chip.

Any help on getting networking working again would be great!

---

### Post by heimo on 2005-08-02
```

sudo modprobe 8139too

``` 
Does it load?

---

### Post by Harokey on 2005-08-02
[QUOTE=heimo]```

sudo modprobe 8139too

``` 
Does it load?[/QUOTE]

It doesn't say anything when I do that. 

But it doesn't give me an error message.

---

### Post by heimo on 2005-08-02
[QUOTE=Harokey]It doesn't say anything when I do that. 

But it doesn't give me an error message.[/QUOTE]

That's how it should work. You can run ifconfig to check that your eth0 is there. If that's true, add the module to /etc/modules so it gets loaded automaticly during boot, configure network (System->Administration->Networking) and you're set.

---

### Post by Harokey on 2005-08-02
[QUOTE=heimo]That's how it should work. You can run ifconfig to check that your eth0 is there. If that's true, add the module to /etc/modules so it gets loaded automaticly during boot, configure network (System->Administration->Networking) and you're set.[/QUOTE]

ifconfig shows eth0, but not with an ip address. 

This was its behaviour before the modprobe.

---

### Post by heimo on 2005-08-02
[QUOTE=Harokey]ifconfig shows eth0, but not with an ip address. 

This was its behaviour before the modprobe.[/QUOTE]

Well, you need to configure IP address using System->Administration->Networking or editing /etc/network/interfaces

---

### Post by Harokey on 2005-08-02
[QUOTE=heimo]Well, you need to configure IP address using System->Administration->Networking or editing /etc/network/interfaces[/QUOTE]


It should be getting dhcp, and it is not.

Line on /etc/network/interfaces
```

iface eth0 inet dhcp
```

---

### Post by heimo on 2005-08-02
[QUOTE=Harokey]It should be getting dhcp, and it is not.

Line on /etc/network/interfaces

iface eth0 inet dhcp[/QUOTE]

Oh, sorry - was just going to add that "unless you use DHCP". You can either try restarting networking or running dhclient manually.
 ```

sudo /etc/init.d/networking restart

or 

sudo dhclient

```

---

### Post by Harokey on 2005-08-02
[QUOTE=heimo]Oh, sorry - was just going to add that "unless you use DHCP". You can either try restarting networking or running dhclient manually.
 ```

sudo /etc/init.d/networking restart

or 

sudo dhclient

```[/QUOTE]

restarting networkign made my eth0 disappear. 

runnding dhclient gave an output similar to this (i'm typing it )

```

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on LPF/sit0/
.
.
.

```

Edit:
Oh and now I have 3 interfaces. eth0 lo and sit0.

---

### Post by heimo on 2005-08-02
Oh.. :-\ :-/
 ```

sudo /etc/init.d/networking stop
sudo rmmod 8139too
lsmod | grep 8139too
sudo modprobe 8139too
sudo /etc/init.d/networking start
ifconfig | grep eth0
sudo dhclient eth0
ifconfig eth0

```

---

### Post by heimo on 2005-08-02
[QUOTE=Harokey]
Edit:
Oh and now I have 3 interfaces. eth0 lo and sit0.[/QUOTE]

That's how it's supposed to be. That looks good.

---

