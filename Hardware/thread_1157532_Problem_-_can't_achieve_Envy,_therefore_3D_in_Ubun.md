---
title: "Problem - can't achieve Envy, therefore 3D in Ubuntu 9.04"
date: 2009-05-12
forum: Hardware
---

### Post by Shnureaga on 2009-05-12
Hi again, now I am trying to get 3D, because even the Chess don't give me 3D access to the game and also i have some slowing in ordinary uses of youtube and other video programs. 

I use laptop Packard-Bell Easynote MZ35 with Radeon Xpress 200M

I tried to install Envy from the official site, the installation goes smoothly. I must see EnvyNG in my menus, but I don't. After that I can't start Envy: 

lukavia@ubuntu:~$ sudo envyng -t
/usr/bin/envyng: line 6: cd: /usr/share/envy: No such file or directory
python: can't open file 'interface.py': [Errno 2] No such file or directory

I searched Synaptic for **python**, but the possibilities are thousands, I even searched **google** for dependencies with Envy - no success. 

Part of lspci - that's my video chip

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]

Any help will be appreciated.

---

### Post by Falcon1002 on 2009-05-12
I know on my computer the default driver that comes with Ubuntu does not do 3D very well so I have to download and install the proprietary driver.
Have you tried ATI's driver for your card? [http://support.amd.com/us/gpudownload/Pages/index.aspx]("http://support.amd.com/us/gpudownload/Pages/index.aspx") 
I thought I should mention that not all of ATI's drivers work with 9.04 (i.e. mine). Hope this helps! :)

---

### Post by Shnureaga on 2009-05-13
Yes, i think i tried these drivers last time and after reboot i got blank screen...
Till the moment the issue is to find out what are the dependencies for python and Envy to work together, but i can't find them in google...

---

### Post by Falcon1002 on 2009-05-13
I got the blank screen when I used the driver on 9.04 also.> python: can't open file 'interface.py': [Errno 2] No such file or directory
It appears to me that python can not find the file interface.py. Have you tried installing envyng-qt from synaptic? It appears to me that that would install a gui interface.

---

### Post by Shnureaga on 2009-05-13
Yes, i installed envyng-qt from synaptic. It's not that
In every case, the drivers from ati.com official site don't work specifically for my video card radeon xpress 200m. I looked over and over on the internet, followed [this guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide) and i had no success. I got blank screen. 

If anybody follows this - there is a solution from the blank screen situation. 

**Start recovery mode after reboot**. Choose **xfix** and after that **drop to shell prompt**
Remove everything connected to **envy** and **fglrx**. 
Use
sudo apt-get remove 
and TAB options

Example: 
sudo apt-get remove envy(use TAB to find out all of the packages connected to Envy)
sudo apt-get remove fglrx(use TAB to find out all of the packages connected to Envy)
Reboot and voalla, gdm starts like nothing happened :)

---

### Post by Falcon1002 on 2009-05-15
Did the driver work on Ubuntu 8.10? Also have you tried just running the driver installer, not makeing the debs and what not?  I don't know a whole lot about drivers I just know what has worked for me and what has not. Sorry if I am not any help.

---

### Post by Shnureaga on 2009-05-19
I haven't started any 3D applications (for example Chess game in Ubuntu) in 8.10, so i am not sure if the driver worked well. 
Falcon1002: What is your video card? Type **lspci** in terminal if you are not sure ;) And how did you succeed installing the drivers for Ati video cards ?

---

### Post by Falcon1002 on 2009-05-26
My video card is a mother board integrated Radeon 1270. On 9.04 I never could get the driver to install on my computer (I did only try once:oops:), but on 8.10 it installed nice and easy.
First I downloaded the driver. After that I made the driver file an executable. Then I ran the file from a terminal (you could just execute it, but I like the terminal it shows me the errors:)). Finally I rebooted the computer. 
Thanks by the way for the lspci command I did not know that!:D I learn something new every day!

---

