---
title: "Wireless card, please help"
date: 2006-03-23
forum: Hardware &amp; Laptops
---

### Post by krypto_wizard on 2006-03-23
I have a DELL latitude 110L. The wireless card is 

Dell Wireless 1470 Dual Band WLAN Mini-PCI Card

Ubuntu doesn't detect the wireless card.

Please help.


Every help is greatly appreciated.

Thanks

---

### Post by krypto_wizard on 2006-03-23
Please help to configure this wlan card.

---

### Post by krypto_wizard on 2006-03-26
Please help

---

### Post by Titus A Duxass on 2006-03-26
Try searching the forum, there are literally hundreds of threads with wireless as the subject.  Help yourself to help yourself.

---

### Post by Sendervictorius on 2006-03-26
I suggest you start by taking a look at this:
[https://wiki.ubuntu.com/WifiDocs](https://wiki.ubuntu.com/WifiDocs)

---

### Post by krypto_wizard on 2006-03-26
I tried ndiswrapper very thoroughly but with no success.

I think its not worth the time, one should wireless cards which are well linux supported.

---

### Post by Titus A Duxass on 2006-03-26
If you follow the howto (see link from sendervictorius) there's a good chance that it will work.

Have you checked that your card is support or is compatible with ndiswrapper?

Have you do anything to help yourself or are you depending on the good nature of the folks here to baby walk you through it!

---

### Post by krypto_wizard on 2006-03-26
I did both.

My card is supported as written in the ndiswrapper wiki. They wrote that it worked well with Fedora. I am now running Dapper. I tried given everything given in the WiFiDoc as well as ndiswrapper.

Don't make harsh comments..okay ? I am posting my queries only after researching and trying. I am a new convert to linux like less than a year.



[QUOTE=Titus A Duxass]If you follow the howto (see link from sendervictorius) there's a good chance that it will work.

Have you checked that your card is support or is compatible with ndiswrapper?

Have you do anything to help yourself or are you depending on the good nature of the folks here to baby walk you through it![/QUOTE]

---

### Post by Titus A Duxass on 2006-03-26
I think you may be giving yourself problems running dapper.

Try running breezy instead.

Harsh comments, what harsh comments?

---

### Post by krypto_wizard on 2006-03-26
"Have you do anything to help yourself or are you depending on the good nature of the folks here to baby walk you through it!"



[QUOTE=Titus A Duxass]I think you may be giving yourself problems running dapper.

Try running breezy instead.

Harsh comments, what harsh comments?[/QUOTE]

---

### Post by Mr Squiddy on 2006-03-26
[QUOTE=Titus A Duxass]I think you may be giving yourself problems running dapper.

Try running breezy instead.[/QUOTE]

I agree.  There have been reported instances of Dapper breaking wlans which worked OK in Breezy.

I am using the 1370 card in a Dell Inspiron 1300 and it works fine but it took me four evenings to get it working.  Try using different driver files.  I could not get mine to work using the Dell-supplied Broadcom drivers (bcmwl5.sys etc).  In the end I used one from the Acer site and it worked fine.

I also found it useful to have a second PC connected to my wireless access point so that when I did manage to connect wirelessly I could see it in the AP configuration screen.

Are you using WEP or WPA?  Whilst you ought to use WPA in the long term you will find it easier to try to get it working using WEP first as it is much simpler.

Finally, I discovered I had to turn SSID broadcasting on my AP to 'on' before it would work.

Sorry for the unstructured brain dump.

---

### Post by krypto_wizard on 2006-03-27
Thanks, I will try that.

[QUOTE=Mr Squiddy]I agree.  There have been reported instances of Dapper breaking wlans which worked OK in Breezy.

I am using the 1370 card in a Dell Inspiron 1300 and it works fine but it took me four evenings to get it working.  Try using different driver files.  I could not get mine to work using the Dell-supplied Broadcom drivers (bcmwl5.sys etc).  In the end I used one from the Acer site and it worked fine.

I also found it useful to have a second PC connected to my wireless access point so that when I did manage to connect wirelessly I could see it in the AP configuration screen.

Are you using WEP or WPA?  Whilst you ought to use WPA in the long term you will find it easier to try to get it working using WEP first as it is much simpler.

Finally, I discovered I had to turn SSID broadcasting on my AP to 'on' before it would work.

Sorry for the unstructured brain dump.[/QUOTE]

[QUOTE=krypto_wizard]I used gnome Ubuntu and remote desktop was working fine. But eversince I have switched to Kubuntu it doesn't work while I am on Kubuntu box at office.

Do I have start any particular daemon ?


Please help[/QUOTE]

---

