---
title: "HP Mini 210-1041NR - Track pad and Wireless not working"
date: 2010-11-05
forum: Hardware
---

### Post by JoeyCyanide on 2010-11-05
I have a HP mini 210-1041NR netbook and cant seem to get the trackpad to work properly or the wireless networking to work at all.

the track pad moves the mouse but no secondary click and the gestures do not work such as two finger scrolling. 

the wireless does not work at all though a driver is installed and active 

both work under Windows 7 but not Ubuntu 10.10
plus I'm kinda new at ubuntu
and win7 and ubuntu are on separate HDD's that I swap. 

if anyone can help please let me know.
thanks

---

### Post by djhorry on 2010-11-06
> **JoeyCyanide said:**
> I have a HP mini 210-1041NR netbook and cant seem to get the trackpad to work properly or the wireless networking to work at all.

the track pad moves the mouse but no secondary click and the gestures do not work such as two finger scrolling. 

the wireless does not work at all though a driver is installed and active 

both work under Windows 7 but not Ubuntu 10.10
plus I'm kinda new at ubuntu
and win7 and ubuntu are on separate HDD's that I swap. 

if anyone can help please let me know.
thanks

I own an ASUS m51vr laptop, which has wireless as well. To make my wireless run correctly I had to open Applications/Ubuntu Software Center and search for "WiFi Radar". I've installed it and rebooted my laptop. It works at least twice as fast as my Win7 genuine driver from ASUS. But to install the WiFi Radar you need an internet cable plugged in. :)
As for the pad, I don't know what to say, I didn't have any problems at all.

---

### Post by P4man on 2010-11-06
> **JoeyCyanide said:**
> I have a HP mini 210-1041NR netbook and cant seem to get the trackpad to work properly or the wireless networking to work at all.

the track pad moves the mouse but no secondary click and the gestures do not work such as two finger scrolling. 

the wireless does not work at all though a driver is installed and active 

both work under Windows 7 but not Ubuntu 10.10
plus I'm kinda new at ubuntu
and win7 and ubuntu are on separate HDD's that I swap. 

if anyone can help please let me know.
thanks

Lets start by finding out exactly what hardware is in your machine. Open a terminal form application > accessories > terminal

and type in:

```
lspci
```

Lets also check the status of the wifi kill switch with:

```
sudo rfkill -list
```

and finally your network configuration with

```
lshw -C
```

Copy paste the output of each of those commands here (I am assuming you have a temporarily wired internet connection, if not let me know and Ill explain how to put the output on  a USB stick. It will be a bit much to type :) ).

BTW, wifi rader is not likely the solution to your problem. Id advice not to install it yet until we find out a bit more.

---

### Post by wack_drummer on 2010-11-06
I'm actually having the same issue, only on a HP mini 210-1092dx. I have problems with both the touch pad and wireless. I have come across multiple drivers for ubuntu 10.10 for broadcom wifi unfortunately none of them seem to work. As for my specs the wireless card is BCM94312HMG and it does have a on/off switch as a key (doesn't work though). :confused:

---

### Post by P4man on 2010-11-06
For a broadcom bcm 4312 have a look here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

You may need the STA or the B43 driver, one or the other, but not both. Im not sure which of both you will need (possibly either works). Its by far easiest if you can connect a network cable temporarily.

Also do make sure to check the status of the killswitch with

```
sudo rfkill list
```

Make sure none is hardblocked (if it is, try the switch or keyboard combination to activate the wireless)

---

### Post by wack_drummer on 2010-11-06
I'm still working on the wireless issues, but as far as the hp mini touch pad buttons not working there was a thread about "right click on hp mini not working" that solved my issue.:)

---

### Post by wack_drummer on 2010-11-06
**when I  go through the different drivers I find that for 10.10 it wants me to do this:**

**10.10 Maverick Meerkat**

 Navigate the install media and double click to install bcmwl-kernel-source



which I attempted to do, and came up with no such file in my install media.:confused: I'm really confused at this point....and it really doesn't help that my netbook doesn't have temp wired internet to begin with.

side note: I did check the kill switch for my card, all are not blocked.
** **

---

### Post by P4man on 2010-11-06
On a regular live cd (or USB in your case?) you should have it in

/media/<yourusb_or_cd_drive>/pool/restricted/b/bcmwl/

If its not, download it from here:
[http://packages.ubuntu.com/maverick/bcmwl-kernel-source](http://packages.ubuntu.com/maverick/bcmwl-kernel-source)

There is a good chance it will tell you it needs other dependant packages, you will have to download them as well (they are probably linked on that same page in the "related" section)

---

### Post by wack_drummer on 2010-11-06
I got it to work via STA driver! great success lol! :P thanks for all your help p4man

---

### Post by the pwner224 on 2011-11-25
Hi,
I also have a mini 210-1041nr. Natty narwhal automatically installed the wifi's drivers, but it is under the additional drivers option in system settings. however, my touchpad has a few problems:
1. the mouse can move on the screen when i am using the left click button and my finger moves.
2. the right click doesnt work.
the scrolling works, and i can right click by tapping with two fingers.

---

