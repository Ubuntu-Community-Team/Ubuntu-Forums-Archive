---
title: "I think I found a few things to speed up firefox (may be just me)"
date: 2008-07-13
forum: General Help
---

### Post by jerome1232 on 2008-07-13
While I was randomly surfing today I stumbled upon this site
[https://calomel.org/firefox_ssh_proxy.html](https://calomel.org/firefox_ssh_proxy.html)

I took these steps:

(copied directly from site, note firefox 3 seemed to default to 6 so I left this alone)
An easy way to speed up Firefox is to increase the amount of parallel connections the browser makes to the server. The default is two(2). Open up Firefox and type in "about:config" in the URL. Then find the line that reads "network.http.max-persistent-connections-per-server" and change it from 2 to 4

(copied directly from site)
To enable pipelining in Firefox browser goto the url about:config . Then search for "pipe" and set "network.http.pipelining" and "network.http.proxy.pipelining" to true. Also increase "network.http.pipelining.maxrequests" from 4 to 8.

It feels like speed has improved, wouldn't mind hearing back if others find the same.

---

### Post by Bubba64 on 2008-07-13
[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

---

### Post by jerome1232 on 2008-07-13
> **Bubba64 said:**
> [http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

nice much more complete, thanks

---

### Post by Bubba64 on 2008-07-13
> **jerome1232 said:**
> nice much more complete, thanks

Works on FF3 on my desktop with no problems, there is also a add on called fasterfox.
[http://fasterfox.mozdev.org/](http://fasterfox.mozdev.org/)

---

