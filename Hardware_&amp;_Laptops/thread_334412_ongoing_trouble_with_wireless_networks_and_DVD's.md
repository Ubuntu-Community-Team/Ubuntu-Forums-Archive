---
title: "ongoing trouble with wireless networks and DVD's"
date: 2007-01-08
forum: Hardware &amp; Laptops
---

### Post by tich on 2007-01-08
i have two really big problems with ubuntu right now...

the first i've had since breezy, if you can believe it. 
i can't burn data-dvd's. after trying with breezy and for a while in dapper i eventually bought a usb drive but it would be really nice to get this up and running.

[https://launchpad.net/ubuntu/+ticket/3010](https://launchpad.net/ubuntu/+ticket/3010)


the second problem has been somewhat more recent, it occurred when i upgraded to edgy and with it i can't connect to/access my wireless router.

[https://launchpad.net/ubuntu/+ticket/2375](https://launchpad.net/ubuntu/+ticket/2375)

the links to my bug reports are under the appropriate blurb. i placed the reports up a while ago but i think i have stumped the kind folks that deal with the bug reports.
all the relevant data that i could think of, or was asked to provide is there... if some other information would be useful please let me know i will post it in both locations.

also if it is frustrating to go to the bug reports and back here let me know and i will copy all the data from there to here.

---

### Post by scrooge_74 on 2007-01-08
Did you tty the Howto for wireless ?

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

[http://www.ubuntuforums.org/showthread.php?t=269438&highlight=wireless+network](http://www.ubuntuforums.org/showthread.php?t=269438&highlight=wireless+network)

---

### Post by tich on 2007-01-09
i checked out the threads and worked up the gumption to follow the advice on:
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

i have no idea what it did but it seems that i am almost there.  it now shows me wireless connections (all of them in the building). 2 of which are passworded and mine (open) when i click on mine it searches and searches but can never connect to it. the other ones a dialogue box pops up right away asking for a password (but it isn't my network so i have no idea if it will go any further than that)

and of course the wired network works just fine (other wise this wouldn't be happening)

any ideas why i can't connect to my network?

i just noticed that after a while the wireless networks disappear from the list in the network-manager, leaving only the 'wired' option and a heading of 'wireless' with nothing listed under it.

---

### Post by scrooge_74 on 2007-01-09
Wireless can be a pain sometimes, try installing Wifi radar and see if it makes it easier to connect.  I still have troubles some time.

from a terminal window you can do iwlist eth1(or the name of your card) scanning

it will give you more info on the networks available

---

