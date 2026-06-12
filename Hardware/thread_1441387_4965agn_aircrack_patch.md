---
title: "4965agn aircrack patch"
date: 2010-03-28
forum: Hardware
---

### Post by jman123 on 2010-03-28
I began using Ubuntu when 7.04 came out. I never really was able to get used to it, but I have tried to come back to it. One thing I would like to be able to do is successfully hack a wireless network. Unfortunately, I have this cursed Intel 4965agn adapter. I tried to follow these patch directions. 

```
wget hxxp://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-228.57.2.23.tgz
wget hxxp://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2

Deal with the firmware
Code:

tar zxvf iwlwifi-4965-ucode-228.57.2.21.tgz
cd iwlwifi-4965-ucode-228.57.2.21
cp iwlwifi-4965-ucode-228.57.2.21/* /lib/firmware/

Deal with the driver
Code:

tar xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*

Get the necessary patch and patch away (there is another but was not needed)
Code:

wget mac hxxp://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch
patch -p1 < mac80211_2.6.28-rc4-wl_frag+ack_v3.patch

build the modules
Code:

make
make install
make unload
echo "options iwlagn swcrypto=1" >> /etc/modprobe.d/options
make load
```

I keep getting an error when I have to run the patch -p1 command. I am sure it's something simple, but I can't figure it out. I don't even know if these patch directions are up to date. :-(

I have searched the web for information, and I tried to use the Backtrack 4 disc, but to be honest, I hate the look, feel, and layout of that OS. I much prefer Ubuntu 9.04. 

If it matters, I installed Ubuntu using Wubi.

Thanks in advance.

---

### Post by zouzou0 on 2010-05-05
im no expert in linux but i managed to get this card working on linux backtrack 4 nd i think it should work for u the same as!!!
since backtrack is ubuntu based....

anw can u post down the error ur getting !!

---

