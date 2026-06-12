---
title: "Acer laptops"
date: 2007-04-04
forum: Hardware &amp; Laptops
---

### Post by 2xtreme on 2007-04-04
I have an acer travel mate 2203LCI and installed ubuntu. Everything seems to work fine except for the wireless network. I have the integrated wireless card. In the networking options it only shows wired lan. Thank you for your help.

---

### Post by tschneiter on 2007-04-05
My acer came with a broadcom wireless card, which does not work natively. This is because Broadcom chooses not to cooperate to develop open source drivers. At any rate, youll need to download the windows drivers for your card, then install ndiswrapper. 

Start with: 
sudo apt-get install ndiswrapper

then, follow the instructions from here on down:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver)

Good luck!

---

