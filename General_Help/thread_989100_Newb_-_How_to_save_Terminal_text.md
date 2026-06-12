---
title: "Newb - How to save Terminal text?"
date: 2008-11-21
forum: General Help
---

### Post by Evil Overlord on 2008-11-21
Brand new to Ubuntu - 8.10 from CD

I have a wireless problem (Broadcom 4306, Gateway 7422GX).

I've seen a lot of posts about how to handle this, and will try some out.  However, if I do need to ask for help, most threads ask for info from a Terminal session.  I can run Terminal fine, and the commands provide a wealth of information.

Sadly, I don't have any idea how to save the result as a file.  Since I have no internet access on the machine in question, I need a file that I can transfer to a flash drive, then to a Windows machine, then paste into a post.

I'm sure this is really simple, but I can't find a save or print command in Terminal. :confused:

---

### Post by Peter09 on 2008-11-21
try command > filename

---

### Post by Kevbert on 2008-11-21
As Peter09 points out you can use '>' to save the info to a file instead of printing the output to a terminal. So
```
lspci > listpcidevices.txt
```
would route the output of lspci to the listpcidevices.txt file in the current directory (your home directory by default). The other way would be to highlight the text with the mouse and use Ctrl-Shift-C to copy and Ctrl-V to paste it elsewhere (in a new post or into a text file which you've already opened).

---

### Post by drs305 on 2008-11-21
As Peter09 suggests, you can send the results to a file.
Example: sudo blkid > $HOME/Desktop/uuid.txt

You can also copy/paste terminal results but it's a bit different than windows. To copy, highlight the text and CTRL-SHIFT-C. To paste into a terminal, CTRL-SHIFT-V.  Anything copied from a terminal window can be inserted in a text file with the more standard CTRL-V.

---

### Post by gpsmikey on 2008-11-21
Check out the man page on "script" (I can never remember it then it takes me a while to find it again - for some reason "script" is not intuitively obvious to me ... sigh .. must be the gray hair :) ).  Anyway, you use "script filename" then until you exit, all things typed/sent to the terminal will go to that file.  It is a regular text file.

mikey

---

### Post by Evil Overlord on 2008-11-25
Thanks to all.:KS  This was very helpful.:)

---

