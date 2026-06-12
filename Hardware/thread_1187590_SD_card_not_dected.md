---
title: "SD card not dected"
date: 2009-06-14
forum: Hardware
---

### Post by lhorace on 2009-06-14
Ok, don't know where to start but I could start off by how mad I am. 

I have been trying to install linux for the past 5 days with absolute no success, I mean I got them to load to desktop just I few things refuse to work.

I tried:
Fedora 11, no ati drivers as of yet.
Fedora 10, ati support yes but will not logout, suspend, or having trouble shutdown successfullllly. 
Kubuntu 9.10, erratic crashes, will not suspend.
Kubuntu 9.04, yes, success, everything works, ati, suspend, logout, all work oh but wait, I have my /home directory mounted off my two partion SD card. Fat32 and Ext4<-- where my home directory is mounted off. Well as of right now, after two reboots, my SD card is no longer dectect by Linux. Nor Fedora 10 KDE Live or Kubuntu Live detect them either. Oh, Windows Vista, Happily dectects the SD card. I tried deleting all the partitions in the hopes of trying again under Windows Vista using diskpart, well diskpart cannot delete partions off of removiable media....
 5 days, I'm sorry, but very angry, and blame all this for  man upstairs, no success.

Right now I reinstall kubuntu 9.04 on my hard drive and right now is what I'm using to write this message..... I have no idea because nothing is posted in dmesg or messages even after I remove and reinserted the card? I don't know if the filesystem not getting read properly or what? if anyone suggest some tools to find what's going on, I would appreciated..:(

---

### Post by lhorace on 2009-06-14
I download gpart, gpart detected the SD card and re-partition it but kubuntu still hasn't dectected it??? Now I'm really lost..

---

### Post by lhorace on 2009-06-15
My sd card is now working after I updated HAL

---

