---
title: "Using WPA2 Encryption in an Ubuntu Command-line Install"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by vergenzt on 2009-07-05
I have an *extremely* old machine on which I'm trying to get a command line Ubuntu up and running (we had tried it with the GUI but it took five hours to load the first page of the installation).

Initially, I had tried to get [Ubuntu minimal](https://help.ubuntu.com/community/Installation/MinimalCD) to work, as I've tried it before and it worked fine, but it gave an error, and I've since given up on that version.

So I tried using the Ubuntu Server CD we had lying around here.  It installs fine up to the point where it attempts to connect to our wireless internet.  The problem is that it assumes the network uses WEP encryption, when in actuality we use WPA2.

My question is this: Is there any way to have the Ubuntu Server 9.04 installation connect to a wireless network using WPA2 encryption?

---

### Post by prshah on 2009-07-05
> **vergenzt said:**
> 
My question is this: Is there any way to have the Ubuntu Server 9.04 installation connect to a wireless network using WPA2 encryption?

If you want to try connecting from the commandline:

Open a terminal (Applications-Accessories-Terminal) and give the commands```
sudo wpa_passphrase **YOUR_SSID YOUR_WPA_KEY** > /root/wpakey.conf
sudo wpa_supplicant -Dwext -i**wlan0** -c/root/wpakey.conf
#at this point, you may need to switch to an alternate terminal. (Ctrl+Alt+f2..f5).
sleep 10
sudo dhclient **wlan0**
```

Replace the parts in bold with that specific to your setup. (Eg, your wireless lan maybe called ath0, or wifi0, or eth4, or so on; check with the command iwconfig)

If it doesn't work, post back the results (fudge security information) for more troubleshooting.

---

### Post by toddedw on 2010-05-31
This method works fine for me however, I would like to get my /etc/network/interfaces file setup and working properly so that this is all automatic at boot. I followed the following tutorial and it yielded no results.

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

Any advice?

---

### Post by prshah on 2010-05-31
> **toddedw said:**
> the following tutorial and it yielded no results.

There's a section there on information to be posted "if you are stumped". Please post back with that information. Please be sure to obfuscate sensitive information, but not in a way that the output becomes misleading.

---

