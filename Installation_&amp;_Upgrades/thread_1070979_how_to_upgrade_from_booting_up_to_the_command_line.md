---
title: "how to upgrade from booting up to the command line to a GUI"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by botanu on 2009-02-15
I've been running Ubuntu 6.06 for a couple of years on a Compaq Deskpro Pentium 3 650 MHz, 780 MG RAM, 10 GB HD. It was configured by a local organization for me originally to have a boot partition, a swap partition and an application and documents partition. I tried to upgrade to the 8.04 LTS using the Update Manager and Synaptic, but kept getting hung up by an error message that said not enough disk space to install the new operating system. Well, there was about 2 GB of free space plus I was trying to upgrade (and replace) the previous operating system. It was welcome to take the whole 10 GB, as far as I was concerned! But perhaps it had something to do with running out of space on the boot partition in particular.

So I finally figured out how to download and burn iso images of the 8.04 and 8.11 onto CDs to try and boot from the CD Drive and then perform the upgrade -- thinking that I would have an upgrade option. But whenever I used either of those CDs to boot and only had the option to install and repartition and not to upgrade. So I went ahead and tried to repartition and install 8.04 LTS. But it kept hanging during install or hang upon booting up and getting to the login screen, whereupon I would have no mouse control or keyboard input. I've been using the same mouse and keyboard for several years with 6.06 LTS with no problem with the drivers, but it seems that the new OSs both were having some issues there. Plus getting stuck during the install process.

Finally I got the alt CD for 8.04 to finish an installation but only by choosing the "Command Line" option. Now I get get booted into the command line from my HD but I can't figure out how to get to a GUI desktop environment or run Synaptic to finish installing packages. When I put in the command "synaptic" it says "Gtk warning" as if gtk isn't installed or allowing apps to run on top of it.

Sorry I'm a real newbie, but that's the best I can do at explaining my problem. I've been trying to use apt-get from the command line to install the gnome enviro or xfce or X11(?). And it's installed some packages, but I can't get any windows or programs that run in windows.

Thanks for you help,
brent

---

### Post by Partyboi2 on 2009-02-15
At the command line type
```
sudo apt-get install ubuntu-desktop
``` to install ubuntu desktop or if you are wanting the xubuntu desktop then
```
sudo apt-get install xubuntu-desktop
```

---

### Post by Neo_The_User on 2009-02-15
I do sudo aptitude and install the base of the desktop managers.

installing xubuntu-desktop or ubuntu-desktop installs too much apps for me.

---

### Post by botanu on 2009-02-15
Thanks for the suggestions. I installed ubuntu desktop as you recommended. It did hang at some point and so I rebooted. It came back to the command line. So I also installed xubuntu desktop and then I got a message that I needed to run "dpkg --configure -a" which I did. And that seemed to run its course, so I rebooted. I got to the graphical login screen and logged in, but I am back to hanging at the next splash screen which is all beige with the cursor stuck in the middle of the screen, but no desktop menu or panels on the top or bottom. And no cursor control. Keyboard commands (like Alt-F2 or Ctrl-Alt-Backspace) don't seem to work either. What do I do now? I did notice by running df that the partitions which were set up did not take advantage of the whole 10 GB of the HD , but were only using like 40%. I could never find any answer as to what are the partititioning requirements (or recommendations) for installing 8.04. Do I need to go back and repartition perhaps? I'm fumbling in the dark here.

---

### Post by botanu on 2009-02-15
Neo_the_User, 

I don't know what "the base of the desktop managers" are to install them individually. Nor do I understand what commands are required to run them individually. None of the Linux literature I have sets out that kind of procedure, nor have I been able to piece it together from what I've read online. I really need to have the user-friendly GUI interface, so I don't mind the app overhead of those desktop packages. (Maybe I'm in over my head and should just go back to XP or OS X. I'm becoming daunted having spent the better part of my President's Day holiday weekend downloading, installing, rebooting, soaping, rinsing, repeating.)

---

### Post by Partyboi2 on 2009-02-16
Normally you would see a beige screen if you are booting into the ubuntu-desktop. But if it was interupted before it had finished installing then that could be causing the problem. 

Since you installed the xubuntu-desktop as well when you are at the login screen select "options" before you attempt to login and select "xfce session" and see if you get to a working Desktop.

---

### Post by botanu on 2009-02-16
Sorry, I just ran df again and I think it's more like 70% of the 10 GB HD is accounted for in the current partitioning. It doesn't appear that any of the current partitions are full, though I wouldn't mind getting that other 30% back.

When I try to run "gksu synaptic" at the command line (in recovery mode) I get the message:

"(gksu:4394): Gtk-WARNING **: cannot open display:"

What does that mean?

---

### Post by botanu on 2009-02-16
I don't have "xfce session" as an option. Here they are:

Run Xclient script
GNOME
Secure Remote connection
Failsafe GNOME
Failsafe Terminal

Is Xclient the same as xfce?

---

### Post by botanu on 2009-02-16
Choosing the Xclient script hangs at the next splash screen (as before).

---

### Post by botanu on 2009-02-16
Choosing Failsafe GNOME hangs at the next splash screen (as before).

---

### Post by Partyboi2 on 2009-02-16
At the login screen press Ctrl+Alt+F2 to get to a terminal, then try removing compiz to see if that could be causing the problem.
```
sudo apt-get remove compiz compiz-core
```

---

### Post by botanu on 2009-02-16
I removed compiz but when I went back and resumed normal boot I got hung up (frozen cursor) at the login screen.

---

### Post by botanu on 2009-02-16
I have 6 choices at boot up. Two pairs of which look the same:

Ubuntu 8.04.2, kernel 2.6.24-23-generic
Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
Ubuntu 8.04.2, kernel 2.6.24-19-generic
Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
Ubuntu 8.04.2, memtest86+
Other operating systems:
Ubuntu 8.04.2, (8.04) (on /dev/sda1)

Can this be cleaned up? Because I really only want one: preferably Hardy, but Intrepid if that'll get me up and running.

---

### Post by Partyboi2 on 2009-02-16
> **botanu said:**
> I removed compiz but when I went back and resumed normal boot I got hung up (frozen cursor) at the login screen.
Since it does not seem to be compiz causing the problems you can reinstall it by going to a terminal and
```
sudo apt-get install compiz compiz-core
```
What graphics card are you using?

---

### Post by botanu on 2009-02-16
I know how to use the graphical Device Manager to find this info, but I don't know how to get it from a command line.

> What graphics card are you using?

---

### Post by Partyboi2 on 2009-02-16
> **botanu said:**
> I know how to use the graphical Device Manager to find this info, but I don't know how to get it from a command line.

> What graphics card are you using?
```
lspci
```

---

### Post by botanu on 2009-02-16
ATI 3D Rage Pro AGP 1x/2x (rev 5c)

---

### Post by botanu on 2009-02-18
Thanks PartyBoi2 for trying to help with this. I used the live CD for Intrepid and re-installed choosing the option to repartition the entire HD. I had wanted Hardy, but I'll settle for Intrepid. It appears to have installed correctly, and I'm up and running in Intrepid. I guess my problem was some sort of hang or freeze during the first install/partitioning, and the lesson I take from it is: if you have a problem during the installation, don't try to fix it, start over and re-install.

---

