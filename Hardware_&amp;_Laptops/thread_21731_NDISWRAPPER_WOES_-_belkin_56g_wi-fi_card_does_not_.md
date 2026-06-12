---
title: "NDISWRAPPER WOES - belkin 56g wi-fi card does not work"
date: 2005-03-23
forum: Hardware &amp; Laptops
---

### Post by robtotheb on 2005-03-23
I have been trying to convert my brother-in-law to Ubuntu (he is not too impressed so far!  :evil: ).  I installed it on his VAIO laptop and his belkin 56g wi-fi card does not work.  I followed the tutorials on setting it up (wiki and the GID forums).  The weird thing is when I typed "ndiswrapper -l" after installing and it said "driver present, hardware present" BUT nothing show up in Networking except the Ethernet connection and I cant see any "add" options.  
Any ideas?

ps the belkin DOES shows up in Device manager.

---

### Post by kperkins on 2005-03-23
Did you do ndiswrapper -m after installing?

---

### Post by robtotheb on 2005-03-24
yes didnt help - no lights show up on the device either

---

### Post by jdodson on 2005-03-24
[QUOTE=robtotheb]I have been trying to convert my brother-in-law to Ubuntu (he is not too impressed so far!  :evil: ).  I installed it on his VAIO laptop and his belkin 56g wi-fi card does not work.  I followed the tutorials on setting it up (wiki and the GID forums).  The weird thing is when I typed "ndiswrapper -l" after installing and it said "driver present, hardware present" BUT nothing show up in Networking except the Ethernet connection and I cant see any "add" options.  
Any ideas?

ps the belkin DOES shows up in Device manager.[/QUOTE]

did you run "modprobe ndiswrapper"?

if that doesnt work then see if there is an updated driver on the net.  if not grap and compile the latest version of ndiswrapper from source, perhaps the bug has been fixed in the latest version.

---

### Post by bpoppa on 2005-03-25
Hello,

I am having the same issues as robtotheb.  I have a different wlan card than him, but same deal.  This card has worked with ndiswrapper on two other distros (Fedora & Suse 9.2) so I know I am using the correct driver.  When I did the modprobe ndiswrapper I get a successful message in dmesg, so all is good there.  My issue is now how to add it in Ubuntu.  The one FAQ says to goto COMPUTER | SYSTEM CONFIGURATION | NETWORKING......  I got nothing like that.  Closet I have is Networking under System | Administration, but no place to add a device.

Thoughts?

Jim

---

### Post by jonny on 2005-03-26
[QUOTE=bpoppa]Closet I have is Networking under System | Administration, but no place to add a device.[/QUOTE]That's the option you're looking for; the menu names were changed in Hoary, and your FAQ is obviously based on Warty.  You don't add devices with this screen but, if everything is working properly, it should list all network devices.

What are your results from ifconfig and iwconfig (type the commands in a terminal window)?

---

### Post by arnieks on 2005-03-27
[QUOTE=robtotheb]I have been trying to convert my brother-in-law to Ubuntu (he is not too impressed so far!  :evil: ).  I installed it on his VAIO laptop and his belkin 56g wi-fi card does not work.  I followed the tutorials on setting it up (wiki and the GID forums).  The weird thing is when I typed "ndiswrapper -l" after installing and it said "driver present, hardware present" BUT nothing show up in Networking except the Ethernet connection and I cant see any "add" options.  
Any ideas?

ps the belkin DOES shows up in Device manager.[/QUOTE]

Don't know if it will help, but I had problems with my broadcom bcmwl.  This is what I had to do. In /etc/ndiswrapper/bcmwl5/ change all the .config files RadioState|1 to RadioState|0
you will have a different path of course, but it fixed it for me
arnie

---

### Post by zevin on 2005-03-27
[QUOTE=arnieks]Don't know if it will help, but I had problems with my broadcom bcmwl.  This is what I had to do. In /etc/ndiswrapper/bcmwl5/ change all the .config files RadioState|1 to RadioState|0
you will have a different path of course, but it fixed it for me
arnie[/QUOTE]
Hey
Very noob to linux in general. I have an intigrated broadcom in my new hp zv5000 laptop. Ubuntu reconizes it, but i'm not getting any connection. I dunno, all the guides i find on the net through google tell me there arn't any 802.11g cards supported by linux, and i think they must be outdated. If anyone can point me to a guide to start getting this card working, would be super:)
thanks.

---

### Post by dcraven on 2005-03-27
[QUOTE=zevin]I have an intigrated broadcom in my new hp zv5000 laptop. Ubuntu reconizes it, but i'm not getting any connection. [/QUOTE]
The Broadcom chipset does work using ndiswrapper. Have a look at [this](http://www.ubuntuforums.org/showthread.php?p=106828#post106828) thread for the method I used to get it to work. Hopefully you'll have similar results.

Let's leave this thread for the OP with the Belkin. No need to hijack it.

HTH
~djc

---

### Post by tmowerman on 2005-03-30
I had to add the following lines to /etc/network/interfaces

iface wlan0 inet dhcp
name Wireless Lan Card
wireless_essid <your essid>

now i can use the wireless card by typing the following

sudo ifdown eth0
sudo ifup wlan0

Not sure if this will help, but if the driver is working it will

Tim

---

