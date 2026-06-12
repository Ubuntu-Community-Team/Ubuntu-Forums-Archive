---
title: "please help!! power outage on upgrade broke my system"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by brallan on 2009-07-02
was upgrading to 9.04 and the power went off while installing the upgrades. The system is broken, but i still can get to a CLI.

I tried sudo dpkg --configure -a

and I get the following error (I'm translating from catalan):

dpkg: analysis error, in the file <</var/lib/dpkg/updates/0068>> near the line 3 of the packet <<libsmbclient>>:
EOF in the value of the field <<Description>> (missing a newline at the end)

what should i do to get dpkg to finish the upgrade?

---

### Post by brallan on 2009-07-02
ok, i was able to reboot using the recovery image and then do the dpkg recovery. the problem is that the files that didn't get properly installed. because of broken dependiencies, its telling me to do an apt-get update. however I have no network. It seems to be that some important network files are broken, because now I have no network, nor mouse. i think i need to reinstall.

---

### Post by papenpj on 2009-07-02
well you could try commenting all of the repositories out and make sure the CD is the only thing allowed.  By no network do you mean it is broken OR it never existed?

what are the results of "ifconfig"

---

### Post by brallan on 2009-07-03
thanks for the reply, papenpj. had to go to bed, so i didn´'t get back right away.

well, it`s odd, ifconfig eth0 shows that the card is still there:

```
eth0   link encap:Ethernet HWaddr 00:07:95:fa:ff:2a
       inet6 addr: fe80::207::95ff:fefa:ff2a/64 Scope:Link
       UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
       RX packets:100 errors:0 dropped:0 overruns:0 frame:0
       TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:14206 (14.2 KB) TX bytes:6282 (6.2 KB)
       Interrupt:11 Base address:0xd400
```

but i am not sure how to manually reconfigure it.

---

### Post by brallan on 2009-07-03
in the end, i just booted the liveCD, recovered the data, and reinstalled. thanks for trying to help. on a fresh install, still had network problems, come to find out the network problem was inside the router, not ubuntu at all, only gave out ip to the first two machines! I think it would've been ok had I just gotten the network up and did sudo apt-get update, sudo apt-get upgrade, dpkg --reconfigure -a, etc.

thanks! this is about the only time I have been forced to reinstall (without breaking the system myself by tinkering), a testament to the wonderful stability of gnu/linux!

---

### Post by papenpj on 2009-07-04
yeah sorry i wasn't able to respond quicker.

if i remember right it is something like 
```

ifconfig eth0 192.168.0.100 255.255.255.0

```
the first number is the ip, the second is the subnet mask which for ALL HOME routers I have dealt with is 255.255.255.0 because you really don't need more than 254 addresses setup.

Or you can manually edit the /etc/network/interfaces
here is my file 

[CODE]

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# Setup for static IP where i map my shares
auto eth0
iface eth0 inet static
        address 192.168.0.55
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.11

## Secondary network interface for backup if connected to a 
#network I don't control or can't run eth0. Also used for   
#sniffing.
auto eth1

---

