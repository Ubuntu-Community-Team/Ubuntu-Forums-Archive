---
title: "[SOLVED] White screen D:"
date: 2008-09-13
forum: General Help
---

### Post by claymater on 2008-09-13
OK guys! i need help quick! When I log into ubuntu (as normal) it goes, plays the log on sound, and then it turns to a black screen then a white one D: 
I waited a bit to see if it would go away (like 10-20 min) and it didnt :( I am right now logged into the failsafe mode. it "works" there. but I still dont get my stuff that i should get when I log in, It started to happen when I was trying to fix the dual screen thing I was working on before, any help?!?! (if you need more info, ask)

---

### Post by phidia on 2008-09-13
Sounds like your xorg.conf might be the problem. Did you create a backup or is there a backup xorg.conf in your /etc/X11 directory?
If you can't find/use a backup you could try to reconfigure x by > sudo dpkg-reconfigure xserver-xorg

---

### Post by Neo_The_User on 2008-09-13
I used to have a lot of problems with Ubuntu dual-screens. Ubuntu handles all the drivers and pretty much anything to do with dual monitors very poorly. It is a train wreck. The Ubuntu developers have HUGE egos with all that stuff so its a real pain (don't say its not Ubuntu's fault because Fedora works just fine for stuff like this)

How I fix it with an ATi card

1.) Fresh install of Ubuntu 8.04.1 LTS

2.) Restart computer.

3.) Install accelerated drivers (System > administration > Hardware drivers)

4.) Restart computer

5.) Go to [http://ati.amd.com/support/driver.HTML](http://ati.amd.com/support/driver.HTML) and download the linux x86 driver for my graphics card (Radeon 9800 series)

6.) I run this command into the terminal:

sudo chmod +x (drag the ati installer binary here)

7.) I run this command into the terminal

sudo (drag ati binary here)

8.) I select "install on xorg 7.1 and later releases" or something along those lines

9.) I select automatic.

10.) Restart computer.

11.) Applications > ATi Catalyst Control Center (if it doesn't show up go into the terminal and type in this code

sudo amdcccle

12.) I configure all my settings the way I want. (Display manager > multi-display and select my options)

13.) I restart computer.




How I fix it via nVIDIA card (really bad)

1.) Fresh install of Ubuntu 8.04.1 LTS

2.) Restart computer

3.) Install accelerated drivers (System > administration > Hardware drivers)

4.) Restart Computer.

5.) Open up terminal and type in this code

sudo apt-get install envy

6.) Launch Envy (EnvyNG) from Applications from the toolbar

7.) Select install the nvidia driver automatically

8.) Wait for Envy to do its thing

9.) Restart computer

IF UBUNTU DOES NOT BOOT-UP IN LOW GRAPHICS MODE AFTER DOING THAT (99% of the time it doesn't ever work the way you want) then you can adjust your settings in the nvidia control panel x configurer or whatever they call it located in System > Administration I THINK

IF UBUNTU DOES BOOT-UP IN LOW GRAPHICS MODE then your going to have so much fun messing with Envy for 20 minutes trying to get it working (magic combination of settings that I deciphered a long time ago but forgot exactly what I did)

---

### Post by claymater on 2008-09-15
Haha, thanks guys, it is fixed :)

---

