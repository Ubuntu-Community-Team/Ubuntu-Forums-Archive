---
title: "Nvidia Driver help"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by enterman on 2009-06-15
Hello, I've been trying to install the video driver on a old desktop of mine but just can't get it to work right. It's using a Nvidia Vanta and EnvyNG says it needs the 71 drivers. Whenever I install them using EnvyNG and reboot I get stuck in low-graphics mode and the only way to make ubuntu work right again is to set it back to generic graphics... I've tried enabling the driver from the hardware drivers but no drivers appear in it. It says "No proprietary drivers are in use on this system." and a blank page is after that.

I've also tried running gksu nvidia-settings but I get this message "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."
[Here]("http://pastebin.com/m305536b") is my [xorg.conf]("http://pastebin.com/m305536b") and [this]("http://pastebin.com/m3fb622fb") is the result of a [lshw]("http://pastebin.com/m3fb622fb"). I've also tried doing what [this]("http://ubuntuforums.org/showpost.php?p=7428402&postcount=9") post said but it didn't fix my problem. I'm using ubuntu 9.04. This is what lspci called my GPU: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15). Any help anyone can provide is appreciated and let me know if you need any more info as I'll be happy to provide.

---

### Post by enterman on 2009-06-15
Anyone? Sorry for the bump but my thread has moved back to page 7 as of this post and I'd rather it not be invisible to those that can help.

---

### Post by jerrrys on 2009-06-16
The only suggestion I would have would be to give 8.04LTS a try.  Its not the latest and greatest, but it has a habit of just working out of the box.

---

### Post by enterman on 2009-06-16
> **jerrrys said:**
> The only suggestion I would have would be to give 8.04LTS a try.  Its not the latest and greatest, but it has a habit of just working out of the box.
Eh I'd really rather not... If I don't get an answer in a day or two I'll try that I guess.

---

### Post by enterman on 2009-06-18
I've tried using 8.10 as well as 8.04. I still had the exact same issue >< I've since reinstalled 9.04 since it seemed going back wasn't going to solve my issue (though I'll go back again if necessary). Anyone have any idea on what to do?

---

### Post by TrakerJon on 2009-06-19
ATI and Nvidia Drivers and Desktop Effects

The new Ubuntu 9.04 Jaunty Jackalope system comes with a Nouveau display graphic driver by default and the advanced effects cannot be used. If you've already tried to enable restricted Ubuntu drivers and ATI/nVidia cannot be found in the list try installing the ATI/nVidia driver with this tutorial:

1. Run Applications/Add/Remove
2. From the left menu choose System Tools
3. Next from the right menu, find and select for install: Desktop Effects (Compiz Setup) and ATI/Nvidia binary X.org Driver (nVidia could be version 173 or 177). Selecting the driver will get the list of supported graphics cards.
4. Click Apply Changes and after installation go to System/Administration/Hardware Drivers
5. The system will search for available drivers, choose the recommended option from the list and activate the driver by clicking Activate.
6. Restart your system and the new ATI/nVidia graphic display driver will be in use.

Note: [www.newegg.com](www.newegg.com) has legacy nVidia cards for under $50

---

### Post by enterman on 2009-06-19
> **TrakerJon said:**
> ATI and Nvidia Drivers and Desktop Effects

The new Ubuntu 9.04 Jaunty Jackalope system comes with a Nouveau display graphic driver by default and the advanced effects cannot be used. If you've already tried to enable restricted Ubuntu drivers and ATI/nVidia cannot be found in the list try installing the ATI/nVidia driver with this tutorial:

1. Run Applications/Add/Remove
2. From the left menu choose System Tools
3. Next from the right menu, find and select for install: Desktop Effects (Compiz Setup) and ATI/Nvidia binary X.org Driver (nVidia could be version 173 or 177). Selecting the driver will get the list of supported graphics cards.
4. Click Apply Changes and after installation go to System/Administration/Hardware Drivers
5. The system will search for available drivers, choose the recommended option from the list and activate the driver by clicking Activate.
6. Restart your system and the new ATI/nVidia graphic display driver will be in use.

Note: [www.newegg.com](www.newegg.com) has legacy nVidia cards for under $50
I did what you said, going to add/remove and installing the nVidia driver that listed my card in it's "supported card" list but there was one issue. The driver for my card was already installed. I tried reinstalling it (it's the 71 driver btw) and then went to hardware drivers but still, it was empty :(. Thanks for at least trying to help though. I don't understand the newegg comment btw lol, are you suggesting a get another card?

---

### Post by starcraft.man on 2009-06-19
Out of curiosity, what graphics card is in this old computer? That's always helpful to know.

I'm not quite sure why you've been having so much trouble. The only thing I can think of is to do a manual install. Go to the nvidia site, and find the specific linux driver you want to install, they keep most of them I think. Then, follow these instructions, to keep it simple make sure you download your drivers .run file to the /home/username directory.You'll be working in the command line for much of this so I advise printing it out.

I mostly do manual installs to get the bleeding edge linux driver for my nvidia card, you can use it with whatever package you want to install. Take note that during the steps you'll be editting the modules to force it, easily reversible if it fails. This also works for ATI binaries btw.

Oh and I didn't make the guide, it was someone else on this forum I forget who. >.> I hope it helps.

EDIT! : One small note I forgot, the last step 13 isn't essential (even though guide says recommended), you can just run the simple process over again if you don't want to go through that. You'll only need to do this process when you install a new kernel, not that often.

> Print out this guide, you will be in pure CLI for part of the install.

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

### Post by enterman on 2009-06-19
I'm about to try what you said starcraft.man, I just wanted to say to see my first post in this thread to find out what GPU is in this old computer.

EDIT: Well I followed the guide twice but to no avail. It was going fine till step 11.b/c. The installer never asked me if I wanted it to write a new xorg.conf but instead told me I need to edit it myself and to read /usr/share/doc/NVIDIA_GLX-1.0/README which I'm doing now.

---

### Post by starcraft.man on 2009-06-19
Ah, must be a really old driver. Nowadays it always asks. In any event the guide covers this, please go back to the terminal (or I assume you didn't start back the gdm) and type in "sudo nvidia-xconfig" that should do it. I'm pretty sure even an old driver should understand that. Or I could be wrong, I'm only human...

---

### Post by enterman on 2009-06-19
> **starcraft.man said:**
> Ah, must be a really old driver. Nowadays it always asks. In any event the guide covers this, please go back to the terminal (or I assume you didn't start back the gdm) and type in "sudo nvidia-xconfig" that should do it. I'm pretty sure even an old driver should understand that. Or I could be wrong, I'm only human...
ah yes I forgot to say, I input that command both times and it says that command doesn't exist (or something along those lines) ><

EDIT: I just attempted to make my own xorg.conf manually. It did not go well... I got the same error on boot as when I installed with EnvyNG (low graphics mode, failed to load module "nvidia" (loader failed, 7) No drivers available). Yes I believe it's a pretty old driver but it's the only one for my card.

---

### Post by starcraft.man on 2009-06-19
Ok, paste me a copy of your xorg and I'll see if it's ok. I can't make any promises, I'm not a super kernel/xorg hacker! I'm certain though that your driver is installed since you did it manually and didn't encounter any errors until the xorg config section. If this persists, maybe the old nVidia driver just isn't any good and since it's out of support cycle I think they may just be an out of luck case >.>.

Can always find a cheap newer AGP nVidia card for less than 50 bucks I'm sure.

---

### Post by enterman on 2009-06-19
[Here]("http://pastebin.com/m8acb67e") is the current xorg.conf file I made. My original xorg.conf is in my first post in this thread. I got some of the info from [this person's]("http://forum.ubuntuusers.de/topic/compiz-nvidia-3d-desktop:-effects-could-not-b/?highlight=v4l#post-1119356") xorg.conf. The reason I used some of the info from his is because he was using the exact same monitor that I'm using for this particular computer.

---

### Post by starcraft.man on 2009-06-19
Quite the quandary. I disclose upfront that I'm no expert, but the entry for device (your gfx card) appears correct, as does most of the rest. It points to the nvidia driver and that driver should have installed since you didn't report errors in the manual install.

Ah, I just had a thought. I am thinking that this ancient driver your trying to install simply isn't compatible with the latest xorg/other subsystems of Ubuntu. That's not something I believe we can fix, I assume the latest driver has cut support for your card and as such, I think the only solution is buying a newer one in support or putting up with vga.

Sorry I can't deliver better news. The only other way would be to downgrade heavily to a version of Ubuntu that it works with but I don't think that's worth it at all, like going back to mesozoic age.

---

### Post by enterman on 2009-06-19
> **starcraft.man said:**
> Quite the quandary. I disclose upfront that I'm no expert, but the entry for device (your gfx card) appears correct, as does most of the rest. It points to the nvidia driver and that driver should have installed since you didn't report errors in the manual install.

Ah, I just had a thought. I am thinking that this ancient driver your trying to install simply isn't compatible with the latest xorg/other subsystems of Ubuntu. That's not something I believe we can fix, I assume the latest driver has cut support for your card and as such, I think the only solution is buying a newer one in support or putting up with vga.

Sorry I can't deliver better news. The only other way would be to downgrade heavily to a version of Ubuntu that it works with but I don't think that's worth it at all, like going back to mesozoic age.
ah well at least we have finally figured it out. Thanks for trying to help, I'll just stick with the generic driver then I guess or go back to tinyxp on it though I'd really rather not do that either lol.

---

