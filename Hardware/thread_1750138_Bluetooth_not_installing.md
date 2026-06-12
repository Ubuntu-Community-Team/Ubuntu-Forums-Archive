---
title: "Bluetooth not installing"
date: 2011-05-05
forum: Hardware
---

### Post by Marchosius on 2011-05-05
Hi all,

Yesterday i installed ubuntu 11.04 on my laptop (new user to linux) with built in bluetooth.

Today i tried using the bluetooth and it got stuck, did not receive any of the files sent. (as a test)
When i restarted my system the bluetooth icon on the top right was gone, and when i run the bluetooth application it tells me that no bluetooth adapters are connected.

how can i fix/re install my bluetooth?

---

### Post by awaldram on 2011-05-17
Try

 sudo /etc/init.d/bluetooth restart

From a terminal window

On my FSC laptop the Bluetothd service attempts to start prior to the adapter being ready during boot.

Think its probably a sequencing bug

---

