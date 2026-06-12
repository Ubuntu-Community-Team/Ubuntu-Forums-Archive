---
title: "Digikam: not possible to erase photos"
date: 2008-11-04
forum: General Help
---

### Post by Achilles124 on 2008-11-04
I have the photomanager Digikam on my desktop. When I want to move photos to trash, I get the following message:

> Could not rename file

There has a been a post elsewhere dealing with this problem:
[http://bugs.kde.org/show_bug.cgi?id=123120]("http://bugs.kde.org/show_bug.cgi?id=123120")

Following the instructions written there, I typed:
ln -s ~/.Trash/ ~/Desktop/Trash 

That didn't work. I get the following error:
/home/ecmpeek/Desktop/Trash': No such file or directory

I am not good at coding. So, I would appreciate your help.

---

### Post by gysvanzyl on 2008-11-04
Create the symbolic link like this instead:
```
ln -s ~/.local/share/Trash ~/Desktop/Trash
```
The delete (move to trash) function now works in Digikam, but you have an ugly new icon on your desktop.

Of course shift-delete still deletes without the need for the symbolic link.

I'm using digikam 0.9.4 on Intrepid.  Didn't have this problem using digikam 0.9.3 on Hardy.

---

### Post by Achilles124 on 2008-11-04
thank you, gysvanzyl

Greetz,

---

### Post by gysvanzyl on 2008-11-04
Aha! I found the right way to fix this.

Open file ~/.kde/share/config/kdeglobals in a text editor.

Change the line

> Trash[$e]=$HOME/Desktop/Trash/

to:

> Trash[$e]=$HOME/.local/share/Trash

Restart digikam and now the delete function works without the ugly symbolic link.

---

### Post by Achilles124 on 2008-11-05
Yes, that works, gysvanzyl. Thank you again. :p

---

