---
title: "asus eee 901 - ubuntu eee crashes on enabling wlan"
date: 2008-09-24
forum: Hardware
---

### Post by michielr on 2008-09-24
Hi there,

I've just done a fresh install of ubuntu eee ([http://ubuntu-eee.com/](http://ubuntu-eee.com/)) 8.04.1. I've done adjustments, yet have some serious trouble with wlan.

If I enable from the BIOS, i can't login - it freezes somewhere during startup (can't move the mouse). If I disable it I can login, use the OS etc. except that it will crash when enabling the wlan using Fn+F2.

From what I can see from my syslog is that upn enabling the wlan (after login) is that a driver is being loaded, hal finds a new device, 'now managing wirless device ra0' and then - "deactivating ra0". 

As I've changed my /var/log to tmpfs I have a screenshot here: [http://home.react.nl/~michiel/misc/eee-wlan.jpg](http://home.react.nl/~michiel/misc/eee-wlan.jpg)

Can anyone help out what I have to do to fix this?

---

### Post by Pan007 on 2008-10-29
I got the same problem as you.

Someone told me that ubuntu eee's newest version supported 901, but it looks like it doesn't. 

I'm going to trash this piece of ****.....
(really hate it when it states that everything works, then it doesn't)

I'll stick with a clean debian......

---

