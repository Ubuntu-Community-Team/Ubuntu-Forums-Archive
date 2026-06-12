---
title: "Installing Hoay in a WPA protected network"
date: 2005-07-26
forum: Hardware &amp; Laptops
---

### Post by WARM3CH on 2005-07-26
Hi,

I'm a long time Windows user and would like to try Linux on my machine. However, it turns to be a bit more difficult than what I thought to install: I tried the live CD and it works fine except that it does not work with my network.

Now, I have a Dlink DWL-520 (rev. A) wirless, 802.11g network card connected to the net through an access point using WPA-TKIP. It seems there is a problem with WPA and Hoary as it does not support it.

So how can I install Hoary 5.04 on my machine and get the network connection working? I'm not sure how to get the required packages in XP. What is your suggestion and how can I continue?

---

### Post by luca_linux on 2005-07-26
You need wpa_supplicant. So, install the "wpasupplicant" package through Synaptic or apt.
Then you'll need to edit a configuration file that can be found at /etc/wpa_supplicant.conf as the following:
```

network={
       ssid="your_network_name"
       proto=WPA
       scan_ssid=1
       key_mgmt=WPA-PSK
       psk="your_secret_key"
}

```
Obviously you need to make some adjustaments.
Then run it through:
```
sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
```
Where "eth1" is your device and "ipw" is the relative driver. What driver are you using instead? Maybe ndiswrapper?
Anyway, have a look at the second part of this HowTo, just for reference: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)
There are also some scripts to start wpa_supplicant at boot.

---

### Post by WARM3CH on 2005-07-26
Thanks a lot luca_linux. This can help. I'll give it a try tonight. 

Do you think all needed packages are already on the CD or I'll need to get something from the web? As I said before, for the moment I can only access the web through Windows.

---

### Post by luca_linux on 2005-07-26
Uhm...I don't remember if wpa_supplicant is on the cd...Anyway, you can download the package under Windows and then use it under Ubuntu. Just go into the Ubuntu Repositories through a browser...

---

