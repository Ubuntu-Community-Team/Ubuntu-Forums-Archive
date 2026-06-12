---
title: "Nvidia GeForce 8400GS: Black screen after installing Nvidia proprietary drivers"
date: 2014-04-17
forum: Hardware
---

### Post by carterly510 on 2014-04-17
Hi Ubuntu community!

I tried to install the Nvidia proprietary drivers through the >Additional Drivers graphic interface in Lubuntu 14.04. The install finished (To note: I was not prompted to restart my system) and I closed out of it. Everything seemed okay until I restarted my system. Once I restarted I get past the splash screen for my computer manufacturer (HP) and I get past the flashing underscore, but then I get a black screen and nothing happens.

My system specs are:
[LIST]
[*]Intel Pentium 4
[*]Nvidia GeForce 8400GS (PCI version if that matters)
[*]2GB DDR2 RAM
[/LIST]

If you need any more information please let me know. Thank you in advance for any help!

---

### Post by rbscycle on 2014-04-17
Just bought a used HPs3720f, Installed Ubuntu 13.10 & just tried 14.04.  No display.  It Has an NVIDIA 7100/630i.  Isn't Ubuntu supposed to work on older computers?  This unit has no problem with Windows VISTA or Windows 7.    On another computer, Ubuntu 10.10,  I see NVIDIA Setup Utility, sadly I can't get to it on the HP with a blank screen.

---

### Post by chesaro on 2014-04-18
You should try using the propietary drivers from nvidia ([http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)), the ones on the repository just don't work, i had a similar problem, but i just couldn't get the right resolution, but using the .run file fixed everything, just keep in mind that it's a little more hard to install.

Download the file -> Press 'Ctrl'+'Alt'+'F1'-> Login -> write 'sudo service lightdm stop' -> Give the file permission to execute the file (where you dowload it) 'chmod +x NVIDIA_(Model).run'->And execute 'sudo ./NVIDIA_(Model).run'

There's a problem with the Nouveau module, so you might have to restart once and enter again with the 'Ctrl'+'Alt'+'F1' combination, and execute the file again, i hope it works for you, good luck

---

### Post by 23dornot23d on 2014-04-18
@ 				 				 					 						 	[**[COLOR=#000000]carterly510[/COLOR]**]("http://ubuntuforums.org/member.php?u=1909885") 	 
 						[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]

Probably the 

linux 8400GS 173 legacy driver will work in Synaptic - search for it ....... this works with my 9300 gs m

Do a google search see what they say for solved and success .........

---

### Post by rbscycle on 2014-04-22
Problem is: My HP-s3720F screen is Blank after login!  I have re-installed, more than once, same problem!  No Screen After Login!

---

### Post by CitadelUniversal on 2014-04-22
Have you had a look at these [http://askubuntu.com/questions/350422/solved-optimus-nvidia-problemblack-login-screen-after-installing-ubuntu-12-04](http://askubuntu.com/questions/350422/solved-optimus-nvidia-problemblack-login-screen-after-installing-ubuntu-12-04) & [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it) - they may or may not help your situation.

---

### Post by Some_Old_Programme on 2014-05-10
I had a very similar problem.

My first boot of 14.04 LTS was sluggish due to high CPU usage of the compiz process. Installing the offered Nvidia driver (version 173.14.39) resulted in a login attempt getting a black screen with nothing but a cursor.

Via google, I followed instructions to remove the Nvidia driver, leaving me with a working system, but not viable for the long term due to high CPU utilization by the compiz process. Some suggestions to help that didn't work for me (e.g. changing compiz parameters to not sync to VBlank).

What saved my installation was to switch to a desktop that didn't use 3D effects; I used the instructions at [https://sites.google.com/site/easylinuxtipsproject/first](https://sites.google.com/site/easylinuxtipsproject/first)
See item 2.1 "Install gnome-session-flashback and consider disabling the visual effects".

So I'm now using a 2D desktop; the system is quite usable and I can wait for whenever the Nvidia driver is no longer borked to see if I want to switch back.

Hope this helps!
[h=3][/h]

---

### Post by Keermalec on 2014-11-13
> **carterly510 said:**
> Hi Ubuntu community!

I tried to install the Nvidia proprietary drivers through the >Additional Drivers graphic interface in Lubuntu 14.04. The install finished (To note: I was not prompted to restart my system) and I closed out of it. Everything seemed okay until I restarted my system. Once I restarted I get past the splash screen for my computer manufacturer (HP) and I get past the flashing underscore, but then I get a black screen and nothing happens.

My system specs are:
[LIST]
[*]Intel Pentium 4 
[*]Nvidia GeForce 8400GS (PCI version if that matters) 
[*]2GB DDR2 RAM 
[/LIST]

If you need any more information please let me know. Thank you in advance for any help!

Had the same issue and this is what worked for me:

1. install synaptic
sudo apt-get install synaptic

2. within synaptic, find the latest Nvidia driver by typing "nvidia" then search and checking version number (in my case v331.38)
nvidia-331-updates

3. after synaptic has done its thing, in a terminal:
sudo nvidia-xconfig

Now I get a perfect boot and am using driver v331.38, not the latest but the latest certified by canonical

:p:p:p

---

