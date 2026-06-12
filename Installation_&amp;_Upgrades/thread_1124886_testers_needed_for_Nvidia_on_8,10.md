---
title: "testers needed for Nvidia on 8,10"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by upchucky on 2009-04-13
This worked very well for 8.04, what is needed is a bunch of people to try it on their 8.10 nvidia, and post the results here.

I have opted to not install 8.10 because it is not a long term supported release, or i would test this myself, however what is needed is several machines to test.

this was a tried and true method of setting up nvidia when all methods failed including Envy. there are other methods including Envy but they were workarounds, and usually they did not set up the multiple resolutions ability of nvidia.


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

### Post by upchucky on 2009-04-14
bump

---

### Post by peyre on 2009-04-15
Excellent instructions, Upchucky--those were clear, well-thought-out, and needed minimal figuring out as you went along.  Those would be considered quality instructions on an intranet help desk knowledge base, where the techs need to be able to know at a glance what to tell the caller, and in what order (I used to manage such a knowledge base).

I tried this on my computer, which is an old PIV 1.8GHz with an NVidia Riva TNT2 AGP card running Xubuntu 8.10.  I'd tried installing the driver from NVidia before, and had tried EnvyNG, without much success with either.  The only real change I made was to run [font="Courier New"]sudo envy**_ng_** --uninstall-all[/font].

Your instructions worked well and it seemed to install without a hitch.  Now, when I ran [font="Courier New"]sudo /etc/init.d/gdm start[/font], I didn't see the NVidia logo as expected, but X started up as normal.  I didn't see any differences from before, though Gnome Device Manager did show the make and model of my card (it might have done that before though; I forget).  I'll have to reboot it tonight to see if the video driver line fails as it has in the past.

**Edit:** I rebooted last night.  Curious.  I used to get a whole bunch of text that scrolled down during bootup, and one of the lines, right somewhere in the middle, was it trying (and failing) to install the proprietary NVidia driver.  I don't see the text any more; it's pretty much all GUI after the initial startup screens that offer to let you into the BIOS etc.  But bootup also seems faster; it doesn't seem to pause like it did while trying to install that driver, so I'm thinking your procedure must have installed it successfully.  Sadly I don't see any differences in video quality and the Windows games that failed to run in Wine still don't run--but it was worth a try, anyway, and it's always nice to have the right driver installed for your hardware.

---

### Post by upchucky on 2009-04-17
after a successful install, you can type this into a terminal to make sure 3d is working with fast frame rates. you should see somewhere around 11,000 FPS and higher.


```
glxgears
```




Oh and I can't claim credit for the how to, i did get it from this forum somewhere a long time ago, and can't remember who did the original post.

---

### Post by peyre on 2009-04-17
It says:

Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

:(

---

