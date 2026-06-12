---
title: "Asus netbook, &quot;download the backports&quot;?"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by Kansasguy on 2009-08-13
Noob to Linux, have loaded 9.04 on an ASUS eee 1005ha via a USB image, it works fine, but there is a known bug with wireed and wireless connection listed below from:

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%201005HA](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%201005HA)

I don't know how to:
"download the backports .deb file to a usb stick and manually install it to get it working."

Thanks in advance for any help.   ht

******************

Asus Eee 1005HA

Tested with 9.04 NBR. Wireless (Atheros AR9285) doesn't work out of the box. The ath9k module which is supplied by default doesn't seem to work correctly. You have to download the backports .deb file to a usb stick and manually install it to get it working.

Wired nic (atl1e) doesn't work out of the box either. You have to download the sourcefile from the manufactorers page and install it. It's described in Ubuntuforums posting: [http://ubuntuforums.org/showpost.php?p=7525735&postcount=2](http://ubuntuforums.org/showpost.php?p=7525735&postcount=2)

lspci output for networking:

user@MiniME:~$ lspci
01:00.0 Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by dudeman69 on 2009-10-23
I have the same problem, can somebody please help?

---

### Post by Kansasguy on 2009-10-23
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%201005HA](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%201005HA)


[http://ubuntuforums.org/showpost.php?p=7525735&postcount=2](http://ubuntuforums.org/showpost.php?p=7525735&postcount=2)


If I remember right, the following link expressed it the best.  If you still can't do it, I'll try to get back to you.

[http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/](http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/)

---

### Post by dudeman69 on 2009-10-23
Jesus flipping christ.

I feel like I have jumped into a 30ft pool without knowing how to swim.

This has been my first experience with Linux and the most frustrating thing I have ever   encountered on a computer.


It has taken me **3 days** to get internet access with Ubuntu and the first thing I am working on now is finding out how to get windows back on my netbook.

As I am sitting here typing this my cursor is jumping all over this message post as if to throw salt into my wounds.

Ubuntu is just not for me. Thanks for the massive headache.

---

### Post by dudeman69 on 2009-10-23
oh and thanks kansusguy, that worked =)

---

