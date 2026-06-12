---
title: "Wifi stopped working"
date: 2009-07-11
forum: Hardware
---

### Post by Zarniwoop79 on 2009-07-11
Hello!

I'm running Xubuntu 8.04 on my laptop. I've been using it for about a year, and I've used wifi in it for a long time. But since a few weeks ago Wireless network is no longer an option in the network settings. I can still connect to the Internet using ethernet, but wireless doesn't seem to exist anymore.

I've tried the physical wireless button, and it doesn't help, so I think that I need to reinstall something, but I am not sure what. 

So I was wondering if anyone knows how I can fix this, and if I can fix this without internet access in Linux (until I get the wireless access back)? I am writing this from Windows, so I can still download things and then reboot to Linux.

Best regards,

Zarniwoop

---

### Post by ToddFisher on 2009-07-19
Any luck?  I just had the same thing happen in Xubuntu 9.04.  Bye bye wifi.

---

### Post by izziere on 2009-07-19
Without more details it is a tricky one to identify.  I have had intermittent problems - usually when a new kernel is released.  

Firstly, try:

```
sudo /etc/init.d/networking restart
```

Most recently I have resolved using

```
sudo ifdown --all
```

This takes down all the network interfaces

Followed by;

```
sudo ifup wlan0
```

Where wlan0 is the name of the wireless interface.

Maybe you could post relevant outputs from **dmesg** and **iwconfig**, plus post the contents of your /etc/network/interfaces file

---

