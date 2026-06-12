---
title: "Question about Proxies and Ubuntu"
date: 2008-09-18
forum: General Help
---

### Post by cod4beast on 2008-09-18
On my shop computer i installed a dual boot of ubuntu behind windows and there are a lot of blocks on the internet.  If i apply a proxy to my web browser will it also unblock sites for all the computers on that network or just my computer.  I wanted to ask because i could get kicked out if they found out i applied a proxy to every school computer?  If it will only work for mine are there any good proxies you would recommend me using.

---

### Post by iaculallad on 2008-09-18
There are plenty of Web Proxy servers available on the net, you only need to search them. Good for you that your SysAd hadn't applied URL filter settings to block URL redirectors on their network Proxy/Firewall server.

---

### Post by nitro_n2o on 2008-09-18
My understanding is that you want to unblock some websites.. 

then use this [http://www.torproject.org/](http://www.torproject.org/) it is somewhat slow, but works fine without a problem..

unless the network you are in can detect such things, which I doubt

---

### Post by cod4beast on 2008-09-18
well my system admin installed blocking software on our network and we cant get to any proxies in my shop at the tech school i go to.  So if i go to system, preferences, network proxy, and have my internet browser go through a proxy will it affect the any of the other computers on that network? or if there are any proxies that cant get blocked or something like that let me know because i own a few proxy sites and when i make a new one it gets blocked within minutes

---

### Post by nitro_n2o on 2008-09-18
that won't affect anything.. 

think of it this way 

YOU---> PROXY----> ANOTHER COMPUTER ---> INTERNET 

this is a simplified version of the proxy idea, it is just like you are accessing through a different computer... so instead of getting on the internet, you get to another computer, which in turn will take you onlie

---

### Post by cod4beast on 2008-09-18
> **nitro_n2o said:**
> that won't affect anything.. 

think of it this way 

YOU---> PROXY----> ANOTHER COMPUTER ---> INTERNET 

this is a simplified version of the proxy idea, it is just like you are accessing through a different computer... so instead of getting on the internet, you get to another computer, which in turn will take you onlie

how do i go about doing this and what if the other person is online while this is going on? sorry im being so tedious about this i dont want to get kicked out cause then i dont have any schools to go to

---

### Post by nitro_n2o on 2008-09-18
try out this website [http://anonymouse.org/](http://anonymouse.org/)

you'll find a box to enter the url you want to visit and it'll send you there.. 

you will not physically use someone's machine.. in the case of the website I sent you.. the machine hosting the website will take care of hiding your identity through some software

---

### Post by iaculallad on 2008-09-18
> **cod4beast said:**
> well my system admin installed blocking software on our network and we cant get to any proxies in my shop at the tech school i go to.  So if i go to system, preferences, network proxy, and have my internet browser go through a proxy will it affect the any of the other computers on that network? or if there are any proxies that cant get blocked or something like that let me know because i own a few proxy sites and when i make a new one it gets blocked within minutes

No, it won't affect any computers in your network, only the PC to which you configured proxy.

---

### Post by cod4beast on 2008-09-18
> **iaculallad said:**
> No, it won't affect any computers in your network, only the PC to which you configured proxy.

thanks
im going to try it then i just didnt know if it would effect every computer on the network cause then id get caught for sure

---

### Post by mb_webguy on 2008-09-18
A proxy is a computer that stands between you and the Internet.  In the case of your network, the proxy is there.  You can't do anything about that.  Changing the proxy settings on your computer will just prevent you from being able to connect to the Internet at all.

What you need is a web proxy like the one nitro_n2o suggested.  A web proxy is a web server that funnels other websites to you, so that you can view websites that would otherwise be blocked by your proxy.  As far as your proxy is concerned, you never leave the web proxy website.

---

