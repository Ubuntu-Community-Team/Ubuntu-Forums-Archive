---
title: "network interfaces changing place"
date: 2006-04-24
forum: Hardware &amp; Laptops
---

### Post by Peter76 on 2006-04-24
Hello, I have a weird problem; I've a box set up as a router server with three nic's in it; one connected to the internet(eth0) and the other two going to two computers. Now every time I reboot the server the other two nic's get other names: first I have eth1 and eth2 ( and eth0 of course) and after a reboot I have eth2 and eth3, or eth1 and eth2 change place ( first nic is eth0, second should be eth1, second eth2, but becomes eth0, eth2, eth1) 
Is there anyway to solve this? I remember reading something a while ago that it is possible t map modules to devices; as the three nics have all different chipsets and drivers, this could sort me out... Or any other solution off course. 
Thanks

---

### Post by mpvano on 2006-04-25
Your problem may be caused by your being at cross purposes with a service that Ubuntu installs that tries to rename interfaces consistently.

If it's set up wrong for what you're trying to do, it can cause problems, but I suspect that if it's set up properly it will do exactly what you're trying to do.

The confusion seems to occur if you don't know it's there or what it's configured to do to you.....

The service is called "ifrename" and it uses a configuration file called "/etc/iftab". try "man ifrename" and "man iftab" for a lot of information about the different ways you can use it. I'm guessing all you need to do is set /etc/iftab to rename the interfaces based on their built-in mac addresses...

hope this helps....

Mario

---

### Post by Peter76 on 2006-04-26
Hi Mpvano, thanks a lot for your solution!!! Never heard of this iftab, but it solved the problem right away; only my eth0 card was mentioned in there... Added the other two and now it works.

---

### Post by dpm on 2006-05-09
What about interfaces that have no mac address?

I already had a look to iftab, since I was having more or less the same problem.

I've got 2 network interfaces on my system: one is eth0, a network card which has got an entry in /etc/iftab, and the other one is simply a normal usb port connected to my router. This interface is usually called eth1.

I am not using eth0 but eth1. So far so good. eth1 always gets a DCHP-assigned IP address from the router with no trouble. The only problem I've got is that eth1 seems to randomly change name to eth2 after some days.

I understand it is not possible to avoid this by using /etc/iftab, since the usb network interface has got no mac address, but is there another way?

---

### Post by mpvano on 2006-05-09
Did you actually read the entire man page for iftab? It describes your problem and gives several other ways to control the mapping besides by MAC address.

One of the other selectors should probably work for you if your card and driver are working properly. 

You may not be able to use iftab/ifrename to "fix" a broken driver that loads twice, or mysteriously crashes and gets reloaded, or something like that.

Perhaps if you would describe the interface and driver more specifically, someone here may recognize it and have more information for you....

Mario

---

### Post by dpm on 2006-05-09
Mario,

thanks a lot for your comments.

I had started a new thread for my problem and I managed to solve it with the help of other forum members:

[http://www.ubuntuforums.org/showthread.php?p=999114#post999114](http://www.ubuntuforums.org/showthread.php?p=999114#post999114)

Basically my eth1 does have a mac address (probably that from the router) and I can give it to /etc/iftab to match the interface.

BTW, as you suggested, what helped was reading the man page for iftab.

---

