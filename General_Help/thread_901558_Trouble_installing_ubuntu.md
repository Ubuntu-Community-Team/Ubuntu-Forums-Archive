---
title: "Trouble installing ubuntu"
date: 2008-08-26
forum: General Help
---

### Post by Bricklinfan on 2008-08-26
Got a bit of a problem..

I tried installing the latest version of Ubuntu on my Vaio laptop this evening. I took the download option and burnt the file to a disc, and followed the procedure. Once it was installed I was told to eject the disc and reboot the computer, which I did. Then when it started the text based thing told me to enter my login and password which I did, but after I do that I just get a command prompt line. I've tried reinstalling it but to no avail. The same thing keeps happening over, and over, and over..... :'(
Right now I'd just be happy to uninstall whatever part of ubuntu is working and go back to windows...

Regards,
Bricklinfan

---

### Post by phidia on 2008-08-26
It sounds like the xserver isn't working-your video card isn't enabled.
Just try this at the commandline you have described.
> sudo dpkg-reconfigure -phigh xserver-xorg 

---

### Post by kellemes on 2008-08-26
> **Bricklinfan said:**
> 
Right now I'd just be happy to uninstall whatever part of ubuntu is working and go back to windows...

Regards,
Bricklinfan

No need to uninstall anything..
Just boot with the Windows install disk and let it do it thing.

---

### Post by Bricklinfan on 2008-08-26
> **phidia said:**
> It sounds like the xserver isn't working-your video card isn't enabled.
Just try this at the commandline you have described.

Thanks. I tried it and got this: "xserver-xorg is not installed" :confused:


> **kellemes said:**
> No need to uninstall anything..
Just boot with the Windows install disk and let it do it thing.

Don't have the disc...:(

---

### Post by kellemes on 2008-08-26
> **Bricklinfan said:**
> Thanks. I tried it and got this: "xserver-xorg is not installed" :confused:

Are you using the desktop edition of Ubuntu? Because it sounds like you're using the server edition.

---

### Post by Bricklinfan on 2008-08-26
> **kellemes said:**
> Are you using the desktop edition of Ubuntu? 

Yes.

---

### Post by kellemes on 2008-08-26
Try..
```
sudo apt-get install ubuntu-desktop
```
It will install a hole lot of stuff, this includes xorg.

If X still isn't working you can try the command already given..
```
sudo dpkg-reconfigure -phigh xserver-xorg 
```

---

### Post by Bricklinfan on 2008-08-26
> **kellemes said:**
> Try..
```
sudo apt-get install ubuntu-desktop
```
It will install a hole lot of stuff, this includes xorg.



Thanks. I got this message "E: Couldn't find package ubuntu-desktop"
:(

---

### Post by gjoellee on 2008-08-26
> **Bricklinfan said:**
> Thanks. I got this message "E: Couldn't find package ubuntu-desktop"
:(

1.try one of those:
```
sudo apt-get install kubuntu-dekstop
``````
sudo apt-get install xubuntu-dekstop
```2.reboot your computer, and when GRUB have this "3 Sec thing" press esc, and boot the recovery kernel. read more:
[http://www.kshoster.net/?c=tipsandtricks&h=xfix](http://www.kshoster.net/?c=tipsandtricks&h=xfix)
there might just be something that have changed the xorg config file

---

### Post by kellemes on 2008-08-26
> **Bricklinfan said:**
> Thanks. I got this message "E: Couldn't find package ubuntu-desktop"
:(

Man, what's going on..
Please post the output of /etc/apt/sources.list

You can issue the following command to write the output to a file.
cat /etc/apt/sources.list > outputfile

So you installed using the livesystem? And you didn't get any errormessages or something?

---

### Post by Bricklinfan on 2008-08-26
> **kellemes said:**
> Man, what's going on..
Please post the output of /etc/apt/sources.list


It tells me "Permission Denied".

> You can issue the following command to write the output to a file.
cat /etc/apt/sources.list > outputfile

I can't because I can't access any file, folder etc

> So you installed using the livesystem? And you didn't get any errormessages or something?

I burnt the download to a CD. No error messages.


> **gjoellee said:**
> 1.try one of those:
[code]
2.reboot your computer, and when GRUB have this "3 Sec thing" press esc, and boot the recovery kernel. read more:
[http://www.kshoster.net/?c=tipsandtricks&h=xfix](http://www.kshoster.net/?c=tipsandtricks&h=xfix)
there might just be something that have changed the xorg config file
Thanks. I tried it. Still nothing though.

---

### Post by raphaelr on 2008-08-26
Use sudo (sudo cat /etc/apt/sources.list > outputfile). Then enter your password.

---

### Post by Bricklinfan on 2008-08-26
Okay, I just rebooted with the CD and did the check CD for errors thing. I got this:
[http://img176.imageshack.us/my.php?image=pictureku3.jpg](http://img176.imageshack.us/my.php?image=pictureku3.jpg)

---

### Post by Bricklinfan on 2008-08-26
How would I go about uninstalling ubuntu in the stage it is at now?

---

