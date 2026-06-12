---
title: "Wireless N with WRT600N and Intel PRO/Wireless 4965 AGN"
date: 2008-09-17
forum: Hardware
---

### Post by zamarax on 2008-09-17
Hello, is there anything special (package wise) I might need for this controller to connect to wireless N networks? My Laptop is dual boot vista / hardy 8.04, in vista there is no problem connecting to both wireless N and wireless G, however in Hardy wireless N just seem to cycle and cycle without ever connecting. I do have the latest Intel drivers installed but that doesn't seem to change anything.

Thanks in advance!

---

### Post by pytheas22 on 2008-09-17
I believe that the iwl4965 driver in Ubuntu Hardy was not compiled with N-mode support because at the time Hardy was released, 11n hadn't been implemented yet by the iwl project.  It should be included by default (I think, but don't quote me) in the next version of Ubuntu, Intrepid.  You can try using the alpha version of Intrepid, which will be released in stable form at the end of October.  Or you can try recompiling the iwl4965 driver on Hardy to support 11n mode.  To do that, run these commands (I'm not sure if this will work; it will just give you the latest stable release of the iwl4965 driver, which hopefully has 11n mode enabled by default):
```

sudo apt-get install build-essential
wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-228.57.2.21.tgz
tar -xzvf iwlwifi*
cp iwlwifi-4965-ucode-228.57.2.21/iwlwifi-4965-2.ucode /lib/firmware
wget http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2
bunzip2 compat-wireless*
tar xf compat-wireless*
cd compat-wireless-2.6-old/
make ###it will take a few minutes here to compile
sudo make install
sudo make unload
sudo make load
```

---

