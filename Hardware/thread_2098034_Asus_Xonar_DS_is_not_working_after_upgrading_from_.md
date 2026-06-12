---
title: "Asus Xonar DS is not working after upgrading from 12.04 to 12.10"
date: 2012-12-25
forum: Hardware
---

### Post by am_i_registered on 2012-12-25
Hello,

I have a custom made workstation at home and a thinkpad x61t.
I was very reluctant to upgrade my machines since 12.04 is LTS, but finally I decided to do so. I did it with the laptop and everything went great! smooth upgrade only a few clicks, reboot and ready.
With my workstation however, it wasn't so simple... dpkg crashed and although the upgrade wasn't complete (not even half of the apps were upgraded) the system was showing that I already have the newest version installed...
so... i did the following
```
sudo apt-get dist-upgrade
```the system started to upgrade some apps and then dpkg crashed again... so i ran 
```
sudo dpkg --configure -a
```and then again
```
sudo apt-get dist-upgrade
```and I repeated this until everything was upgraded.
After a reboot everything seems to be working as it should, except of the sound card.
I have an onboard intel sound card which works ok, but my xonar ds is not.
It is recognized as it should: CMI8788 (Oxygen HD Audio), but there is no sound.
Please take under consideration that it was working great with all versions from 10.4 to 12.04 and I have configured my asound.conf for surround sound 5.1 as it's shown in this thread:
[http://ubuntuforums.org/showthread.php?p=11912733](http://ubuntuforums.org/showthread.php?p=11912733)
Any help is highly appreciated!

---

