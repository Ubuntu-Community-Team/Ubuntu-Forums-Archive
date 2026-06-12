---
title: "Nvidia graphics card not working on ubuntu 8.10"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by wisedrunkard on 2009-04-12
I just upgraded from ubuntu 8.04 to 8.10 and have tried using envy to install my graphics drivers with no success. I've also tried manually installing the driver from the Nvidia website and using synaptic package manager to install drivers.

My graphics card used to work perfectly with ubuntu 8.04 and was simple to install. So far I've had no success figuring this out.

Anybody familiar with the problem?

---

### Post by tommcd on 2009-04-12
Did you remove --purge the old driver(s) before installing the new ones? Installing the nvidia driver from envy, nvidia.com, and synaptic without completely removing the old driver first before installing the new one is asking for trouble.

What nvidia card do you have? If you have a fairly recent card you can use nvidia-glx-180 or nvidia-glx-177 from synaptic. Completely remove *all* nvidia drivers. Then check out nvidia-glx-180 and nvidia-glx-177 in synaptic. See which one supports your card. It is possible they both do. Pick one of those, install it, then run:
```
sudo nvidia-xconfig
```
to configure the driver. Then reboot.

---

### Post by inobe on 2009-04-12
any information for the hardware in question, what type of card is it ?

---

### Post by wisedrunkard on 2009-04-13
Thanks for the replies guys. Here's some info on the computer I'm using.

Processor                 AMD Athlon 64 X2 2.6 GHz
Chipset                   NVIDIA GeForce 8600 GT
Installed Memory          2 GB (DDR2 SDRAM)
Video Output Interface    PCI Express
Hard Drive Interface      Serial ATA

I've purged the old Nvidia drivers but this didn't seem to do anything.
Typing 'sudo nvidia-xconfig' in the terminal brings up:


Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have
                  a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


Also, whenever I try to start up NVIDIA X Server Settings I get the message:


You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 


Does this help at all?

---

### Post by tommcd on 2009-04-13
> **wisedrunkard said:**
> 
Chipset                   NVIDIA GeForce 8600 GT

If you type in terminal:
```
aptitude show nvidia-glx-180
```
You will see that the 8600GT is supported by that driver. The nvidia-glx-177 driver supports the 8600GT also. I would use the 180 driver, since it is newer and you have a fairly recent video card.
> **wisedrunkard said:**
> 
I've purged the old Nvidia drivers but this didn't seem to do anything.
Typing 'sudo nvidia-xconfig' in the terminal brings up...

Did you install a *new* nvidia driver? After purging all the old drivers you have to install a new driver (and only from 1 source this time). To install the 180 driver, hit ctrl + alt + F2 to get to a virtual terminal, login, and run:
```

sudo /etc/init.d/gdm stop
sudo apt-get install nvidia-glx-180
sudo nvidia-xconfig
sudo reboot

```
This should get the driver working for you. Assuming you can then boot to a working desktop, open a terminal and run:
> glxinfo | grep -i direct
It should retun "direct rendering yes".

---

### Post by Johnny19734 on 2009-04-13
Just use ENVY 

[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

---

### Post by upchucky on 2009-04-13
since you do not have a working nvidia you could try this, it is the proper way to set up nvidia on 8.04

other methods including Envy worked on some machines but not all machines, as they were just workarounds and more often than not did not set up to have multiple resolutions available.

with that said, this solution is for 8.04 I do not know if it worked for 8.10 and i have not tested it since 8.10 is not a long term supported release.
Please if you decide to give this a go, post the results here, or if it works as well as it does for 8.04 make a new thread declaring how to and posting the solution for everyone.



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

### Post by imaginashawn on 2009-04-13
First of all, let me be the first to point out, I don't know squat ok? lol But one of my machines is a Duron, and I just installed the nvidia 5200 using the linux driver I downloaded from nvidia's site and it worked first try. Hope this helps.

---

### Post by Johnny19734 on 2009-04-13
Dude just go ENVY, if you do an update and the graphics mess up just open ENVY and run it again. IF your a noob you don't want to  manually compile the kernel, install the crap to compile the kernel and do this in command line as listed above. ENVY take care of all that for you.

---

### Post by tommcd on 2009-04-13
The nvidia driver from the Ubuntu repos should always be your first choice. You should only consider using envy or the driver from nvidia.com if the drivers from the Ubuntu repos don't work in your situation for some odd reason. Or if you absolutely must have the latest driver from nvidia.com as soon as it is available. Usually, this is not the case.
There is no advantage to using the driver from nvidia.com as long as the driver in the Ubuntu repos is working ok.

Using Ubuntu's package management system to instsall and maintain the driver results in a cleaner, and easier to manage system. Using the driver from nvidia.com will require you to reinstall the driver when there is a kernel update for Ubuntu. With the driver from the Ubuntu repos, this is done automatically.
The OP said he tried envy and had problems. He should try just using the driver from the repos first. 
Nvidia guru TSEliot (the author of envy) even recommended the driver from the Ubuntu repos as his "method 1" in this very detailed (although out of date) guide:
[https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)

---

### Post by silentrebel on 2009-04-14
Try Johnny19734's suggestion, it worked very well for me:

```
sudo apt-get install envyng-gtk
```

This should help you find the best nVidia driver for your card, in most cases. Just choose the nVidia option. Then choose the driver that is compatible and recommended. If such a driver is not suggested, you'll have to risk using one of the other offered drivers. If I find any other useful information, I'll let you know.

---

### Post by Chudilo on 2009-04-14
I say  use envy. 
You can't go wrong there.

---

### Post by Claus7 on 2009-04-14
Hello,

because none of the above suggestions worked for me, in case you belong to this adorable category, then I would advice you the following:
stick with 180 nvidia kernel, after you have got rid of everything else that has to do with nvidia and the like. Then take your original xorg.conf file (which was working) and with some tweaking here and there, you will have a descent graphical enviroment. In case something brokes (e.g. during an update) I think that you can retry in 10 days or so where the final distro will be out (that's in jaunty). Also you will be able to send feedback to the ubuntu developers (jaunty too).

In intrepid I have read that the situation is similar. I hope that you will be able to fix your problem by configuring your xorg.conf file.

Regards!

---

### Post by Johnny19734 on 2009-04-14
You guys will get alot of Gung-Ho linux ubuntu people out here. This is an open source community and everyone has alot to offer even  the author ENVY. :) Remember when you update the kernel you might have to run ENVY agian. Each time the kernel changes the graphic driver has to be reinstalled. But always try use the restricted drivers if available in the next update! On the PLUS side ENVY uses the latest and greatest drivers! So you might even get a boost in performance! (I dunno how much that will affect a 5200 though) hehe

---

