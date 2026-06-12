---
title: "Starting programs, executing commands on start-up"
date: 2008-11-11
forum: General Help
---

### Post by costre on 2008-11-11
I have two issues I think can be helped by making Ubuntu do stuff during boot-up that I now do by hand after boot-up.

First, my RAID array doesn't mount. The command I enter to do this is 

```
mount /dev/md0 /media/raid
```

Second, I configure my shared internet connection. I found a guide online, I think some of the commands were meant for one-time use only, but I repeat them anyway, the terminal have them cached for easy access :)

The commands are:

```
 echo 1 > /proc/sys/net/ipv4/ip_forward
 dpkg-reconfigure ipmasq
 iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
 ifconfig eth0 192.168.0.1
 /etc/init.d/dnsmasq restart
 /etc/init.d/ipmasq restart 
```

Before I execute these commands, neither my ETH1 (nternet) card, or my ETH0 (LAN) card seem to work properly.. 

Thanks!

---

### Post by tuga on 2008-11-12
For the second issue...
Install firestarter and run the wizard: >firewall>run wizard.
I don't now why but this worked for me.

---

### Post by costre on 2008-11-13
I tried firestarter earlier, didn't seem to work for me. It could be that these commands I had run conflicted somehow. Anyway, this way works great for me, without the "side effects" of firestarter (the firewall, I feel, is bound to cause issues)

It would simply be nice if ubuntu could execute these commands for me :)

---

### Post by iponeverything on 2008-11-13
> **costre said:**
> I have two issues I think can be helped by making Ubuntu do stuff during boot-up that I now do by hand after boot-up.

First, my RAID array doesn't mount. The command I enter to do this is 

```
mount /dev/md0 /media/raid
```

Second, I configure my shared internet connection. I found a guide online, I think some of the commands were meant for one-time use only, but I repeat them anyway, the terminal have them cached for easy access :)

The commands are:

```
 echo 1 > /proc/sys/net/ipv4/ip_forward
 dpkg-reconfigure ipmasq
 iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
 ifconfig eth0 192.168.0.1
 /etc/init.d/dnsmasq restart
 /etc/init.d/ipmasq restart 
```

Before I execute these commands, neither my ETH1 (nternet) card, or my ETH0 (LAN) card seem to work properly.. 

Thanks!

just add them to /etc/rc.local

you can nuke the " dpkg-reconfigure ipmasq" that does not need to be done more than once.

setup eth0 in /etc/network/interfaces

and mount your raid from /etc/fstab

that will pair it down a bit.

---

