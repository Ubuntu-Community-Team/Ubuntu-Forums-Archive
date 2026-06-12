---
title: "Setting a mandatory system-wide proxy"
date: 2008-08-08
forum: General Help
---

### Post by mssever on 2008-08-08
I want to run all HTTP connections through a proxy for filtering purposes. This should apply to all users and should not be possible to circumvent. This appears to be more difficult than I'd imagined.

I set up the proxy in gconf and marked the affected keys as mandatory. Here's what I have: ```
system/http_proxy/host: localhost
/system/http_proxy/ignore_hosts: [localhost,127.0.0.8/8,*.local,192.168.0.0/24]
/system/http_proxy/port: 8080
/system/http_proxy/use_http_proxy: true
/system/proxy/secure_host: localhost
/system/proxy/secure_port: 8080
```
The environment variables are getting set--at least in the terminal: ```
~:$ env | grep proxy
http_proxy=http://localhost:8080/
no_proxy=localhost,127.0.0.0/8,*.local,192.168.0.0/24
```

However, my logs show that these settings are followed by apt and the weather applet, but nothing else. Epiphany has no separate proxy settings, so I can't imagine why it won't follow gconf.

To make matters more difficult, what about browsers that don't check gconf for proxy settings? How can I set that? I want to configure things so that only root can bypass the proxy (barring tunnelling or something like that).

As a special exception, I want apt to use my apt-cacher proxy.

Any suggestions as to what I'm doing wrong, and how to further lock down the system?

---

### Post by mssever on 2008-08-11
bump

---

### Post by mattdee on 2010-04-02
I'm trying the same thing...but when I do my network is unaccessable...


# Set the Proxy for Network
gconftool-2 --type string --set /system/proxy/mode  "manual"
gconftool-2 --type boolean --set /system/http_proxy/use_http_proxy  1
gconftool-2 --type boolean --set /system/http_proxy/use_same_proxy  1
gconftool-2 --type string --set /system/http_proxy/host www-proxy.com
gconftool-2 --type int --set /system/http_proxy/port 80


Anyone have any ideas???

---

### Post by dcstar on 2010-04-03
> **mattdee said:**
> I'm trying the same thing...but when I do my network is unaccessable...


# Set the Proxy for Network
gconftool-2 --type string --set /system/proxy/mode  "manual"
gconftool-2 --type boolean --set /system/http_proxy/use_http_proxy  1
gconftool-2 --type boolean --set /system/http_proxy/use_same_proxy  1
gconftool-2 --type string --set /system/http_proxy/host www-proxy.com
gconftool-2 --type int --set /system/http_proxy/port 80


Anyone have any ideas???

In this context a proxy is an internal IP address used for external access, not an external destination.

---

