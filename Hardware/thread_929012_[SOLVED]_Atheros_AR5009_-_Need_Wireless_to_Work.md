---
title: "[SOLVED] Atheros AR5009 - Need Wireless to Work"
date: 2008-09-24
forum: Hardware
---

### Post by Vakman on 2008-09-24
[http://www.bestbuy.ca/catalog/proddetail.asp?sku_id=0926INGFS10108501&logon=&langid=EN&test_cookie=1](http://www.bestbuy.ca/catalog/proddetail.asp?sku_id=0926INGFS10108501&logon=&langid=EN&test_cookie=1) <--- Is the laptop that I have.
I have had Linux Mint 5 on it as well as Ubuntu 8.04. I didn't try 7.10 yet which also solved issues I had on my desktop before (not wireless other problems). Anyway, I need wireless to work on this. Network Manager does not detect any networks, I also tried using Wifi Radar (downloaded it on my desktop, transfered to laptop with Flash drive) and it didn't find any either. I have no problem connecting to wireless on Windows or through my Nintendo Wii. Also I can't even seem to get a Wired connection to work. When I have everything I need entered into the Network Manager for the Wired it won't let me use it and goes to Wired Roaming Mode. Anyway Wireless is all I need anyway really, Wired can be solved later. The sooner the better, thanks :)

---

### Post by Vakman on 2008-09-24
I am guessing this means nobody has a clue. Ubuntu 7.10 did not help things AND sound does not work on it. And in Linux Mint 5 I found no networks. Does anybody know? If it helps, I have to add ''all_generic_ide'' to the boot options to boot into any Linux distro I have tried on this laptop. I don't know what it does, Google helped me. Anyway... Wireless help please.

---

### Post by Vakman on 2008-09-24
I found the solution through Google and other... took me all night but it probably will work. I am allowed to access wireless networks now. In /etc/modules add 
```
ath9k
```
after installed a driver. compat-wireless-ath9k-2.6.24-19-generic_20080806-mactel1_i386.deb is what you will need to download and install. Bye.

---

