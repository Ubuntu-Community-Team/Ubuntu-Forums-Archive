---
title: "Ubuntu 8.10 Ibex LiveCD asking for username/password??"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by dislodge112 on 2008-12-18
I've searched the forum and it seems like people were having a similar problem on 8.04... you boot from the liveCD (not install), and it pulls up the login screen asking for username and password.

people suggested (where _ means entering nothing as the password):

"ubuntu/_"
"ubuntu/ubuntu"
"root/root"
"root/_"

i've tried every combination of these, including capitalizing the first letters... no luck :(

i've checked the disk for errors, no errors were found

i'd really like to boot into the live version so that i can play around, please help me.

---

### Post by Partyboi2 on 2008-12-18
If you downloaded the ubuntu iso make sure that the [[COLOR=Blue]md5sum [/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")match and try burning a new copy at x4 or less speed.  Out of curiosity  what happens when you choose Safe graphics mode (pressing F4 at the main menu) does it still ask for a password?

---

### Post by helpmekevin on 2009-03-22
The user name is ubuntu. When prompted with password, just hit enter without entering anything.

---

### Post by helpmekevin on 2009-03-28
I also just found out if you leave the login screen on for a while, about 15 seconds for me, without tinkering (doing anything) with it, 8.10 will automatically get into the desktop.

It is also not required to enter password to run sudo or get into the console (Ctrl-Alt F2, for example).

---

