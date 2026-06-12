---
title: "Unable to connect to wireless network"
date: 2008-08-24
forum: Hardware
---

### Post by mat4291 on 2008-08-24
I've recently installed ubuntu 8.04 and I have encountered a slight problem. I can't connect it to the internet via the wireless card. Unfortunately Wireless is the only option else I would try wired.

I'm completely new to the world of linux so completely lost. Usually I would try to figure out myself but I have no idea where to start. After searching the web I have started to get familiar with the terminal. So I can tell you that I am using a RaLink RT2561/RT61 802.11g PCI. Unfortunately my knowledge ends there.

Any help would be greatly appreciated.

Matt

---

### Post by cl0ckwork on 2008-08-24
try checking out this thread, there might be some help on it

[http://ubuntuforums.org/showthread.php?t=832809](http://ubuntuforums.org/showthread.php?t=832809)

---

### Post by david sousa on 2008-08-24
Hey!

If know your wireless card you only have to search for correspondent drivers and download them.

Then follow this instructions [here]("https://help.ubuntu.com/7.10/internet/C/ndiswrapper.html") to get it work through ndiswrapper.

;)

---

### Post by mat4291 on 2008-08-24
Thanks for the fast replies :D

> **cl0ckwork said:**
> try checking out this thread, there might be some help on it

[http://ubuntuforums.org/showthread.php?t=832809](http://ubuntuforums.org/showthread.php?t=832809)
I have read this topic, It mention's many things that go right over my head. But I will reread and research the things I don't understand.
> **david sousa said:**
> Hey!

If know your wireless card you only have to search for correspondent drivers and download them.

Then follow this instructions [here]("https://help.ubuntu.com/7.10/internet/C/ndiswrapper.html") to get it work through ndiswrapper.

;)

I think I should be able to understand this. I know you can install applications by using the command Apt-get in the terminal but I am unable to do this as I can not access the internet. Is there any way to get the installation files via a windows machine that I have connected to the internet.

Matt

---

### Post by REMCZY on 2008-08-24
Hi guys I own a Toshiba A205-S5000 and I've tried all... It has an Atheros wi-fi card but it's not supported by xubuntu 8.04... I deny myself to use another operating system, please Help me... One possible solution might be using ndiswrapper but I can't find the xp driver for that card.

---

### Post by david sousa on 2008-08-24
Search for ndiswrapper installation files at google

---

### Post by libra1780 on 2008-08-24
try to check out madwifi as well
[http://www.madwifi.org]("http://www.madwifi.org")
atheros is their thing

---

### Post by mat4291 on 2008-08-24
> **david sousa said:**
> Search for ndiswrapper installation files at google

Do you know if it is including with the live CD? If it is could I use a command such as "sudo apt-get install ndiswrapper" or "sudo apt-get install ndiswrapper-utils" to install it.

---

### Post by cl0ckwork on 2008-08-24
> **mat4291 said:**
> Do you know if it is including with the live CD? If it is could I use a command such as "sudo apt-get install ndiswrapper" or "sudo apt-get install ndiswrapper-utils" to install it.

ndiswrapper may come along with the live-cd, but you still need to get the driver to use along with it

---

### Post by david sousa on 2008-08-24
You can download ndiswrapper [here]("http://ndiswrapper.sourceforge.net/joomla/#Install_Windows_driver") and install it through the instructions that come with it.

Then search for the driver wich corresponds to your card and install it through "Windows wireless drivers" at system --> admnistration.

If you are not sure of you wireless card, just type lspci at the console and you  have the network controller at the last line.

;)

---

### Post by REMCZY on 2008-08-24
I've tried the ndiswrapper, madwifi and nothing happend... I installed Xubuntu Intrepid 8.10 and I have the wireless options but the laptop can't reach the router... I'm so frustrated...

---

### Post by libra1780 on 2008-08-25
> I installed Xubuntu Intrepid 8.10 and I have the wireless options but the laptop can't reach the router... I'm so frustrated...
maybe it's just missing the firmware

---

### Post by REMCZY on 2008-08-30
I've tried the ndiswrapper and it works only once. When I restart my laptop the wireless goes down and there is no way to ping the router... I also tried madwifi with no results... I upgraded my kernel to rc4 and nothing...I think I've read most of the posts that are related... I hate to say this, but I'll have to install vista to get wifi, That Sucks!:confused:

---

### Post by david sousa on 2008-08-30
go at system -> administration  -> hardware drivers and check the box there, then just reboot

---

### Post by Bucky Ball on 2008-08-30
[http://linuxkc.wordpress.com/2008/03/10/howto-install-serialmonkey-drivers-for-ralink-rt61-wireless-card/](http://linuxkc.wordpress.com/2008/03/10/howto-install-serialmonkey-drivers-for-ralink-rt61-wireless-card/)

That link should get close to fixing things. It appears you need to use the serialmonkey drivers and blacklist the RT61 drivers.

---

