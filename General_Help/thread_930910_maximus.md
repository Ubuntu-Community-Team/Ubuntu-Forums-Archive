---
title: "maximus"
date: 2008-09-26
forum: General Help
---

### Post by dragon2611 on 2008-09-26
Can someone tell if it's possible to configure maximus not to maximise certain windows (e.g the AMSN main window).

---

### Post by dragon2611 on 2008-09-27
In case anyone else encounters the same problem I found the anwser elsewhere.

run gconf-editor (as the user your logged as rather than root) and then go to applications > maximus there is a key there that defines what to exclude from being auto maximised.

---

### Post by ugm6hr on 2009-05-16
Just to clarify:

```
gconf-editor
```
In /apps/maximus/
Name: exlude_class
Right-click -> New key
Enter the app command (Totem is there by default on 9.04NBR)
e.g. *gwibber*

---

### Post by Ultim8Fury on 2009-07-14
thankyou, exactly what I was after.

---

### Post by jakobb on 2009-10-21
Okay, Maybe you will also be able to help me.
I want to use maximus, but I don't want any program to maximize when opening.

So is there a trick not to write every piece of software on that list??

---

### Post by javierrivera on 2009-10-21
> **jakobb said:**
> Okay, Maybe you will also be able to help me.
I want to use maximus, but I don't want any program to maximize when opening.

So is there a trick not to write every piece of software on that list??

Yes, open gconf-editor, go to apps/Maximus, check nomaximize.

---

### Post by jakobb on 2009-11-24
Super! Thank you very much.
Now All I need is to get a minimize and an unmaximize button on "window-picker-applet"

I think this is a good solution to get more pixels out of a small screen :)

---

### Post by cmcanulty on 2010-05-31
I installed maximus and I want all the windows to maximize by default like pdf files office docs etc how do I set that in maximus. I have no maximize unchecked but so far my apps still don't open maximized.

---

### Post by kerry_s on 2010-05-31
> **cmcanulty said:**
> I installed maximus and I want all the windows to maximize by default like pdf files office docs etc how do I set that in maximus. I have no maximize unchecked but so far my apps still don't open maximized.

is maximus running?
did you try logging out & back in?

---

### Post by potrick on 2010-08-24
So useful; thank you everyone!

---

### Post by thatguyisjames on 2010-09-28
does anyone know if its specific for the terminal launch command or just the app name?

what i've added was

Empathy, gnome-terminal

it works as expected (THANK YOU) but i'm wondering should I be using syntax as if i was launching from the term

ie "empathy" not "Empathy"
and "gnome-terminal" not "GNOME Terminal"

or does the software know that this is all the same application

---

### Post by kernst on 2011-01-26
> **thatguyisjames said:**
> does anyone know if its specific for the terminal launch command or just the app name?

What you need to use is the CLASS returned by the [FONT="Courier New"]xprop[/FONT] command. If you install the [FONT="Courier New"]x11-utils[/FONT] package, you'll get this command (not sure if that package is installed by default).

An example for GNOME Terminal:
[LIST]
[*]Run GNOME Terminal
[*]Type [FONT="Courier New"]xprop | grep CLASS[/FONT] [ENTER]
[*]Put the crosshairs over the GNOME Terminal window and click
[/LIST]

This is the result:
```
WM_CLASS(STRING) = "gnome-terminal", "Gnome-terminal"
```

And so you need to add "Gnome-terminal" (no quotes) to Maximus' exclude list using the techniques described earlier in this thread.

Here is a script which you can bind to a hotkey to do all this automatically: [http://ubuntuforums.org/showthread.php?t=1483946](http://ubuntuforums.org/showthread.php?t=1483946). It works really well, and makes using Maximus for all windows (*e.g.*, the "no_maximize" option unset) actually tolerable.

---

