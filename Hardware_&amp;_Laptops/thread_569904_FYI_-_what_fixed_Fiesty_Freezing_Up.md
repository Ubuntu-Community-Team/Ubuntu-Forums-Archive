---
title: "FYI - what fixed Fiesty Freezing Up"
date: 2007-10-07
forum: Hardware &amp; Laptops
---

### Post by gambothell on 2007-10-07
I am running wireless on an old AMD Athlon XP 1800+ using a Belkin 802.11g wireless adapter. All Ubuntu updates are current and my nVidia driver is the current Linux driver 100.14.19. Ubuntu would freeze up periodically. At first I thought is was Firefox, but I later noticed that it would freeze during a screen saver. I turned on message logging using:

  # tail -f /var/log/messages

After the next lock up and reboot, I read the messages log under /var/log/messages and found that the system was locking up with the following:

Oct  7 13:16:43 UbuntuGame dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain

I found this real interesting since I do not even have an RJ11 jack on the computer. That is why I am running wireless. In addition, what is this rehat comment? 

What fixed the problem for me was editing the interfaces file under /etc/network/interfaces. I removed all the eth0, eth1, etc. sections from the list and saved the file. Remember, for us beginners, you must be in administrator to do this. I used sudo gedit /etc/network/interfaces to accomplish this. After rebooting, I was able to go to sites successfully that used to freeze up, like logging on on the ubuntu/forums page....

I hope this helps

---

### Post by vambo on 2007-10-07
That sounds like a bloody well done =D>

---

### Post by corney91 on 2007-10-07
Also, well done from me too :)

But remember:
```
gksudo gedit
```
not
```
sudo gedit
```
;)

---

