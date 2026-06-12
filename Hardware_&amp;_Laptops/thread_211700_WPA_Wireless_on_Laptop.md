---
title: "WPA Wireless on Laptop"
date: 2006-07-08
forum: Hardware &amp; Laptops
---

### Post by mech7 on 2006-07-08
[-o< How can i get this working? I only have an option to put in a WEP key which is well totally useless lol :)

ps:
Also is there a SecureW2 client for ubuntu as I need that for school :-s

---

### Post by sylverwing on 2006-07-08
here is more information on the subject

[http://www.ubuntuforums.org/showthread.php?t=125150&highlight=networkmanager](http://www.ubuntuforums.org/showthread.php?t=125150&highlight=networkmanager)

on SecureW2 I can't help you

---

### Post by mech7 on 2006-07-08
hmm I installed that.. and i got some sort of 2 small computer screens on the right top I think that it is that :s as there are no new programs :| 

Anyways.. when I click on it it only says no wired connection nothing about wireless :-s Been trying for a couple of hours now.

I found some pages saying i need to edit a .conf file somewhere but they are all very unclear :mad:

---

### Post by sylverwing on 2006-07-08
try this; comment (put a "#" in front) al your devices except for the "lo"

Edit: *sudo gedit /etc/network/interfaces*

like this:

```
auto lo
iface lo inet loopback


#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet static
#address xxx.xxx.x.x
#netmask 255.255.255.0
#gateway xxx.xxx.x.x
#wireless-essid USR5461
#wireless-key s:xxxxxxxxxxx

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp
```

---

### Post by mech7 on 2006-07-09
Ok i did this (bitch to open and edit as root btw) there was only one from my wireless and then it just adds it again?

And when i click on tje 2 screens on the right it just says wired again which cant be selected :mad:

---

### Post by mech7 on 2006-07-09
Is this little screen of 2 windows really the network manager? How can i check if it's really running it is instaled and even reinstalled :|

---

### Post by Firetech on 2006-07-10
> **mech7 said:**
> Ok i did this (bitch to open and edit as root btw) there was only one from my wireless and then it just adds it again?

And when i click on tje 2 screens on the right it just says wired again which cant be selected :mad:

Try rebooting after making that edit. That worked for me, anyway.

---

