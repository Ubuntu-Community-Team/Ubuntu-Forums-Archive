---
title: "Another Broadcom Problem"
date: 2006-11-08
forum: Hardware &amp; Laptops
---

### Post by JediElf on 2006-11-08
I just downloaded Ubuntu 6.10 - the Edgy Eft and I am having problems with my Broadcom Wireless Card.  I did the whole NDISWRAPPER thing...didn't                 work.  I did the bcm43xx-fwcutter thing too...sorta worked.  If I run a iwlist ethX scan, it brings up all the wireless networks in the building, including mine.   I installed the network manager, but it only recognizes the wired network.  Even when I reboot and unplug the cable.  I know this may have been posted on already, but I couldn't find it.  Thanks for the help.

---

### Post by slynki on 2006-11-08
I've been fighting with same problem since the Edgy release. I've got a bcm4318 card if I remember correctly. I am away from my lappy at the moment.

---

### Post by DannyG on 2006-11-08
I had the same problems with my BCM4318, but found [this giude]("http://www.ubuntuforums.org/showthread.php?t=190177&highlight=kind+sir") did the job perfectly.

I think the main problem with the BCM43** range ndiswrapper is the choice of drivers you use, so make sure you use the ones that are linked to in that guide.

Also, make sure you remove all your previous ndiswrapper settings and configurations and are starting from scratch.

The only problem i've had after using this guide is an error that occassionaly occurs with the Network Manager, it doesn't stop the Wirless working but you can't view the Network Status. To fix this I just removed that Network Manager and added the one that you get when you click "Add to Panel" and it works perfectly.

---

### Post by JediElf on 2006-11-08
Thanks for the tips guys.  I ended up just re-installing Ubuntu (I figured I must have messed something up in my previous wireless attempts) and then did []("http://ubuntuforums.org/showthread.php?t=185174&highlight=broadcom")this tutorial.  It worked, although I am stuck to 802.11b.  But b is better than nothing  and my internet speed is only 6Mb/s anyways ;)

---

### Post by DannyG on 2006-11-08
Until Linux hits the mainstream a bit more, we're all gonna have to do with wrapper programs and tweaking drivers.

Still, slow wireless is better than no wireless at all.

Daniel.

---

