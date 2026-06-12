---
title: "many headaches with Ubuntu - noob"
date: 2020-02-03
forum: Hardware
---

### Post by mastercore on 2020-02-03
This is my second time running ubuntu in my life. First was in 2007 and it took some screwing around but I did manage to get it to work passably well on an old clapped out laptop. Now for my second and I hope longer term relationship with Ubuntu, but it is off to a shaky start

I had a home brew rig which was aging and I needed upgrading bad. Before I lay the old machine to rest, I downloaded Ubuntu 18.04.3 onto a stick and booted it up on to test the peripherals, which would pretty much be staying the same (wireless keyboard/mouse, screen, wifi usb stick, etc...) All looked good so I rebuilt the computer.

Now I installed Ubuntu, many headaches I did not expect have cropped up.
Straight off the bat is the wifi usb stick is ignored, and my screen resolution is stuck in 1024x768 when the screen is 1920x1080

I have to admit guys, after an hour of messing about and not getting anywhere on just these first 2 issues is disheartening.
It is late an night and I hope to have some new inspirations tomorrow morning, but this is a work computer and it cannot be left in an unusable condition. I really hate myself for thinking this, but I may have to go and install windows 10 if Linux is still not up for it.



Just an idea of what I have as hardware in the new computer...

[COLOR=#000000][FONT=Arial]Gigabyte B450 Gaming X - motherboard[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]AMD RYZEN 7 1800X - chipset[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Crucial 32GB KIT(16GBX2) DDR4 2400 MT - RAM[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Sapphire Radeon RX 5700 XT Nitro+ (8GB) - GPU

(should be a pretty sweet and fast machine with linux. really not looking forward to falling back onto win10)



The display is a Samsung SyncMaster XL2370 attached with HDMI
The WIFI adapter is: Fritz! WLAN usb stick AC 430[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]


I would be super appreciative if anyone out there could point me in the right direction to get these first 2 issues sorted.[/FONT][/COLOR]

---

### Post by him610 on 2020-02-03
Welcome to the forum Mastercore,
We were all noobs at one time. It looks like you have built a nice system. There are some really knowledgeable people who frequent these forums, and will be glad to help. How about providing a few more details by running *inxi F* from a terminal and posting the results between the code tags?

---

### Post by CatKiller on 2020-02-03
> **mastercore said:**
> [COLOR=#000000][FONT=Arial]Sapphire Radeon RX 5700 XT Nitro+ (8GB) - GPU[/FONT][/COLOR]

This needs new stuff. New kernel, ideally a newer version of Mesa.

For the new kernel, there are three options. 18.04.**3**, which is the install image you're using, comes with the 5.0 kernel. What you're after is the 5.3 kernel. If you install from your 18.04.3 image and update normally you'll be bumped up to 18.04.**4**, which has that newer kernel. Obviously you'll need to either get your wireless dongle to work or plug into the network before you can do that update. That's option 1. Otherwise, Ubuntu 19.10, which isn't an LTS release, comes with the 5.3 kernel. That's option 2. Option 3 is to wait for them to release an 18.04.4 install image: it's roadmapped for sometime this month, but I don't know exactly when.

For the new version of Mesa, you have quite a few options. 19.10 will come with a newer version of Mesa than 18.04, but there are a lot of PPAs that will provide newer versions for 18.04. Just a bit newer, latest release, and development pre-release are all available, depending on which PPA you use. I don't have AMD graphics myself, but I understand that [this PPA](https://launchpad.net/~kisak/+archive/ubuntu/kisak-mesa) is popular with people that do: the latest Mesa point release with the ACO shader compiler instead of LLVM.

---

### Post by CelticWarrior on 2020-02-03
As above.

Regarding the WiFi, "[COLOR=#000000][FONT=Arial]Fritz! WLAN usb stick AC 430" isn't very useful. Please run 'lsusb' in terminal and post the line about the WiFi so we can identify the chipset and then find out what drivers it needs.[/FONT][/COLOR]

---

### Post by CatKiller on 2020-02-03
> **mastercore said:**
> [COLOR=#000000][FONT=Arial]The WIFI adapter is: Fritz! WLAN usb stick AC 430[/FONT][/COLOR]

If the Google translation of [this page](https://wiki.ubuntuusers.de/WLAN/Karten/AVM/) is accurate, that should work with a 5.3 kernel. If it's the MU-MIMO variant, which uses an entirely different chip, apparently it doesn't work.

---

### Post by mastercore on 2020-02-04
```
CPU~8 core AMD Ryzen 7 1800X Eight-Core (-MT-MCP-) speed/max~1868/3600 MHz Kernel~5.0.0-23-generic x86_64 Up~34 min Mem~1514.6/32174.4MB HDD~500.1GB(1.3% used) Procs~389 Client~Shell inxi~2.3.56
```

---

### Post by mastercore on 2020-02-04
```
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 048d:8297 Integrated Technology Express, Inc. 
Bus 001 Device 004: ID 057c:8502 AVM GmbH 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

The second last one is the wifi dongle

---

### Post by mastercore on 2020-02-04
Just did a ```
sudo apt-get dist-upgrade
``` in the hopes of shaking loose some of these problems, but no bananas yet

I have managed to drag a long ethernet cable through the office to get internet to the box but so far I am still wrestling with the screen resolution issue.

---

### Post by CelticWarrior on 2020-02-04
Why don't you try 19.10? Much better support for your hardware.

---

### Post by mastercore on 2020-02-05
Ok Guys,
I have downloaded 19.1 onto a stick and installed it onto my box. 1 Banana out of 2 for this thread have been achieved. Ubuntu immediately recognized the display and adjusted to the correct resolution. Yippeee
The second banana is still our of reach as my system still does not see the Wifi dongle.

But I have run into a snag...

Seems something has gone wrong with the system which blocks me from installing apps...
```
Unable to install "Font Manager": E: Cound not get lock /var/lib/dpkg/long-frontend. It is held by process 3459 (apt-get) - open (11: Resource temporarily unavailable)
```
This is from the front end Ubuntu SW manager

I get a different but similar notification if I try apt-get in the terminal.


Is this one of the bugs floating around the 19.1 version?

---

### Post by mastercore on 2020-02-05
p.s.
This is what I get in the terminal....```
E: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 2849 (apt-get) - open (11: Resource temporarily unavailable)
N: Be aware that removing the lock file is not a solution and may break your system.
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?
```

This was right after a reboot by the way

---

### Post by mastablasta on 2020-02-05
something locked the apt-get. maybe something is performing an update in the background or the update is not finished. the process has a number. if you use top or htop you can see the processes and numbers next to them you can then identify the process blocking the whole thing.

for the wi-fi you need to identify the chip, then you can check what is blocking the driver or why is it failing to load (which is strange, if it loaded normally in live session). if chip really did work in live session, you will be able to get this chip information from there. the chip could be "*somename*" but then using realtek drivers to run. 

sweet setup. i am sure we will get it working. and just in case we can't  the usb wi-fi chips that are fully linux compatible (and tested to work well with linux) are sold in shops that sell rapsberrypi and they are really cheap.

i just made a somewhat similar setup for my kid. but weaker nvidia GPU. he will be doing primarily gaming and youtube videos, but lately he discovered e-mail, search engines, and wikipedia. so far he is very pleased. and everything worked just as it should from the start. he might still buy windows later, but so far he is preoccupied with linux games and windows games that work well in Linux. we installed Kubuntu on it as i prefer that interface and simply love some KDE applications. kids got used to it fast before when we switched to KDE in 2019 (transitioning from Winxp desktop to KDE was easy for them).

---

### Post by mastercore on 2020-02-05
I have marked this thread as solved because it is partially true.
Moving up to 19.10 solved the display resolution issue, but the wifi dongle problem persists.
A new issue with installing new apps has prompted me to split this thread off into individual problem threads as I step by step get this machine up and running.

---

### Post by mastablasta on 2020-02-06
fully compatible modules (tested to work with linux) from 7 EUR up: [https://thepihut.com/pages/search-results?q=usb%20wifi&page_num=5](https://thepihut.com/pages/search-results?q=usb%20wifi&page_num=5)

the app install issue is likely connected with apt-get being locked by a process.

---

