---
title: "apt and a web proxy"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by charles.gretton on 2009-01-05
Hi All,

At work I have to use a web proxy. For 8.10, how do I notify apt of the details of this? -- Incidentally, I have already added an apt.conf file to /etc/apt/ containing the text:

ACQUIRE {
http::proxy "http://servername:port/"
}

cheers,
Charles

---

