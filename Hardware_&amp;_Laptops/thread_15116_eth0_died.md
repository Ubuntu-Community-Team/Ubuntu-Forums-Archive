---
title: "eth0 died"
date: 2005-02-12
forum: Hardware &amp; Laptops
---

### Post by malegria on 2005-02-12
I've had my Ubuntu installation going for over 3 months now, and just now my ethernet/internet connection died (via my cable modem). I use automatic-DHCP to assign my IP address. My cable modem is fine and the internet connection works in Yoper & WINXP. I've tried to activate via "Network Settings" and it de-activates after I click the box. Any ideas?

---

### Post by kleeman on 2005-02-12
What is the output of "sudo ifconfig"?
Try "sudo ifdown eth0" followed by "sudo ifup eth0" and report the output...

---

### Post by malegria on 2005-02-12
```
julio@ubuntu:~ $ sudo ifconfig
Password:
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2642 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2642 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:243434 (237.7 KiB)  TX bytes:243434 (237.7 KiB)
```

```
julio@ubuntu:~ $ sudo ifdown eth0
ifdown: interface eth0 not configured
```

```
julio@ubuntu:~ $ sudo ifup eth0
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth0 ; No such device.
Internet Systems Consortium DHCP Client V3.0.1rc14
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up eth0.
```

Could I need to reinstall something? I could download something via Yoper/WinXP and then install it in Ubuntu since I have a fat32 partition between them if needed.

---

### Post by lucus on 2005-02-12
ok, i had a similar problem with mine, but it was doing that when i first installed. 
so i am not sure if i can help much...
what i did to fix the problem was go into my 'interfaces' file (/etc/network/interfaces) and change it
this is what it is set up as

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

i couldn't get it to set up through the "networking" icon... i did it manually.
maybe it accidentally got changed...
i do hope this can help you

---

### Post by malegria on 2005-02-13
Well, I just opted to reinstall Ubuntu, which I've already done.

Still, thanks for the help. Next time I'll be patient and just wait.

---

