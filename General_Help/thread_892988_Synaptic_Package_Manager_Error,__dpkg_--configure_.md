---
title: "Synaptic Package Manager Error,  dpkg --configure -a........"
date: 2008-08-17
forum: General Help
---

### Post by Karoniakowa on 2008-08-17
Last night i was downloading/installing a Program from Synaptic Package Manager And it appeared to have stopped installing/downloading so i closed it. i am running ubuntu 7.10 i believe 

Since then every time i try to install or download something from synaptic i get the following error: 

dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

After typing in the sudo dpkg --configure -a this is what i get.

> shitbird@shitbird-desktop:~$ sudo dpkg --configure -a
[sudo] password for shitbird:
Setting up flashplugin-nonfree (9.0.124.0ubuntu1~gutsy1) ...
Downloading...
--19:25:47--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.247.74.70
Connecting to fpdownload.macromedia.com|72.247.74.70|:80... failed: Connection timed out.
Retrying.

--19:28:57--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
  (try: 2) => `./install_flash_player_9_linux.tar.gz'
Connecting to fpdownload.macromedia.com|72.247.74.70|:80... failed: Connection timed out.
Retrying.

--19:32:08--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
  (try: 3) => `./install_flash_player_9_linux.tar.gz'
Connecting to fpdownload.macromedia.com|72.247.74.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,044,538 (2.9M) [application/x-gzip]

    0K .......... .....

My knowledge of Ubuntu is limited but to me it appears to be trying to download/install what i had canceled. 

Do i have to wait it out or is there a way to cancel the whole thing all together and not have to install? (assuming its doing what i think its doing)

I apologize if this should have been posted some where else. 

also does that ''nonfree'' mean im not supposed to be installing it? :confused:

Thanks.

---

### Post by jualin on 2008-08-17
You should wait until everything finishes downloading so you don't run into this problem again. Or if you want to cancel it just press CTRTL-C when you are on the terminal. Hope this helps!

---

### Post by jualin on 2008-08-17
And the "nonfree" part just means that is not open source. What you are downloading is the Adobe Flash Plugin which doesn't come by default in Ubuntu. Everything that you find in Synaptic Package Manager or in Add and Remove is perfectly fine for you to download. In some countries some packages such as the DVD Encryption package is not considered legal.

---

### Post by Karoniakowa on 2008-08-17
Hi crtl C worked great thanks. im going to wait awhile in tell i have a faster connection to install/download it thanks

---

### Post by jualin on 2008-08-17
Glad it worked. The CTRL-C key combination will stop anything that you run on the terminal so it applies to anything you are running on the terminal.

---

