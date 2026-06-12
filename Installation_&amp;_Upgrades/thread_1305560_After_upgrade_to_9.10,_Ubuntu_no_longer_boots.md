---
title: "After upgrade to 9.10, Ubuntu no longer boots"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Depafro on 2009-10-30
[SIZE=3]**Summary**[/SIZE]
After upgrading to Karmic, Ubuntu doesn't finish booting, and flashes a full screen terminal with a login prompt.

[SIZE=3]**Background**[/SIZE]
I upgraded from 9.04 (fully updated)  to 9.10 Using the Alternate Download Cd as a mounted ISO according to [these instructions]("http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20from%20a%20Torrent"). I downloaded it using bittorrent.  It was necessary for me to do these additional commands to start the upgrade dialogue:[INDENT]*If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2: *
*gksu "sh /cdrom/cdromupgrade"*[/INDENT]I am using a LG R700-X.AP01A9 laptop with a Core 2 duo T7500. Nvidia graphics card. 
I have Ubuntu dual booted with Vista Home Premium using the Grub bootloader. 
I can access my ubuntu filesystem from within windows (or a liveCD, if necessary)
I have a second monitor using HDMI. Network: 802.11preN

[SIZE=3]**Problem**[/SIZE]

When I boot, I see the regular screen for awhile:[INDENT][I]Loading essential drivers...                                 OK
Running /scripts/init-premount                            OK
Mounting root file system...
Running /scripts/local-top                                   OK
Running /scripts/local-premount                          OK
Running /scripts/local-bottom                              OK
Running /scripts/init-bottom                                
Starting AppArmor profiles                                 OK
Preparing restricted drivers...
Starting AppArmor profiles
Starting clamAV virus database updater freshclam[/I]
[/INDENT]And then it switches to what appears to be a full-screen terminal:


[INDENT]<first few lines ommited for brevity and laziness>

[I]Begin: Running /scripts/local-premount ...
Done.
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Begin: Starting AppArmor profiles ...
Skipping profile in /etc/apparmor .d/disable: user.bin.firefox-3.5
Warning: found user.bin.freshclam in /etc/apparmor.d/force-complain, forcing complain mode
Done.
Done.

Ubuntu 9.10 depafro-laptop ttyl

depafro-laptop login: _[/I]
[/INDENT]the above screen flashes on and off about 5 times a second. 

I have only little experience with the terminal, but I tried to login, and  only  2 of the characters of my login name showed up on screen. The first ones did not appear on screen, and I was unable to login. My keyboard and screen work great in windows.

---

### Post by moe_syzlak on 2009-10-30
Many people are complaining up GRUB problems. I would wait and see. The solution should show itself soon in these here forums.

---

### Post by moe_syzlak on 2009-10-30
Since Ubuntu is not that good at configuring dual displays out of the box. I would try a fresh install with 9.10 livecd. Have only one monitor connected while doing so.

---

### Post by inearlygaveup on 2009-10-30
My system just loops continually at the sign in screen, even though I have auto login selected.
The screen just will not accept my password.
I did get in once - managed to check that auto loging was set ok - rebooted after 8 attempts I stll cant get back in.
Will probably re install 9.04

---

### Post by Strohfeuer on 2009-10-30
I have the same problem as the OP. I can not log in because of the flashing screen. Updating GRUB in the recovery mode didn't solve the problem. :(

---

### Post by layingback on 2009-10-30
Had same problem.

[Here]("http://ubuntuforums.org/showthread.php?p=8195286#post8195286")'s what worked for me.

---

### Post by Strohfeuer on 2009-10-30
thanks layingback, now I remember that I made the same mistake with the 3rd party before the upgrade. I don't have a Knoppix CD but in recovery mode I can view the xconf-file and there is now Nvidia driver. 
Is there another way to solve the problem?

I can do:
> 
less /etc/apt/sources.list

Which repositories should be diplayed there? I can not post my output. :-(

And how do I manually change the list in the terminal? Via the apt-get manager?

---

### Post by Strohfeuer on 2009-10-30
*bump* 
:???:

How do I add the appropriate drivers via apt-get?

---

### Post by Turtle.net on 2009-10-30
Quick and easy solution : dump the nvidia driver for the vesa one.
Boot in recovery mode. Access your prompt and 
```
sudo nano /etc/X11/xorg.conf
```Search the line with 
```
Driver "Nvidia"
```and change it to 
```
Driver "vesa"
```Then save (F3) and exit nano (Ctrl+x) and reboot.
You should end up with a dirty but functional graphical interface.

Then to really fix the problem ... I'm still looking into it ...

---

### Post by Turtle.net on 2009-10-30
I tried several options to solve this problem, here is what I have done to solve it (at least for me ...)
Make sure that the nvidia drivers are uninstalles (use synaptic, search for nvidia and uninstall completely).
Then follow this [process]("http://ubuntuforums.org/showthread.php?t=990978") to install the [latest nVidia]("http://www.nvidia.com/Download/index.aspx?lang=en-us") driver that you may require.
Reboot and smile :)

---

### Post by layingback on 2009-10-30
I used 9.10 Live CD, mounted HDD manually for read/write after finding device id using GParted, edited as sudo using nano to change "nvidia" to "nv" in 1 place in etc/X11/xorg-cong under driver.  Then it booted OK.  Alas this had interrupted the upgrade - shown as a partial upgrade - so had to redo.

[ After getting it upgraded I did install 1.90 nvidia driver - and this has changed it back to nvidia! :shrug: ]

I've just re-read the Release Notes.  I didn't miss anything - you are supposed to divine that switching Nvidia cards back to default before upgrade is required.  It's not for anything else, eg. Broadcom driver which is needed for network upgrade.  So should be spelt out IMHO.

---

### Post by Depafro on 2009-11-06
layingBack, I tried the method you linked, changing all the words "nvidia" to "nv" in xorg.conf. I did this from windows, as my ubuntu partition is mounted to drive U. While what the screen showed me did change, I still had no GUI, and so I changed it back. 

I have just downloaded the full ubuntu Cd, and I think I'm going to have to do a clean install.

---

### Post by Turtle.net on 2009-11-06
> **Depafro said:**
> layingBack, I tried the method you linked, changing all the words "nvidia" to "nv" in xorg.conf. 
Have you tried changing nvidia to vesa ?
I don't think that a clean install will change anything.
If changing manualy nvidia to nv or vesa doesn't solve your problem then ... a clean install will use one of these drivers anyway so you'l back to square one.
You should remove the packages installing the nvidia driver ```

sudo aptitude search nvidia
``` look at all the packages with a "i" in front of them and remove them {CODE]sudo apt-get remove ...[/CODE]
then make sure that your xorg.conf was changed to point the driver to vesa or nv (for me it worked better with vesa) and then reboot.

---

### Post by Depafro on 2009-11-07
No, I haven't given the vesa thing a try. I will do that now

Just to clarify, I'm changing nvidia to vesa in *every* line in xorg.conf, right? It says:

    Driver         "nvidia"

In about 3 places in mine.

---

### Post by Turtle.net on 2009-11-07
It should be in only one place ....
Maybe you should post your xorg.conf

---

### Post by Depafro on 2009-11-07
Tried the vesa thing. Didn't help at all. Whenever I try to do anything with apt-get or aptitude from the Ubuntu recovery terminal, I get the following message:

> W: Not using lock for read only lock file /var/lib/dpkg/lock
E: unable to write to /var/cache/apt
E: the package lists or status file could not be parsed or opened


Also, I've attached my xorg.conf.

---

### Post by Turtle.net on 2009-11-11
Disconnect your second monitor, use the file attached as your new xorg.conf
It's a minimalist version (I guess that using Karmic you could also just remove or rename your xorg.conf).
Then when everything is ok, install the nvidia driver (using Hardware Drivers utility for instance) then connect the second monitor and use nvidia-settings to do the configuration.

---

### Post by Depafro on 2009-11-12
Turtles.net, you are my new favourite person. 

I replaced xorg.conf from windows, disconnected the HDMI, and booted into ubuntu without a hitch.I have a full GUI and everything. 

Ubuntu has prompted me to finish the upgrade now, so I will go about doing that. Apparently I need to download 2GB of files?  I will post if there are any problems.

Thank you!

---

### Post by Turtle.net on 2009-11-12
2 gigs seems a little bit high ... but I don't know exactly what you have previously installed on your PC
Anyway, let us know if you achieve to reinstall nvidia driver and your second screen (should be a walk in the park now :p)

---

### Post by Depafro on 2009-11-13
Upgrade went smoothly, and I've reinstalled the Nvidia driver, and remade my Xorg.conf through the Nvidia server settings GUI, and I have dual screens at full resolution working in ubuntu. 

Thanks again, Turtles.net, I really appreciate your help.

---

