---
title: "Nvidia 8600GTS crashing Ubuntu."
date: 2008-12-22
forum: Hardware
---

### Post by travislhendrix on 2008-12-22
I have been trying to install Ubuntu for a couple of days now.  Everything goes well, except that I cannot get my video card to install.  I have an ECS NFORCE 4M-A v3.0 motherboard.  The video card I have is an Nvidia 8600GTS.  I have tried ubuntu 8.04 and 8.10.  I have updated Ubuntu before installing the video card drivers, and have tried the 177.82 driver from Nvidia's site and tried the 2 drivers available from the hardware drivers section of Ubuntu.  Every time the driver installs correctly then it asks me to reboot.  When I reboot Ubuntu, it boots into a low resolution mode.  I have to revert to the original X server file to get it to boot normal.  I am very good with Windows but am pretty new to linux.  What am I missing?

---

### Post by travislhendrix on 2008-12-28
what could be causing ubuntu to boot into low resolution mode, and is there a config file I can upload to help figure out what the problem is?  Do you need any more information?

---

### Post by Captain_tux on 2008-12-28
Can you get to a GUI? If so, try activating the nVidia driver through System > Administration > Hardware Drivers.

Buena suerte!

---

### Post by Rohan Kapoor on 2008-12-29
> **Captain_tux said:**
> Can you get to a GUI? If so, try activating the nVidia driver through System > Administration > Hardware Drivers.

Buena suerte!

He said that makes him reboot into low-graphics mode. Try this guide (skip the dual monitors part)

[http://vasir.net/blog/ubuntu/set-up-dual-monitors-with-ubuntu-804](http://vasir.net/blog/ubuntu/set-up-dual-monitors-with-ubuntu-804)

---

### Post by travislhendrix on 2008-12-30
I followed the instructions on using EnvyNG, and they kind of worked.  They booted the computer into the low resolution mode again, but the error on the screen said that the video card's external power supply was not connected (it is) and that if I get the error when I should not to add a line to my xorg.conf file.  I found that file and in the screen section I added Option "NoPowerConnectorCheck"  it now boots up fine.  When altering screens and resolutions using the Nvidia X server settings it will not save so I had to copy the contents out of the preview and past them into the xorg.conf file.  It now works great.  Thanks for your help. :D

---

### Post by Rohan Kapoor on 2008-12-30
> **travislhendrix said:**
> I followed the instructions on using EnvyNG, and they kind of worked.  They booted the computer into the low resolution mode again, but the error on the screen said that the video card's external power supply was not connected (it is) and that if I get the error when I should not to add a line to my xorg.conf file.  I found that file and in the screen section I added Option "NoPowerConnectorCheck"  it now boots up fine.  When altering screens and resolutions using the Nvidia X server settings it will not save so I had to copy the contents out of the preview and past them into the xorg.conf file.  It now works great.  Thanks for your help. :D
Glad to help. Just remember if you upgrade to 8.10 don't use Envyng, it completely messed up my install.

---

### Post by travislhendrix on 2008-12-31
> **darth-vader said:**
> Glad to help. Just remember if you upgrade to 8.10 don't use Envyng, it completely messed up my install.

What did it do to your install?  I used it on 8.10 and I have not noticed any problems, except that the grub option for my Vista no longer works so I had to find a work around for that, but I am not sure that they are even related.

---

### Post by Rohan Kapoor on 2008-12-31
> **travislhendrix said:**
> What did it do to your install?  I used it on 8.10 and I have not noticed any problems, except that the grub option for my Vista no longer works so I had to find a work around for that, but I am not sure that they are even related.
Here's exactly what happened to me when I used EnvyNG on Ubuntu 8.10:

1. Brand new install
2. Install EnvyNG
3. EnvyNG Gui doesn't work
4. Install ATI drivers from CLI (EnvyNG)
5. Reboot Ubuntu into low-graphics mode
6. From CLI uninstall EnvyNg and Ati drivers
7. Reboot, Ubuntu freezes on every boot with the screen going garbled.
8. From CLI, restore xorg.conf and reboot
9. Screen still is garbled.
9A. Checking xorg.conf from CLI shows that is has become the same messed up version, so something from EnvyNG is messing up my xorg.conf every boot!


Working way of doing it:
1. Install Ubuntu 8.10
2. Install Restricted Drivers which included the ATI one.
3. Reboot and suddenly everything works including Compiz!!!



I probably should rephrase my original statement. Do not use EnvyNG to install ***ATI*** graphics cards in 8.10 because it will mess up your system.

---

### Post by travislhendrix on 2009-01-01
> **darth-vader said:**
> Here's exactly what happened to me when I used EnvyNG on Ubuntu 8.10:

1. Brand new install
2. Install EnvyNG
3. EnvyNG Gui doesn't work
4. Install ATI drivers from CLI (EnvyNG)
5. Reboot Ubuntu into low-graphics mode
6. From CLI uninstall EnvyNg and Ati drivers
7. Reboot, Ubuntu freezes on every boot with the screen going garbled.
8. From CLI, restore xorg.conf and reboot
9. Screen still is garbled.
9A. Checking xorg.conf from CLI shows that is has become the same messed up version, so something from EnvyNG is messing up my xorg.conf every boot!


Working way of doing it:
1. Install Ubuntu 8.10
2. Install Restricted Drivers which included the ATI one.
3. Reboot and suddenly everything works including Compiz!!!



I probably should rephrase my original statement. Do not use EnvyNG to install ***ATI*** graphics cards in 8.10 because it will mess up your system.

About the same thing happened to me.  Here is what happened.
1. Installed Envyng-core and Envyng-gtk
2. There was no 'System Tools' listed under applications so I installed Envying-qt to see what it would do.
3. Now it had EnvyNG listed under applications - system tools.
4. Installed the Nvidia driver.
5. Rebooted and got the low resolution error but it contained the line about not having power connected to it.  
6. Selected the option to use the original conf file. (not sure exactly what this was I believe that I clicked ok on the error and then clicked the box for reconfigure x-server or reconfigure graphics or something like that, then there was an option to use the original.  I selected that and rebooted and it boots with the original xorg.conf file.)
7. Followed the steps I listed in the above post and that got me into Ubuntu without any problems.

I am not sure if other people have had similar problems, but I am going to try it on 8.04 and see if it does anything different.

---

### Post by Rohan Kapoor on 2009-01-01
> **travislhendrix said:**
> About the same thing happened to me.  Here is what happened.
1. Installed Envyng-core and Envyng-gtk
2. There was no 'System Tools' listed under applications so I installed Envying-qt to see what it would do.
3. Now it had EnvyNG listed under applications - system tools.
4. Installed the Nvidia driver.
5. Rebooted and got the low resolution error but it contained the line about not having power connected to it.  
6. Selected the option to use the original conf file. (not sure exactly what this was I believe that I clicked ok on the error and then clicked the box for reconfigure x-server or reconfigure graphics or something like that, then there was an option to use the original.  I selected that and rebooted and it boots with the original xorg.conf file.)
7. Followed the steps I listed in the above post and that got me into Ubuntu without any problems.

I am not sure if other people have had similar problems, but I am going to try it on 8.04 and see if it does anything different.
I see. Then it seems to be a common problem with EnvyNG in 8.10. Except you managed to fix your xorg.conf and mine kept reverting to the faulty one ***every*** boot!

---

### Post by travislhendrix on 2009-01-01
> **travislhendrix said:**
> I am going to try it on 8.04 and see if it does anything different.

1. Installed a clean copy of 8.04 then updated it.
2. Installed Envyng-core and Envyng-gtk
3. Used Envyng to install the Nvidia driver.
4. Rebooted and got the low resolution problem, but could not get to the options to revert to the old copy and could not read the error message.
5. booted from the Ubuntu Live cd and added the "NoPowerConnectorCheck" option to the xorg.conf file.
6. Rebooted into Ubuntu 8.04.
7. Ran Nvidia X Server Settings as administrator and updated it to the right resolution and number of monitors.
8. Rebooted and it went back to low res.  
9. booted from the Ubuntu Live cd again and replaced the xorg.conf with the backup.
10. booted back into ubuntu fine.  
11.  Ran Nvidia X Server Settings as administrator and updated it to the right resolution and number of monitors again, but this time unchecked the box that says "Merge with existing file."
12.  added the "NoPowerConnectorCheck" option to the xorg.conf file yet again and this time have a perfectly working good install of the driver.

Wow was that a learning adventure.  Thanks a ton for all your help.:D

---

### Post by starcannon on 2009-01-01
Using either the drivers from Ubuntu Hardware Drivers manager, or using the nvidia.com drivers:

[LIST]
[*]Press CTRL-ALT-F1 at the log in screen
[*]enter your username and password when prompted
[*]type ```
sudo nvidia-xconfig
```
[*]type ```
sudo /etc/init.d/gdm restart
```
[/LIST]
That may get you going. I have the Nvidia 8400m GS and have not had any issues getting it working. I have a guide that you can try if you like, it is how I do all of my nvidia installs:
[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

GL and have fun

---

### Post by Rohan Kapoor on 2009-01-01
> **starcannon said:**
> Using either the drivers from Ubuntu Hardware Drivers manager, or using the nvidia.com drivers:

[LIST]
[*]Press CTRL-ALT-F1 at the log in screen
[*]enter your username and password when prompted
[*]type ```
sudo nvidia-xconfig
```
[*]type ```
sudo /etc/init.d/gdm restart
```
[/LIST]
That may get you going. I have the Nvidia 8400m GS and have not had any issues getting it working. I have a guide that you can try if you like, it is how I do all of my nvidia installs:
[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

GL and have fun

You may not have noticed but the problem is solved and this was the results of an experiment that travislhendrix was trying and sharing! His problem has already been fixed!

---

### Post by travislhendrix on 2009-01-02
> **darth-vader said:**
> You may not have noticed but the problem is solved and this was the results of an experiment that travislhendrix was trying and sharing! His problem has already been fixed!

you thought that answer was kind of comical also didn't you darth-vader.  The idea never would have worked and it was obvious that he had not read any of the rest of the thread.

---

### Post by Rohan Kapoor on 2009-01-02
> **travislhendrix said:**
> you thought that answer was kind of comical also didn't you darth-vader.  The idea never would have worked and it was obvious that he had not read any of the rest of the thread.
It was highly comical. The idea would have worked... just not on your computer! Yes it was obvious that he read (parts of) the first post and nothing else.

---

### Post by starcannon on 2009-01-04
The thread should be marked as SOLVED, and as for what I read or did not read, it makes little difference. I only posted the solution I thought would work; further, your attitude is not becoming of the general way we do things here on the ubuntuforums; if the forums are going to turn into nothing more than a bridge for troll to hang out under, I will move on to something else.

Peace

---

