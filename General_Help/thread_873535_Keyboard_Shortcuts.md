---
title: "Keyboard Shortcuts"
date: 2008-07-29
forum: General Help
---

### Post by Barriehie on 2008-07-29
Quick ? regarding the keyboard shortcuts.  Where can I find a list that will tell me what 0xb2 and such maps to what keystrokes???

Edit: I should rephrase that to what keys generate 0xb2, etc.

TIA,
Barrie

---

### Post by dexter.deepak on 2008-07-29
system -> preferences -> keyboard shortcuts

---

### Post by The Dragon Master on 2008-07-29
Hmmm, doesn't do the job for me Dexter 

I recently upgraded to Hardy and have some teething problems. If I do what you said I get a window titled "Keyboard Shortcuts" containing a table with columns "Action" and "Shortcut". In "Action" are three entries, "Sound", "Desktop" and "Window Management". Under "Shortcut" there is nothing. Below the table is a hint "To edit a shortcut key, click on the corresponding row and type a new accelerator, or press backspace to clear." Neither clicking the rows or hitting backspace achieves anything and the "Help" button returns an error message. The only thing that works in this window is the "Close" button. :-({|=

---

### Post by dexter.deepak on 2008-07-29
oops ! this is somewhat strange.try this :
press Alt+F2 and run this command:
```
gconf-editor
```
now go to apps->metacity , you will find a bunch of options to modify ..

---

### Post by The Dragon Master on 2008-07-30
> **dexter.deepak said:**
> oops ! this is somewhat strange.try this :
press Alt+F2 and run this command:
```
gconf-editor
```
now go to apps->metacity , you will find a bunch of options to modify ..

Great, thanks Dexter.

---

