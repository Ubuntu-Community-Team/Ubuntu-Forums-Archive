---
title: "Replacement For  Intel 3945abg (dell 640m)"
date: 2008-05-18
forum: Hardware
---

### Post by kg87 on 2008-05-18
Just a quick query really, 

Im looking for a replacement for the standard intel card for my laptop. Im going on the assumption that the Dell 640m utilises MiniPCI

Im looking for an atheros based chipset (for use with backtrack/Aircrack etc) and stumbled upon the _AR5006XS_

Will this card be compat with my laptop, also, is there any problems/issues with using this card with Hardy? 

the link is to the place i intend to buy it. 
[Wireless Card link]("http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=180242753639&mpt=1211120531420&tGUID=cacae89c1190a09c13c45384fff3e357")

Thanks in advance.

---

### Post by EXCiD3 on 2008-05-18
Should work just fine with the madwifi driver according to: [http://madwifi.org/wiki/Compatibility/Atheros](http://madwifi.org/wiki/Compatibility/Atheros)

A fellow community member has written a script to make installation of the madwifi driver easy for anyone: [http://ubuntuforums.org/showthread.php?t=798485](http://ubuntuforums.org/showthread.php?t=798485)

---

### Post by kg87 on 2008-05-18
Ah, I didnt read the Spec correctly, The Dell uses miniPCI-E, not mini PC.

[update purchase details!]("http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=300223897389&mpt=1211129417939&tGUID=cacae89c1190a09c13c45384fff3e357")

How about that 1?

---

### Post by EXCiD3 on 2008-05-18
I checked the compatibility site again and says it works perfect with madwifi 0.9.3.1 on a recent kernel. :)

---

### Post by starcannon on 2008-05-18
Intel 3945abg we use that card in an HP dv2600 and a dell 1420n, it works flawlessly out of the box with both 7.10 gutsy, and 8.04 hardy. I am thinking you have some other issue? not sure changing from one excellent card to another is going to fix you or not.

---

### Post by EXCiD3 on 2008-05-18
I also have the 3945 and it works great except the connections can be somewhat flaky at times and the light doesnt come on by default. There are still a few issues but they arent noticeable to most users. I like it just fine, but if he wants to upgrade, go for it!

---

