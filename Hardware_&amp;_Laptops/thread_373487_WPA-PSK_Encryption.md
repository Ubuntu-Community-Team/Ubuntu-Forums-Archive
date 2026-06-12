---
title: "WPA-PSK Encryption"
date: 2007-03-01
forum: Hardware &amp; Laptops
---

### Post by pvhorne on 2007-03-01
I am very new to Ubuntu and I wanted to install it on my laptop. The install went fine but I am not able to get WPA-PSK Encryption running on my wireless card. Can someone please assist from the begining. Thanks in advance.

---

### Post by timmir on 2007-03-01
It will be much easier if you install network manager.  Connect your computer using ethernet and install network-manager-gnome using synaptic or apt-get.
```
sudo apt-get install network-manager-gnome
```

The built-in gnome network dialog only does wep.  Network Manager will do that and WPA1 and 2.

I've found that after installing network-manager it's best to comment out everything except the 'lo' interface in the /etc/interfaces file.

then either manually restart networking and start nm-applet by typing these commands:
```
sudo /etc/init.d/networking restart
```
```
nm-applet
```

let me know if you need more information or if something doesn't work.

---

### Post by pvhorne on 2007-03-03
I will try tonight. Thank you for your help.

---

### Post by kic on 2007-03-03
I've had zero luck with network manager. I checked the interfaces file and saw that only loopback and my wired connection were present. Just for kicks, I commented out the wired connection and restarted the networking, but the wireless card still refuses to connect.

I'm using WPA2 PSK on my router at the moment, and if I go through hacking the config files, I can actually get it to work. But using network manager appears to be hopeless. Any suggestions?

---

### Post by rk_misra on 2007-03-04
Network manager worked perfectly in my case.. I was having hard time configuring wpa-2 and tried lots of hack on /etc/network/interfaces files and all failed and finally when i installed network manager, it started working so thanks to the person who posted how to install network manager..

---

### Post by Fitzcarraldo on 2007-03-07
> **kic said:**
> I've had zero luck with network manager. I checked the interfaces file and saw that only loopback and my wired connection were present. Just for kicks, I commented out the wired connection and restarted the networking, but the wireless card still refuses to connect.

I'm using WPA2 PSK on my router at the moment, and if I go through hacking the config files, I can actually get it to work. But using network manager appears to be hopeless. Any suggestions?


Is the following thread of any help to you, *kic*?

[http://www.ubuntuforums.org/showthread.php?t=378179](http://www.ubuntuforums.org/showthread.php?t=378179)

---

### Post by shambotics on 2007-03-07
> **Fitzcarraldo said:**
> Is the following thread of any help to you, *kic*?

[http://www.ubuntuforums.org/showthread.php?t=378179](http://www.ubuntuforums.org/showthread.php?t=378179)

That thread helped me - thank you!

---

### Post by firedrow on 2007-03-08
I couldn't get the Gnome network manager to work with my Atheros card.  But KNetworkManager (and yes I am still using Gnome with KDE Apps) took care of it.  I use a MAC-Locked wireless in my apartment, and WPA-PSK at work. Going between the two is like windows, I just turn it on and it detects and connects.

---

### Post by TheVeech on 2007-03-08
Try this: [Enable WPA]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html")

Worked for me (on Edgy) with my Atheros card (not forgetting the restricted modules for the madwifi driver).
(Atheros Communications, Inc. AR5212 802.11abg NIC).

Let us know what you finally get working.

---

