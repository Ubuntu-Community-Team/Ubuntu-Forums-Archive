---
title: "Firefox Flash Plugin"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by lewisforlife on 2009-10-01
I have running ubuntu 8.04 netbook.  I currently have Firefox 3.5.3, according to synaptic adobe-flashplugin 10.0.32.18 is installed, however in firefox if I go to tools-add-on-plugins it says flash 9 is installed.  How can I truly upgrade to flash 10 in firefox?

Thanks,

David

---

### Post by running_rabbit07 on 2009-10-01
If you are running 32Bit, go to a terminal and enter ```
sudo apt-get install ubuntu-restrcited-extras
``` I did that and it works with my 64 bit, but some people are saying they have problems with running the 32 bit on a 64 bit system. It is also in SYnaptic Package Manager.

---

### Post by HappyFeet on 2009-10-02
Uninstall any flash you have, go [here]("http://get.adobe.com/flashplayer/") and download the .tar.gz flash file, extract it, and put the **libflashplayer.so** file into ~/.mozilla/plugins OR .usr/lib/mozilla/plugins. Restart firefox.

---

