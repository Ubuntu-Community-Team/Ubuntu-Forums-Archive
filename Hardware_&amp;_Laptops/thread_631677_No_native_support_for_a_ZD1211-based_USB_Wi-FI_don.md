---
title: "No native support for a ZD1211-based USB Wi-FI dongle ?"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by Shinigami Delroën on 2007-12-04
Hi !

I have a Sagem XG-760A dongle, which is based on the ZD1211 chipset. It was natively supported when I used Feisty.

I'va had a serious problem with Feisty so I've had to format my system partition. Since I installed Gutsy, that USB dongle is not natively supported anymore.

I've found an old Dapper documentation explaining how to re-compile the driver from the sources, but I find it quite strong for a "natively" material.

Can someone explain what to do ?

Thank you !

---

### Post by DraQla on 2008-02-01
I have a similar problem, mainly an "onboard" zd1211(b?) device that doesn't work, or even show up, though everyone tells me it should be supported. I tried half a dozen how-to's and none worked for me (for some I didn't even find the required files to begin with) - maybe because I'm quite new to Linux.
Help, please?:confused:

(And sorry for just tagging along, Shinigami Delroën)

---

### Post by rye_ on 2008-02-13
Two methods spring to mind, I'd try the first to begin with though I have used the second myself.

/*
method 1
*/

sudo apt-get install zd1211-source
module-assistant update
module-assistant build zd1211

Note: I cant remember if the last two commands require a preceding 'sudo'

/*
method 2
*/

wget [http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-2.6
make
sudo make install
sudo make load

I hope that helps.

Ryan

---

