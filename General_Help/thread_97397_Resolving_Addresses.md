---
title: "Resolving Addresses"
date: 2005-11-30
forum: General Help
---

### Post by exiztone on 2005-11-30
My webbrowser is working A-Okay, but I can't seem to resolve addresses through any other programs (even my shell). I've disabled Ipv6. What's going on here?

Here's an example of what I mean:
```
Err http://archive.ubuntu.com hoary Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)

```

It happens with IRC too, and connecting to things via SSH. I can't resolve any domain. :( Any clues?

---

### Post by akudewan on 2005-12-01
That is quite odd...do you have a proxy server running?

Can you give the output of ```
 nslookup www.google.com 
```

---

### Post by akiro.yamamoto on 2005-12-01
Also check that you have an entry in your resolv.conf file:
It should look something like this:

nameserver 256.256.256.01 (well your nameserver will be different)
nameserver 256.256.256.02 (this one too :smile: )

The above numbers are Bogus but it should give you an idea of what it should look like.
One primary DNS server and One secondary...
Regards.
PS...
Check the resolv.conf file after your logged on to the internet..
Just in case it's being set dynamically :smile:

---

### Post by exiztone on 2005-12-01
Hi guys.

Well, when I put  nslookup [www.google.com](www.google.com) I get this.

> 
tim@sakura:~$  nslookup [www.google.com](www.google.com)
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
[www.google.com](www.google.com)  canonical name = [www.l.google.com](www.l.google.com).
Name:   [www.l.google.com](www.l.google.com)
Address: 66.249.85.104
Name:   [www.l.google.com](www.l.google.com)
Address: 66.249.85.99


as in the case of resolv.conf, it has the following line.

> 
nameserver 192.168.1.1


Which is essentially correct because Windows used this. It's the IP to my router, not my ISP's DNS addresses. My router automatically gets them.

It's funny. I tried: ssh norge.freeshell.org
and it just tried connecting for ages with no hope. Then I did your 'nslookup' command to freeshell.org, got the IP, and used: ssh 192.94.73.30 and it connected fine!

I wonder what the problem is. :confused:

---

### Post by exiztone on 2005-12-01
Aha! problems are fixed!
I tried something different. I'm just going to mention what I did so if any other users are having the same trouble, they can do it too.

I use a D-Link router and in Windows I just DHCP automatic method and it worked fine. In Linux, I tried the same and that might be what's wrong.

In Etho0, I used 'static' I put 192.168.1.5 as my computer's IP, 255.255.255.0 as my netmask, 192.168.1.1 as my gateway (my router's IP)

Then, I said OK and went into the DNS tab and put my ISP's DNS servers in there. I clicked okay and voila, everything is a-okay. :)

I hope this helps someone! :KS

---

