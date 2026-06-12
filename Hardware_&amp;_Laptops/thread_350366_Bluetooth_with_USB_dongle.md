---
title: "Bluetooth with USB dongle"
date: 2007-01-31
forum: Hardware &amp; Laptops
---

### Post by Znortfl on 2007-01-31
Dear Ubuntu people,

I just bought a new phone (Samsung S410i) with bluetooth support. I also have a bluetooth "dongle" I believe it is called. It has got a USB connector and is supposed to enable me to use bluetooth (Sitecom CN-512 v1 001). When I plug it in and I search for bluetooth devices on my mobile, it finds my phone (named "Tobias") and my sisters phone (named "Banana"). When I try sharing a picture with my phone I right-click the file and choose "Send to...", select Bluetooth and select my phone.

Then my phone asks for a PIN code. This is the big problem: I tried everything I could imagine. The default PIN code (1234), my phone's code and even some random ones. Neither seem to work.

However, when I try to share a file to my sisters phone (LG c3800) I am not asked for a PIN code and file transfer *does* work.

Also, when I try hcitool scan, it finds both devices but kdebluetooth finds none.

Thank you in advantage,

Tobias

---

### Post by flangemonkey on 2007-02-15
ok, I cannot proimise this will work, but in your /etc/bluetooth/hcid.conf file change the pin program.

There are about 3 to choose from, if in doubt post your hcid.conf file and people might be able to help, or search the forum for hcid.conf and you will see them. I am stil trying to get my dongle detected :/ but have read quite a lot of posts on the net and people seem to be struggling when using a bluetooth pinwrapper. 

hth

---

