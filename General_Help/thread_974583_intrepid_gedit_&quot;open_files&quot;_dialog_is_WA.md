---
title: "intrepid gedit &quot;open files&quot; dialog is WAY TOO SMALL!"
date: 2008-11-07
forum: General Help
---

### Post by unebaguettesvp on 2008-11-07
is anyone else getting this?!
[IMG]http://i37.photobucket.com/albums/e91/unebaguettesvp/gedit.png[/IMG]
i've seen this on two machines with intrepid. it's REALLY annoying!

has anyone seen this? workarounds? bug reports? i tried doing a google and forums search.

---

### Post by xkalibur84 on 2008-11-07
Actually I think that happens anytime you want to open anything because it's happened to me(using Intrepid also), but I wasn't using gedit.  I forgot what I was using at the time, but yeah, anytime I get the open dialogue box, it would show up pretty much exactly like the one in your picture.

---

### Post by unebaguettesvp on 2008-11-07
you're right. sorry, i should have been more clear. i've also seen this with the archive manager when i want to create a new file.

is this a gtk problem? anyone know anything about this?

---

### Post by unebaguettesvp on 2008-11-07
bump. has anyone seen this? should i open up a bug report?

---

### Post by fragos on 2008-11-07
I've seen it but don't recall which application. I just tried Gedit and the open window was fine. You should file a bug if you can tell what you do when the problem happenes so that the developers can reproduce the problem.

---

### Post by tjajab on 2008-11-13
I have the exact same problem in some applications. Right now I can reproduce it in "Glade interface designer", but I have previously seen it in some other applications too. In my other applications (e.g. firefox), it seems as if it opens small and then immediaty resizes to a more appropriate size.

---

### Post by RDV on 2008-11-18
I have this same problem with numerous programs under Intrepid 2.6.27-8 64bit with compiz-fusion turned on. This issue has appeared ever since I upgraded to Intrepid on my 64bit PC. 

This problem does not happen on my Intrepid 32bit install (eeePC 4C 701). Even with compiz-fusion turned on.

I have seen a bug report ([https://bugs.launchpad.net/ubuntu/+bug/279699](https://bugs.launchpad.net/ubuntu/+bug/279699)) but no work around just someone commenting that turning off compiz-fusion fixes the problem. I do not find that an acceptable solution. 

IMHO this is an important bug to get fixed.

Apps I have seen this issue:
gedit
mkvmerge_gui
avidemux
Remote Desktop Viewer
NOTE: On this list only gedit inconsistently has this problem. 

Apps without the issue:
Firefox
Thunderbird
K3b
File Search
Smplayer
Audacity
Gimp
Open Office Word v3
Totem (movie player)

---

### Post by dr7heads on 2008-11-18
I'm seeing this as well using Bluefish and Firefox with 8.10 32bit with compiz.

---

### Post by svivian on 2008-11-29
Yeah I've had this, too. Oddly enough if I keep doing Ctrl+O, Esc, Ctrl+o and so on, sometimes I get the small window, sometimes I get the normal sized window. I'd say it's a bug, I mean, it shouldn't be happening.

---

### Post by skalka on 2008-11-29
It happens when the mother window is smaller than the child. Try to open a file in gedit with the application maximized, everything works fine. Try now to write an image with brasero, when you try to choose a path the result is a damn small child window, everything is ok again with a maximized window. Now we have something useful to reproduce the bug, we can add it to launchpad I think. The same happens with metacity, at least on my machine. I hope it helps!

---

### Post by Leperous on 2008-12-01
I've seen this (or something very similar) when choosing icons for menu/desktop items, so I'm not sure if it's a gedit bug. But it's certainly very annoying, especially since it happens *sometimes* when you click "open file" rather than always.

---

### Post by DJ_Peng on 2008-12-13
It's definitely *not* a gedit bug. I see it in Firefox, Evolution, OpenOffice.org, and just about any app that uses the file open/save dialog. It's not 100% of the time, but it does seem to happen on the first time you open the dialog in an app, although I have seen it multiple times in a single session with a single app.

You're absolutely right, RDV, that's not a solution, and luckily someone has dispelled the notion that it's Compiz-related.

I'll try to find an upstream bug, and if I find one I'll post a link.

---

### Post by sdowney717 on 2008-12-13
I tried to duplicate this and could not

shrunk firefox very small and open dialog was normal size.

I can also manually resize the dialog box

---

### Post by DJ_Peng on 2008-12-13
I can always resize the window, but it's a definite pain to have to resize that one dialog so often. I suspect there's a combination of software/settings that can trigger it, but as you see from my screenie it has occurred on multiple systems.

---

### Post by jojohippo on 2009-01-24
Bump. I've also got this problem... it seems like it happens on all sorts of apps when using the open/save dialogue. Anyone find a fix?

---

### Post by beeman on 2009-02-02
I have the same problems on two machines, both Ubuntu 8.10 32bit. :(

---

### Post by mr_niceguy on 2009-02-02
Yep, same issue here.

---

### Post by unebaguettesvp on 2009-02-25
looks like this issue will be solved in jaunty!

[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/285285](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/285285)

---

