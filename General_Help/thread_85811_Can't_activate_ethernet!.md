---
title: "Can't activate ethernet!"
date: 2005-11-03
forum: General Help
---

### Post by TrumpetMan258 on 2005-11-03
I'm having some problems activating my ethernet connection on my laptop and it's getting really annoying!  I go into network settings, go into administrator mode, and try to activate ethernet.  However, the status changes from disabled to enabled for about a second, then goes back to disabled.  I just switched from using Gnome to using KDE a couple of days ago.  The ethernet was working fine until yesterday, then everything went wrong.  Oh, another related problem: most of the time, I can't even go into administrator mode.  I put in the password, but then nothing happens.  Both of these problems started about the same time.  I currently have no wireless access, so this is really getting frustrating!

---

### Post by invalid on 2005-11-03
Try typing this in a terminal, and posting the output:

```

sudo ifconfig eth0
sudo ifup eth0

```

(if you are using eth1 or another, replace as needed)

Cheers,
Cb

---

### Post by TrumpetMan258 on 2005-11-03
Okay, so after doing sudo ifconfig eth0, here's what comes up:
```
Link encap:Ethernet  HWaddr 00:12:3F:0E:F9:01
BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (o.o b)  TX bytes:0 (o.o b)
Interrupt:16
```

After sudo ifup eth0, I get this:
```
/etc/network/interfaces:20: too few parameters for iface line
ifup: couldn't read interfaces file "/etc/network/interfaces"
```

Obviously, that second part is what's causing problems, probably.  So is there something I can do to fix this?

---

### Post by invalid on 2005-11-03
Next step would be to examine the interfaces file. Type the following, and paste the output.

```

cat /etc/network/interfaces

```

Cheers,
Cb

---

### Post by TrumpetMan258 on 2005-11-03
Okay, here's the result:
```
# This file describes the network interfaces available on your system
# and how to activate them.  For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
            script grep
            map eth0

# The primary network interface
iface eth0 inet dhcp



iface wlan0 inet
```

---

### Post by Delvien on 2005-11-05
Do you have your ethernet connection disabled in windows? i find that to be my problem EVERY single time. with wireless as well.

---

### Post by mlomker on 2005-11-06
> Obviously, that second part is what's causing problems, probably.  So is there something I can do to fix this?

It looks like it is up but doesn't have an IP address.

Try **sudo dhclient eth0**

---

### Post by TrumpetMan258 on 2005-11-06
I don't have Windows now, only Kubuntu.  When I did have Windows, this was never a problem.  It always just worked.

---

### Post by TrumpetMan258 on 2005-11-06
Here's what I got from sudo dhclient eth0:
```
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.ort/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:12:3f:0e:f9:01
Sending on   LPF/eth0/00:12:3f:0e:f9:01
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPOFFER from 130.101.94.2
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 130.101.94.2
bound to 130.101.95.146 -- renewal in 6961 seconds.
```

---

### Post by shinygerbil on 2005-11-06
That sounds good to me -  it seems you're connected.

Steve

---

### Post by TrumpetMan258 on 2005-11-06
Well, I'm not.  I'm still having the same problem.  No idea what to do.

---

### Post by mlomker on 2005-11-06
[QUOTE=TrumpetMan258]Well, I'm not.  I'm still having the same problem.  No idea what to do.[/QUOTE]

Can you ping your router?  Can you ping something on the Internet by number?  Can you simply not use Firefox?

After getting your IP address try pinging your router by number, something on the Internet by number, and then something on the Internet by name:

```

mlomker@mlomkernote:/$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.7.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         10.0.7.1        0.0.0.0         UG    0      0        0 eth0
mlomker@mlomkernote:/$ ping 10.0.7.1
PING 10.0.7.1 (10.0.7.1) 56(84) bytes of data.
64 bytes from 10.0.7.1: icmp_seq=1 ttl=64 time=0.895 ms
64 bytes from 10.0.7.1: icmp_seq=2 ttl=64 time=0.902 ms

--- 10.0.7.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.895/0.898/0.902/0.030 ms
mlomker@mlomkernote:/$ ping 128.101.101.101
PING 128.101.101.101 (128.101.101.101) 56(84) bytes of data.
64 bytes from 128.101.101.101: icmp_seq=1 ttl=58 time=16.7 ms
64 bytes from 128.101.101.101: icmp_seq=2 ttl=58 time=8.00 ms

--- 128.101.101.101 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 8.005/12.366/16.727/4.361 ms
mlomker@mlomkernote:/$ ping www.mpr.org
PING www.mpr.org (209.98.65.80) 56(84) bytes of data.
64 bytes from 209.98.65.80: icmp_seq=1 ttl=115 time=41.4 ms
64 bytes from 209.98.65.80: icmp_seq=2 ttl=115 time=26.1 ms
64 bytes from 209.98.65.80: icmp_seq=3 ttl=115 time=27.7 ms

```

---

### Post by TrumpetMan258 on 2005-11-06
Okay, I figured out something.  Whenever I reboot my computer or logout or anything, I have to type "sudo dhclient eth0" in konsole.  That activates my ethernet connection.  That's the only way I can seem to do it.  Like I originally stated in my first post here, I'm having some big difficulties with the network settings program.  Most of the time I'm not able to go into administrator mode, and in the few times I can, I'm not able to activate the connection.  It just goes back to being disabled.  That command in konsole seems to be the only way to get it work.  Any ideas as to why and how I can get the network settings to work?

---

### Post by Qrk on 2005-11-07
This might work.

```
sudo cat /etc/network/interfaces
```

add the line:

auto eth0

to the bottom of it. I've never had your exact problem, so I'm not positive it will do anything.

---

### Post by mlomker on 2005-11-07
> auto eth0

to the bottom of it.

That's exactly right.  You could also add it to the **auto lo** line and just make it **auto lo eth0**

Have you tried going into system settings by typing **kdesu systemsettings** on the Run line or in a terminal?  The 'Administrator' button business is a work in progress.

---

### Post by TrumpetMan258 on 2005-11-07
Thanks.  I'll see if that helps.  I figured that the administrator button just had some problems that need to be worked out.  I guess I can't expect KDE to be 100% perfect.  Oh, well.  At least I have Internet access again!

---

### Post by KittyChunk on 2005-12-05
Hi TrumpetMan,

Had the same problem (and same error) on my freshly installed Breezy cluster management box, running two wired ethernet cards. Damnable thing refused to let me bring either card up from either the GUI, or console using ifup. It seems to be fussing about having a certain number of arguments after the "iface" commands in the /etc/network/interface file. The last two lines of mine looked as follows while I was having the problem:

```
iface eth0 inet dhcp
iface eth1 inet
```

Changing it to this, and making sure lo and eth0 were in the auto line, fixed it:

```
iface eth0 inet dhcp
iface eth1 inet dhcp
```

Apparently it really needs that dhcp/static argument, so if something mangles the interfaces file, it's tickets for the high level network tools. Hope this helps.

---

### Post by Ferri on 2006-03-23
[QUOTE=KittyChunk]
```
iface eth0 inet dhcp
iface eth1 inet dhcp
```

Apparently it really needs that dhcp/static argument, so if something mangles the interfaces file, it's tickets for the high level network tools. Hope this helps.[/QUOTE]
It's been of help for me. Thank you!

---

### Post by Barrakketh on 2006-03-23
[QUOTE=Ferri]It's been of help for me. Thank you![/QUOTE]
Alternatively, if you want a static IP you can use something like this:
```
iface eth0 inet static
address 192.168.254.10
netmask 255.255.255.0
gateway 192.168.254.254
```

There is a manpage for that file, so if you need help with it use "man interfaces"


With that said, holy necropost, Batman!

---

