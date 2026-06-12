---
title: "Remote access behind NAT router"
date: 2008-11-01
forum: General Help
---

### Post by polc1410 on 2008-11-01
I don't know where to post this, so its going in general.  Move it if there is someplace better.

I'm going to describe a small network:

Office 1: 3 Linux PCs (192.168.1.101-103) - Behind a single router (192.168.1.1 / Internet IP-1)

Office 2: 2 Linux PCs (192.168.0.70-71) - Behind a single router (192.168.0.0 / Internet IP-2)

If a user in the same office needs remote support using rdesktop that is quite achievable.

If a user in Office 1 wants support from Office 2 or vice versa - we get stuck because we need to change the firewall rules.  The snag being that we don't allow remote administration of firewall rules, and if a user is requesting remote assistance they probably shouldn't be within 100 miles of the firewall rules ;-)

So how can we do this on a scalable way to allow say 50 users in each office and 50 offices...  Have I missed something obvious?

It seems MS remote assistance for vista, can do it if the "right" form of NAT is used (for that I read insecure!!):lolflag:  But is there a method that doesn't need a specific 'brand' of router and doesn't need the firewall changing each time?  The alternative method on MS is to use MSN to initiate the assistance request.  

Ideally I'd like:
- Linux based assistance 
- To linux machines
- To XP / Vista machines (I haven't mentioned them in my stuff above as they are being supported from MS to MS via MSN ( :(( )
- No extra software to install (or at least installed by support before the assistance request)
- No firewall changes or one single change in advance

Your thoughts are awaited...
:popcorn:

---

### Post by deconectat on 2008-11-01
Why don't you join all your offices in a vpn network? This has a lot of advantages, like being able to use a single file server, or web server for your company's intranet.

---

### Post by alphacrucis2 on 2008-11-01
> **polc1410 said:**
> I don't know where to post this, so its going in general.  Move it if there is someplace better.

I'm going to describe a small network:

Office 1: 3 Linux PCs (192.168.1.101-103) - Behind a single router (192.168.1.1 / Internet IP-1)

Office 2: 2 Linux PCs (192.168.0.70-71) - Behind a single router (192.168.0.0 / Internet IP-2)

If a user in the same office needs remote support using rdesktop that is quite achievable.

If a user in Office 1 wants support from Office 2 or vice versa - we get stuck because we need to change the firewall rules.  The snag being that we don't allow remote administration of firewall rules, and if a user is requesting remote assistance they probably shouldn't be within 100 miles of the firewall rules ;-)

So how can we do this on a scalable way to allow say 50 users in each office and 50 offices...  Have I missed something obvious?

It seems MS remote assistance for vista, can do it if the "right" form of NAT is used (for that I read insecure!!):lolflag:  But is there a method that doesn't need a specific 'brand' of router and doesn't need the firewall changing each time?  The alternative method on MS is to use MSN to initiate the assistance request.  

Ideally I'd like:
- Linux based assistance 
- To linux machines
- To XP / Vista machines (I haven't mentioned them in my stuff above as they are being supported from MS to MS via MSN ( :(( )
- No extra software to install (or at least installed by support before the assistance request)
- No firewall changes or one single change in advance

Your thoughts are awaited...
:popcorn:

Set up a VPN between the two sites. Some routers support IPSec VPN's which allows you to set up an encrypted tunnel between the two routers across the internet. You can then SECURELY pass whatever traffic you like over the IPSec tunnel. If your routers don't support IPSEC VPN's then you could use a linux box at each site to terminate the VPN. IPSec tunnels on Linux are supported by OpenSwan but you may have trouble getting that to work through the NAT on the routers (NAT traversal). So instead you could use OpenVPN running over whatever port you specify. The router at the server end of the connection would port forward the selcted port to the OpenVPN server.

---

### Post by Sami_Sdata on 2008-11-01
> **polc1410 said:**
> I don't know where to post this, so its going in general.  Move it if there is someplace better.

I'm going to describe a small network:

Office 1: 3 Linux PCs (192.168.1.101-103) - Behind a single router (192.168.1.1 / Internet IP-1)

Office 2: 2 Linux PCs (192.168.0.70-71) - Behind a single router (192.168.0.0 / Internet IP-2)

If a user in the same office needs remote support using rdesktop that is quite achievable.

If a user in Office 1 wants support from Office 2 or vice versa - we get stuck because we need to change the firewall rules.  The snag being that we don't allow remote administration of firewall rules, and if a user is requesting remote assistance they probably shouldn't be within 100 miles of the firewall rules ;-)

So how can we do this on a scalable way to allow say 50 users in each office and 50 offices...  Have I missed something obvious?

It seems MS remote assistance for vista, can do it if the "right" form of NAT is used (for that I read insecure!!):lolflag:  But is there a method that doesn't need a specific 'brand' of router and doesn't need the firewall changing each time?  The alternative method on MS is to use MSN to initiate the assistance request.  

Ideally I'd like:
- Linux based assistance 
- To linux machines
- To XP / Vista machines (I haven't mentioned them in my stuff above as they are being supported from MS to MS via MSN ( :(( )
- No extra software to install (or at least installed by support before the assistance request)
- No firewall changes or one single change in advance

Your thoughts are awaited...
:popcorn:



 I have several machines at my home running Linux, BSD and some windows.  All have vnc configured so I can update from my work on slow nights.  I use the connectvia option in tightvnc and connect by ssh into one BSD box (this is my router/firewall but could be any box used as a jump server) then from their I connect to the machine I want to access.  So with a vncserver running on 10.99.99.102 and my login as "me" on firewall.box.  From the Solaris box at my work I would run

vncviewer -via [email]me@firewall.box[/email] 10.99.99.102:0

I get a prompt to login to the firewall with my ssh password, then I get another prompt for the vnc login.  This also makes all the traffic outside your firewall encrypted in ssh.  The machine at 10.99.99.102 can be running any OS that has a vnc server.  I'm using a Unix box at the client end but I have seen walkthroughs for doing the same thing with putty in windows but I've never had to try that out.

---

### Post by polc1410 on 2008-11-02
Yeh VPN would be logical option I agree, **however** what I didn't explain was Office 1 and Office 2 are actually different organisations.

Office 1 have provided the linux boxes for Office 2, and provide the support for them (on or offsite).  If we scale that up we would have 50 clients all with their own networks.... don't know that I fancy 50 VPN connections either permanently or temporary.  Then on top of that I anticipate supporting specific software on MS boxes (Probably XP and Vista) - or even just when a client says what they see on the MS IE screen is different to what we are seeing to be able to look and see...  I had a client (reasonably sensible) last night who we were doing some work with - their issue was an MS IE issue and I suggested they open the page (not one of mine!) in IE7 to see if it behaved better and she said it didn't.  When I took remote control - she had safari open! (Don't even know how she got safari on there!)

Does raise a good question about the connections... I read someplace that rdesktop is encrypted (seems odd since MS use it!)  I was hoping to use kdesktop for that reason and cause windows doesn't then need stuff installed. I take it vnc isn't?  in which case it should be tunnelled via a VPN or SSH...

Will go read about via.  Thats kind of what I'm looking for.  What would really make sense would be if NAT allowed an @ symbol! i.e. [email]192.168.1.100@my.internet.ip[/email] !!

---

