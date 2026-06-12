---
title: "HOW TO: Change output/resolution on eeePC in one click"
date: 2008-05-24
forum: Hardware
---

### Post by komputes on 2008-05-24
I got sick of having to authenticate myself every time I wanted to change the resolution, as well as having to reboot so that Ubuntu sees that VGA was available, so I made the following two xrandr scripts to switch between monitors with **one click**.

1) Copy the following lines into your text editor and give them the following filenames

Filename: mon_lcd.sh
```
#!/bin/bash
xrandr --output LVDS --on
xrandr --output LVDS --mode 800x480
xrandr --output VGA --off
```
*Note: If you run a eeePC 900 please send me the max resolution for LVDS by running the "xrandr" command.*

Filename: mon_vga.sh
```
#!/bin/bash
xrandr --output VGA --on
xrandr --output VGA --mode 1280x1024
xrandr --output LVDS --off
```*Note: The "xrandr" command spits out valid resolutions, which can be used. You can run this command and find out what resolution is good for you, then simply replace the "1280x1024"*

2) Save both in your home directory and bring up a Terminal in which you will type the following to make your scripts executable.
```

chmod +x mon_*.sh
```3) If you do not want them kept in the root of your home directory move the script to where it will be stored. in my case it is in a directory called "eee".

```
cp mon_*.sh eee/
```4) Navigate to /home/_your_user_name_here_/eee and drag the two files to the panel (the bar with the clock). Then you can name them VGA and LCD and give them an icon, I used the gnome-display-properties.svg icon for both.

Now whenever you need to switch your resolution/output you can, in one click!

:guitar:

---

### Post by jordanius on 2008-07-09
This worked a treat, thanks so much!

---

### Post by Moey on 2008-07-09
I wish i had one of thoes little mini lappys......

---

