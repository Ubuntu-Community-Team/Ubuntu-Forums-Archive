---
title: "undo libexec command ?"
date: 2014-11-07
forum: Hardware
---

### Post by arapaho on 2014-11-07
I search for solution for my problem and I did something without knowing the effects. I wanted to mount disk and found

[http://web.archiveorange.com/archive/v/268W5AGQ1KKnpXDiCZXl](http://web.archiveorange.com/archive/v/268W5AGQ1KKnpXDiCZXl)
# /usr/libexec/polkitd &
# /usr/libexec/udisks-daemon &

So i did
sudo /usr/libexec/polkitd &
 sudo /usr/libexec/udisks-daemon &

Disk is mounted but it has root:root ownership. 
I tried to use chown to change ownership but it doesn't work.

How can I undo those commands?

---

