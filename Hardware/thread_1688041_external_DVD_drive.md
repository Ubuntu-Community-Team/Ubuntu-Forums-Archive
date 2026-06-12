---
title: "external DVD drive"
date: 2011-02-14
forum: Hardware
---

### Post by zimaaron on 2011-02-14
Hey all, 
I'm pretty new to Ubuntu and Linux in general, but the site has been a great help so far. 
I have ubuntu 10.10 running on an asus eeepc. The big issue is there is no cd/dvd drive. My uncle gave me a HP dvd1040 dvd reader/burner that is meant for a desktop machine. I bought the IDE cables to hook it up via usb, and it almost works. It powers on, when I put in a dvd, it shows up with the name of the dvd. The issue is that I can't read any of the discs I put in, only the title seems to show up. Any thoughts? This seems pretty strange to me...

Thanks a bunch!

---

### Post by jerrrys on 2011-02-16
two things, first do you have 'ubuntu restricted extras' installed ? and

[ATTACH]183625[/ATTACH]

---

### Post by PaulReaver on 2011-02-16
movie discs???


ubuntu-restricted-extras.... a bit like bringing a nuke to paintball. a touch excessive.



you only need to install codecs and libdvdcss

sudo apt-get install libdvdread4 libdvdnav4
sudo /usr/share/doc/libdvdread4/install-css.sh


restart your machine and when you try to play them it will automatically prompt you to install the correct codecs :)

---

