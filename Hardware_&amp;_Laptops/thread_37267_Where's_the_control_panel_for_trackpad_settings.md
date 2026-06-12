---
title: "Where's the control panel for trackpad settings?"
date: 2005-05-26
forum: Hardware &amp; Laptops
---

### Post by ciprol on 2005-05-26
Absolute newbie to Ubuntu and Linux here and have just installed 5.0.4 on a Dell Latitude laptop. For the life of me I could not find a control panel for the various settings of my trackpad. I hate those tap-clicks and is desperate to turn it off.

Pls give me a pointer. Thanks!

---

### Post by mlord on 2005-05-26
[QUOTE=ciprol]Absolute newbie to Ubuntu and Linux here and have just installed 5.0.4 on a Dell Latitude laptop. For the life of me I could not find a control panel for the various settings of my trackpad. I hate those tap-clicks and is desperate to turn it off.

Pls give me a pointer. Thanks![/QUOTE]
 There isn't one (or not that I know of, anyway).

The command-line tool is **synclient**, as in:

      **synclient -l**

which dumps out the current settings.  You can then change them on the command line as per the man page.

Cheers

---

### Post by ciprol on 2005-05-27
[QUOTE=mlord]There isn't one (or not that I know of, anyway).

The command-line tool is **synclient**, as in:

      **synclient -l**

which dumps out the current settings.  You can then change them on the command line as per the man page.

Cheers[/QUOTE]
 Thanks.

Pretty much my first install of Linux. Gosh, it's so much more technical than Mac OS X and even Windows by a big margin. I have to say that I am a little disappointed. Can't believe there's no easier way to configure the trackpad and the need for command line for 3rd party app installation.

Continue to struggle away...

---

### Post by tim@bigredtree.com on 2005-05-27
In a terminal type 
```

sudo gedit /etc/X11/xorg.conf

```
Search for Section "Device"
Find the "device" section that is for your mouse. It should include the line: 
Option          "SendCoreEvents" 
In that section add the line:
Option "MaxTapTime" "0"
Save.
After you restart X, that should disable tapclicks.

---

