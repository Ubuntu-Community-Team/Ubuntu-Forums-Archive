---
title: "Hostname error"
date: 2005-11-29
forum: General Help
---

### Post by Insane on 2005-11-29
I dont even know what this is. I JUST installed ubuntu, and when it asked me for a hostname in the installation, I just kept the default, which was ubuntu

Now, when I log in, it tells me that It cannot connect to the hostname or something like that and that I must change ubuntu (which i set as the hostname) and it tells me that gnome might not function correctly.

So, I am limited to opening only a few aaplications.

The hostname file is in /etc/hostname.txt or whatever the extension is. I tried to edit the file...since it only contains one word, ubuntu. But, it is read only.

How do I fix this? :'(

---

### Post by Insane on 2005-11-29
**Here are the complete file contents of related files...but they have nothign to do with the price of eggs:**

/etc/hosts

```
127.0.0.1	localhost.localdomain	localhost	localhost

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

/etc/hosts.conf

```
order hosts,bind
multi on
```

/etc/hostname

```
ubuntu
```
--------------------------------
**I have tried everything. doing this:**

```
ifconfig
```

**which gives me this:**

```
eth0      Link encap:Ethernet  HWaddr 00:11:09:96:1E:64
          inet addr:10.0.0.9  Bcast:255.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::211:9ff:fe96:1e64/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2438 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2059 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2357519 (2.2 MiB)  TX bytes:302245 (295.1 KiB)
          Interrupt:20 Base address:0xae00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9556 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9556 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:862777 (842.5 KiB)  TX bytes:862777 (842.5 KiB)

```

**and I read in a similar thread that I must check the contents of etc/nsswitch.conf which is**

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```
[B]
And if I try to sudo anything, I get:[/B]

```
sudo: unable to lookup ubuntu via gethostbyname()
```

---

### Post by Insane on 2005-11-29
I restarted and I found the exact message displayd. Here is is:

Could not load up address for ubuntu. This will prevent GNOME from operating correctly. It may be possible to correct the problem by adding ubuntu to the file /etc/hosts.

---

### Post by pheitman on 2005-11-29
I believe that if you edit /etc/hosts with

sudo nano /etc/hosts

and add ubuntu to the end of the line with 127.0.0.1 on it, that it will fix your problem.

Peter

---

### Post by Insane on 2005-11-29
I could....but I can't sudo....if I do that then I get:

```
andre@ubuntu:~$ sudo nano /etc/hosts
sudo: unable to lookup ubuntu via gethostbyname()

```

---

