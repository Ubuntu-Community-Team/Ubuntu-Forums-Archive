---
title: "upgrading ubuntu on two laptops"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by jarrah-95 on 2009-10-03
i have two ubuntu laptops and have a caped internet connection so i only want to download it once is there a torrent or disk that i can download to upgrade but keep the same settings.
thanks

---

### Post by s3MA00RRNY on 2009-10-03
Just download the new desktop disk and set it as a source in Synaptic.

---

### Post by jarrah-95 on 2009-10-03
isnt the proper way to use the alternant cd i have never done it before and was going to try it the way you said before but then ended up having to reinstall it because the cd whouldent upgrade it

---

### Post by cariboo on 2009-10-03
You can use apt-cacher, it is in the repositories, it will allow you to download the updates once and then distribute it to other computers on your network.

---

### Post by jarrah-95 on 2009-10-04
2 questions about apt-cacher 
1 will that let me install a full (system) update (as in upgrading from jaunty to karmic) 
2 do i have to have a network connection between the two laptops as i only have one internet connection and cannot properly set up a ad-hoc network between them
thankyou

---

### Post by Lars Noodén on 2009-10-04
> **jarrah-95 said:**
> 2 questions about apt-cacher 
1 will that let me install a full (system) update (as in upgrading from jaunty to karmic) 
2 do i have to have a network connection between the two laptops as i only have one internet connection and cannot properly set up a ad-hoc network between them
thankyou

I would second cariboo907's suggestion of apt-cacher.
You may have to do some juggling.  You did the main install from the CD.  

Then install apt-cacher or apt-cache-ng on the first computer.  Set it so that APT uses the apt-cacher proxy:
[https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)

Test using 'apt-get update' and following the apt-cacher logs with tail, or your favorite method.  

Then disconnect the switch from the network, at least the first time to be sure you are using the cache, and make the second machine use the first machine as its proxy.  Be sure the first machine has apt-cacher running and the firewall open on the appropriate port.  

You might also consider installing squid on each machine, if you haven't already, and proxying your regular web browsing through that.  Be sure to check the cache after a bit of use to see if it's full or has plenty of space.

---

### Post by jarrah-95 on 2009-10-05
i dont think that will work as i dont have a network between the two computers i just have one internet connection that i switch between the two (one at a time)
also what do you mean about did i install it from a disk

---

### Post by Meow27 on 2009-10-05
if you have disk imaging software, you can just past the 1st image to the next laptop since the drivers are generic... graphics drivers and such are a different story though

but caching apt seems like a good idea.

---

### Post by Lars Noodén on 2009-10-05
> **jarrah-95 said:**
> i dont think that will work as i dont have a network between the two computers i just have one internet connection that i switch between the two (one at a time)
also what do you mean about did i install it from a disk

Install apt-cacher on a machine and then make sure that it is configured to turn on automatically.

Then on the machine with the cache, also install dnsmasq.  
But set it so that it should not start automatically and only start when told to [FONT="Courier New"]sudo update-rc.d -f dnsmasq remove[/FONT]

Either configure dnsmasq to include a range of ip address to dole out.
You may want to add an alias.  The example below adds the IPv4 address 10.2.1.2 to interface eth0 with a label 'dhcpserver'

[INDENT][FONT="Courier New"]ip addr add 10.2.1.2/24 dev eth0 label eth0:dhcpdserver[/FONT][/INDENT]

```

test -e /etc/apt/apt.conf.orig \
|| cp /etc/apt/apt.conf /etc/apt/apt.conf.orig

echo 'Acquire::http::Proxy "http://jarrah-95-a:3142";' > /etc/apt/apt.conf

```

Then, with apt-cacher running, do your update.  
Then disconnect from the net and start dnsmasq.
Connect your second laptop directly to the first one.
Make sure that it has apt.conf configure to point to the first laptop.
Update.

---

### Post by jarrah-95 on 2009-10-05
i think ill just download the alternate install and install it on both 
thanks

---

### Post by jarrah-95 on 2009-10-24
ive finaly got there and have downloaded the alternant install but now have a nother problem, i cant get it to upgrde i have booted onto the usb and have pluged it in while in ubuntu but still nothing (tryed sources and synaptic)
thanks

---

### Post by Lars Noodén on 2009-10-25
What are the symptoms or error messages when it fails to upgrade?

---

