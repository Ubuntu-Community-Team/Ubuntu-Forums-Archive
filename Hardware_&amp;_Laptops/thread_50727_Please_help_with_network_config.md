---
title: "Please help with network config"
date: 2005-07-21
forum: Hardware &amp; Laptops
---

### Post by HJB on 2005-07-21
Hi, I installed the server edition of Breezy and I am trying to do a minimal instalation. So far so good but I have a problem.

How do I change the network settings from the command prompt (no GUI yet...).
I have a DHCP setup at home and a fixed ip at work and carry the laptop between the two.

Also how do I use apt-get with a proxy (work)

Thanks in advance
Bye
H

---

### Post by odin on 2005-07-21
For the apt-get thing I had the same problem and I solved it like this:

edit this file with vi or vim:

vi /etc/apt/apt.conf.d/proxy

and then write the following line in that file:

Acquire::http::Proxy "http://your_proxy_IP: proxy_port";

and that should make it work with the repos using http.I am on research  for a solution to the ftp repositories.If I find the solution I'll post it  :grin:


And for the network configuration try to edit /etc/network/interfaces and configure it there.I am not sure about this and probably with the command "ifconfig" you can do something but right now I have a problem with the man pages and cant see it to help you a bit more. ](*,)  hope it is enough so you can start working a bit

---

### Post by anders on 2005-07-21
This might help you. You need to edit the /etc/network/interfaces file. For static ip it should contain something like this
```
iface eth0 inet static
        address 192.168.0.111
        netmask 255.255.255.0
        gateway 192.168.0.1
auto eth0
```
The name of the network interface in this case being eth0 (which it should be in your case aswell if you have only one network interface). /etc/resolv.conf should contain the DNS server ips
```
nameserver xxx.xxx.xxx.xxx
nameserver yyy.yyy.yyy.yyy
```

For dhcp /etc/network/interfaces should contain
```
iface eth0 inet dhcp
auto eth0
```
the dhcp client will update the resolv.conf automatically.

When you have edited the files bring up the interface with
```
sudo ifup eth0

```and take it down with
```
sudo ifdown eth0
```

Here's all you need to know
[http://www.debian.org/doc/manuals/reference/ch-gateway.en.html](http://www.debian.org/doc/manuals/reference/ch-gateway.en.html)

Of course it's much easier to use the network config gui in ubuntu :) I think it also can change between different profiles if you need two sets of configurations.

I don't know about apt-get with proxy.

---

### Post by HJB on 2005-07-21
:) THANK YOU both anders and odin, your advice were spot on.
Everything works now. :)

---

### Post by odin on 2005-07-21
totally welcome.Enjoy it!!! :grin:

---

