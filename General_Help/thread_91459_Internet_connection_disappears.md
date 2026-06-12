---
title: "Internet connection disappears"
date: 2005-11-17
forum: General Help
---

### Post by -aj on 2005-11-17
First of all, I am totally beginner for Ubuntu and Linux things. So, please tell everything in &#8220;beginner mode&#8221;. Thanks.

My setup:
Compaq Armada M700
D-link DWL-650+ (wlan-card)
Ubuntu 5.10

My network:
Router/Firewall D-link DI-614+
Router ip 10.10.10.1.
Every network computer get ip in range 10.10.10.100-10.10.10.110 via dhcp.

Problem:
I installed Ubuntu 5.10 and all works fine couple of days until yesterday problems with internet connection started. Firefox, Opera, Thunderbird, Gaim, Skype and Synaptic can&#8217;t connect to internet.

All connection details looks normal: My computer gets ip from my router and ping works. 

I have searching around Ubuntu forums ant try to find solution to my problem without success. I don&#8217;t have made any changes to my router and my desktop computer with XP works fine.

Here is more information which may be important.

iwconfig

```
aj@pingviini:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+  ESSID:"oj_ap"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:40:05:C9:EF:7E
          Bit Rate=22 Mb/s   Tx-Power=18 dBm   Sensitivity=187/255
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=95/100  Signal level=93/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

ifconfig

```
aj@pingviini:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:D0:59:14:10:BB
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:101848 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101848 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7536588 (7.1 MiB)  TX bytes:7536588 (7.1 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:40:05:CB:AE:D4
          inet addr:10.10.10.101  Bcast:10.10.10.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3502 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1101090 (1.0 MiB)  TX bytes:2669 (2.6 KiB)
          Interrupt:11 Base address:0x4c00

```

ping to my router

```
aj@pingviini:~$ ping -c 6 10.10.10.1
PING 10.10.10.1 (10.10.10.1) 56(84) bytes of data.
64 bytes from 10.10.10.1: icmp_seq=1 ttl=127 time=3.10 ms
64 bytes from 10.10.10.1: icmp_seq=2 ttl=127 time=3.07 ms
64 bytes from 10.10.10.1: icmp_seq=3 ttl=127 time=3.09 ms
64 bytes from 10.10.10.1: icmp_seq=4 ttl=127 time=3.07 ms
64 bytes from 10.10.10.1: icmp_seq=5 ttl=127 time=3.07 ms
64 bytes from 10.10.10.1: icmp_seq=6 ttl=127 time=3.07 ms

--- 10.10.10.1 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 4999ms
rtt min/avg/max/mdev = 3.072/3.082/3.103/0.072 ms
```

ping to google.com

```
aj@pingviini:~$ ping -c 6 www.google.com
PING www.l.google.com (64.233.183.104) 56(84) bytes of data.
64 bytes from 64.233.183.104: icmp_seq=1 ttl=234 time=55.6 ms
64 bytes from 64.233.183.104: icmp_seq=2 ttl=234 time=56.1 ms
64 bytes from 64.233.183.104: icmp_seq=3 ttl=234 time=55.0 ms
64 bytes from 64.233.183.104: icmp_seq=4 ttl=234 time=53.9 ms
64 bytes from 64.233.183.104: icmp_seq=5 ttl=234 time=54.0 ms
64 bytes from 64.233.183.104: icmp_seq=6 ttl=234 time=57.2 ms

--- www.l.google.com ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5004ms
rtt min/avg/max/mdev = 53.986/55.355/57.235/1.149 ms
```

/etc/resolv.conf

```
nameserver 10.10.10.1
```

that is my routers ip

I have also tried to put my internet connection provider DNS to /etc/resolv.conf like this:

```
nameserver 10.10.10.1
nameserver 212.146.30.200
nameserver 212.146.30.201
nameserver 62.240.72.10
```

That didn&#8217;t help.

I also disable IPv6 in Firefox (network.dns.disableIPv6: true) and also in Ubuntu:

in /etc/modprobe.d/aliases I changed this:
 
```
alias net-pf-10 ipv6
``` 

to this

```
alias net-pf-10 off #ipv6
```

And last here are connection details from my desktop computer with XP.

```
Windows IP Configuration

        Host Name . . . . . . . . . . . . : shuttle
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Ethernet NIC
        Physical Address. . . . . . . . . : 00-30-1B-24-13-5F
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 10.10.10.100
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 10.10.10.1
        DHCP Server . . . . . . . . . . . : 10.10.10.1
        DNS Servers . . . . . . . . . . . : 10.10.10.1
        Lease Obtained. . . . . . . . . . : 17. marraskuuta 2005 7:33:46
        Lease Expires . . . . . . . . . . : 24. marraskuuta 2005 7:33:46

```

Now I don&#8217;t know what should I try next. I hope you can understand my problem and someone can help me. 

Thanks in advance!

---

### Post by -aj on 2005-11-17
And I have solved my problem. Problem was in iptables rules which I made by firestarter. I didn't understand that firestarter rules are valid even if program is down. Now everything is ok.

---

### Post by Thunderguy on 2005-11-17
Ah yes, and you'll be happy to know that Firestarter configures your kernel's IpTables so whatever settings you make are running by default so long as your network is up :)

---

