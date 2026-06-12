---
title: "Today's 8.04.2 kernel patch update and Nvidia proprietary graphics driver"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by Riverside on 2009-04-07
Today's 2.6.24-23-generic #1 SMP Wed Apr 1 21:47:28 kernel patch update for 8.04.2 appears to have broken proprietary Nvidia (the version packaged with 8.04.2) graphics driver functionality.

For example:

[http://www.yoyo.org/~anthony/gfx_after_update.png](http://www.yoyo.org/~anthony/gfx_after_update.png)

See the artifacts now visible in rendering that (desktop background) image 3/4 of the way down.

Is anyone else seeing this or anything similar?

---

### Post by frodon on 2009-04-07
Do you use compiz ? if yes test without it if you have still the issue.

---

### Post by Riverside on 2009-04-07
In fact, this is really strange.  Further investigation has revealed that the Nvidia graphics are working fine but the desktop background wallpaper image file itself has become corrupted (as evidenced by a checksum comparison between it and a newly downloaded copy, and also when opening the file in the Gimp, a message about corrupt jpeg data is presented).

So, presumably, either my hard disk is beginning to fail (although no other files appear to be affected) or the act of rebooting somehow caused the background image file in use to be corrupted, presumably once the reboot had taken place?  If so, a Gnome bug perhaps?

---

### Post by Bearly Able on 2009-04-07
I think I have a related problem.  I'm also running 8.04 with Nvidia drivers, but since I installed this morning's updates, I can't boot into Ubuntu at all, not even in recovery mode.  I get "Error 17 - unable to load selected partition" (or something similar - sorry I should have written it down).  This is the only other post in the forums that seems to relate to the same issue, and I was beginning to think it was just me.

I have no idea what to do next and would be most grateful for any assistance.  I'm dual-booting with XP, but the Windows boot loader loads GRUB, not the other way around.

---

### Post by frodon on 2009-04-07
More likely your partition reference in boot/grub/menu.lst is wrong. Boot a live CD and check this file, especially the partition UUID.

---

### Post by Bearly Able on 2009-04-07
Thanks, frodon, but how do I change directory to edit the boot menu on the hard drive?  Also, what is UUID?

---

### Post by frodon on 2009-04-07
Through the live CD access your ubuntu partition with your file browser as usual, you should find the menu.lst file. It is the file GRUB reads to know what partition to boot.

The UUID is the ID of your partition, it is a number which identifies your partition. Type sudo vol_id -u /dev/sda1 to know the uuid of the corresponding partition, modify /dev/sda1 by the name of your ubuntu partition (do "sudo fdisk -l" if you don't know it).

Once you have the uuid number corresponding to your partition open the menu.lst file and check that this uuid is the one used for your partition if not bingo ! you just replace the wrong number by the right one and you're back to work.

ERROR 17 means that the partition specified in menu.lst exists but the filesystem is not correct (understand do not correspond to bootable OS)

---

### Post by Bearly Able on 2009-04-07
Thanks for that; we're back up and running. :)  I was expecting something difficult - it didn't occur to me to try anything as simple as gksudo nautilus!

It looks as if the update reset the boot info to point at the wrong hard drive.  I'll know in future to check for that before I start to panic (my husband hadn't backed up his files...).

Thanks for the explanations of UUID and Error 17.  I really want to learn as much as I can about Ubuntu and it helps when people take the time to explain these things - much appreciated.

---

### Post by frodon on 2009-04-07
Don't worry i know this only because it happened to me too once and i was like you when it occured, i was completely lost and someone there gave me the solution.

Maybe next time it's you who will be thanked by a user for solving his/her issue ;)

As a side note this is not supposed to happen to anyone but i have noticed from my experience than it can happen sometimes even if it is really rare. I never really understood how the upgrade-grub script (i think it is the guilty script) can sometimes do such wrong thing.

---

### Post by kenmiles on 2009-04-07
I am aso running 8.04 with nvidia and had problems with this upgrade. When booting it can't find the graphics card and boots in low graphics mode.
Boots into the previous kernel version without bother.
Is there a way to uninstall this upgrade?

Regards, Kenneth.
[http://kmiles.co.uk](http://kmiles.co.uk)

---

### Post by ronparent on 2009-04-07
I am running with 8.10 and had the same problem with this mornings kernel upgrade. I don't know if this work for anyone else, but I rebooted to the prior kernel. There was obviously no graphics driver loaded there, so, I tried to look at the System> Administrator> Nvidia X Server Settings and got an error box telling me to run nvidia-xconfig in a terminal. I did that and on reboot idadvertently used the latest kernel. Everything booted normal (with nvidia driver enabled)!!!!!!

---

### Post by upchucky on 2009-04-07
for those that do not get the nvidia working again with the new 8.04 patch.

the following is the only proper way to enable nvidia with 7.10 all the way up to 8.04

there are other ways like envy that do work on some machines, but they are workarounds and may or may not enable all the resolutions that nvidia can do.


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

### Post by frodon on 2009-04-07
Please at least explain to others (especially beginners) than installing nvidia drivers manually you may need to reinstall them after each kernel update so this is definitely not an option to recommend to beginners. Otherwise we may get even more of those "Last kernel update broke my ubuntu" threads because users installed manually nvidia drivers following a tutorial without knowing they will have to do it each time after kernel update, believe me we can see those threads appearing after each kernel update.
Advanced users are not concerned by this reminder.

---

### Post by Riverside on 2009-04-08
> **Riverside said:**
> In fact, this is really strange.  Further investigation has revealed that the Nvidia graphics are working fine but the desktop background wallpaper image file itself has become corrupted (as evidenced by a checksum comparison between it and a newly downloaded copy, and also when opening the file in the Gimp, a message about corrupt jpeg data is presented).

So, presumably, either my hard disk is beginning to fail (although no other files appear to be affected) or the act of rebooting somehow caused the background image file in use to be corrupted, presumably once the reboot had taken place?  If so, a Gnome bug perhaps?It appears unlikely that the issue has been caused by hardware failure and much more likely that an operating system (or perhaps, file system?) bug has caused the desktop background file that was in use at the time to become corrupted during the reboot.

The output of cmp -l run against the corrupted file, and a known good original, shows the byte numbers and values of all differing bytes:

[http://www.yoyo.org/~anthony/cmp_jpegs.txt](http://www.yoyo.org/~anthony/cmp_jpegs.txt)

---

