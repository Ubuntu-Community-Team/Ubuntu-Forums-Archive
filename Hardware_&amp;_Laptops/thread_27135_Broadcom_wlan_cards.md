---
title: "Broadcom wlan cards?"
date: 2005-04-15
forum: Hardware &amp; Laptops
---

### Post by fazer on 2005-04-15
Hello,

I have a Thinkpad 600E and I was able to get the Live CD up and running after a little bit of tweaking (needed it so that my PCMCIA Ethernet card would work)

Currently, I have a Microsoft MN 720 802.11g card.  I have been trying to get it to work with Ubuntu but I have failed.  I am still deciding which driver I should use.  I was using these: [http://ankhcraft.com/drivers/mn720-ankh.zip](http://ankhcraft.com/drivers/mn720-ankh.zip)  with some success (atleast I would get wlan0) but it wouldn't get an IP assigned to it nor would it connect to my AP.  Do I have to do an OS install for it to work?

Any help would be appreciated!

Thanks.

---

### Post by accuser on 2005-04-15
Make sure you have the radio turned on. I have a wireless lan card with a broadcom chipset, and it seems to be off by default. I had to change the driver .conf file (you will find this under /etc/ndiswrapper) thus:
```

RadioState|0

```
and then everything worked fine!

---

### Post by jonny on 2005-04-15
For full instructions [read this how-to](http://ubuntuforums.org/showthread.php?t=25683).

---

### Post by fazer on 2005-04-15
[QUOTE=accuser]Make sure you have the radio turned on. I have a wireless lan card with a broadcom chipset, and it seems to be off by default. I had to change the driver .conf file (you will find this under /etc/ndiswrapper) thus:
```

RadioState|0

```
and then everything worked fine![/QUOTE]

Damn, I ran that sed command that turns it to RadioSate|0 and then modprobed it, still it doesn't work.

 ](*,)

---

### Post by fazer on 2005-04-16
Nevermind.  I was able to get it working.  The trick is to use ndiswrapper 1.1 (compiled from source).

---

