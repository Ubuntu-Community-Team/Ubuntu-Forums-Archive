---
title: "Dell E6500 Laptop Wireless - Intel a/b/g/n 5300 - Installation Instructions (Hardy)"
date: 2008-09-25
forum: Hardware
---

### Post by DaveTRG on 2008-09-25
Mostly taken from Pytheas22's post here (nice German translation!), with some mods:
[http://ubuntuforums.org/showthread.php?t=906865](http://ubuntuforums.org/showthread.php?t=906865)

For kernels <=2.6.26, do this:

```
sudo apt-get install build-essential
wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-5.4.A.11.tar.gz
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2
tar -xzvf iwlwifi*
sudo cp iwlwifi-5000-ucode-5.4.A.11/iwlwifi-5000-1.ucode /lib/firmware
bunzip2 compat-wireless-old.bz2
tar xf compat-wireless-old.tar
cd compat-wireless-2.6-old/
make
sudo make install
sudo make unload
sudo make load
```

Then, reboot and you should be good.

For kernels >= 2.6.27:

You'll need to grab this file:
```
wget http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
```

Then follow the rest of the instructions here:
[http://ubuntuforums.org/showthread.php?t=906865](http://ubuntuforums.org/showthread.php?t=906865)

---

### Post by SteveONCSU on 2009-05-04
This didn't work for me.  After doing this, I actually don't have wireless working at all.  iwlagn isn't recognized as a service anymore.

I'm on 64bit Jaunty.   Plus I'm on a Thinkpad T500 but I have the same Wifi with the same symptoms a lot of others on here (and other forums) seem to have.  Anybody got any ideas??

---

