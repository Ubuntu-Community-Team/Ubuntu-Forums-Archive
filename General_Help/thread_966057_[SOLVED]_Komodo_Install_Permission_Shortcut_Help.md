---
title: "[SOLVED] Komodo Install Permission Shortcut Help"
date: 2008-11-01
forum: General Help
---

### Post by MikeyDL on 2008-11-01
I recently installed Komodo and when I run the command to start Komodo from a terminal window with sudo

     [FONT="Courier New"]sudo ./komodo[/FONT]

the program runs fine.  However, the desktop shortcut and symbolic link I used to create the menu option doesn't seem to work.  I figure it's a perm issue.  The desktop shortcut has root as owner and it's not checked as "allow executing file as program."  Do I need to take ownership and change that checkbox item to get the shortcut to work?  Any ideas?

Thanks!

---

### Post by MikeyDL on 2008-11-01
Been working on this a bit.  

Tried taking ownership of the folder and giving it to my main logon that is working the program.  The program was stored in /home/username/Komodo-IDE-4.  Game my main user owndership of that folder and the shortcuts.  However, still can't run the IDE program without running it from a terminal window and tacking on sudo to the command.

---

### Post by Sand Lee on 2008-11-01
Please post the output of ```
ls -l komodo
```
You said the program can only work correctly as root. In this case, the way to go is running ```
sudo chmod 755 komodo
``` That'll give execute permissions to everyone and write permission for root.

If you want to learn more about permissions, see this tutorial:
[http://tille.garrels.be/training/tldp/ch03s04.html](http://tille.garrels.be/training/tldp/ch03s04.html)

---

### Post by MikeyDL on 2008-11-01
Thanks!  

You game me some of the right ideas.  An ls -l of the bin directory has this ouput.

-rwxr-xr-x 1 luksonm root 582 2008-07-10 06:53 komodo

even with a chown 755 on the file I still wasn't runnign the app.  However, this time I ran the app from terminal without the sudo and it came up with a perm error for a hidden directory .komodoide/

I went and and did a chown -R on that and now the app is running from the shortcut and menu links I created.  :)

I sure wish they had popup error messages for shortcut and link errors but at least got it working.

Thanks!

---

### Post by Sand Lee on 2008-11-01
Excellent! :guitar:
Don't forget to mark this thread as [solved] through Thread Tools.

---

