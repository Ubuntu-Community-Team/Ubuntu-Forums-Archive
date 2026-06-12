---
title: "Canon LBP6000 not printing"
date: 2011-10-22
forum: Hardware
---

### Post by yendorian on 2011-10-22
I have a canon lbp6000 printer which has been working well for six months in 11.04 but after an update to 11.10 I can not get it to work.

I have been to the canon site and downloaded the CAPT driver version 2.20 installed but doesn't work ver 2.23 will not install has an error message : dependency is not satisfiable : gs-esp:     confused:

---

### Post by Alekamos on 2011-11-25
i got the same problem,keep an eye on this thread:
[http://ubuntuforums.org/showthread.php?t=1701975](http://ubuntuforums.org/showthread.php?t=1701975)

---

### Post by nicky75 on 2011-11-27
I succeeded with great difficulty, but I do not remember exactly the steps. First I downloaded the latest drivers 2.30 from the malaysian Canon website, then I downloaded the script to install the drivers from the site radu cotescu modifying the script so that it was using the latest drivers (just change the name), then I downloaded from the site Ubuntu gs-esp package as required by canon driver and given that no longer exists in the latest version 11.10 since been replaced by ghostscript, so I started the script and I installed the Canon drivers. Finally I gave: "sudo modprobe usblp" and then: "sudo /etc/init.d/ccpd restart". I use in printer only lbp6000.

---

### Post by ppqq on 2012-03-17
I'm also trying an lbp6000! if only I'd known about Canons, they just look better made than HP's though.

it kind of doesn't get a usb connection with the ubuntu community method or radu's bash script -I can unplug it and it still marked as Idle.

sometimes when i turn on the printer it gets added automatically,  but still doesn't print.

I'm at the point of smashing it up but might try to sell it...
I'm with xubuntu 64bit, next to try with debian squeeze

my work-flow is here
[https://sites.google.com/site/xubuntuinstallhowto/canon-printer-setup]("https://sites.google.com/site/xubuntuinstallhowto/canon-printer-setup")

---

