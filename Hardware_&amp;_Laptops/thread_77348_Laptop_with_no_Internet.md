---
title: "Laptop with no Internet"
date: 2005-10-16
forum: Hardware &amp; Laptops
---

### Post by larry on 2005-10-16
Dear All,
I am quite a newbie, but Breezy seems to have installed smoothly on my laptop.
My only question is the following: I will be using it even without a internet connection and I do not want it to stand still waisting time looking for a connection every time.
I would like to be prompted something while the laptop boots up and have it skip the sincronization with Ubuntu clock and the search for an internet connection if I choose so.
I think it must be something pretty easy...if you know what to edit and how!
Many thanks
Larry

---

### Post by Joe_lurker on 2005-10-16
From the menu choose System | Administration | Services uncheck "Clock synchronization Service (ntpupdate)".
Joe

---

### Post by zachtib on 2005-10-16
when the 
"configuring network interfaces" pops up during boot, just press Ctrl-C to cancel it.

---

### Post by geir on 2005-10-17
One thing you can do is to lower the amount of time the dhcp client waits if it cannot get a connection.

The default timeout parameter for dhcp is 60 seconds (which I think is way to high) but if you have a fairly responsive network (your dhcp server responds quickly if you are at all connected) you can lower this to 5 seconds and then you laptop won't hang for 60 seconds when booting away from an internet connection.

Edit [FONT="Courier New"]**/etc/dhcp3/dhclient.conf**[/FONT] and uncomment the timeout parameter so that it looks like this
[FONT="Courier New"]timeout 5;[/FONT]
instead of how it looks by default, something like this
[FONT="Courier New"]#timeout 60;[/FONT]

---

### Post by knappen on 2005-10-17
Just go into networksettings and deselect the option to have the card activated on boot.

---

