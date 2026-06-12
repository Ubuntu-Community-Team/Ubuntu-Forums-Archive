---
title: "Dialog redraw problem with effects enabled on Ubunutu 8.10"
date: 2008-11-28
forum: General Help
---

### Post by bilbothebaggins on 2008-11-28
Hi all.

SHORT SUMMARY: Open/Save Dialogs are not redrawn unless they are resized after they opened (when effects are on).

I thought I would share this problem, maybe someone knows more:
I have just installed Ubuntu 8.10 Intrepid Ibex on a new Compaq Presario CQ60-100. The graphics card is a GeForce 8200M G.

The default setting for desktop effects was chosen as "normal" and it all started out pretty well. After switching to the proposed NVIDIA drivers (accelerated v177.80) the speed of everything is really nice and everything looks fine.
However: All dialogs, such as, and especially, Open/Save will not redraw once opened. What I mean is the following: 1) Open gedit 2) File:open 3) the file dialog is displayed 4) If I click around in the dlg nothing happens -- or rather, the dialog reacts, but the action is not displayed, all gui elements stay as they are.
If I go and maximize, or resize this dialog then the redrawing works again, i.e. the dialog behaves normally.
(Clicking 'Cancel' or 'Open' will always correctly close the dialog.)
 
I have observerd this behaviour with:
* All Gnome File dialogs in all applications
* Open Document Dialog in Firefox 3
* Also in the project settings dialog of ecplise (-> Java) but there it seems to only happen every other launch of the dialog.

If I set the Desktop Effects to "Extra/High" the behavior is the same.
If I disable the desktop effects, everything is working OK and all dialogs are displayed and behave correctly!

So I'm stuck for now with disabled effects, which is a real shame because performance-wise it's running good even on the "High/Extra" settings.

Should I change some NVIDIA X Server Settings or maybe try the 173 driver version? What modules are responsible for the effects, maybe it's something on this side?

cheers,
-btb-

---

### Post by bilbothebaggins on 2008-12-05
I found a thread that describes my problem:
[SOLVED] dialog boxes dont work with desktop effects 
[http://ubuntuforums.org/showthread.php?t=984645](http://ubuntuforums.org/showthread.php?t=984645)

Only thing is, this was tagged a "solved" with the solution being that you should maximise every file-dialog prior to using it.
I also discovered that the dialogs work once they have been maxed/resized, but that's just one aspect of the bug and certainly not a solution :)

Has anyone found a better solution ?

cheers,
btb

---

