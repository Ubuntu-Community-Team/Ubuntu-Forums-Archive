---
title: "Forcing an App to Quit"
date: 2008-08-04
forum: General Help
---

### Post by lupinesoul on 2008-08-04
The thing is, I was using Blender's 3D renderer for my model, but I accidentally hit Render Scene/Animation(I forget which) instead of Render Frame.  I just need to close the renderer, which is in a separate window,but obviously the x won't work because it keeps looping a single frame. Is there a way to force it to quit, like Windows' Task Manager?

---

### Post by loboc on 2008-08-04
in a terminal type 

```
 ps -u username | less 
``` to list the processes you are running to identify the PID number of the window
it looks like this  
 ```

 PID TTY          TIME CMD
 5831 tty1     00:00:00 bash
 5842 ?        00:00:00 gnome-keyring-d

```

then type 
```
kill #
```

OR type

killall blender

to killa nay instance of blender you are running

If you use sudo you can kill processes that are root or owned by another user

read 
```

man kill

```
and 
```

man ps

```

---

### Post by lupinesoul on 2008-08-04
Thank you.  That's very helpful, but none of my processes is actually called blender.  Does anything here seem out of the norm?  The only other windows I have up are a nautilus file browser, a firefox web browser, and the Terminal.

```
  PID TTY          TIME CMD
 5898 ?        00:00:01 gconfd-2
 5900 ?        00:00:00 gnome-keyring-d
 5901 ?        00:00:00 x-session-manag
 6020 ?        00:00:00 seahorse-agent
 6024 ?        00:00:00 dbus-daemon
 6025 ?        00:00:01 gnome-settings-
 6031 ?        00:00:02 pulseaudio
 6036 ?        00:00:00 gconf-helper
 6053 ?        00:00:14 gnome-screensav
 6054 ?        00:00:11 metacity
 6055 ?        00:00:08 gnome-panel
 6057 ?        00:00:08 nautilus
 6064 ?        00:00:00 bonobo-activati
 6066 ?        00:00:00 bluetooth-apple
 6069 ?        00:00:00 gvfsd
 6070 ?        00:00:00 update-notifier
 6077 ?        00:00:00 evolution-alarm
 6078 ?        00:00:00 tracker-applet
 6083 ?        00:00:00 trackerd
 6086 ?        00:00:00 gnome-volume-ma
 6088 ?        00:00:08 nm-applet
 6091 ?        00:00:00 gvfs-fuse-daemo
```

Edit: Nevermind; It decided to stop running and I was able to close it.  However, you were still a great help.  Thank you.

---

### Post by cszikszoy on 2008-08-04
If you right click on a gnome panel, and add an applet, there is one called Force Quit.  Pressing this will bring up a dialog box asking you to click on the window that isn't responding, and it will kill it for you.

Also, you can type ps -ef | grep <program name>.  This will bring up the process id.

To force quit right away, use: kill -15 <process id>

---

### Post by caljohnsmith on 2008-08-04
Just thought I would mention this, Lupinesoul, but an easy way to kill a GUI app is to use:
```
sudo xkill
```
Then use the cross-hairs to click on the window you want to kill. The only drawback is that it sometimes doesn't kill all the processes associated with the window you kill, but most of the time it works quite well.

If you want to know the process name of a GUI program, here's another trick:
```
xprop | grep WM_CLASS
```
Again, use the cross-hairs to click on the GUI window you want to know the process name for. For instance, when I click on a Gnome terminal window it returns:
```
WM_CLASS(STRING) = "gnome-terminal", "Gnome-terminal"
```
So the process/program name is "gnome-terminal". I could then do:
```
sudo killall gnome-terminal
```
And that would kill gnome-terminal and any child processes it might have. That trick of using xprop to find the GUI program name won't work in all cases, but for many apps it works great.

---

### Post by x1a4 on 2008-08-04
Hi,
You can also use Ctrl+Alt+Esc then click on the window to close.  You can also use **pkill** to kill an app without having to bother to look-up its process ID.  
```
pkill *appexec*
```
Where *appexec* is the executable of the application.

The only catch with pkill is that it will kill _all_ processes with that name--as long as you have permission to kill it.  

If neither kill nor pkill work use the **-9** option, but only if you can't close the app any other way.
```
pkill -9 *appexec*
```
```
kill -9 *procid*
```

---

### Post by lavinog on 2008-08-05
Have you tried pressing ESC or ctrl-c to stop the render?

---

