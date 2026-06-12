---
title: "Network Manager"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by Baelfael on 2007-02-10
I need help. I have a WPC54G v.3.1 wireless card, and I followed a guide on this site on how to set up NetworkManager. Some problems:

a) I'm totally new with Ubuntu
b) The NetworkManager thing says theres no connections available... how do I actually OPEN this NetworkManager?
c) I don't know how to connect to the internet with my card. I try going to the terminal and typing "sudo dhclient eth1" but it tries to connect and then times out eventually. I need major help.

---

### Post by gradedcheese on 2007-02-10
Network Manager does its own management of the interfaces, so basically you have to choose: do you want Network Manager or the original method (where you can run ifconfig and iwconfig)?  If you chose network manager, then be aware that it will ignore any interface managed by the original facility.  That is, if you want it to use eth1, then you need to remove eth1 from /etc/network/interfaces and then try again.  To do that, open the file in a text editor ("sudo gedit /etc/network/interfaces" should work), comment out (ie: add a # in front of) any line that contains eth1, and save.  Now start network manager.  If it was already running, you could:

killall nm-applet
nm-applet &

to restart it (don't close the terminal).  If that worked, then log out of gnome and log back in again.

---

### Post by Baelfael on 2007-02-10
That didn't seem to work. :( 

Network Manager still says "No network devices have been found".

---

### Post by gradedcheese on 2007-02-10
try:

sudo /etc/init.d/networking restart

and then restart network manager...

---

### Post by icalderus on 2007-02-19
I am in the same boat...however when I type in nm-applet as a normal user ( non root) I see the following:


nm-applet not found..

for the life of me i cannot start nor locate nor find the icon for the NetWork Manager application


can someone assist with this? is this a PATH issue ( ive tried as root and normal user)

i started out with  Mandrake and chose ubuntu but this desktop and navigation is turning out to be a little more tricky than i had anticipated! anyhelp with network manager would help

** I am trying to enable wireless connection with my eth1(nic) entry..

tx

---

