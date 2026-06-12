---
title: "fjbdrv: stylus does not follow rotation on fujitsu lifebook t5010 under kubuntu 12.10"
date: 2013-02-11
forum: Hardware
---

### Post by markwig on 2013-02-11
Hello,

I am running kubuntu 12.10 on a Fujitsu Lifebook T5010 and I have some
trouble with the rotation of the tablet. I have installed the packages
[INDENT]fjbtndrv-2.3.2-1
fjbtndrv-kernel-source-2.3.2-1
fscd-2.3.2-1
fscrotd-2.3.2-1
[/INDENT]from  [https://launchpad.net/~khnz/+archive/ppa/+build/2976449](https://launchpad.net/~khnz/+archive/ppa/+build/2976449)
as was suggested in the thread
[http://ubuntuforums.org/showthread.php?t=1916679](http://ubuntuforums.org/showthread.php?t=1916679)

With the normal orientation the stylus works fine and rotation via the
tablet button works also. However, after rotating the screen the
stylus is out of tune. When I point to some corner, the pointer moves
to the neighbouring corner anti-clockwise. This is the case for the
orientations left, inverse and right likewise. Moreover, coming back
to normal the stylus uses only half the screen.

I have tried different solutions that were suggested for previous
versions of ubuntu in different threads:

1. [http://ubuntuforums.org/showpost.php?p=6274392&postcount=1](http://ubuntuforums.org/showpost.php?p=6274392&postcount=1)
[LIST]
[*]I tried the script in method 1 without any change.
[/LIST]

[LIST]
[*]I tried the package wacomrotate in method 4 without any change.
[/LIST]

[LIST]
[*]I tried to install magick-rotate. The installation said that the program was installed properly but checkmagick did not work
[/LIST]
2. [http://ubuntuforums.org/showthread.php?t=1904356&highlight=fjbtndrv](http://ubuntuforums.org/showthread.php?t=1904356&highlight=fjbtndrv)
I tried the change in rotate-wacom.sh suggested in this thread but
that did not change anything either.

3. [http://doc.ubuntu-fr.org/fujitsu-siemens_lifebook_t1010](http://doc.ubuntu-fr.org/fujitsu-siemens_lifebook_t1010)
I have tried the script provided at the end of this thread, but then
the stylus didn't work at all. 

Previously I was running ubuntu 9.10 on the laptop and everything
worked fine.

Has anybody any other suggestion what I might try?

Best, Thomas

---

### Post by Favux on 2013-02-11
Hi Thomas,

Welcome to Ubuntu forums!

> I tried to install magick-rotate. The installation said that the program was installed properly but checkmagick did not work
With Quantal's 3.5 kernel there should already be a working fujitsu-tablet.ko.  The kernel maintainers finally accepted it into the 3.3 kernel and the bug fixes into the 3.4 kernel.  My guess the reason Magick Rotation did not work is the fjbtndrv PPA you installed is interfering.  That has an old version of fujtsu-tablet.ko which Magick probably can't read.

I'm surprised you were able to install the Oneiric fjbtndrv in Quantal but you probably need to remove that PPA before you can get automatic rotation working.  Not sure why the rotation script in fjbtndrv isn't working for you but figuring out the problem could be tough.  I've looked at it before but it is confusing because Robert uses c code to grab values, developer type stuff, rather than user level stuff we could probably decode.

You'll lose the tablet button for rotation until you find its keycode in xev and bind it to a rotation script.

---

### Post by markwig on 2013-02-11
Dear Favux,

thanks for the very fast reply. I have deinstalled fjbtndrv and reinstalled the kernel version 3.5.0-23 in order to ensure that I have the right fujitsu-tablet.ko. 

I was now able to install magick rotate. I have checked the setup and then I have used xrotate.py to rotate. That works, but the stylus does not follow. So, unfortunately the problem remains the same. 

Best, Thomas

PS: I value your comments. Two years ago they made it possible for me to get the rotation working under kubuntu 9.10. Thanks also for that.

---

### Post by Favux on 2013-02-11
So when you rotate the screen now Magick automatically rotates your screen orientation?  Correct?

If so then fujitsu-tablet.ko is working and there is another issue.  What is the output of the following command in a terminal?
```
xinput list
```

---

### Post by markwig on 2013-02-11
> **Favux said:**
> So when you rotate the screen now Magick automatically rotates your screen orientation?  Correct?


According to the "xrandr -q --verbose" output the orientation changes with each application of xrotate.py. However, no matter whether in the setup of magick-rotate the rotation mode is right or left, it switches from normal to left to inverted to right to normal. I don't know if that is important. 

> **Favux said:**
> 
If so then fujitsu-tablet.ko is working and there is another issue.  What is the output of the following command in a terminal?
```
xinput list
```

The output of xinput list is as follows:
```
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                id=16   [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                id=17   [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch                 id=18   [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                        id=15   [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                id=19   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                           id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=8    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                           id=9    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02BF                           id=10   [slave  keyboard (3)]
    &#8627; Power Button                              id=11   [slave  keyboard (3)]
    &#8627; Sleep Button                              id=12   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=14   [slave  keyboard (3)]
    &#8627; FJ Camera                                 id=13   [slave  keyboard (3)]

```

---

### Post by Favux on 2013-02-11
xrotate.py can function as a stand alone rotation script.  But that is not how if is suppose to function in Magick.  Do you see the green arrow tray icon?  When you right click on it and go into set up and set direction to go to when rotated, is that the direction it rotates the screen orientation when you rotate the screen?

In other words from what you've said I still have no idea whether Magick is working for you yet.

The xinput list output looks normal.

---

### Post by markwig on 2013-02-11
> **Favux said:**
> xrotate.py can function as a stand alone rotation script.  But that is not how if is suppose to function in Magick.  Do you see the green arrow tray icon?  When you right click on it and go into set up and set direction to go to when rotated, is that the direction it rotates the screen orientation when you rotate the screen?


How do I rotate the screen with Magick if not by calling xrotate.py?

If I set the orientation in the setup to right and call xrotate.py it rotates to the left anyhow. But if I understand your comment correctly, xrotate.py and the setup are independent of each other.

---

### Post by Favux on 2013-02-11
Magick senses the hinge signal when you physically swivel the screen into tablet or laptop mode and auto-magically rotates your screen orientation so you do not have to call a rotation script.

So you do have the green arrow icon in the tray?  And clicking on it gets you to setup?

---

### Post by markwig on 2013-02-11
> **Favux said:**
> Magick senses the hinge signal when you physically swivel the screen into tablet or laptop mode and auto-magically rotates your screen orientation so you do not have to call a rotation script.


Ok. Then Magick is not working properly. When I switch to tablet mode, nothing happens.

> 
So you do have the green arrow icon in the tray?  And clicking on it gets you to setup?

Yes, I do have the green arrow icon in the tray.  And yes, I do get the setup, when right-clicking on it.

---

### Post by Favux on 2013-02-11
OK, then go into Setup and then Advanced Setup and click on the debugging tool log.  Rotate the screen to tablet mode and back a couple of times and then attach the log to your next post.

Edit:  And which version of Magick are you using?

---

### Post by markwig on 2013-02-11
> **Favux said:**
> OK, then go into Setup and then Advanced Setup and click on the debugging tool log.  Rotate the screen to tablet mode and back a couple of times and then attach the log to your next post.


I just realised why Magick was not able to rotate. I installed the programme with sudo and my username was missing in the group. Now that I have changed this, Magick does the auto rotation. Sorry. However, the stylus does not follow. 

I enclose the log file:

```

23:50:48: checking for rotation
23:50:48: /usr/bin/checkmagick32
23:51:13: cur_state: 1 
23:51:13: old_state: None 
23:51:13: calling rotation b: 
23:51:13: left
23:51:14: calling cellwriter --show-window
23:51:14: Change to Tablet mode
23:51:14: checking for rotation
23:51:14: /usr/bin/checkmagick32
23:52:06: cur_state: 0 
23:52:06: old_state: 1 
23:52:06: calling rotation a: 
23:52:06: normal
23:52:06: calling cellwriter --hide-window
23:52:06: Change to normal state
23:52:06: checking for rotation
23:52:06: /usr/bin/checkmagick32
23:52:13: cur_state: 1 
23:52:13: old_state: 0 
23:52:13: calling rotation b: 
23:52:13: left
23:52:13: calling cellwriter --show-window
23:52:13: Change to Tablet mode
23:52:13: checking for rotation
23:52:13: /usr/bin/checkmagick32
23:52:16: cur_state: 0 
23:52:16: old_state: 1 
23:52:17: calling rotation a: 
23:52:17: normal
23:52:17: calling cellwriter --hide-window
23:52:17: Change to normal state
23:52:17: checking for rotation
23:52:17: /usr/bin/checkmagick32
23:52:22: cur_state: 1 
23:52:22: old_state: 0 
23:52:23: calling rotation b: 
23:52:23: left
23:52:23: calling cellwriter --show-window
23:52:23: Change to Tablet mode
23:52:23: checking for rotation
23:52:23: /usr/bin/checkmagick32
23:52:26: cur_state: 0 
23:52:26: old_state: 1 
23:52:27: calling rotation a: 
23:52:27: normal
23:52:27: calling cellwriter --hide-window
23:52:27: Change to normal state
23:52:27: checking for rotation
23:52:27: /usr/bin/checkmagick32

```

> 
Edit:  And which version of Magick are you using?

Version 1.6.2

---

### Post by Favux on 2013-02-11
> my username was missing in the group. Now that I have changed this, Magick does the auto rotation.
Nice.  Good job on diagnosing!

Log file looks good now.
> However, the stylus does not follow.
Let's try the xsetwacom commands manually and see if they work.

So to go to right portrait with the stylus motion use in a terminal:
```
xsetwacom set "Serial Wacom Tablet stylus" rotate cw
```
And then to bring it back to laptop:
```
xsetwacom set "Serial Wacom Tablet stylus" rotate none
```
Does that change the stylus orientation?

You don't still have Wacomrotate active do you?

---

### Post by markwig on 2013-02-12
> **Favux said:**
> Nice.  Good job on diagnosing!
 
Well, it says so in the instructions and I had inserted the my username in the group each time in before, when I installed Magick. I shouldn't have forgotten to do so this time.

> 
You don't still have Wacomrotate active do you?

It was still active. I have deinstalled it now.

> 
Log file looks good now.

Let's try the xsetwacom commands manually and see if they work.

So to go to right portrait with the stylus motion use in a terminal:
```
xsetwacom set "Serial Wacom Tablet stylus" rotate cw
```And then to bring it back to laptop:
```
xsetwacom set "Serial Wacom Tablet stylus" rotate none
```Does that change the stylus orientation?

You don't still have Wacomrotate active do you?

While wacomrotate was still installed the first command made the stylus actually follow on right rotation perfectly. But when switching back to normal mode the second command would still lead to a stylus which only used half the screen.

After deinstallation of wacomrotate the stylus does not work anymore at all. Also reinstalling Magick has not changed that.

---

### Post by markwig on 2013-02-12
> **markwig said:**
> 
After deinstallation of wacomrotate the stylus does not work anymore at all. Also reinstalling Magick has not changed that.

I have figured out that once I have used the command 
```
xsetwacom set "Serial Wacom Tablet stylus" rotate none
```after rotating the screen back then the stylus does not work after a restart of the laptop. However, restarting the laptop again, the stylus works again fine. I don't know the reason, but that is not really a problem.

Moreover, the command
```
xsetwacom set "Serial Wacom Tablet stylus" rotate cw
```makes the stylus follow the right rotation of the screen invoked by Magick.

When rotating back, the orientation of the stylus is apparently changed back to normal automatically, however the "Coordinate Transformation Matrix" is changed from
```
1 0 0 0 1 0 0 0 1
```to 
```
1.6 0 0 0 0.625 0 0 0 1
```which caused the problem, that only half the screen is used and the stylus is out of tune. The same applies to touch and eraser.

The commands 
```
xinput set-prop "Serial Wacom Tablet stylus" "Coordinate Transformation Matrix" 1 0 0 0 1 0 0 0 1
xinput set-prop "Serial Wacom Tablet touch" "Coordinate Transformation Matrix" 1 0 0 0 1 0 0 0 1
xinput set-prop "Serial Wacom Tablet eraser" "Coordinate Transformation Matrix" 1 0 0 0 1 0 0 0 1
```change the matrices back. 

In some sense this solves my problem. I can now use the tablet with rotation. It would however be nice if this was done automatically by Magick. Any idea what I would have to change there?

---

### Post by markwig on 2013-02-12
> **markwig said:**
> 
In some sense this solves my problem. I can now use the tablet with rotation. It would however be nice if this was done automatically by Magick. Any idea what I would have to change there?

One way to get this automatic is to save the commands in a script, say stylus-rotation-fix.sh, copy this to /usr/share/magick-rotation, make it executable for anybody and add the magic rotation setup in the advanced section on the line "Run after switch to tablet" and on the line "Run after switch to normal" the following:
```
/usr/share/magick-rotation/stylus-rotation-fix.sh
```I enclose my version of this script for which I have allowed myself to modify script posted by favux in the thread [http://ubuntuforums.org/showpost.php?p=6274392&postcount=1](http://ubuntuforums.org/showpost.php?p=6274392&postcount=1) under method 1.

I suppose there are better ways to solve this issue, but it works at least.

---

### Post by Favux on 2013-02-12
Sweet, you've actually found a working solution for your issue.

However you've managed to totally confuse me.  Magick does not use the coordinate transform matrix for xf86-input-wacom rotation.  Only for evdev rotation.  I have no idea why your CTM changes on rotation back to laptop giving you the half screen thing.

What I'm getting is without wacomrotate Magick now does right portrait and so on correctly stylus and touch wise.  Is that right?  Just the half screen issue on rotation to laptop left?

I'm trying to think of how I could have messed up 1.6.2, when I fixed the CTM for evdev, to get the wacom X driver included in a CTM.  I just don't see it.  I'm thinking this is some bug in kwin or something.  Is there something else active which is trying to assist in rotation?

---

### Post by markwig on 2013-02-12
> **Favux said:**
> 
However you've managed to totally confuse me.


I am sorry about that. :-)

> 
What I'm getting is without wacomrotate Magick now does right portrait and so on correctly stylus and touch wise.  Is that right?
No. The rotation of the stylus is done by the script via xsetwacom.

>  Just the half screen issue on rotation to laptop left?
That remains as well.

> 
Is there something else active which is trying to assist in rotation?Not that I am aware of. I installed and deinstalled wacomrotate and the fjbtndrv-packages. They are gone As far as I remember I did not try to install anything else.  What else could there be? Anything I should look for?

---

### Post by Favux on 2013-02-12
Well my KDE test setup on my Desktop for Magick is Kubuntu 12.04 and openSUSE so I can't test 12.10.  Don't have either on my tablet PC.
> I installed and deinstalled wacomrotate and the fjbtndrv-packages. They are gone As far as I remember I did not try to install anything else. What else could there be? Anything I should look for? 
I was thinking of some other rotation script.  Or maybe you have the KDE Wacom tablet system tool installed?  Don't think that has anything for rotation other than maybe flipping a graphic tablet to left handed.  Wondering if something new was added to the KDE version in 12.10.

Let's see if we can get a handle on if this is a kwin or video driver issue.  Kwin is the window manager for KDE like Mutter is the window manager for Gnome 3.

The xrandr commands to change screen orientation to the right and then back to laptop would be:
```
xrandr -o right

xrandr -o normal
```
Without the fix script running does just doing that change the CTM for the stylus to .625 when rotating back to laptop?

Does just doing the matching xsetwacom commands:
```
xsetwacom set "Serial Wacom Tablet stylus" rotate cw

xsetwacom set "Serial Wacom Tablet stylus" rotate none
```
also change the stylus CTM?

Oh and by the way.  With recent xf86-input-wacom's (actually for a while now) just doing the xsetwacom rotate command on the stylus will also flip the eraser and touch, and least on serial or ISDv4 tablet PCs.  With usb still need a separate command for touch because it is a separate parent not daughter device.  No longer need a separate command for each input tool.

---

### Post by markwig on 2013-02-13
> **Favux said:**
> 
I was thinking of some other rotation script.  Or maybe you have the KDE Wacom tablet system tool installed?  Don't think that has anything for rotation other than maybe flipping a graphic tablet to left handed.  Wondering if something new was added to the KDE version in 12.10.


I feel sooo bad ... you are absolutely right. In the systems section there is a subsection for input devices which supposedly also handles the tablet. Before I tried anything else after the installation of kubuntu I checked there a box in the subsubsection for the pad options which says "Rotation with the screen" (the installation is German, so in the English version it might be slightly different). Unchecking this box has solved all the problems. Magick and xrotate.py work perfect without any further scripts or adjustments. 

I am really sorry that I forgot about that box and wasted your time. Thanks a lot for your help.

---

### Post by Favux on 2013-02-13
Outstanding!  Mystery solved and now I know what to look for in KDE.
> I am really sorry that I forgot about that box and wasted your time.
lol  Macht nichts.  :)

---

