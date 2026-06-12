---
title: "I'm new to Ubutu, cant install new programmes."
date: 2008-11-30
forum: General Help
---

### Post by shout2008 on 2008-11-30
Help! I'm a newbie and being a Windows user most of my life I am now trying out Ubuntu, which I think is really great. If I can get the hang of how to install 3rd party programmes then I will change over completeley I recently tried to install Google Earth for Linux and had no success, I followed the instructions by opening a terminal and typing the command line, just got errors. So if there's anyone who can advise me how to go about it that would be great.
Thanks

---

### Post by Idefix82 on 2008-11-30
People won't be able to help you unless you are more specific. What errors did you get, which guide were you following,...

Welcome, by the way!

---

### Post by mesastok on 2008-11-30
You can install/unistall packages (programs ) using the Synaptic Package manager.
You can find this in the System->ADministration->Synaptic Package Manager.
Write in the wuich search google and you will find google earth.Its very easy to install.
If you have problems installing this way please post the errors in the forum.

---

### Post by gjoellee on 2008-11-30
Ok, you have the "Add/Remove", and you have "Synaptic" or you can learn using the terminal.

Ok first of all you don't want to be "root" (root is the admin user). When you are not root, you put in the word "sudo" in front of the command you would do as root.

Then the package management tool in Ubuntu is APT. and the command for using it is "apt-get"

Then you want to install something so you add the word "install", if you want to remove something you can use "remove instead".

Then at last add the name of the package/program you want to install. Ex: opera.

IN most comman cases you will ask you for something an then somewhere in the line it says "Y/N" the Y=Yes, N=No, remember to read what you are saying yes or no to if you don't know what you are doing.

the full command for installing opera is:
```
sudo apt-get install opera
```

the full command for removing opera is:
```
sudo apt-get remove opera
```

two commands to become root is:
```
sudo su
```
you have the "sudo" because you are not root, and the "su" is for "superuser". now it will ask you to write your password, type it in (there will not be any graphical feedback) and press enter.

second command to become root:
```
su
```
NOTE: This command requires a root password


now if you are root, you don't need to have the "sudo" in front, so installing opera as root will use this command:
```
apt-get install opera
```

and romeving oprea:
```
apt-get remove opera
```

you will learn more commands as the time goes...

---

### Post by gjoellee on 2008-11-30
ok, this is an easy way to install google earth:
download this package: [http://download.softpedia.ro/dl/a6aad3d7a5b16a5be788d656dc1a7bcf/49328918/500024551/linux/ultamatix-1.8.0-3_all.deb](http://download.softpedia.ro/dl/a6aad3d7a5b16a5be788d656dc1a7bcf/49328918/500024551/linux/ultamatix-1.8.0-3_all.deb)

when downloaded just double click on it and click on install

after the install look for "Ultamatix" in the menu. click on it, and then search for google earth on Ultamatix.

---

### Post by spike_naples on 2009-03-31
Yup, Google for Ultamatix... It seems very helpful for newbies like us to Ubuntu.

---

### Post by LowSky on 2009-03-31
NO NO dont use Ultamatix!!!

and Spike_naples dont bring old post back from the dead

Ultamatix while it might seem helpful is dangerous

use add/remove or synaptic o install software, if you cant find it there, use Getdeb or medibuntu for help.

---

### Post by spike_naples on 2009-03-31
> **LowSky said:**
> NO NO dont use Ultamatix!!!

and Spike_naples dont bring old post back from the dead

Ultamatix while it might seem helpful is dangerous

use add/remove or synaptic o install software, if you cant find it there, use Getdeb or medibuntu for help.


Sorry I did...didn't mean to.

---

### Post by hyper_ch on 2009-03-31
if you have no clue about linux first have a read at [http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu)

---

