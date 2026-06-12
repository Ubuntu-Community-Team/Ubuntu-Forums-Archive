---
title: "[HOWTO] Install Ndiswrapper on 8.04 for Atheros NICs"
date: 2008-06-23
forum: Hardware
---

### Post by ruhtranayr on 2008-06-23
I installed Ubuntu 8.04 on an old Acer Aspire 3500 Laptop

This and many Acer Laptops have an Atheros Wireless Card in them.
Upon fresh install the Wireless card wasn't working and I realize this is very common.

This is how I got mine to work, I hope someone can benefit from this.

I got most of these steps from [http://ankurs.com/2008/04/installing-ndiswrapper-on-ubuntu-804/](http://ankurs.com/2008/04/installing-ndiswrapper-on-ubuntu-804/) I should mention.

Before we start, Determine your network card. Run

$ lspci 

This shows we have an Atheros Communications Inc. AR2413 802.11bg NIC (rev 01) card

STEP ONE - Disable Restricted Drivers

First thing, we have to disable the restricted drivers that come enabled by default.

System >> Administration >> Hardware Drivers

Disable both Atheros Hardware Access Layer (HAL) and Support for Atheros 802.11 wireless Lan cards.


STEP TWO - Install Ndiswrapper

Now we install Windows Wireless Drivers

Applications >>Add/Remove...

Click Search

Search for "ndis" and a program called Windows Wireless Drivers should pop-up

Install Windows Wireless Drivers

Open this program under System >> Administration >> Windows Wireless Drivers


STEP THREE - Get drivers

Now we need the drivers. get them at 

[http://www.atheros.cz](http://www.atheros.cz)

download the windows 32 bit driver

you should see 2413, or choose your card

Now extract the .zip file. Youre .inf file is in there.

Actually there were two in mine, netathw.inf and netathwx.inf

I loaded netathw.inf and it works perfectly... but you're not done yet.

Step 4 -- Edit /etc/rc.local

We have to edit /etc/rc.local to load the ndiswrapper module on boot. I prefer to use gedit but you can use any editor. I recommened nano.

$ sudo gedit /etc/rc.local

it should read:

rmmod ssb
modprobe ndiswrapper
exit 0

Save and reboot. Enjoy!
:guitar:

---

### Post by vancity on 2008-07-05
Thanks for posting that, I also have an Acer Aspire 3500 and the wireless went down sometime after the last downloaded update I think but had been working fine before. I followed the steps you posted but unfortunately I still couldn't get the wireless working for some reason. I'm very new to Ubuntu/linux so any other tips would be appreciated.

Thanks!

---

