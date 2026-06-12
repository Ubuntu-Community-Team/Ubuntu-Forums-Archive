---
title: "Rainbow screen of death?"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by PhysicsGeek on 2009-03-13
I'm installing 8.10 from disc, however, the installation stops about one minute into the process and the entire screen is covered with an array of hundreds of multicolored rectangles, about a dozen of which are flashing.

I have no idea what is going on.

The machine itself is a recent build by a first-timer-- should I double check my video/screen drivers?:confused:

---

### Post by Neo_The_User on 2009-03-13
Could you post a video or picture of it happening?

---

### Post by upchucky on 2009-03-13
need some clairification. 

1, did the live cd boot ok and you had an ok display before actually doing an install? if yes, then it will install ok.

2, did the screen go all scrambled when booting only the live cd? if yes then its gonna need some screen parameters set after an install before it will show a good display.

3, if the display went all scrambled in the first few minutes of the install, or after an install completed see step 2.

4, if the display is an nvidia card, 8.10 has issues with nvidia better to use 8.04

5, if nvidia, the this is the proper way to set up nvidia card with 8.04
There are ways to do it using envy but envy is a workaround, not a true nvidia setup.

Set up Nvidia driver after you have a working install of 8.04 or earlier release of Ubuntu.

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

