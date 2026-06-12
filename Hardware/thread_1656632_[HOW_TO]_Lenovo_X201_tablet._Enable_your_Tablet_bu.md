---
title: "[HOW TO] Lenovo X201 tablet. Enable your Tablet buttons!"
date: 2010-12-31
forum: Hardware
---

### Post by linuxd00 on 2010-12-31
For the sake of completenes i reedited this post:
 
I present you the scripts i use to make my X201 a nicer place to live. I got these on the net and modified them to work on the 201 or by the awesome help from fellow users in this forum. Enjoy!






**_[SIZE="4"]setX201tKeys.sh [/SIZE]_**

i present you a script to enable your tablet buttons( [Based on this]("http://www.thinkwiki.org/wiki/Tablet_Hardware_Buttons")).
Run this script to enable your Tablet buttons on the Lenovo X201 Tablet.
even better set it to autostart with the system (System->Preferences->Startup Applications)

On my system (Maverick 64) somehow the usage of setkeycodes sets the keycode by 8 values above the intended keycode:
For example: you write "sudo setkeycodes 0x67 148" then the keycode will be actually set to "156"... dunno why. So if in your system its different (test with the xev command) you can change it accordingly below

i mapped the toolbarbutton to XF86LaunchB, because i set it to toggle the unhide option for the ubuntu panel using a script see below.

you can actually map to the existing button XF86RotateWindows, which rotates the screen out of the box, but the pen and finger input will not be "rotated"... Instead i use a custom script i found on the net. Thus you have the "unlabeled" (XF86Launch1) and the padlock (XF86Launch2) to set to something you like (on System->Preferences->Keyboard Shortcuts).
for writing recognition im using cellwriter (awesome handwriting recognition program for any language ever)




**_[SIZE="4"]hideUnhidePanel.sh  [/SIZE]_**

To maximize my viewing area i hide the task bar/task panel. In order to show it you'd normally hover the mouse to the lower part of the screen (or the side where its hidden). in tablet mode i just press the toolbox button instead:

I mapped the Toolboxbutton to hide and unhide the panel... since the panel is hidden anyway i made it also bigger so its touch-friendly (right click on it and set the size to 45 pixels).

so when im in tablet mode and need to switch programs or access the program menu i unhide the panel, click on a program on the task bar and hit the button to rehide it.. nifty!

 (on System->Preferences->Keyboard Shortcuts) 






**_[SIZE="4"]rotateX201.sh  [/SIZE]_**

This rotates the display. Its needed since the built in rotation does not rotate the touch and pen drivers.. a mess i tell you. This script will rotate the display clockwise everytime you hit it...
I made it back then when computers were steam powered and internet was based on pidgeon-over-IP... there was no option. Nowadays you can and probably should use the uber excellent program: Magick Rotation from Favux. it can rotate your display automatically when you switch to tablet mode!! it also lets you deactivate  touch and much more.. to rotate use the provided file "xrotate.py" in the install dir.

[https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

It explicitly supports the Lenovo X201!!!







**_[SIZE="4"]mountTruecryptFavorites.sh [/SIZE]_**

This script i use to mount my private data on startup. just put it to your autostarts (Preferences->Startup Applications). The problem is that it will always ask you for your admin pass and THEN for your volume pass.. the solution is ( [based on this]("http://judsonsnotes.com/notes/index.php?option=com_content&view=article&id=65:truecrypt-and-sudoers&catid=37:tech-notes&Itemid=59")):
basically you have to add an exception that allows to run truecrypt without password. So add this line to /etc/sudoers using the command "sudo visudo":
```

username ALL=(root) NOPASSWD:/usr/bin/truecrypt
```
replacing "username" with... well your username, then you can place the truecrypt mount command in your autostart options











**_[SIZE="4"]Setting up the trackpoint[/SIZE]_**

To set up the trackpoint speed and sensitivity. you need to run these lines in super user mode (run this command in a terminal: "sudo su"), a simple sudo wont work.
> 
echo -n 1 > /sys/devices/platform/i8042/serio1/serio2/press_to_select 
echo -n 125 > /sys/devices/platform/i8042/serio1/serio2/speed 
echo -n 254 > /sys/devices/platform/i8042/serio1/serio2/sensitivity 


yet putting this at system start doesnt seem to work always..

its kind of broken. search the forum for "i8042 serio1 press_to_select": it seems to be a bug where the files that the driver use(the serio1, serio2 bit) are created with different names at every boot... so the script wouldnt quite work.. i got frustrated and actually didnt bother looking further into it. i put the needed lines in the script for anybody wanting to look for a solution. If i  find any ill update the post once more.




have fun!

---

### Post by espen77 on 2011-01-17
Hi, thank you for the scripts,
I use the following script mapped to the portrait/landscape button in keyboard shortcutts. Also working on a little python app to show a customizable menu when i press the button under the padlock.

```
:~$ cat /usr/bin/tablet.sh 
#!/bin/bash

if [ `xsetwacom --get "Serial Wacom Tablet" Rotate` = "NONE" ]; then
xsetwacom --set "Serial Wacom Tablet" Rotate CW
xrandr -o right
MyScriptStylus &
else
xsetwacom --set "Serial Wacom Tablet" Rotate NONE
xrandr -o normal
killall MyScriptStylus
fi

```

MyScriptStylus is just a non-free handwriting rec, it is not needed for the script to work.

---

### Post by miobrad on 2011-02-06
hi linuxd00
thank you very much for your scripts - it works well for me to start with!
i am new to this and have a question - i get this messages:

Cannot find device 'Serial Wacom Tablet'.
Cannot find device 'Serial Wacom Tablet touch'.

but no error for "Serial Wacom Tablet eraser". i have the x201i without multitouch - so only the pen works. still, it is strange that only the eraser works. how do i test which device names there are? is the eraser to work enough?

the other question that i have - i am using magick rotation (thanks guys!!) and wonder about integration of your solution with that of magick rotation. 

at the moment i have magick rotation set to invert the screen. but then the setting of your script does not rotate it at all. ie - it only works when i am in "normal" mode.

do i make this clear? i tried changing to "Rotate CCW" but that also did not work when in tablet mode..

thanks a lot!

---

### Post by Favux on 2011-02-06
Hi miobrad,

To find your "device names" enter in a terminal:
```
xinput list
```
and check the output.  My guess is your stylus is named "Serial Wacom Tablet stylus".  If so use that, or whatever the correct name for stylus is, in the script.  Do you mean your X201t does not have touch?  If so remove the touch lines from the script.

By the way, instead of the rotation script, you could use Magick Rotation's rotation engine called xrotate.py.  Instructions are in the Magick-README.txt.

---

### Post by miobrad on 2011-02-06
thanks a lot - i got it to work with xrotate.py - great!

---

### Post by linuxd00 on 2011-02-07
hey miobrad... for the sake of completness i updated my posting with all the little scripts i use on my x201.

including a much needed, somewhat working script to set up the speed and sensitivity on the trackpoint... its inside "setX201tKeys.sh"


i dont know why you get that error.. i get it too but its ok.. works anyway.

i also updated the rotation script: it doesnt rotate normal/right back and fort but goes full circle :)

but yes you should probably use Magick rotation instead... it rocks! and i use it myself now.

 hehe..

---

### Post by miobrad on 2011-02-08
:)

i would like to map one of the buttons to the ALT-TAB behaviour, ie, looping through the open applications. it is however not possible (or is it?) to map multiple shortcuts to the same action. and i do not want to loose that keyboard short! i have now decided to map "initiate window picker" to one tablet buttons, does a similar job..

---

### Post by linuxd00 on 2011-02-08
hey, did exactly the same.

i mapped the circular arrow tablet button to "window picker" and the padlock to open a new console (since its a task i do often).

however i find myseld using the taskbar hide/unhide more often than window picker: it gives me access to tray icons (such as cellwriter if needed) and to the program menu.

---

### Post by mikio on 2011-02-09
ha, i just saw your hideUnhidePanel.sh. it seems i have extactly the same settings. i have both panels hidden, set to show with 1px. 

i did not think of unhiding with a button, though i did find it hard to access them with the pen - until i found that when i go into the black area beyond the edge of the screen, then the pointer will actually go to the very edge and still react - ie: it will unhide the panel quite naturally.

that is in contrast to just trying to go to that 1px at the very edge, which had the effect of making the panel flicker (due to not being able to precisely stay on the 1px..). 

i have only done this for one day though - i might come back to your script if it turns out not so good in the longer run..

one more thing: it seems, it is not enough to add the script in "startup applications" - it needs super user rights - isn't that so? so what would you suggest? also, you might want to point that out in your tutorial.. correct me if i am wrong!!

---

### Post by linuxd00 on 2011-02-10
hey mikio,

actually i have a different display case than you..  i saw at the store that some x201 have a completely flat display (iphone like) mine has a display with a frame aroung it like this

[http://www.dascus.de/shop/images/x201t.jpg](http://www.dascus.de/shop/images/x201t.jpg)

anyway... the hide unhide is more handy when you use your x201 with fingers only. which i do more often than not.

i am not sure what you mean with superuser rights. Hideunhide does not need it. you use it from "shortcuts" not autostart

or do you mean setting mouse speed? it is in set 201keys... 

yeah, that is right it need super user rights... but its kind of broken anyway. search the forum for "i8042 serio1 press_to_select": it seems to be a bug where the files that the driver use are created with different names at every boot... so the script wouldnt quite work.. i got frustrated and actually didnt bother looking further into it. i put the needed lines in the script for anybody wanting to look for a solution :) ill update the post once more.

---

### Post by miobrad on 2011-03-02
magick rotation stopped working - for you too?

here is what happens when i run it:

./magick-rotation 
Traceback (most recent call last):
  File "./magick-rotation", line 236, in <module>
    magick = engine()
  File "./magick-rotation", line 121, in __init__
    self.toggle_touch()
  File "./magick-rotation", line 143, in toggle_touch
    self.touch_on.show()
glib.GError: Unable to connect to server


?? what is happening. i am not sure when it happened. yesterday my computer did a system upgrade. i have since restarted tonight - it stopped working. in between i also tried to install xournal from scratch. i thought that maybe the installation of dependent packages might have messed things up. i removed them again, but it still does not work - i am not sure what the cause of the problem is..

any ideas?
miki

---

### Post by Ayuthia on 2011-03-04
> **miobrad said:**
> magick rotation stopped working - for you too?

here is what happens when i run it:

./magick-rotation 
Traceback (most recent call last):
  File "./magick-rotation", line 236, in <module>
    magick = engine()
  File "./magick-rotation", line 121, in __init__
    self.toggle_touch()
  File "./magick-rotation", line 143, in toggle_touch
    self.touch_on.show()
glib.GError: Unable to connect to server


?? what is happening. i am not sure when it happened. yesterday my computer did a system upgrade. i have since restarted tonight - it stopped working. in between i also tried to install xournal from scratch. i thought that maybe the installation of dependent packages might have messed things up. i removed them again, but it still does not work - i am not sure what the cause of the problem is..

any ideas?
miki

Can you post the results of:
```

dpkg -l libc6
dpkg -l gcc

```
You might need to use sudo to make the commands work.  I just updated my Maverick partition and it seems to still be working so I am trying to figure out what packages are different between our systems.  Are you using the backport repositories?

---

### Post by linuxd00 on 2011-03-06
hi,

yeah it seems the latest wacom driver update (2 weeks ago) broke rotation.

i posted about it some days ago on this thread:

[http://ubuntuforums.org/showthread.php?p=10507868#post10507868](http://ubuntuforums.org/showthread.php?p=10507868#post10507868)

i havent tested it yet but it seems the latest wacom driver git has it fixed(see favux response)... so either wait until it hit the repository or git update it.

---

### Post by miobrad on 2011-03-07
hi,
thanks for the reply, here my dpkg -l results:

ii  libc6 2.12.1-0ubuntu10.2 Embedded GNU C Library: Shared libraries
ii  gcc 4:4.4.4-1ubuntu2 The GNU C compiler


thanks!! (i'll be reading your posts linuxd00 - thanks also!)

---

### Post by Ayuthia on 2011-03-08
> **miobrad said:**
> magick rotation stopped working - for you too?

here is what happens when i run it:

./magick-rotation 
Traceback (most recent call last):
  File "./magick-rotation", line 236, in <module>
    magick = engine()
  File "./magick-rotation", line 121, in __init__
    self.toggle_touch()
  File "./magick-rotation", line 143, in toggle_touch
    self.touch_on.show()
glib.GError: Unable to connect to server


?? what is happening. i am not sure when it happened. yesterday my computer did a system upgrade. i have since restarted tonight - it stopped working. in between i also tried to install xournal from scratch. i thought that maybe the installation of dependent packages might have messed things up. i removed them again, but it still does not work - i am not sure what the cause of the problem is..

any ideas?
miki

I have been searching for the reason why this is happening.  Are you able to get into the setup?  If so, can you turn off the notification (Advanced Setup->Allow Notification)?  I am not positive yet, but it might have something to do with libnotify or pynotify.

---

### Post by miobrad on 2011-03-08
no, i can not go into the setup. there is no icon in the gnome panel..

---

### Post by Ayuthia on 2011-03-08
> **miobrad said:**
> no, i can not go into the setup. there is no icon in the gnome panel..

Ok.  Can you try and edit your .magick-rotation.xml file?  Look for the entry:
```

    <option name="isnotify">
        <value>"True"</value>
    </option>

```
and change it to:
```

    <option name="isnotify">
        <value>"False"</value>
    </option>

```

Then try starting it up again.

---

### Post by miobrad on 2011-03-09
yes, that was it - it works now!

a note to anyone else reading: 

.magick-rotation.xml is in your home directory..

also, after changing the value all i had todo is run ./magick-rotation for it to work again. i did however restart my system to see if it will still start as it should.. - all good!

thanks again - this is great!!

---

### Post by Ayuthia on 2011-03-09
> **miobrad said:**
> yes, that was it - it works now!

a note to anyone else reading: 

.magick-rotation.xml is in your home directory..

also, after changing the value all i had todo is run ./magick-rotation for it to work again. i did however restart my system to see if it will still start as it should.. - all good!

thanks again - this is great!!

Thanks for clarifying the location of the .magick-rotation.xml file.  I will see if I can figure out how to solve the libnotify/python-notify issue.

---

### Post by miobrad on 2011-03-10
no - thanks you, again! ;)

---

