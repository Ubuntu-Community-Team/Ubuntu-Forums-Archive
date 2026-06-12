---
title: "How to AVOID using proxy connection when I use apt-get ?"
date: 2008-09-29
forum: General Help
---

### Post by LlmL on 2008-09-29
Students in my college uses http proxy to connect to Internet. So I set the proxy in System | Preferences | Network Proxy. It works. APT works well too(through the proxy).
But now I'm back home. I need not to use proxy. So I fixed that setting to the default(Direct Internet connection), but APT still tries to connect to the proxy, of cause failed.
I cleared apt.conf in directory /ect/apt, but apt still tries to connect to proxy. I don't know why...
How can I avoid using proxy?

---

### Post by Elfy on 2008-09-29
Not completely sure but what is set in synaptic (System > Admin) preferences - network - is that still looking for a proxy or is it set to direct connection to

---

### Post by LlmL on 2008-09-29
Not using proxy.
I've checked that...

I mean that configuration is set not to use proxy, but apt still looks for proxy.

---

### Post by LlmL on 2008-09-30
OK, I've found the reason. In my export list I see the followings three items:
declare -x ftp_proxy="ftp://sproxy.nju.edu.cn:8080/"
declare -x http_proxy="http://sproxy.nju.edu.cn:8080/"
declare -x https_proxy="https://sproxy.nju.edu.cn:8080/"

I rebooted the computer, and they still exist.
I wounder when & where are they set by *exprot*?

---

### Post by Elfy on 2008-09-30
I have no idea why, never looked into proxies too much tbh. I probably wouldn't have posted either if I thought you'd checked in synaptic.

Then I forgot about you :(

Glad you got it sorted.

---

### Post by LlmL on 2008-09-30
Thanks anyway.

---

### Post by pervin on 2011-03-26
im a ubuntu 9.04 user..
im using a proxy server connection to access internet..i could not update my ubuntu because of the proxy..can some1 help me to get rid this problem??whenever i want to update it shows message that we failed to fetch data..apt does not pass through the proxy.and i cannot install any application from synaptic package manager and my update manager is not running..

---

