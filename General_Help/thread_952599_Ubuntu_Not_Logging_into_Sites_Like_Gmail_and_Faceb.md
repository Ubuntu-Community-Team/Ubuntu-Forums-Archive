---
title: "Ubuntu Not Logging into Sites Like Gmail and Facebook on an Intel Pentium 4 Mobile"
date: 2008-10-19
forum: General Help
---

### Post by Akilias on 2008-10-19
Hello, recently I've been having trouble accessing websites like Gmail and Facebook on Ubuntu. My laptop can make it as far as the login screen and then never logs in. I use Firefox 3.0.3 on an Intel Pentium 4 Mobile CPU 1.60GHz with 640 MB of RAM. I tried logging into these sites on Windows XP on the same computer and they worked just fine. Any help is much appreciated, and thank you in advance.

P.S. On Ubuntu my Nvidia adapter is enabled. It's an NVIDIA GeForce2 Go.

---

### Post by sethvath on 2008-10-19
Gmail and facebook are the only sites you cannot access? Did you try a non javascript heavy site?

---

### Post by Akilias on 2008-10-19
Yup, all non java heavy sites are working just fine.

---

### Post by Akilias on 2008-10-19
bump...

---

### Post by sethvath on 2008-10-20
My guess is something is wrong with how javascript is rendering. Without any error codes its hard to tell. 

Search for your firefox folder
In terminal: cd /folder/to/firefox .ie /usr/bin/firefox
./firefox (this will cause you to run firefox in terminal)

post any error codes you see from terminal here

---

### Post by Hangwire on 2008-10-20
A reinstall never hurt anybody.
Reinstall firefox and java?

---

### Post by tonybaqain on 2008-10-20
use this :
[list]
[*] open a new tab in firefox
[*] write **about:config**
[*] if any message appears, click on **i'll be careful**
[*] in the filter inputbox, write: general.useragent.vendor
[*] at bottom, the left panel will display the same search filter, double click on that
[*] change the value to **Mozilla/4.0 ( compatible; MSIE 7.0; Windows NT 5.1)**
[*] restart firefox, and try again .
[/list]

have fun.

---

