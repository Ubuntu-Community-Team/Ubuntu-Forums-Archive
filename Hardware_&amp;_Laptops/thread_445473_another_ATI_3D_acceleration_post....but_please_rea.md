---
title: "another ATI 3D acceleration post....but please read"
date: 2007-05-15
forum: Hardware &amp; Laptops
---

### Post by porphiron on 2007-05-15
Lo folks,

before i start, please don't take this post as a gripe or a flame am running xubuntu edgy, ubuntu has one of the best communities out there, with its help i've now installed xubuntu edgy on 4 machines including this lappy , have used this forum heavily and found an answer to every problem faced so far and have a couple machines left to sort and will carry on using it, simply because i love it. But am now am reaching the end of my tether, espesh after reading the output from the ENVY app...(which i will get to in a mo)

right, my problem is this, am trying to get 3D acceleration working on my half decent spec (to me. ;) ), acer travel mate 2200, its got a 2.66 celeron D with  1.5gb mem / 120gb hhd.

unfortunately, acer for some odd reason fitted it with a 9100 IGP chip, try as i might, i cannot get this to use the fglrx accelerated drivers, so i can use cedega.

so far i have followed just about every howto or info snippet about getting ati accelerated drivers working although i did manage to get direct GL working. but not the actual 3D acceleration required...ho hum.

after reboot all i get is this

to make sure that you have the latest version.                   &#9618;
Module Loader present
 Markers: (--) probed, (**) from config file,
(==) default setting,       &#9618;
(++) from command line, (!!) notice,
(II) informational,         &#9618;
(WW) warning, (EE) error, (NI) not
implemented, (??) unknown.    &#9646;
(==) Log file: "/var/log/Xorg.0.log", Time: Wed
May 16 03:40:50 2007     &#9618;
(==) Using config file: "/etc/X11/xorg.conf"
 (EE) No devices detected.

i've edited most of the spacing and rubbish, but sorry if some still remains.

am getting kinda peeved as i've followed every post i've come across to the letter, but what irks me is that, before hand this machine had an old SuSE 9.3 installand also XP Home, both of which worked fine, and most games ran ok. Ok  i can see that it would work ok under XP as someones pocket has been lined and driver support has been purchased, but hopefully this will now change with the latest news of ati going open source.

What has realy irked me is that SuSE 9.3 had no problem working with this laptop or one of the other machines both have ati cards the laptop as i've said is a 9100 IGP, the desktop has a 9250 card, but both refuse to use any kind of acceleration...for pities sake, if a 6 yr old distro can run acceleration (ok i know the cards were the thing for that time, but should still work now tho!, surly the same kind of drivers are still available??),but very old nvidia drivers work fine, is it that (x)ubuntu only caters for nvidia cards, if so why not mention it, which leads me onto somthing rather annoying

I recently tried the new version of ENVY....the nice gui that helps you install the right driver e.t.c....it gave me some startling news in the form of...Your graphic card has been detected as a ATI Mobility Radeon 9000/9100 IGP Series
Your graphic card is supported by the legacy Driver
ENVY ERROR: ATI's legacy driver does not support your operative system.

is that it then?

whats the point of using an distro if its not supported

will i ever get acceleration working?

look if it could be done a few years ago, why the hell why cant it be done now....

am seriously looking at putting m$ back on....

sorry but its late an am very tired an p-d off

(no rant intended you guys work very hard to sort stuff out and so far this is the only sticking point for me....i even got the wireless stuff sorted just from a couple of posts)

[porph]

---

### Post by jocko on 2007-05-16
The problem is that ATI stopped developing drivers for older cards (older than radeon 9500), which is something the ubuntu developers have no way of changing.
The "legacy" driver is the last version of ATIs driver that contain support for the older cards, but this driver did not contain support for xorg 7.2 or kernel 2.6.20, so it will only work on older distros.
Again, something the ubuntu developers have no power to change.

The open source driver included in xorg does support older cards, so you should have accelerated graphics as long as you DON*T try to install any other driver.

---

### Post by porphiron on 2007-05-16
cheers for the  very quick reply!

ah, well that answers that then! :( ,

erm pardon my ignorance, but the accelerated drivers that come with xorg, would those be  the "tungsten" ones, as cedega doesn't recognise the system as accelerated with them (even tho the cogs spin that fast they could catch fire :) ).

if its not the drivers mentioned above, which ones are we talking about?, and how do I enable em?.

do i need to to remove all the restricted driver stuff e.t.c.??

thanks again!

[porph]

---

### Post by pigboy306 on 2007-05-19
I too have a TM 2200... Have you got this working if so how... in simple terms for a noob please!!! Have you got the correct resoloution on the screen again if so how any help appreciated.

Have you got the wireless working?

---

### Post by porphiron on 2007-05-19
Pigboy306!,

I hope this helps.....still not sure wether acceleration is working properly (cedega says not, but then tbh it blows!), but this link will enable GL rendering,

[http://ubuntuforums.org/showthread.php?t=246746&highlight=ati](http://ubuntuforums.org/showthread.php?t=246746&highlight=ati),

and the wireless card, or as i like to refer to it, the cause of most of my pain,

i sorted it eventually, basically, try the following

open a terminal, or use a console (ctrl+alt+f1)

login and type lspci and look for somthing like this,

Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)

I dont mean to be a bit vague, but google for the  INPROCOMM IPN 2220 Wireless LAN Adapter, bit and you should find some windows drivers, grab em and apt-get install ndiswrapper, or use synaptic,

ndiswrapper is pretty simple, afaik, unzip the driver package and using terminal/console cd to its contents then ndiswrapper -i ( i think) <name.inf>, try ndiswrapper --help, but it is pretty simple, and then ndiswrapper -m sorts out the modprobe stuff, you should then get a new entry in Applications ->system ->network-> wireless adapter.

right, the way i managed to config it, was using iwconfig, type iwconfig --help in console/terminal and set everything up that way, not forgetting to use iwconfig commit, to commit each change......oh and remember to hit the orange button at boot....

sorry for the crappyness of the info, but i hope some of it helps

---

### Post by pigboy306 on 2007-05-21
I sort of got the wireless card working. :???: 
For all travelmate users here goes.

get the windows driver and ndiswrapper installed.

cd to the directory

sudo ndiswrapper -i drivername.inf
iwlist wlano0 scan
 note the name of your network
sudo iwconfig wlan0 essid MATTNETWORK
sudo iwconfig wlan0 key restricted <your wep key goes here>
sudo dhclient wlan0

that works for me.

unfortunately i have to do the last three lines each time i start.

---

### Post by porphiron on 2007-05-21
make sure you use the commit command....i.e iwconfig commit, and then you shouldnt have to, but yeah, thats it in a nutshell

---

### Post by porphiron on 2007-05-21
let me try that one again...

when setting up the wlan, use iwconfig <setting>, then after setting, each setting...ahem....use iwconfig commit, then you shouldn't have to run the last three of your commands every time as the settings should be written to a config file (of which i have never found)

is what i meant

[porph]

---

### Post by pigboy306 on 2007-05-23
Thanks for that... I am running ubunut on my laptop as an experiment really, sort of getting used to it any recommendations for advice sites

---

