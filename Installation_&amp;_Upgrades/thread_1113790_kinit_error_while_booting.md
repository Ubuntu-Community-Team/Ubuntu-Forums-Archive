---
title: "kinit error while booting"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by vpnm_87 on 2009-04-02
am using Ubuntu 8.10..i removed libxml2 package mistakenly and found some icons looking strange in desktop,some options were missing in all desktop menu...
I reinstalled it from terminal using
apt-get install libxml2

then rebooted the machine..
now i couldnt enter the GUI login...automatically entering to command line login with some kinit error msg.

kinit:name_to_dev_t(some uuid)
kinit:trting to resume from /dev/disk/by-uuid/(same uuid)
kinit:no resume image

I tried
[http://ubuntuforums.org/showthread.php?t=661611](http://ubuntuforums.org/showthread.php?t=661611)

But it did not worked.

What pakages should i install in terminal to recover GUI log in?

---

### Post by igorc on 2009-04-26
I guess something went wrong with your usplash install. Someone suggested running strace and trying to find the what's missing:

# sudo strace usplash &> error

and than check what is it complaining about.

---

