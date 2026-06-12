---
title: "wireless connection is...very slow!"
date: 2005-11-16
forum: General Help
---

### Post by WGH on 2005-11-16
Hi! After I had this problem ([http://www.ubuntuforums.org/showthread.php?p=481500#post481500)](http://www.ubuntuforums.org/showthread.php?p=481500#post481500)), my Wirelss Connection became very slow...Before that, opening internet pages was very fast: what's happened?

What I could do to resolve this problem?!
Thank's to all...

WGH...

---

### Post by Sloth on 2005-11-16
Maybe you have a bad DNS setting and that is timing out before moving to the next DNS server?  Look in network/domain name system and verify that those DNS servers are correct.

---

### Post by WGH on 2005-11-16
I have got:
- one ADSL router (192.168.0.1 - Server DHCP);
- one PC Winzoz (192.168.0.2 - static IP);
- one Access Point (192.168.0.50 - static IP);
- one PC Linux Kubuntu (dynamic IP).

PC Linux uses a wireless connection 'cause it was difficult to connect with a net-cable.

My DNS Server should be the router, isn't it?
So, in network/domain I should have as DNS server 192.168.0.1, is this right?

Thanks a lot,
WGH...

---

### Post by Sloth on 2005-11-16
Sounds right.  To verify that it's not a dns problem, run nslookup and type the name of a server you are trying to reach at the nslookup command line.  See how long it takes and if the responding server matches the first one in your DNS settings in system settings.  Here's example output from my machine:

> [www.news.com](www.news.com)
Server:         192.168.2.1
Address:        192.168.2.1#53

Non-authoritative answer:
[www.news.com](www.news.com)    canonical name = c10-sha-redirect-lb.cnet.com.
Name:   c10-sha-redirect-lb.cnet.com
Address: 216.239.115.148
> q
Server:         192.168.2.1
Address:        192.168.2.1#53

---

### Post by Maverick911 on 2005-11-16
[QUOTE=Sloth]Sounds right.  To verify that it's not a dns problem, run nslookup and type the name of a server you are trying to reach at the nslookup command line.  See how long it takes and if the responding server matches the first one in your DNS settings in system settings.  Here's example output from my machine:

> [www.news.com](www.news.com)
Server:         192.168.2.1
Address:        192.168.2.1#53

Non-authoritative answer:
[www.news.com](www.news.com)    canonical name = c10-sha-redirect-lb.cnet.com.
Name:   c10-sha-redirect-lb.cnet.com
Address: 216.239.115.148
> q
Server:         192.168.2.1
Address:        192.168.2.1#53[/QUOTE]

I thought the DNS server addresses were supplied by your ISP. My router is 192.168.0.1 but nslookup returns the address I entered that was provided by my ISP.

[www.news.com](www.news.com)
Server:         66.1.0.5
Address:        66.1.0.5#53

Non-authoritative answer:
[www.news.com](www.news.com)    canonical name = c10-sha-redirect-lb.cnet.com.
Name:   c10-sha-redirect-lb.cnet.com
Address: 216.239.115.148

P.S. My wireless is VERY fast.

---

### Post by Sloth on 2005-11-16
> I thought the DNS server addresses were supplied by your ISP. 

They should be.  In my case, my router is acting as a local DNS and forwarding those requests along.

---

### Post by WGH on 2005-11-17
/**So, what I have to "write" exactly in root terminal?! Sorry, but I newbie on Linux!*/

Ok, I've done this without any problem!
The result ```
> www.news.com
Server:         192.168.0.1
Address:        192.168.0.1#53

Non-authoritative answer:
www.news.com    canonical name = c10-sha-redirect-lb.cnet.com.
Name:   c10-sha-redirect-lb.cnet.com
Address: 216.239.115.148

```appears in a second... 

So, I think isn't a DNS problem, isn't it?!
Opening Internet pages is slow again... :(

What can also do?
Thanks a lot!

---

### Post by WGH on 2005-11-17
I notice that PC opens some site (like: [www.google.it](www.google.it), [www.comune.bolzano.it](www.comune.bolzano.it)) very fast, but other (like: this forum) in a very slow way!!!

WGH...

---

