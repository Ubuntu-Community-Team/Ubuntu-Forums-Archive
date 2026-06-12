---
title: "run touchpad script on resume"
date: 2011-04-16
forum: Hardware
---

### Post by ne0genius on 2011-04-16
I have been using this startup script to activate multitouch on the my T410 trackpad. Works great. 

touchpad-quick.sh
```
#!/bin/bash
#
# list of synaptics device properties http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4
#
# Some useful commands :
#	xinput list
#	xinput list-props "SynPS/2 Synaptics TouchPad"
#	xinput test "SynPS/2 Synaptics TouchPad"
#	xinput test-xi2 "SynPS/2 Synaptics TouchPad"
#
# sleep 5
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 4
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 8         # Below width 1 finger touch, above width simulate 2 finger touch. - value=pad-pixels
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 0   # vertical scrolling, horizontal scrolling - values: 0=disable 1=enable
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 0 0 0       # vertical, horizontal, corner - values: 0=disable  1=enable
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 250 # stabilize 2 finger actions - value=pad-pixels
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Tap Action" 0 0 0 0 1 2 0   # pad corners rt rb lt lb tap fingers 1 2 3 (can't simulate more then 2 tap fingers AFAIK) - values: 0=disable 1=left 2=middle 3=right etc. (in FF 8=back 9=forward)
#xinput --set-button-map "SynPS/2 Synaptics TouchPad" 2 1 3 4 5 6 7 8 9                                       # swap left and middle click, gives you middle click on the left button and left click on tap. - values: lb, mb, rb, b4, b5, etc.
exit
```

Of course it becomes inactive when i resume from sleep. I did my research and created another script and placed it in /etc/pm/sleep.d

99touchpad-resume
```
#!/bin/sh

# enable multitouch touchpad on resume

case "$1" in
	thaw|resume)
		sh /home/alan/Scripts/touchpad-quick.sh	
		;;
esac
```

However it doesn't work. Can anyone see what i did wrong here? Thanks.

---

### Post by ErwinJunge on 2011-04-23
Hi, I've been looking at the same problem, and your script probably does run (mine did).

To check, put this after the comments in the script (touchpad-quick.sh):

echo 'script ran' > /home/alan/test

Suspend/resume and check if /home/alan/test exists. It did for me.

Now to solve your problem of the touchpad thing not working, I'm pretty sure it has to do with X not being initialized properly fast enough. That's what the sleep N line that you commented is for. It doesn't work for me either though, so I'll continue looking (maybe running the script after finishing the password prompt would be a solution?)

I'll post back here if I find anything.

---

### Post by ErwinJunge on 2011-04-26
Fixed it :)

The trick is shown in this post: [http://ubuntuforums.org/showpost.php?p=10220575&postcount=6]("http://ubuntuforums.org/showpost.php?p=10220575&postcount=6")

You need to change

```
sh /home/alan/Scripts/touchpad-quick.sh
```

into

```
DISPLAY=:0.0 su `who | grep tty7 | sed 's/\([a-z]*\).*/\1/'` -c 'sh /home/alan/Scripts/touchpad-quick.sh'
DISPLAY=:0.0 su `who | grep tty8 | sed 's/\([a-z]*\).*/\1/'` -c 'sh /home/alan/Scripts/touchpad-quick.sh'
```

Please mark this thread solved if this fixes your problem.

Greetings,

Erwin

PS The way this works is that it executes the xinput and synclient commands using the right display and the right user. Without the extra bit of magic, it's running as root, in an unknown display.

---

### Post by ne0genius on 2011-04-26
Yes! That worked. Everything seems to be working as it should. Touchpad resumes, I tried multiple times. Thanks for the help. My final resume script looked like this.

```
#!/bin/sh
case "$1" in
        thaw|resume)
	DISPLAY=:0.0 su `who | grep tty7 | sed 's/\([a-z]*\).*/\1/'` -c '/home/alan/Scripts/touchpad.sh'
        DISPLAY=:0.0 su `who | grep tty8 | sed 's/\([a-z]*\).*/\1/'` -c '/home/alan/Scripts/touchpad.sh'
        ;;
        *)
        ;;
        esac
exit $?
```

---

### Post by ne0genius on 2011-11-19
this method seems to break with Oneiric. I came across this thread post below where the user indicates with Oneiric the hotplug script should be used. Can anyone elaborate on the methods to make the trackpad resume work using the hotplug script. I unfortunately am not adept at bash scripts

possible hotplug method mentioned here
[http://askubuntu.com/questions/14714/making-touchpad-and-resume-password-changes-permanent](http://askubuntu.com/questions/14714/making-touchpad-and-resume-password-changes-permanent)

example use case
[http://who-t.blogspot.com/2011/03/custom-input-device-configuration-in.html](http://who-t.blogspot.com/2011/03/custom-input-device-configuration-in.html)

script template
[http://git.gnome.org/browse/gnome-settings-daemon/tree/plugins/common/input-device-example.sh](http://git.gnome.org/browse/gnome-settings-daemon/tree/plugins/common/input-device-example.sh)


Thanks!

---

### Post by ErwinJunge on 2011-11-20
I haven't tested it, but this is probably what you want:

[http://pastebin.com/BPEHxFtS](http://pastebin.com/BPEHxFtS)

This assumes you are still using the same script (/home/alan/Scripts/touchpad-quick.sh).

---

### Post by ne0genius on 2011-11-26
EDIT: 
Okay. Sorry for my ignorance. Apparently in 11.10 multitouch touchpad is supported for my hardware without any additional scripts or driver settings. Under the "Mouse and Touchpad" settings enabling multitouch fixes the issue. Thanks @ErwinJunge for the help. This was an issue in 11.04 that they have resolved. Thankful for the excellent developer support for Linux.

------------------

I tried the script and it probably is correct but I am not sure the method I outlined is even a working solution. 

To bring this back to the original issue I am providing the log output from pm-powersave.log. The script that originally worked is running but failing.

I remember reading somewhere that possibly the TTY address is incorrectly specified. The log output is below. 

```
Running hook /etc/pm/sleep.d/99-touchpad-resume resume suspend:
No protocol specified
Unable to connect to X server
```

output from tty
```
/dev/pts/0
```

---

