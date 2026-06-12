---
title: "Broadcom Wireless is makeing me crazy!"
date: 2007-06-13
forum: Hardware &amp; Laptops
---

### Post by Antonio44 on 2007-06-13
Ok so I started linux three days ago I saw it online thought it looked cool. Plus I was tired of Windows crap. So i installed it, partitioned my drives, tried once failed, tried again successfully, then I turned it on and tried to use the internet. Wireless doesn't work so after crying in the corner for awhile I looked around. It detects the card but still no internet. Now I am not a great computer person, I have used Windows for all of my 18 years on this planet. Please help me graphically because command line minds well be written in cantonese. Any info that you need me to give you to help you I will. I am at a loss for what to do. I have a gateway laptop (MX6437) and the card came in it. It is broadcom and this is the info I am getting from the information window in windows:

Hardware Details:

Board: BCM94318MPG   Rev 4.2

Chipset: BCM4318

MAC Address: (I think I Am supposed to keep that private)


Software Details:

3.100.64.0 built by: WinDDK

Driver date, provider, etc


all of this is gibberish to me. But I really do like this operating system but if I can't use my wireless internet I will have to stay with windows. Please help me step by step ( type 1, press enter key) 

Bless anyone who offers me help,


A.

---

### Post by MaximusTG on 2007-06-13
Well, there are plenty of howto's around here on the forum. But those all use the command line. If you want to do it without the command line, you could use synaptic to install ndiswrapper and the ndisgtk package. Ndisgtk is a gui for the installation of the windows drivers for your wireless card. Al that you have to do then is edit /etc/modules and add a line saying 'ndiswrapper' without the quotes. (and install the drivers via ndisgtk) You have to be root to do that though.  Paste this line in a terminal:

sudo gedit /etc/modules

and add the ndiswrapper line. (reboot)

Done!

---

### Post by floke on 2007-06-13
How about this

[http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom)

---

### Post by fooman on 2007-06-13
you might want to give this guide a try,  it sounds pretty easy to follow:

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

