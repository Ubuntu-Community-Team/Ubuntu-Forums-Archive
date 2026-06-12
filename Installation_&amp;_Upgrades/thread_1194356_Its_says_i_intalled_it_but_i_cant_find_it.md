---
title: "Its says i intalled it but i cant find it?"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by caffeinatedcupcake on 2009-06-22
okee, so earlier i installed Playonlinux,i have ubuntu 9.04... and i went to add and remove programs, it wasnt there, so then i went to synaptic package manager and looked up "PlayonLinux" it showed up but it said it was already installed,so then i went to where Playonlinux should be located, the games tab of the applications drop down menu. it wasnt there....any ideas?

---

### Post by aesis05401 on 2009-06-22
How did you install it?

---

### Post by caffeinatedcupcake on 2009-06-22
> **aesis05401 said:**
> How did you install it?
i first downloaded the deb file, then i went to the terminal and pasted the respitory command in which was:sudo wget [http://deb.playonlinux.com/playonlinux_jaunty.list](http://deb.playonlinux.com/playonlinux_jaunty.list) -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux

---

### Post by aesis05401 on 2009-06-22
Ok, unless there were errors during install all we need to do is create a menu launcher for the program - remember that .deb files are compatable with, but not configured for Ubuntu.

System/Preferences/Main Menu

*Note - There appears to be an issue with window focus on 9.04, so the Main Menu window opens under other windows, as do all the action dialogs opened from within Main Menu - so the first thing to do is move the Main Menu window over to the side of the screen so we can see new child windows. 

From within the Main Menu window select the Menu you want to add playonlinux.  With the proper menu highlighted click 'New Item.'  The rest of the process is identical to creating a desktop launcher.  You can just browse to the location of playonlinux executable, or change the launcher type to 'Application in Terminal' and provide a command line launch argument.

If you are having trouble finding the actual files simply use : 
```

sudo find / -name 'playonlinux' 

```

---

### Post by caffeinatedcupcake on 2009-06-22
> **aesis05401 said:**
> Ok, unless there were errors during install all we need to do is create a menu launcher for the program - remember that .deb files are compatable with, but not configured for Ubuntu.

System/Preferences/Main Menu

*Note - There appears to be an issue with window focus on 9.04, so the Main Menu window opens under other windows, as do all the action dialogs opened from within Main Menu - so the first thing to do is move the Main Menu window over to the side of the screen so we can see new child windows. 

From within the Main Menu window select the Menu you want to add playonlinux.  With the proper menu highlighted click 'New Item.'  The rest of the process is identical to creating a desktop launcher.  You can just browse to the location of playonlinux executable, or change the launcher type to 'Application in Terminal' and provide a command line launch argument.

If you are having trouble finding the actual files simply use : 
```

sudo find / -name 'playonlinux' 

```
omgosh! youre a genius! THANK YOU SO MUCH! IVE BEEN TRYING TO FIGURE THAT OUT FOR 5 DAYS! :D *hugs*

---

### Post by aesis05401 on 2009-06-22
;)

Happy trails.

---

