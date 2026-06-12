---
title: "unable to patch ar5007eg"
date: 2009-08-09
forum: Hardware
---

### Post by noiz354 on 2009-08-09
i'm currently using ubuntu jaunty jackalope .i couldn't see any ath0 on my terminal but i only get wlan0 and i can't modprobe ath_pci after use"sudo make install"

i use this >  Jaunty Jackalope - Atheros ar5007eg doesn't work
Ok here's the method i use to get my wifi working with mad wifi.

1.- download the driver from here (I always choose the newest) : madwifi-hal:(

2.- Download all the things needed to compile
$sudo apt-get install build-essential linux-headers-`uname -r`

3.- extract the files
$sudo tar --xzvf /directory/file_name.tar.gz

4.- move to that directory
$cd /uncompressed_directory/file_name

5.- Compile
$sudo make

6.- Remove possible previous installed versions
$sudo rm -rf /lib/modules/`uname -r`/madwifi

7.- Install Driver
$sudo make install

8.- Reboot

this is from a guide from here (in spanish) that I used since 8.04 I'm gonna try it now with jaunty so I will post my experience for my box I'm using the atheros support from restricted drivers manager.

Hope it helps but i can't modeprobe ath0

---

