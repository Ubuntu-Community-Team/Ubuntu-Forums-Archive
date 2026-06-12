---
title: "Drapper and Dell Inspiron 6400"
date: 2006-09-12
forum: Hardware &amp; Laptops
---

### Post by arthur_kalm on 2006-09-12
Hi everyone,

I'm really thinking about getting a Dell Inspiron 6400 (the Core 2 Duo one with an X1400). I wanted to know if anyone here has had experience with this laptop and whether they were able to install Drapper on it? Were there any problems?

The [Core 2 Duo page]("https://wiki.ubuntu.com/Core_2_Duo_Support") doesn't list the Dell Inspiron. Has there been no problems with the dual core aspect?

Thank you for your time.

---

### Post by lifeempowered.com on 2006-09-12
I have a dell inspiron 6400 with:
core duo 1.66
1 gig ram
120 gig HD
1280x800 screen
ati x1300 card
dvd rw
firewire
sound (sigmatel)
dell wifi (broadcom chipset)
cardreader

Here's what didn't work:
wifi

Not Tested:
card reader
suspend/hibernate

The problem with the wifi, somewhat unknown.  I followed 3 different guides to make it work and nothing worked.  I got to where the wifi light lit and it saw the networks, but didn't get an ip.

I'm going to try it again, but want a better how to first since I rely on wifi.

---

### Post by Zaffe on 2006-09-13
6400 core duo here

I have the Dell 1390 wireless working with ndiswrapper, but u have to download a new version cuz the one that comes with dapper is old.

[http://www.ubuntuforums.org/showthread.php?t=193350](http://www.ubuntuforums.org/showthread.php?t=193350)

Suspend/hibernate works too.. no problems with ati x1300.

---

### Post by lifeempowered.com on 2006-09-13
Ok, I've completed a step by step for the Dell Inspiron 6400 with compiz working!  My particular setup has the ATI x1300, the Dell 1390 wireless, and the 1280x800 res, 1.6 core duo, sony dvd, etc...  I'll post it in the morning after one more test.

Only thing not working: card reader.

My how to guide:
Updated as of Sep 19 here: [http://ubuntuforums.org/showthread.php?t=257684](http://ubuntuforums.org/showthread.php?t=257684)

---

### Post by Zaffe on 2006-09-15
Mmm.. this is what i did for the wireless dell 1390

1) First remove the old ndiswrapper that comes with dapper
```

sodo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

```

2) Get the needed tools for install
```

sudo apt-get install build-essential linux-headers-386 linux-headers-686

```

3) Unpack ndiswrapper & install 
```

tar xvzf ndiswrapper-1.17.tar.gz
cd ndiswrapper-1.17
make
sudo make install

```

4) Get the drivers from windows & check
```

cd ~/.wine/drive_c/dell/drivers/R115321/DRIVER
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper
dmesg

```

Thats all.

sudo network-admin should show u wlan0

---

