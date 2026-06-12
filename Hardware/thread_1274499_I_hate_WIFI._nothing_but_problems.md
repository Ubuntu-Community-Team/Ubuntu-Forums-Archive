---
title: "I hate WIFI. nothing but problems"
date: 2009-09-24
forum: Hardware
---

### Post by PsYcHoTiC_MaDmAn on 2009-09-24
first off, I have no wifi hub, what I've been doing is using another laptop (alas, running vista) which was set to share Internet > then new conection > set up a wireless Ad-Hoc networl> named the network testing, and had it unsecured.

then on the aspire 150l (running ubuntu 9.04) I was able to find the network and connect through to the Internet. restart the Acer, and now it wont connect. spend a lot of time trying to replicate the conditions, and got nowhere.

I then found a reference on here for using Wicd instead. so installed that (which it then removed gnome-networkmanager) and as it was with gnome, it can see the network, but cannot connect to it (cant find the IP address)

works fine with ethernet, but I want to get wifi working for when I go to uni.

the other thing is that unlike gnome, it seems I cant switch off wifi if I dont use it (to prolong battery)

help please

---

### Post by duanedesign on 2009-09-25
I am pretty sure your laptop has the AR242x. You can confirm this by running this command in a Terminal.
Applications > Accessories > Terminal

```
lspci -vnn
```

you should see something like this:

03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)

If that is correct you should be using the Ath5k driver. To confirm this you should see in the same stanza as the information above two lines like this:

Kernel driver in use: ath5k
Kernel modules: ath5k

This particular card is not easy to get working. Some have had better luck than others so I dont want to discourage you from trying.
To try the latest ath5k driver run the following in the Terminal:

```
sudo apt-get install linux-backports-modules-jaunty
```

also make sure the ath_pci is blacklisted

```
sudo nano /etc/modprobe.d/blacklist.conf
```
NOTE: your file may or may not have .conf on the end. if you do not find this file try /etc/modprobe.d/blacklist. If this is the case after you are done with it save it with .conf on the end, this is the preferred format.

Look for a line in the file like the one below. If it is not there add it and save the file:
> blacklist ath_pci

Try this newer driver and see if you have any change in performance.

If you do not get any improvement I would try the site below. If you are going to try the driver recommended below you need to delete the line you added to /etc/modprobe.d/blacklist.conf.

A couple of things not mentioned on this link.
1. You will need to run the following to install build-essentials if you are going to install the mad-wifi driver. Run the following in the Terminal before leaving this page.

```
sudo apt-get install build-essential
```

2. After you install the ath_pci driver 'modprobe ath_pci' you will need to go to System > Administration > Hardware Drivers to enable the new driver and disable the old Atheros one.

[http://adamdotnet.net/2008/08/18/acer-one-wifi-fix/](http://adamdotnet.net/2008/08/18/acer-one-wifi-fix/)
-
-
-

---

### Post by PsYcHoTiC_MaDmAn on 2009-09-25
as you said I have the AR242x 802.11abg

I managed to reinstall gnome-networkmanager and having done so I've been able to get wifi running again.

however it is through an unsecured network didn't have much luck with WEP or WPA1&2

today I managed to get 2 Aspire one 150l's to connect to the toshiba laptop and access the web through it.

all I did was reinstate gnome and disable the madfi drivers (which I'd tried when the previous attempt failed.)

will see how I get on tomorrow with the university network

thank you for the help however, I may still need it.

---

### Post by PsYcHoTiC_MaDmAn on 2009-09-28
well got it sorted with little issue (though the techs all scattered when I mentioned ubuntu (why would a learning institute not support linux??))

now all I got to sort is VPN, despite using all the settings they list in their guides for macs and M$, it refuses my attempts to connect via VPN (no shared secrets??)

---

### Post by wilee-nilee on 2009-09-28
> **PsYcHoTiC_MaDmAn said:**
> as you said I have the AR242x 802.11abg

I managed to reinstall gnome-networkmanager and having done so I've been able to get wifi running again.

however it is through an unsecured network didn't have much luck with WEP or WPA1&2

today I managed to get 2 Aspire one 150l's to connect to the toshiba laptop and access the web through it.

all I did was reinstate gnome and disable the madfi drivers (which I'd tried when the previous attempt failed.)

will see how I get on tomorrow with the university network

thank you for the help however, I may still need it.

I just ran into the same problem after installing sun's Vbox puel and installed wicd which saw no wireless networks I reinstalled network manager and everything is working. I have been having various problems with wifi on another laptop me thinks there is a bug.

---

### Post by PsYcHoTiC_MaDmAn on 2009-09-28
got a new bug however.

authentication
it signs into the network easily. however about 2-8minutes after it cuts off. having been in with the computer techs at uni. their saying that the logs are saying that it logs in fine at the beginning, but then fails to give authentication when it challenged again by the network.

I will be seeing the more experienced tech later, as the others all say they dont know enough about linux to help.

wondering if there is a script that could respond to such verification requests, or  constantly broadcasts authentication (though obviouslly this will eat battery and steal bandwidth

---

### Post by ChumleyEX on 2009-09-28
Wifi access points make this all very easy.

---

### Post by PsYcHoTiC_MaDmAn on 2009-09-28
> **ChumleyEX said:**
> Wifi access points make this all very easy.

what do you mean by that. I'm in a wifi enabled area. and whilst connecting was relatively easy this authentication bug does make it irritating.

still waiting to see the tech who's supposed to be able to deal with linux.

---

