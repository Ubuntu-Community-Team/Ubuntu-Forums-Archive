---
title: "Bluetooth Mouse in K/Ubuntu"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by fogNL on 2007-04-22
I have a Logitech bluetooth mouse that I purchased recently, however, i'm having a small problem with it in Kubuntu 7.04.

Is there a much easier way to setup bluetooth mice?  It seems the only method I can find is via the command line using hidd.

Anyways, I setup my mouse using:

hidd --search

and then

hidd --connect macaddress

The mouse works fine.  However, if i get up and go away from my laptop for a few minutes and come back, the mouse is no longer working, but whenever I attempt to move it, the kbluetooth trayicon appears and disappears repeativly.  (this also happened before my initial setup)

Is there a way for the system to 'remember" so I don't have to mess with connecting my mouse every time I sit down at the laptop?

I also went into /etc/default/bluetooth and manually set it in there with:

HIDD_ENABLED=1
HIDD_OPTIONS="-i 00:07:61:xx:xx:xx --server"

However it did not help at all.

Thanks for your help in advance.

---

### Post by x64Jimbo on 2007-04-23
There's a thread for this:
[http://ubuntuforums.org/showthread.php?t=227057](http://ubuntuforums.org/showthread.php?t=227057)

---

