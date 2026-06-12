---
title: "Enabling wireless card without internet connection."
date: 2008-09-26
forum: Hardware
---

### Post by vidus on 2008-09-26
I am going to toss xp and install linux (mint). The problem is I do not have access to a wired connection. 

I have been playing around with the live cd trying to see if I can get the wireless to work without an internet connection but so far have not been able to get it going. I have the BCM4318 Broadcom card, and am trying to use ndiswrapper.

So far I have done the following:

gksu gedit /etc/modprobe.d/blacklist

^and added the line to blacklist.

sudo modprobe -r bcm43xx

sudo modprobe ndiswrapper 

Then I install the new driver for my broadcom which I have saved on a usb drive. In Mint there is a program pre-installed called Windows Wireless Drivers Installation Tool which does things for you.

Once the driver is installed... I dont know what to do... No wireless connections are detected. The system does recognize the carn in wlan1, but it doesnt do anything... I also tried to enable the wireless driver in the network manager, (which says "in use") but it tries to download fwcutter, which obviously without a connection it cant do. I did save fwcutter deb on the usb drive and install it but after its installed i dont know what to do with it, the system still tries to download it when i check enable...

I am following the guide located here: [http://www.linuxmint.com/wiki/index.php/MintWifi#Broadcom_43xx](http://www.linuxmint.com/wiki/index.php/MintWifi#Broadcom_43xx)

Any help appreciated. I have used linux before but I had a wireless connection so it was not a problem. I hope this all makes sense.

---

### Post by vidus on 2008-09-27
sigh... so i gather its impossible to run linux with wireless for users that do not have a wired connection first.

back to xp for me i guess! :(

---

### Post by niccholaspage on 2008-09-27
You asked this 2 hours ago. Just because a lot of people are on the forums doesn't mean that you will get super fast answers.

---

