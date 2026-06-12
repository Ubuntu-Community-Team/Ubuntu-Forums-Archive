---
title: "[SOLVED] Firefox about:config changes revert back, wont keep changes I make"
date: 2008-11-04
forum: General Help
---

### Post by sdowney717 on 2008-11-04
any ideas?

---

### Post by mindwarp on 2008-11-04
> **sdowney717 said:**
> any ideas?

Not a ton of information there, my guess would be your user doesn't have permissions to update your firefox settings.

What does 'ls -la .mozilla' show?

Try running: 'sudo chown -R yourusername .mozilla' then doing it again and see if that resolves it.

---

### Post by sdowney717 on 2008-11-04
scott@scott-desktop:~$ ls -la .mozilla
total 64
drwx------   6 scott scott  4096 2008-09-27 10:50 .
drwxr-xr-x 297 scott scott 20480 2008-11-04 09:22 ..
-rw-r--r--   1 scott scott  1043 2008-09-27 11:05 appreg
drwx------   4 scott scott  4096 2008-07-11 23:30 default
drwx------   4 scott scott  4096 2008-06-28 09:38 extensions
drwx------   3 scott scott  4096 2008-04-17 20:47 firefox
-rw-r--r--   1 scott scott   530 2007-11-20 18:34 mozver.dat
-rw-------   1 scott scott 15147 2008-09-27 11:05 pluginreg.dat
drwxr-xr-x   2 scott scott  4096 2008-04-10 07:35 plugins
scott@scott-desktop:~$

---

### Post by sdowney717 on 2008-11-04
tried it and it still reverts back.

I also then tried it with sudo firefox, still no go.

---

### Post by aysiu on 2008-11-04
_Never_ run the command *sudo firefox*. That (or something similar) is probably what got you that problem in the first place. *sudo* should be run for terminal applications. *gksudo* should be run for graphical applications. More details [here](http://www.psychocats.net/ubuntu/graphicalsudo).

In the meantime, try this:

**Step 1**
Close Firefox completely.

**Step 2**
Paste this command into the terminal: ```
sudo chown -R $USER:$USER ~/.mozilla
```

**Step 3**
Start Firefox again

**Step 4**
Make a change in about:config and see if it sticks.

---

### Post by sdowney717 on 2008-11-04
Tried that, still wont make the change

I would like to get hotmail working again. this thread says if you make this change, then it will work. In past years, I have been able to affect changes in about:config without any trouble.

[http://ubuntuforums.org/showthread.php?t=967743](http://ubuntuforums.org/showthread.php?t=967743)

---

### Post by aysiu on 2008-11-04
How about this, then?

**Step 1**
Close Firefox

**Step 2**
Paste this command in the terminal: ```
mv ~/.mozilla ~/.mozilla.old
```

**Step 3**
Start Firefox

**Step 4**
Try to modify the about:config. See if the changes stick.

---

### Post by sdowney717 on 2008-11-04
ok, first I found this. Apparently the preferences are stored  in prefs.js file, can that be modified directly instead of using 'about:config'?


Just a note: before making any changes to about:config (and they do happen straight away), back up your prefs.js file, which is located in your profile directory. That way if you make a change and want to revert back, you can just use the old preferences file (make sure you close Firefox before restoring).
[http://scott2096.blogspot.com/2007/05/optimising-firefox-by-using-aboutconfig.html](http://scott2096.blogspot.com/2007/05/optimising-firefox-by-using-aboutconfig.html)

---

### Post by sdowney717 on 2008-11-04
yes , that made the changes stick
AND hotmail now works fine.

Is there an easy way to restore my bookmarks?

---

### Post by aysiu on 2008-11-04
> **sdowney717 said:**
> yes , that made the changes stick
AND hotmail now works fine.

Is there an easy way to restore my bookmarks?
Sure, they should be in /home/*username*/.mozilla.old/firefox/*profilename*/bookmarks.html

You can use the Bookmarks > Organize Bookmarks > Import and Backup > Restore > Choose File to get it back in your new profile.

---

### Post by sdowney717 on 2008-11-04
yes, I got them. thanks.

Do you know if when running 'alt+F2', should not the window appear in the foreground?

Mine appears behind whatever windows has the focus.

---

