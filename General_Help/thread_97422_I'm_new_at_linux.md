---
title: "I'm new at linux"
date: 2005-12-01
forum: General Help
---

### Post by Linux Noob on 2005-12-01
i need help with elememtary things.
-cant play mp3s
-cant install new apps
-having probs with connecting to the internet
please help im very interested in switching over to linux.

---

### Post by RAOF on 2005-12-01
Well, the first two of your problems can be solved [here]("http://help.ubuntu.com/starterguide/C"), if you have an internet connection.

If you want our help setting up your internet, we'd need some details about how you normally connect to the 'net, what you've done, and what's not working.

---

### Post by cgjones on 2005-12-01
I would start by checking out the Ubuntu 5.10 Starter Guide at [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/) . This should answer a lot of your questions. Also, try searching the forum for any problems you might have. I've already answered many of my own questions by reading through the forums.

---

### Post by akiro.yamamoto on 2005-12-01
xmms is a nooob's friend (believe me :smile: )....
Check the links in my sig for more info....
Regards

---

### Post by Linux Noob on 2005-12-01
im on dial up. i read on this one website to configure my connections.
To configure dialup
sudo pppconfig

To connect dialup
sudo pon provider_name

To disconnect dialup
sudo poff

i edited the repositories by:
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

replaced with

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

and saved it


with all those things done i cant install gnome ppp or get anything else working.

---

### Post by akiro.yamamoto on 2005-12-01
Perhaps a step by step approach will help...
Let us deal with the modem first.....!!

Is your modem detected?....
Is it a external serial modem or is it a 'winmodem'?
If it's a winmodem do you have the drivers(linux) for it....?
If it's a harware modem can you connect to and browse the internet with a browser?
If not what errors if any are you getting....?
If you have the drivers (if needed) for your modem or if it is already detected... You can use the built in network configuration dialog utility to set up your dialup account....
Click on System >> Administration >> Networking
When the dialog comes up..Highlight Modem connection then click on properties... It's here that you can enter the info for your account... 
Click on the checkbox for Enable this connection and from there it's basically self explanatory...
Post here when you've got all this set up 
Hopefully that will be from firefox running on Ubuntu 5.10 :smile:
If not "sigh" post here with any errors you recieved....

Hope this helps...
Regards

---

### Post by Linux Noob on 2005-12-01
[QUOTE=akiro.yamamoto]Perhaps a step by step approach will help...
Let us deal with the modem first.....!!

Is your modem detected?....
Is it a external serial modem or is it a 'winmodem'?
If it's a winmodem do you have the drivers(linux) for it....?
If it's a harware modem can you connect to and browse the internet with a browser?
If not what errors if any are you getting....?
If you have the drivers (if needed) for your modem or if it is already detected... You can use the built in network configuration dialog utility to set up your dialup account....
Click on System >> Administration >> Networking
When the dialog comes up..Highlight Modem connection then click on properties... It's here that you can enter the info for your account... 
Click on the checkbox for Enable this connection and from there it's basically self explanatory...
Post here when you've got all this set up 
Hopefully that will be from firefox running on Ubuntu 5.10 :smile:
If not "sigh" post here with any errors you recieved....

Hope this helps...
Regards[/QUOTE]

-my modem is not detected i think. it says its a 56k modem in the device manager. also about 80% of my devices are unknown.
-its a win modem.
-no i dont have the driver for linux
-i dont know if my modem is harware

---

### Post by akiro.yamamoto on 2005-12-01
Then My friend were in for an interresting time... :smile:
GO Here.....:
[http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/)
Read through the site... but first things first....
Download this : [http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)
Extract the file and run it on your linux system....
With the above site and the results from the scanmodem utility you will have some idea or a starting point... to get your problems solved...
:smile: 
Post back here with any problems...
Regards

---

