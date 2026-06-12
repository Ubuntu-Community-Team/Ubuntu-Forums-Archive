---
title: "Firefox fails to &quot;resolve host&quot;"
date: 2005-12-06
forum: Installation &amp; Upgrades
---

### Post by ebh on 2005-12-06
I just installed Ubuntu-5.10 on an Asus M6R laptop. The install went fine without problem.

However Firefox is unable to see anything. I can ping google.com & download the page via wget. However Firefox is "unable to resolve host". What's more Firefox can not even display a local HTML file. i.e. file:///home/ebh/index.html.

I've run a quick search via Google and could not find anything. There was a thread on this forum about a year ago with the same title (I pinched it :). Yet it looks like the user was having network problems.

- Alex

---

### Post by inhetep on 2005-12-06
You might want to have a look at

[http://www.ubuntuforums.org/showthread.php?t=95350](http://www.ubuntuforums.org/showthread.php?t=95350)


especially the ipv6 stuff

---

### Post by ebh on 2005-12-07
Thanks. Changing the **network.dns.disableIPV6** setting worked.

Sorry I had not found that page when I was searching before.

- Alex

---

