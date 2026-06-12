---
title: "Installing a bluetooth connection in ubuntu"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by Souljah on 2009-03-07
Hi

I'm trying to install a bluetooth dial up connection in ubuntu but I'm having extreme difficulty in it. I need some help. I have followed the directions provided here:

[http://www.spiration.co.uk/post/1307/Ubuntu%20Linux%20-%20Bluetooth%20and%20GPRS%20dialup%20connection](http://www.spiration.co.uk/post/1307/Ubuntu%20Linux%20-%20Bluetooth%20and%20GPRS%20dialup%20connection)

However, for some reason at this step "pon BluetoothDialup" it doesn't do anything. I need to get these files if possible, anyway I can get them offline?

```
First you need to install the bluetooth packages on your linux machine:

$sudo apt-get install bluez-utils
$sudo apt-get install blues-pin


Now you need to make sure you have the ppp package installed

$sudo apt-get install ppp
```

So technically, I can't install these packages due to there being no internet. Can someone help me in setting up a bluetooth connection in ubuntu? I'm in XP now, dual booting.

Ryan

---

### Post by cariboo on 2009-03-07
You obviously have an internet connection, so you can go [here]("http:///packages.ubuntu.com/") and download the packages you need. Use a usb thumbdrive or burn them to cd and install then on your computer running Ubuntu.

Jim

---

