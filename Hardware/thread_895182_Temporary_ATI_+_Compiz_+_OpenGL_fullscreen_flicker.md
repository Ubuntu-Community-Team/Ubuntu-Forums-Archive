---
title: "Temporary ATI + Compiz + OpenGL fullscreen flicker fix"
date: 2008-08-19
forum: Hardware
---

### Post by gatekeep on 2008-08-19
Thought I'd share this to the community after fighting with this annoying bug in the fglrx drivers.

Basically, this whole mess comes down to a incompatibility between compiz and fglrx drivers when an OpenGL application is fullscreen or windowed.

My little fix for this is as follows:
1) Create off_compiz in ~/bin (create directory if it doesn't exist) with the following content:
```
#!/bin/bash
PID=`ps x | awk '/compiz.real/ && !/awk/ {print $1}'`
kill -KILL $PID
```

2) Create on_compiz in the same directory as off_compiz, with the following content:
```
#!/bin/bash
COMPIZ=`which compiz`
$COMPIZ --sm-client-id default0 >/dev/null 2>/dev/null &
```

3) Modify any menu entries (for example Extreme Tux Racer), using the menu editor, change the command for Extreme Tux Racer to:
```
bash -c "off_compiz && etracer; on_compiz"
```

(Be sure to login/logout if you didn't have a bin directory in your home directory.)

Basically what this will do, is modify the OpenGL application launcher with the flicker problem, it will effectively terminate compiz before executing the application and then restart compiz after the application has exited.

I find that for me on my laptop this solves most of my problems with flicker, until ATI fixes their damn drivers.

(Note: If this post is in the wrong place, moderators, feel free to move it to the proper location.)

---

### Post by paintbalforjesus on 2008-12-04
we were talking about this in a different forum: [http://ubuntuforums.org/showthread.php?p=6309489#post6309489](http://ubuntuforums.org/showthread.php?p=6309489#post6309489)

but I thought I'd post my question here since it actually deals with this post.

Can this be used to fix screensaver flicker too?  Is there some command that runs/exits the screensaver that I can edit to have this fix the screensaver too?

---

### Post by perixx on 2009-02-07
Thank you for this skript, gatekeep!


There is but a problem with it: as long as the started application is running, you're left without any window manager; if the application doesn't run in fullscreen, or if you switch to windowed mode meanwhile, there's trouble ahead. It's also impossible to use multiple apps via the task switcher and should your application crash, you might be left without a window manager as well. In this case, there's also no shortcut availible, to manually run the on_compiz script.

I've tried to do auto-toggling between compiz and xfwm4 in your script, prior to starting the application, but this will only make the skript halting on launching xfwm4. The script will only continue and run the desired application, when xfwm4 is terminated...

Do you have any suggestions on that?

Greetings,,


perixx

---

### Post by perixx on 2009-02-15
OK, here it is:

**How to temporarily disable compiz via script and per application AND switching to alternative xwfm4 window manager for windowed action.**

Note, that this poses an example script, which must be adapted to your needs and can be run from a starter; I presume here, that you've already prepared **gatekeep's** scripts above - my example is based on them: 

```
#! /bin/bash

cd ~/someapplication
~/bin/off_compiz; (xfwm4 & ~/someapplication/thebinary) & wait
~/bin/on_compiz
``` > save it e.g. in ~/scripts

Basically, what this will do is: running gatekeep's **off_compiz** script and then it will run the xfce-windowmanager **xfwm4** together with your desired application in a parallel subshell process. It then waits for termination of the application and runs **on_compiz** script, which brings back up compiz.

**The advantage** of this is, that you're not left without any window manager and can do app-switching & windowed viewing, while still using OpenGL (but not compiz).

If you can't run your scripts, check for executability:
rightclick > properties > permissions > run file as program (checkmark)
or on the terminal do: ```
chmod 754 ~/scripts/yourscript
```

Other workarounds, like 'unredirect fullscreen windows' or applying aticonfig switches didn't work at all or not reliably for me here, but with the new ATI 9.1 driver, it's at least possible to watch videos in fullscreen via OpenGL without flickering.

regards and thanks to gatekeep,


perixx

---

