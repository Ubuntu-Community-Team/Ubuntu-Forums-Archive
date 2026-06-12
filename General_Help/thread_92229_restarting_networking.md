---
title: "restarting networking"
date: 2005-11-19
forum: General Help
---

### Post by monkblah on 2005-11-19
Hi, I use ubuntu 5.10... sometimes I need to unplug my computer from one network and plug it into another. I want to then restart networking to connect to the new network, get an ip address, etc.  I do this:

sudo /etc/init.d/networking restart

but it doesn't seem to work, and I must reboot to get networking to start.  

How can I restart networking without rebooting?

Help appreciated, thank you.

---

### Post by adwait on 2005-11-19
What do you mean it doesn't seem to work? Does it give an erros?Have you tried
```
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start
```

Its essentially the same thing.....but might as well try it.

---

### Post by Quirky on 2005-11-19
I have a similar problem - if my wireless router isn't switched on *before* booting ubuntu, the network won't come up using /etc/init.d/networking stop|start|restart after booting. It seems to create a duff network interface on boot up (no IP address, empty SSID, no encryption, etc) that semi-breaks the networking script. I then have to manually set the interface to down with ifconfig followed by the various steps from /etc/network/interfaces. But that is for wireless, which as we all know can be a bit rough around the edges in ubuntu.

What happens if you *ifconfig down* the interface before reconfiguring the newtork? ifdown might work too.

---

### Post by monkblah on 2005-11-22
Hi, thanks for the replies. To be more specific about my experience: when I boot my computer, my interface eth0 gets connected to my network, assigned an IP address, and works fine. If I do
```

sudo ifconfig eth0 down
sudo ifconfig eth0 up

```
...the network interface goes down and back up without a problem.

However, if I attempt to restart networking services, either by
```

sudo /etc/init.d/networking restart

```
or
```

sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start
```

... then my network interface does not connect successfully to the network unless I reboot. Doing an 'ifconfig eth0 up' following the networking restart doesn't help either.

Here are the messages I get:

```

$ sudo ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:48:56:42:57:12
          inet addr:192.146.0.50  Bcast:192.146.0.255  Mask:255.255.255.0
          inet6 addr: fe80::248:54ff:ee4e:53f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:412946 errors:0 dropped:0 overruns:0 frame:0
          TX packets:287979 errors:0 dropped:0 overruns:0 carrier:0
          collisions:3703 txqueuelen:1000
          RX bytes:316081443 (301.4 MiB)  TX bytes:59933843 (57.1 MiB)
          Interrupt:5 Base address:0xa400

$ sudo /etc/init.d/networking stop
 * Deconfiguring network interfaces...                                   [ ok ]
$ sudo /etc/init.d/networking start
 * Configuring network interfaces...                                     [ ok ]
$ sudo ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:48:56:42:57:12
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:412952 errors:0 dropped:0 overruns:0 frame:0
          TX packets:287980 errors:0 dropped:0 overruns:0 carrier:0
          collisions:3703 txqueuelen:1000
          RX bytes:316081803 (301.4 MiB)  TX bytes:59934185 (57.1 MiB)
          Interrupt:5 Base address:0xa400
$ sudo ifconfig eth0 up
$ sudo ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:48:56:42:57:12
          inet6 addr: fe80::248:54ff:ee4e:53f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:412952 errors:0 dropped:0 overruns:0 frame:0
          TX packets:287983 errors:0 dropped:0 overruns:0 carrier:0
          collisions:3703 txqueuelen:1000
          RX bytes:316081803 (301.4 MiB)  TX bytes:59934423 (57.1 MiB)
          Interrupt:5 Base address:0xa400
$

```

It seems like I get an IP address when I boot, but not when I restart networking. any idea why this would be so?

---

### Post by dubz on 2005-11-22
No idea,but in order to give yourself an ip address again just type

sudo ifconfig eth0 192.146.0.50     --mine.
Thats the ssimplest way,and thats why i love networking in Linux.

---

### Post by YoG%*@ on 2005-11-22
[QUOTE=monkblah]
It seems like I get an IP address when I boot, but not when I restart networking. any idea why this would be so?[/QUOTE]

Think you're right there. If you receive your IP through DHCP try 
```
sudo dhclient ethX
```
which should get you one. (ethX should be your ethernet device, so in your case eth0 i guess).

hth, mux

---

### Post by mättu on 2005-12-19
I have the same problem.
The weird thing is that the same machine set up with a "normal" debian restarts the network properly.
Does ubuntu use a different networking-script?

---

### Post by maglis on 2005-12-19
It would be interesting to see /etc/network/interfaces file. That is the place that holds information about your network interfaces and how, when and by what process they should be activated.

---

### Post by monkblah on 2005-12-19
I think I may have solved my problem, sort of.

First, in my /etc/network/interfaces file, I found that my eth0 interface was being controlled by hotplug. I couldn't really figure out how that worked, so I commented out the hotplug section:

```

#mapping hotplug
#       script grep
#       map eth0

```

Now, when I plug into a different network, I do this:

```

sudo ifconfig eth0 down
   [ now plug into new network]
sudo ifconfig eth0 up
pump -i eth0

```

This doesn't totally solve my problem, because for another computer I would like to continue to use hotplug to manage the ethernet interface, but I don't really understand how the mapping system works (the man pages don't help, can't find any comprehensible documentation & no one on the forums seems to know). And I dont undertand why runnint the init.d/networking script with restart doesn't work correctly. But at least this helps a bit for my desktop computer, I don't need to reboot when I switch networks.

---

### Post by maglis on 2005-12-20
First of all, please read manual for interfaces (man interfaces).

[quote=monkblah]First, in my /etc/network/interfaces file, I found that my eth0 interface was being controlled by hotplug. I couldn't really figure out how that worked, so I commented out the hotplug section:
[/quote] You shouldn't have. Network hotplug feature does what it says: it brings interfaces up/down on hotplugging on/off the link. This should be all you needed. When you pull out the link, hotplug subsystem detects that an interface (/etc/interfaces) it monitors is off and deconfigures it. When the link is up it reconfigures it. If the interface is getting ip address from a dhcp server then it successfully does that.
[quote=monkblah]
Now, when I plug into a different network, I do this:

```

sudo ifconfig eth0 down
   [ now plug into new network]
sudo ifconfig eth0 up
pump -i eth0

``` 
[/quote] 
you could manually bring up/down any interface at any time by doing 
```

sudo ifup eth0
sudo ifdown eth0

```

---

### Post by mättu on 2005-12-20
[QUOTE=maglis] When the link is up it reconfigures it. If the interface is getting ip address from a dhcp server then it successfully does that.
[/QUOTE]
Obviously not (in all cases). Or we would not be posting here. ;-)

---

### Post by tuxy on 2005-12-20
[QUOTE=monkblah]Hi, I use ubuntu 5.10... sometimes I need to unplug my computer from one network and plug it into another. I want to then restart networking to connect to the new network, get an ip address, etc.  I do this:

sudo /etc/init.d/networking restart

but it doesn't seem to work, and I must reboot to get networking to start.  

How can I restart networking without rebooting?

Help appreciated, thank you.[/QUOTE]

You are missing the "."(dot) and "/"(slash) when you are executing the command.
You have to type in  :
/etc/init.d/./networking restart **not** /etc/init.d/networking restart

---

### Post by alamba on 2005-12-20
Do you have the same problem when activating and deactivating an interface with system>admin>networking?

Akshay

---

### Post by maglis on 2005-12-20
[quote=mättu]Obviously not (in all cases). Or we would not be posting here. ;-)[/quote]

True, but I had to explain the norm for I did not know what you were doing in detail. 

When you unplug the first connection and then plug the second, THEN do ifdown/ifup. Do you get an IP address? If not do you get the same problem when you return to the first network? If you get the problem only on one network, then you should look at the behaviour of dhcp server and/or client.

---

