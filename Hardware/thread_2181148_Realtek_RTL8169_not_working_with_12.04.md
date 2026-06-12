---
title: "Realtek RTL8169 not working with 12.04"
date: 2013-10-16
forum: Hardware
---

### Post by zaoka on 2013-10-16
I have TP-LINK TG-3269 card that is using RTL8169 SC chip, I can see this card with ifconfig -a its listed as eth0 however, it does not work.
I am using latest 12.04 Server.

I tried power off PC, unplug cable fro the card for 15 seconds, turned back on, it does not work.

I have seen this card making problems with older Ubuntu distros, was that problem fixed or I am dealing with some other problem?

(PA: card is brand new)

---

### Post by zaoka on 2013-10-16
Was not driver issue, had to do this:

```
1) deleting a file: sudo rm /etc/udev/rules.d/70-persistent-net.rules
 2) reboot
```

found here
[http://www.linuxquestions.org/questions/linux-server-73/does-a-new-nic-need-to-be-manually-configured-in-ubuntu-server-643580/](http://www.linuxquestions.org/questions/linux-server-73/does-a-new-nic-need-to-be-manually-configured-in-ubuntu-server-643580/)

---

### Post by mastermindg on 2014-03-09
In 13.10 this file is re-created. There are instances of R8169 in that file.

---

