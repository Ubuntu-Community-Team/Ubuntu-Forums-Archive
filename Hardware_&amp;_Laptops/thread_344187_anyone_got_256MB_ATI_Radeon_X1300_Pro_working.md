---
title: "anyone got 256MB ATI Radeon X1300 Pro working?"
date: 2007-01-22
forum: Hardware &amp; Laptops
---

### Post by Fittersman on 2007-01-22
i was wondering if anyone has gotten the 256MB ATI Radeon X1300 Pro working on ubuntu yet, because before i buy a new computer i want to know if its guna work on ubuntu or not

yes i have searched around and found a few people still trying to get it to work, nobody that has been successful yet though)

also if anyone has used it for pc (windows) games yet, i would like to know how it fairs out :D (im mainly a command and conquer generals/zero hour so if you have used that game...) and how much of the 256 is actually dedicated to the video card and how much of it is shared? (i have been looking at laptops lately and found that some video card have dedicated and shared so im not sure if its hte same for desktops too, or when the say 256 if they mean that it actually has 256 on it....)

---

### Post by Homunculi on 2007-01-24
i had troubles getting mine to work ... 
i have : 
ati X1300 256 agp
intel 2.8ghx 
1gb ram 
2 250gb 16mb cache harddisks 
sb audigy
3com 10/100 

 i got the ati card to wok after trying solaris /fedora and ubuntu (dapper) 
this is what you can do - it is a open source driver .. i hope it helps 

eneable the restricted repository in the /etc/apt/sources.list (remove the # marks from in from of them) 
using the command: sudo gedit  save.
use gedit to edit the xorg.conf  (eg) sudo gedit /etc/X11/xorg.conf ...
add the lines  at the end of the xorg.conf file
Section "Extensions"
            Option "Composite" "Disable"
EndSection

then you want to do some updateing : 

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)  // it might say that they are already installed 
sudo apt-get install xorg-driver-fglrx
sudo depmod -a

after that is all done then 
sudo aticonfig --initial 
and last but not least 
sudo aticonfig --overlay-type=Xv

and i have now a nice looking desktop no troubles @ 1280x1024 
gook luck

---

### Post by Fittersman on 2007-01-24
have you played any pc games on it? cuz if it plays games (command and conquer generals) well and it works on ubuntu then its a good card for me.

---

### Post by lafw on 2007-11-21
Hi!

A very good source for installing ATI related drivers is the Unofficial ATI Linux driver wiki. In it, I found the necessary information to get my ATI radeon X1300 pro to work.

The wiki page I used was the following:

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

In brief, all I had to do is to click on System > Administration > Software Sources to check if the "Propietary drivers for devices (restricted)" box was enabled (it should be).

Then, I clicked on System > Administration > Restricted Drivers Manager and enabled the box refering to the ATI accelerated graphics driver.

After that, I just needed to reboot my system and everything now works awesome!

Hope this helps...

---

