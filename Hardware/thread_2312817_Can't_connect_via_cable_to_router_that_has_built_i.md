---
title: "Can't connect via cable to router that has built in DHCP server off"
date: 2016-02-07
forum: Hardware
---

### Post by Matias_Palacios on 2016-02-07
Hello all!

let me explain my problem. I have a Netgear Router which it's DHCP server not always works fine. Anyway, I installed ISC-DHCP server in an Ubuntu machine that connects to the Router via cable.

Here are the steps I followed to do it.

I logged in to the Ubuntu computer, made sure it was wired and working, then installed ISC-DHCP-SERVER, then went to the Router admin page, turned off the DHCP server on the router. That worked flawlessly. I tailed the log on the ubuntu machine and saw the DHCP server working just fine.

The problem came when I had to restart the Ubuntu computer (let's say to apply an update). Every time I have to restart the computer, I have to log in to the router's admin page via wifi and turn DHCP back on so the Ubuntu machine can connect via cable. If I don't do that, then I can't connect via cable from the Ubuntu machine and thus, cannot start the DHCP server on that computer. Is worth mentioning that the Ubuntu Machine has only a cable adapter and no wifi.

Now, while I can follow those simple steps every time I need to restart, the rest of the people in my family can't. Do you know if there is a way to avoid having to do this every time I restart?

Thanks!

---

### Post by newbie-user on 2016-02-08
You need to set the Ubuntu server to have a static IP address, otherwise it won't be able to connect to anything. That's probably why you're having problems now.

To set up a static IP address, edit /etc/network/interfaces with your preferred settings. Some example settings are shown below:

```
auto eth0
iface eth0 inet static
     address 192.168.1.2
     netmask 255.255.255.0
     network 192.168.1.0
     gateway 192.168.1.1
     broadcast 192.168.1.255
```

---

### Post by Matias_Palacios on 2016-02-09
unfortunately it didn't work. I used 

```

auto eth0
iface eth0 inet static
     address 192.168.10.22
     netmask 255.255.255.0
     network 192.168.10.0
     gateway 192.168.10.1
     broadcast 192.168.10.255
```

which matches my network configuration.

---

### Post by SeijiSensei on 2016-02-09
What specifically does "it didn't work" mean in this context?

If you run the command "ifconfig" in a terminal, do you see an entry for eth0 with the designated address?

Is eth0 the only active interface on the machine other than localhost?  If not, you may need to change the INTERFACES directive in /etc/default/isc-dhcp-server.

---

### Post by Matias_Palacios on 2016-02-09
Good question. 
Didn't work means "every time I restart my Desktop (ubuntu with ISC-DHCP-SERVER) it does not connect to the router. The IU shows a message that reads 'you are offline'. To solve that I need to log into the server admin page, turn dhcp back on. That connects my Desktop to the router. Then I can safely turn DHCP off again in the router and turn ISC-DHCP-SERVER on again on the desktop"

Is worth noting that I tried adding the startup script to local.rc. I removed it after I couple of reboots with no changes. 

eth0 is the only interface in the machine, yes. And if I run an ifconfig I see the interface with no ip address on it.

Thanks.

---

### Post by SeijiSensei on 2016-02-10
So even after you added the static configuration for eth0 to /etc/network/interfaces, the address isn't assigned at boot?  You shouldn't need any special script to make this happen.  Perhaps it's some bad interaction with the GUI NetworkManager?  Have you tried configuring the interface statically with that tool instead of editing the interfaces file?

Have you read this? [https://help.ubuntu.com/lts/serverguide/network-configuration.html](https://help.ubuntu.com/lts/serverguide/network-configuration.html)

---

