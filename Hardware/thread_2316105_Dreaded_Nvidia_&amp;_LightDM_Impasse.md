---
title: "Dreaded Nvidia &amp; LightDM Impasse"
date: 2016-03-05
forum: Hardware
---

### Post by satan3 on 2016-03-05
Hi everyone,

I'm running Ubuntu Mate 15.10 alongside Windows 8.1 on a Dell Inspiron 7537 with a Nvidia GeForce GT 750M GPU.  Like a fool, I tried to switch from the X.org Nouveau  driver to the recommended Nvidia proprietary driver and on a reboot got the message 

```
Starting Light Display Manager... and dealing with any changes. signatures... ut down..
```
At which point the system hangs, and there's nothing to do but go into tty using Ctrl-Alt-F4 or something like that.

After some googling, this seems to be quite the standard problem, LightDM doesn't know how to handle Nvidia chips, which is in turn a standard annoying Ubuntu problem - out of nowhere comes a problem with no warning when two bits of technology are connected.  While not being a total novice with Ubuntu, I'm no expert either, so I couldn't fully understand the ins and outs of this problem  

So here's some information and things i have tried:


[LIST]
[*]'cat /etc/x11/default-display-manager' says it's LightDM 
[*]tried 'sudo dpkg-reconfigure lightdm'
[*]'/etc/x11/xorg.conf' had an error, which says 'The number of screens doesn't match the number of detected devices'.  I have only one screen. 
[*]and i think '/var/log/lightdm/x-0.org' says 'Fatal Server Error: No screens found' and refers me to wiki.x.org. 
[*]Tried removing and purging Nvidia drivers and reinstalling 
[*]Tried reinstalling the nouveau driver 
[*]Tried installing Bumblebee 
[/LIST]


But nothing worked.  I couldn't even get it back to the way it was and after 9 hours messing around had to reinstall Ubuntu Mate again, good grief.  I still would like to make use of the Nvidia drivers but don't want to mess up my installation again.  Anyone have any pointers?  What the hell am i doing wrong?   Is Bumblebee relevant here? 

Any advice would be really appreciated...

---

### Post by vidtek on 2016-03-05
> **satan3 said:**
> Hi everyone,

I'm runnning Ubuntu Mate 15.10 alongside Windows 8.1 on a Dell Inspiron 7537 with a Nvidia GeForce GT 750M GPU.  Like a fool, I tried to switch from the X.org Nouveau  driver to the recommended Nvidia proprietary driver and on a reboot got the message 

```
Starting Light Display Manager... and dealing with any changes. signatures... ut down..
```
At which point the system hangs, and there's nothing to do but go into tty using Ctrl-Alt-F4 or something like that.

After some googling, this seems to be quite the standard problem, LightDM doesn't know how to handle Nvidia chips, which is in turn a standard annoying Ubuntu problem - out of nowhere comes a problem with no warning when two bits of technology are connected.  While not being a total novice with Ubuntu, I'm no expert either, so I couldn't fully understand the ins and outs of this problem  

So here's some information and things i have tried:


[LIST]
[*]'cat /etc/x11/default-display-manager' says it's LightDM 
[/LIST]

[LIST]
[*]tried ```
 sudo dpkg-reconfigure lightdm
``` 
[*]'/etc/x11/xorg.conf' had an error, which says 'The number of screens doesn't match the number of detected devices'.  I have only one screen. 
[*]and i think '/var/log/lightdm/x-0.org' says 'Fatal Server Error: No screens found' and refers me to wiki.x.org. 
[*]Tried removing and purging Nvidia drivers and reinstalling 
[*]Tried reinstalling the nouveau driver 
[*]Tried installing Bumblebee 
[/LIST]


But nothing worked.  I couldn't even get it back to the way it was and after 9 hours messing around had to reinstall Ubuntu Mate again, good grief.  I still would like to make use of the Nvidia drivers but don't want to mess up my installation again.  Anyone have any pointers?  What the hell am i doing wrong?   Is Bumblebee relevant here? 

Any advice would be really appreciated...

Satan (really?) -
You could try replacing lightdm with another such as sddm.
I run 15.1 on a nvidia card with sddm and it works well, always had problems with lightdm.
You may run into the login screen small fonts issue where the edid is wrong, 
you can generate a new xorg.conf with this:
```
sudo nvidia-xconfig --no-use-edid-dpi
```
Then add this to the "monitor" section of the file
```
Option "DPI" "96 x 96"
```

That should fix it.
Cheers, Tony.

---

### Post by satan3 on 2016-03-05
Thanks a million for your swift reply Tony, it is indeed I the Prince of Darkness.  Fallen on hard times for my sins, i'll give this a go and report back, for some reason it never occurred to me i could switch display managers...

---

### Post by satan3 on 2016-03-05
So i installed sddm, which went fine, then installed the recommended nvidia driver, rebooted and had more or less the same problem, though this time it got stuck at a black screen except for some text that said something about sda6 (where ubuntu lives) being fine, then it hangs.  Thankfully using tty i was able to roll back the nvidia driver and i'm back again with the old nouveau driver.

Tried a bunch of other Display Managers willy nilly, all failed, some made everything blink, none were helpful.  I'm thinking perhaps it has something to do with the fact that it's Mate, though thats a wild guess. 

Like so many other problems with Ubuntu, there's no warning or recommendations and it's up to the user to put things together and find a solution, god knows what it's like for someone who hasnt' a notion what  they're doing, which is most people making the leap from proprietary software to open source, and this is what they're faced with.  If it wasn't for people like yourself Vidtek, it would be a total loss.  

Any other suggestions?

---

### Post by vidtek on 2016-03-06
> **satan3 said:**
> So i installed sddm, which went fine, then installed the recommended nvidia driver, rebooted and had more or less the same problem, though this time it got stuck at a black screen except for some text that said something about sda6 (where ubuntu lives) being fine, then it hangs.  Thankfully using tty i was able to roll back the nvidia driver and i'm back again with the old nouveau driver.

Tried a bunch of other Display Managers willy nilly, all failed, some made everything blink, none were helpful.  I'm thinking perhaps it has something to do with the fact that it's Mate, though thats a wild guess. 

Like so many other problems with Ubuntu, there's no warning or recommendations and it's up to the user to put things together and find a solution, god knows what it's like for someone who hasnt' a notion what  they're doing, which is most people making the leap from proprietary software to open source, and this is what they're faced with.  If it wasn't for people like yourself Vidtek, it would be a total loss.  

Any other suggestions?

Satan-

Sorry to do this to you but I've never had any success with Mate other than the live DVD version using nouveau.
I migrated to KDE a few years ago and never regretted it.  KDE admittedly has a few bugs, but they are well known and documented, and usually only minor ones.  There is also a great KDE development team and forum.  It takes a little bit of a learning curve, but with Plasma desktop is ultra-configurable and a smooth, intuitive and beautiful interface.
The "activities" are useful now that the multiple desktops no longer support different icon, widget and backgrounds, I now use them instead of multiple desktops.  This is not as smooth and intuitive as the old KDE without activities but the development team decided for good or ill that activities are the way forward.  I personally think it's a retrograde step to remove the option for a different icon, widget and backgrounds set in multiple desktops, but it's not going to change any-time soon.

So, my next suggestion would be to re-install sddm and run KDE on top instead of Mate.  Don't forget to put the dpi setting to 96 in xorg.conf after installing the nvidia driver as per my last post; otherwise you may not be able to read the fonts on the login screen, they will probably be tiny otherwise, depending on your monitor.
 
Best of luck, Tony.

---

### Post by mastablasta on 2016-03-07
> **satan3 said:**
> 

Any other suggestions?
obviously it's not a display manager issue.

have you tried using nomodeset boot parameter?

also the system doesn't hang if you can go to another TTY console. the x might have crashed though. you should be still able to create NVidia report if you had to.

---

### Post by SeijiSensei on 2016-03-07
I am also a happy KDE user for well over a decade now and am running Kubuntu 14.04 with a GTX 750.  I installed the nvidia-346 driver package which seems to work well:
```

sudo apt-get install nvidia-346
[reboot]
sudo nvidia-xconfig

```

Mine is connected to an LG TV, and I've found I've needed to make a change to /etc/X11/xorg.conf to display text in a readable font.  (Had the same problem with other NVIDIA connections to TVs).  If you have this problem, edit that file with the command
```
sudo nano /etc/X11/xorg.conf
```
and add this line to the "Monitor" section of that file:
```
Option "DPI" "96x96"
```
then reboot.

---

