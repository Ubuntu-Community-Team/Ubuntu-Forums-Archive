---
title: "installing flash plugin in hardy"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by abhinav.p on 2009-02-21
when i tried to install adobe flash pugin,it showed an error due to network problem and did not complete the installation.when i tried again later,it showed  already installed.but u tube videos do not work in my laptop..

---

### Post by Partyboi2 on 2009-02-21
Open a terminal and try reinstalling flashplugin-nonfree
```
sudo apt-get --reinstall install flashplugin-nonfree
```

---

### Post by abhinav.p on 2009-02-21
this was where the reinstall got stuck.is it a network problem?  









         => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 60.254.170.70
Connecting to fpdownload.macromedia.com|60.254.170.70|:80...




when i tried to reinstall again,this was the message



E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 




what should i do?

---

### Post by Partyboi2 on 2009-02-22
Open a terminal and type
```
sudo dpkg --configure -a
```

---

### Post by edittert on 2009-03-03
I also had a problem with this symptom.  In my case at least, it was because I am behind a firewall, so the flash installer needed to know about a proxy.  For me, the following succeeded (in a sudo shell).  You should substitute appropriate values for <proxy> and <port>

export http_proxy=http://<proxy>:<port>
dpkg --configure -a

For more info, such as if your proxy requires username and password, just search the web for "http_proxy".

Good luck.

---

### Post by abhinav.p on 2009-03-03
yes i did that.after i ran #dpkg --configure -a,it sait flashplugin not installed.so i did apt-get install flashplugin-nonfree.this is the output.what shoukd i do?






Downloading...
--08:22:50--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Connecting to 172.16.1.5:8080... connected.
Proxy request sent, awaiting response... 404 Not Found
08:22:54 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.

---

