---
title: "Nvidia beta drivers = black screen"
date: 2006-11-01
forum: Hardware &amp; Laptops
---

### Post by robersant on 2006-11-01
Hi! I have a problem when i try to install the nvidia drivers from the guide in [http://www.ubuntuforums.org/showthread.php?t=263851&highlight=nvidia:](http://www.ubuntuforums.org/showthread.php?t=263851&highlight=nvidia:) i install drivers, reboot, and after the "ubuntu" logo (while ubuntu loads) my screen goes to black and nothing else happens (even when i try to press keys or move the mouse). So, I have to reboot again by the power button on my pc, and start the recovery system where I change the device in the xorg.conf to "nv" and then i can start gdm.

But... Why the drivers dont work?? I have done all the guides I found on the internet and always I get the black screen. I have done it 20 times (installing ubuntu from scratch). I read all the posts in this forum, I have done all the tips that i found here, but the black screen does not disappear.

I have the Nvidia 6600 PCI-E that with the "nv" drivers works nice, but i want the nvidia drivers, and i cant get work. My monitor is a CRT that is plugged via an adapter (VGA > DVI) to one of the 2 DVI ports that comes with the videocard.

Im posting my xorg.conf and his log because I didnt find any error, but it just doesnt work!!

Please help mee!

---

### Post by BillGod on 2006-11-02
I am not positive but I think I read somewhere this exact same problem and they fixed it by #ing out the triple buffer option like so.# Option    "TripleBuffer" "true"  Cant hurt to try it.

Bill

---

### Post by wwwonder on 2006-11-02
you need to comment the "eeprom" entry in /etc/modules

---

### Post by tuke81 on 2006-11-02
Or you can patch your nvidia installer:
[http://www.nvnews.net/vbulletin/showpost.php?p=996233&postcount=20]("http://www.nvnews.net/vbulletin/showpost.php?p=996233&postcount=20")

---

### Post by robersant on 2006-11-03
in /etc/modules there is not an "eeprom" entry... :( so... what else can i try?

---

### Post by jougs on 2006-11-12
> **robersant said:**
> in /etc/modules there is not an "eeprom" entry... :( so... what else can i try?

You can check which modules are loaded with
```
lsmod
```
For me, removing eeprom from /etc/modules indeed solved the issue. The module was added by sensors-detect from the lmsensors package

---

### Post by robersant on 2006-11-12
The module is no loaded (is not listing with that command). So... Just doesnt work? :???:

---

### Post by ruipedroca on 2008-02-02
Though this tutorial was intended for another use and it's passed more than a year, maybeit will help other users:
give it a look, especially the Envy part.

Hope it helps,
Regards

How to install Edubuntu in a computer with NVIDIA or ATI (you need internet access)
or
How to solve the black screen when installing Edubuntu 
(forgive my bad english)

This problem (unusual in Linux) is that Nvidia didn't provide the community with the test drivers. They've tried latter to correct this error, but a bit to late.. so, it's not linux, it's nvidia (or so i've read in the internet!


-install edubuntu using the cd-rom as normally
-when the installation finishes, it needs to reboot 
(in my case, during the installation the dhcp wasn't installed, i was using a static address)
-when it reboots, it shows the horizontal bar, but when it completely grows the screen turns black, this happens because the nvidia driver is missing
-when the screen turns black, press CTR + ALT + F1
-log in the terminal using the username and password set during the installation
-type: 
# cd /etc/network
# sudo chmod +w interfaces [this is needed because the interfaces file is originally read only, so we've got to make it writable]
# sudo vi interfaces [this will open the interfaces file, which needs to be configured properly]
-enter the password set during the installation
-press "i" to enter the vi insert mode
-be sure to change the interface file so it looks like this:

[BEGGINING]
# This file describes the network interfaces available on your system

# and how to activate them. For more information, see interfaces(5).



# The loopback network interface

auto lo

iface lo inet loopback



iface eth0 inet static

address 192.168.10.100 [this must be set to the static address you want to use]

netmask 255.255.255.0 [this must be your netmask, usually equal to this one]

gateway 192.168.10.1 [this must be the ip address of your gateway]



auto eth0
[END]

-press ESC to exit the vi insert mode
-press "ZZ" (capitol zz two times, in order to save the changes)

-now type:
# /etc
# sudo vi resolv.conf
-press "i" to enter the vi insert mode
-just write:
domain edubuntu [this must be the domain you used during the installation: it shows in the terminal, in my case, edubuntu@user
nameserver 195.22.0.136 [this must be the dns you use]
-press ESC to exit the vi insert mode
-press "ZZ" (capitol zz two times, in order to save the changes)

-now you can test your internet access by making ping to the ip adress of another machine 

# cd /opt
# sudo dpkg -i envy_0.9.10-0ubuntu2_all.deb [since i've made several atempts, i'm not sure if this step is the one or the other below (just try), it may ask for the installation cd of Edubuntu for some packages]
# sudo apt-get install -f
# sudo dpkg -i envy_0.9.10-0ubuntu2_all.deb [since i've made several atempts, i'm not sure if this step is the one or the other above]
# sudo envy -t [this will start Envy in the text mode]
-now just type your choice ["1" in my case, and press Enter)
-now it will automatically download and install the drivers you need 
-"y" + Enter (happens twice)
-when it reboots, you will be able to see the Edubuntu normal log in: no more black screen! 
Everything should be ok!

Have fun!



credits:
[http://ubuntuforums.org/archive/index.php/t-132808.html](http://ubuntuforums.org/archive/index.php/t-132808.html)
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

