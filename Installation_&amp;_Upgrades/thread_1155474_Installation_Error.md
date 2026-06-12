---
title: "Installation Error"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by LeonWolf on 2009-05-10
Hi all.

I have one problem. Few months ago I downloaded Ubuntu 8.10, but when I try to install it, after bootscreen I only got background image and "X" in center of it. I got Ubuntu 7.04 from friend and it's working, but 8.10 simply wont install. I even tried to upgrade from 7.04 but I always got some error. I even tought that CD have some error so I downloaded it again and It's still same. I hope that someone know what can I do to install it without that error.

P.S. Sorry for my english, I am from Bosnia and Herzegovina.

---

### Post by upchucky on 2009-05-10
the x is the x server that starts the display,

8.10 has issues with some displays, and the last known well working issue with most displays is 8.04.

if you have a nvidia card then this is how to set up the card with version 8.04

you only need to do this if you want the 3d acceleration of the card working for games or cad or special desktop effects.

```
Set up Nvidia driver

Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from http://www.nvidia.com/Download/index.aspx?lang=en-us
	1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
	5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
	5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
	7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
	7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
		-------------------------------------------------------------------------------------------------------
		If you used Envy to attempt a previous nvidia install please run this command now before you go on:

               sudo envy --uninstall-all 
		sudo dpkg -P envy 

		-------------------------------------------------------------------------------------------------------
		If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:

		sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*

		-------------------------------------------------------------------------------------------------------
		If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

		sudo nvidia-installer --uninstall

		-------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
	8.a) Okay were in Command Line only now, we have a little left to do in here.
	8.b)login:
	8.c)Password:

9) sudo /etc/init.d/gdm stop
	9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
	10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
	11.a) Answer to the affirmative for all questions.
	11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
	11.c) If you somehow answered incorrectly on the last question in the installer then:
		c.I) sudo nvidia-xconfig #this will write a new or attempt repair of
                     an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
	12.a) You should see an Nvidia Logo, and then be put at your login screen, 
              you should also be able to enable desktop effects.

Optional But recommended:
13) To get the driver to update itself when a new kernel is installed from the update
    manager be sure to follow the guide in this link:
     http://ubuntuforums.org/showpost.php?p=5227704&postcount=1
```

---

### Post by LeonWolf on 2009-05-10
Thanks for quick reply.

I have ATI Sapphire HD 2400 Pro graphic card. I still haven't tried to install Ubutnu 9.04, but i will try tomorow when I wake up :D

---

