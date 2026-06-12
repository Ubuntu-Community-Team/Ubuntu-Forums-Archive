---
title: "Ubuntu Wireless nework problem"
date: 2009-01-09
forum: Hardware
---

### Post by Taiki on 2009-01-09
So just recently I installed Ubuntu. When I tried to connect to the Internet, It couldn't find any networks.

Its probably some compatibility problem, but is there a way to fix this?

My computer is the HP Pavilion tx2510ca

And my network card is the Broadcom 4321AG 802.11a/b/g/draft-n Wi-Fi Adapter

---

### Post by Piro24 on 2009-01-09
Check to see if the driver you are running is indeed the driver for your card. 

If so, try moving closer to the router, the driver may not be totally complete, and so might make the usability of the card a bit lower.

I know this is recommended way too often, but if that fails, try using Ndiswrapper.

---

### Post by jdelasalas on 2009-01-09
Are you already using ndiswrapper?

---

### Post by Taiki on 2009-01-10
I don't have Ndiswrapper, so I'm getting it now.

Does it need to be installed in Ubuntu?

And how do I install this?

---

### Post by jdelasalas on 2009-01-10
you can get ndiswrapper by sudo apt-get install ndiswrapper-common

then you will need to locate your windows driver to do the rest

---

### Post by Taiki on 2009-01-10
OK, I got everything installed by reading [this]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper"), but I'm stuck from step 3 on.

When I try to add blacklist bcm43xx, blacklist b43, blacklist b43legacy and blacklist ssb to the end of the file, I save and it says I don't have permission. How do I get past this?

---

### Post by jdelasalas on 2009-01-11
you would have to do stuff in terminal as   sudo in order to have the proper permissions

---

### Post by Taiki on 2009-01-11
Could you tell me the exact things to type?

---

### Post by fmonson on 2009-01-11
I'm new to this Forum, so I don't know any other way to navigate within this site.  

[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)

Broadcom does not have as good a rep as Linksys, and Linksys is just so-so.

I have reloaded 8.04 three times to get mine (LinkSys WMP54G) right after the initial kernel update/upgrades (16-23).

So far this one is OK, but on the 3rd reboot I had to reconnect to my router. 

BTW, I recommend that you set your router to broadcast, if that is off.

Hope this little bit helps.  Not much I suspect.

---

### Post by Taiki on 2009-01-14
I was hoping that would work, but it didn't.

---

