---
title: "nvidia 6xx graphics drivers from synaptic..?"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by musky on 2009-04-21
Running 8.04 on a compaq [[COLOR="Blue"]*sr2020nx*[/COLOR]]("http://www.shopping.com/xPF-Hewlett-Packard-HP-SR2020NX-Compaq-Presario-Desktop-PC") with onboard nvidia 6xx graphics chip & wanted to update the drivers but dunno which one to pick from synaptic? tia

---

### Post by musky on 2009-04-30
bump

---

### Post by taurus on 2009-04-30
There should be a [Recommended] version if your card is on the list from System -> Administration -> Hardware Drivers.

---

### Post by musky on 2009-04-30
Checked it out & get an empty box that has in the header:
-No proprietary drivers are in use in this system

fwiw, the above link shows NVIDIA GeForce 6150 LE

---

### Post by musky on 2009-05-01
Well.. good news is a search of '6150' brings up alota hits so prob stumble on some info at some point.

Scrolling is the biggest prob right now, very sloow & choppy, barely works.

Gotta get up to speed on this stuff so I can set up the wife & kids. Probably I'll pick up a thing or 2 sortin my own vid first. 

I'll try a search of ~linux driver & 6150 next.

---

### Post by upchucky on 2009-05-01
once you determine the right driver for your card, the following is the proper way to set up nvidia on 8.04

Set up Nvidia driver

Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
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
     [http://ubuntuforums.org/showpost.php?p=5227704&postcount=1](http://ubuntuforums.org/showpost.php?p=5227704&postcount=1)

---

### Post by musky on 2009-05-02
Hmm.. just had a look at my wubi setup & the drivers are installed.

Went through the instructions [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=4790346&postcount=1") on that setup & maybe I'll try that way first here..but thx for the info. 

[IMG]http://i39.tinypic.com/2czaaer[/IMG]

---

### Post by musky on 2009-05-02
> **upchucky said:**
> 4) gksudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit

Not sure where to add "nvidia" here?
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
fuse
```
Guess like this?
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
fuse
nvidia
```

---

### Post by musky on 2009-05-03
I'm not having any luck in the end. Maybe not meant to work with portable ubuntu in win?

EDIT-Turns out can't do this with portable ubuntu.

thx for the solid info nevertheless..

[http://portableubuntu.demonccc.cloudius.com.ar/](http://portableubuntu.demonccc.cloudius.com.ar/) (can't tag it..)
> You can't use you nvidia drivers on Portable Ubuntu because it uses Xming as X server. Xming is a X server for Windows and use the same drivers that use Windows. 

---

