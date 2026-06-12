---
title: "Site tooo slow in Ubuntu - fast in Windows, Red Hat, etc."
date: 2008-11-10
forum: General Help
---

### Post by amador on 2008-11-10
Hello.

I've trying to figure out what's going wrong with a site we have deployed on internet.

The url is [http://www.bolsatecnologia.pt](http://www.bolsatecnologia.pt)

With Ubuntu the site takes about 15 minutes or more to load, but in Windows, Red-Hat, Leopard, etc, it takes just a few seconds to load.
The network configuration is the same in all machines.

This site was deployed in Tomcat in a Host container, in a Windows 2003 Server.

---

### Post by dribeas on 2009-04-01
> **amador said:**
> 
With Ubuntu the site takes about 15 minutes or more to load, but in Windows, Red-Hat, Leopard, etc, it takes just a few seconds to load.
The network configuration is the same in all machines.


I have deployed a JSPWiki 2.8 on a freshly installed ubuntu 8.10 with tomcat6 (launched with jsvc) with java alternative pointing to java-6-openjdk and the system is really slow.

---

### Post by FluffyElmo on 2009-04-01
It seems to load quickly enough here. There are a number of css errors in Firefox though that are not present in Safari. Check *Tools->Error Console * in Firefox to see the specific issues. You can try another browser like Opera on Ubuntu as well to to get an idea if it is an underlying network issue or a client side browser issue.

You should install the Firefox plug-in *Firebug* to help diagnose client side issues, it has a JS debugger among other tools. The Firefox plug-in *YSlow* help diagnose server issues, it lists all the files fetched by the page with request times, redirects and other metrics.

I don't have the time  to look very closely myself but maybe this will give you a place to start if you haven't solved the problem already. Good Luck!

---

### Post by TenPlus1 on 2009-04-01
Loaded in 6 seconds here... Opera 10 baybee...

---

