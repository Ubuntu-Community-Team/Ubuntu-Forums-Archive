---
title: "Wha'ts with the title bar in 8.10 ?"
date: 2008-11-18
forum: General Help
---

### Post by Drakkor on 2008-11-18
Sometimes it's orange,but most times,it just disappears ! :confused:
As in this screenshot of a browser window with no title bar,and the
Add-Remove application,also with no title bar !

---

### Post by Crafty Kisses on 2008-11-18
I've had the same issue but I've solved it. What you need to do is for a temporary fix is press "F11" twice, or for the permanent fix, do the following, go into the Compiz Settings Manager, and find "Windows Decorations" add the following line to "Decoration Windows":
```
(any) | class=Firefox

```
Once you've done that, close out CCSM, then open CCSM back up again, then change that to:
```
any
```
Then that should solve the problem, it worked flawlessly. If that doesn't work you can always revert back to metacity:
```
metacity --replace
```
I've also found another fix, what you want do to is press F11 twice. Then once you've done that minimize it and resize the window then make it smaller, then close Firefox then reboot it, and it will be back to normal.

---

### Post by Drakkor on 2008-11-18
The funny part about is that I don't even have CCSM installed and haven't got any eyecandy at all on here...............

---

### Post by Crafty Kisses on 2008-11-18
Then in that case press "F11" twice, and then minimize it and resize the Firefox window, and see if that works. :)

---

### Post by ToFue on 2008-11-20
I've got the same issue, and it's with any app at any moment.. mostly switching between windows.

it just seems pretty lame though- that every time my title bar disappears, I have to execute a nintendo style button combo to fix it...

but thanks for the info anyway! :guitar:

---

### Post by ciscosurfer on 2008-11-20
From what I've gathered, it has to do with only certain themes after enabling a 3rd party graphics driver.  Some themes play nicely, some don't.  If you've enabled the 3rd party graphics driver, then by default, compiz gets enabled as well.  It's very annoying but I've chosen certain themes that do play nicely so I can't complain anymore :-)  I think theme developers need to recognize this b/c this is a recurring problem (and has been for quite some time).

---

### Post by drs305 on 2008-11-20
ciscosurfer,

What you wrote makes sense and applies to me. I'm using an nvidia driver (default install) with the default Intrepid theme and I've seen the characteristics described above. I've tinkered with compiz but haven't found the right combination to change the behavior while keeping the default theme.

---

### Post by ToFue on 2008-11-20
so is there a list compiled that shows an average of which themes play well with what 3rd party driver?

---

### Post by mc4man on 2008-11-20
With default theme or otherwise I mainly see this when the mouse pointer moves into or thru the min., restore, max. button area in unmaximized windows (using nvidia 

Then the title bar becomes partially or fully transparent or disappears altogether.

Normally it's a full colored bar when focus in on window, transparent when not.
Usually clicking in the window (not the bar) restores it.

---

### Post by jbeaunaux on 2008-11-20
I've suddenly had this issue cropping up with both Firefox and OpenOffice 3.0. I've tried the whole pressing F11 twice on both programs and it's only worked on Firefox so far, and even then it only works during that particular session. If I close Firefox after resizing and then relaunch the program, the title bar disappears all over again and I have to repeat the F11 trick to get the title bar back. As far as with OpenOffice, it doesn't work at all there. I know that one of the solutions is to go into compiz manager. How do I find that program, and how exactly should I enter the coding to try the permanent fix? Thanks!

---

### Post by ciscosurfer on 2008-11-21
> **jbeaunaux said:**
> ...How do I find that program, and how exactly should I enter the coding to try the permanent fix? Thanks!You have to actually install it (I have absolutely no idea why the user doesn't get prompted to install it, or even told they can/should install it, after enabling compiz-fusion..but, oh well).  You've basically got two choices, and neither are Canonical supported```
sudo apt-get install compizconfig-settings-manager

sudo apt-get install simple-ccsm
```The gconf backend for Compiz does get installed when you enable your 3rd party driver, but really, who wants to fuss with that?  If I'm going to use eyecandy, I might as well use a GUI to configure it.  But that's just me.  You can find more items that are either already installed or that you can install by running these searches as well```
sudo aptitude update && aptitude search compiz ccsm

sudo apt-get update && apt-cache search compiz
sudo apt-get update && apt-cache search ccsm
```

---

