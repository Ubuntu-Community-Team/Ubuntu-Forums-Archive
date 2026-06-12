---
title: "[SOLVED] Server not visible from internet"
date: 2008-07-23
forum: General Help
---

### Post by El Rogueo on 2008-07-23
I've been using linux for a few years now, but I've never had a successful server build before, so this current build is the closest I've been:

I have a 766MHz Pentium 2 with 128 MB of RAM running in my basement, with Apache2 and vsftpd installed, along with Wolfenstein: Enemy Territory. On the local network (accessing the server via its local address 192.168.x.x) I can get to Apache2's "It Works!" page, upload and download files via vsftpd, connect through SSH with putty, and play games against bots on Enemy Territory. However, as soon as I try to connect via the internet I get time out errors.

I am behind a Dell TrueConnect 2300 router, with all the ports I use forwarded. I signed up a DynDNS name to the machine, pointed at the external IP of the router, but that doesn't come through either.

The only thing I can think of is to plug the server directly into the cable modem, but then I would have no way to test it short of driving to the library, and if it didn't work, no idea where to go from there.

I have followed several different guides to set up servers, but many of them have steps like, "Just install this and you're done" or "Once you change this config, everything should be great", with no explanation of what to do if things do not work out.

I read somewhere that some ISPs block certain ports to discourage home servers, but I have a friend with a server and my ISP, confirming that that is not the case.

What's the best way to go about this?

Thanks.

---

### Post by apswartz on 2008-07-23
Maybe your friend can look at your setup?

My guess is that there is something wrong with your router setup.

Sounds like you have a dynamic IP addy. Does you friend have a dynamic addy or a static one? It may make a difference in the way your ISP treats ports and servers.

Also, most Cable ISPs prohibit servers in their TOS.

With DSL it may vary, sometimes depending on the type of account and whether you have a static/dynamic addy.

---

### Post by El Rogueo on 2008-07-23
> **apswartz said:**
> 
My guess is that there is something wrong with your router setup.


That was my conclusion also.

> 
Sounds like you have a dynamic IP addy.

The server is set to a static IP address to make things simpler, also, for port forwarding reasons.

> Also, most Cable ISPs prohibit servers in their TOS. 

While looking up my TOS is a good idea anyway, my friend with his own server is on both the same cable provider and same cable package as mine, with no difficulty. Whether or not the activity is "not allowed", I would prefer to discern why the server is nonfunctional first.

---

### Post by apswartz on 2008-07-23
What I meant was that it sounds like you have a dynamic addy assigned to your cable modem by your isp. What about your friend? Is his also dynamic?

---

### Post by El Rogueo on 2008-07-23
My external IP could concievably be dynamic, as I am unsure how to be sure, but from personal experience it has only changed when I specifically renewed it. My friend describes his similary as "only about once a milennia"

---

### Post by apswartz on 2008-07-23
Are you willing to post a domain name for us to see what it resolves to for us and what error message(s) we may be getting?

---

### Post by El Rogueo on 2008-07-23
> **apswartz said:**
> Are you willing to post a domain name for us

rather stupidly, I only didn't because it didn't occur to me
also, your error will most likely only be a connection fail or timeout, but still appreciated.

wolfet-oldfag.dnsalias.com

apache should also respond to wolfet-oldfag.dnsalias.com:22222

In addition, I read through my ISP's AUP, which only prohibits using a server for commercial or enterprise purposes, but not for private use.

---

### Post by apswartz on 2008-07-23
Maybe the problem is in the domain name. When I do a whois lookup I get...

No match for "WOLFET-OLDFAG.DNSALIAS.COM".
>>> Last update of whois database: Wed, 23 Jul 2008 13:38:17 EDT <<<

---

### Post by El Rogueo on 2008-07-23
> **apswartz said:**
> Maybe the problem is in the domain name. When I do a whois lookup I get...

No match for "WOLFET-OLDFAG.DNSALIAS.COM".
>>> Last update of whois database: Wed, 23 Jul 2008 13:38:17 EDT <<<
I thought dnsalias was the domain name, and that wolfet-oldfag was the hostname; when I try whois.net, it tells me the entire name is not a domain, dnsalias.com is a registered domain, and nothing else.

And if the problem is the domain name, what would I do about it? Just get another one?

---

### Post by sp0nge on 2008-07-23
I have a similar issue. 

I am able to connect through my LAN, but this morning I forwarded the port for putty (I changed the default port 22) and came to work. Once I got settled, I tried to connect via putty by typing my external IP address 65.60.XXX.XXX and entering the port I forwarded on my router to get an error saying connection refused. 

I'm not concerned with the domain name yet, I'm simply working with the IP at this point to keep the problems as simple as possible. I just want to be able to access this server while I'm at work.

---

### Post by El Rogueo on 2008-07-23
> **sp0nge said:**
> I have a similar issue. 
(I changed the default port 22) 

For what reason did you change the default putty port, and do you have other daemons running that you can try to connect to? Also, are you sure your server is listening on the new port?

for the sake of curiosity, what kind of router do you have?

---

### Post by sp0nge on 2008-07-23
Linksys WR54G

---

### Post by apswartz on 2008-07-23
> **El Rogueo said:**
> I thought dnsalias was the domain name, and that wolfet-oldfag was the hostname; when I try whois.net, it tells me the entire name is not a domain, dnsalias.com is a registered domain, and nothing else.

And if the problem is the domain name, what would I do about it? Just get another one?

Yes, but you have to have a DNS entry for wolfet-oldfag.dnsalias.com for web browsers to find it.

---

### Post by cariboo on 2008-07-23
I've got the same router and it took all of 5 minutes to get it set up. I'm using Noip. I'm running the Noip applet on my server as it is always on. The linksys router has buitin ddns, but it is only for DynDNS and TZO.com.

I only setup port forwarding for ftp using the standard port as that is all I need. No sooner had I set things up and I had someone from Korea banging on my server trying to get in using Administrator as the user name. I set up fail2ban and the next time they tried they got banned for an hour and I haven't seen them since.

I would suggest using Noip and using standard ports, just to keep it simple. Once you got everything working then you can starting changing port mappings.

Jim

---

### Post by El Rogueo on 2008-07-23
> **apswartz said:**
> Yes, but you have to have a DNS entry for wolfet-oldfag.dnsalias.com for web browsers to find it.

My (apparently erroneous) assumption was that by registering with DynDNS, an entry would be created. So, what should I do about it?

> **cariboo907 said:**
> I've got the same router and it took all of 5 minutes to get it set up. I'm using Noip. I'm running the Noip applet on my server as it is always on. The linksys router has buitin ddns, but it is only for DynDNS and TZO.com. 

The same router as whom, Jim? Sp0nge?

---

### Post by apswartz on 2008-07-23
Sorry, I am not familiar with DynDNS.

But, it would seem to me that you need to register a domain with a domain name registry and then point your domain to DynDNS, perhaps with a CNAME record (there should be instructions).

---

### Post by sp0nge on 2008-07-23
I must have missed something. 

Do I need to have a Dyn DNS account to make this work? I'm not even dealing with a domain name at the moment, I simply want to be able to make my site live while referencing the url my.ip.add.ress/index.htm (which I can do on the LAN). Eventually I'll want to have a domain name associated with the server, but for now, I'm not concerned with that. 

I should be able to forward the port to the server and when I call the external IP XX.XX.XXX.XXX/index.htm the page should show- or am I totally off base?

---

### Post by apswartz on 2008-07-23
okay, give us the IP address to try. (We will keep trying until we get it :-0 )

---

### Post by El Rogueo on 2008-07-23
> **apswartz said:**
> Sorry, I am not familiar with DynDNS.

But, it would seem to me that you need to register a domain with a domain name registry and then point your domain to DynDNS, perhaps with a CNAME record (there should be instructions).

"Dynamic DNS (DDNS) allows you to create a hostname that points to your dynamic IP or static IP address or URL." according to their website. It has preregistered domains, of which you can choose up to five, which it appends to your hostname and registers it to redirect.

Which is to say, I thought I did register it.

---

### Post by El Rogueo on 2008-07-23
> **sp0nge said:**
>  

I should be able to forward the port to the server and when I call the external IP XX.XX.XXX.XXX/index.htm the page should show- or am I totally off base?

this is totally what I thought to, so I hope you're right

---

### Post by apswartz on 2008-07-23
Would you share your numerical IP address so we can test it?

---

### Post by sp0nge on 2008-07-23
It's not accessible. 

I've been able to use the internal IP to access the page from another machine on the LAn. After I forwarded the ports this morning for ssh (I realize now I didn't open port 80), I went to work to attempt to connect via putty and the connection was refused. I'll open port 80 and post the IP once I am in front of the machine again.

---

### Post by apswartz on 2008-07-23
@El Rogueo
would you share your numerical IP addy?

---

### Post by El Rogueo on 2008-07-23
70.94.246.255

---

### Post by jimv on 2008-07-23
> **apswartz said:**
> Sorry, I am not familiar with DynDNS.

But, it would seem to me that you need to register a domain with a domain name registry and then point your domain to DynDNS, perhaps with a CNAME record (there should be instructions).

No, you don't have to register a domain.  All you need is an account with DynDNS and they take care of the DNS for your IP.

---

### Post by jimv on 2008-07-23
> **apswartz said:**
> Maybe the problem is in the domain name. When I do a whois lookup I get...

No match for "WOLFET-OLDFAG.DNSALIAS.COM".
>>> Last update of whois database: Wed, 23 Jul 2008 13:38:17 EDT <<<

WHOIS isn't going to find anything for a subdomain.

---

### Post by jimv on 2008-07-23
> **El Rogueo said:**
> 70.94.246.255


70.94.246.255  is not a valid IP.  An ip address cannot end it 255...I think that's a netmask.

Go to this page:

[http://whatismyip.com/](http://whatismyip.com/)

It will show you your external IP.  Then update DynDNS with that IP and your server will work.

---

### Post by apswartz on 2008-07-23
> **El Rogueo said:**
> 70.94.246.255

No, your IP addy doesn't end in 255

---

### Post by El Rogueo on 2008-07-23
> **jimv said:**
> 70.94.246.255  is not a valid IP.  An ip address cannot end it 255...I think that's a netmask.

Go to this page:

[http://whatismyip.com/](http://whatismyip.com/)

It will show you your external IP.  Then update DynDNS with that IP and your server will work.

> **apswartz said:**
> No, your IP addy doesn't end in 255

If either of you would like to place some sort of bet, I would love to take your money :). My IP address is 70.94.246.255. My netmask is 255.255.255.0. Whatismyip.com confirms my ip address, as does my firefox applet that shows my external IP.

your internal IP might not be able to end in 255, or your external IP might not be able to start with 255, but this address is definitely valid.

pic included

---

### Post by apswartz on 2008-07-23
Ah, I'll take that bet. 225 is not 255. ;-)

---

### Post by apswartz on 2008-07-23
Okay, your web page is visible! It Works!

Your router is fine.

---

### Post by El Rogueo on 2008-07-23
> **apswartz said:**
> Ah, I'll take that bet. 225 is not 255. ;-)

oh god
I just laughed so hard I almost cried

I wonder if that one works :lol:

---

### Post by El Rogueo on 2008-07-23
hm

I'm not sure what you saw, but when I type in the correct IP, I get the login to my router (yikes), not apache for my server.

Is there some simple step I'm missing now that we're over the large mistake of being illiterate?

---

### Post by apswartz on 2008-07-23
> **El Rogueo said:**
> oh god
I just laughed so hard I almost cried

I wonder if that one works :lol:

Yep, it works!

---

### Post by apswartz on 2008-07-23
> **El Rogueo said:**
> hm

I'm not sure what you saw, but when I type in the correct IP, I get the login to my router (yikes), not apache for my server.

Is there some simple step I'm missing now that we're over the large mistake of being illiterate?

I imagine that is because you are typing it in from INSIDE your network. You need to search from outside the network.

---

### Post by El Rogueo on 2008-07-23
For sure, I just tried it using TOR and it showed up properly, thanks a lot!

---

### Post by apswartz on 2008-07-23
Ah! [http://wolfet-oldfag.dnsalias.com](http://wolfet-oldfag.dnsalias.com) now works as well!

---

### Post by El Rogueo on 2008-07-23
many many thanks for your time (and proofreading skills!)

---

### Post by apswartz on 2008-07-23
No problem. Glad it is working! That's what it is about.

---

