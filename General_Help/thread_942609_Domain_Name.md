---
title: "Domain Name"
date: 2008-10-09
forum: General Help
---

### Post by bgblanch on 2008-10-09
I want to assign my domain name so that when I connect to a computer on the network at work I don't have to completely qualify the server name.

currently
i.e. telnet <server>.mycompany.com

would like
i.e. telnet <server>


My hostname contains the following:

<computer name> (not fully qualified with domain)

My /etc/hosts contains the following:

127.0.0.1       <computer name>        localhost.localdomain   localhost
::1       <computer name>.mycompany.com <computer name> localhost.localdomain localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


Thank you in advance for your help.

---

### Post by bodhi.zazen on 2008-10-09
First you should probably consider changing to something more secure such as ssh :twisted:

Second, just add a line to /etc/hosts

ip_address  server_name

---

### Post by bgblanch on 2008-10-09
> **bodhi.zazen said:**
> 

Second, just add a line to /etc/hosts

ip_address  server_name

Thank you for your reply.  I already have a line in the /etc/hosts with the domain name.

::1 mycomputer.mycompany.com mycomputer localhost.localdomain localhost

Shouldn't the above give my computer a fully qualified name of mycomputer.mycompany.com?

---

### Post by bodhi.zazen on 2008-10-09
You do not need a FQDN on a LAN.

You should probably put your server name on a line with the IP address (usually local host is on 127.0.0.1 or 127.0.1.1).

---

### Post by bgblanch on 2008-10-09
What I want to be able to do is just type the server name without the domain when telneting to a server on the network.  What I have to do now is "telnet servername.mycompany.com".  What I'd like to be able to do is just type  "telnet servername".

---

### Post by fragos on 2008-10-09
You coulds use a simple shell script called telnetme.

#!/bin/bash
telnet $1.domain.com

Run it as in "telnetme server"

If your server is on a LAN with your client PC you can do "telnet hostname.local".

---

### Post by Iowan on 2008-10-09
> **bgblanch said:**
> ::1 mycomputer.mycompany.com mycomputer localhost.localdomain localhostLooks like IPv6 address - your company using IPv6? (or, maybe I'm confused... again)

---

### Post by 0xD4 on 2009-06-19
I did :
```
apt-file search resolv.conf
```
and saw there is a resolvconf package.

After installing it and looking in its documentation, I can say the fix is, as root :
```
apt-get install resolvconf
echo search mycompany.com >/etc/resolvconf/resolv.conf.d/tail
```

I you have a subdomain, the last line above becomes :
```
printf "search %s\n" mycompany.com subdomain.mycompany.com >/etc/resolvconf/resolv.conf.d/tail
```

I hope this helps.

---

