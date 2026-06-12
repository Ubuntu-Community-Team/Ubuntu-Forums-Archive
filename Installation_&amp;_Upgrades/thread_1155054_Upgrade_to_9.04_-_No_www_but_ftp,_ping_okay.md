---
title: "Upgrade to 9.04 - No www but ftp, ping okay"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by enrite on 2009-05-10
Hi All,

I am a newbie, having used Ubuntu for the last 6 months or so.  I just updated to 9.04 and now have issues connecting to the internet.

I can ping web sites using the network tool and connect to ftp sites but cannot connect to a web site using a browser.  Any suggestions?  I have tried some solutions mentioned in other threads but cannot solve the problem.  If I need to, I can do a fresh install of 9.04 but I'd rather see if this can be easily fixed.

Thanks,

Ian

---

### Post by andrewc6l on 2009-05-11
The first thing is to determine if you're being blocked on your box or upstream.

Try this (from a command line):

```
telnet www.google.com 80
```

If you connect, type:
```
GET /
```

If you see a response, the problem is likely with your web browser (maybe it's trying to use a proxy that's not reachable?) If not, it could be that your local firewall is blocking port 80.

---

### Post by enrite on 2009-05-11
Hi,

Thanks for your response and sorry for taking so long to get back to you. 

I fail to connect to Google through telnet.

---

### Post by andrewc6l on 2009-05-16
Ok, can you try the same thing with an IP address:

```
telnet 74.125.67.100 80
```

(That's an IP address for google.com.) If you can connect with the IP address but not the name, then your DNS config is bad - you'll need to find out what the right DNS is from your ISP. If you can't connect using IP address, I'm at a loss - since you say you can connect over web sites and ping. Maybe a firewall is blocking port 80 somewhere?

---

### Post by enrite on 2009-05-16
I can telnet to the ip address.  I actually ended up reinstalling from scratch.  I booted from CD and could browse, so I took that route.

Thanks for the suggestions, though!

Ian

---

