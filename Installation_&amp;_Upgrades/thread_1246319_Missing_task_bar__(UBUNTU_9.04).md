---
title: "Missing task bar  (UBUNTU 9.04)"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by yzfvie on 2009-08-21
I am new to UBUNTU and wanted to try it out. I installed UBUNTU a few days ago and started with 8.10 and upgraded to 9.04. I started installing a couple of applications.

After trying to install these applications, I started getting error messages that some application components were not running properly(can't remember anymore). I turned off the computer for the day and when I rebooted the next day, all I had was the desktop screen without the taskbars. The only thing I can do is Cntl-alt-del to turn off the computer and the right mouse button opens a box with options (Create folder,launcher or document) and (Change desktop background)

Is there anything I can do to restore my taskbar short of re-installing UBUNTU?

Thanks.

---

### Post by wojox on 2009-08-21
This worked for me in 8.10 haven't had to try it in 9.04 yet:

Alt+F2

type gnome-terminal in box click run

In the terminal

```
gconftool-2 --shutdown
```

```
gconftool --recursive-unset /apps/panel
```

```
rm -rf ~/.gconf/apps/panel
```

```
pkill gnome-panel
```

---

### Post by yzfvie on 2009-08-21
I have no function control with my keyboard except for Cntrl-Alt-Del

---

### Post by Unethical on 2009-08-21
This may not be a full fix, but maybe it can be a lead to you, or someone else. 

Right click the desktop and go to change background > add. In the drop menu where "Images" is selected, press all files. From here you can find files and drag them to your desktop. 

Maybe try getting into the terminal from there...?

---

### Post by jkarcz on 2009-08-21
Had this happened to me too after an upgrade.  Something must have got trashed in the gnome settings.  I finally just renamed/deleted the .gconf, gconfd, .gnome2, and .gnome2_private, then log out and log in.  You'll loose any customized settings, but it works.

---

### Post by yzfvie on 2009-08-21
I found out that to get a terminal screen, I created a folder and opened it. I then went to /usr/bin and opened gnome-terminal executable file. 

I tried commands as per WOJOX post and had no results. After the 4 commands lines, nothing happened.

Any other ideas?
Thanks for the quick suggestions.

---

### Post by yzfvie on 2009-08-21
Thanks jkarcz for your input.
I will try this tomorrow.

---

### Post by startrekker on 2009-08-22
I had a similar issue with my Eee900 after an upgrade the gnome-panel and window manager stopped loading at launch.  Alt-F2 did not open the run launcher for me. I had to right-click (option click for those using a different mouse configuration) and create a launcher for the gnome-panel. This works to get the panel up. Then I launch metacity with the terminal. It does not startup automatically, but I will try the instructions in the post from Wojox.

---

### Post by startrekker on 2009-08-22
> **startrekker said:**
> I had a similar issue with my Eee900 after an upgrade the gnome-panel and window manager stopped loading at launch.  Alt-F2 did not open the run launcher for me. I had to right-click (option click for those using a different mouse configuration) and create a launcher for the gnome-panel. This works to get the panel up. Then I launch metacity with the terminal. It does not startup automatically, but I will try the instructions in the post from Wojox.

:( that did not fix my issue.

---

### Post by yzfvie on 2009-08-23
Sorry to have wasted everyone's time. After trying one thing after another, I decided I had spent too much time on the problem and did a fresh installed of 9.04. I did not really have anything critical on the system anyway.

Thanks.

---

