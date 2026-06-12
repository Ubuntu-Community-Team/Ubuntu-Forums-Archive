---
title: "Internet connection problems"
date: 2008-08-31
forum: General Help
---

### Post by _King_Q_ on 2008-08-31
Hi im new here and i need a bit of help

my brother recently sent me a laptop with ubuntu installed which is great but i can seem to get my home internet working

as of right now i only have my modem with 1 ethernet cord and when i plug in my ethernet cord to my laptop it lights up showing it is connected but i cant connect to the internet

i use the same method at work and its perfectly fine but at home it sucks

i have comcast if that helps any

i appreciate any help i can get

---

### Post by pytheas22 on 2008-09-01
It probably has to do with Comcast more than Ubuntu, since it works fine at work.  Did you ever have to install software on Windows to get things working with Comcast?  And are you plugged directly into the Internet, or are you behind a router/firewall?

After the ethernet cord is plugged into your computer, please run these commands and post the output here:
```

lshw -C Network
ifconfig
ping -c 3 google.com
ping -c 3 72.14.207.99
host google.com
cat /etc/resolv.conf
```

That will help to figure out what's going on.

(Keep mind that if you can't get online on the Ubuntu laptop at all at home, you can copy the output from those commands into a text file and either paste it here from work, or transfer it to another computer on a USB drive.)

---

