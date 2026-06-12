---
title: "Desktop will not load"
date: 2008-07-27
forum: General Help
---

### Post by bolter40k on 2008-07-27
last night i installed a new theme.  This morning i turned on my computer to check my email and the desktop will not load.

There are two ways i can fix this:
1:use hot keys to get to the menus (i dont know the hotkey commands)

2:reformat and start over.  Im prepared to do this but i need to know how to use terminal to back up my hard drive.  I know how to navigate, and i know the copy and move commands.  I do not know how to navigate a removable disk.

---

### Post by overdrank on 2008-07-27
> **bolter40k said:**
> last night i installed a new theme.  This morning i turned on my computer to check my email and the desktop will not load.

There are two ways i can fix this:
1:use hot keys to get to the menus (i dont know the hotkey commands)

2:reformat and start over.  Im prepared to do this but i need to know how to use terminal to back up my hard drive.  I know how to navigate, and i know the copy and move commands.  I do not know how to navigate a removable disk.

HI and have you tried to boot into recovery mode which is the usually the seconded choice from the grub. Then you my try the xfix option and then continue booting.

---

### Post by bolter40k on 2008-07-27
> **overdrank said:**
> HI and have you tried to boot into recovery mode which is the usually the seconded choice from the grub. Then you my try the xfix option and then continue booting.

i just tried the xfix option.  It completed and then i booted normally it did not work i still have a desktop that wont load

---

### Post by mbarak on 2008-07-27
May you please explain more about what you mean by the desktop will not load?
Can you log in?
Can you see anything?
How did you install the theme?

If you can log in, you can log into GNOME Failsafe and try to fix your account from there

Other than that, I cannot help you without more detail

Edit:
To log in to GNOME Failsafe click on Actions (bottom left) > Change Session and select Gnome Failsafe
Then log in as usual

---

### Post by bolter40k on 2008-07-27
> **mbarak said:**
> May you please explain more about what you mean by the desktop will not load?
Can you log in?
Can you see anything?
How did you install the theme?

If you can log in, you can log into GNOME Failsafe and try to fix your account from there

Other than that, I cannot help you without more detail

Edit:
To log in to GNOME Failsafe click on Actions (bottom left) > Change Session and select Gnome Failsafe
Then log in as usual

i can login then when i get to the desktop there are no menus icons or anything except my wallpaper.

i intalled the theme by dragging it into the menu with the rest and then double clicked

---

### Post by mbarak on 2008-07-27
Ok, that's easy to fix :p
First I want to check if the menus are actually there, and if you're desktop is, well - actually there

Type Alt+F1 - thats the Shortcut for the Applications Menu
if nothing comes up, you're menus aren't there (don't panic - easily fixed)

Next, right click on the desktop - nothing? again, see the above message

Type Alt+F2 - the box that comes up lets you start any program you want
If you have menus type in
```
gnome-panel
```
If you have no desktop type in
```
nautilus
```

That should fix it temporarily

Now go to System > Preferences > Sessions

Close all your programs (at least the ones you don't want starting up everytime you log in :p)
click on the last tab in the Session Preferences program (Called Session Options)
finally, click "Remember Currently Running Applications"

Log out, and back in, and see if everything has been fixed

---

### Post by bolter40k on 2008-07-27
> **mbarak said:**
> Ok, that's easy to fix :p
First I want to check if the menus are actually there, and if you're desktop is, well - actually there

Type Alt+F1 - thats the Shortcut for the Applications Menu
if nothing comes up, you're menus aren't there (don't panic - easily fixed)

Next, right click on the desktop - nothing? again, see the above message

Type Alt+F2 - the box that comes up lets you start any program you want
If you have menus type in
```
gnome-panel
```
If you have no desktop type in
```
nautilus
```

That should fix it temporarily

Now go to System > Preferences > Sessions

Close all your programs (at least the ones you don't want starting up everytime you log in :p)
click on the last tab in the Session Preferences program (Called Session Options)
finally, click "Remember Currently Running Applications"

Log out, and back in, and see if everything has been fixed

thank you very much... I would like to reformat any ways but now i can back my files thanks again

---

