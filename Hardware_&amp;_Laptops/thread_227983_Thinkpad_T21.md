---
title: "Thinkpad T21"
date: 2006-08-02
forum: Hardware &amp; Laptops
---

### Post by __dave on 2006-08-02
Hi, I've also posted a similar question to this in the networking forum but I was just wondering if anyone else has had a problem connecting to the internet on a thinkpad with a pcmcia ethernet card??

---

### Post by Orestes on 2006-08-03
I've got a T22, works fine with built-in ethernet and my Orinoco Gold wireless PCMCIA card. What model is your PCMCIA card?

---

### Post by __dave on 2006-08-04
I have 2 but neither of them seem to work. One is a '3Com Etherlink III 3C589D-TP' and the other's a 'Xircom CE3B-100BTX'.
They are both detected in Ubuntu but neither of them will let me connect to the internet. The Xircom one is constantly 'idle' under status in network connections and the 3Com one just flicks through 'sending/receiving, sending, idle etc.'

---

### Post by Carbonfish on 2006-08-04
I am having a similar frustration with a PCMCIA card in my T23.

I am showing a solid connection to the network, I have great signal strength, I can ping anyone in the terminal and show a connection with no packet loss. But no matter what I try, Firefox won't load web pages (it spins its wheels until it times out).

So the card is recognized. It connects to the net. But it doesn't play nice with the browser.

Whazzup??

KC

---

### Post by __dave on 2006-08-05
My problem is continuing to get worse it seems.
I've posted more details on this thread:

[http://www.ubuntuforums.org/showthread.php?t=227356](http://www.ubuntuforums.org/showthread.php?t=227356)

If you go to my last post on that thread, you'll see what I mean. :(

---

### Post by isharra on 2006-08-05
I don't know if this could be related or not. 

My last install on this T22, when the installer made the adjustments to /etc/network/interfaces it put my dns address as the gateway ip and neglected to put any entry in /etc/resolv.conf. When I corrected that all networking worked properly.

---

### Post by isharra on 2006-08-05
> **Carbonfish said:**
> So the card is recognized. It connects to the net. But it doesn't play nice with the browser.
That's generally a sign that the DNS setting is wrong in /etc/resolv.conf (no name resolution)

verify that there is a "nameserver xxx.xxx.xxx.xxx" line in /etc/resolv.conf (and that it's using the correct ip address for this connection).

If that is correctly set up then verify that you have a default route active. 'route -n' you should see a line with destination 0.0.0.0 if not that's your problem.

Sorry old habits lead me to command line checks, I'm a long time *nix user but new to Ubuntu. 

If you prefer to use a gui. In Ubuntu, System -> Networking. On the Connections tab: make sure your active card is selected as the Default gateway device. then click on your card and hit properties and make sure the netmask and gateway are correct if using static ip, finally check the DNS tab and be sure your nameserver is properly entered.

---

