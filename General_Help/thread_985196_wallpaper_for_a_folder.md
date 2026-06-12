---
title: "wallpaper for a folder"
date: 2008-11-17
forum: General Help
---

### Post by bambitous on 2008-11-17
Hello
How an I put a wallpaper for my folders ?
thanks,

---

### Post by Merovius on 2008-11-17
I can't remeber specifically and I'm on a windows machine right now, but, when you have a nautilus file browser window open, one of the options at the top edit, or view or whatever has an option to change the background. Can't remeber what it's called specifically.

Sorry. It is there though.

---

### Post by sirjoebob on 2008-11-17
Edit> Backgrounds and Emblems...

I have used Ubuntu since 5.10 and never know you could do this... lol

---

### Post by bambitous on 2008-11-17
That's working correctly but can I make the operation by editind TXT file like Descktop.ini in Windows ?

---

### Post by sirjoebob on 2008-11-17
I did not understand what you are asking here... I don't know of a text file you can edit for this but dont really see why you would need to either.

---

### Post by kerry_s on 2008-11-17
> **bambitous said:**
> That's working correctly but can I make the operation by editind TXT file like Descktop.ini in Windows ?

i believe the .gtkrc-2.0-mine is the equivalent.

for color:
```
style "mine" = "default"
{
  bg[NORMAL] = "#ffffff"
  bg[ACTIVE] = "#ffffff"
}
widget_class "*Collection*" style "mine"
```

or

for image:
```
pixmap_path "/home/yourhome/images"
style "mine" = "default"
{
  bg_pixmap[NORMAL] = "?.png"
}
widget_class "*Collection*" style "mine"
```

---

### Post by bambitous on 2008-11-19
I make what you said Kerry and I edit correctly the second code.
The crated txt file disappear after I leave the folder and come back but without the change of the wallpaper.

---

### Post by kerry_s on 2008-11-19
> **bambitous said:**
> I make what you said Kerry and I edit correctly the second code.
The crated txt file disappear after I leave the folder and come back but without the change of the wallpaper.

i'm sorry i guess my notes are kind of old, i haven't kept up with gtk changes.

try this one:
```
pixmap_path "/home/user/images"
style "mine" = "default"
{
  bg_pixmap[NORMAL] = "your.png"
}
class "*GtkWindow*" style "mine"
```

---

### Post by bambitous on 2008-11-19
I get the same problem :(

---

### Post by kerry_s on 2008-11-19
> **bambitous said:**
> I get the same problem :(

oh well, just have to do it through the gui.

---

### Post by bambitous on 2008-11-20
> **kerry_s said:**
> oh well, just have to do it through the gui.

How ?

---

### Post by sirjoebob on 2008-11-20
> How ?

> Edit> Backgrounds and Emblems...


From any open folder, do the above and you can change folder BG

---

