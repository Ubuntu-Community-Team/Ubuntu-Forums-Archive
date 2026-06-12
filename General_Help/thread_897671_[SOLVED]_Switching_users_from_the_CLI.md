---
title: "[SOLVED] Switching users from the CLI?"
date: 2008-08-22
forum: General Help
---

### Post by unutbu on 2008-08-22
Ctrl-Alt-F7 takes me to my current X session.
Ctrl-Alt-F8 takes me to a blank screen.

If I press the little green running man in the upper right corner, however, I can select Switch User, and
Ctrl-Alt-F8 becomes a gdm login screen.

[list=1]
[*]Is there a CLI command that is equivalent to clicking the Switch User button?
[*]Is there a gdm configuration option which will make a gdm login screen on my virtual terminal #8 automatically?
[/list]

---

### Post by LateNiteTV on 2008-08-22
are you trying to switch the entire user gnome session? or just in the console?
if you just want to change users in the console do:

su userName

---

### Post by unutbu on 2008-08-22
Thanks LateNiteTV, actually I'm trying to switch the entire gnome session.

---

### Post by kdnewton on 2008-08-22
I'm taking a stab in the dark here. I believe if you go to another tty ( alt+ctrl+1-6,8 ) you'll find the CLI. Log in with the user and then type "startx". It works for my fluxbox configuration and may work for Gnome,KDE. Otherwise it might be /etc/init.d/gdm start or /etc/init.d/kdm start for gnome/kde respectively.

Edit: After a second reading of your original post I think I may have missed the mark here. You want tty8 to automatically have the gdm login screen running when the PC is turned on, just the same as tty7 is?

---

### Post by mali2297 on 2008-08-22
You can start a new X session in virtual terminal #8 with the command
```

startx -- :1

```

---

### Post by unutbu on 2008-08-22
Thanks for the suggestions. Unfortunately, I haven't figured out how to make them work.

> 
You want tty8 to automatically have the gdm login screen running when the PC is turned on, just the same as tty7 is?

Yes, this is my second option. It would be neat to know a command which can do the same think as the "Switch User" button, but just having tty8 ready with a gdm login screen is fine too.

@mali2297, when I type "startx -- :1" in a gnome-terminal, I get 
```

out@themovies:~% startx -- :1
xauth:  creating new authority file /home/out/.serverauth.10935
X: user not authorized to run the X server, aborting.
xinit:  Server error.
Couldnt get a file descriptor referring to the console

```
And when I go to tty2 (Ctrl-Alt-F2) and type
```

startx -- :1 2>~/startx-errors
```

Then I get 
```

xauth:  creating new authority file /home/out/.serverauth.10854

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux themovies 2.6.22-14-generic #1 SMP Tue Feb 12 UTC 2008 i686
Build Date: 18 January 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Fri Aug 22 2008
(==) Using config file: "/etc/X11/xorg.conf"

(II) Module already built-in


waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.



```

Either way I do not get an X session.

---

### Post by kdnewton on 2008-08-22
Right, startx -- :1 should work.

When the PC starts it runs something equivalent to "startx -- :0" to tell the display manager to draw the first screen on tty7. You run "startx -- :1" to tell it to draw the next screen in the series on whatever tty you are in. If you want yet another then you type "startx -- :2" etc...

Worked for me. Give it a try again with another value.

---

### Post by LateNiteTV on 2008-08-22
can you post the output of:
```
ps aux | grep xorg
```

---

### Post by unutbu on 2008-08-22
I can get a very ugly X session going on tt8 by typing
```

xinit -- :1
```
from tty2. However, this circumvents gdm and GNOME. 
I suspect startx would do the same kind of thing, even if I got it to work. (Doesn't startx call init?)

Thank you for your suggestions, but I'm looking for a way to get to a second gdm login window from the CLI.

@kdnewton: 
```
% startx -- :2
xauth:  creating new authority file /home/out/.serverauth.11068

X: user not authorized to run the X server, aborting.

```
I then switched to tty8, tty9, tty10, but all I get is a black screen and a flashing cursor in the upper left corner. I guess this is not surprising since it said X was aborting.

Since I don't get my prompt back, I then did a Ctrl-Z:
```

[1]+  Stopped                 startx -- :2
% kill %1
```

The terminal then gives me this (I did not type "giving up" -- that was from stderr)
```

% giving up.
xinit:  Connection refused (errno 111):  unable to connect to X server
xinit:  No such process (errno 3):  unexpected signal 15.

[1]+  Terminated              startx -- :2

```

@LateNiteTV:
```

% ps aux | grep xorg
out   11046  0.0  0.0   2972   760 pts/0    S+   14:54   0:00 grep xorg

```

---

### Post by zekica on 2008-08-22
Go to system -> administration -> login screen

Go to Security tab, and click on: Configure X server...
Click add/modify and then choose VT: 1 Server: standard and try to see if it works.

You don't need to restart your computer, you just need to type:
sudo /etc/init.d/gdm restart

to restart GDM and apply new settings (it will kill your current gnome session).

---

### Post by kdnewton on 2008-08-22
> **zekica said:**
> You don't need to restart your computer, you just need to type:
sudo /etc/init.d/gdm restart

to restart GDM and apply new settings (it will kill your current gnome session).

I'm curious. Is /etc/init.d/gdm restart the same as the hotkeys CTRL-ALT-BACKSPACE? I know that will restart your current X-Session but does that restart/apply changes to gdm?

---

### Post by unutbu on 2008-08-22
Thank you zekica, it works!

---

### Post by bodhi.zazen on 2008-08-22
See this thread :

[How-to run Multiple (Virtual) X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=271674")

---

