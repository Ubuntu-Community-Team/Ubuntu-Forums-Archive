---
title: "[SOLVED] trouble setting up internet in hardy"
date: 2008-08-16
forum: General Help
---

### Post by jmd9qs on 2008-08-16
hi

i am setting up a friends comp with ubuntu, but when i try to go online, it won't let me. when i set up my comp, it found the internet right away with no trouble, but his won't. he is dual-booting w/vista and the internet works w/MS so i know the router is okay... any suggestions as to what i should try? i am a little new at this, and not sure how to setup networks in linux. any help is appreciated.

---

### Post by Naatan on 2008-08-16
What are the results of executing the following command in the terminal:

ifconfig

---

### Post by jmd9qs on 2008-08-16
here are the results for ifconfig:

sean@sean-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:4c:51:30  
          inet6 addr: fe80::21f:c6ff:fe4c:5130/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294967251 overruns:0 frame:0
          TX packets:0 errors:0 dropped:33 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x8000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1f:c6:4c:51:30  
          inet addr:***.***.4.196  Bcast:***.***.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:220 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1926 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100844 (98.4 KB)  TX bytes:100844 (98.4 KB)

---

### Post by Naatan on 2008-08-16
I'm guessing it's simply not resolving domain names, try doing:

ping [www.google.com](www.google.com)

and give the results for that, as well as the following:

ping 64.233.169.104

Please paste back both results

---

### Post by jmd9qs on 2008-08-16
okay... i am getting results from both pings, but they just keep going. i had to shut down the terminal. here is a sample of one of the pings...


jmd9qs@jmd9qs-desktop:~$ ping 64.233.169.104
PING 64.233.169.104 (64.233.169.104) 56(84) bytes of data.
64 bytes from 64.233.169.104: icmp_seq=1 ttl=240 time=66.3 ms
64 bytes from 64.233.169.104: icmp_seq=2 ttl=240 time=68.2 ms
64 bytes from 64.233.169.104: icmp_seq=3 ttl=240 time=65.2 ms
64 bytes from 64.233.169.104: icmp_seq=4 ttl=240 time=65.3 ms
64 bytes from 64.233.169.104: icmp_seq=5 ttl=240 time=67.3 ms
64 bytes from 64.233.169.104: icmp_seq=6 ttl=240 time=66.4 ms
64 bytes from 64.233.169.104: icmp_seq=7 ttl=240 time=66.4 ms
64 bytes from 64.233.169.104: icmp_seq=8 ttl=240 time=65.5 ms
64 bytes from 64.233.169.104: icmp_seq=9 ttl=240 time=66.6 ms
64 bytes from 64.233.169.104: icmp_seq=10 ttl=240 time=66.6 ms
64 bytes from 64.233.169.104: icmp_seq=11 ttl=240 time=65.7 ms
64 bytes from 64.233.169.104: icmp_seq=12 ttl=240 time=65.6 ms
64 bytes from 64.233.169.104: icmp_seq=13 ttl=240 time=65.8 ms
64 bytes from 64.233.169.104: icmp_seq=14 ttl=240 time=66.8 ms
64 bytes from 64.233.169.104: icmp_seq=15 ttl=240 time=68.9 ms
64 bytes from 64.233.169.104: icmp_seq=16 ttl=240 time=65.9 ms
64 bytes from 64.233.169.104: icmp_seq=17 ttl=240 time=66.0 ms
64 bytes from 64.233.169.104: icmp_seq=18 ttl=240 time=66.1 ms
64 bytes from 64.233.169.104: icmp_seq=19 ttl=240 time=67.1 ms
64 bytes from 64.233.169.104: icmp_seq=20 ttl=240 time=67.2 ms


i'm sorry... i just realized im doing this on the ACTIVE comp... the ifconfig was for the correct one. hold on for the results of ping from the inactive comp

---

### Post by jmd9qs on 2008-08-16
here are the right ping results, but again the ping just kept going, so its not complete:

sean@sean-desktop:~$ ping [www.google.com](www.google.com) 
ping: unknown host [www.google.com](www.google.com)
sean@sean-desktop:~$ ping [http://www.google.com](http://www.google.com)
ping: unknown host [http://www.google.com](http://www.google.com)
sean@sean-desktop:~$ ping 64.223.169.104
PING 64.223.169.104 (64.223.169.104) 56(84) bytes of data.
From ***.***.4.196 icmp_seq=1 Destination Host Unreachable
From ***.***.4.196 icmp_seq=2 Destination Host Unreachable
From ***.***.4.196 icmp_seq=3 Destination Host Unreachable
From ***.***.4.196 icmp_seq=4 Destination Host Unreachable
From ***.***.4.196 icmp_seq=5 Destination Host Unreachable
From ***.***.4.196 icmp_seq=6 Destination Host Unreachable
From ***.***.4.196 icmp_seq=7 Destination Host Unreachable
From ***.***.4.196 icmp_seq=8 Destination Host Unreachable
From ***.***.4.196 icmp_seq=9 Destination Host Unreachable

---

### Post by Naatan on 2008-08-16
Sorry I assumed you knew how to end a running process from the terminal, in this case you could have simply pressed ctrl+c.

It's easy to solve your problem, you have to use custom dns server settings, in your terminal type:

```
sudo cp /etc/resolv.conf /etc/resolv.conf.auto
```

Then type the following

```
sudo vim /etc/dhcp3/dhclient.conf
```

Look for the following line:

```
#prepend domain-name-servers 127.0.0.1;
```

Add the following underneath:

```
prepend domain-name-servers 192.168.0.1;
```

This is assuming that your router has the ip 192.168.0.1, if your router uses a different ip, use that ip instead.

Alternatively you can use the OpenDNS ip's, like so

```
prepend domain-name-servers 208.67.222.222, 208.67.220.220;
```

After that restart your networking service

```
sudo /etc/init.d/networking restart
```

And that's it.

---

### Post by jmd9qs on 2008-08-16
i did that with no success (and after learning quite a bit about vim, i might add). ping results showed 100% packet loss and ifconfig hasn't changed... is there anything else that might be wrong?

---

### Post by Naatan on 2008-08-16
Are you sure you followed my steps correctly? Can you show the contents of 

/etc/dhcp3/dhclient.conf

You can also try editing the following file

/etc/resolv.conf

and entering the following:

nameserver 192.168.0.1

That's it, if you feel more comfortable using gedit you can just replace vim with gedit in the commands I gave you.

---

### Post by jmd9qs on 2008-08-17
this is the output of the file requested:

Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
#prepend domain-name-servers 192.168.2.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}



my router ip is 192.168.2.1

---

### Post by Naatan on 2008-08-17
Your line is commented thus it won't be ran, replace the following line

#prepend domain-name-servers 192.168.2.1;

with:

prepend domain-name-servers 192.168.2.1;

So basically.. remove the "#" symbol at the start.

---

### Post by jmd9qs on 2008-08-17
thank you, that fixed it... i noticed that there was no # in front of prepend; thought it was a typo. sorry for assuming, but i appreciate your help.

---

