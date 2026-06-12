---
title: "Installing Atheros AR5008X drivers on Ubuntu 8.04"
date: 2008-09-23
forum: Hardware
---

### Post by Kraaijenzank on 2008-09-23
Hey guys!

After being fed up with Microsoft Windows for a couple of years, I finally switched to Ubuntu 8.04. It seemed to me that it is now user friendly enough for the average computer user.

Now, I have a Zepto 3215W laptop with an Intel Dual Core processor and 2 GB RAM. I have assigned 20 GB of space for Ubuntu (excluding the space for swap). I have a Zepto Zpro WiFi card. That card has an Atheros AR5008X chipset. I found out that I need MadWifi to be able to use my WiFi card with Ubuntu.

So, what I did was downloading madwifi-0.9.4 and I entered these lines of code (after extracting the package):

```
make
```
```
sudo make install
```

It seemed to work fine after I entered "make". But after the second line, the terminal told me that MadWifi drivers were already installed. I don't get that since the WiFi is definitely not working.

Do you have any tips for a newbie like me? :D Thanks in advance!

---

