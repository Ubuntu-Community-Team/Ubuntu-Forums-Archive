---
title: "Help with display card and monitor setup."
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by Prof.Arronax on 2009-03-26
I am migrating this machine from Windows XP to Ubuntu 8.10. It escapes me how such a sophisticated OS as Ubuntu is unable to configure itself to work properly with my display card and monitor... My machine is fairly straightforward. An AOpen AX4SG-UN board, 2.4G Pentium 4, 2G RAM, NVidia GeForce FX5200 display card and Acer P201WD monitor (connected via KVM switch.) Windows adapts to this quickly and allows adjustment of the display to any mode the monitor can handle. I cannot do that *at present* under Ubuntu.
Thus far I've installed the recommended restricted driver (NVidia version 96). After installation the maximum display resolution of 800x600 that the system allowed was reduced to a maximum of 640x480.

Question here is, how do I tell the OS what the monitor is and what its capabilities are. I don't see anything of use on the Acer web site that would serve like an ".INF" file such as Windows utilises. What shall I install or configure to accomplish this?

Incidentally, the NVidia driver does work and provides the so-called desktop effects and good colour depth with no problems; I just cannot do very much at all with 640X480.

---

### Post by Mark Phelps on 2009-03-26
> **Prof.Arronax said:**
>  It escapes me how such a sophisticated OS as Ubuntu is unable to configure itself to work properly with my display card and monitor
Actually, in many cases, it DOES do that. With ATI or Nvidia cards, you nearly always get the opportunity to install proprietary drivers, which you can often do simply by selecting System --> Administration --> Hardware Drivers.  In other cases, you can download and install the drivers from the AMD or Nvidia sites.

>  Windows adapts to this quickly and allows adjustment of the display to any mode the monitor can handle. I cannot do that *at present* under Ubuntu. 
That's because everyone provides MS Windows drivers; they don't do the same for Linux.  The way to check your monitor is to go into System --> Preferences --> Screen Resolution and see what it says.  On my system, it has the brand name of the monitor (Syncmaster) and a list of possible resolutions.  If yours has "generic", you can experiment with different settings to see if you can get a higher resolution.

> 
Thus far I've installed the recommended restricted driver (NVidia version 96). After installation the maximum display resolution of 800x600 that the system allowed was reduced to a maximum of 640x480.

Try the stuff I mentioned above to see if you can change the resolutions.

Also, open a terminal window and type "xrandr".  It will provide you a list of resolutions.

> 
Question here is, how do I tell the OS what the monitor is and what its capabilities are. I don't see anything of use on the Acer web site that would serve like an ".INF" file such as Windows utilises. What shall I install or configure to accomplish this?

See above regarding Screen Resolution.

---

### Post by Prof.Arronax on 2009-03-27
> **Mark Phelps said:**
> ]Actually, in many cases, it DOES do that. With ATI or Nvidia cards, you nearly always get the opportunity to install proprietary drivers, which you can often do simply by selecting System --> Administration --> Hardware Drivers.  In other cases, you can download and install the drivers from the AMD or Nvidia sites.

That's because everyone provides MS Windows drivers; they don't do the same for Linux.  The way to check your monitor is to go into System --> Preferences --> Screen Resolution and see what it says.  On my system, it has the brand name of the monitor (Syncmaster) and a list of possible resolutions.  If yours has "generic", you can experiment with different settings to see if you can get a higher resolution.[/I]

 As usual, it tells me "Unknown" and lists the two resolutions, 640x480 and 320x240 @ 50Hz - nothing else. :-(

> [I]Try the stuff I mentioned above to see if you can change the resolutions.
Also, open a terminal window and type "xrandr".  It will provide you a list of resolutions.[/I]

From terminal screen:

==========
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0  

==========

This Acer P201WD is capable of far more than this! I want to find out which file I should be editing and and its format.

---

### Post by Mark Phelps on 2009-03-27
I had the same problem with a different monitor and was able to set it up properly using the Screen Resolution applet by experimenting with different monitor brands and resolutions.  Before that, I was unable to get widescreen resolution no matter what I did.

---

### Post by Prof.Arronax on 2009-03-27
> **Mark Phelps said:**
> *I had the same problem with a different monitor and was able to set it up properly using the Screen Resolution applet by experimenting with different monitor brands and resolutions.  Before that, I was unable to get widescreen resolution no matter what I did*.

Mark, TTBOMK, in the Screen Resolution applet I didn't see an option panel anywhere for inputting the brand or type of monitor.  Am I missing something here??

---

### Post by upchucky on 2009-03-27
8.10 is not a long term release, it has issues with 3d, and specific issues with nvidia, there are workarounds, but you are better to use 8.04

with the above said, this is the proper way to set up nvidia on 8.04

I have not tested it with 8.10, cause of the 3d issues with 8.10



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

### Post by Prof.Arronax on 2009-03-29
> **upchucky said:**
> [I]8.10 is not a long term release, it has issues with 3d, and specific issues with nvidia, there are workarounds, but you are better to use 8.04

with the above said, this is the proper way to set up nvidia on 8.04[/I] 

I followed your suggestions and it worked *perfectly*... Until I selected that screensaver that alternates and shifts the space scenes.  The preview worked perfectly, but once committed the selection it has resulted in a **hard locked** machine that does not respond to anything whatsoever once I'm past the login screen.  DEAD.  No keyboard response, no mouse movement, no nothing.  A "*Red Button" (hard) *Reboot is the only way to get back to a log-in screen.  Disappointing to say the least, after having the screen resolution, colours, and effects working so nicely.  The system has gone daft.

Have you any method of doing a "safe-mode" boot up that I can attempt before re-installing the OS again?

---

### Post by Prof.Arronax on 2009-03-30
> **Prof.Arronax said:**
> *I followed your suggestions and it worked perfectly... Until I selected that screensaver that alternates and shifts the space scenes.  The preview worked perfectly, but once committed the selection it has resulted in a **hard locked** machine that does not respond to anything whatsoever once I'm past the login screen.  DEAD.  No keyboard response, no mouse movement, no nothing.  A "*[I]Red Button" (hard) Reboot is the only way to get back to a log-in screen.  Disappointing to say the least, after having the screen resolution, colours, and effects working so nicely.  The system has gone daft.

Have you any method of doing a "safe-mode" boot up that I can attempt before re-installing the OS again?[/I] 

A bit more research here...  I did a "recovery" reboot and told the system to fix broken packages; it did with some warnings about not being able to communicate with various servers since the networking had not started at that point... The problem turned out to be not the screen saver after all, but some anomaly with the SCSI Plextor CDROM; when I put an audio disk in it locks the machine - - The IDE DVD/CD doesn't have this effect.  And this effect did not show up under v8.10.  Both the IDE and SCSI optical devices co-existed just fine. . .  But I'll start another thread to cover this.

Thanks for the pointers about installing the NVidia properly - it works well.

---

