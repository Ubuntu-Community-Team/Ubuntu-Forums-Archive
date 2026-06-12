---
title: "ubuntu 9.04 internet problems (help!)"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by mr.Hsmith on 2009-04-27
ok, i installed ubuntu studio 9.04 on to a 9 gig partition on my laptop, however i could not configure my DNS server, so i cannot connect to the internet while using ubuntu studio, how can i fix this?

---

### Post by culmore on 2009-04-27
Need a bit more information. Does ubuntu boot? are you stuck not knowing your user name and password. Try and describe what is displayed on the screen when you turn on the machine.

---

### Post by mr.Hsmith on 2009-04-27
everything loads properly, but when i try to open firefox i get the "firefox cannot find this page" thing., nor will it find the updates

---

### Post by Sef on 2009-04-27
Sounds like an internet connection problem.   How are you connected to the internet?

---

### Post by mr.Hsmith on 2009-04-27
i use DSL, 

come to think about it, i had trouble configureing my DNS server, this is most likely the problem, how do i solve this?

---

### Post by mr.Hsmith on 2009-04-27
any ideas? anyone?

---

### Post by culmore on 2009-04-29
If it is your internet connection try the following. Open a console window and type

ping google.com

if you get a response then your internet and DNS setting are fine. You should get something like this

PING google.com (74.125.67.100) 56(84) bytes of data.
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=3 ttl=51 time=683 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=4 ttl=51 time=688 ms


If this does not work then type, in a console windows

ping 74.125.67.100

If this command gives a response then indeed it is a DNS problem. If it does not work at all then you are not connected to the internet.

To configure your DNS right click on the little networking icon on your top menu bar. It should not be to hard to enter the ip addresses of DNS servers. You will need to get the ip addresses of the DNS servers from your router/other PC/Internet Service Provider.

---

### Post by tru infini on 2010-01-26
i am having problems with my ubuntu 9.04 connecting to the internet. i have tried to ping google like you said and it said it was an unknown host. So i tried to ping 74.125.67.100 and it said the network is unreachable.

---

### Post by Kanna2412 on 2011-02-20
I also using ubuntu 9.04 and have the same problem. It worked earlier until I formated my computer 2 weeks ago. My internet provider gives dynamic ip (DHCP). So I need not configure the ip in my network manager settings. 

I check the internet connection on my friend's laptop with Windows 7 and it is working fine. 

The network manager applet shows up like it is disabled. Loop back ip 127.0.0.1 is pinging. I am tired searching blogs and forums for the solution. 

I has so much work to do on my computer. Please somebody help me fix the issue.

---

