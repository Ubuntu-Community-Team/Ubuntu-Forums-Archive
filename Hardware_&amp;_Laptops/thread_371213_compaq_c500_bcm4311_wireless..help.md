---
title: "compaq c500 bcm4311 wireless..help?"
date: 2007-02-26
forum: Hardware &amp; Laptops
---

### Post by pixeldotz on 2007-02-26
so i just got a compaq c500. the wireless minipci card is a broadcom  rev 4311. i've follwed countless guides and used fwcutter to install the drivers. the light is on and the laptop sees the  card but it won't connect to anything. network manager doesn't seem to make a difference.

does anyone know a super simple guide on using ndiswrapper? it seems more people are having more success using that instead of fwcutter.

getting another wireless card is not an option since this laptop does not have any pcmcia slots.

any help would be greatly appreciated.

---

### Post by nachotronics on 2007-02-26
You can get it working following _**[these steps]("http://www.ubuntuforums.org/showthread.php?t=297092&highlight=edgy+dell+1390")**_
The driver in that post is the one from support.dell.com, in my case that one didn't work so i used the one i'm attaching.

After getting your wlan working you might want to install network-manager-gnome following _**[this howto]("https://help.ubuntu.com/community/WifiDocs/NetworkManager?highlight=%28network%29%7C%28manager%29")**._ This utility helps you set up WEP or WPA secured networks.

Hope this helps.

---

### Post by hgordon on 2007-04-12
I tried this, and 
[INDENT]sudo ndiswrapper -l[/INDENT]

reports
[INDENT]bcmw15 :  invalid driver![/INDENT]

I have a new Compaq Presario C508, now running 7.04 Feisty

======
update - whoops - the '1' should have been an 'l' .  I tried bcmwl6, but discovered that it is a Vista driver, and it doesn't work with ndiswrapper.  after locating bcmwl5 and starting over

ndiswrapper -i bcmwl5.inf
depmod -a
modprobe ndiswrapper
ndiswrapper -mi
ndiswrapper -ma
depmod -a modprobe ndiswrapper

The command "ndiswrapper -l" gives me:
installed drivers:
bcmwl5 driver installed, hardware (14E4:4328) present

after a few reboots, it now works !

---

