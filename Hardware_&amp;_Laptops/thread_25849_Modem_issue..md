---
title: "Modem issue."
date: 2005-04-11
forum: Hardware &amp; Laptops
---

### Post by Slapdash on 2005-04-11
I had a post in here about my modem problem and I cant see it at all.

Anyway, I used a USR internal 56K modem at first. 
Didnt work.

Now I have a Duxbury 56K External modem.
Ubuntu picks it up and i can dail and it connects. i can use terminal services byt typing in the IP address.
I CANT use Synaptic or Firefox for the net. I have no idea how to get this to work :(
The modem shows its connected.   :-?   
Is it maybe a name resolving problem or a service problem?

---

### Post by kassetra on 2005-04-12
[QUOTE=Slapdash]Now I have a Duxbury 56K External modem.
Ubuntu picks it up and i can dail and it connects. i can use terminal services byt typing in the IP address.
I CANT use Synaptic or Firefox for the net. I have no idea how to get this to work :(
The modem shows its connected.   :-?   
Is it maybe a name resolving problem or a service problem?[/QUOTE]

Ok yeah, that means that Synaptic and Firefox can't find a DNS server...
Have you tried typing in an IP into Firefox?  (Just to prove that Firefox is working, but that it can't find a DNS server) ....

Have you tried changing your DNS IP?

---

### Post by Slapdash on 2005-04-13
Yeah I did that and that is what seems to be the problem.
But I tried to change it and still the same problem

---

### Post by kassetra on 2005-04-13
[QUOTE=Slapdash]Yeah I did that and that is what seems to be the problem.
But I tried to change it and still the same problem[/QUOTE]

Er.  Ok, you've tried changing your DNS to a completely different IP all together ... and still no name resolution?  Do you have a firewall?  Router?

(p.s. totally off topic -- Marlowe is AWESOME stuff!)

---

### Post by heimo on 2005-04-13
You can check if the DNS is working with dig. On terminal type:
```
dig www.ubuntuforums.org
```

If you don't get ip address for that name (probably 66.246.118.210),  your DNS is not working. You can try spesific DNS server this way:
```
dig @yourDNSipaddress www.ubuntuforums.org
```

When you find working DNS server, add it to /etc/resolv.conf

You can verify that it's not other problem with ping. Just ping some host that returns pongs. ;) Ubuntuforums.org should be ok. (if you don't have firewall blocking ICMP packets)

---

### Post by az on 2005-04-13
Open a terminal and do sudo pppconfig.  Name the connection "provider".  Save before quitting.

In another teminal do 

plog -f

as you do 

sudo pon 

in another terminal.

---

### Post by Slapdash on 2005-05-03
Azz you are a genius thanks. Works like a charm

---

