---
title: "Problem with .gconf after installing desktop settings file (in Ibex)"
date: 2008-11-23
forum: General Help
---

### Post by lavikl on 2008-11-23
Hi there !
I'm kinda stuck...
I've downloaded and installed "Clear Night" theme, and also the Desktop settings file. after installing the desktop setting everything went wrong. I can't find the apps menu and so on... I just want to undo everything and go back to normal. question is : How do i undo the merge I did with the gconf files ?! or is there a way to restore gconf defaults ( as it was when I just installed interpid?)
I would appriciate and response, I really can't function when my computer is in this state...

---

### Post by ajgreeny on 2008-11-23
In terminal type ```
metacity --replace
``` and compiz will disappear for that session.  You can then use** System->Preferences->Advanced Desktop Effects** to reset the various plugins to a more standard setup, including I hope the merge with gconf, though I'm not quite sure what you mean by that.  You can just change the theme back to something else then by right clicking on the desktop, as normal.

I hope that helps.

---

### Post by lavikl on 2008-11-23
ahh.... this might be a newibe question but :
one of the problems is that I can't see the apps menu (the equivelent to Start menu) and so I don't know how to reach Terminal. I tried to move to a one of the Ctrl-Alt-F3 or the other terminals but I the line :
> metacity --replace 
got me the answer 
> Window manager error :unable to open X display

and I'll try to explain again what I meant before :
After I merged the gconf files, I lost the upper toolbar and it turned into some kind of transparent toolbar with strange symbols ( I guess it happend because I'm sing a foreign language in Ubuntu) and I can't reach any of the softwares that you could normally reach through the toolbar.
I tried to switch into a different Theme (right clicked on the desktop and doing it from there) but although the theme was changed, the strange toolbar remained. I just want to get everything back the way it was when I installed Ubuntu.

---

### Post by ajgreeny on 2008-11-23
OK, I've understood.  To issue the command *metacity --replace* you can also use the Alt+F2 run dialog.  That should switch compiz back to metacity for you for the moment.

As for your merge of .gconf, which I misunderstood as you didn't say you had updated and I assumed a clean install, I think it may eventually be easier to just rename your old hidden .**gconf** folder to **.gconf-bak**, restart gnome by logging out and in again, and then setting gnome as you want it again.  You will still have all of the .gconf subfolders which you can copy back from the backup if you wish, but just be careful or you will end up in the same situation again.

---

