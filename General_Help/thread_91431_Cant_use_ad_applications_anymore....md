---
title: "Cant use ad applications anymore..."
date: 2005-11-17
forum: General Help
---

### Post by tomwell on 2005-11-17
Hi,

I have just tried to followed this how to

[COLOR="Red"]http://www.ubuntuforums.org/showthread.php?t=33040&page=2&highlight=gnomad[/COLOR]

In particular in this how to i followed this code:

[COLOR="Red"]#!/bin/bash
#gnomad2 setup on ubuntu 5.04
#untested; copy-pasted from my main ubuntu setup script which has been
#(i.e. use this at own risk ;-)
#also, please note the last section of the script; a manual edit is required
################################################

#update apt sources
sudo mv /etc/apt/sources.list /etc/apt/sources.list_bak
wget "http://download.ubuntuforums.org/ubuntusetup/sources.list"
sudo cp sources.list /etc/apt/sources.list
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg --armor --export 1F41B907
sudo apt-key add -
sudo apt-get update

#get dev packages
sudo apt-get install build-essential
sudo apt-get install gcc g++
sudo apt-get install libgtk2.0-dev libgnomeui-dev libxml-perl
sudo apt-get install libusb-dev libid3tag0-dev

#build libnjb
wget "http://easynews.dl.sourceforge.net/sourceforge/libnjb/libnjb-2.1.1.tar.gz"
tar xvfz libnjb-2.1.1.tar.gz
cd libnjb-2.1.1
./configure
make
sudo make install
sudo cp nomadjukebox /etc/hotplug/usb/nomadjukebox
sudo chmod 755 /etc/hotplug/usb/nomadjukebox
sudo cp nomad.usermap /etc/hotplug/usb/nomad.usermap
sudo ldconfig
#cleanup
cd ..
rm -Rf libnjb-2.1.1
#restart usb hotplug service
sudo /etc/init.d/hotplug restart
#refresh shared libraries
sudo echo /usr/local/lib >> /etc/ld.so.conf
sudo ldconfig
#build gnomad2
wget "http://easynews.dl.sourceforge.net/sourceforge/gnomad2/gnomad2-2.6.3.tar.gz"
tar xvfz gnomad2-2.6.3.tar.gz
cd gnomad2-2.6.3
./configure
make
sudo make install
#cleanup
cd ..
rm -Rf gnomad2-2.6.3

#permissions...
sudo gedit /etc/hotplug/usb/nomadjukebox
#change DEVICEPERMS=0600 --> DEVICEPERMS=0666
#ensure gpilotd is paused (if you use this daemon; caused me some issues)
#plugin in device & cross fingers :-)
#eof
################################################[/COLOR]

 and now my add application program doesnt work... it just keeps searching... if i try using Synaptics package manager i get these error messages 

view screen shots...

Does anyone know what happened??

Am so pissed off i had just finished installing Ubuntu and everything was working fine...!!! After a week and a half...!!!

Bumed!!!

But on the other hand with this problem am sure i will leran something new...!

Thank you for all your help in advance...

Peace!!!!

---

### Post by matthewv on 2005-11-17
Try restoring your old /etc/apt/sources.list file 
```

sudu cp /etc/apt/sources.list /etc/apt/sources.list.old
sudo cp /etc/apt/sources.list_bak /etc/apt/sources.list
sudo apt-get update

```

---

### Post by tomwell on 2005-11-17
Thx man that has done the trick, 

what was wrong?? 

Do i need to reeinstall universe and multiverse???

And do you think i have messed up more things by doing this how to?? 

I am so worried because i spent so much time setting Ubuntu up...

Thank you for replying so quickly...!!

Peace Tom

---

### Post by matthewv on 2005-11-17
You might need to re-add them, depends whether you had them added before. Just go to synaptic, then settings --> repositories --> add. Go to ubuntu binary and select all the check boxes. Press OK, then OK again, the reload and you're all set.

---

### Post by tomwell on 2005-11-17
If i understand correctly what you told me to do was back up from a back up i made...??? correct? so if i had installed the repositories i dont need to do again right?

Do you know what i screwed up when i did that how to??

thx for your time...!

---

