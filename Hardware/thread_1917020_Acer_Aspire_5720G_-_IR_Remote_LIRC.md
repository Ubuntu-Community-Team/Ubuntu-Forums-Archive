---
title: "Acer Aspire 5720G - IR Remote LIRC"
date: 2012-01-29
forum: Hardware
---

### Post by benpaka on 2012-01-29
Helo,

I am trying to make the IR remote control work, but I can't find the solution.

After looking at [https://wiki.ubuntu.com/LircHowto](https://wiki.ubuntu.com/LircHowto) & [https://help.ubuntu.com/community/LIRC](https://help.ubuntu.com/community/LIRC) I have tried the following:

Try co change various remote controler (as it works well on windows I have selected the "Windows Media Center" and i have also try other models by using: ```
sudo dpkg-reconfigure lirc
```

By doing lsusb I have the following

```
~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 07ca:a310 AVerMedia Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

So I also try the 3 AverMedia remotes in the lirc configuration but still nothing.


I also try to add [http://lirc.sourceforge.net/remotes/acer/RC-802](http://lirc.sourceforge.net/remotes/acer/RC-802) to the lirc.conf but I didn't change anything. (My remote is RC-804 so it should be really similar)

when I do 
```
irw
```
 I don't have any response from the terminal if I push any button, with any of the previous configuration.


Can someone please help me? or told me which step I should check before?

---

