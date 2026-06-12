---
title: "noobie question - network settings"
date: 2005-12-07
forum: Installation &amp; Upgrades
---

### Post by Houman on 2005-12-07
Hi there, im setting ubuntu up on a school computer, when it gets to hostname and domain name i dont really knwo what to enter;

there is a guide in our school for setting up networks and the domain name is say gal.university.com, and when the installation was asking about a hostname it had some default value in it : bob2345.something.university.com.

On a corporate or school network where ips are assigned statically, does it matter what i enter for the domain? (I have internet already) and what good does that do ?:| also as for the hostname, is is a fixed thing? should i change what it gave me? 

also if the hostname is bob2345.something.university.com, can i actually access the machine (through ssh) form outside if i use this address, evebnthough the machine is behind a gateway?

sorry i dont understand about this hostname and domain name, if someone can explain or give a link ill be very grateful 

also, is there a way to know if the machine is dual core or 64 bit? i installed teh regular 32 bit on the computer (Dell Precision 650 Xeon) but i think it might be dual core or 64 bit, i tired cat /proc/cpuinfo but it says nothing about the 32/64 and single/dual core thing, i think i have to reinstall the OS if its actually 64 bits (althoguh the 32 works)



regards;

---

### Post by Dr. Nick on 2005-12-07
you can use 32bit on a 64bit no problem, not sure what yours is though. The hostname is the name of the computer that would appear on the "newtwork neighborhood" if it was a windows computer. 
[Google Definitions of hostname]("http://www.google.com/search?q=define%3Ahostname&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-US:unofficial") 

The domain name doesnt affect dns. To connect to the computer you would use hostname@domainname I believe. 
[Google definition of domainname]("http://www.google.com/search?hs=mBB&hl=en&lr=&client=firefox&rls=org.mozilla%3Aen-US%3Aunofficial&q=define%3Adomainname&btnG=Search")
If you have internet then these settings are meaning less in that regard, the only reason to set them would be so that you comply with the school policy. Static Ips dont rely on domain name usually. You may be able to access it through ssh but it would depend more on the gateway setup I believe and you would hae to configure ssh on ubuntu.

---

