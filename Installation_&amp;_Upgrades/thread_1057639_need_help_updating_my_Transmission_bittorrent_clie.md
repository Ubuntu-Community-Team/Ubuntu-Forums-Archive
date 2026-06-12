---
title: "need help updating my Transmission bittorrent client from 1.06"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by EvilBear on 2009-02-02
Hi. I need help updating my Transmission bittorrent client from 1.06 to something newer. Anyone there that can walk me through it? I know a little of cli commands.

---

### Post by Partyboi2 on 2009-02-02
What version of Ubuntu are you using?

---

### Post by EvilBear on 2009-02-02
Hardy 8.04

---

### Post by Partyboi2 on 2009-02-02
One option is to use  Transmission 1.22 which is in the backports repository for hardy.
Go to Software Sources (System>Admin>Software Sources) and on the update tab enable backports, then close Software Sources and update to 1.22

Another option is for transmission 1.42 is to add the 3rd party repo
Add 
```
deb http://ppa.launchpad.net/transmissionbt/ubuntu hardy main
deb-src http://ppa.launchpad.net/transmissionbt/ubuntu hardy main
``` to your 3rd party list in Software Sources or by the terminal
```
gksu gedit /etc/apt/sources/list
```
add the above repos, then save and back in the terminal add the key
```
gpg --keyserver keyserver.ubuntu.com --recv 976b5901365c5ca1
gpg --export --armor 976b5901365c5ca1 | sudo apt-key add -
```
Then update
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by EvilBear on 2009-02-02
Up graded it...now trying to get it to work. :)

---

### Post by EvilBear on 2009-02-02
Thank you, it worked. Now to see if it fixes my closed port problem. Any setting i should change from default for this upgraded version?

---

### Post by Partyboi2 on 2009-02-02
I am not sure, should work fine with default settings though.

---

### Post by EvilBear on 2009-02-02
Yep, ort problem seems fixed. used to dwnld speeds never more that 100kbs, easily hitting over 300kbs on average. Thank you very much. People like you are why people like my started using computers again, after swearing off the things because of certain OS's that were not nice to us :)

---

### Post by Partyboi2 on 2009-02-02
Happy to help, all the best :)

---

