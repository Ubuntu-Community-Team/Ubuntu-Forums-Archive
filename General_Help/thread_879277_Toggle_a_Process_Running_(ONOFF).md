---
title: "Toggle a Process Running (ON/OFF)"
date: 2008-08-03
forum: General Help
---

### Post by ernz on 2008-08-03
Hi all. Not asking a question, just leaving a quick note on a little problem I had and what my solution was. As usual, this tutorial is designed to be very easy to follow for newbs like myself. This tutorial will assume that you already have Compiz-Fusion up and running.

Problem:
With compiz-fusion on a zoomed view or some games on full screen views, the mouse cursor obscures your view. We want to hide it temporarily.

Solution: 
Install unclutter
Create toggle script
Assign Compiz-fusion hot key

Method:
Install unclutter using the terminal command...
```
sudo apt-get install unclutter
```

Create toggle script...
Using gedit, or whatever editor you want create a new file and paste this into it...
```
#!/bin/sh
#Ernz's Toggle Script
#Toggles a process (ON/OFF)

#Name for process
PROCESS='unclutter'
#Actual command to run
FULLCOMMAND='unclutter -idle 1'

if ps ax | grep -v grep | grep $PROCESS > /dev/null
then
    #Killing process
    kill $(pgrep $PROCESS) &
    echo "$PROCESS was running. I killed it. MuHAhahAHH!"
else
    #Starting process
    $FULLCOMMAND &
    echo "$PROCESS was not running. I just started it for you. You're welcome!"
fi

exit
```

Save the file as '.togglecursor.sh' and close the editor. (The '.' prefix makes the file hidden. In the nautilus file manager, press CTRL + H to toggle hidden files visibilty)

Now navigate to the file, right click on it, select Properties and in the Permissions tab, check the checkbox to make the file executable. 

All you have to do now is create a hot key. You will need CompizConfig Settings Manager for this one. If it's not already installed, just type into the terminal...
```
sudo apt-get install ccsm
```

...and then run ccsm or go to System > Preferences > Advanced Desktop Effects Settings.

In the CompizConfig Settings Manager, go to General Options > Commands > Expand Commands. On the next available command line enter...
```
sh ~/.togglecursor.sh
```

Now collapse Commands, and expand Key Bindings. In the corresponding command, Click the 'Disabled' button. Enable and Grab Key Combination. At this point you can assign your own combination to hide/unhide the cursor. I found that CTRL + BACKSPACE feels quite natural and it's easy to remember. Of course, if this combo is assigned to anything else on your system already, you may need to choose another to avoid a conflict.

That's it. You can now close down the CompizConfig Settings Manager and you are 'good-to-go'! Just hit CTRL + BACKSPACE to toggle cursor visibility. 

Note that the "FULLCOMMAND='unclutter -idle 1'" line in the script can be customised. The idle time in this case is 1000ms. This means after you stop moving your mouse there will be a 1 second delay before the cursor disappears. Moving your mouse again will show the cursor briefly. Check out the unclutter man page for more info...
```
man unclutter
```


Hope this helps :)

---

