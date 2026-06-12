---
title: "Cannot connect Dell D610 laptop wifi with Ubuntu v11.04"
date: 2011-06-12
forum: Hardware
---

### Post by London User on 2011-06-12
Hi everyone - new user here,

I recently switched over a home desktop PC and laptop computer to Ubuntu (v11.04) from XP and love it for both.

Unfortunately, I've got an unresolvable issue connecting the laptop (Dell Latitude D610) to the home wifi network. The laptop broadband can be connected via an ethernet cable but not the wifi. I've searched the forums for answers and have downloaded and installed the b43 driver which enabled the router to recognize the laptop wirelessly. I just can't seem to actually use the Internet. I've got a double 'no' for hard and soft blocked.

Any ideas anyone? I read the great exchange between chili555 and Dom/djavet and tried some of those suggestions but I think Dom's issue may be different from mine although I'm not sure < [http://ubuntuforums.org/showthread.php?t=1773198&highlight=dell+d610+wifi](http://ubuntuforums.org/showthread.php?t=1773198&highlight=dell+d610+wifi) >.

Thanks in advance for any assistance!

Christopher

FYI:

christopher@D610:~$ lspci -nn | grep -i 14e4
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
03:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

and

christopher@D610:~$ lsmod | grep -e b43 -e ssb -e wl
b43                   296610  0 
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
ssb                    45942  1 b43

---

### Post by mörgæs on 2011-06-12
I have a D 610, and wirefree worked out of the box with Ubuntu 10.10 and Xubuntu 11.04. Since it worked by itself I can not tell you what I did, but if you want to 'have a look', you are welcome.

Else I guess best is to post in the other thread. Seems to be given first class advice there.

---

### Post by webofunni on 2011-06-12
What is the o/p of 

```

ls -l /sys/class/net/

```

---

### Post by London User on 2011-06-12
christopher@D610:~$ ls -l /sys/class/net/
total 0
lrwxrwxrwx 1 root root 0 2011-06-12 09:03 eth0 -> ../../devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth0
lrwxrwxrwx 1 root root 0 2011-06-12 09:03 lo -> ../../devices/virtual/net/lo
lrwxrwxrwx 1 root root 0 2011-06-12 09:03 wlan0 -> ../../devices/pci0000:00/0000:00:1e.0/0000:03:03.0/ssb0:0/net/wlan0

---

### Post by webofunni on 2011-06-12
system is able to detect your wireless card. Usually at the top right corner of the screen there will be a network icon. click on that and see, if you are able to see the wireless networks

---

### Post by London User on 2011-06-12
Yes - thanks, but that is not the issue here. My laptop recognizes and connects to the home WiFi (and recognizes others WiFi signals in the area) but my laptop won't connect and allow 'surfing' of the web. What could I do to 'connect' that final step?

Thanks again!

---

### Post by London User on 2011-06-13
Hi Everyone,

I'm going to end this post and try a different one as I think this one has run its course.

Thanks for all the help so far!

C

---

### Post by webofunni on 2011-06-13
What is the network status after you connect to the wifi network. Connect to the wifi network and execute 

```

ifconfig
iwconfig
route -n

```

---

