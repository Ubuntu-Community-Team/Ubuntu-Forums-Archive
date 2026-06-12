---
title: "Tablet PC screen rotation problem"
date: 2011-03-08
forum: Hardware
---

### Post by xdominex on 2011-03-08
Hello!
I just have a minor problem to solve. I have these scripts obtained from here:
[https://wiki.edubuntu.org/HP%20TouchSmart%20tm2]("https://wiki.edubuntu.org/HP%20TouchSmart%20tm2")

The scripts I am using from there are the rotate-display script and the auto-rotate script. Both of these work wonderfully except for one small problem; the stylus input is still backwards for the "left" and "right" orientations. It works fine in the "half" and "none" rotations. I figure there is probably a very simple fix for this but am not sure what it is.

Also, if someone who knows some basic command-writing would like to right me a simple command that does the operations specified below, that would be fantastic! Thank you so much in advance for your help!

If ROTATE="NONE", execute "rotate-display left"
If ROTATE="CCW", execute "rotate-display half"
If ROTATE="HALF", execute "rotate-display right"
If ROTATE="CW", execute "rotate-display none"

My purpose for this command is to assign it to my "rotate screen" button on the side of my monitor.

---

### Post by Favux on 2011-03-08
Hi xdominex,

While those look technically correct from my perspective they are needlessly complex.  All you need are xsetwacom commands.  I don't know why xinput commands are needed, you're trying to set up a device on the wacom drivers, not evdev drivers.  It sounds like cw and ccw are reversed which is a bug I've encountered before.

A basic review is the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  That has the scripts you need including the automatic one and the Magick Rotation applet.

Also see the linux wacom project mediawiki:
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Rotation](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Rotation)
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_PC_Setup](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_PC_Setup)

---

### Post by xdominex on 2011-03-09
Well, (now) these two scripts accomplish everything I want except for doing the 90-180-270-360 rotation that I would like (I switched "CW" with "CCW" like you pointed out, so the backwards input is solved); the only problem is that these processes only execute in command-line. I set shortcuts for rotating the display using xbindkeys using commands like this:
gnome-terminal -x bash -c "rotate-display none"

However, I would like to be able to execute these commands with a simple "rotate-display none" (or similar command according to how I want the screen orientated). Also, it would be nice if auto-rotate would be able to start and run in the background instead of requiring me to have it open in terminal all of the time. Everything I've tried so far does not work, yet the script runs perfectly and, to the naked eye, instantly when running in terminal. Do you have any suggestions for this?

---

### Post by Favux on 2011-03-09
No xsetwacom rotates the input tool(s).  You use xrandr to rotate the display, as in:
```

#    -rotate to the left 
    xrandr -o left 
    xsetwacom set stylus rotate CCW 
    xsetwacom set touch rotate CCW 
    xsetwacom set eraser rotate CCW 

```
Excerpt from method 1 script.

---

### Post by xdominex on 2011-03-09
Ok, I removed the first three lines from the rotate-display script (pasting the contents into a new unsaved text document during testing), and everything worked perfectly fine. Good call on that one. Now, I have the lone problem of being able to make these scripts run without opening a terminal and running them there. Do you know how I can do this? I don't know how much you know about Upstart scripts, but I would like to write one for the auto-rotate script.

About the scripts I am using vs the scripts you have listed in your "Rotation HOW TO.." The scripts I am using use simple inputs for manual rotation directly to the orientation I want (e.g. "rotate-display right" rotates the top of the display to what is normally the right side of the screen. The person who wrote this script then uses it as a shortcut for his rather-short script that automatically rotates the screen when the screen is docked. Both scripts are written with admirable efficiency and flexibility (convenience for use in other scripts) with the exception of, as you pointed out, the "xinput" lines. In fact, I could adapt the code you listed in "Method 1" to have simple command outputs of "rotate-display none," "rotate-display left," etc. instead of individual "xsetwacom" and "xrandr" command outputs for each "current xrandr status." However, while this would make the coding much cleaner and briefer, I DO recognize that unnecessarily chaining another process between my input and the desired result is less efficient than just using the code you listed.

Anyway, I essentially just need to make those commands work without having to be run in terminal. Auto-rotate needs to run and work at all times, and I would like to be able to run auto-rotate in the Run-Application window (F2) or as a command in the "keyboard shortcuts" configuration. Do you know how I can do this? I feel as if this is all fixed very extremely simply, but I don't know how.

---

### Post by Favux on 2011-03-09
> Now, I have the lone problem of being able to make these scripts run without opening a terminal and running them there. 
Sure.  For example you take the method 5 autorotation script make it executable and set it up in Startup Applications.

Instructions on using a Launcher or keybinding with Compiz to a bezel button are right below method 5.

---

### Post by xdominex on 2011-03-09
Ok, after reboot I definitely found out that those 3 lines were necessary after all lolz.

---

### Post by xdominex on 2011-03-09
Ok, thank you so much for your help! I'm going to start a different thread to ask about why these scripts will only run in terminal.

---

