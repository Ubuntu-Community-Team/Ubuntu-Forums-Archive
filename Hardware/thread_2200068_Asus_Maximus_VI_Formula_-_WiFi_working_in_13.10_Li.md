---
title: "Asus Maximus VI Formula - WiFi working in 13.10 LiveCD mode, not after install though"
date: 2014-01-17
forum: Hardware
---

### Post by maxbar on 2014-01-17
Just wanted to note the above... WiFi is detected when starting Ubuntu 13.10 to install it, then once installed and restarted, not showing up.

At the top-right is the WiFi / Internet Icon, on which I clicked to edit settings and added under Wireless the SSID, encryption type and password... nothing happens then.

(I filed a bug report with above info)

Now I could use some help:

Wired connection is not really an option, but I also have Windows installed, where I have WiFi working, so I could download stuff onto my USB drive and then copy over, compile / install and run in Ubuntu. Question is though, what do I download and where, and do I have to compile anything and if so, is the software for that installed by default or if not, how do I install it?

Thanks in advance for any help!

---

### Post by varunendra on 2014-01-18
Welcome to the forums maxbar !

We can start by looking at your wifi card and the driver if loaded. Please open a terminal (Ctrl-Alt-T) and post back the output of the following command -
```
lspci -nnk | grep -iA2 net
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

