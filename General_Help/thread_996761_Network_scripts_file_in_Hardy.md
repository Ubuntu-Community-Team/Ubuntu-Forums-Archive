---
title: "Network scripts file in Hardy?"
date: 2008-11-29
forum: General Help
---

### Post by gvanto on 2008-11-29
I'm reading a tutorial on networking in Linux and they're talking about
network configuration files located at: /etc/sysconfig/network-scripts (where  the IP address, wehther DHCP should be used, etc is configured). Looks like this in the tut:

> 

Changing Your IP Address
 If you wanted, you could give this eth0 interface an IP address using the ifconfig command.
    [root@bigboy tmp]# ifconfig eth0 10.0.0.1 netmask 255.255.255.0 up
 The "up" at the end of the command activates the interface. To make this permanent each time you
 boot up you'll have to add this command in your /etc/rc.local file which is run at the end of
 every reboot.
 Fedora Linux also makes life a little easier with interface configuration files located in the
 /etc/sysconfig/network-scripts directory. Interface eth0 has a file called ifcfg-eth0,
 eth1 uses ifcfg-eth1, and so on. You can place your IP address information in these files,
 which are then used to auto-configure your NICs when Linux boots. See Figure 3-1 for two samples
 of interface eth0. One assumes the interface has a fixed IP address, and the other assumes it
 requires an IP address assignment using DHCP.

                                                     29
                          Figure 3-1 File formats for network-scripts
                                              Fixed IP Address
                   [root@bigboy tmp]# cd /etc/sysconfig/network-scripts
                   [root@bigboy network-scripts]# less ifcfg-eth0
                   DEVICE=eth0
                   IPADDR=192.168.1.100
                   NETMASK=255.255.255.0
                   BOOTPROTO=static
                   ONBOOT=yes
                   #
                   # The following settings are optional
                   #
                   BROADCAST=192.168.1.255
                   NETWORK=192.168.1.0
                   [root@bigboy network-scripts]#
                                    Getting the IP Address Using DHCP
                   [root@bigboy tmp]# cd /etc/sysconfig/network-scripts
                   [root@bigboy network-scripts]# less ifcfg-eth0
                   DEVICE=eth0
                   BOOTPROTO=dhcp
                   ONBOOT=yes
                   [root@bigboy network-scripts]#
     As you can see eth0 will be activated on booting, because the parameter ONBOOT has the value
     yes and not no. You can read more about netmasks and DHCP in Chapter 2, "Introduction to
     Networking".
     The default RedHat/Fedora installation will include the broadcast and network options in the
     network-scripts file. These are optional.
     After you change the values in the configuration files for the NIC you have to deactivate and
     activate it for the modifications to take effect. The ifdown and ifup commands can be used to do
     this:
       [root@bigboy network-scripts]# ifdown eth0
       [root@bigboy network-scripts]# ifup eth0
     Your server will have to have a default gateway for it to be able to communicate with the Internet.
     This will be covered later in the chapter.





Only problem is, I'm not using the same linux version (hardy) as they are (fedora), so I'm wondering where this equivalent file would be located under Hardy?

Help much appreciated,
Gerry
networking newbie

---

### Post by jgoguen on 2008-11-29
The equivalent file is /etc/network/interfaces/  Unlike Fedora (and all other Red Hat-based distros) Ubuntu (and Debian derivatives) configure all interfaces in the same file.  The syntax is much different, nothing at all like the tutorial you're looking at.  Enter this command at a terminal to see the manual for the interfaces file:
```
man 5 interfaces
```

If you're not sure about something it's telling you, or if you need clarification, feel free to post more questions and someone will help you out. :)

---

### Post by gvanto on 2008-11-30
Hey thanks alot jgoguen.

my interfaces file looks like this:

> pacific@mainbox:/etc/network$ cat interfaces
auto lo
iface lo inet loopback


I have found the page: [https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html)

but nowhere is anything mentioned about 'lo', any ideas as to what this means?

I am trying to figure out how to configure my network so I have static internal addresses. If someone knows of a handy tutorial for how to set this up in Hardy, would be so awesome.

Many thanks for the help so far,
Gerry
networking newbie

---

### Post by jgoguen on 2008-11-30
The 'lo' interface is your loopback address.  It's what replies when you access "localhost", "127.0.0.1", and other addresses that point to localhost (basically 127.anything).  You definitely want to leave those lines just as they are :)

You can easily use the interfaces file to set up static addresses.  Simply add a block similar to this to the end of the file.
> auto eth0
iface eth0 inet static
[INDENT]       pre-up /sbin/iptables-restore -c < /etc/iptables.rules
post-down /sbin/iptables-save -c > /etc/iptables.rules
address 10.202.149.50
netmask 255.255.252.0
broadcast 10.202.148.255
gateway 10.202.148.1
[/INDENT]

Watch for line breaks, there should be no blank lines in that block.  Let's look at this line-by-line now.
> auto eth0This line marks eth0 as an interface to be brought up at boot time or whenever **ifup -a** is run.  This also allows running the commands **ifup eth0** to bring up only eth0, or **ifdown eth0** to bring down only eth0.

> iface eth0 inet static
This specifies that the interface eth0 (iface eth0) uses IPv4 (inet) and will be configured statically (static).

> pre-up /sbin/iptables-restore -c < /etc/iptables.rules
Before bringing up the interface, restore iptables rules.  This is optional, it's just something I do and include in my examples because someone is going to wonder how to do it :)

> post-down /sbin/iptables-save -c > /etc/iptables.rules
After bringing the interface down, save iptables rules so they can be restored later.  Again, this is optional, but if you save and restore iptables rules using this method then you'll need both of these lines.

> address 10.202.149.50
Assign the address 10.202.149.50 to eth0.

> netmask 255.255.252.0
Set the subnet mask to 255.255.252.0.  This is the equivalent of the /22 CIDR.

> broadcast 10.202.148.255[quote]
Use 10.202.148.255 to send broadcast messages to the whole subnet.

[quote]gateway 10.202.148.1
Use 10.202.148.1 as the default gateway.

Similar blocks will set up other interfaces for you.  If anything here isn't clear, just ask and I'll try to clear it up for you.

---

### Post by gvanto on 2008-12-01
thanks alot, much much appreciated!

gonna do bit more reading, then attempt to apply these principles ...

---

