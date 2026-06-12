---
title: "Wireless problems"
date: 2005-07-04
forum: Hardware &amp; Laptops
---

### Post by brim4brim on 2005-07-04
Hi,

I keep loosing my network connection.  It works fine but if I don't use it for a while cuts out and won't come back on until I restart.

I'm using a Dell Latitude D810 with Intel wireless card.

Anyway I was wondering if anyone could help out.

---

### Post by Seti on 2005-07-04
Could it have something to do with your access-point/wireless router? I recently had a D-Link router die on me and was having the same thing happening on our LAN. Have you noticed it taking a long time to load web pages also? Just a suggestion.

---

### Post by brim4brim on 2005-07-04
[QUOTE=Seti]Could it have something to do with your access-point/wireless router? I recently had a D-Link router die on me and was having the same thing happening on our LAN. Have you noticed it taking a long time to load web pages also? Just a suggestion.[/QUOTE]

Thanks, sometimes it takes a long time for websites to load as it has trouble connecting to the website or waiting for responses but most of the time it's fast.  I can't adjust anything with routers end.

I have XP installed aswell and sometimes it disconnects but XP auto reconnects.  Can I enable that in Linux.  I've been editing the /etc/pcmcia/wireless.opts file and the connections is a little more stable but if I get disconnected completely from the network I want to auto reconnect and it's just not doing it and I can't find any command to do it.

Or else the other thing I think might be causing the problem is I'm using a laptop so could the wireless card be turning off to save power or something on a timeout and if so do you know how to stop that.

---

### Post by snop on 2005-07-05
Hello,

You're probably using an intel 2200 wireless card (comes with Centrino machines) and those wireless connection drops are a known bug. Installing the new drivers fixes this issues.

Check this threads:
[http://www.ubuntuforums.org/showthread.php?t=21056](http://www.ubuntuforums.org/showthread.php?t=21056)
[http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

SnOp

---

### Post by brim4brim on 2005-07-05
[QUOTE=snop]Hello,

You're probably using an intel 2200 wireless card (comes with Centrino machines) and those wireless connection drops are a known bug. Installing the new drivers fixes this issues.

Check this threads:
[http://www.ubuntuforums.org/showthread.php?t=21056](http://www.ubuntuforums.org/showthread.php?t=21056)
[http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

SnOp[/QUOTE]

Thanks a million, it's working so far after installing the new drivers.

---

