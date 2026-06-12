---
title: "Help writing a script or BAT file"
date: 2008-10-20
forum: General Help
---

### Post by Brandon81 on 2008-10-20
Here's what I want to do... 

I have Ubuntu and XP installed. GRUB Loads off menu.lst. I want to make two other files: windows.lst and ubuntu.lst, each one that will make the default OS in the grub menu that OS. (Doing a lot of stuff by way of remote desktop)

So basically I am looking to click one menu item (script file or batch file) for Windows and copy the windows.lst over the menu.lst (leaving windows.lst there of course as well), overwrite the file, and not ask me if I want to overwrite it or anything. To just do it. Same with the Ubuntu lst file. 

Something like 
```
sudo cp /media/160gbXP/windows.lst /media/160gbXP/menu.lst -overwrite modifier
```

Also if anyone can tell me if there's anything specific I would have to do to make Windows load first aside from re-ordering the OS entries in the menu.lst. I also don't know how to make a "bat" file in Ubuntu. (Unless there's an easier way to do this!) I would assume I would make a new text file and then give it some kind of specific extension. And I would need to know how to launch it from the menu, what program to associate with it. (Like how you can't make a folder a menu item without putting down nautalis /folder)

Thanks so much in advance. This will help me incredibly.

---

### Post by Brandon81 on 2008-10-20
Bump... Anyone?

---

### Post by Sam on 2008-10-20
Excuse me, but what's the point in this ? What's the differences between windows.lst and ubuntu.lst ?

---

### Post by mixmaster on 2008-10-20
I have no idea what -overwrite modifier is supposed to achieve, but if you create a file called change_boot containing these two lines:


#!/bin/bash
sudo cp -f /media/160gbXP/windows.lst /media/160gbXP/menu.lst

Then issue the command 
chmod 755 change_boot

you will be able to do what you want by executing change_boot

(files are made executable in linux via chmod not via file extensions).

Personally I'm not convinced this is a good idea.  It is better to set up the default to the OS you use most then select the other as and when you need it - there is too much chance of screwing something up if you keep changing system files on the fly like this.

---

### Post by Brandon81 on 2008-10-20
I appreciate the responses. I'd basically just like an easy way to change the default boot OS because I do a lot of work on my computer via remote desktop, so being able to go in and just change the menu.lst to a premade one for either linux or windows would, to me, be the ideal situation. 

Thank you very much for the suggestion on how to accomplish this, I think that'll work. Exactly what I was looking for! I just need to copy menu.lst and make the changes. If I just put the Windows boot information at the top of the file, that would make Grub choose windows by default, right?

I just want to be able to click "Windows" so that when I restart the computer it will restart in windows, then be able to easily change it back.

EDIT: The overwrite modifier is because I assumed if you said "copy windows.lst to menu.lst it would ask me if I want to overwrite the file, and I wanted it to not ask everytime. Not that familiar with the linux command line situation, so thanks again!

---

