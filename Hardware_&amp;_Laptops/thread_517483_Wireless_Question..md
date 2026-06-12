---
title: "Wireless Question."
date: 2007-08-04
forum: Hardware &amp; Laptops
---

### Post by jseiser on 2007-08-04
Wheni run ubuntu i always server install, and then run evilwm and avoid all the gnome stuff.  Will i be able to use wireless internet on my new laptop without some sort of connection manager?  DHCP on my lan works on my desktop, but i ordered a everex laptop with internal wireless, and i want to take it to school and use their network.  I think i may even need a WEP password etc.  Will i have to run gnome to be able to do this?

---

### Post by fredj on 2007-08-05
No you don't need a GUI to configure wireless. You can do it just by editing the /etc/network
interfaces file. In fact everything in Linux can be configured without using a GUI such as 
Gnome but you have to know what you are doing. For example you need to know how to edit
files in a terminal window and which editor to use. A GUI simplifies things, even the editor is easier 
to use because you have a full screen WSIYG editor rather than a line editor. But with a little
practice you should be able to find your way around without GNOME or KDE. The learning
curve is steeper but without a GUI you will quickly learn more about the internal structure of
Linux.

---

### Post by jseiser on 2007-08-05
i use nano for all my editing, so i should be good with that.  The thing i wont know how to do is keep say eth0 set-up with dhcp so i can plug the laptop into my router at home, and also have a eth1 set up for my schools wireless network.  I imagine eth0 will set-up automaticly and i would then go to school and somehow make my internal wireless detect their network and then fill in the wep/wpa and the like?  Is there any guides to doing this textually?  The laptop has 512 ram but its a slow via processor, so the less i need to run graphicly the better :)  Im just hoping frame bugger works so i can use links2 with graphics, cplay with run fine, as will rtorrent, so i should be able to do anything i need and still keep the computer running nice and fast.

---

### Post by fredj on 2007-08-05
The first two entries in your /etc/network/interfaces file should be

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

This should take care of the localhost and the wired internet connection. Now all you need
is an entry for the wireless interface. Look in the Wireless and networking forum for more
infromation about this.

To get the name of your wireless interface (sometimes eth1 or wlan0) open a terminal and
type sudo lshw -class network. This will also give you the name of the driver that is being loaded.
Some of Ubuntus built in drivers will work with WEP but not with WPA. The only way to get round 
this is to use windows XP driver files with ndiswrapper and modprobe. However be warned the
version of ndiswrapper in the repositories is faulty. You may need to download the latest source
files and recompile it from scratch.

---

