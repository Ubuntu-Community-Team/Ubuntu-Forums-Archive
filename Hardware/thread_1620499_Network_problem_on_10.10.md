---
title: "Network problem on 10.10"
date: 2010-11-13
forum: Hardware
---

### Post by PulsUA on 2010-11-13
Hello. My laptop is Asus K42, My system is Maverick. My problems are:
1. The icon of network manager on the upper panel of GNOME has disappeared. I cannot connect to Interney. How to return this icon. I used advice to delete and restore the panel of notification. But all icons are but nm.

2. How to connect to PPPoE
command sudo ppoeconf and next setting do not help. i enter my login/passwoed and press Yes. How to connect? I used FAQ on the website of my provider. ther is a answer that but it does not work. What to do?
And how can I connect to PPPoE using graphic interface like connecting to VPN? Advice please

---

### Post by dineshs on 2010-11-14
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)

---

### Post by PulsUA on 2010-11-15
There is another problem. Your replies were too late. I will try to do that another time.
But now I cannot connect to my always-working vpn. I connect LAN-cable but wired-connection is not active. And the text about networks is grey. I will switch the language while booting and will make the screenshot. YOUR IDEAS?
I do not want to return to win7... 
I reinstalled Ubuntu twice on the last week. I think it's not normal...

---

### Post by PulsUA on 2010-11-15
[IMG]http://s011.radikal.ru/i318/1011/86/5d47cc7aaed7.jpg[/IMG]

---

### Post by dineshs on 2010-11-16
Pl refer [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)
> d. Why won't Network Manager manage my Networks?
If your network connection is listed in /etc/network/interfaces, it is unavailable to NetworkManager with its default setup (read this to see how to change it to manage these connections: [http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager) ). The best option for a standard setup is to open the file using
```
sudo gedit /etc/network/interfaces 
```
and comment out (ie put a # in front of) or delete every line in the /etc/network/interfaces file except the two with lo in them- they read
```
auto lo
iface lo inet loopback
```
How do you connect VPN?Have you tried the VPN tab in Network manager?
I suggest you follow instructions in
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)
to create DSL connection and use the VPN tab in NM to configure VPN in the same way.

---

### Post by PulsUA on 2010-11-16
I have connected VPN in Network Manager but after setting pppoeconf this problem has appeared. And often the icon of NM disappeared and I typed
```
sudo service network-manager stop
sudo rm /var/lib/NetworkManager/NetworkManager.state
sudo service network-manager start
```
And the last. Last time ther is a problem with data. The data that others copy to my flashdrive or external hhd are not displayed on my PC. And other people cannot read my data on this devices, because permission is denied
Soon I will try to do what you have typed

---

