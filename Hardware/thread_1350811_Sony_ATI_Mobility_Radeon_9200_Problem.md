---
title: "Sony ATI Mobility Radeon 9200 Problem"
date: 2009-12-09
forum: Hardware
---

### Post by steward on 2009-12-09
Hi 
I m absolutely new to Ubuntu 9.10..
I d like to install My graphic card (ATI Mobility Radeon 9200) on UBUNTU 9.10. Would you please guide me step by step to install this critical driver because it really bothers my eye.

---

### Post by phillw on 2009-12-09
> **steward said:**
> Hi 
I m absolutely new to Ubuntu 9.10..
I d like to install My graphic card (ATI Mobility Radeon 9200) on UBUNTU 9.10. Would you please guide me step by step to install this critical driver because it really bothers my eye.


Hi, this is from the video thread in Installation and Upgrade area of the forum.
[http://ubuntuforums.org/showthread.php?t=1305459&page=27](http://ubuntuforums.org/showthread.php?t=1305459&page=27)

Having read it, I *think* you need to :

>                      Originally Posted by **DustofDust**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8240104#post8240104")                 
                 [I]sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon xorg-driver-fglrx
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
dpkg-reconfigure xserver-xorg
sudo apt-get install xserver-xorg-video-mach64

last line or radeon or fglrx depending which generation of card you have.[/I]
                                 For your card, the last line would be one of these.

> if you have a radeon just drop my last line with mach64 and use instead the following

sudo apt-get install xserver-xorg-video-radeon

if you want to use the closed source drivers and you have a newer card which is supported by ati then it is 

sudo apt-get install xserver-xorg-video-fglrx
That should get you running, for any further queries - you'd have to post to that thread.

Regards,

Phill.

Assuming it all works, and it should - say thanks to DustofDust for the solution

---

