---
title: "Can anybody please help me get this sorted???"
date: 2009-03-27
forum: Hardware
---

### Post by scrypt on 2009-03-27
I cannot stop the default wireless driver to stop loading at bootup.

I am trying to patch my Intel wirelss3945abg wireless card to a driver that allow package injection.

I am pretty new to Ubuntu so i m still learning.

I am trying to load this driver: ipwraw

and remove this driver: iwl3945

I want o blacklist the iwl3945 driver but no mater hat i do it still loads at bootup?

mark@ubuntu:~$ lsmod | grep iwl
iwl3945                99316  0 
rfkill                 17048  2 iwl3945
mac80211              216820  1 iwl3945
led_class              12164  1 iwl3945
cfg80211               32392  2 iwl3945,mac80211 


I have tried this command among othere and even added to: sudo cat 


sudo modprobe -r iwl3945

Can somebody please help me sort this out and also give me correct advice?

Thanks

scrypt

---

### Post by scrypt on 2009-03-27
I was given these commands.

But are they wrong to me they look conflicting is this correct??

Did you execute these commands step by step ?

echo "blacklist ipwraw" | sudo tee /etc/modprobe.d/ipwraw (blacklist the default ipwraw)

sudo depmod -ae (create a dependency file for the modules)

sudo modprobe -r iwl3945 (unload driver that you do not need)

sudo modprobe ipwraw (load the driver that you installed)

sudo ifconfig wlan0 up (enable the network adapter)

---

