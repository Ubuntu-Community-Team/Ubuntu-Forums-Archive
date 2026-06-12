---
title: "Howto: Tablet PC Summary"
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by jharbert on 2007-02-27
I've noticed, while trying to get my tablet to work, that there is no central place that covers general setup of Tablet PC's.  Information seems to be scattered around the forum/web.  My goal is to provide a central location for information on using Ubuntu with a tablet.  I have a Toshiba M205 running Ubuntu Feisty.

First and most important: the stylus.  If you're using Edgy or Dapper, simply follow the instructions on [this guide]("http://ubuntuforums.org/showthread.php?t=184542") and everything should work just fine.
For Feisty, I just needed to install wacom-tools to aid in setting up right click (the pen worked out of the box)!

To handle screen rotation (including automatic detection), stylus preferences (right click), express keys, etc., I combined a number of different commands from various places into a single script.  Save the script anywhere you want (I used the .gnome folder in home since it was out of the way) and add it to your startup programs list (System - Preferences - Session - Startup Programs)

```
#!/bin/sh
#Original Authors: Patrick Coke & Tim Pope
#Updated By: Joshua Harbert

while xset q >/dev/null 2>&1; do
sleep 2 # Polling Interval, 2 seconds

lid="`cat /proc/acpi/button/lid/LID/state|awk '{print $2}'`"

# Looks to see if what orientation the screen is in (Normal or Left)
# and puts the orientation into the $orientation variable
orientation="`/usr/bin/X11/xrandr --query | /bin/grep 'Current rotation' | /usr/bin/awk '{print $4}'`"
dpms="`xset q|grep 'Monitor is'|awk '{print $3}'`"
if [ "$orientation" = "normal" -a "$lid" = "closed" -a "$dpms" = "On" ]; then
# Rotates screen orientation to the right
/usr/bin/X11/xrandr --orientation right
# Rotates the stylus cordinate plane
xsetwacom set stylus rotate CW
#redefines the tablet quick keys
/usr/bin/X11/xmodmap -e "keycode 11 = KP_Left"
/usr/bin/X11/xmodmap -e "keycode 13 = KP_Up"
/usr/bin/X11/xmodmap -e "keycode 10 = KP_Right"
/usr/bin/X11/xmodmap -e "keycode 12 = KP_Down"
/usr/bin/X11/xmodmap -e "keycode 14 = KP_Enter"
#enable right click w/ hover
xsetwacom set stylus button2 3
xsetwacom set stylus TPCButton 0
#use a portrait photo for the wallpaper
#gconftool-2 -t str --set /desktop/gnome/background/picture_filename "path to portrait photo"
elif [ "$orientation" = "right" -a "$lid" = "open" ]; then
# Rotates the screen back to normal
/usr/bin/X11/xrandr --orientation normal
# Rotates the stylus cordinate plane to normal
xsetwacom set "stylus" Rotate 0
#Returns keys to normal
/usr/bin/X11/xmodmap -e "keycode 11 = 2 at"
/usr/bin/X11/xmodmap -e "keycode 13 = 4 dollar"
/usr/bin/X11/xmodmap -e "keycode 10 = 1 exclam"
/usr/bin/X11/xmodmap -e "keycode 12 = 3 numbersign"
/usr/bin/X11/xmodmap -e "keycode 14 = 5 percent"
#return wallpaper to standard
#gconftool-2 -t str --set /desktop/gnome/background/picture_filename "path to landscape photo"
fi
done
```

Where I got them from:
[Express Keys]("http://www.ubuntuforums.org/showthread.php?t=301146")
[Right Click]("http://www.ubuntuforums.org/showthread.php?t=221537")
[Rotation Script]("http://i-otto.blogspot.com/2006/09/toshiba-portg-m200-with-ubuntu.html")

Make sure you add
```
Option "RandRRotation" "On"
```
in the Nvidia section of your xorg.conf file to enable rotation.

Note: If the script does not return the keys to the correct keycode for your keyboard, [here]("http://www.in-ulm.de/~mascheck/X11/keysyms.txt") is a list of all the accepted keycodes.

If you want to enable the onscreen keyboard on login, follow the information on [this thread.]("http://ubuntuforums.org/showthread.php?p=1792228")

For a notepad application I would recommend [Xournal.]("http://www.ubuntuforums.org/showthread.php?t=113621")  It has many nice features such as using a PDF as a background for the page.

As a pen command input I found a nice little program called [OneStroke]("http://www.missirina.com/risujin/onestroke.php").

If you have any other tips or useful programs, post them and I'll add them to the list.

---

### Post by bwiewiora on 2007-03-03
This is a thread on getting the touchscreen for a Fujitsu 3400/3500 to work:

[http://ubuntuforums.org/showthread.php?t=159373]("http://http://ubuntuforums.org/showthread.php?t=159373")

I'll have to try the screen rotation to see how it'll work on my little tablet.

---

### Post by NumericalMe on 2007-03-03
Relatively new to Ubuntu myself.  Though I used the script for screen rotation and button configuration for some time, I noticed that it did not work in regular/laptop mode.  I've altered the script with some additional xmodmap commands that take into account the Meta_R modifier.  Since the keyboard itself has only one Meta key, I altered the Meta_R as the Mode_Switch.  If anyone has any reason why this is a bad thing, please let me know.  
```
#!/bin/sh
#Author: Tim Pope
#Edited: Leon van der Ree
#Edited again:  T. Deems (1 March 2007)

xmodmap -e "keycode 116 = Mode_switch"
xmodmap -e "keycode 10 = 1 exclam Down"
xmodmap -e "keycode 11 = 2 at Up"
xmodmap -e "keycode 12 = 3 numbersign Left"
xmodmap -e "keycode 13 = 4 dollar Right"
xmodmap -e "keycode 14 = 5 percent Return"
xmodmap -e "keycode 15 = 6 asciicircum Escape"


while xset q >/dev/null 2>&1; do
sleep 2 # Polling Interval, 2 seconds

lid="`cat /proc/acpi/button/lid/LID/state|awk '{print $2}'`"

# Looks to see if what orentation the screen is in (Normal or Left)
# and puts the orientation into the $orientation variable
orientation="`/usr/bin/X11/xrandr --query | /bin/grep 'Current rotation' | /usr/bin/awk '{print $4}'`"
dpms="`xset q|grep 'Monitor is'|awk '{print $3}'`"

if [ "$orientation" = "normal" -a "$lid" = "closed" -a "$dpms" = "On" ]; then
# Rotates screen orentation to the right
/usr/bin/X11/xrandr --orientation right
# Rotates the stylus cordinate plane
xsetwacom set "stylus" Rotate 1
xsetwacom set "eraser" Rotate 1
xsetwacom set "cursor" Rotate 1

xmodmap -e "keycode 116 = Mode_switch"
xmodmap -e "keycode 10 = 1 exclam Right"
xmodmap -e "keycode 11 = 2 at Left"
xmodmap -e "keycode 12 = 3 numbersign Down"
xmodmap -e "keycode 13 = 4 dollar Up"


elif [ "$orientation" = "right" -a "$lid" = "open" ]; then
# Rotates the screen back to normal
/usr/bin/X11/xrandr --orientation normal
# Rotates the stylus cordinate plane to normal
xsetwacom set "stylus" Rotate 0
xsetwacom set "eraser" Rotate 0
xsetwacom set "cursor" Rotate 0

xmodmap -e "keycode 10 = 1 exclam Down"
xmodmap -e "keycode 11 = 2 at Up"
xmodmap -e "keycode 12 = 3 numbersign Left"
xmodmap -e "keycode 13 = 4 dollar Right"
xmodmap -e "keycode 14 = 5 percent Return"

fi
done
```

This original script came from:
[Rotation Script]("http://i-otto.blogspot.com/2006/09/toshiba-portg-m200-with-ubuntu.html")

---

### Post by kic on 2007-03-03
Firstly, thank you OP for starting the thread. I'm trying to get Edgy running on a Toshiba m200 (basically an m205), but I'm running into some pretty annoying problems.

Primarily, rotation isn't working right now. I've tried using that script, Otto's original one, and the modified one posted on his blog, all to no avail. Running a manual command to query and then to change orientation results in this:

> xxxx@ubuntu:~$ /usr/bin/X11/xrandr --query
 SZ:    Pixels          Physical       Refresh
*0   1400 x 1050   ( 240mm x 180mm )  *60  
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none

xxxx@ubuntu:~$ /usr/bin/X11/xrandr --orientation right
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  155 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

Unfortunately, I've been out of the linux loop for quite a while, and I never was very good at hacking config files or figuring out how to fix things in general.

To fill in the blanks, I've installed the wacom-tools set as well as the nvidia drivers. However, regardless of running the nvidia drivers, rotation doesn't work. I've tried hacking the xorg.conf according to Otto's blog regarding the video driver section, and no change.

Tablet input does is functional (but I don't have pressure sensitivity working yet). The main thing I'm concerned with is getting the screen rotating functioning. Other problems like pressure and no sound (did I mention that?) can come later.

I'd love to get this working and would appreciate some assistance in getting rotation working.

Thanks in advance.

Edit to add: I'm not sure if this tablet is running the latest bios updates or if that even matters with any of these problems, and frankly, I'm not sure what it'd take to update it at this point. I've never had to deal with a laptop not having an optical drive, and it's making my life miserable. I'm about ready to crack and get a usb one or get rid of this notebook and get a newer one.

---

### Post by jharbert on 2007-03-03
Try adding 
```
Option "RandRRotation" "On"
```
to the nvidia driver section of your xorg.conf file, that's what I had to do.

---

### Post by kic on 2007-03-04
> **jharbert said:**
> Try adding 
```
Option "RandRRotation" "On"
```
to the nvidia driver section of your xorg.conf file, that's what I had to do.

Done that and it still doesn't rotate. Very frustrating. :(

---

### Post by jharbert on 2007-03-08
The only other thing I can think of is the default depth in the screen section of your xorg.conf file.  I have mine set to 24.  Did you restart Gnome?

---

### Post by jharbert on 2007-04-22
Updated for Feisty!

---

### Post by mrming on 2007-06-10
Just to add to this, I found that after upgrading from Edgy to Feisty pushing the pen tip always resulted in a right click rather than a click. To fix this use the following command:

xsetwacom set stylus button1 1

---

### Post by toontastic on 2007-10-30
I wonder if anyone can help. I've managed so far to get my stylus to work regardless of the direction my screen is in. I've also managed to get my screen to rotate by clicking a button on my desktop. I would however love to have my screen automatically rotate if I just turn it. I've tried using the script at the top but I've had no luck with it, it just doesn't seem to do anything. Any ideas what I'm doing wrong ?

---

### Post by ravi_s on 2007-10-30
I'm glad I ran into this thread!
I have a Fujitsu Lifebook P1510 Tablet and I really need to get the touchscreen working. This tablet uses a passive screen as opposed to the Toshiba and bigger Fujis and I dont think it's a Wacom. I'd be really grateful if any of you guys could help - I'm a total noob of 3 days Ubuntu experience so any help would be great.
Really like the idea of a Tablet PC Info repository!!

R.

---

### Post by toontastic on 2007-10-31
Not sure if this is any help to you:

[http://www.leog.net/fujp_forum/topic.asp?TOPIC_ID=9436](http://www.leog.net/fujp_forum/topic.asp?TOPIC_ID=9436)
[http://kavaro.com/mediawiki/index.php/P1510](http://kavaro.com/mediawiki/index.php/P1510)
[http://samengstrom.com/nxl/10301/p1510_external_display_page.en.html](http://samengstrom.com/nxl/10301/p1510_external_display_page.en.html)

The top one seems to include a driver which will let the touch screen work on your tablet.

---

### Post by toontastic on 2007-10-31
Seen as this thread seems to be all about tablets now, thought I would let people know about a bit of software I found yesterday. It includes a keyboard and handwriting recognition which seems to work great after the first bit of training. It's called cellwriter and you can download it's installer from [http://risujin.org/cellwriter/](http://risujin.org/cellwriter/) or [http://www.gnomefiles.org/app.php?soft_id=2127](http://www.gnomefiles.org/app.php?soft_id=2127) I got it from gnomefiles and the installer worked great.

---

### Post by thf on 2007-11-03
i had problems with the automatic rotation script above, and after some tinkering changed the line 
```
orientation="`/usr/bin/X11/xrandr --query | /bin/grep 'Current rotation' | /usr/bin/awk '{print $4}'`"
```
to the following:
```
orientation="`xrandr --verbose | /bin/grep '(normal left inverted right)' |awk '{print $5}'`"
```
and now it works

---

### Post by toontastic on 2007-11-05
> **thf said:**
> i had problems with the automatic rotation script above, and after some tinkering changed the line 
```
orientation="`/usr/bin/X11/xrandr --query | /bin/grep 'Current rotation' | /usr/bin/awk '{print $4}'`"
```
to the following:
```
orientation="`xrandr --verbose | /bin/grep '(normal left inverted right)' |awk '{print $5}'`"
```
and now it works

Thanks for that I'll give it a try later today.

---

### Post by toontastic on 2007-11-05
I'm so chuffed now, that worked great. I've added two more lines of code so that the nib and 3rd button work and now it works perfectly. I've added it to start up as well now.

I'm going to see if I can get it to load cellwriter automatically when it's in tablet mode now :D

---

