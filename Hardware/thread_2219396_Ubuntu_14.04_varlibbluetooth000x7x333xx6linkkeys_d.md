---
title: "Ubuntu 14.04 /var/lib/bluetooth/00:0x:7x:33:3x:x6/linkkeys does not exist"
date: 2014-04-23
forum: Hardware
---

### Post by mocho on 2014-04-23
hello 
I am trying to pair a bluetooth magic mouse in a triple boot situation, already is working in windows and MAC now my problem is with Ubuntu 14.04 trusty tahr
As per this page 
[http://ubuntuforums.org/showthread.php?t=1479056](http://ubuntuforums.org/showthread.php?t=1479056)
I should be inserting the linkkey in /var/lib/bluetooth/00:0x:7x:33:3x:x6/linkkeys 

the problem is that this file does not exist even after I pair another bluetooth microsoft mouse and Ubuntu manpage says this file should exist 
[http://manpages.ubuntu.com/manpages/trusty/en/man8/bluetoothd.8.html](http://manpages.ubuntu.com/manpages/trusty/en/man8/bluetoothd.8.html)
i think this manpage is not updated because there are several files in the directory that are not mentioned

How can i insert the linkkeys in Trusty tahr???


regards

---

### Post by mocho on 2014-04-24
ok, It seems yet another bug in ubuntu bluetooth. 
Instaled blueman and could pair magic mouse and linkkyes is created

---

