---
title: "Will my WLAN work? atheros"
date: 2007-12-06
forum: Hardware &amp; Laptops
---

### Post by SpinningAround on 2007-12-06
I have this wlan hardware and i wonder if it will work since, i did find info on this webpage that it might be a problem [http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5007EG](http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5007EG)

Please say what you think, if someone have any experiense with this hardware please say so.

I have tested with ubuntu live cd and I did get some info with "wifi not found" but didn't try to fix it since i didn't get any info about the wlan under network settings.

---

### Post by Donskov on 2007-12-06
Yes and no. my ar5007eg works with [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29") . The card does not work after a suspend or after switch is turn off and on. Although  the issues I have my be realated to my acpi. 

Here are some links that helped me get my ar5007eg up and running.

[The divers work. The instructions were missing the removal of ath_hal. Everything should work after you use the code from below.]("http://docs.google.com/View?docid=dtvgpkz_46fv8dwf")


You will also want to disable ath_hal in your restricted drivers and dont forget to remove the module for ath_pci and ath_hal with.

should look something like DISABLED_MODULES="ath_hal"
```
sudo nano -w /etc/default/linux-restricted-modules-common
```
```
sudo modprobe -r ath_pci
```

---

