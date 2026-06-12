---
title: "nano and gedit help"
date: 2008-10-15
forum: General Help
---

### Post by guest_user on 2008-10-15
How do I get these 2 editors to display line numbers at the side of the screen? Thanks.

---

### Post by scragar on 2008-10-15
well in gedit it's:

edit > preferences
display line numbering

---

### Post by Denestria on 2008-10-15
For nano if you have a file open ctrl-c will show cursor position or you can invoke it from the command line with nano -c or you can make a .nanorc in your home directory with **set const** option in it to make it always open files with cursor position.

---

### Post by guest_user on 2008-10-15
> **Denestria said:**
> For nano if you have a file open ctrl-c will show cursor position or you can invoke it from the command line with nano -c or you can make a .nanorc in your home directory with **set const** option in it to make it always open files with cursor position.

where can I learn how to make a .nanorc file?

---

### Post by Denestria on 2008-10-15
Applications > Accessories > Terminal

To see a list of options:
```
man nanorc
```
To open/create the file:
```
nano .nanorc
```
In the blank file enter: 
```
set const
```
and any other settings you want then control-x to exit, y to save.

---

### Post by guest_user on 2008-10-15
> **Denestria said:**
> Applications > Accessories > Terminal

To see a list of options:
```
man nanorc
```
To open/create the file:
```
nano .nanorc
```
In the blank file enter: 
```
set const
```
and any other settings you want then control-x to exit, y to save.
Ok, it worked, what does the set const in the file do anyway? and thanks.

---

### Post by Sam on 2008-10-15
> **guest_user said:**
> Ok, it worked, what does the set const in the file do anyway? and thanks.

set/unset const
   Constantly display the cursor position in the status bar.

```
man nanorc
```

---

