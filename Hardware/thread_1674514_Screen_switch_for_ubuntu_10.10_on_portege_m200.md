---
title: "Screen switch for ubuntu 10.10 on portege m200"
date: 2011-01-24
forum: Hardware
---

### Post by NoonienSoong97 on 2011-01-24
I finally got ubuntu desktop 10.10 on a new 320 gig drive for my Toshiba Portege m200. Found out that 10.10 already has the tablet support however the system doesn't allow to switch over to a second screen setting when the computer is in tablet mode. Is this due to nvidia card limitations on third party software? Or is there some software fix?

---

### Post by daibewklein on 2011-03-09
I just installed 10.10 on my m200 but the tablet doesn't seem to be working.  Did you have to any special configuration?

---

### Post by NoonienSoong97 on 2011-04-29
I started with installing ubuntu on a unformatted drive. When ubuntu started the install procedure I had to setup a swap section of 1 gig with the main drive. I had to make sure the OS was updated before a system restart.

---

### Post by NoonienSoong97 on 2011-07-06
Found out that nvidia now supports xrandr 1.2. I am trying out a program called arandr I have no visual issues while rotating back and forth. However the touchscreen function did not rotate with the screen. Is there a solution to this issue?

---

### Post by Favux on 2011-07-06
Hi NoonienSoong97,

I believe your Toshiba m200 uses a Wacom digitizer, correct?
> However the touchscreen function did not rotate with the screen. Is there a solution to this issue? 
Changing the screen orientation does not rotate the Wacom stylus and touch, if you have it.  You need a script to do that.  Have you put one in?

---

### Post by NoonienSoong97 on 2011-07-07
Found a script however it worked for awhile but now it is restricted. All I need to know is how to get the launcher to process restricted files.

---

### Post by NoonienSoong97 on 2011-07-07
The error I get is:

There was an error launching the application.
Details: Failed to execute child process "/home/nooniensoong97/bin/rotateleft.sh" (Permission denied)

---

### Post by Favux on 2011-07-07
Right click on rotateleft.sh in /home/nooniensoong97/bin.  In Properties click on the Permissions tab.  See if the box in front of "Allow executing as a program" is checked, if it isn't check it.  What does the script look like by the way?

---

### Post by NoonienSoong97 on 2011-07-07
It is the script you gave out for someone else. link is [http://ubuntuforums.org/showthread.php?t=1719514&highlight=screen+rotation+ubuntu+10.10&page=2](http://ubuntuforums.org/showthread.php?t=1719514&highlight=screen+rotation+ubuntu+10.10&page=2)

However I changed it around so I could have 4 different launchers for each rotation.

---

### Post by NoonienSoong97 on 2011-07-07
Still having problems with the function not rotation along with the screen rotation. here is one of the four scripts that I used.

#!/bin/sh 

# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "strip" out current orientation. 

rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')" 

# Using current screen orientation proceed to rotate screen and input tools. 

case "$rotation" in 
    normal) 
#    -rotate to inverted 
    xrandr -o inverted 
    xsetwacom set "Serial Wacom Tablet stylus" rotate HALF 
    xsetwacom set "Serial Wacom Tablet eraser" rotate HALF 
    ;; 
    left) 
#    -rotate to inverted 
    xrandr -o inverted 
    xsetwacom set "Serial Wacom Tablet stylus" rotate HALF 
    xsetwacom set "Serial Wacom Tablet eraser" rotate HALF 
    ;; 
    inverted) 
#    -rotate to inverted 
    xrandr -o inverted 
    xsetwacom set "Serial Wacom Tablet stylus" rotate HALF 
    xsetwacom set "Serial Wacom Tablet eraser" rotate HALF 
    ;; 
    right) 
#    -rotate to inverted 
    xrandr -o inverted 
    xsetwacom set "Serial Wacom Tablet stylus" rotate HALF 
    xsetwacom set "Serial Wacom Tablet eraser" rotate HALF 
    ;; 
esac

---

### Post by Favux on 2011-07-07
Please post both the output of *xinput list* and *xsetwacom list* in a terminal.

And your stylus has an eraser, but you do not have touch, correct?

---

### Post by NoonienSoong97 on 2011-07-07
here is the list:

nooniensoong97@nooniensoong97-PORTEGE-M200:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                              	id=10	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft Notebook Receiver v2.0	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
    &#8627; Toshiba input device                    	id=14	[slave  keyboard (3)]

Yea the Toshiba that I have doesn't have the touch screen only the magnetic pen.

---

### Post by NoonienSoong97 on 2011-07-07
Since inverted is a rotation of half what is the rotation for left and right?

---

### Post by Favux on 2011-07-07
So was there output from *xsetwacom list*?  From your xinput list output the xsetwacom commands are correct with "Serial Wacom Tablet stylus" and "Serial Wacom Tablet eraser".

left = ccw
right = cw

What video chipset do you have?:
```
lspci | grep VGA
```

---

### Post by NoonienSoong97 on 2011-07-07
nooniensoong97@nooniensoong97-PORTEGE-M200:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 32M/64M] (rev a1)

---

### Post by NoonienSoong97 on 2011-07-07
nooniensoong97@nooniensoong97-PORTEGE-M200:~$ xsetwacom list
Serial Wacom Tablet eraser ERASER    
Serial Wacom Tablet stylus STYLUS

---

### Post by NoonienSoong97 on 2011-07-07
Everything is working now. I have launchers setup for left, right, inverted, and none rotation. I might expand on it later with an app., but for now the launchers will do fine.

---

### Post by Favux on 2011-07-07
Great!  Nice work.  :)


Your *xsetwacom list* is good so you are on the wacom drivers.  For more ideas the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1") might be helpful.

---

### Post by NoonienSoong97 on 2011-07-07
Here is the final scripting for screen and device rotations for the Toshiba Portege M200:

#!/bin/sh 

# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "strip" out current orientation. 

rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')" 

# Using current screen orientation proceed to rotate screen and input tools. 

case "$rotation" in 
    normal) 
#    -rotate to left 
    xrandr -o left 
    xinput set "Microsoft Microsoft Notebook Receiver v2.0" rotate CCW 
    xinput set "AlpsPS/2 ALPS GlidePoint" rotate CCW 
    xsetwacom set "Serial Wacom Tablet stylus" rotate CCW 
    xsetwacom set "Serial Wacom Tablet eraser" rotate CCW 
    ;; 
    left) 
#    -rotate to left 
    xrandr -o left 
    xinput set "Microsoft Microsoft Notebook Receiver v2.0" rotate CCW 
    xinput set "AlpsPS/2 ALPS GlidePoint" rotate CCW 
    xsetwacom set "Serial Wacom Tablet stylus" rotate CCW 
    xsetwacom set "Serial Wacom Tablet eraser" rotate CCW 
    ;; 
    inverted) 
#    -rotate to left 
    xrandr -o left 
    xinput set "Microsoft Microsoft Notebook Receiver v2.0" rotate CCW 
    xinput set "AlpsPS/2 ALPS GlidePoint" rotate CCW 
    xsetwacom set "Serial Wacom Tablet stylus" rotate CCW 
    xsetwacom set "Serial Wacom Tablet eraser" rotate CCW 
    ;; 
    right) 
#    -rotate to left 
    xrandr -o left 
    xinput set "Microsoft Microsoft Notebook Receiver v2.0" rotate CCW 
    xinput set "AlpsPS/2 ALPS GlidePoint" rotate CCW 
    xsetwacom set "Serial Wacom Tablet stylus" rotate CCW 
    xsetwacom set "Serial Wacom Tablet eraser" rotate CCW 
    ;; 
esac

---

### Post by Favux on 2011-07-07
Hi NoonienSoong97,

Not quite sure I understand what you are doing.  For whichever of the four screen orientations the screen is in you always want it to go to left handed Portrait orientation?

---

### Post by NoonienSoong97 on 2011-07-07
well this is just the script to switch to left hand rotation no matter which orientation your in. I haven't shown the other three scripts because the line of code for each are the same with different values. However I still have some tweaks to work out. I have to have the tablet in laptop mode for the scripts to work. If I am in tablet mode the scripts do not work.

---

### Post by Favux on 2011-07-07
Right, see the method 1 scripts on the Rotation HOW TO to do a script to rotate through 360 degrees or to rotate right or left and back.  You're almost there.

---

