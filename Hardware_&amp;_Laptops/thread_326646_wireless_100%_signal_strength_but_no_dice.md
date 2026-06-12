---
title: "wireless 100% signal strength but no dice"
date: 2006-12-27
forum: Hardware &amp; Laptops
---

### Post by poadshaw on 2006-12-27
hi all, love ubuntu!

I was using 6.06 on my laptop, and tried to upgrade to 6.10 screwed up, so i made a live cd of 6.10 and all is well... except wirless is not working.  I have signal strength but cannot ping or visit web pages.

I'm using PRO/Wireless 2200BG Network device.  default driver with 6.10

here's some info I pulled off the terminal:

$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:12:88:D0:1C:E1
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              22 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=96/100  Signal level=-29 dBm  
                    Extra: Last beacon: 1824ms ago

sit0      Interface doesn't support scanning.


$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:A6:2B:F5  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fea6:2bf5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:122997 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:173518359 (165.4 MiB)  TX bytes:5526789 (5.2 MiB)
          Interrupt:177 

eth1      Link encap:Ethernet  HWaddr 00:13:CE:A3:3E:CF  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fea3:3ecf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:883 errors:24 dropped:24 overruns:0 frame:0
          TX packets:103 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:72680 (70.9 KiB)  TX bytes:13416 (13.1 KiB)
          Interrupt:50 Base address:0x2000 Memory:b8006000-b8006fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:270 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26877 (26.2 KiB)  TX bytes:26877 (26.2 KiB)



under General tab in my Connection Properties: eth1 (my wireless connection) I have:
Name: eth1
Status: Idle / Receiving / Sending (switches between these)
Activity
Recieved: 1148 packets (82.5 Kb) (always increasing in value)
Sent: 133 packets (14.1 Kb) (also increasing in value)
Signal Strength (100%)


I am not able to ping anything or visit websites.  If i don't have my essid or my webkey in correctly I get a signal strength of 0%, but then I change it back and it jumps to 100% but still no internet.  ](*,) 

I have been using Linux for 1 month so feel free to explain things as if i'm a 3 year old
Thanks in advance for any suggestions.

---

### Post by Metaljaz on 2006-12-28
Read through the below thread. Maybe there is something in it that can help you.
I had the same problem until i picked up a different pcmcia card and since then
all is good. Lovin Ubuntu


[http://www.ubuntuforums.org/showthread.php?t=308879](http://www.ubuntuforums.org/showthread.php?t=308879)

---

### Post by adamcin on 2006-12-28
Is eth1 set as your default connection?

Also, do you have admin access on the router?

---

### Post by Metaljaz on 2006-12-28
ath0 is my network connection. Here is another site that may be of interest.


[http://www.linuxquestions.org/questions/showthread.php?t=513914](http://www.linuxquestions.org/questions/showthread.php?t=513914)

---

### Post by amo-ej1 on 2006-12-28
Well the first step there is seeing is you can ping your router... When you open a terminal, and run

```

edb@rogue:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

You can get your default gateway. The default destination 0.0.0.0 is routed to the gateway 192.168.1.1  Next you should see if you are able to ping that gateway:

```

edb@rogue:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.24 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.961 ms

```

In the code above you can see the gateway is responding. The next step is seeing if you can ping your nameserver (the computer responsible for translating the hostnames):

```

edb@rogue:~$ cat /etc/resolv.conf 
search home.de-brauwer.be
nameserver 195.130.130.5
nameserver 195.130.130.133

```

Now see with ping if you can reach these adresses. If ping doesn't help, try traceroute and see how far you get.

Please respond with how for you got in this procedure and what error messages you get.

---

### Post by poadshaw on 2006-12-28
AWSOME!

wireless is up and runinning!  Thank you so much, the step-by-step ping info was invaluable, as were the linked tutorials.

The absolute best part of Ubuntu is the community behind it.  Thanks again

---

### Post by poadshaw on 2006-12-28
yes, in 6.06 my wirless was eth0 but now it is eth1... mystery but that's the way it is ??

---

