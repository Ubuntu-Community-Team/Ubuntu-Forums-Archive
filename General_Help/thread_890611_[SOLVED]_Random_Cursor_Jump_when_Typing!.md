---
title: "[SOLVED] Random Cursor Jump when Typing!"
date: 2008-08-15
forum: General Help
---

### Post by Jose Catre-Vandis on 2008-08-15
and lol it happened whilst typing the title :)

Running Fiesty on a Dell Inspiron 9300 desktop replacement laptop (Dual booting with XP).

Irrespective of the place I am typing, e.g. Ooo, gedit, terminal, web forms, the cursor has a tendency to jump to another place. Annoying as I am a stare at the keyboard whilst typing person! No such problems under XP so this probably discounts a hardware issue.

Any suggestions as how to resolve?

---

### Post by durand on 2008-08-15
I don't know much about this issue but it's probably your touchpad being touched when you are typing. There will be a setting somewhere to disable the touchpad while typing.

EDIT: [http://ubuntuforums.org/showthread.php?t=271052&highlight=disable+touchpad+while+typing](http://ubuntuforums.org/showthread.php?t=271052&highlight=disable+touchpad+while+typing)

---

### Post by mrsteveman1 on 2008-08-15
Synaptics touchpads do this, not when they are touched by accident just at random. Doesn't happen in XP because its using the real driver there.

In linux its a community written xorg driver.

---

### Post by Jose Catre-Vandis on 2008-08-15
Thanks I'll give it a try and report back...

---

### Post by Jose Catre-Vandis on 2008-08-18
I have tried the following:

```
sudo nano /etc/X11/xorg.conf
```
Find section:
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"

```

Add

```
Option   "SHMConfig"    "on"
```

Save

System ->  Preferences  -> Sessions -> Startup Programs

Add New

```
syndaemon -i 3 -d -t -k
```
as both name and command

```
CTRL+ALT+BACKSPACE
```

No problems so far

Usage for syndaemon:

```
Usage: syndaemon [-i idle-time] [-d] [-t] [-k]
-i How many seconds to wait after the last key press before
enabling the touchpad. (default is 2.0s)
-d Start as a daemon, ie in the background.
-p Create a pid file with the specified name.
-t Only disable tapping and scrolling, not mouse movements.
-k Ignore modifier keys when monitoring keyboard activity.
-K Like -k but also ignore Modifier+Key combos.
```

[COLOR="Sienna"]**EDIT: After three days testing, no jumping about so problem solved. Thanks to all for help and pointers.**[/COLOR]

---

### Post by Loaded.len on 2008-08-18
> **mrsteveman1 said:**
> Synaptics touchpads do this, not when they are touched by accident just at random. Doesn't happen in XP because its using the real driver there.

In linux its a community written xorg driver.

It does happen in XP as a matter of fact, but it's fixable if you lower the acceleration of the pointer by one or two notches.

---

### Post by kray_zee1 on 2009-01-31
I  have the same problem on a dell d505 I have tried this and am not getting anywhere...none of there commands
are working for me..im new and may not be doing this right but if i cant solve it i cant stay with ubuntu.

---

### Post by abn91c on 2009-01-31
> **kray_zee1 said:**
> I  have the same problem on a dell d505 I have tried this and am not getting anywhere...none of there commands
are working for me..im new and may not be doing this right but if i cant solve it i cant stay with ubuntu.
TRy the simple stuff first, may sure the touchpad is clean, no greasy finger prints,etc....

---

### Post by crjackson on 2009-04-19
> **Jose Catre-Vandis said:**
> I have tried the following:

```
sudo /etc/X11/xorg.conf
```
Find section:
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"

```

Add

```
Option   "SHMConfig"    "on"
```

Save

System ->  Preferences  -> Sessions -> Startup Programs

Add New

```
syndaemon -i 3 -d -t -k
```
as both name and command

```
CTRL+ALT+BACKSPACE
```

No problems so far

Usage for syndaemon:

```
Usage: syndaemon [-i idle-time] [-d] [-t] [-k]
-i How many seconds to wait after the last key press before
enabling the touchpad. (default is 2.0s)
-d Start as a daemon, ie in the background.
-p Create a pid file with the specified name.
-t Only disable tapping and scrolling, not mouse movements.
-k Ignore modifier keys when monitoring keyboard activity.
-K Like -k but also ignore Modifier+Key combos.
```

[COLOR="Sienna"]**EDIT: After three days testing, no jumping about so problem solved. Thanks to all for help and pointers.**[/COLOR]

I just wanted to note that things have changed with Jaunty. If you are using Jaunty you only need to create the Syndaemon. Changing the xorg.conf file can and will likely cause booting problems (it did for me). I got booted to CLI and had to restore my old xorg.conf file. However the Syndaemon was running upon reboot and it took effect without the need to modify the xorg.conf.

---

### Post by Jose Catre-Vandis on 2009-04-20
Thanks for the update crjackson :)

---

### Post by pwebster25 on 2009-04-30
I did just the following:  I added the new session, per suggestion.  

System ->  Preferences  -> Sessions -> Startup Programs

Add New

```
syndaemon -i 3 -d -t -k
```

It solved the jumping cursor problem.  However, now I can't middle-click on my regular USB mouse to open a link in a new tab.  This bugs, as I use this feature all the time in firefox.  Otherwise all the buttons and even the scroll works fine on my USB mouse, just not the middle-click (clicking with the mouse roller).

---

### Post by Jose Catre-Vandis on 2009-04-30
> **pwebster25 said:**
> I did just the following:  I added the new session, per suggestion.  

System ->  Preferences  -> Sessions -> Startup Programs

Add New

```
syndaemon -i 3 -d -t -k
```

It solved the jumping cursor problem.  However, now I can't middle-click on my regular USB mouse to open a link in a new tab.  This bugs, as I use this feature all the time in firefox.  Otherwise all the buttons and even the scroll works fine on my USB mouse, just not the middle-click (clicking with the mouse roller).

Remove the syndaemon and try touchfreeze (its in the repos), see if that sorts things out for you?

---

### Post by pwebster25 on 2009-05-01
> **Jose Catre-Vandis said:**
> Remove the syndaemon and try touchfreeze (its in the repos), see if that sorts things out for you?

This worked perfectly (at least so far).  Thanks.  I have put up with this for so long.  If I would have just checked it out I could have eliminated this annoyance a long time ago.

Thanks
pw

---

### Post by Jose Catre-Vandis on 2009-05-02
My pleasure, I only found it because I couldn't answer your initial query so went off searching for help and it came back on another post on another forum (arch I think). So I guess if touchfreeze does the same job, the original fix is now redundant :)

---

### Post by willperrin on 2009-05-06
thanks for tips on the changes in jaunty - but any chance of an idiots guide to doing this - i am competent in windows etc but only slowly picking up ubuntu so not quite clear how to create the daemon.  

this problem is a nightmare on my old vaio laptop

cheers

w

---

### Post by pwebster25 on 2009-05-06
> **willperrin said:**
> thanks for tips on the changes in jaunty - but any chance of an idiots guide to doing this - i am competent in windows etc but only slowly picking up ubuntu so not quite clear how to create the daemon.  

this problem is a nightmare on my old vaio laptop

cheers

w

The simplest no-code method is to install TouchFreeze which may/may-not solve your problem.  I'm not sure if it has solved my problem on a Gateway cx2618. It seems better but not completely gone.  If touchfreeze doesn't work then you will need to go with a more complex solution, as above.

I'm not much more than a newbie myself but here goes (maybe a little too simple for you):
1) System Menu -> Admin -> Synaptic Package Manager
2) QuickSearch for TouchFreeze
3) Click to Install and Apply
4) It should appear in your Applications -> Accessories (I'm not sure if it works if it is not opened). If not, then you will need to set it to open on startup (Sessions.  Someone else will need to help out on setting it up to run automatically).

Good luck.

---

### Post by ballistik on 2009-05-19
Thanks!! THis helped me so much!!

---

### Post by mhpathfinder on 2009-05-19
Thanks to all on this string for this.  My long-term jumping cursor is still.
I have an HP Special Edition L2005US with an AMD Turion 64 and Synaptics Touchpad.  I've been seeking a resolution for the jumping through the past four UBUNTU distros.  Thought I had one for Hardy Heron, but jumping continued.  I missed these resolutions until today.  I tested through Thunderbird email client, Open Office Writer, and this reply.  NO JUMPING CURSOR.  Amazing how one little annoyance can magnify itself when all other aspects of a fine operating system are working so well.
Thanks again.
MH Pathfinder

---

