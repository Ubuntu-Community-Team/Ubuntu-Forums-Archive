---
title: "[SOLVED] Transmission bittorrent client and TOR"
date: 2008-07-25
forum: General Help
---

### Post by Kain000 on 2008-07-25
Hey all,
I was just searching around without any real sucess but I was wondering if the transmission bittorrent client that comes bundled with Ubuntu uses SOCKS proxy so that it routs threw TOR to connect to the host server and thus it's traffic would be encrypted or if TOR needs to be configured for this to happen.  If not does any one know of a client that is compatiable with TOR?

I know TOR works in firefox with it's torbutton and a quick check to whatismyip.com but does it automatically mask all network traffic in and out of my system?  

I've tried the command 

          sudo tor status

and get:
 
Jul 25 02:55:17.611 [notice] Tor v0.1.2.19. This is experimental software. Do not rely on it for strong anonymity.
Jul 25 02:55:17.612 [warn] Command-line option 'status' with no value. Failing.
Jul 25 02:55:17.612 [err] Reading config failed--see warnings above.

---

### Post by daveerickson on 2008-08-18
I am also looking for an answer to this question. I know that Azureus can be set to use tor, but I really don't need all of the other features that it has.

---

### Post by Kain000 on 2008-08-18
> **daveerickson said:**
> I am also looking for an answer to this question. I know that Azureus can be set to use tor, but I really don't need all of the other features that it has.

Yeah upon further searching on the net and primarly transmission's own forums it would appear that as handy and lightweight as transmission is, it isnt able to take advantage or TOR, at least not yet, there was alot of people requesting support for TOR and other such proxies to avoid the problem of ISPs' shaping your bittorent traffic.   not to mention big brother watching everything your downloading.   So until then I've moved to Azureus.  IT's an ok program, but your right about it being more than you need.   I liked transmission because it was tidy and simple.   
if you end up with azureus or bitcomet or Utorrent check out this page for simple instructions on how to encrypt the traffic to avoid the comcasts out there.
hope this helps.
-sean

[http://torrentfreak.com/how-to-encrypt-bittorrent-traffic/http://torrentfreak.com/how-to-encrypt-bittorrent-traffic/](http://torrentfreak.com/how-to-encrypt-bittorrent-traffic/http://torrentfreak.com/how-to-encrypt-bittorrent-traffic/)

---

### Post by jakupl on 2009-03-29
PLEASE don’t run peer-to-peer download data through Tor as it can’t handle the network traffic. If people continue to do this then Tor will start banning such traffic which will badly impact legitimate use

---

### Post by Kain000 on 2009-03-29
> **jakupl said:**
> PLEASE don’t run peer-to-peer download data through Tor as it can’t handle the network traffic. If people continue to do this then Tor will start banning such traffic which will badly impact legitimate use

no no you mistaken my post, I agree TOR cannot handle p2p traffic, not to mention the throughput would be a disastor.

I mean to use tor to proxy your connection to a p2p tracker, not the actual downloading.

vuse can do this eaisly.

---

### Post by sebrock on 2009-04-02
I would also like to know this.

EDIT: Why is this marked as solved? Is it solved, then please write the instructions.

---

### Post by Kain000 on 2009-04-02
> **sebrock said:**
> I would also like to know this.

EDIT: Why is this marked as solved? Is it solved, then please write the instructions.

as you would of discovered form my former post the answer is that transmission cannot take advantage of a socks 5 proxy.   Vuze can

---

### Post by aalbuquerque on 2009-05-06
> **Kain000 said:**
> no no you mistaken my post, I agree TOR cannot handle p2p traffic, not to mention the throughput would be a disastor.

I mean to use tor to proxy your connection to a p2p tracker, not the actual downloading.

vuse can do this eaisly.
You can do that with Transmission. Goto Edit->Preferences and choose the Trackers tab. There you can set the proxy to use when connection to a tracker.

---

### Post by Kain000 on 2009-05-06
> **aalbuquerque said:**
> You can do that with Transmission. Goto Edit->Preferences and choose the Trackers tab. There you can set the proxy to use when connection to a tracker.

ohhhh well thankyou for this sir, transmission is ALOT easier to get a 'mom or pop' user to use than vuze.

---

### Post by suomalainen on 2009-12-22
I'm using Transmission 1.06 (5136) and do not have the trackers tab.

---

### Post by Apache0c on 2011-01-02
I know this is an old topic but I found it with a google search and wanted to respond the this question for others.

> **suomalainen said:**
> I'm using Transmission 1.06 (5136) and do not have the trackers tab.
It's actually under the Proxy tab in GTK version 1.93. 

But it is not in every version of Transmission. For example, I'm running Kubuntu and I have both the QT and GTK versions of Transmission installed. The QT version does not have this Proxy tab while the GTK version does.

---

