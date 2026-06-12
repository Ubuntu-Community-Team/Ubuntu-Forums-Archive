---
title: "At or Cron doesnt work starting miro and other programs"
date: 2008-11-16
forum: General Help
---

### Post by micdhack on 2008-11-16
What i want is simple. I go to sleep leaving my computer downloading software and i calculate how much will it take. After this i want to autostart miro so it can download new updates while i am asleep.
Sound simple but it doesnt work..
i used at, and cron. At puts out an error about mail
```
atd[11493]: Exec failed for mail command: No such file or directory
```
While cron interestingly doesnt. Cron returns:
```
Nov 17 02:02:01 micdhack-laptop /USR/SBIN/CRON[14587]: (root) CMD (exec /usr/bin/miro > /home/micdhack/cronerror.txt 2>&1)
Nov 17 02:03:01 micdhack-laptop /USR/SBIN/CRON[14691]: (root) CMD (/usr/bin/miro > /home/micdhack/cronerror.txt 2>&1)
Nov 17 02:04:01 micdhack-laptop /USR/SBIN/CRON[14789]: (root) CMD (/usr/bin/miro > /dev/null 2>&1)
```
These are some examples...
I tried anything i could find but the damn thing wont start through cron. If i run /usr/bin/miro it will work fine. I use crontab -e to edit the cron file.
I also tested echo "test" >> /home/micdhack/error.log which indeed printed error through cron. So an echo command to a file runs but miro doesnt?

---

### Post by p_quarles on 2008-11-16
Neither at nor cron are running as users that have permission to use the X display you have running, so they are not able to run Miro on that display. Using xhost or su you could get around this, but since you indicated you just want it to wait a certain amount of time before starting, I recommend sleep:
```
sleep 600 && miro
```
The "sleep" command is specified in seconds, and will hold the shell for that amount of time and then exit successfully.

---

### Post by jpkotta on 2008-11-16
Looks like at least 2 things are wrong.  I have never used miro, but it looks like it is a graphical app.  If you run it from cron, it won't know which X server to use.  You can tell it by setting the DISPLAY environment variable (the default display is ':0').  Second, it looks like it's getting run as root.  Make sure you're doing this from your own crontab and not root's.

Save this to somewhere like ~/bin/miro_cron.sh
```

#!/bin/bash

export DISPLAY=:0

/usr/bin/miro --options
```

```
export EDITOR=nano
crontab -e
```
```
* 3 * * * /home/micdhack/bin/miro_cron.sh
```

---

### Post by micdhack on 2008-11-17
p_quarles your idea is very good..i didnt thought of sleep..

jpkotta i didnt know that you have to specify at crons which display to use.

Thanks you both for your help. you been helpfull :)

---

### Post by bungledoe on 2009-03-02
Hi,

Did you get this working for launching Miro via cron?

I've tried (running Hardy Heron 8.04 x86) and it doesn't seem to work for me.

I've got a bash script with the following in being run by cron:

> #!/bin/bash

export DISPLAY=:0

/usr/bin/miro

Fails to launch with following output:

> Invalid MIT-MAGIC-COOKIE-1 key/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
libnotify-Message: Unable to get session bus: dbus-launch failed to autolaunch D-Bus session: Invalid MIT-MAGIC-COOKIE-1 keyAutolaunch error: X11 initialization failed.

/var/lib/python-support/python2.5/miro/frontends/widgets/gtk/persistentwindow.py:43: GtkWarning: gdk_screen_get_root_window: assertion `GDK_IS_SCREEN (screen)' failed
  wclass=gtk.gdk.INPUT_OUTPUT, event_mask=0)
/var/lib/python-support/python2.5/miro/frontends/widgets/gtk/persistentwindow.py:43: GtkWarning: gdk_window_new: assertion `GDK_IS_WINDOW (parent)' failed
  wclass=gtk.gdk.INPUT_OUTPUT, event_mask=0)
location: /usr/lib/xulrunner-1.9.0.6/libxpcom.so 
before 3
Traceback (most recent call last):
  File "/usr/bin/miro.real", line 251, in <module>
    startapp()
  File "/usr/bin/miro.real", line 198, in startapp
    startup(props_to_set)
  File "/usr/bin/miro.real", line 80, in startup
    from miro.plat.frontends.widgets.application import GtkX11Application
  File "/var/lib/python-support/python2.5/miro/plat/frontends/widgets/application.py", line 46, in <module>
    from miro.frontends.widgets.application import Application
  File "/var/lib/python-support/python2.5/miro/frontends/widgets/application.py", line 46, in <module>
    from miro.frontends.widgets import dialogs
  File "/var/lib/python-support/python2.5/miro/frontends/widgets/dialogs.py", line 41, in <module>
    from miro.frontends.widgets import style
  File "/var/lib/python-support/python2.5/miro/frontends/widgets/style.py", line 40, in <module>
    from miro.frontends.widgets import imagepool
  File "/var/lib/python-support/python2.5/miro/frontends/widgets/imagepool.py", line 41, in <module>
    from miro.plat.frontends.widgets import widgetset
  File "/var/lib/python-support/python2.5/miro/plat/frontends/widgets/widgetset.py", line 36, in <module>
    from miro.frontends.widgets.gtk.widgetset import *
  File "/var/lib/python-support/python2.5/miro/frontends/widgets/gtk/widgetset.py", line 53, in <module>
    from miro.frontends.widgets.gtk.video import VideoRenderer, can_play_file
  File "/var/lib/python-support/python2.5/miro/frontends/widgets/gtk/video.py", line 47, in <module>
    from miro.frontends.widgets.gtk.persistentwindow import PersistentWindow
  File "/var/lib/python-support/python2.5/miro/frontends/widgets/gtk/persistentwindow.py", line 43, in <module>
    wclass=gtk.gdk.INPUT_OUTPUT, event_mask=0)
RuntimeError: could not create GdkWindow object

Would be useful to get this working so I can effectively schedule Miro to download podcasts when my ISP considers it to be off peak usage.

If not anyone recommend a RSS based Podcast downloader like Miro with scheduling functionality?

Cheers, any help would be gratefully received.

---

### Post by bungledoe on 2009-03-03
Fixed, had to run xhost +.

Sorted it.

---

### Post by mister_p_1998 on 2010-01-25
> **bungledoe said:**
> Fixed, had to run xhost +.

Sorted it.

Whats the syntax for the cron?
Steve

---

