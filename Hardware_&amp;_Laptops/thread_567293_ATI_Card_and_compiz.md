---
title: "ATI Card and compiz"
date: 2007-10-04
forum: Hardware &amp; Laptops
---

### Post by tanman on 2007-10-04
I am wondering if I could get some opinions on a ATI card vs Nvidea. I have been using a Nvidea 6600 with Gutsy Gibbons and everyhting was great! Just recently though the fan on the card has gotten really loud (I have taken it out and tried cleaning it). Anyway I decided to get a 8500GT card, but when I went to pick one up they were out, but the salesmen said he used a ATI 1650xpro with Ubuntu and it worked fine plus it had dual monitor support so I went with it. The installation went fine and I can get the right resolution's, but when I go to enable desktop effects I get a error that composite is not installed. I can not even enable basic effects. When I open screen graphics that card has a fgxl, I think, driver installed. I am at work and not by the computer. Is there something I am missing or should I just take the card back and go with another Nvidea card. I am finding through the forums that ATI is still giving some users problem. By the way I reinstalled the 6600 and everything is back to normal with my advance desktop effects, but the noise from the fan is driving me crazy. Would a clean install help with the ATI card
Also when installing the cards I have reconfigured my xorg manually
Thanks for any input.

---

### Post by tanman on 2007-10-04
Well the more digging I do it seems that ATI, as of now anyway, is having some issues with open drivers and that one should stick with Nvidea.

---

### Post by kellemes on 2007-10-04
I'm using the ATI x1650pro AGP without problems..
You need to use fglrx + xgl to get it working.. it's not as hard as it looks..
[http://ubuntuforums.org/showthread.php?t=488385]("http://ubuntuforums.org/showthread.php?t=488385")
[https://help.ubuntu.com/community/BinaryDriverHowto]("https://help.ubuntu.com/community/BinaryDriverHowto")

If you get stuck please post /etc/xorg.conf **and** /var/log/Xorg.0.log (after a failed X-session)
Since I have the same card surely I can help..

---

### Post by tanman on 2007-10-04
If I have time tonight I will switch out cards again and see if I can get compize working. The thing I did like about the Nvidea card is that it just worked. When I go to recongigure my xorg should I pick the defaults?
Thanks.

---

