---
title: "After upgrade to 9.10: full disk encryption stops working, boot impossible"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by bafimann on 2009-11-04
Yesterday upgraded my Jaunty system to Koala. The upgrade seemed to work, until I tried to reboot. Grub stopped with an error, telling me that it could not mount the selected partition. My system is configured to use full disk encryption (as what you get from using the alternate installer cd). I have to mention, that during the upgrade, I was asked if I wanted to update my menu.lst, to which I agreed. What I already found out is that this update produced a wrong "root=" parameter (originally it was sda6_crypt, but the update changed it to sda8_crypt). But even after changing this I still get the grub error. Grub does not even ask for a decryption passphrase, as it used to.
I am still able to mount my root partition with the karmic koala alternate installer cd in rescue mode.

I think this is quite a serious problem. Just by upgrading a system you end up not being able to boot it anymore...

I hope someone can give me any advice about this...
Michael

---

### Post by tacitdynamite on 2009-11-24
Wow, dude, sorry no one has replied. Unluckily, I'm a linux noob, and this is my first upgrade. Watching your success [or lack thereof] with anxiety ...

You may want to check back in with [this]("http://www.uluga.ubuntuforums.org/showthread.php?p=8376252#post8376252") thread and [this]("http://ubuntuforums.org/showthread.php?p=8376168#post8376168") thread, both of which contain a single person asking for help with encryption and upgrades to karmic.

---

