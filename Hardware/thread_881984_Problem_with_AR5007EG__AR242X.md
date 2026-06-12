---
title: "Problem with AR5007EG / AR242X"
date: 2008-08-06
forum: Hardware
---

### Post by eddygazilion on 2008-08-06
Hello, I have a 64 bit laptop that has an Atheros AR5007EG / AR242X wireless card, and I'm having troubles setting it up. I was able to use Ndiswrapper to get the card identified, but then I can't connect to my home network, it sees the card, but can't use it. So, I was wondering if anyone had the correct ndiswrapper .inf file for a 64 bit AR5007EG / AR242X wireless card driver. If anyone could help, that would be great!

Thanks!
-Eddy

---

### Post by dca on 2008-08-06
You're going to have to go to the manufacturer of the card's website to get that if you're using ndiswrapper.
 
For instance I have an Acer Aspire 5610z with an Ambit PCI-e (Atheros AR242x, AR5BXB63)
 
I can get the Windows drivers direct from Acer's website because I guess abit doesn't offer a place to get drivers for their products.
 
Someone might want to chime in and help because I'm not familiar with 64-bit installs, I used this for my 32bit -
[http://ubuntuforums.org/showthread.php?t=662877](http://ubuntuforums.org/showthread.php?t=662877)
 
..but I found this for 64bit
[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

---

### Post by phidia on 2008-08-06
Madwifi also supports that card in 64 bit now. The thread for madwif 64bit is [here]("http://ubuntuforums.org/showthread.php?t=816780&highlight=atheros+ar5007eg").
There is a howto for ndiswrapper for 64 bit but I can't find it right now. :(
[URL="http://ubuntuforums.org/showthread.php?t=512828&highlight=atheros+64+bit+ndiswrapper"]
This ndiswrapper howto[/URL] is for a different version but I used it on gutsy and hardy and it worked.

---

