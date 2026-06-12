---
title: "Seagate Freeagent Trouble"
date: 2008-06-12
forum: Hardware
---

### Post by fivezerofour on 2008-06-12
I am having some trouble with my external HDD. up until today it was working very well, formatted ext3 and recognized every time in my new hardy install. I have some very valuable data on this drive and would like to get it working again...  so here's the trouble, when I plug it in (USB2.0) nothing happens on the computer, but the HDD light comes on on the drive, lsusb shows that it is not recognized ( the result is the same with the drive plugged in as unplugged), and when I "tail -f /var/log/syslog" unplug and plug it in nothing is printed. the USB cable works, as I get some information in syslog when I use the same cable to connect my motorola phone (as with lsusb)

the drive is a seagate freeagent desktop 500gb

any ideas about how to get my drive up and running again?

---

