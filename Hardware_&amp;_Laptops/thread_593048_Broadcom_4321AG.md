---
title: "Broadcom 4321AG"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by esei15 on 2007-10-26
ok i've been trying forever to install a driver for my broadcom 4321ag wireless card but nothing works. i've tried  ndiswrapper with the files included in vista and i've tried bcm43xx and neither work.


hp dv6449us

specs; 
    amd 64 x2 tl-56 1.8ghz
    nvidia geforce go 6150
    160gb harddrive
    2gb ram
    Ubuntu 7.10 (live cd right now)

---

### Post by Loyll on 2008-04-25
I just solved this problem with the same wifi card.

First install those two packages from this website:
[http://security.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/](http://security.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/)
1 - ndiswrapper-common_1.50-1ubuntu1_all.deb
2 - ndiswrapper-utils-1.9_1.50-1ubuntu1_amd64.deb (select your own platform)

Download this file from rapidshare (4321AG Wifi drivers):
[http://rapidshare.com/files/72536890/SP36684A.zip.html](http://rapidshare.com/files/72536890/SP36684A.zip.html)

Then type in those commands in a terminal window:
cd [path where you unpacked the drivers]

sudo ndiswrapper -i bcmwl5.inf

sudo ndiswrapper -m

sudo ndiswrapper -mi

sudo ndiswrapper -ma

sudo reboot now

Personnaly I disabled the Wifi switch on the laptop for the reboot but I don't think it is necessary. Activate it afterwards, you will now be able to detect wifi networks and connect to one of them. Left-click on the Network Manager and select Wireless Networks to do so.

Voilà.

---

### Post by mmellado on 2008-04-29
this ACTUALLY WORKS!!

i had been looking for a way to make my bcm 4321 card work for a month or so, i tried this for hardy heron, hardy beta and gusty gibbon, it works on the 3 versios, thanks a lot =D rep++

---

### Post by Standy on 2008-05-03
Thanks a lot!

If you are using Ubuntu 8.04 Desktop you'd find ndiswrapper in:
-> applications -> add/remove applications -> search for ndiswrapper and install the package called "Windows Wireless Drivers (Ndiswrapper driver installation tool)"

Good work! Thanks a bunch!:)

---

### Post by Loyll on 2008-06-10
So glad I helped you guys.

---

### Post by deltaprime on 2008-06-15
going to try it out now just got a new laptop so i gotta figure this out!
finished my install 2 mins ago and dissappointed that my net card did not work = (
once it does i can get back to hacking and cracking some new stuff i set up on my network the last few days yay!
 
thanks will reply later if it did not work 
 
thanks to you!
 
delta

---

### Post by afdanistan on 2008-06-26
Thank you so much! Worked perfectly. Brilliant!

---

