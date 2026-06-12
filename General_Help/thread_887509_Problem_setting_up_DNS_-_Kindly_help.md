---
title: "Problem setting up DNS - Kindly help"
date: 2008-08-12
forum: General Help
---

### Post by Avinash.Rao on 2008-08-12
Hello all,

I am trying to setup DNS server for my intranet and below is the error and configuration. Studio is my server name and the IP address is 10.10.10.4. I am wondering if the file names and the entries are correct. I also a wins server, how can i configure DNS to get the hostnames from the WINS server instead of adding them manually?

Contents of /etc/network/interfaces
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
address 10.10.10.4
netmask 255.255.255.0
network 10.10.10.0
broadcast 10.10.10.255

Contents of /etc/hosts

127.0.0.1 localhost.localdomain localhost

10.10.10.4 studio.abc.org studio
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Contents of /etc/default/bind9

OPTIONS="-u bind -t /var/lib/named"
# Set RESOLVCONF=no to not run resolvconf
RESOLVCONF=yes

Contents of /etc/bind/named.conf

zone "abc.org" {
type master;
file "/etc/bind/zones/abc.org.db";
};

zone "10.10.10.in-addr.arpa" {
type master;
file "/etc/bind/zones/rev.10.10.10.in-addr.arpa";
};

key "rndc-key" {
algorithm hmac-md5;
secret "9WNiBNj5fFyBWUxfR88nAQ==";
};

controls {
inet 127.0.0.1 port 953
allow { 127.0.0.1; } keys { "rndc-key"; };
};

Contents of /etc/bind/named.conf.options. I don't have any other DNS servers in my network so i have commented all the entries except below.

forwarders {
123.123.123.123;
};

Contents of /etc/bind/zones/rev.10.10.10.in-addr.arpa

@ IN SOA studio.abc.org. root (
2006081401;
28800;
604800;
604800;
86400
)
IN NS studio.abc.org.
4 IN PTR abc.org

Contents of /etc/bind/zones/abc.org.db

abc.org. IN SOA studio.abc.org. root (

// Do not modify the following lines!
2006081401
28800
3600
604800
38400
)

// Replace the following line as necessary:
// ns1 = DNS Server name
// mta = mail server name
// example.com = domain name

abc.org. IN NS studio.abc.org.
//abc.org. IN MX 10 mta.abc.org. - Dont have a mail server

// Replace the IP address with the right IP addresses.
studio IN A 10.10.10.4


/etc/init.d/bind9 restart

root@studio:/etc/bind# /etc/init.d/bind9 restart
* Stopping domain name service... bind rndc: connect failed: 127.0.0.1#953: connection refused
[fail]
* Starting domain name service... bind usage: named [-4|-6] [-c conffile] [-d debuglevel] [-f|-g] [-n number_of_cpus]
[-p port] [-s] [-t chrootdir] [-u username]
[-m {usage|trace|record|size|mctx}]
named: extra command line arguments
[fail]

---

### Post by hyper_ch on 2008-08-12
[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

[http://www.howtoforge.com/installing-an-ubuntu8.04-dns-server-with-bind](http://www.howtoforge.com/installing-an-ubuntu8.04-dns-server-with-bind)

---

### Post by Avinash.Rao on 2008-08-12
Sorry, forgot to mention that, the /etc/resolv.conf file has the following entries

search abc.org
nameserver 10.10.10.4

---

### Post by Avinash.Rao on 2008-08-12
I configured DNS after reading the docs from the link you mentioned.


> **hyper_ch said:**
> [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

[http://www.howtoforge.com/installing-an-ubuntu8.04-dns-server-with-bind](http://www.howtoforge.com/installing-an-ubuntu8.04-dns-server-with-bind)

---

### Post by Avinash.Rao on 2008-08-12
I made a few changes and updated the configuration as above. I have edited the post instead of posting the whole cfg file again.

---

### Post by Avinash.Rao on 2008-08-13
I don't have any firewall configured in my network. I am setting up this DNS Server for my intranet. I have a squid proxy server running to access the internet and i have not configured firewall. I have a DHCP server running on another Linux Server that runs Squid and LTSP. Do you see any problem with this.

---

### Post by Avinash.Rao on 2008-08-14
Hi Everybody,

I have a domain name "abcd.org" registered on the internet, website managed by an ISP and its working fine. I am planning to have an Intranet site for the students for which i am configuring DNS, can i create a domain say for example, "students.abcd.org" which would be accessible only inside the office? Coz, all the machines have access to the internet so will there be a conflict? The students should be able to access the site using their web browser through the url, [http://students.abcd.org](http://students.abcd.org)!

Kindly help as this is very crucial.

---

